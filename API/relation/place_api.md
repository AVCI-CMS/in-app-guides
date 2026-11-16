# Place API Guide

The Place API manages physical venues, event locations, and geographical interest points. It provides detailed logistical information such as capacity, operational hours, and precise location data.

## Base URL
`GET /v1/place`

---

## Place Statuses
- `ACTIVE`: Publicly visible and bookable location.
- `DRAFT`: Venue under setup.

**Cascade on soft-delete:** When a place is soft-deleted (e.g. venue closed), the platform may **unpublish or set to Draft** any **events** that use this place, and any **routes** that contain those events, so that broken tours do not stay on sale. See [Event API – Platform behavior (Routes)](../catalog/event_api.md#platform-behavior-routes) for the event/route side.

---

## Data Structures

### Place Logistics
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | The venue name. |
| `capacity` | `object` | `{ min: number, max: number }` visitor limits. |
| `working` | `array` | Daily operational hours (0-6 for Mon-Sun). |
| `pricing` | `object` | `{ isPaid: boolean, pricingType?: 'HOURLY'|'DAILY'|'PER_EVENT'|'FIXED', amount?: number, currency?: string }` rental rate. |
| `address` | `object` | Detailed physical address, coordinates, and district info. |
| `area` | `array` | List of categories/neighborhoods this place belongs to. |

---

## Endpoints

### List Places
`GET /v1/place`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `area` | `string` | Filter by area/neighborhood slug |
| `search` | `string` | Search by name or description |

---

### Get Short Place Info
`GET /v1/place/short/:slug`

Retrieves a condensed version of the venue profile, optimized for mobile cards and list overlays.

---

### Get Place Details
`GET /v1/place/:slug`

Retrieves the exhaustive venue profile, including gallery images, full capacity details, pricing model, and weekly schedule.

**Response Data (`data`):**
```json
{
  "name": "The Grand Workshop",
  "slug": "grand-workshop",
  "abstract": "A spacious venue for artisan events.",
  "capacity": { "min": 20, "max": 150 },
  "working": [
    { "day": 1, "hours": { "start": "09:00", "end": "18:00" } }
  ],
  "pricing": {
    "isPaid": true,
    "pricingType": "DAILY",
    "amount": 25000,
    "currency": "TRY"
  },
  "address": { "city": "Istanbul", "district": "Besiktas" },
  "logo": { "url": "..." },
  "gallery": [ { "url": "..." } ]
}
```

---

### Get Place Details by ID
`GET /v1/place/id/:_id`

Retrieves the exhaustive venue profile directly using its database `_id` identifier.

---

## Social & Interactions
- `/v1/place/category`: Browse place categories (mapped as `area`).
- `/v1/place/like/:slug`: Favorite a venue.
- `/v1/place/view/:slug`: Log a location view.
- `/v1/place/question/:slug`: Venue-specific Q&A.
- `/v1/place/share/:slug`: Track venue profile sharing.

---

## Place Ownership & Event Hosting Access Rules

Places in AVCI CMS have strict multi-tenant ownership and delegation rules:

### Ownership & Scope Fields
| Field | Type | Description |
| :--- | :--- | :--- |
| `ownerType` | `'WORKSPACE' \| 'MERCHANT' \| 'BRAND' \| 'ORGANIZATION'` | Entity category that owns this venue. |
| `ownerEntity` | `ObjectId` | ID of the Merchant, Brand, or Organization. |
| `isPublicPool` | `boolean` | If true, any authorized seller/brand in the workspace can book events here. |
| `inheritToAffiliates`| `boolean` | If true (when owned by an Organization), all affiliated merchants can book events here. |
| `authorizedMerchants`| `ObjectId[]` | Specific merchants granted hosting permissions. |
| `rentals` | `PlaceRental[]` | Leased periods `{ renterType, renterEntity, startDate, endDate }`. |

### Event Creation Authorization Check
When creating or updating an event with a `place`:
1. **Platform Admins / Owners (`AVCI`, `WORKSPACE_OWNER`, `WORKSPACE_ADMIN`)** can use any place in the workspace.
2. **Merchants & Brands** can only book a place if:
   - They **own** the place (`ownerType === 'MERCHANT' && ownerEntity === user.merchantId`), OR
   - The place is in the **public pool** (`isPublicPool: true`), OR
   - The place is owned by an **Organization** the merchant is affiliated with and `inheritToAffiliates: true`, OR
   - The merchant is explicitly listed in `authorizedMerchants`, OR
   - The merchant has an **active rental** covering the event dates.
3. If unauthorized, the API returns `403 Forbidden` (`FORBIDDEN_ACCESS`).


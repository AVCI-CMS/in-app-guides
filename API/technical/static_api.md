# Static & Location API Guide

The Static API provides constant or semi-constant data required for form population, address management, and corporate validation.

## Base URL
`GET /v1/static`

---

## Endpoints

### List Cities
`GET /v1/static/cities`

Retrieves the official list of cities.

**Response Data (`data` array item):**
```json
{
  "cityId": 34,
  "name": "İstanbul"
}
```

---

### List Districts
`GET /v1/static/districts/:cityId`

Retrieves districts for the specified city.

**Response Data (`data` array item):**
```json
{
  "districtId": 450,
  "name": "Kadıköy",
  "cityId": 34
}
```

---

### List Neighborhoods
`GET /v1/static/neighborhoods/:districtId`

Retrieves neighborhoods (mahalleler) for the specified district.

**Response Data (`data` array item):**
```json
{
  "neighborhoodId": 12040,
  "name": "Caferağa Mah.",
  "districtId": 450
}
```

---

### Tax Administrations
`GET /v1/static/tax-administration/:cityId`

Retrieves a list of valid Revenue Administration (GİB) tax offices (Vergi Dairesi) for a specific city.

#### Plate Code Normalization
The backend automatically normalizes plate numbers (`1`, `01`, `001`, `34`, `034`) to the corresponding 3-digit GİB province identifier.

#### Query Parameters
- `district` *(optional)*: Case-insensitive filter to match tax offices located in a specific district (e.g. `?district=Kadıköy`).

**Example Request:**
`GET /v1/static/tax-administration/34?district=Kadıköy`

**Response Data (`data` array item):**
```json
{
  "officeCode": "34260",
  "name": "Kadıköy Vergi Dairesi Müdürlüğü",
  "cityId": 34
}
```


---

### Use Cases
- **Address Selection**: Populate city/district dropdowns in user profiles or checkout forms.
- **Merchant Onboarding**: Validate tax office selections during legal entity registration.

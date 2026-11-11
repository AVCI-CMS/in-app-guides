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
  "name": "Beşiktaş",
  "cityId": 34
}
```

---

### Tax Administrations
`GET /v1/static/tax-administration/:cityId`

Retrieves a list of valid tax offices (Vergi Dairesi) for a specific city.

**Response Data (`data` array item):**
```json
{
  "officeCode": "34260",
  "name": "Beşiktaş Vergi Dairesi",
  "cityId": 34
}
```

---

### Use Cases
- **Address Selection**: Populate city/district dropdowns in user profiles or checkout forms.
- **Merchant Onboarding**: Validate tax office selections during legal entity registration.

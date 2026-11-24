# CareCompass: BedFinder Blitz (v2.1)

A React + Vite emergency bed-discovery demonstration with a Leaflet map, proximity estimates, ward filters, local demo reservations, validated persistence, audit history, and an Express sample API.

## Features

- Haversine distance and approximate travel-time estimates
- Leaflet facility map with a list-based fallback if map tiles/library loading fails
- Search by facility, address, and specialty; ward availability filters and sorting
- Browser geolocation with a clear fallback location
- ICU/general demo bed holds, release actions, and a local audit trail
- Local persistence for facility counts, reservations, and audit history
- Admin console with bounded bed-count adjustments
- Input validation utilities, schema-checked local persistence with v2 migration, safer DOM-based map popups, error boundary, and automated frontend/API tests
- API-level bed capacity validation, structured errors, health endpoint, and bounded audit history
- Express sample API with health, listing, and bed update endpoints

## Run locally

Requirements: Node.js 18+ and npm.

```bash
npm install
npm test
npm run build
npm run dev
```

In a second terminal, run the optional API:

```bash
npm run server
```

The Vite development server proxies `/api` to `http://localhost:4000`. Set `CLIENT_ORIGIN` to the exact frontend origin when enabling cross-origin API access.

## Demo access

The Admin Console demo passcode is `ADMIN2026`. It is intentionally a client-side demonstration gate and is **not authentication**. Do not use this implementation or passcode for real hospital operations. A production deployment must move authentication and authorization to the server, use role-based access control, HTTPS, rate limiting, persistent database transactions, audit retention, and verified hospital integrations.

## Data and safety limitations

- Facility names, phone numbers, capacities, and bed counts are sample/demo data and must not be treated as live hospital availability.
- Browser local storage is device/browser-specific and is not shared between users. The sample API uses in-memory data and resets when the server restarts. API audit history is also in-memory.
- Distance is straight-line Haversine distance; ETA is an estimate, not live traffic routing.
- A bed hold in this demo is not a confirmed hospital reservation. Call the facility to verify availability and admission suitability.
- Do not enter patient-identifiable or other sensitive health information.

## Project structure

```text
src/
  components/   UI cards, map, admin console, error boundary
  data/         sample facility dataset
  utils/        distance and validation helpers
server/         sample Express API
tests/          Node test runner tests
```

## Verification

Tests cover distance calculations, bed-count validation, text sanitization, persisted-state validation and migration, API health/listing, invalid update rejection, valid bed updates, and audit logging. Run `npm test` and `npm run build` before deployment.

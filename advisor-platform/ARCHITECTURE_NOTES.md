# Architecture Notes (Current Implementation)

This document reflects the implementation currently present in source files.

## Runtime shape
- Backend entrypoint: `server/index.js` (Express app + cron setup).
- Frontend entrypoint: `src/main.jsx` (React SPA with protected routes).
- Shared persistence: PostgreSQL through `server/db/index.js`.

## Implemented backend domains
- Auth: register/login/me/refresh/logout (`server/routes/auth.js`).
- Performance: list periods, query a period, CSV upload with transaction upsert, delete period (`server/routes/performance.js`).

## Stubbed backend domains
- Advisors, reports, analytics, and admin route handlers currently return HTTP 501 placeholders.
- Scheduler and Reynolds import services currently return `skipped` placeholders.

## Frontend state
- Routing shell and role/token guard are implemented.
- Most pages are scaffold placeholders with “coming soon” style content.

## Data model
- Initial migration creates users, performance, commission, goals, logs, and scheduler metadata tables.
- Utility parsing helpers normalize comma-formatted numeric strings before CSV persistence.

## Notable risks
- Project docs claim broader feature completeness than currently implemented source.
- Generic SQL helpers interpolate table names directly; this is safe only when internal callsites pass trusted constants.

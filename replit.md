# SafeHer Safety Alert

SafeHer is a mobile-friendly safety companion with a demo-only SOS flow, local emergency contacts, one-time location sharing, safety tools, incident reports, and profile settings.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/safeher run dev` — run the SafeHer web app through its managed workflow
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/safeher/src/App.tsx` — app shell, routes, local persistence, SOS flow, safety tools, contacts, reports, and profile settings
- `artifacts/safeher/src/index.css` — SafeHer visual theme and responsive styling
- `artifacts/safeher/README.md` — run instructions and safety/privacy notes

## Architecture decisions

- The first build is frontend-only and uses browser `localStorage` so the core app remains usable without a database or external service.
- SOS is intentionally review-first and demo-only; no SMS, calls, or emergency-service contact occurs automatically.
- Browser geolocation is requested only from explicit user actions and is never watched continuously.

## Product

The app gives users a calm home screen with a prominent SOS entry point, a persistent safety circle, one-time location tools, an audio siren, a fake incoming-call demo, private incident reports, and local profile/settings controls.

## User preferences

The requested interface uses soft lavender, white, and light pink with rounded cards, readable type, clear icons, accessible touch targets, and bottom navigation on mobile.

## Gotchas

- Geolocation requires browser permission and may be unavailable in preview environments; the UI includes a manual fallback message.
- SafeHer is not a replacement for local emergency services. Real messaging requires an explicitly configured, supported backend service.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details

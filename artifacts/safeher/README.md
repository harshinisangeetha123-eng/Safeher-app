# SafeHer

SafeHer is a mobile-friendly safety companion with a demo-only SOS flow, locally saved emergency contacts, one-time location sharing, a siren, a fake-call screen, and private incident reports.

## Run locally

From the repository root:

```bash
pnpm --filter @workspace/safeher run dev
```

The Replit workflow supplies `PORT` and `BASE_PATH`. For a direct local run, set them yourself, for example:

```bash
PORT=5173 BASE_PATH=/ pnpm --filter @workspace/safeher run dev
```

## Safety and privacy notes

- Contacts, profile details, incident reports, and the last captured location are stored in this browser with `localStorage`.
- Location is requested only after the user asks for it. SafeHer does not track location in the background.
- Demo Mode never sends SMS, makes calls, or contacts emergency services. The SOS flow always shows a review screen first.
- The siren starts only after the user presses **Start siren** and can be stopped with **Stop siren**.
- The fake call is a visual simulation and never places a real call.
- No map or messaging API key is required. Captured coordinates use a Google Maps link that opens in the user’s browser.

For a real alert service, add a supported backend integration and an explicit confirmation flow before enabling message delivery. Do not place provider keys in frontend code.
# Current task — 2026-10-18

## Canonical deployment repository

`deus-ex-machina-18/rota-radar-2b2cb`, branch `main`, is the source connected to
Netlify project `majestic-caramel-6d22e3`. Make future application changes here.
Production: https://majestic-caramel-6d22e3.netlify.app/
The older `rota-radar` repository supplied the 8 October fixes; changes there
are not automatically deployed to this Netlify project.

## Completed and verified

- Synced the exact tested source tree of `rota-radar` commit `d0ddeea` into the
  deployment repository as `7151ab653b60a239f00794a0df7a5ace11e54471`.
- Netlify published that commit successfully on 18 October 2026.
- Production `/api/destinations`: HTTP 200; 83 destinations, 75 flight and 8 ground.
- Production history: HTTP 200 with eight saved records, labelled as history.
- Ground-only live flight request: HTTP 422; unsupported traveller count: HTTP 400.
- Real CMN / 3-adult scan first surfaced provider HTTP 401; after the user's key
  update and redeploy it surfaces HTTP 429. The fallback record is labelled old.
- Previous core and controlled radar/API/Blobs tests passed for the synced source.
  They do not verify real fares or a seller checkout.

## Current blocker and next single task

The user re-saved the Production `SEARCHAPI_API_KEY` on 18 October 2026.
Netlify redeploy `6ad5280c99c24e448b5b4c27` published successfully with that setting.
A real CMN / 3-adult scan now returns provider HTTP 429 (query/rate limit), rather
than the previous HTTP 401. The UI clearly labels the fallback as an old record.
The account's remaining credits and hourly usage have not been inspected, so the
exact quota reason is not established. Stop repeated scans; check the provider
account quota/reset, then verify one live fare and its seller handoff when allowed.
The stored key was not read or copied by the agent. Never commit it or expose it
in logs, browser output or client code.

Scheduled scans and Android push notifications are not implemented.

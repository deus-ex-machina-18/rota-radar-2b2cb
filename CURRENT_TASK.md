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
- Real CMN / 3-adult scan surfaces HTTP 401 from the fare provider and explicitly
  labels the fallback record as old, not live.
- Previous core and controlled radar/API/Blobs tests passed for the synced source.
  They do not verify real fares or a seller checkout.

## Current blocker and next single task

The Production `SEARCHAPI_API_KEY` is configured for Builds, Functions and Runtime,
but SearchAPI rejects the live request with HTTP 401. Its stored secret is not
readable in the Netlify UI. Correct/replace the Production value using a valid
SearchAPI credential, redeploy, then verify one live route and its seller handoff.
Never commit the key or expose it in logs, browser output or client code.

Scheduled scans and Android push notifications are not implemented.

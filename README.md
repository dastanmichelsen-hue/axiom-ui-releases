# axiom-ui-releases

Release artifacts only. **No source lives here.**

Each release carries:

| Asset | What it is |
|---|---|
| `axiom.exe` | The portable AxiomUI build. One file, nothing to install. |
| `manifest.json` | Version, size and SHA-256 of the exe. |

AxiomUI reads `manifest.json` on launch to see whether a newer build exists.

**Why this repo is public.** The app cannot update itself *using a credential
that can expire* — if the token lapsed, the fix for the lapse could not be
delivered. So this channel is unauthenticated on purpose, and the payload stays
private behind its own rotating token.

Publishing is done by `tools/release-app.cjs`. Do not upload assets by hand; the
manifest and the binary have to agree, and a hand-uploaded asset is how they stop
agreeing.

# web

Container image for the ClawCombinator V1 web application (Next.js frontend + API).

**Registry path:** `ghcr.io/tiltprotocol/clawcombinator-containers/web:latest`

**Source code:** [TiltProtocol/clawcombinator-web](https://github.com/TiltProtocol/clawcombinator-web)

---

## Pull

```bash
docker pull ghcr.io/tiltprotocol/clawcombinator-containers/web:latest
```

No authentication required — this image is public.

---

## Run

```bash
docker run -p 3000:3000 \
  -e DATABASE_URL="..." \
  -e NEXT_PUBLIC_API_URL="..." \
  ghcr.io/tiltprotocol/clawcombinator-containers/web:latest
```

---

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `DATABASE_URL` | Yes | Postgres connection string |
| `NEXT_PUBLIC_API_URL` | Yes | Base URL for API calls from the browser |
| `NEXTAUTH_SECRET` | Yes | Secret for NextAuth session signing |
| `NEXTAUTH_URL` | Yes | Canonical URL of the deployment |

*(See the source repo for the full list of env vars.)*

---

## Builds

Images are built by `.github/workflows/build-web.yml` in this repo. Triggers:
- Daily at 12:00 UTC
- Manual: `gh workflow run build-web.yml -R TiltProtocol/clawcombinator-containers`
- Specific ref: add `-f ref=<sha>`

Tags pushed:
- `latest` — always points to the most recent build of `main`
- `<short-sha>` — immutable per-commit tag (7-char SHA from `clawcombinator-web`)

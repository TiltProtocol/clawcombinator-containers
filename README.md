# clawcombinator-containers

Public registry of container images for the ClawCombinator V1 launchpad.

Images are built and pushed by GitHub Actions in the source repos (or in this repo's own workflows) and published to:

```
ghcr.io/tiltprotocol/clawcombinator-containers/<image>:latest
```

All packages inherit this repo's **public** visibility, making them anonymously pullable.

---

## Images

| Image | Path | Source Repo |
|-------|------|-------------|
| `web` | `ghcr.io/tiltprotocol/clawcombinator-containers/web:latest` | [clawcombinator-web](https://github.com/TiltProtocol/clawcombinator-web) |
| `sai` | `ghcr.io/tiltprotocol/clawcombinator-containers/sai:latest` | [clawcombinator-sai](https://github.com/TiltProtocol/clawcombinator-sai) *(coming V1)* |
| `orchestrator` | `ghcr.io/tiltprotocol/clawcombinator-containers/orchestrator:latest` | [clawcombinator-orchestrator](https://github.com/TiltProtocol/clawcombinator-orchestrator) *(coming V1)* |

---

## Architecture

Source code lives in the named repo for each image. Build workflows in **this** repo (`clawcombinator-containers`) check out the source repo at build time and publish into this repo's package namespace. This ensures all published packages inherit the public visibility of this repo.

Trigger a manual build:

```bash
gh workflow run build-web.yml -R TiltProtocol/clawcombinator-containers
```

Or pass a specific ref:

```bash
gh workflow run build-web.yml -R TiltProtocol/clawcombinator-containers -f ref=<sha-or-branch>
```

Builds also run on a **daily cron** (12:00 UTC) to keep images fresh.

---

## License

MIT — see [LICENSE](./LICENSE).

# radicalbit-github-workflows

Reusable GitHub Actions workflows for the Radicalbit organization.

## Reusable Workflows

| Workflow | File | Description |
|---|---|---|
| **Docker Build & Push** | `.github/workflows/docker.yaml` | Build and push Docker images to a registry (multi-platform `amd64`/`arm64`), with optional `latest` tag and Docker Hub description update |
| **Trivy FS Scan** | `.github/workflows/trivy-fs-scan.yaml` | Run [Trivy](https://trivy.dev) filesystem vulnerability scans with configurable severity levels, optional PR commenting, and skippable directories |
| **Semantic PR Lint** | `.github/workflows/semantic-pull-requests.yaml` | Validate that pull request titles follow [conventional commits](https://www.conventionalcommits.org/) format |

## Other Automation

- **Release** (`.github/workflows/release.yaml`): Automated releases via [release-please](https://github.com/googleapis/release-please-action). Merges to `main` using conventional commit messages trigger automatic versioning, changelog updates, GitHub releases, and floating tags (`v1`, `v1.x`, `v1.x.y`).
- **Pre-commit config** (`.pre-commit-config.yaml`): Shared [pre-commit](https://pre-commit.com) hooks for conventional commit messages and Python linting with [Ruff](https://docs.astral.sh/ruff/).

## Usage

Reference a workflow from another repository:

```yaml
jobs:
  docker:
    uses: radicalbit/radicalbit-github-workflows/.github/workflows/docker.yaml@v1
    with:
      image: my-image
      tag: "1.0.0"
      push: true
    secrets:
      USERNAME: ${{ secrets.DOCKER_USERNAME }}
      PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
      ORGANIZATION: ${{ secrets.DOCKER_ORG }}
```

# Plan My Journey — Reusable Workflows

Central GitHub Actions workflows for the [Plan-My-Journey](https://github.com/orgs/Plan-My-Journey) organization.

## Workflows

| Workflow | Purpose |
|---|---|
| `reusable-build.yml` | Lint, build multistage images, Trivy scan, ECR push |
| `reusable-security.yml` | Snyk, SonarCloud, Gitleaks |
| `reusable-terraform.yml` | fmt, validate, plan, apply with approval gate |
| `reusable-deploy.yml` | GitOps tag update, smoke tests, notifications |

## Usage

```yaml
jobs:
  build:
    uses: Plan-My-Journey/planmyjourney-workflows/.github/workflows/reusable-build.yml@main
    secrets:
      AWS_ACCOUNT_ID: ${{ secrets.AWS_ACCOUNT_ID }}
      AWS_ROLE_ARN: arn:aws:iam::${{ secrets.AWS_ACCOUNT_ID }}:role/ai-travel-github-actions-prod
```

## Required Secrets

- `AWS_ACCOUNT_ID`
- `AWS_ROLE_ARN` (per environment)
- `SNYK_TOKEN`
- `SONAR_TOKEN`
- `GITOPS_PAT`

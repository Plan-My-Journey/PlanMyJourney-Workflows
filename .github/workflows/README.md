# PlanMyJourney Workflows

Reusable GitHub Actions workflows (`workflow_call` only). **No triggers run in this repository.**

Callers live in **PlanMyJourney-App** (`ci.yml`, `dev-deploy.yml`, `promotion.yml`, `release.yml`).

Full architecture, trigger matrix, secrets, and migration notes: **[CI-CD-ARCHITECTURE.md](../CI-CD-ARCHITECTURE.md)**.

## Reusable workflow index

| Workflow | Purpose |
|----------|---------|
| `_detect-changed-services.yml` | Monorepo path diff → service matrix |
| `_ci-service-pull-request.yml` | PR scan chain (Sonar + Snyk + quality gate) |
| `_dev-deploy-backend.yml` | Dev backend: build → ECR → GitOps → ArgoCD → smoke |
| `_dev-deploy-frontend.yml` | Dev frontend: S3 deploy → smoke |
| `_release-backend-service.yml` | Release: build → ECR → service git tag |
| `_release-frontend.yml` | Release: S3 promote → service git tag |
| `_platform-version-check.yml` | Validate platform release semver |
| `_platform-tag.yml` | Create `platform-vX.Y.Z` tag |
| `_sast.yml` | SonarCloud |
| `_sca.yml` | Snyk |
| `_quality-gate.yml` | Aggregate gate |
| `_docker-build.yml` | Docker + Trivy |
| `_docker-publish.yml` | ECR push |
| `_cd.yml` | GitOps deploy PR |
| `_argocd-sync.yml` | ArgoCD sync |
| `_smoke-test.yml` | Post-deploy validation |
| `_pr-comment.yml` | PR summary comment |
| `_production-gate.yml` | Manual production approval |
| `_frontend-build.yml` | npm build artifact |
| `_frontend-s3-deploy.yml` | S3 + CloudFront dev deploy |
| `_frontend-s3-promote.yml` | S3 dev → prod promote |
| `_record-artifact-validation.yml` | Commit status for validated artifacts |
| `_tag.yml` | Per-service release git tag |
| `_terraform.yml` | Terraform plan/apply (used by Terraform repo) |

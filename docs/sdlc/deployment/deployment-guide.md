# Deployment Guide

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start how-it-deploys -->
Pushes to `main` run `.github/workflows/deploy.yml`, which builds the API image (if there is a backend) and deploys the SPA to AWS Amplify. Commits touching only `docs/sdlc/**` don't deploy. Deployments can also be started from the platform's Deployment tab.
<!-- sdlc:auto:end how-it-deploys -->

<!-- sdlc:auto:start environments -->
| Name | Service | Runtime | Scaling | Environment |
|---|---|---|---|---|
| Store SPA | React static site on S3 + CloudFront | Static assets (React 19 build) | CDN edge cache | dev |
| Store API | FastAPI on AWS App Runner | Python 3.12 container (FastAPI 0.115, Uvicorn) | 1 instance, auto-scale on request volume | dev |
| PostgreSQL | Amazon RDS for PostgreSQL 16 | PostgreSQL 16 | Single db.t-class instance, encrypted at rest | dev |
| Media Bucket | Amazon S3 | Object storage | Managed | dev |
<!-- sdlc:auto:end environments -->

<!-- sdlc:auto:start live -->
_Not deployed yet._
<!-- sdlc:auto:end live -->

<!-- sdlc:auto:start topology -->
```mermaid
graph LR
  n_Store_SPA["Store SPA<br/>React static site on S3 + CloudFront"]
  n_Store_API["Store API<br/>FastAPI on AWS App Runner"]
  n_PostgreSQL["PostgreSQL<br/>Amazon RDS for PostgreSQL 16"]
  n_Media_Bucket["Media Bucket<br/>Amazon S3"]
  n_Store_SPA -->|"HTTPS"| n_Store_API
  n_Store_API -->|"TLS/PostgreSQL"| n_PostgreSQL
  n_Store_API -->|"HTTPS"| n_Media_Bucket
  n_Store_SPA -->|"HTTPS"| n_Media_Bucket
```
<!-- sdlc:auto:end topology -->

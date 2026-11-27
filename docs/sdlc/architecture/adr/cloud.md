<!-- sdlc:auto:start adr -->
# ADR-0004: Use AWS for Cloud

Status: Accepted  
Date: 2026-11-27

## Context and Problem Statement

Which Cloud technology does the project use? Decided in architecture v1.

## Considered Options

- AWS
- GCP
- Azure

## Decision Outcome

Chosen option: AWS, because Approved stack; RDS for PostgreSQL 16, S3 for the app's own product media storage, ECS Fargate for the API and S3/CloudFront for the SPA.

## Consequences

Single-region dev setup; multi-AZ/availability hardening deferred beyond the lightweight MVP.
<!-- sdlc:auto:end adr -->
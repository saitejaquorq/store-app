<!-- sdlc:auto:start adr -->
# ADR-0004: Use AWS for Cloud

Status: Accepted  
Date: 2026-11-26

## Context and Problem Statement

Which Cloud technology does the project use? Decided in architecture v1.

## Considered Options

- AWS
- GCP
- Azure

## Decision Outcome

Chosen option: AWS, because Approved stack. SPA on S3+CloudFront, API on App Runner, RDS PostgreSQL 16, and product media in an S3 bucket as the app's own media storage.

## Consequences

Two origins require CORS on the API; encryption at rest (RDS/S3) and in transit supports the served country's data rules once confirmed.
<!-- sdlc:auto:end adr -->
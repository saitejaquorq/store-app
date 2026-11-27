<!-- sdlc:auto:start adr -->
# ADR-0002: Use FastAPI 0.115 for Backend

Status: Accepted  
Date: 2026-11-27

## Context and Problem Statement

Which Backend technology does the project use? Decided in architecture v1.

## Considered Options

- FastAPI 0.115
- Django REST Framework
- Flask

## Decision Outcome

Chosen option: FastAPI 0.115, because Approved stack; hosts catalogue, checkout orchestration, Stripe/SendGrid/S3 integration, admin auth and session validation with Pydantic validation for checkout and product forms.

## Consequences

Async stack requires care around blocking SDK calls; Stripe and SendGrid calls run in worker threads or async clients.
<!-- sdlc:auto:end adr -->
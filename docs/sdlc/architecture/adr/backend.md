<!-- sdlc:auto:start adr -->
# ADR-0002: Use FastAPI 0.115 for Backend

Status: Accepted  
Date: 2026-11-26

## Context and Problem Statement

Which Backend technology does the project use? Decided in architecture v1.

## Considered Options

- FastAPI 0.115
- Django REST Framework
- Flask

## Decision Outcome

Chosen option: FastAPI 0.115, because Approved stack. Hosts catalogue, pricing, checkout/payment orchestration, order tracking and admin management, with Pydantic validation for checkout and product forms.

## Consequences

Async orchestration of Stripe and SendGrid is straightforward; background email sending is kept inline for the lightweight scope rather than a queue.
<!-- sdlc:auto:end adr -->
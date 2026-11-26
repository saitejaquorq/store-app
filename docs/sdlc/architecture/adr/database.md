<!-- sdlc:auto:start adr -->
# ADR-0003: Use PostgreSQL 16 for Database

Status: Accepted  
Date: 2026-11-26

## Context and Problem Statement

Which Database technology does the project use? Decided in architecture v1.

## Considered Options

- PostgreSQL 16
- MySQL
- SQLite

## Decision Outcome

Chosen option: PostgreSQL 16, because Approved stack. Stores catalogue, orders, admin users, sessions and single-row store config; numeric money columns and transactional stock decrement at checkout.

## Consequences

Server-side session rows need periodic cleanup of expired tokens; trivial for this volume.
<!-- sdlc:auto:end adr -->
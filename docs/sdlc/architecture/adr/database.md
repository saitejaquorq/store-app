<!-- sdlc:auto:start adr -->
# ADR-0003: Use PostgreSQL 16 for Database

Status: Accepted  
Date: 2026-11-27

## Context and Problem Statement

Which Database technology does the project use? Decided in architecture v1.

## Considered Options

- PostgreSQL 16
- MySQL
- SQLite

## Decision Outcome

Chosen option: PostgreSQL 16, because Approved stack; relational model fits products, variants, orders and transactional stock decrement with a unique order reference index. Full catalogue, orders and config all live here.

## Consequences

Needs transactional stock-decrement discipline to prevent overselling under concurrency.
<!-- sdlc:auto:end adr -->
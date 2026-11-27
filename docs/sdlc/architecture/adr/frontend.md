<!-- sdlc:auto:start adr -->
# ADR-0001: Use React 19 for Frontend

Status: Accepted  
Date: 2026-11-27

## Context and Problem Statement

Which Frontend technology does the project use? Decided in architecture v1.

## Considered Options

- React 19
- Vue
- SvelteKit

## Decision Outcome

Chosen option: React 19, because Approved stack; built as a mobile-responsive SPA (Vite) served from its own origin, storing the admin opaque token and sending it as Authorization: Bearer.

## Consequences

A separate SPA origin means no shared cookies with the API, so admin auth is token-based rather than cookie sessions.
<!-- sdlc:auto:end adr -->
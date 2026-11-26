<!-- sdlc:auto:start adr -->
# ADR-0001: Use React 19 for Frontend

Status: Accepted  
Date: 2026-11-26

## Context and Problem Statement

Which Frontend technology does the project use? Decided in architecture v1.

## Considered Options

- React 19
- Vue
- SvelteKit

## Decision Outcome

Chosen option: React 19, because Approved stack. Built as a mobile-responsive SPA (Vite build) covering storefront and admin, reading the API base URL from VITE_API_BASE_URL and sending the admin session token as a Bearer header.

## Consequences

A client-side cart and SPA routing need deliberate responsive design to meet NFR-006 on small screens; no server-side rendering, acceptable for this lightweight store.
<!-- sdlc:auto:end adr -->
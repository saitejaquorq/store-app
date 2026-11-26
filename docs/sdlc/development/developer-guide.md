# Developer Guide

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start status -->
_Up to date._
<!-- sdlc:auto:end status -->

<!-- sdlc:auto:start source -->
Generated from commit `c460a7c` · model `claude-sonnet-5`
<!-- sdlc:auto:end source -->

<!-- sdlc:auto:start overview -->
store-app is a Quorq-generated clothing store project with two independent applications in one repo. The frontend (`frontend/`) is a Vite + React 19 single-page app whose screens were approved by the team and currently run entirely on seeded sample data via a component/icon/UI vocabulary in `src/lib`. The backend (`backend/`) is a FastAPI 0.115 service scaffolded from an approved API spec but with no data model or endpoints implemented yet beyond a `/health` liveness check; it uses SQLAlchemy over a SQLite file by default (swappable via `DATABASE_URL`, e.g. to the PostgreSQL 16 instance defined in `docker-compose.yml`) and will later use Alembic migrations once `backend/alembic.ini` exists.
<!-- sdlc:auto:end overview -->

<!-- sdlc:auto:start prerequisites -->
- Node.js (for npm, Vite 6, React 19 tooling)
- Python 3.12 (matches backend/Dockerfile base image)
- pip
- Docker and Docker Compose (optional, for the PostgreSQL service in docker-compose.yml)
<!-- sdlc:auto:end prerequisites -->

<!-- sdlc:auto:start setup -->
1. Clone the repository
2. Copy .env.example to .env and fill in any values it defines
3. cd backend && pip install -r requirements.txt
4. (optional) docker compose up -d to start the PostgreSQL 16 database, then set DATABASE_URL to point at it instead of the default SQLite file
5. cd frontend && npm install
<!-- sdlc:auto:end setup -->

<!-- sdlc:auto:start run -->
| Name | Command | Description |
|---|---|---|
| backend dev | `uvicorn app.main:app --reload` | Runs the FastAPI backend locally with auto-reload (run from backend/, after pip install) |
| frontend dev | `npm run dev` | Starts the Vite dev server for the React SPA (run from frontend/) |
| frontend build | `npm run build` | Bundles the frontend for production; note it does not run TypeScript typechecking |
| frontend preview | `npm run preview` | Serves the production build locally |
| db up | `docker compose up -d` | Starts the PostgreSQL 16 database service defined in docker-compose.yml |
<!-- sdlc:auto:end run -->

<!-- sdlc:auto:start structure -->
| Path | Purpose |
|---|---|
| `backend` | FastAPI service: app package (main, database, models, schemas, routers), tests, requirements, Dockerfile |
| `backend/app` | Application code: entrypoint (main.py), DB engine/session setup (database.py), SQLAlchemy models, Pydantic schemas, routers package |
| `backend/tests` | Pytest suite, split into unit/ and integration/ (e.g. health check test) |
| `frontend` | Vite + React 19 SPA: approved screens, shared UI/icon libraries, API client stub, e2e tests, build/lint/test config |
| `frontend/src` | Application source: entrypoint (main.tsx), shared lib (api.ts, ui.tsx, icons.tsx, navigate.ts), global styles, test setup |
| `frontend/e2e` | Playwright end-to-end specs and support helpers |
| `.devcontainer` | Dev container configuration for a consistent local environment |
| `.quorq` | Platform metadata (handoff.json) used by the Quorq SDLC tooling |
| `docker-compose.yml` | Defines the local PostgreSQL 16 database service |
<!-- sdlc:auto:end structure -->

<!-- sdlc:auto:start conventions -->
- Backend routes are organized as one router per architecture component under backend/app/routers, with one route per API-spec endpoint
- Unimplemented backend routes return a typed StubResponse (schemas.py) rather than raising, keeping OpenAPI complete before handlers exist
- SQLAlchemy models all inherit the shared Base from app.database; app.models is imported in main.py before create_all so tables register
- Database prepared in the FastAPI lifespan handler, not at import time, so importing the app never opens a connection
- DATABASE_URL env var selects the database (SQLite file by default, Postgres/etc. in deployment) with no code changes required
- CORS origins are configured via the ALLOWED_ORIGINS env var (comma-separated), falling back to local Vite dev origins
- Backend code style/linting enforced via ruff (ruff.toml)
- Frontend screens live one module per approved screen, written against the shared src/lib/ui.tsx and icons.tsx vocabulary
- Frontend API access is centralized in src/lib/api.ts (apiFetch) with bearer-token auth (session token from localStorage, falling back to VITE_API_PROJECT_ID); screens currently use seeded sample data instead of real calls
- Frontend styling via Tailwind CSS (v4) with CSS variables in index.css for brand tokens
- Frontend linting via ESLint flat config (eslint.config.js) and formatting via Prettier (.prettierrc)
<!-- sdlc:auto:end conventions -->

<!-- sdlc:auto:start testing -->
| Name | Command | Description |
|---|---|---|
| backend unit/integration tests | `pytest` | Runs the backend test suite (tests/unit, tests/integration) from the backend/ directory |
| backend lint | `ruff check .` | Lints the backend codebase |
| backend format | `ruff format .` | Formats backend code |
| frontend unit tests | `npm run test` | Runs Vitest component tests under src/ |
| frontend typecheck | `npm run typecheck` | Runs tsc --noEmit; not run by npm run build |
| frontend lint | `npm run lint` | Runs ESLint over the whole frontend app |
| frontend format check | `npm run format:check` | Checks formatting with Prettier without writing changes |
| frontend e2e install | `npm run test:e2e:install` | Installs the Chromium browser needed by Playwright |
| frontend e2e tests | `npm run test:e2e` | Runs Playwright acceptance tests from e2e/; without E2E_BASE_URL it boots the backend (from backend/.venv) and builds/serves the frontend itself |
<!-- sdlc:auto:end testing -->

<!-- sdlc:auto:start troubleshooting -->
| Problem | Solution |
|---|---|
| Frontend requests to the backend are blocked by the browser (CORS error) | Set the ALLOWED_ORIGINS environment variable on the backend to include the frontend's origin, or run both on the default local ports (5173 for Vite, 8000 for the API) which are allowed by default |
| Backend data doesn't persist across environments or you need Postgres instead of the default SQLite file | Set the DATABASE_URL environment variable (e.g. to the docker-compose Postgres service) before starting the backend; no code changes are needed |
| `npm run test:e2e` fails to start the backend | Ensure the backend's virtual environment is created and dependencies installed at backend/.venv (pip install -r backend/requirements.txt), since Playwright's webServer config runs backend/.venv/bin/python directly |
| `npm run build` succeeds but deployment or CI fails on type errors | Run `npm run typecheck` (tsc --noEmit) separately, since the build step does not typecheck |
| Playwright tests fail because no browser is installed | Run `npm run test:e2e:install` once before running `npm run test:e2e` |
<!-- sdlc:auto:end troubleshooting -->

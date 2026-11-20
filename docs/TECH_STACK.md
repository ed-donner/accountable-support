# Tech stack

This project uses the same technical stack as Accountable:

1. Node.js 26, the current LTS (24 or later works) / TypeScript for the frontend, using React and Vite, in `frontend/`
2. Python 3.12 for the backend using uv, with FastAPI, in `backend/`, with `pyproject.toml` and `uv.lock` at the repo root

The frontend gets its data from the backend's JSON API. The backend uses SQLAlchemy Core with a SQLite file and fills a new database with the sample data. Prefer popular, well-supported libraries to custom code, such as for the charts.

Commands are npm scripts in a `package.json` at the repo root, with `frontend/` as an npm workspace, so they work the same on Mac, Linux and Windows:

- `npm run dev` fetches whatever is missing on the first run, then starts the backend and frontend together and prints the app's address
- `npm test` runs all the tests and fails if any test fails
- `npm run check:quick` runs the type checks and the unit tests, without the end-to-end tests
- `npm run seed` resets the database to the sample data, after asking

Testing will cover unit tests for the frontend with Vitest, unit tests for the backend with pytest, and end-to-end tests in `e2e/` with Playwright Test and the installed Google Chrome. The tests start the app themselves and use databases of their own.

On every push to any branch, GitHub Actions runs `npm run check:quick` from `.github/workflows/ci.yml`, on Node 26 with uv installed. CI leaves out the end-to-end tests.

## Ports

Support runs alongside Accountable and Accountable Status on the same computer, so it has ports of its own:

- Frontend: 5180
- Backend: 8780

# Sarnami Bol Naa

A Progressive Web App for learning Sarnami — a Hindi-derived language spoken in Suriname — through gamified, bite-sized lessons.

## Features

- **Structured lessons** — Unit 1 covers greetings, pronouns, family nouns, and basic sentences
- **5 exercise types** — multiple choice, word bank, fill-in-the-blank, matching, and flashcards
- **Spaced repetition** — Leitner system schedules vocab reviews at increasing intervals
- **Gamification** — XP, streaks, hearts (lives), stars, and milestone badges
- **PWA** — installable, offline-capable, works on mobile

## Prerequisites

- [Node.js](https://nodejs.org/) v22+ (install via [nvm](https://github.com/nvm-sh/nvm))

## Getting started

```bash
# Install dependencies
npm install

# Start the dev server (http://localhost:5173)
npm run dev
```

## Available scripts

| Script | Description |
|---|---|
| `npm run dev` | Start Vite dev server with hot reload |
| `npm run build` | Type-check and produce a production build in `dist/` |
| `npm run preview` | Serve the production build locally |
| `npm run typecheck` | Run TypeScript type-checking without emitting |
| `npm test` | Run unit tests (Vitest) |
| `npm run test:e2e` | Run Playwright end-to-end visual tests (requires a build first) |
| `npm run lint` | Lint with ESLint |

## Running end-to-end tests

E2E tests use [Playwright](https://playwright.dev/) and need a production build:

```bash
npm run build
npx playwright install chromium --with-deps
npm run test:e2e
```

## Project structure

```
src/
├── components/       # UI components (exercises, HUD, layout, feedback)
├── data/             # Static content — units, vocab, badge definitions
├── domain/           # Pure business logic (gamification, Leitner, types)
├── hooks/            # React hooks for lesson sessions, review queue, content
├── routes/           # Page-level route components
├── services/         # Repository interfaces + localStorage / HTTP implementations
├── state/            # React context for global progress state
└── i18n/             # Dutch UI strings
e2e/                  # Playwright visual tests
```

## Deployment

Merging to `main` triggers a GitHub Actions workflow that builds the app and deploys it to the Hetzner webspace at `/public_html/sarnami_bol/` via FTPS. Required repository secrets: `FTP_SERVER`, `FTP_USERNAME`, `FTP_PASSWORD`.

## Tech stack

- [React 18](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vitejs.dev/) + [vite-plugin-pwa](https://vite-pwa-org.netlify.app/)
- [Tailwind CSS](https://tailwindcss.com/)
- [React Router](https://reactrouter.com/)
- [FontAwesome 6](https://fontawesome.com/) (free solid icons)
- [Vitest](https://vitest.dev/) + [Playwright](https://playwright.dev/) for testing

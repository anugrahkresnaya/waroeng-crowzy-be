# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

NestJS 12 + TypeScript backend for Warung Hidup. It is the future `apps/api` from `../docs/PRD.md`: accounts, cloud saves, leaderboards, score verification by replaying recorded commands, and an AI-chat proxy. These come after the offline game phases, so the game itself must never depend on this service. The code is still the Nest starter (`AppController`/`AppService`).

## Commands (pnpm)

- `pnpm start:dev`: run with watch (port 3000, or `PORT`)
- `pnpm build` / `pnpm start:prod`
- `pnpm lint`: oxlint with type-aware rules; `no-floating-promises` is an error
- `pnpm format`: prettier
- `pnpm test`: Vitest unit tests (`**/*.spec.ts`)
- Single test: `pnpm vitest run src/app.controller.spec.ts` or `pnpm vitest run -t "name"`
- `pnpm test:e2e`: uses `vitest.config.e2e.ts`; files are `test/*.e2e-spec.ts`

## Gotchas

- ESM (`"type": "module"`): relative imports need the `.js` extension (`import { AppModule } from './app.module.js'`), and `main.ts` uses top-level await.
- Tests use Vitest, not Jest. Vitest resolves tsconfig path aliases through `resolve.tsconfigPaths` (requires Vite 8).
- Linting is oxlint, not ESLint.

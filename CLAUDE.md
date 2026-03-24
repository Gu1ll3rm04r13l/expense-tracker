# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install       # Install dependencies
npm run dev       # Start dev server at http://localhost:5173
npm run build     # Production build
npm run lint      # Run ESLint
npm run preview   # Preview production build
```

> Requires Node.js 20.19+ or 22.12+ (Vite 7 incompatible with Node 18).

## Architecture

This is a single-file React app — all logic lives in [src/App.jsx](src/App.jsx). There are no separate components, routing, or backend; state is in-memory only (no persistence).

**Transaction data shape:**
```js
{ id, description, amount, type: "income"|"expense", category, date }
```

**Known issues (intentional for the course):**
- `amount` is stored as a string, causing string concatenation instead of numeric addition in the income/expense/balance totals.
- The UI has styling and layout issues.
- Code is not split into components.

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

React app with no routing or backend; state is in-memory only (no persistence).

**Component tree:**
- `App` — holds the `transactions` array in state, passes data and callbacks down
  - `Summary` — receives `transactions`, computes and displays totals (income, expenses, balance)
  - `TransactionForm` — owns its own form state, calls `onAdd(transaction)` prop on submit
  - `TransactionList` — owns filter state, receives `transactions` and renders the filtered table

**Transaction data shape:**
```js
{ id, description, amount: number, type: "income"|"expense", category, date }
```

Categories are defined as a constant in both `TransactionForm` and `TransactionList`: `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

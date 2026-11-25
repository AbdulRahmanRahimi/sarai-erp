# SARAI ERP: Waheed Ghani

> **Client project** · Built by [Rahimi Tech Solution](https://github.com/rahimiabdulrahmanab) · The source code is private to the client.

A dual-currency (AFN ؋ / USD $), bilingual (English / Pashto) **double-entry ERP** for a cooking-oil and sugar import and distribution business that imports from Malaysia into Afghanistan.

## What it covers

- **Financial core**: double-entry accounting in two currencies
- **Parties and products**: suppliers, customers and the product catalogue
- **Purchasing, orders and receiving**
- **Warehouses (سرای) and dispatch**
- **Sarafs**: separate ledgers for the money exchangers the business works with
- **Roznamcha**: the daily cash book for physical drawer cash
- **Expenses**, data integrity checks and user administration

## Engineering highlights

- **Accounting rules enforced in the database.** Every financial event is a balanced journal entry, and a trigger rejects any posting that does not balance **per currency**.
- **Posted documents are immutable.** Corrections are made with reversal entries, never by editing.
- **Exact money.** Every amount is `NUMERIC(18,4)`, with no floating point anywhere.
- **Warehouse isolation through PostgreSQL Row Level Security.** Warehouse users can only ever see their own warehouse, and this is enforced by the database rather than the UI.
- **Append-only audit log** on every business table.
- An automated SQL test suite covers journal balance, immutability, RLS isolation, the posting functions and an end-to-end scenario.

## Tech stack

| Layer | Tools |
|---|---|
| Frontend | Next.js (App Router), TypeScript (strict), Tailwind CSS, TanStack Table & Query, React Hook Form + Zod |
| Database | Supabase: PostgreSQL, PL/pgSQL posting functions, triggers, Row Level Security, Auth |
| Hosting | Vercel |

---

Designed, built and deployed by **Abdul Rahman Rahimi**.

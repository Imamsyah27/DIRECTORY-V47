# React Customer Dashboard — Phase 1

This folder contains the first React redesign for the customer portal dashboard. The existing `pelanggan/` portal remains intact so the current login and legacy feature modules are not overwritten during the first migration step.

## Stack
- React + Vite
- Supabase JS v2 (uses the existing `customer_login` session token and `get_my_orders` RPC)
- Framer Motion for subtle entrance/hover transitions
- Recharts dependency is included for upcoming chart migration
- Lucide React icons

## Run locally
```bash
cd pelanggan-react
npm install
npm run dev
```

The Supabase URL and public anon key default to the current values from `../pelanggan/config.js`. For a deployment-specific setup, create `.env.local` using `.env.example` and set `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`.

## Session and migration notes
- Sign in using the existing portal at `../pelanggan/index.html` on the same origin, then open this React app. The app reads the existing `pelanggan_session_token` and `pelanggan_username` from local storage (and supports the admin-view session token).
- The React dashboard uses the existing `get_my_orders` and `customer_logout` RPCs. It does not change SQL schema or customer data.
- The `Portal lengkap` button opens the original dashboard so all existing modules remain available during this initial dashboard-only migration. Other menu links currently open the original portal; those modules are not migrated to React in this phase.
- Do not remove the old portal until the React dashboard has been tested in the target hosting environment and remaining modules have been migrated.

## Design references researched
- SaaSUI analytics dashboard patterns: https://www.saasui.design/analytics-dashboard-design-examples
- Codec Factory SaaS analytics dashboard concept: https://www.codecfactory.com/portfolio/concept-saas-analytics-dashboard-ui
- shadcn/ui dashboard blocks: https://pro.shadcn.co/pro-blocks/application-dashboard

The design adapts common SaaS patterns—compact sidebar navigation, clear KPI cards, a primary progress hero, status-aware table rows, responsive layout, restrained gradients, and reduced-motion support—to the existing customer portal menu and subscription monitoring workflow.

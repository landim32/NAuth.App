# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

NAuth.App is the frontend web application for the NAuth authentication ecosystem. It's a React SPA that demonstrates and consumes the [nauth-react](https://github.com/landim32/NAuth.React) component library, backed by the [NAuth.API](https://github.com/landim32/NAuth.API) REST API.

## Commands

```bash
npm run dev          # Start Vite dev server (http://localhost:5173)
npm run build        # TypeScript type-check + Vite production build
npm run lint         # ESLint on .ts/.tsx files
npm run type-check   # TypeScript type-check only (tsc --noEmit)
npm run preview      # Serve the built dist/ locally
```

Docker build: `docker build -t nauth-app . && docker run -p 80:80 nauth-app`

No test framework is configured.

## Environment

Requires Node.js 18+ and a running NAuth.API backend. Copy `.env.example` to `.env` and set:

```
VITE_API_URL=http://localhost:5004
```

## Architecture

**Stack:** React 19, TypeScript 5.9, Vite 7, Tailwind CSS 3, React Router 7

**Path alias:** `@` maps to `./src` (configured in vite.config.ts and tsconfig)

### Key Patterns

- **Auth provider:** `NAuthProvider` from `nauth-react` wraps the entire app in [App.tsx](src/App.tsx). All auth forms (login, register, forgot/reset password, user edit) come from this library — the app provides page-level wrappers around them.
- **Route protection:** [ProtectedRoute](src/components/ProtectedRoute.tsx) checks `useAuth()` hook state; unauthenticated users are redirected to `/login` with the intended destination stored in `sessionStorage`.
- **Routing:** All routes are defined in [App.tsx](src/App.tsx) as flat routes inside a `<Layout>` wrapper. Route path constants live in [src/lib/constants.ts](src/lib/constants.ts).
- **Layout:** [Layout.tsx](src/components/Layout.tsx) renders a conditional [Navbar](src/components/Navbar.tsx) (auth-aware) plus `<Outlet>` for nested content.
- **Styling:** Tailwind with class-based dark mode, custom HSL CSS variables for theming (defined in [index.css](src/index.css)), and `cn()` utility ([src/lib/utils.ts](src/lib/utils.ts)) for merging class names via `clsx` + `tailwind-merge`. Tailwind config also scans `nauth-react` dist for classes.
- **Notifications:** `sonner` Toaster component for toast messages.

### Source Layout

- `src/pages/` — One file per page. Public pages: Home, Login, Register, ForgotPassword, ResetPassword. Protected pages: Dashboard, Profile, ChangePassword, SearchUsers, Roles, UserEdit.
- `src/components/` — Layout shell, Navbar, ProtectedRoute, UserMenu, and `ui/` for reusable primitives (Card).
- `src/lib/` — `constants.ts` (route paths, app metadata) and `utils.ts` (cn helper).

## Ecosystem

This app is one part of the NAuth ecosystem. The core backend is NAuth.API (.NET). Shared types are in NAuth.DTO (NuGet). The .NET HTTP client is NAuth.ACL. The React component library consumed here is nauth-react (NPM).

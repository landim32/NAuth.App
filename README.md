# NAuth.App

![React](https://img.shields.io/badge/React-19-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue)
![Vite](https://img.shields.io/badge/Vite-7-purple)
![License](https://img.shields.io/badge/License-MIT-green)

Frontend web application for the [NAuth](https://github.com/landim32/NAuth.API) authentication ecosystem. Built with React, TypeScript, Tailwind CSS, and the [nauth-react](https://github.com/landim32/NAuth.React) component library.

> **Part of the NAuth ecosystem** — see [NAuth.API](https://github.com/landim32/NAuth.API) for the main project and full documentation.

## Features

- User login, registration, and password recovery
- User profile management and editing
- User search with pagination
- Role management (CRUD)
- Protected routes with authentication guards
- Light/Dark theme support
- Responsive, mobile-first design

## Tech Stack

- **React 19** + **TypeScript 5.9**
- **Vite 7** — dev server and build tool
- **nauth-react** — authentication component library
- **Tailwind CSS 3** — utility-first styling
- **React Router 7** — client-side routing
- **Lucide React** — icons
- **Sonner** — toast notifications

## Quick Start

### Prerequisites

- Node.js 18+
- A running [NAuth.API](https://github.com/landim32/NAuth.API) backend

### Setup

```bash
# Install dependencies
npm install

# Copy environment file and configure the API URL
cp .env.example .env
```

Edit `.env` and point to your NAuth API:

```env
VITE_API_URL=http://localhost:5004
```

### Development

```bash
npm run dev
```

### Build

```bash
npm run build
```

### Preview production build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/       # Layout, Navbar, ProtectedRoute, UI
├── pages/            # Application pages
│   ├── HomePage.tsx
│   ├── LoginPage.tsx
│   ├── RegisterPage.tsx
│   ├── DashboardPage.tsx
│   ├── ProfilePage.tsx
│   ├── UserEditPage.tsx
│   ├── SearchUsersPage.tsx
│   ├── ChangePasswordPage.tsx
│   ├── ForgotPasswordPage.tsx
│   ├── ResetPasswordPage.tsx
│   └── RolesPage.tsx
├── lib/              # Constants and utilities
└── App.tsx           # Routes and providers
```

## Docker

```bash
docker build -t nauth-app .
docker run -p 80:80 nauth-app
```

The Dockerfile uses Nginx to serve the built application.

## Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start Vite dev server |
| `npm run build` | Type-check and build for production |
| `npm run preview` | Preview production build locally |
| `npm run lint` | Run ESLint |
| `npm run type-check` | TypeScript type checking |

## NAuth Ecosystem

This application is part of the **NAuth** ecosystem. The main project is [NAuth.API](https://github.com/landim32/NAuth.API).

| Project | Description |
|---------|-------------|
| **[NAuth.API](https://github.com/landim32/NAuth.API)** | Central REST API backend (main project) |
| **[NAuth.DTO](https://github.com/landim32/NAuth.DTO)** | Shared Data Transfer Objects (NuGet) |
| **[NAuth.ACL](https://github.com/landim32/NAuth.ACL)** | HTTP client library (NuGet) |
| **[NAuth.React](https://github.com/landim32/NAuth.React)** | React component library (NPM) |
| **NAuth.App** | Frontend web application — you are here |

## License

MIT © [Rodrigo Landim](https://github.com/landim32)

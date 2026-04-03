# Next.js App — Agent Instructions

**Copy this file to your Next.js project root and customize it.**

## Project Overview
- **Type:** Next.js Full-Stack App (TypeScript + React)
- **Root:** [Your project path - e.g., D:\projects\my-nextjs-app]
- **Framework Version:** [Version - e.g., 15.x]
- **Router:** App Router (src/app)
- **Port:** 3000 (`npm run dev`)
- **Styling:** [Tailwind/CSS Modules/etc]

## Architecture

### Directory Structure
```
src/
├── app/                         # App Router pages & layouts
│   ├── (auth)/                  # Route group
│   │   ├── login/page.tsx
│   │   └── register/page.tsx
│   ├── dashboard/
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── api/                     # API routes
│   │   ├── auth/route.ts
│   │   └── resources/route.ts
│   ├── layout.tsx               # Root layout
│   └── page.tsx                 # Home page
├── components/                  # Reusable components
│   ├── ui/                      # Atomic components
│   └── features/                # Feature components
├── lib/                         # Utilities
│   ├── api.ts                   # API client
│   ├── auth.ts                  # Auth utilities
│   └── db.ts                    # Database setup
├── hooks/                       # Custom hooks
│   ├── useAuth.ts
│   └── useFetch.ts
├── types/                       # TypeScript types
│   └── index.ts
└── middleware.ts                # Next.js middleware (auth, etc)
```

### Key Concepts

#### Server Components (Default)
```typescript
// src/app/dashboard/page.tsx
export default async function Dashboard() {
  // Can access database directly
  const data = await db.resource.findMany();

  return <div>{/* Render data */}</div>;
}
```

#### Client Components
```typescript
'use client'; // Must be at top

import { useState } from 'react';

export default function Counter() {
  const [count, setCount] = useState(0);
  // Can use hooks here
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

#### API Routes
```typescript
// src/app/api/resources/route.ts
export async function GET(request: Request) {
  const resources = await db.resource.findMany();
  return Response.json({ data: resources });
}

export async function POST(request: Request) {
  const body = await request.json();
  const resource = await db.resource.create({ data: body });
  return Response.json({ data: resource }, { status: 201 });
}
```

## Data Fetching Strategy

### Server-Side Fetching
```typescript
// Preferred for SEO, security, initial data
export default async function Page() {
  const data = await fetch('http://localhost:3000/api/resource', {
    cache: 'revalidate', // ISR: revalidate every X seconds
  });
  return <Component data={data} />;
}
```

### Client-Side Fetching
```typescript
'use client';

import { useEffect, useState } from 'react';

export default function Component() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/resource')
      .then(res => res.json())
      .then(data => setData(data));
  }, []);

  return <div>{data && <p>{data.name}</p>}</div>;
}
```

### Incremental Static Regeneration (ISR)
```typescript
export const revalidate = 60; // Revalidate every 60s

export default async function Page() {
  // This page will be regenerated every 60 seconds
  const data = await db.resource.findMany();
  return <Component data={data} />;
}
```

## Styling

### Tailwind CSS (if applicable)
```typescript
export default function Button() {
  return (
    <button className="bg-blue-500 hover:bg-blue-700 text-white px-4 py-2 rounded">
      Click me
    </button>
  );
}
```

### CSS Modules
```typescript
// component.tsx
import styles from './component.module.css';

export default function Component() {
  return <div className={styles.container}>{/* content */}</div>;
}
```

## Common Tasks

### Create a New Page

1. **Create route directory:**
```bash
mkdir -p src/app/feature
```

2. **Create page component:**
```typescript
// src/app/feature/page.tsx
import { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'Feature Page',
  description: 'Feature description',
};

export default async function FeaturePage() {
  const data = await fetch('http://localhost:3000/api/feature').then(r => r.json());

  return (
    <main className="container mx-auto py-8">
      <h1>Feature</h1>
      {/* Render data */}
    </main>
  );
}
```

3. **Create layout (if needed):**
```typescript
// src/app/feature/layout.tsx
export default function FeatureLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div className="feature-layout">
      <nav>{/* Navigation */}</nav>
      {children}
    </div>
  );
}
```

### Create an API Route

1. **Create route file:**
```typescript
// src/app/api/feature/route.ts
import { NextRequest, NextResponse } from 'next/server';

export async function GET(request: NextRequest) {
  try {
    const resources = await db.feature.findMany();
    return NextResponse.json({ data: resources });
  } catch (error) {
    return NextResponse.json(
      { error: 'Failed to fetch' },
      { status: 500 }
    );
  }
}

export async function POST(request: NextRequest) {
  try {
    const body = await request.json();
    const resource = await db.feature.create({ data: body });
    return NextResponse.json({ data: resource }, { status: 201 });
  } catch (error) {
    return NextResponse.json(
      { error: 'Failed to create' },
      { status: 400 }
    );
  }
}
```

### Create a Custom Hook

```typescript
// src/hooks/useFeature.ts
'use client';

import { useEffect, useState } from 'react';

export function useFeature(id: string) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(`/api/feature/${id}`)
      .then(res => res.json())
      .then(data => {
        setData(data);
        setLoading(false);
      })
      .catch(err => {
        setError(err);
        setLoading(false);
      });
  }, [id]);

  return { data, loading, error };
}
```

### Create a Component

```typescript
// src/components/features/FeatureCard.tsx
interface FeatureCardProps {
  feature: Feature;
  onSelect: (id: string) => void;
}

export function FeatureCard({ feature, onSelect }: FeatureCardProps) {
  return (
    <div className="card p-4 border rounded">
      <h3>{feature.name}</h3>
      <p>{feature.description}</p>
      <button onClick={() => onSelect(feature.id)}>
        Select
      </button>
    </div>
  );
}
```

## Testing

### Unit Tests (with Jest)
```typescript
import { render, screen } from '@testing-library/react';
import { Component } from './component';

describe('Component', () => {
  it('renders text', () => {
    render(<Component />);
    expect(screen.getByText('Hello')).toBeInTheDocument();
  });
});
```

### E2E Tests (with Playwright)
```typescript
import { test, expect } from '@playwright/test';

test('can navigate to feature page', async ({ page }) => {
  await page.goto('http://localhost:3000/feature');
  await expect(page).toHaveTitle(/Feature/);
});
```

## Authentication (if applicable)

### Middleware for Protected Routes
```typescript
// src/middleware.ts
import { NextRequest, NextResponse } from 'next/server';

export function middleware(request: NextRequest) {
  const token = request.cookies.get('auth-token');

  if (!token && request.nextUrl.pathname.startsWith('/dashboard')) {
    return NextResponse.redirect(new URL('/login', request.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ['/dashboard/:path*', '/admin/:path*'],
};
```

## Deployment (Vercel)

### Environment Variables
```bash
# .env.local (local development, ignored by git)
# .env.production (production environment)
NEXT_PUBLIC_API_URL=https://api.example.com
SECRET_KEY=your-secret-key
```

### Deploy Commands
```bash
npm run build         # Build for production
npm start             # Start production server

# Or use Vercel:
vercel deploy         # Deploy to Vercel
```

## Run Commands

```bash
# Development
npm run dev                     # Start dev server (port 3000)
npm run build                  # Build for production
npm start                      # Start production server

# Testing
npm test                       # Run unit tests
npm run test:watch             # Watch mode
npm run test:e2e               # Run E2E tests

# Linting & Formatting
npm run lint                   # Run ESLint
npm run lint:fix               # Fix linting issues
npm run format                 # Format code (if Prettier configured)

# Type Checking
npm run type-check             # Check TypeScript

# Database (if using Prisma)
npx prisma migrate dev --name name  # Create migration
npx prisma generate           # Generate Prisma client
```

## Before Committing

Checklist:
- [ ] All components have TypeScript types
- [ ] Server/Client components marked correctly
- [ ] API routes have error handling
- [ ] Metadata set for pages (SEO)
- [ ] Tests pass: `npm test`
- [ ] No console errors or warnings
- [ ] Environmental variables configured
- [ ] Links use Next.js Link component (not `<a>`)
- [ ] Images use Next.js Image component
- [ ] No hardcoded API URLs (use env vars)

## Code Review Criteria

✅ **Good:**
- Server Components for data fetching
- Proper use of client components with 'use client'
- Error boundaries for error handling
- Type-safe API routes
- Tests for components
- Responsive design with Tailwind

❌ **Issues:**
- Over-use of client components
- Missing error handling in API routes
- Hardcoded URLs or credentials
- Missing metadata for pages
- No types on props
- Unoptimized images

---

**Update this file as your application evolves!**

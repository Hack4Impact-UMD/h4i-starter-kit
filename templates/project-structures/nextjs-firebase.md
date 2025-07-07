# Next.js + Firebase Project Structure

This template provides a recommended project structure for Next.js applications using Firebase as the backend.

## Directory Structure

```
your-project/
├── .github/                    # GitHub workflows and templates
│   ├── workflows/
│   │   └── ci.yml             # CI/CD pipeline
│   └── pull_request_template.md
├── src/
│   ├── app/                   # Next.js App Router (Next.js 13+)
│   │   ├── (auth)/           # Route groups
│   │   │   ├── login/
│   │   │   └── register/
│   │   ├── dashboard/
│   │   │   ├── page.tsx
│   │   │   └── layout.tsx
│   │   ├── api/              # API routes
│   │   │   ├── auth/
│   │   │   └── users/
│   │   ├── globals.css       # Global styles
│   │   ├── layout.tsx        # Root layout
│   │   ├── page.tsx          # Home page
│   │   └── loading.tsx       # Loading UI
│   ├── components/           # Reusable UI components
│   │   ├── common/          # Shared components
│   │   │   ├── Button/
│   │   │   ├── Input/
│   │   │   └── index.ts
│   │   ├── layout/          # Layout components
│   │   │   ├── Header/
│   │   │   ├── Footer/
│   │   │   └── Sidebar/
│   │   └── index.ts
│   ├── hooks/               # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useFirestore.ts
│   │   └── index.ts
│   ├── lib/                 # Utility libraries
│   │   ├── firebase.ts      # Firebase configuration
│   │   ├── auth.ts          # Authentication logic
│   │   ├── db.ts            # Database operations
│   │   ├── storage.ts       # File storage operations
│   │   └── utils.ts         # General utilities
│   ├── types/               # TypeScript type definitions
│   │   ├── auth.ts
│   │   ├── user.ts
│   │   ├── api.ts
│   │   └── index.ts
│   ├── styles/              # Additional stylesheets
│   │   ├── components.css
│   │   └── utilities.css
│   └── middleware.ts        # Next.js middleware
├── functions/               # Firebase Cloud Functions
│   ├── src/
│   │   ├── auth/           # Authentication functions
│   │   ├── api/            # API endpoints
│   │   ├── triggers/       # Database triggers
│   │   ├── utils/          # Utility functions
│   │   └── index.ts        # Functions entry point
│   ├── package.json
│   └── tsconfig.json
├── public/                  # Static assets
│   ├── images/
│   ├── icons/
│   └── favicon.ico
├── docs/                    # Documentation
│   ├── STARTER_KIT_GUIDE.md
│   ├── API.md
│   └── DEPLOYMENT.md
├── .env.example             # Environment variables example
├── .env.local              # Local environment variables
├── .gitignore
├── firebase.json           # Firebase configuration
├── .firebaserc            # Firebase project configuration
├── firestore.rules        # Firestore security rules
├── storage.rules          # Storage security rules
├── next.config.js         # Next.js configuration
├── package.json
├── tailwind.config.js     # Tailwind CSS configuration (if using)
├── tsconfig.json
└── README.md
```

## Directory Explanations

### `/src/app/` (App Router)
Next.js 13+ App Router structure:
- **Route groups**: `(auth)` for grouping related routes
- **page.tsx**: Page components
- **layout.tsx**: Layout components
- **loading.tsx**: Loading UI components
- **error.tsx**: Error UI components
- **not-found.tsx**: 404 page
- **api/**: API routes (serverless functions)

### `/src/components/`
Reusable UI components organized by scope:
- `common/`: Shared components across the app
- `layout/`: Layout-specific components
- Each component has its own folder with component and styles

### `/src/hooks/`
Custom React hooks for reusable logic:
- `useAuth.ts`: Authentication state management
- `useFirestore.ts`: Firestore operations
- `useLocalStorage.ts`: Browser storage

### `/src/lib/`
Utility libraries and configurations:
- `firebase.ts`: Firebase SDK initialization
- `auth.ts`: Authentication utilities
- `db.ts`: Database operations
- `utils.ts`: General utility functions

### `/src/types/`
TypeScript type definitions:
- Organized by domain (auth, user, api)
- Shared interfaces and types

### `/functions/`
Firebase Cloud Functions:
- `auth/`: Authentication-related functions
- `api/`: HTTP API endpoints
- `triggers/`: Database triggers

## App Router vs Pages Router

### App Router (Recommended for new projects)
```
src/app/
├── page.tsx              # Home page
├── layout.tsx            # Root layout
├── dashboard/
│   ├── page.tsx         # Dashboard page
│   └── layout.tsx       # Dashboard layout
└── api/
    └── users/
        └── route.ts     # API endpoint
```

### Pages Router (Legacy)
```
src/pages/
├── index.tsx            # Home page
├── dashboard.tsx        # Dashboard page
├── _app.tsx            # App component
├── _document.tsx       # Document component
└── api/
    └── users.ts        # API endpoint
```

## File Naming Conventions

- **Pages**: `page.tsx` (App Router) or `ComponentName.tsx` (Pages Router)
- **Components**: PascalCase (e.g., `UserProfile.tsx`)
- **Utilities**: camelCase (e.g., `userService.ts`)
- **API Routes**: `route.ts` (App Router) or `endpoint.ts` (Pages Router)

## Usage Examples

### App Router Page
```tsx
// src/app/dashboard/page.tsx
import { Button } from '@/components/common';
import { useAuth } from '@/hooks';

export default function DashboardPage() {
  return (
    <div>
      <h1>Dashboard</h1>
      <Button variant="primary">Get Started</Button>
    </div>
  );
}
```

### API Route (App Router)
```tsx
// src/app/api/users/route.ts
import { NextRequest, NextResponse } from 'next/server';
import { db } from '@/lib/firebase';

export async function GET(request: NextRequest) {
  const users = await db.collection('users').get();
  return NextResponse.json(users.docs.map(doc => doc.data()));
}
```

### Custom Hook
```tsx
// src/hooks/useAuth.ts
import { useAuthState } from 'react-firebase-hooks/auth';
import { auth } from '@/lib/firebase';

export const useAuth = () => {
  const [user, loading, error] = useAuthState(auth);
  
  return {
    user,
    loading,
    error,
    signOut: () => auth.signOut(),
  };
};
```

## Next.js Configuration

### next.config.js
```javascript
/** @type {import('next').NextConfig} */
const nextConfig = {
  experimental: {
    appDir: true, // Enable App Router
  },
  images: {
    domains: ['firebasestorage.googleapis.com'],
  },
  env: {
    FIREBASE_PROJECT_ID: process.env.FIREBASE_PROJECT_ID,
  },
};

module.exports = nextConfig;
```

### Path Mapping (tsconfig.json)
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"],
      "@/components/*": ["./src/components/*"],
      "@/lib/*": ["./src/lib/*"],
      "@/hooks/*": ["./src/hooks/*"]
    }
  }
}
```

## Best Practices

1. **Use App Router**: For new projects, use the App Router for better performance
2. **Server Components**: Leverage Server Components for better performance
3. **Route Groups**: Organize routes logically with route groups
4. **TypeScript**: Use TypeScript for type safety
5. **Path Aliases**: Configure path aliases for cleaner imports
6. **Environment Variables**: Use `.env.local` for environment-specific configs
7. **Middleware**: Use middleware for authentication and redirects
8. **Error Boundaries**: Implement error boundaries for better error handling

## Environment Setup

1. **Create Next.js app**:
   ```bash
   npx create-next-app@latest my-app --typescript --tailwind --app
   ```

2. **Install Firebase**:
   ```bash
   npm install firebase
   ```

3. **Firebase tools**:
   ```bash
   npm install -g firebase-tools
   firebase init
   ```

4. **Additional dependencies**:
   ```bash
   npm install react-firebase-hooks
   npm install -D @types/node
   ```

## Deployment

### Vercel
```bash
npm install -g vercel
vercel
```

### Firebase Hosting
```bash
npm run build
firebase deploy
```

This structure provides a robust foundation for scalable Next.js applications with Firebase integration, taking advantage of the latest Next.js features and best practices. 
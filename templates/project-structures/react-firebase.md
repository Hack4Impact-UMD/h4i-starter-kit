# React + Firebase Project Structure

This template provides a recommended project structure for React applications using Firebase as the backend.

## Directory Structure

```
your-project/
├── .github/                    # GitHub workflows and templates
│   ├── workflows/
│   │   └── ci.yml             # CI/CD pipeline
│   └── pull_request_template.md
├── src/
│   ├── components/             # Reusable UI components
│   │   ├── common/            # Shared components across the app
│   │   │   ├── Button/
│   │   │   ├── Input/
│   │   │   └── index.ts
│   │   ├── layout/            # Layout components
│   │   │   ├── Header/
│   │   │   ├── Footer/
│   │   │   └── Sidebar/
│   │   └── index.ts
│   ├── pages/                 # Page components
│   │   ├── Home/
│   │   ├── Dashboard/
│   │   ├── Profile/
│   │   └── index.ts
│   ├── hooks/                 # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useFirestore.ts
│   │   └── index.ts
│   ├── services/              # API services and business logic
│   │   ├── auth.ts
│   │   ├── firestore.ts
│   │   ├── storage.ts
│   │   └── index.ts
│   ├── utils/                 # Utility functions
│   │   ├── helpers.ts
│   │   ├── constants.ts
│   │   ├── validation.ts
│   │   └── index.ts
│   ├── types/                 # TypeScript type definitions
│   │   ├── auth.ts
│   │   ├── user.ts
│   │   ├── api.ts
│   │   └── index.ts
│   ├── styles/                # Global styles and themes
│   │   ├── globals.css
│   │   ├── variables.css
│   │   └── components.css
│   ├── config/                # Configuration files
│   │   ├── firebase.ts
│   │   ├── environment.ts
│   │   └── index.ts
│   ├── assets/                # Static assets
│   │   ├── images/
│   │   ├── icons/
│   │   └── fonts/
│   ├── App.tsx                # Main App component
│   ├── index.tsx              # React entry point
│   └── index.css              # Global styles
├── functions/                 # Firebase Cloud Functions
│   ├── src/
│   │   ├── auth/              # Authentication functions
│   │   ├── api/               # API endpoints
│   │   ├── triggers/          # Database triggers
│   │   ├── utils/             # Utility functions
│   │   └── index.ts           # Functions entry point
│   ├── package.json
│   └── tsconfig.json
├── public/                    # Static public assets
│   ├── index.html
│   ├── favicon.ico
│   ├── logo192.png
│   └── manifest.json
├── docs/                      # Documentation
│   ├── STARTER_KIT_GUIDE.md
│   ├── API.md
│   └── DEPLOYMENT.md
├── .env.example               # Environment variables example
├── .env.local                 # Local environment variables
├── .gitignore
├── firebase.json              # Firebase configuration
├── .firebaserc               # Firebase project configuration
├── firestore.rules           # Firestore security rules
├── storage.rules             # Storage security rules
├── package.json
├── tsconfig.json
└── README.md
```

## Directory Explanations

### `/src/components/`
Houses all reusable UI components. Organized by scope:
- `common/`: Components used across multiple pages
- `layout/`: Components for page layout structure
- Each component has its own folder with `.tsx` and `.module.css` files

### `/src/pages/`
Contains page-level components that represent different routes/screens in your application.

### `/src/hooks/`
Custom React hooks for reusable stateful logic:
- `useAuth.ts`: Authentication state management
- `useFirestore.ts`: Firestore data operations
- `useLocalStorage.ts`: Browser storage operations

### `/src/services/`
API services and business logic:
- `auth.ts`: Authentication operations
- `firestore.ts`: Database operations
- `storage.ts`: File upload/download operations

### `/src/utils/`
Utility functions and constants:
- `helpers.ts`: General helper functions
- `constants.ts`: Application constants
- `validation.ts`: Form validation functions

### `/src/types/`
TypeScript type definitions organized by domain:
- `auth.ts`: Authentication-related types
- `user.ts`: User data types
- `api.ts`: API response types

### `/src/config/`
Configuration files:
- `firebase.ts`: Firebase initialization
- `environment.ts`: Environment-specific configurations

### `/functions/`
Firebase Cloud Functions organized by purpose:
- `auth/`: Authentication-related functions
- `api/`: HTTP API endpoints
- `triggers/`: Database triggers and scheduled functions

## File Naming Conventions

- **Components**: PascalCase (e.g., `UserProfile.tsx`)
- **Files**: camelCase (e.g., `userService.ts`)
- **Directories**: PascalCase for components, camelCase for others
- **Constants**: UPPER_SNAKE_CASE (e.g., `API_ENDPOINTS`)

## Usage Example

```tsx
// src/pages/Dashboard/Dashboard.tsx
import React from 'react';
import { Button, Input } from '@/components/common';
import { useAuth } from '@/hooks';
import { userService } from '@/services';
import styles from './Dashboard.module.css';

export const Dashboard: React.FC = () => {
  const { user, loading } = useAuth();

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <div className={styles.dashboard}>
      <h1>Welcome, {user?.displayName}!</h1>
      <Button variant="primary">
        Get Started
      </Button>
    </div>
  );
};
```

## Environment Setup

1. **Install dependencies**:
   ```bash
   npm install react react-dom
   npm install -D @types/react @types/react-dom
   ```

2. **Firebase setup**:
   ```bash
   npm install firebase
   firebase init
   ```

3. **Development tools**:
   ```bash
   npm install -D eslint prettier typescript
   ```

This structure provides a solid foundation for scalable React applications with Firebase integration. 
# H4I Starter Kit Guide

Welcome to the Hack4Impact-UMD Starter Kit! This guide will help you get started with building your H4I project using our templates and components.

## 🚀 Quick Start

1. **Clone the starter kit:**
   ```bash
   git clone https://github.com/Hack4Impact-UMD/h4i-starter-kit.git
   cd h4i-starter-kit
   ```

2. **Copy templates to your project:**
   ```bash
   # Copy the README template
   cp templates/README_TEMPLATE.md your-project/README.md
   
   # Copy CI/CD workflows
   cp -r .github/ your-project/.github/
   
   # Copy component library
   cp -r components/ your-project/src/components/
   ```

3. **Customize the templates** (see sections below)

## 📋 README Template

The README template (`templates/README_TEMPLATE.md`) follows H4I's established style and includes:

- **Professional branding** with logo and badges
- **Comprehensive setup guide** for different development environments
- **Project structure** documentation
- **Team contact information**
- **Style guide** references
- **System overview** with tech stack details

### Customization Steps

Replace the following placeholders in the template:

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `[PROJECT_NAME]` | Your project name | `Food For All DC` |
| `[PROJECT_EMOJI]` | Project emoji | `🥗` |
| `[PROJECT_TAGLINE]` | Brief project description | `Modernizing food delivery for our community` |
| `[ORGANIZATION_DESCRIPTION]` | Partner organization description | `A nonprofit dedicated to feeding those in need` |
| `[PATH_TO_LOGO]` | Path to your project logo | `src/assets/logo.png` |
| `[REPOSITORY_URL]` | Your GitHub repository URL | `git@github.com:Hack4Impact-UMD/project.git` |
| `[PROJECT_DIRECTORY]` | Project directory name | `food-for-all-dc` |
| `[FRONTEND_FOLDER]` | Frontend directory name | `my-app` or `src` |
| `[TECH_LEAD_NAME]` | Technical lead name | `John Smith` |
| `[TECH_LEAD_EMAIL]` | Technical lead email | `john.smith@example.com` |
| `[UI_LIBRARY]` | UI framework used | `Material-UI`, `Tailwind CSS` |
| `[BUILD_TOOL]` | Build tool used | `Next.js`, `Vite` |
| `[AUTH_METHODS]` | Authentication methods | `Google, email/password` |
| `[DEPLOYMENT_PLATFORM]` | Deployment platform | `Firebase Hosting` |
| `[PRODUCTION_URL]` | Production URL | `https://your-app.web.app` |
| `[LICENSE_TYPE]` | License type | `MIT` |

## 🔄 CI/CD Workflow

The CI/CD workflow (`.github/workflows/ci.yml`) provides:

- **Multi-environment testing** (frontend, backend, Python)
- **Automatic deployment** on main branch
- **Security scanning** with npm audit and Trivy
- **Flexible job execution** based on commit messages

### Configuration

1. **Set up GitHub Secrets:**
   ```
   FIREBASE_TOKEN - Firebase CLI token
   FIREBASE_PROJECT_ID - Firebase project ID
   ```

2. **Generate Firebase token:**
   ```bash
   firebase login:ci
   # Copy the generated token to GitHub Secrets
   ```

### Workflow Features

- **Skip CI:** Add `[skip ci]` to commit message
- **Skip deployment:** Add `[skip deploy]` to commit message
- **Backend-only CI:** Include `functions` or `backend` in commit message
- **Python CI:** Include `python` in commit message

## 🎨 Component Library

The component library (`components/`) provides reusable UI components:

### Available Components
#### Button Component
### Styling
### Adding New Components

1. **Create component directory:**
   ```
   components/common/ComponentName/
   ├── ComponentName.tsx
   ├── ComponentName.module.css
   └── index.ts
   ```

2. **Follow naming conventions:**
   - PascalCase for component names
   - Descriptive prop names
   - Consistent prop patterns

3. **Include documentation:**
   - JSDoc comments
   - Usage examples
   - Prop descriptions

4. **Export from index:**
   ```tsx
   // components/index.ts
   export * from './common/ComponentName/ComponentName';
   ```

## 📁 Project Structure Templates

### React + Firebase Structure
```
your-project/
├── src/
│   ├── components/          # Reusable components
│   ├── pages/              # Page components
│   ├── hooks/              # Custom hooks
│   ├── services/           # API services
│   ├── utils/              # Utility functions
│   ├── types/              # TypeScript types
│   └── styles/             # Global styles
├── functions/              # Firebase functions
├── public/                 # Static assets
└── .github/               # CI/CD workflows
```

### Next.js + Firebase Structure
```
your-project/
├── src/
│   ├── app/               # Next.js App Router
│   ├── components/        # Reusable components
│   ├── lib/               # Utility libraries
│   └── types/             # TypeScript types
├── functions/             # Firebase functions
├── public/                # Static assets
└── .github/              # CI/CD workflows
```

## 🛠️ Development Workflow

### 1. Initial Setup
```bash
# Clone your project repository
git clone your-repo-url
cd your-project

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your Firebase config
```

### 2. Development
```bash
# Start development server
npm run dev

# Start Firebase emulators
firebase emulators:start

# Run tests
npm test

# Run linter
npm run lint
```

### 3. Deployment
```bash
# Build for production
npm run build

# Deploy to Firebase
firebase deploy
```

## 🎯 Best Practices

### Component Design
- **Keep components focused** on single responsibility
- **Use composition over inheritance**
- **Provide good defaults** for props
- **Include accessibility attributes**

### Documentation
- **Keep README updated** with current setup instructions
- **Document complex business logic**
- **Include examples** in component documentation
- **Update changelog** for significant changes

## 🤝 Contributing

We welcome contributions to improve the starter kit:

1. **Fork the repository**
2. **Create a feature branch**
3. **Make your changes**
4. **Add tests** if applicable
5. **Submit a pull request**

**Contribution guidelines:**
- Follow existing code style
- Update documentation for new features
- Test changes thoroughly
- Keep pull requests focused

---

<div align="center">
  <p><strong>Built with ❤️ by Hack4Impact-UMD</strong></p>
  <p>Empowering nonprofits through technology</p>
</div> 
# H4I Starter Kit Guide

## Copy Templates

```bash
cp templates/README_TEMPLATE.md your-project/README.md
cp -r .github/ your-project/.github/
cp -r components/ your-project/src/components/
```

## README Template Placeholders

Replace these placeholders:

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

## CI/CD Setup

Required GitHub Secrets:
- `FIREBASE_TOKEN` - Get with `firebase login:ci`
- `FIREBASE_PROJECT_ID` - Your Firebase project ID

Commit message controls:
- `[skip ci]` - Skip all CI
- `[skip deploy]` - Skip deployment  
- Include "functions" or "backend" - Trigger backend CI
- Include "python" - Trigger Python CI

## Development Commands

```bash
npm install              # Install dependencies
npm run dev             # Start development server
firebase emulators:start # Start Firebase emulators
npm test                # Run tests
npm run lint            # Run linter
npm run build           # Build for production
firebase deploy         # Deploy to Firebase
``` 
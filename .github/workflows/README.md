# H4I CI/CD Workflows

## Setup

1. Copy workflow: `cp .github/workflows/firebase-nodejs.yml your-project/.github/workflows/`
2. Add GitHub Secrets: `FIREBASE_TOKEN`, `FIREBASE_PROJECT_ID`
3. Push to trigger CI/CD

## Firebase + Node.js (`firebase-nodejs.yml`)

Auto-detects and runs these scripts: `lint`, `type-check`, `test`, `build`

**GitHub Secrets:**
- `FIREBASE_TOKEN` - Get with `firebase login:ci`
- `FIREBASE_PROJECT_ID` - Your Firebase project ID

## Adding New Workflows

Naming: `{platform}-{language}.yml` (e.g., `vercel-nextjs.yml`)

Future workflows: `netlify-react.yml`, `heroku-django.yml`, `aws-lambda-python.yml`

## Commit Controls

- `[skip ci]` - Skip all CI
- `[skip deploy]` - Skip deployment
- Include "functions" or "backend" - Trigger backend CI  
- Include "python" - Trigger Python CI
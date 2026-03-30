# SETUP.md - Getting Started with OpenClaw

This guide contains all the instructions you need to set up your development environment and run the OpenClaw monorepo locally.

## Purpose

`SETUP.md` provides step-by-step instructions for:
- Cloning the repository
- Installing dependencies
- Setting up your local development environment
- Running scripts and tests locally

## When to Use SETUP.md

- **First time cloning the repository** — Follow these steps to install dependencies
- **Setting up your local development environment** — Get your machine ready to develop
- **Running scripts locally** — Learn how to execute and test your code
- **Verifying your setup is correct** — Troubleshoot common issues

## Key Steps

### 1. Clone the Repository

Get a local copy of the OpenClaw codebase:

```bash
git clone https://github.com/priorodds-mesh8/openclaw.git
cd openclaw
```

### 2. Install Dependencies

Set up all required packages using npm:

```bash
npm install
```

This installs:
- Node.js dependencies (from `package.json`)
- Development tools
- Build utilities

### 3. Set Up Your Development Workflow

#### Create a Feature Branch

Before making changes, create a new branch for your work:

```bash
git checkout -b feature/your-feature-name
```

Branch naming conventions:
- `feature/` — New features
- `bugfix/` — Bug fixes
- `docs/` — Documentation changes
- `chore/` — Maintenance tasks

#### Make Your Changes

Edit files, add new code, update documentation:

```bash
# Edit files in your editor
# Example: scripts/ollama/SETUP.md

# Stage your changes
git add .

# Commit with a clear message
git commit -m "Add setup guide for Ollama integration"
```

#### Push to Remote

Push your branch to GitHub:

```bash
git push origin feature/your-feature-name
```

### 4. Running the Project

#### Development Server

Start the development server:

```bash
npm start
```

This will:
- Start the local development environment
- Watch for file changes
- Hot-reload your code
- Display errors and logs

#### Running Tests

Execute the test suite:

```bash
npm test
```

This runs:
- Unit tests
- Integration tests
- Linting checks

#### Building for Production

Create an optimized production build:

```bash
npm run build
```

### 5. Verify Your Setup

Check that everything is working correctly:

```bash
# Verify Node.js is installed
node --version

# Verify npm is installed
npm --version

# Verify dependencies are installed
npm list

# Test your local setup
npm test
```

## Environment Variables

Create a `.env` file in the root directory for local development:

```bash
# Example .env file
NODE_ENV=development
DEBUG=true
OLLAMA_URL=http://localhost:11434
```

Refer to `.env.example` for a complete list of required variables.

## Common Issues & Troubleshooting

### Issue: `npm install` fails

**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall dependencies
npm install
```

### Issue: Port already in use

**Solution:**
```bash
# Find process using the port (example: port 3000)
lsof -i :3000

# Kill the process
kill -9 <PID>
```

### Issue: Node version mismatch

**Solution:**
Check the required Node.js version in `package.json`. Use Node Version Manager (nvm) to switch versions:

```bash
nvm install <version>
nvm use <version>
```

### Issue: Module not found errors

**Solution:**
```bash
# Ensure all dependencies are installed
npm install

# Clear node_modules cache
npm ci
```

## Next Steps

Once your setup is complete:

1. **Read `CONTRIBUTING.md`** — Understand how to contribute to the project
2. **Explore the codebase** — Familiarize yourself with the directory structure
3. **Create a feature branch** — Start working on your changes
4. **Submit a pull request** — Share your work with the team

## Directory Structure

```
openclaw/
├── scripts/
│   ├── ollama/          # Ollama-related documentation
│   │   ├── SETUP.md     # This file
│   │   ├── CONTRIBUTING.md
│   │   ├── MODEL_ROUTING.md
│   │   └── ollama-qwen-quick-start.md
│   └── ...
├── package.json         # Dependencies and scripts
├── tsconfig.json        # TypeScript configuration
├── .env.example         # Example environment variables
└── README.md            # Project overview
```

## Getting Help

- **Documentation:** Check the `README.md` in each directory
- **Issues:** Search existing GitHub issues for solutions
- **Discussions:** Start a discussion on GitHub for questions
- **Contributing Guide:** See `CONTRIBUTING.md` for contribution guidelines

## Quick Start Checklist

- [ ] Clone the repository
- [ ] Install Node.js (if not installed)
- [ ] Run `npm install`
- [ ] Verify setup with `npm test`
- [ ] Create a feature branch
- [ ] Make your first changes
- [ ] Push to GitHub
- [ ] Read `CONTRIBUTING.md` for next steps

---

**Last updated:** 2026-03-30
**Maintained by:** OpenClaw team

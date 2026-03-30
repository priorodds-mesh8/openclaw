# CONTRIBUTING.md - How to Contribute to OpenClaw

This guide explains how to contribute to the OpenClaw monorepo. Whether you're fixing bugs, adding features, or improving documentation, we appreciate your contributions.

## Purpose

`CONTRIBUTING.md` provides:
- Contribution guidelines and best practices
- Code standards and conventions
- Pull request process
- Testing and validation requirements
- How to report issues and suggest improvements

## When to Use CONTRIBUTING.md

- **Before submitting a pull request** — Ensure your contribution follows project standards
- **When reporting a bug or feature request** — Know how to format your issue
- **When writing code or docs** — Follow our coding conventions and style guides
- **When improving the project** — Understand our contribution workflow

## Getting Started

### 1. Understand the Project Structure

Familiarize yourself with how the monorepo is organized:

```
openclaw/
├── scripts/          # Utility scripts and guides
├── src/              # Main source code
├── tests/            # Test files
├── docs/             # Project documentation
└── package.json      # Dependencies and metadata
```

### 2. Set Up Your Development Environment

Follow `SETUP.md` to:
- Clone the repository
- Install dependencies
- Configure your local environment

## Contribution Workflow

### Step 1: Create an Issue (for bugs or features)

Before starting work, create a GitHub issue to discuss your change:

1. Go to [Issues](https://github.com/priorodds-mesh8/openclaw/issues)
2. Click "New Issue"
3. Choose a template (Bug Report or Feature Request)
4. Fill in details:
   - **Title:** Clear, concise description
   - **Description:** What's the problem or request?
   - **Expected behavior:** What should happen?
   - **Current behavior:** What actually happens?
   - **Steps to reproduce:** How can we verify this?

### Step 2: Fork and Clone

Create your own copy of the repository:

```bash
# Fork the repo on GitHub (click "Fork" button)

# Clone your fork
git clone https://github.com/YOUR-USERNAME/openclaw.git
cd openclaw

# Add upstream remote to stay synced
git remote add upstream https://github.com/priorodds-mesh8/openclaw.git
```

### Step 3: Create a Feature Branch

Create a branch for your changes:

```bash
# Update from upstream
git fetch upstream
git checkout main
git merge upstream/main

# Create your feature branch
git checkout -b feature/your-feature-name
```

**Branch naming conventions:**
- `feature/description` — New features
- `bugfix/description` — Bug fixes
- `docs/description` — Documentation updates
- `chore/description` — Maintenance tasks
- `test/description` — Test improvements

### Step 4: Make Your Changes

Write code or documentation following our standards:

#### Code Style
- Use consistent indentation (2 spaces)
- Follow existing code patterns
- Write meaningful variable/function names
- Keep functions small and focused
- Add comments for complex logic

#### Documentation Style
- Use clear, concise language
- Follow Markdown formatting standards
- Include code examples where relevant
- Link to related documentation
- Keep line length around 80 characters

#### Example: Documentation Changes

```bash
# Edit documentation files
nano scripts/ollama/SETUP.md

# Verify formatting
cat scripts/ollama/SETUP.md

# Stage changes
git add scripts/ollama/SETUP.md
```

### Step 5: Commit Your Changes

Write clear, descriptive commit messages:

```bash
# Good commit message format
git commit -m "Add Ollama setup documentation

- Create SETUP.md with installation instructions
- Add troubleshooting section
- Include directory structure overview
- Closes #123"
```

**Commit message guidelines:**
- Use imperative mood ("Add feature" not "Added feature")
- Capitalize the subject line
- Keep first line under 50 characters
- Separate subject from body with blank line
- Reference related issues (#123)

### Step 6: Test Your Changes

Ensure your changes don't break anything:

```bash
# Run the test suite
npm test

# Run linting
npm run lint

# Build the project
npm run build

# For documentation, preview locally if possible
```

### Step 7: Push to Your Fork

Push your feature branch to your GitHub fork:

```bash
git push origin feature/your-feature-name
```

### Step 8: Create a Pull Request

1. Go to your fork on GitHub
2. Click "Compare & pull request"
3. Fill in the PR template:
   - **Title:** Clear description of changes
   - **Description:** Why are these changes needed?
   - **Related issue:** Link to issue #123
   - **Changes made:** What specifically changed?
   - **Testing:** How was this tested?
   - **Checklist:** Mark completed items

### Step 9: Address Review Comments

Maintainers will review your PR. If changes are requested:

```bash
# Make requested changes
# Commit with descriptive message
git commit -m "Address review feedback: improve clarity"

# Push updates (no new PR needed)
git push origin feature/your-feature-name
```

### Step 10: Merge

Once approved, maintainers will merge your PR into `main`.

## Code Standards

### Documentation

- Use Markdown formatting
- Include code examples
- Keep explanations clear and concise
- Link to related resources

### Scripts

- Bash scripts should start with `#!/bin/bash`
- Add comments explaining complex logic
- Use meaningful variable names
- Test thoroughly before committing

### Metadata

- Update version numbers in `package.json` if needed
- Add yourself to `CONTRIBUTORS` file
- Update `CHANGELOG.md` with your changes

## Testing Requirements

### For Code Changes
- Write or update unit tests
- Ensure all tests pass: `npm test`
- Maintain or improve code coverage

### For Documentation
- Check for spelling and grammar
- Verify code examples work
- Test internal links
- Preview formatting

## Reporting Issues

### Bug Reports

Provide clear information to help us fix the issue:

```markdown
**Title:** Brief description of bug

**Current behavior:**
What's happening now?

**Expected behavior:**
What should happen instead?

**Steps to reproduce:**
1. Step one
2. Step two
3. Step three

**Environment:**
- OS: macOS 12.4
- Node version: 18.0.0
- npm version: 8.5.0

**Additional context:**
Any other helpful information
```

### Feature Requests

Explain the use case and proposed solution:

```markdown
**Title:** Brief feature description

**Problem:**
What problem does this solve?

**Proposed solution:**
How should this work?

**Alternative approaches:**
Other ways to solve this?

**Additional context:**
Why is this important?
```

## Code Review Process

### What Reviewers Look For

- **Code quality** — Clean, readable, well-documented
- **Functionality** — Does it solve the stated problem?
- **Testing** — Adequate test coverage
- **Documentation** — Clear explanations and examples
- **Compatibility** — No breaking changes without discussion
- **Performance** — No unnecessary performance degradation

### Tips for Getting Approved

1. **Keep PRs focused** — One feature or fix per PR
2. **Add tests** — Show your code works
3. **Document changes** — Explain the "why"
4. **Be responsive** — Address feedback promptly
5. **Follow conventions** — Match existing code style

## Maintainer Responsibilities

Maintainers will:
- Review PRs promptly
- Provide constructive feedback
- Help improve code quality
- Merge approved changes
- Update documentation

## Community Guidelines

### Be Respectful

- Treat everyone with respect
- Assume good intentions
- Ask questions before critiquing
- Welcome newcomers

### Be Collaborative

- Help others when possible
- Share knowledge and resources
- Celebrate contributions
- Work toward common goals

### Be Professional

- Use clear, constructive language
- Focus on ideas, not people
- Provide actionable feedback
- Maintain a positive tone

## Resources

- **Setup Guide:** See `SETUP.md`
- **Documentation:** Check the `docs/` directory
- **Examples:** Look at existing code for patterns
- **Issues:** Browse open issues for ideas
- **Discussions:** Join conversations on GitHub

## Questions?

- **Documentation questions:** Create a GitHub Discussion
- **Contribution questions:** Comment on a relevant issue
- **General questions:** Check existing documentation first

## Thank You!

We appreciate all contributions, no matter how small. Your work helps make OpenClaw better for everyone.

---

**Last updated:** 2026-03-30
**Maintained by:** OpenClaw team

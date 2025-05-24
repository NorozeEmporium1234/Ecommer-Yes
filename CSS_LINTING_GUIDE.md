# CSS Linting Guide

This project uses Stylelint to catch CSS syntax errors and maintain consistent code quality.

## Setup

The following tools are configured:

- **Stylelint**: CSS linting
- **Prettier**: Code formatting
- **Husky**: Git hooks
- **Lint-staged**: Run linters on staged files

## Available Scripts

\`\`\`bash
# Lint and fix CSS files
npm run lint:css

# Check CSS without fixing
npm run lint:css-check

# Lint both JavaScript and CSS
npm run lint:all

# Format all files
npm run format

# Check formatting
npm run format:check

# Run pre-commit checks
npm run pre-commit
\`\`\`

## VS Code Integration

The project includes VS Code settings for:

- Real-time CSS linting
- Auto-fix on save
- Tailwind CSS IntelliSense
- Custom CSS property recognition

## Stylelint Rules

Key rules configured:

- **Tailwind CSS support**: Recognizes @tailwind, @apply, @layer directives
- **Property ordering**: Alphabetical ordering of CSS properties
- **Consistent formatting**: Double quotes, lowercase hex colors
- **Error prevention**: Catches unknown properties and functions

## Common Issues and Fixes

### 1. Unknown at-rule errors
\`\`\`css
/* ❌ Wrong */
@unknown-rule base;

/* ✅ Correct */
@tailwind base;
\`\`\`

### 2. Missing spaces in utility classes
\`\`\`css
/* ❌ Wrong */
.class { @apply flex items-centerspace-x-4; }

/* ✅ Correct */
.class { @apply flex items-center space-x-4; }
\`\`\`

### 3. Property ordering
\`\`\`css
/* ❌ Wrong */
.class {
  margin: 0;
  display: flex;
  background: white;
}

/* ✅ Correct (alphabetical) */
.class {
  background: white;
  display: flex;
  margin: 0;
}
\`\`\`

## Pre-commit Hooks

The project automatically runs linting and formatting checks before each commit:

1. Lints and fixes CSS files
2. Lints and fixes JavaScript/TypeScript files
3. Formats all files with Prettier
4. Prevents commits if there are unfixable errors

## Ignoring Files

Add files to ignore in `.stylelintrc.json`:

\`\`\`json
{
  "ignoreFiles": [
    "node_modules/**/*",
    "dist/**/*",
    ".next/**/*"
  ]
}
\`\`\`

## Custom Rules

To add custom rules, modify `.stylelintrc.json`:

\`\`\`json
{
  "rules": {
    "your-custom-rule": "value"
  }
}
\`\`\`

## Troubleshooting

### Installation Issues
\`\`\`bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
\`\`\`

### VS Code Not Working
1. Install the Stylelint extension
2. Reload VS Code
3. Check the Output panel for errors

### Husky Hooks Not Running
\`\`\`bash
# Reinstall husky
npm run prepare

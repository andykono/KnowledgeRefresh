# Tooling Quick Reference

## Vite Setup

```bash
npm create vite@latest my-app -- --template react-ts
cd my-app && npm install
```

### Minimal vite.config.ts

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: { "@": "/src" },
  },
  server: { port: 3000 },
  build: {
    outDir: "dist",
    sourcemap: true,
  },
});
```

---

## ESLint + Prettier Setup

```bash
npm install -D eslint @eslint/js typescript-eslint eslint-plugin-react eslint-plugin-react-hooks
npm install -D prettier eslint-config-prettier eslint-plugin-prettier
```

### .eslintrc.cjs (minimal)

```javascript
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:react-hooks/recommended",
    "plugin:react/recommended",
    "prettier",
  ],
  ignorePatterns: ["dist", ".eslintrc.cjs"],
  parser: "@typescript-eslint/parser",
  plugins: ["react-refresh"],
  settings: { react: { version: "detect" } },
  rules: { "react/react-in-jsx-scope": "off" },
};
```

### .prettierrc

```json
{
  "semi": true,
  "singleQuote": false,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

---

## GitHub Actions Minimal Workflow

```yaml
# .github/workflows/ci.yml
name: CI
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "npm"
      - run: npm ci
      - run: npm run lint
      - run: npm run test
      - run: npm run build
```

---

## Useful package.json Scripts

```json
{
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "lint:fix": "eslint . --ext ts,tsx --fix",
    "format": "prettier --write \"src/**/*.{ts,tsx,css,json}\"",
    "format:check": "prettier --check \"src/**/*.{ts,tsx,css,json}\"",
    "test": "vitest",
    "test:ui": "vitest --ui",
    "test:coverage": "vitest run --coverage",
    "typecheck": "tsc --noEmit"
  }
}
```

**Tip**: Add `"prepare": "husky"` for git hooks; use `lint-staged` to run lint/format on staged files only.

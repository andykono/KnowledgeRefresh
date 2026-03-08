# Frontend Learning Vault

Comprehensive knowledge base for modern **React + TypeScript** frontend development and system design.

---

## Structure

```
Learning/
├── 1. React/                         ← Everything React
│   ├── Core Concepts                 (components, JSX, props, state, rendering)
│   ├── Hooks                         (useState → custom hooks → v19 hooks)
│   ├── Routing                       (React Router v6+)
│   ├── Data Fetching                 (fetch, TanStack Query, SWR, Suspense)
│   ├── Forms                         (controlled, React Hook Form, validation)
│   ├── Server Components             (RSC, server actions, streaming)
│   ├── Styling                       (CSS Modules, Tailwind, CSS-in-JS)
│   ├── Accessibility                 (ARIA, focus management, a11y testing)
│   ├── React Patterns                (Compound Components, HOCs, Custom Hooks)
│   ├── State Management              (Redux, Zustand, Jotai, XState, TanStack Query)
│   ├── Testing                       (unit, component, integration, E2E)
│   ├── Performance                   (rendering, memoization, code splitting)
│   ├── Tooling & Build               (Vite, Next.js, ESLint, CI/CD)
│   └── Real-World Examples           (Todo, E-commerce, Chat, Auth, Dashboard)
│
├── 2. TypeScript/                    ← TypeScript for React developers
│   ├── Fundamentals                  (types, generics, utility types)
│   ├── Typing Components             (props, events, refs, HOCs)
│   ├── Typing Hooks                  (useState, useReducer, custom hooks)
│   ├── Advanced Types                (conditional, mapped, branded types)
│   └── Type-Safe API Layer           (typed fetch, Zod, route params)
│
├── 3. Patterns/                      ← Design & architectural patterns
│   ├── Design Patterns               (Singleton, Factory, Observer, Decorator, Strategy, Facade)
│   ├── Architectural Patterns        (MVC, MVVM, Clean, Onion, FSD)
│   └── Anti-Patterns                 (React, State Management, TypeScript)
│
├── 4. Common/                         ← Shared concepts
│   ├── 1. EventLoop                  (call stack, task queue, microtasks, Promise executor)
│   │   ├── 1. EventLoop              (overview and examples)
│   │   └── 2. PromiseExecutor        (Promise executor & microtask queue)
│   ├── 2. Debounce                   (debounce, throttle, React hooks, examples)
│   │   ├── 1. Debounce               (definition, JS/TS implementations)
│   │   ├── 2. ReactHooks             (useDebounce hook, stale closure)
│   │   ├── 3. Examples                (search, validation, autosave, filtering)
│   │   └── 4. Throttle               (definition, implementations, examples)
│   ├── 3. Hoisting                   (var/let/const hoisting, TDZ, function declarations)
│   │   └── 1. Hoisting               (definition, examples, comparison, best practices)
│   └── EventEmitter                  (pub/sub pattern)
│
├── 5. FED/                            ← Frontend fundamentals
│   ├── HTML                          (Semantic HTML, ARIA, HTML5 features)
│   ├── CSS                           (Layout, Box Model, Specificity, Responsive, Animations)
│   ├── JavaScript                    (this, closures, prototypes, ES6, DOM, Browser API)
│   ├── Web performance               (page load, rendering, responsiveness)
│   ├── Accessibility (a11y)          (WCAG, assistive technologies)
│   ├── Security                      (XSS, CSRF, CSP)
│   └── Front end frameworks          (React, Vue, Angular comparison)
│
└── 6. System Design/                  ← System design for interviews
    ├── Scalability                   (horizontal/vertical scaling, load balancing)
    ├── Modularity                    (separation of concerns, boundaries)
    ├── Performance and Reliability   (caching, CDN, fault tolerance)
    ├── Maintainability               (code quality, documentation)
    ├── Accessibility                 (design for scale, inclusive systems)
    └── Trade-offs                    (CAP, consistency vs availability)
```

---

## Recommended Learning Path

| Phase | Sections | Duration |
| :-- | :-- | :-- |
| **Fundamentals** | [[1. React/README|1. React]] (Core + Hooks) | 6 weeks |
| **TypeScript** | [[2. TypeScript/2. TypeScript|2. TypeScript]] | 2 weeks |
| **FED Basics** | [[5. FED/1. HTML/Semantic HTML|5. FED]] (HTML, CSS, JavaScript) | 3 weeks |
| **Ecosystem** | React Patterns, State Management, Routing, Data Fetching | 3 weeks |
| **Patterns** | [[3. Patterns/README|3. Patterns]] | 3 weeks |
| **Quality** | Testing, Performance, [[5. FED/6. Security/1. security|Security]] | 3 weeks |
| **Production** | Tooling & Build, Real-World Examples | 2 weeks |
| **System Design** | [[6. System Design/1. Scalability|6. System Design]] | 2 weeks |

**Total estimated time: ~24 weeks** (at moderate pace)

---

## Quick Start

- **New to React?** Start with [[1. React/1. React Core Concepts/1. React Core Concepts]]
- **Know React, learning TypeScript?** Go to [[2. TypeScript/2. TypeScript]]
- **Frontend fundamentals?** Check [[5. FED/1. HTML/Semantic HTML]], [[5. FED/2. CSS/1. Layout (Flexbox, Grid)]], [[5. FED/3. JavaScript/1. Core concepts/1. this]]
- **Looking for patterns?** See [[3. Patterns/QUICK_REFERENCE]]
- **Choosing state management?** [[1. React/10. State Management/4. State Management]]
- **Setting up a project?** [[1. React/13. Tooling & Build/7. Tooling & Build]]
- **System design interview?** [[6. System Design/1. Scalability]]
- **Need a reference example?** [[1. React/14. Real-World Examples/8. Real-World Examples]]

---

## Statistics

- **Sections:** 6 main sections (React, TypeScript, Patterns, Common, FED, System Design)
- **Files:** 170+ markdown files
- **Code Examples:** 500+
- **Patterns Covered:** 40+

---

**Last Updated:** March 4, 2026  
**Version:** 4.0

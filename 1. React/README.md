# React Complete Guide

Comprehensive guide to **React Core Concepts, Hooks, React v19 Features, and Best Practices** with TypeScript examples.

---

## Structure

```
React/
├── 1. React Core Concepts/         ← Fundamental concepts
│   ├── 1. React Core Concepts.md
│   ├── 1.1 Components.md
│   ├── 1.2 JSX.md
│   ├── 1.3 Props and State.md
│   ├── 1.4 Rendering.md
│   ├── 1.5 Keys and Refs.md
│   ├── 1.6 Portals.md
│   ├── 1.7 Error Boundaries.md
│   ├── 1.8 Performance Optimization.md
│   ├── 1.9 Context API.md
│   └── 1.10 Advanced Patterns.md
│
├── 2. React Hooks/                 ← React Hooks API
│   ├── 2. React Hooks.md
│   ├── 2.1 Rules of Hooks.md
│   ├── 2.2–2.10 (core hooks)
│   └── 2.11 React v19 Hooks/       ← React v19 new features
│       ├── 2.11 React v19 Hooks.md
│       └── 2.11.1–2.11.7 (v19 hooks)
│
├── 3. Routing/                      ← React Router v6+
│   ├── 3. Routing.md
│   ├── 3.1 React Router Basics.md
│   ├── 3.2 Nested and Dynamic Routes.md
│   ├── 3.3 Protected Routes.md
│   └── 3.4 Lazy Routes.md
│
├── 4. Data Fetching/               ← Fetching & caching data
│   ├── 4. Data Fetching.md
│   ├── 4.1 Fetch and Axios Patterns.md
│   ├── 4.2 TanStack Query.md
│   ├── 4.3 SWR.md
│   └── 4.4 Suspense for Data.md
│
├── 5. Forms/                        ← Form handling & validation
│   ├── 5. Forms.md
│   ├── 5.1 Controlled vs Uncontrolled.md
│   ├── 5.2 React Hook Form.md
│   └── 5.3 Validation Patterns.md
│
├── 6. Server Components/           ← RSC architecture
│   ├── 6. Server Components.md
│   ├── 6.1 Server vs Client.md
│   ├── 6.2 Server Actions.md
│   └── 6.3 Streaming and Suspense.md
│
├── 7. Styling/                      ← CSS approaches for React
│   ├── 7. Styling.md
│   ├── 7.1 CSS Modules.md
│   ├── 7.2 Tailwind CSS.md
│   └── 7.3 CSS-in-JS.md
│
├── 8. Accessibility/               ← A11y patterns
│   ├── 8. Accessibility.md
│   ├── 8.1 ARIA and Semantic HTML.md
│   ├── 8.2 Focus Management.md
│   └── 8.3 Testing Accessibility.md
│
├── 9. React Patterns/              ← React-specific patterns
│   ├── 9. React Patterns.md
│   ├── 9.1 Compound Components.md
│   ├── 9.2 Render Props, HOCs, Hooks.md
│   ├── 9.3 Custom Hooks Patterns.md
│   └── 9.4 Context API Patterns.md
│
├── 10. State Management/           ← Managing app state
│   ├── 4. State Management.md
│   ├── 4.1 React Built-in State.md
│   ├── 4.2 Redux Toolkit.md
│   ├── 4.3 Zustand.md
│   ├── 4.4 Jotai.md
│   ├── 4.5 XState.md
│   └── 4.6 Server State with TanStack Query.md
│
├── 11. Testing/                    ← Testing strategies & tools
│   ├── 5. Testing.md
│   ├── 5.1 Unit Testing.md
│   ├── 5.2 Component Testing.md
│   ├── 5.3 Integration Testing.md
│   ├── 5.4 E2E Testing.md
│   ├── 5.5 Mocking Strategies.md
│   └── 5.6 Testing Best Practices.md
│
├── 12. Performance/                ← Making React apps fast
│   ├── 6. Performance.md
│   ├── 6.1 React Rendering Model.md
│   ├── 6.2 Memoization.md
│   ├── 6.3 Code Splitting.md
│   ├── 6.4 Virtualization.md
│   └── 6.5 Web Vitals.md
│
├── 13. Tooling & Build/            ← Dev tools & CI/CD
│   ├── 7. Tooling & Build.md
│   ├── 7.1 Vite.md
│   ├── 7.2 Next.js Basics.md
│   ├── 7.3 ESLint and Prettier.md
│   └── 7.4 CI and Deployment.md
│
├── 14. Real-World Examples/        ← Complete app examples
│   ├── 8. Real-World Examples.md
│   ├── 8.1 Todo App (FSD).md
│   ├── 8.2 E-commerce Dashboard.md
│   ├── 8.3 Real-time Chat App.md
│   ├── 8.4 Authentication Flow.md
│   └── 8.5 Dashboard with Charts.md
│
├── QUICK_REFERENCE.md              ← Cheat sheet
└── README.md                        ← This file
```

---

## 🚀 Recommended Learning Path

### Week 1: React Core Concepts
- [ ] **Read:** [[1. React Core Concepts/1. React Core Concepts.md|1. React Core Concepts]]
- [ ] **Learn:** [[1. React Core Concepts/1.1 Components.md|Components]] (functional vs class)
- [ ] **Learn:** [[1. React Core Concepts/1.2 JSX.md|JSX]] syntax and rules
- [ ] **Learn:** [[1. React Core Concepts/1.3 Props and State.md|Props and State]]
- [ ] **Practice:** Build simple components

### Week 2: React Rendering & Performance
- [ ] **Learn:** [[1. React Core Concepts/1.4 Rendering.md|Rendering]] (reconciliation, diffing)
- [ ] **Learn:** [[1. React Core Concepts/1.5 Keys and Refs.md|Keys and Refs]]
- [ ] **Learn:** [[1. React Core Concepts/1.8 Performance Optimization.md|Performance Optimization]]
- [ ] **Practice:** Optimize component rendering

### Week 3: Advanced Concepts
- [ ] **Learn:** [[1. React Core Concepts/1.6 Portals.md|Portals]]
- [ ] **Learn:** [[1. React Core Concepts/1.7 Error Boundaries.md|Error Boundaries]]
- [ ] **Learn:** [[1. React Core Concepts/1.9 Context API.md|Context API]]
- [ ] **Learn:** [[1. React Core Concepts/1.10 Advanced Patterns.md|Advanced Patterns]]

### Week 4: React Hooks Fundamentals
- [ ] **Read:** [[2. React Hooks/2. React Hooks.md|React Hooks Overview]]
- [ ] **Learn:** [[2. React Hooks/2.1 Rules of Hooks.md|Rules of Hooks]] (critical!)
- [ ] **Learn:** [[2. React Hooks/2.2 useState.md|useState]] hook
- [ ] **Learn:** [[2. React Hooks/2.3 useEffect.md|useEffect]] lifecycle hook
- [ ] **Practice:** Refactor class components to hooks

### Week 5: Advanced Hooks
- [ ] **Learn:** [[2. React Hooks/2.4 useContext.md|useContext]]
- [ ] **Learn:** [[2. React Hooks/2.5 useReducer.md|useReducer]]
- [ ] **Learn:** [[2. React Hooks/2.6 useCallback.md|useCallback]] and [[2. React Hooks/2.7 useMemo.md|useMemo]]
- [ ] **Learn:** [[2. React Hooks/2.8 useRef.md|useRef]]

### Week 6: Custom Hooks & React v19
- [ ] **Learn:** [[2. React Hooks/2.9 Custom Hooks.md|Custom Hooks]]
- [ ] **Learn:** [[2. React Hooks/2.10 Hook Composition.md|Hook Composition]]
- [ ] **Read:** [[2. React Hooks/2.11 React v19 Hooks/2.11 React v19 Hooks.md|React v19 Hooks]]
- [ ] **Learn:** [[2. React Hooks/2.11 React v19 Hooks/2.11.1 use().md|use()]] - unwrap promises
- [ ] **Learn:** [[2. React Hooks/2.11 React v19 Hooks/2.11.4 useOptimistic.md|useOptimistic]]

### Week 7: Routing & Data Fetching
- [ ] **Learn:** [[3. Routing/3. Routing.md|Routing]] with React Router v6+
- [ ] **Learn:** [[3. Routing/3.3 Protected Routes.md|Protected Routes]]
- [ ] **Learn:** [[4. Data Fetching/4. Data Fetching.md|Data Fetching]] strategies
- [ ] **Learn:** [[4. Data Fetching/4.2 TanStack Query.md|TanStack Query]]

### Week 8: Forms & Validation
- [ ] **Read:** [[5. Forms/5. Forms.md|Forms Overview]]
- [ ] **Learn:** [[5. Forms/5.1 Controlled vs Uncontrolled.md|Controlled vs Uncontrolled]]
- [ ] **Learn:** [[5. Forms/5.2 React Hook Form.md|React Hook Form]]
- [ ] **Learn:** [[5. Forms/5.3 Validation Patterns.md|Validation Patterns]]

### Week 9: Server Components
- [ ] **Read:** [[6. Server Components/6. Server Components.md|Server Components Overview]]
- [ ] **Learn:** [[6. Server Components/6.1 Server vs Client.md|Server vs Client]]
- [ ] **Learn:** [[6. Server Components/6.2 Server Actions.md|Server Actions]]
- [ ] **Learn:** [[6. Server Components/6.3 Streaming and Suspense.md|Streaming and Suspense]]

### Week 10: Styling & Accessibility
- [ ] **Learn:** [[7. Styling/7. Styling.md|Styling approaches]]
- [ ] **Learn:** [[7. Styling/7.2 Tailwind CSS.md|Tailwind CSS]]
- [ ] **Learn:** [[8. Accessibility/8. Accessibility.md|Accessibility]] fundamentals
- [ ] **Learn:** [[8. Accessibility/8.2 Focus Management.md|Focus Management]]

### Week 11: React Patterns
- [ ] **Read:** [[9. React Patterns/9. React Patterns.md|React Patterns Overview]]
- [ ] **Learn:** [[9. React Patterns/9.1 Compound Components.md|Compound Components]]
- [ ] **Learn:** [[9. React Patterns/9.3 Custom Hooks Patterns.md|Custom Hooks Patterns]]
- [ ] **Learn:** [[9. React Patterns/9.4 Context API Patterns.md|Context API Patterns]]

### Week 12: State Management
- [ ] **Read:** [[10. State Management/4. State Management.md|State Management Overview]]
- [ ] **Learn:** [[10. State Management/4.3 Zustand.md|Zustand]]
- [ ] **Learn:** [[10. State Management/4.2 Redux Toolkit.md|Redux Toolkit]]
- [ ] **Learn:** [[10. State Management/4.6 Server State with TanStack Query.md|TanStack Query]]

### Week 13: Testing
- [ ] **Read:** [[11. Testing/5. Testing.md|Testing Overview]]
- [ ] **Learn:** [[11. Testing/5.2 Component Testing.md|Component Testing]]
- [ ] **Learn:** [[11. Testing/5.4 E2E Testing.md|E2E Testing]]
- [ ] **Learn:** [[11. Testing/5.5 Mocking Strategies.md|Mocking Strategies]]

### Week 14: Performance & Tooling
- [ ] **Learn:** [[12. Performance/6. Performance.md|Performance]] optimization
- [ ] **Learn:** [[12. Performance/6.2 Memoization.md|Memoization]]
- [ ] **Learn:** [[13. Tooling & Build/7.1 Vite.md|Vite]] setup
- [ ] **Learn:** [[13. Tooling & Build/7.3 ESLint and Prettier.md|ESLint & Prettier]]

### Week 15: Real-World Examples
- [ ] **Study:** [[14. Real-World Examples/8.1 Todo App (FSD).md|Todo App (FSD)]]
- [ ] **Study:** [[14. Real-World Examples/8.4 Authentication Flow.md|Auth Flow]]
- [ ] **Study:** [[14. Real-World Examples/8.2 E-commerce Dashboard.md|E-commerce Dashboard]]

---

## 🎯 Quick Comparison: Core vs Hooks vs v19

| Feature | Class Components | React Hooks | React v19 |
| :-- | :-- | :-- | :-- |
| **Syntax** | Class-based | Function-based | Function-based |
| **State** | this.state | useState | useState (better) |
| **Lifecycle** | Methods | useEffect | useEffect (optimized) |
| **Logic Sharing** | HOCs, Render Props | Custom Hooks | use() for unwrapping |
| **Performance** | shouldComponentUpdate | useMemo, useCallback | useTransition, useDeferredValue |
| **Recommended** | ❌ Legacy | ✅ Modern | ✅⭐ Latest |
| **Learning Curve** | 🟠 Medium | 🟢 Easy | 🟡 Easy-Medium |

---

## 📖 Key Takeaways

### React Core Concepts (Week 1-3)
- ✅ Components are functions returning JSX
- ✅ Props flow down, events flow up
- ✅ State causes re-renders
- ✅ React uses virtual DOM and reconciliation
- ✅ Keys help React identify list items
- ✅ Refs access DOM directly (use sparingly)
- ✅ Error Boundaries catch rendering errors
- ✅ Context API shares state globally
- ✅ Performance optimization is critical

### React Hooks (Week 4-6)
- ✅ Hooks are functions that hook into React features
- ✅ Only call hooks at top level (Rules of Hooks)
- ✅ useState replaces this.state
- ✅ useEffect replaces lifecycle methods
- ✅ useContext accesses Context values
- ✅ useReducer for complex state logic
- ✅ useMemo/useCallback prevent unnecessary renders
- ✅ useRef doesn't cause re-renders
- ✅ Custom hooks extract reusable logic

### React v19 Features
- ✅ use() unwraps promises and context in components
- ✅ useActionState replaces useTransition for forms
- ✅ useFormStatus shows form submission status
- ✅ useOptimistic updates UI before server response
- ✅ useTransition marks state updates as transitions
- ✅ useDeferredValue defers value updates
- ✅ Server Components + Client Components architecture
- ✅ Actions (server functions) simplify API calls

---

## 🔍 How to Use This Guide

### For Learning
1. Start with [[1. React Core Concepts/1. React Core Concepts.md|Core Concepts]]
2. Progress through [[2. React Hooks/2. React Hooks.md|Hooks]] in order
3. Learn [[2. React Hooks/2.11 React v19 Hooks/2.11 React v19 Hooks.md|React v19 features]]
4. Practice with code examples
5. Build projects to apply knowledge

### For Reference
1. Use [[QUICK_REFERENCE.md]] for quick lookup
2. Search by topic (Components, Hooks, Performance, etc.)
3. Copy code examples
4. Check comparison tables for pattern selection

### For Your Project
1. Review [[1. React Core Concepts/1.8 Performance Optimization.md|Performance Optimization]]
2. Implement proper [[2. React Hooks/2.1 Rules of Hooks.md|Hook patterns]]
3. Use [[2. React Hooks/2.9 Custom Hooks.md|Custom Hooks]] to extract logic
4. Leverage [[2. React Hooks/2.11 React v19 Hooks/2.11.4 useOptimistic.md|v19 features]] for modern UX

---

## 💡 Tips & Tricks

✅ **DO:**
- Read React docs alongside this guide
- Practice writing components daily
- Understand WHY before memorizing WHAT
- Use TypeScript for type safety
- Test your components

❌ **DON'T:**
- Don't use Hooks inside loops/conditions
- Don't overuse useMemo/useCallback
- Don't forget cleanup in useEffect
- Don't ignore React DevTools
- Don't skip the fundamentals

---

## 🔗 Resources

- **Official:** [React Docs](https://react.dev)
- **Learning:** [React Core Concepts](https://react.dev/learn)
- **Hooks API:** [Hooks Reference](https://react.dev/reference/react/hooks)
- **v19 Features:** [React v19 Release Notes](https://react.dev/blog)
- **TypeScript:** [TypeScript Handbook](https://www.typescriptlang.org/docs/)

---

## Statistics

- **Total Files:** 80+ markdown files
- **Total Sections:** 14 main sections, 60+ concepts
- **Code Examples:** 500+
- **Estimated Learning Time:** 15 weeks

---

**Last Updated:** February 25, 2026
**Version:** 3.0 (complete React ecosystem: core, hooks, routing, data fetching, forms, RSC, styling, a11y, patterns, state management, testing, performance, tooling, examples)

---

Start with: [[1. React Core Concepts/1. React Core Concepts.md]] or [[QUICK_REFERENCE.md]] for quick overview!

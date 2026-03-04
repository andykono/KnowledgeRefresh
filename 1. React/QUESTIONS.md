# React Interview Questions

Self-test questions organized by difficulty. Expand each answer to check your understanding.

---

## Easy

### Q: What is the difference between state and props?

<details>
<summary>Answer</summary>

**Props** are passed from parent to child and are read-only. **State** is internal to a component and can change over time. When state updates, the component re-renders. Props flow down; state is local.

See: [[1. React Core Concepts/1.3 Props and State]]

</details>

### Q: What is JSX and how does it differ from HTML?

<details>
<summary>Answer</summary>

JSX is a syntax extension that lets you write HTML-like markup in JavaScript. Key differences: use `className` instead of `class`, `htmlFor` instead of `for`, camelCase for attributes, and you must close all tags (e.g. `<img />`). JSX compiles to `React.createElement()` calls.

See: [[1. React Core Concepts/1.2 JSX]]

</details>

### Q: What is a React component?

<details>
<summary>Answer</summary>

A component is a reusable piece of UI that returns JSX. It can be a function (function component) or a class. Components accept props and can manage local state. They compose together to build the UI tree.

See: [[1. React Core Concepts/1.1 Components]]

</details>

### Q: When does a React component re-render?

<details>
<summary>Answer</summary>

A component re-renders when: (1) its state changes via `setState` or `useState`, (2) its props change, (3) its parent re-renders (unless memoized), or (4) the context it consumes changes.

See: [[1. React Core Concepts/1.4 Rendering]]

</details>

### Q: What are React keys and why are they important?

<details>
<summary>Answer</summary>

Keys help React identify which items have changed, been added, or removed in a list. Use a stable, unique identifier (e.g. `id`). Avoid array index as key when the list can reorder—it can cause bugs and unnecessary re-renders.

See: [[1. React Core Concepts/1.5 Keys and Refs]]

</details>

### Q: What is the difference between useMemo and useCallback?

<details>
<summary>Answer</summary>

`useMemo` caches a computed **value**, `useCallback` caches a **function reference**. `useCallback(fn, deps)` is equivalent to `useMemo(() => fn, deps)`.

See: [[2. React Hooks/2.6 useCallback]] | [[2. React Hooks/2.7 useMemo]]

</details>

### Q: What does useEffect do?

<details>
<summary>Answer</summary>

`useEffect` runs side effects after render. It accepts a function and an optional dependency array. With `[]`, it runs once on mount. With `[a, b]`, it runs when `a` or `b` change. Without deps, it runs after every render.

See: [[2. React Hooks/2.3 useEffect]]

</details>

### Q: How do you share state between components without prop drilling?

<details>
<summary>Answer</summary>

Use the **Context API**: create a context with `createContext`, wrap the tree with a Provider, and consume with `useContext`. For complex state, consider Zustand, Redux, or Jotai.

See: [[1. React Core Concepts/1.9 Context API]] | [[9. React Patterns/9.4 Context API Patterns]]

</details>

### Q: What is a controlled vs uncontrolled input?

<details>
<summary>Answer</summary>

**Controlled:** the input value is driven by React state (`value={state}` + `onChange`). **Uncontrolled:** the DOM holds the value; you read it via `ref.current.value`. Prefer controlled for most forms.

See: [[5. Forms/5.1 Controlled vs Uncontrolled]]

</details>

### Q: What is the purpose of useRef?

<details>
<summary>Answer</summary>

`useRef` holds a mutable value that persists across renders without causing re-renders. Common uses: (1) accessing DOM elements, (2) storing previous values, (3) holding timers or subscriptions.

See: [[2. React Hooks/2.8 useRef]] | [[1. React Core Concepts/1.5 Keys and Refs]]

</details>

### Q: What is React.memo and when should you use it?

<details>
<summary>Answer</summary>

`React.memo` is a higher-order component that memoizes a component—it skips re-renders when props are shallowly equal. Use it for expensive components that receive stable props. Don't overuse; measure first.

See: [[12. Performance/6.2 Memoization]]

</details>

### Q: What is a Portal and when would you use one?

<details>
<summary>Answer</summary>

`ReactDOM.createPortal(child, container)` renders `child` into a different DOM node (e.g. `document.body`). Use for modals, tooltips, or dropdowns that need to escape parent overflow/z-index constraints.

See: [[1. React Core Concepts/1.6 Portals]]

</details>

### Q: What is an Error Boundary?

<details>
<summary>Answer</summary>

An Error Boundary is a class component that catches JavaScript errors in its child tree, displays a fallback UI, and prevents the whole app from crashing. It catches render errors and lifecycle errors, but not event handlers or async code.

See: [[1. React Core Concepts/1.7 Error Boundaries]]

</details>

### Q: What are Server Components vs Client Components?

<details>
<summary>Answer</summary>

**Server Components** run only on the server—no JS shipped, can access DB directly. **Client Components** run in the browser and support interactivity (state, effects, event handlers). In Next.js, `"use client"` marks a Client Component.

See: [[6. Server Components/6.1 Server vs Client]]

</details>

---

## Medium

### Q: Why can't you call hooks inside conditions or loops?

<details>
<summary>Answer</summary>

Hooks must be called in the same order on every render. React relies on call order to associate state with each hook. Conditional calls would change the order between renders, breaking React's internal hook state mapping.

See: [[2. React Hooks/2.1 Rules of Hooks]]

</details>

### Q: When would you use useReducer over useState?

<details>
<summary>Answer</summary>

Use `useReducer` when: (1) state logic is complex with multiple sub-values, (2) next state depends on previous state, (3) you have many state transitions, or (4) you want to centralize update logic. Good for forms, wizards, and state machines.

See: [[2. React Hooks/2.5 useReducer]]

</details>

### Q: What is the React Fiber architecture?

<details>
<summary>Answer</summary>

Fiber is React's reconciliation algorithm (React 16+). Each component instance has a Fiber node—a lightweight JS object representing a unit of work. Fiber enables incremental rendering, prioritization, and concurrent features like `useTransition` and `useDeferredValue`.

See: [[12. Performance/6.1 React Rendering Model]]

</details>

### Q: How does useOptimistic work?

<details>
<summary>Answer</summary>

`useOptimistic` lets you show an optimistic UI before a server action completes. You pass the current state and an updater function. It returns `[optimisticState, addOptimistic]`—call `addOptimistic` with the expected result, then revert when the real response arrives.

See: [[2. React Hooks/2.11 React v19 Hooks/2.11.4 useOptimistic]]

</details>

### Q: What is use() and when would you use it?

<details>
<summary>Answer</summary>

`use()` (React 19) unwraps promises and context. Unlike `useEffect`, it can be used in render and integrates with Suspense—the component suspends until the promise resolves. Use it for data fetching in Client Components with Suspense boundaries.

See: [[2. React Hooks/2.11 React v19 Hooks/2.11.1 use()]] | [[4. Data Fetching/4.4 Suspense for Data]]

</details>

### Q: How does useActionState differ from useTransition for forms?

<details>
<summary>Answer</summary>

`useActionState` (React 19) wraps a server action and returns `[state, formAction]`—state holds the action's return value (e.g. validation errors). It's designed for form submissions. `useTransition` gives `[isPending, startTransition]` for marking updates as non-urgent.

See: [[2. React Hooks/2.11 React v19 Hooks/2.11.2 useActionState]] | [[6. Server Components/6.2 Server Actions]]

</details>

### Q: When would you use useTransition?

<details>
<summary>Answer</summary>

Use `useTransition` when you have state updates that are low-priority (e.g. filtering a list, switching tabs). Wrap the update in `startTransition`—React keeps the current UI responsive and applies the update when possible. Good for improving perceived performance.

See: [[2. React Hooks/2.11 React v19 Hooks/2.11.5 useTransition]] | [[12. Performance/6.5 Web Vitals]]

</details>

### Q: How do you implement protected routes in React Router?

<details>
<summary>Answer</summary>

Create a wrapper component that checks auth (e.g. from context or a hook). If authenticated, render `<Outlet />` (or `children`); otherwise redirect to login. Use `Navigate` or `redirect()` for the redirect logic.

See: [[3. Routing/3.3 Protected Routes]]

</details>

### Q: What are the trade-offs between TanStack Query and SWR for data fetching?

<details>
<summary>Answer</summary>

**TanStack Query:** More features (mutations, devtools, cache invalidation, optimistic updates). **SWR:** Simpler API, smaller bundle. Both handle caching, revalidation, and loading/error states. Choose TanStack Query for complex apps, SWR for simpler ones.

See: [[4. Data Fetching/4.2 TanStack Query]] | [[4. Data Fetching/4.3 SWR]]

</details>

### Q: How do you handle form validation with React Hook Form?

<details>
<summary>Answer</summary>

Use `register` with validation rules (`required`, `minLength`, `pattern`, etc.) or schema validation (Zod, Yup) via `useForm`'s `resolver`. Access errors via `formState.errors`. For server actions, combine with `useActionState` for server-side validation.

See: [[5. Forms/5.2 React Hook Form]] | [[5. Forms/5.3 Validation Patterns]]

</details>

### Q: What is code splitting and how do you implement it in React?

<details>
<summary>Answer</summary>

Code splitting splits your bundle so users only load what they need. Use `React.lazy()` with `Suspense` for component-level splitting, or dynamic `import()` for route-based splitting. Lazy routes load components only when the route is visited.

See: [[12. Performance/6.3 Code Splitting]] | [[3. Routing/3.4 Lazy Routes]]

</details>

### Q: How do custom hooks help with logic reuse?

<details>
<summary>Answer</summary>

Custom hooks are functions that use other hooks. They encapsulate stateful logic (e.g. `useAuth`, `useLocalStorage`, `useDebounce`) and can be shared across components. They follow the Rules of Hooks and keep components focused on rendering.

See: [[2. React Hooks/2.9 Custom Hooks]] | [[9. React Patterns/9.3 Custom Hooks Patterns]]

</details>

### Q: What is the compound component pattern?

<details>
<summary>Answer</summary>

Compound components are a set of components that work together (e.g. `Select`, `Select.Option`, `Select.Trigger`). They share implicit state via Context. The parent provides the API; children compose the UI. Good for flexible, customizable components like tabs or dropdowns.

See: [[9. React Patterns/9.1 Compound Components]]

</details>

### Q: When would you use a HOC vs a custom hook?

<details>
<summary>Answer</summary>

**HOC:** Wraps a component to add props or behavior. Use when you need to inject props or wrap with providers. **Custom hook:** Extracts logic; the component calls it directly. Prefer hooks—they avoid wrapper hell and are easier to compose. Use HOCs for cross-cutting concerns (e.g. `withAuth`).

See: [[9. React Patterns/9.2 Render Props, HOCs, Hooks]]

</details>

### Q: How do you ensure accessibility in a React app?

<details>
<summary>Answer</summary>

Use semantic HTML (`<button>`, `<nav>`, `<main>`), ARIA attributes when needed (`aria-label`, `aria-expanded`), keyboard navigation, focus management (e.g. trap focus in modals), and sufficient color contrast. Test with screen readers and axe-core.

See: [[8. Accessibility/8.1 ARIA and Semantic HTML]] | [[8. Accessibility/8.2 Focus Management]] | [[8. Accessibility/8.3 Testing Accessibility]]

</details>

### Q: What are Server Actions and how do they work?

<details>
<summary>Answer</summary>

Server Actions are async functions that run on the server. They can be passed to form `action` or called from Client Components. They handle mutations (create, update, delete) and return serializable data. Use with `useActionState` for form state and errors.

See: [[6. Server Components/6.2 Server Actions]]

</details>

### Q: How does streaming with Suspense improve UX?

<details>
<summary>Answer</summary>

Streaming sends HTML as it's ready instead of waiting for the full page. Suspense boundaries show fallbacks (e.g. skeletons) while async components load. Users see content progressively instead of a blank screen. Works with RSC and `use()` for data.

See: [[6. Server Components/6.3 Streaming and Suspense]]

</details>

### Q: What are the main styling approaches in React and when to use each?

<details>
<summary>Answer</summary>

**CSS Modules:** Scoped CSS, no runtime cost. **Tailwind:** Utility-first, fast iteration, purges unused styles. **CSS-in-JS (styled-components, Emotion):** Dynamic styles, theming, component-scoped. Choose based on team preference and need for dynamic styles.

See: [[7. Styling/7.1 CSS Modules]] | [[7. Styling/7.2 Tailwind CSS]] | [[7. Styling/7.3 CSS-in-JS]]

</details>

### Q: How do you test a component that uses hooks and context?

<details>
<summary>Answer</summary>

Wrap the component in the necessary providers when rendering. Use `@testing-library/react`'s `render` with a custom wrapper. Mock context values or use a real provider with test data. For hooks in isolation, use `renderHook` from `@testing-library/react`.

See: [[11. Testing/5.2 Component Testing]] | [[11. Testing/5.5 Mocking Strategies]]

</details>

---

## Hard

### Q: How would you debug unnecessary re-renders in a large component tree?

<details>
<summary>Answer</summary>

Use React DevTools Profiler to record and inspect renders. Add `console.log` or `React DevTools` "Highlight updates" to see what re-renders. Check: (1) unstable props/children (inline objects, arrow functions), (2) context consumers, (3) parent re-renders. Fix with `React.memo`, `useCallback`, `useMemo`, or splitting context.

See: [[12. Performance/6.1 React Rendering Model]] | [[12. Performance/6.2 Memoization]]

</details>

### Q: When does useCallback actually prevent re-renders?

<details>
<summary>Answer</summary>

`useCallback` only helps when the child component is memoized (`React.memo`) and receives the callback as a prop. If the child isn't memoized, it re-renders anyway when the parent re-renders. The callback reference must be stable for memo to skip the child.

See: [[2. React Hooks/2.6 useCallback]] | [[12. Performance/6.2 Memoization]]

</details>

### Q: How would you implement virtualization and when is it necessary?

<details>
<summary>Answer</summary>

Virtualization renders only visible rows/items (e.g. with `react-window` or `@tanstack/react-virtual`). Use when you have long lists (100+ items) that cause layout thrashing. The list container has fixed height; only items in viewport are in the DOM.

See: [[12. Performance/6.4 Virtualization]]

</details>

### Q: How do you structure state for a complex form with nested fields and conditional sections?

<details>
<summary>Answer</summary>

Use `useReducer` or a form library (React Hook Form, Formik). Model state as a nested object; use dot-path or array indices for field names. For conditional sections, derive visibility from state and only validate visible fields. Consider splitting into sub-forms with local state.

See: [[5. Forms/5.1 Controlled vs Uncontrolled]] | [[5. Forms/5.3 Validation Patterns]] | [[2. React Hooks/2.5 useReducer]]

</details>

### Q: How would you implement optimistic updates with TanStack Query?

<details>
<summary>Answer</summary>

Use `onMutate` to update the cache optimistically before the request completes. Store the previous data with `queryClient.getQueryData`. In `onError`, roll back with `queryClient.setQueryData`. In `onSettled`, invalidate to refetch. Or use `useOptimistic` with server actions.

See: [[10. State Management/4.6 Server State with TanStack Query]] | [[2. React Hooks/2.11 React v19 Hooks/2.11.4 useOptimistic]]

</details>

### Q: What's the difference between useEffect cleanup and useLayoutEffect?

<details>
<summary>Answer</summary>

`useEffect` runs after paint (asynchronous); `useLayoutEffect` runs synchronously after DOM mutations but before paint. Use `useLayoutEffect` for DOM measurements or when you need to prevent visual flicker. Both support cleanup—return a function that runs before the next effect or on unmount.

See: [[2. React Hooks/2.3 useEffect]] | [[2. React Hooks/2.11 React v19 Hooks/2.11.7 useLayoutEffect & useInsertionEffect]]

</details>

### Q: How do you handle authentication state across the app with minimal re-renders?

<details>
<summary>Answer</summary>

Split context: one for auth state (user, token), one for auth actions (login, logout). Memoize the value passed to Provider. Use a library like Zustand or Jotai for granular subscriptions so only components that need auth state re-render. Consider storing tokens in httpOnly cookies.

See: [[10. State Management/4.1 React Built-in State]] | [[9. React Patterns/9.4 Context API Patterns]] | [[14. Real-World Examples/8.4 Authentication Flow]]

</details>

### Q: When would you choose Redux vs Zustand vs Jotai for state management?

<details>
<summary>Answer</summary>

**Redux:** Complex global state, time-travel debugging, middleware (logging, persistence). **Zustand:** Simpler API, minimal boilerplate, good for medium-sized apps. **Jotai:** Atomic state, fine-grained subscriptions, good for derived state. Prefer Zustand/Jotai for most apps; Redux when you need its ecosystem.

See: [[10. State Management/4.2 Redux Toolkit]] | [[10. State Management/4.3 Zustand]] | [[10. State Management/4.4 Jotai]]

</details>

### Q: How do you test async behavior and data fetching in React components?

<details>
<summary>Answer</summary>

Use `waitFor` and `findBy*` queries from Testing Library for async assertions. Mock fetch/API with MSW (Mock Service Worker) for realistic network behavior. For TanStack Query, wrap in `QueryClientProvider`. Avoid testing implementation details; assert on user-visible outcomes.

See: [[11. Testing/5.3 Integration Testing]] | [[11. Testing/5.5 Mocking Strategies]]

</details>

### Q: How would you migrate a class component to a function component with hooks?

<details>
<summary>Answer</summary>

Map `this.state` to `useState` (or `useReducer` for complex state). Map lifecycle methods: `componentDidMount` → `useEffect` with `[]`, `componentDidUpdate` → `useEffect` with deps, `componentWillUnmount` → cleanup in `useEffect`. Refactor `this.props` to function params. Extract logic to custom hooks if needed.

See: [[2. React Hooks/2. React Hooks]] | [[1. React Core Concepts/1.1 Components]]

</details>

### Q: What is useDeferredValue and how does it differ from useTransition?

<details>
<summary>Answer</summary>

`useDeferredValue` defers updating a value (e.g. search input passed to a slow list). React keeps showing the old value until it can update. `useTransition` marks state updates as transitions. Both help keep the UI responsive during expensive updates. `useDeferredValue` is for deferring a value; `useTransition` is for deferring an update.

See: [[2. React Hooks/2.11 React v19 Hooks/2.11.6 useDeferredValue]] | [[2. React Hooks/2.11 React v19 Hooks/2.11.5 useTransition]]

</details>

### Q: How do you implement E2E tests for a React app with authentication?

<details>
<summary>Answer</summary>

Use Playwright or Cypress. Store auth state (e.g. localStorage, cookies) and reuse it via fixtures or `beforeEach` to avoid logging in for every test. Use `storageState` (Playwright) or `cy.session` (Cypress) to persist auth. Test critical flows: login, protected routes, logout.

See: [[11. Testing/5.4 E2E Testing]] | [[14. Real-World Examples/8.4 Authentication Flow]]

</details>

### Q: How would you structure a large React app for scalability (folder structure, boundaries)?

<details>
<summary>Answer</summary>

Use Feature-Sliced Design or similar: layers (app, features, entities, shared) and slices within features. Colocate components, hooks, and types per feature. Keep shared code in `shared/`. Use clear boundaries: features don't import from each other; shared has no feature imports. Consider FSD for strict scalability.

See: [[14. Real-World Examples/8.1 Todo App (FSD)]] | [[9. React Patterns/9. React Patterns]]

</details>

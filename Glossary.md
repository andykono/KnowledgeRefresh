# Frontend Glossary

An alphabetical reference of key terms used across this vault.

---

## A

- **ARIA** — Accessible Rich Internet Applications; a set of attributes that make web content accessible to assistive technologies. [[8.1 ARIA and Semantic HTML]]
- **Atomic State** — State that is indivisible and updated as a single unit; contrasts with derived state. [[4.1 React Built-in State]]
- **Async/Await** — Syntax for handling Promises in a synchronous style; used for data fetching and async operations. [[4.1 Fetch and Axios Patterns]]
- **API** — Application Programming Interface; the contract for how client and server communicate. [[4.1 Fetch and Axios Patterns]]
- **A11y** — Shorthand for accessibility (11 letters between A and y); making apps usable by everyone. [[8. Accessibility]]

## B

- **Bundler** — Tool that combines modules into optimized bundles (e.g., Vite, Webpack). [[7.1 Vite]]
- **Branded Types** — TypeScript pattern using unique symbols to distinguish otherwise identical types. [[2.4 Advanced Types]]

## C

- **CLS** — Cumulative Layout Shift; Web Vital measuring visual stability; low CLS means less unexpected layout movement. [[6.5 Web Vitals]]
- **CORS** — Cross-Origin Resource Sharing; browser mechanism controlling cross-origin requests. [[4.1 Fetch and Axios Patterns]]
- **CSS-in-JS** — Styling approach where CSS is written in JavaScript (e.g., styled-components). [[7.3 CSS-in-JS]]
- **CSS Modules** — Scoped CSS where class names are locally unique to avoid conflicts. [[7.1 CSS Modules]]
- **Component** — Reusable, composable UI unit; the building block of React applications. [[1. React Core Concepts]]
- **Context API** — React's built-in way to share state globally without prop drilling. [[1.9 Context API]]
- **Code Splitting** — Splitting bundle into smaller chunks loaded on demand to improve initial load. [[6.3 Code Splitting]]
- **CRUD** — Create, Read, Update, Delete; the four basic operations for persistent data. [[4. Data Fetching]]
- **Compound Components** — Pattern where components work together as a group (e.g., Tabs + TabPanel). [[9.1 Compound Components]]

## D

- **Discriminated Union** — TypeScript union type with a common discriminant property for type narrowing. [[2.4 Advanced Types]]
- **DX** — Developer Experience; how pleasant and productive it is to work with a tool or framework.
- **Debounce** — Delaying execution until after a pause in input; useful for search inputs. [[5. Forms]]
- **Derived State** — State computed from other state rather than stored directly. [[4.1 React Built-in State]]

## E

- **E2E** — End-to-end testing; tests that run against the full application in a real browser. [[5.4 E2E Testing]]
- **Error Boundary** — React component that catches JavaScript errors in its child tree. [[1.7 Error Boundaries]]
- **ESLint** — Linter that finds and fixes problems in JavaScript/TypeScript code. [[7.3 ESLint and Prettier]]

## F

- **FCP** — First Contentful Paint; when the first content appears on screen. [[6.5 Web Vitals]]
- **FID** — First Input Delay; deprecated metric replaced by INP for measuring responsiveness. [[6.5 Web Vitals]]
- **FSD** — Feature-Sliced Design; architectural methodology for frontend project structure. [[8.1 Todo App (FSD)]]
- **Fiber** — React's internal reconciliation algorithm and data structure for the component tree. [[6.1 React Rendering Model]]
- **forwardRef** — React API for passing refs through components to DOM elements. [[1.5 Keys and Refs]]

## G

- **Generic** — TypeScript feature for reusable type parameters; `function identity<T>(x: T): T`. [[2.1 TypeScript Fundamentals]]
- **Guard (route)** — Component that protects routes from unauthorized access. [[3.3 Protected Routes]]

## H

- **HOC** — Higher-Order Component; function that takes a component and returns an enhanced component. [[9.2 Render Props, HOCs, Hooks]]
- **Hydration** — Process where React attaches event listeners to server-rendered HTML. [[6.1 Server vs Client]]
- **Hook** — React function (useState, useEffect, etc.) that lets you use state and other features in function components. [[2. React Hooks]]

## I

- **INP** — Interaction to Next Paint; Web Vital measuring responsiveness to user input. [[6.5 Web Vitals]]
- **ISR** — Incremental Static Regeneration; hybrid of SSG and SSR used in Next.js. [[7.2 Next.js Basics]]
- **Immutable** — Data that cannot be changed after creation; React state updates should be immutable. [[4.1 React Built-in State]]
- **Interceptor** — Middleware that runs before/after HTTP requests (e.g., adding auth headers). [[4.1 Fetch and Axios Patterns]]

## J

- **JSX** — JavaScript XML; syntax extension for writing HTML-like code in JavaScript. [[2.2 Typing React Components]]
- **JWT** — JSON Web Token; compact token format for authentication. [[8.4 Authentication Flow]]
- **Jest** — JavaScript testing framework; often used with React Testing Library. [[5.1 Unit Testing]]

## K

- **Key (React)** — Special prop that helps React identify which items changed in lists. [[1.5 Keys and Refs]]

## L

- **LCP** — Largest Contentful Paint; Web Vital measuring when the main content is visible. [[6.5 Web Vitals]]
- **Lazy Loading** — Loading components or data only when needed. [[3.4 Lazy Routes]]
- **Live Region** — ARIA region that announces dynamic content changes to screen readers. [[8.1 ARIA and Semantic HTML]]

## M

- **Memoization** — Caching computed values to avoid redundant work; useMemo, useCallback, React.memo. [[6.2 Memoization]]
- **MSW** — Mock Service Worker; intercepts network requests for testing. [[5.5 Mocking Strategies]]
- **Middleware** — Code that runs between request and response; used in routing and API layers. [[3. Routing]]
- **Mutation** — Operation that changes server data (create, update, delete). [[4.2 TanStack Query]]

## O

- **Optimistic Update** — Updating UI before server confirms; rollback on error. [[4.2 TanStack Query]]
- **Observer Pattern** — Design pattern where objects subscribe to and react to state changes. [[1. Patterns]]

## P

- **Portal** — Renders children into a DOM node outside the parent hierarchy (e.g., modals). [[1.6 Portals]]
- **Prefetching** — Loading data before the user navigates to reduce perceived latency. [[4.2 TanStack Query]]
- **Progressive Enhancement** — Building core functionality first, then layering enhancements. [[8. Accessibility]]
- **Provider** — Component that supplies context values to descendants. [[1.9 Context API]]

## Q

- **Query Key** — Unique identifier for TanStack Query cache entries; enables invalidation. [[4.2 TanStack Query]]
- **Query Client** — TanStack Query's central cache and configuration object. [[4.2 TanStack Query]]

## R

- **RSC** — React Server Components; components that run only on the server. [[6. Server Components]]
- **RTK** — Redux Toolkit; official Redux package with simplified patterns. [[4.2 Redux Toolkit]]
- **Reconciliation** — React's process of comparing virtual DOM trees to update the real DOM. [[6.1 React Rendering Model]]
- **Reducer** — Pure function `(state, action) => newState`; used in useReducer and Redux. [[2.5 useReducer]]
- **Ref** — Mutable object that persists across renders; used for DOM access or storing values. [[1.5 Keys and Refs]]
- **Render Prop** — Pattern where a component receives a function as children to render content. [[9.2 Render Props, HOCs, Hooks]]
- **Revalidation** — Refetching data to ensure it's fresh; used in SWR and TanStack Query. [[4.2 TanStack Query]]

## S

- **SSR** — Server-Side Rendering; rendering HTML on the server for each request. [[6. Server Components]]
- **SSG** — Static Site Generation; pre-rendering pages at build time. [[7.2 Next.js Basics]]
- **SWR** — Stale-While-Revalidate; data fetching library by Vercel. [[4.3 SWR]]
- **Suspense** — React feature for declarative loading states and streaming. [[6.3 Streaming and Suspense]]
- **Server Action** — Async function that runs on the server; used for mutations in RSC. [[6.2 Server Actions]]
- **Singleton** — Design pattern ensuring only one instance exists. [[1. Patterns]]
- **State Machine** — Explicit model of states and transitions; XState implements this. [[4.5 XState]]
- **Strategy Pattern** — Design pattern for interchangeable algorithms. [[1. Patterns]]

## T

- **TanStack Query** — Library for server state: caching, fetching, mutations. [[4.2 TanStack Query]]
- **Throttle** — Limiting how often a function runs (e.g., scroll handlers). [[5. Forms]]
- **Transition** — React 18+ API for marking updates as non-urgent. [[6.1 React Rendering Model]]
- **Tree Shaking** — Build step that removes unused code from the bundle. [[7.1 Vite]]
- **Type Guard** — Function that narrows types at runtime; `x is Type`. [[2.4 Advanced Types]]
- **Type Narrowing** — TypeScript inferring a more specific type from checks. [[2.4 Advanced Types]]

## U

- **Utility Types** — Built-in TypeScript types like Partial, Pick, Omit for type transformations. [[2.4 Advanced Types]]
- **useEffect** — Hook for side effects (data fetching, subscriptions) after render. [[2.3 useEffect]]
- **useState** — Hook for local component state. [[2.2 useState]]

## V

- **Virtual DOM** — In-memory representation of the DOM; React diffs it for efficient updates. [[6.1 React Rendering Model]]
- **Virtualization** — Rendering only visible items in long lists for performance. [[6.4 Virtualization]]
- **Vitest** — Fast unit test framework for Vite projects. [[5.1 Unit Testing]]

## W

- **Web Vitals** — Core metrics (LCP, INP, CLS) that measure user experience. [[6.5 Web Vitals]]
- **WebSocket** — Protocol for bidirectional real-time communication. [[8.3 Real-time Chat App]]
- **Windowing** — Same as virtualization; rendering a window of items in long lists. [[6.4 Virtualization]]

## X

- **XState** — Library for state machines and statecharts in JavaScript. [[4.5 XState]]

## Z

- **Zustand** — Minimal state management library with a simple API. [[4.3 Zustand]]
- **Zod** — TypeScript-first schema validation library. [[5.3 Validation Patterns]]

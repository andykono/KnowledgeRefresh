# Frontend Glossary

An alphabetical reference of key terms used across this vault.

---

## A

- **ARIA** — Accessible Rich Internet Applications; a set of attributes that make web content accessible to assistive technologies. [[1. React/8. Accessibility/8.1 ARIA and Semantic HTML]]
- **Atomic State** — State that is indivisible and updated as a single unit; contrasts with derived state. [[1. React/10. State Management/4.1 React Built-in State]]
- **Async/Await** — Syntax for handling Promises in a synchronous style; used for data fetching and async operations. [[1. React/4. Data Fetching/4.1 Fetch and Axios Patterns]]
- **API** — Application Programming Interface; the contract for how client and server communicate. [[1. React/4. Data Fetching/4.1 Fetch and Axios Patterns]]
- **A11y** — Shorthand for accessibility (11 letters between A and y); making apps usable by everyone. [[1. React/8. Accessibility/8. Accessibility]]
- **Availability** — System design property; system remains operational. CAP theorem trade-off with consistency. [[6. System Design/6. Trade-offs]]

## B

- **Big O** — Notation describing algorithm complexity; O(1), O(n), O(n²), O(log n). [[5. FED/3. JavaScript/6. Data structures & algorithms/3. big O]]
- **Bundler** — Tool that combines modules into optimized bundles (e.g., Vite, Webpack). [[1. React/13. Tooling & Build/7.1 Vite]]
- **Branded Types** — TypeScript pattern using unique symbols to distinguish otherwise identical types. [[2. TypeScript/2.4 Advanced Types]]

## C

- **CAP Theorem** — Distributed systems: can guarantee only 2 of 3 — Consistency, Availability, Partition tolerance. [[6. System Design/6. Trade-offs]]
- **CLS** — Cumulative Layout Shift; Web Vital measuring visual stability; low CLS means less unexpected layout movement. [[1. React/12. Performance/6.5 Web Vitals]]
- **CORS** — Cross-Origin Resource Sharing; browser mechanism controlling cross-origin requests. [[1. React/4. Data Fetching/4.1 Fetch and Axios Patterns]]
- **CSP** — Content Security Policy; HTTP header restricting script sources to prevent XSS. [[5. FED/6. Security/1. security]]
- **CSRF** — Cross-Site Request Forgery; attacker tricks user's browser into making unwanted requests. [[5. FED/6. Security/1. security]]
- **CQRS** — Command Query Responsibility Segregation; separate read and write models for scalability. [[6. System Design/1. Scalability]]
- **CSS-in-JS** — Styling approach where CSS is written in JavaScript (e.g., styled-components). [[1. React/7. Styling/7.3 CSS-in-JS]]
- **CSS Modules** — Scoped CSS where class names are locally unique to avoid conflicts. [[1. React/7. Styling/7.1 CSS Modules]]
- **Component** — Reusable, composable UI unit; the building block of React applications. [[1. React/1. React Core Concepts/1. React Core Concepts]]
- **Context API** — React's built-in way to share state globally without prop drilling. [[1. React/1. React Core Concepts/1.9 Context API]]
- **Code Splitting** — Splitting bundle into smaller chunks loaded on demand to improve initial load. [[1. React/12. Performance/6.3 Code Splitting]]
- **CRUD** — Create, Read, Update, Delete; the four basic operations for persistent data. [[1. React/4. Data Fetching/4. Data Fetching]]
- **Compound Components** — Pattern where components work together as a group (e.g., Tabs + TabPanel). [[1. React/9. React Patterns/9.1 Compound Components]]
- **Critical Rendering Path** — Sequence of steps browser takes to render a page (HTML → DOM → CSSOM → Render tree → Layout → Paint). [[5. FED/3. JavaScript/5. Performance/3. critical rendering path]]
- **Consistency** — System design property; all nodes see the same data. CAP theorem trade-off. [[6. System Design/6. Trade-offs]]

## D

- **Debounce** — Delaying execution until after a pause in input; useful for search, resize. [[4. Common/debounce]]
- **Discriminated Union** — TypeScript union type with a common discriminant property for type narrowing. [[2. TypeScript/2.4 Advanced Types]]
- **DX** — Developer Experience; how pleasant and productive it is to work with a tool or framework.
- **Derived State** — State computed from other state rather than stored directly. [[1. React/10. State Management/4.1 React Built-in State]]
- **DOMPurify** — Library for sanitizing HTML to prevent XSS. [[5. FED/6. Security/1. security]]

## E

- **E2E** — End-to-end testing; tests that run against the full application in a real browser. [[1. React/11. Testing/5.4 E2E Testing]]
- **Error Boundary** — React component that catches JavaScript errors in its child tree. [[1. React/1. React Core Concepts/1.7 Error Boundaries]]
- **ESLint** — Linter that finds and fixes problems in JavaScript/TypeScript code. [[1. React/13. Tooling & Build/7.3 ESLint and Prettier]]
- **Event Loop** — JavaScript mechanism for handling async operations; call stack, task queue, microtasks. [[4. Common/Event loop]] [[4. Common/1. JS some cases/1. event loop promise]]
- **Event Delegation** — Attaching one listener to a parent to handle events from children. [[5. FED/3. JavaScript/3. DOM manipulation/3. event delegation]]
- **EventEmitter** — Pub/sub pattern for decoupled communication. [[4. Common/EventEmmiter]]

## F

- **FCP** — First Contentful Paint; when the first content appears on screen. [[1. React/12. Performance/6.5 Web Vitals]]
- **FID** — First Input Delay; deprecated metric replaced by INP for measuring responsiveness. [[1. React/12. Performance/6.5 Web Vitals]]
- **FSD** — Feature-Sliced Design; architectural methodology for frontend project structure. [[1. React/14. Real-World Examples/8.1 Todo App (FSD)]]
- **Fiber** — React's internal reconciliation algorithm and data structure for the component tree. [[1. React/12. Performance/6.1 React Rendering Model]]
- **forwardRef** — React API for passing refs through components to DOM elements. [[1. React/1. React Core Concepts/1.5 Keys and Refs]]
- **Flexbox** — CSS layout model for one-dimensional layouts. [[5. FED/2. CSS/1. Layout (Flexbox, Grid)]]

## G

- **Generic** — TypeScript feature for reusable type parameters; `function identity<T>(x: T): T`. [[2. TypeScript/2.1 TypeScript Fundamentals]]
- **Grid** — CSS layout for two-dimensional layouts. [[5. FED/2. CSS/1. Layout (Flexbox, Grid)]]
- **Guard (route)** — Component that protects routes from unauthorized access. [[1. React/3. Routing/3.3 Protected Routes]]

## H

- **HOC** — Higher-Order Component; function that takes a component and returns an enhanced component. [[1. React/9. React Patterns/9.2 Render Props, HOCs, Hooks]]
- **Hydration** — Process where React attaches event listeners to server-rendered HTML. [[1. React/6. Server Components/6.1 Server vs Client]]
- **Hook** — React function (useState, useEffect, etc.) that lets you use state and other features in function components. [[1. React/2. React Hooks/2. React Hooks]]
- **Horizontal Scaling** — Adding more servers/instances; scale out. [[6. System Design/1. Scalability]]

## I

- **INP** — Interaction to Next Paint; Web Vital measuring responsiveness to user input. [[1. React/12. Performance/6.5 Web Vitals]]
- **ISR** — Incremental Static Regeneration; hybrid of SSG and SSR used in Next.js. [[1. React/13. Tooling & Build/7.2 Next.js Basics]]
- **Immutable** — Data that cannot be changed after creation; React state updates should be immutable. [[1. React/10. State Management/4.1 React Built-in State]]
- **Interceptor** — Middleware that runs before/after HTTP requests (e.g., adding auth headers). [[1. React/4. Data Fetching/4.1 Fetch and Axios Patterns]]

## J

- **JSX** — JavaScript XML; syntax extension for writing HTML-like code in JavaScript. [[2. TypeScript/2.2 Typing React Components]]
- **JWT** — JSON Web Token; compact token format for authentication. [[1. React/14. Real-World Examples/8.4 Authentication Flow]]
- **Jest** — JavaScript testing framework; often used with React Testing Library. [[1. React/11. Testing/5.1 Unit Testing]]

## K

- **Key (React)** — Special prop that helps React identify which items changed in lists. [[1. React/1. React Core Concepts/1.5 Keys and Refs]]

## L

- **LCP** — Largest Contentful Paint; Web Vital measuring when the main content is visible. [[1. React/12. Performance/6.5 Web Vitals]]
- **Lazy Loading** — Loading components or data only when needed. [[1. React/3. Routing/3.4 Lazy Routes]]
- **Live Region** — ARIA region that announces dynamic content changes to screen readers. [[1. React/8. Accessibility/8.1 ARIA and Semantic HTML]]
- **Load Balancer** — Distributes incoming requests across multiple servers. [[6. System Design/1. Scalability]]

## M

- **Memoization** — Caching computed values to avoid redundant work; useMemo, useCallback, React.memo. [[1. React/12. Performance/6.2 Memoization]]
- **Microtask** — Asynchronous task with higher priority than macrotasks; Promise.then, queueMicrotask, MutationObserver. [[4. Common/1. JS some cases/1. event loop promise]]
- **MSW** — Mock Service Worker; intercepts network requests for testing. [[1. React/11. Testing/5.5 Mocking Strategies]]
- **Middleware** — Code that runs between request and response; used in routing and API layers. [[1. React/3. Routing/3. Routing]]
- **Mutation** — Operation that changes server data (create, update, delete). [[1. React/4. Data Fetching/4.2 TanStack Query]]
- **Modularity** — Separation of concerns; clear boundaries between system parts. [[6. System Design/2. Modularity]]

## O

- **Optimistic Update** — Updating UI before server confirms; rollback on error. [[1. React/4. Data Fetching/4.2 TanStack Query]]
- **Observer Pattern** — Design pattern where objects subscribe to and react to state changes. [[3. Patterns/1. Design Patterns/1. Patterns]]

## P

- **Promise** — JavaScript object representing eventual completion or failure of an async operation; states: pending, fulfilled, rejected. [[5. FED/3. JavaScript/2. ES6 features/1. Promises, async-await]]
- **Promise Executor** — Callback function passed to Promise constructor; runs synchronously and receives resolve/reject. [[4. Common/1. JS some cases/1. event loop promise]]
- **Portal** — Renders children into a DOM node outside the parent hierarchy (e.g., modals). [[1. React/1. React Core Concepts/1.6 Portals]]
- **Prefetching** — Loading data before the user navigates to reduce perceived latency. [[1. React/4. Data Fetching/4.2 TanStack Query]]
- **Progressive Enhancement** — Building core functionality first, then layering enhancements. [[1. React/8. Accessibility/8. Accessibility]]
- **Provider** — Component that supplies context values to descendants. [[1. React/1. React Core Concepts/1.9 Context API]]

## Q

- **Query Key** — Unique identifier for TanStack Query cache entries; enables invalidation. [[1. React/4. Data Fetching/4.2 TanStack Query]]
- **Query Client** — TanStack Query's central cache and configuration object. [[1. React/4. Data Fetching/4.2 TanStack Query]]

## R

- **RSC** — React Server Components; components that run only on the server. [[1. React/6. Server Components/6. Server Components]]
- **RTK** — Redux Toolkit; official Redux package with simplified patterns. [[1. React/10. State Management/4.2 Redux Toolkit]]
- **Reconciliation** — React's process of comparing virtual DOM trees to update the real DOM. [[1. React/12. Performance/6.1 React Rendering Model]]
- **Reducer** — Pure function `(state, action) => newState`; used in useReducer and Redux. [[1. React/2. React Hooks/2.5 useReducer]]
- **Ref** — Mutable object that persists across renders; used for DOM access or storing values. [[1. React/1. React Core Concepts/1.5 Keys and Refs]]
- **Render Prop** — Pattern where a component receives a function as children to render content. [[1. React/9. React Patterns/9.2 Render Props, HOCs, Hooks]]
- **Revalidation** — Refetching data to ensure it's fresh; used in SWR and TanStack Query. [[1. React/4. Data Fetching/4.2 TanStack Query]]

## S

- **SSR** — Server-Side Rendering; rendering HTML on the server for each request. [[1. React/6. Server Components/6. Server Components]]
- **SSG** — Static Site Generation; pre-rendering pages at build time. [[1. React/13. Tooling & Build/7.2 Next.js Basics]]
- **SWR** — Stale-While-Revalidate; data fetching library by Vercel. [[1. React/4. Data Fetching/4.3 SWR]]
- **Suspense** — React feature for declarative loading states and streaming. [[1. React/6. Server Components/6.3 Streaming and Suspense]]
- **Server Action** — Async function that runs on the server; used for mutations in RSC. [[1. React/6. Server Components/6.2 Server Actions]]
- **Singleton** — Design pattern ensuring only one instance exists. [[3. Patterns/1. Design Patterns/1. Patterns]]
- **State Machine** — Explicit model of states and transitions; XState implements this. [[1. React/10. State Management/4.5 XState]]
- **Strategy Pattern** — Design pattern for interchangeable algorithms. [[3. Patterns/1. Design Patterns/1. Patterns]]
- **Sharding** — Partitioning data across multiple databases by key (e.g., user_id). [[6. System Design/1. Scalability]]
- **Semantic HTML** — HTML elements that convey meaning (header, nav, main, article). [[5. FED/1. HTML/Semantic HTML]]
- **Specificity** — CSS rule that determines which styles apply when rules conflict. [[5. FED/2. CSS/3. Specificity]]

## T

- **TanStack Query** — Library for server state: caching, fetching, mutations. [[1. React/4. Data Fetching/4.2 TanStack Query]]
- **Throttle** — Limiting how often a function runs (e.g., scroll handlers). [[5. FED/3. JavaScript/5. Performance/1. Debouncing, throttling]]
- **Transition** — React 18+ API for marking updates as non-urgent. [[1. React/12. Performance/6.1 React Rendering Model]]
- **Tree Shaking** — Build step that removes unused code from the bundle. [[1. React/13. Tooling & Build/7.1 Vite]]
- **Type Guard** — Function that narrows types at runtime; `x is Type`. [[2. TypeScript/2.4 Advanced Types]]
- **Type Narrowing** — TypeScript inferring a more specific type from checks. [[2. TypeScript/2.4 Advanced Types]]

## U

- **Utility Types** — Built-in TypeScript types like Partial, Pick, Omit for type transformations. [[2. TypeScript/2.4 Advanced Types]]
- **useEffect** — Hook for side effects (data fetching, subscriptions) after render. [[1. React/2. React Hooks/2.3 useEffect]]
- **useState** — Hook for local component state. [[1. React/2. React Hooks/2.2 useState]]

## V

- **Virtual DOM** — In-memory representation of the DOM; React diffs it for efficient updates. [[1. React/12. Performance/6.1 React Rendering Model]]
- **Virtualization** — Rendering only visible items in long lists for performance. [[1. React/12. Performance/6.4 Virtualization]]
- **Vertical Scaling** — Adding more CPU/RAM to a single server; scale up. [[6. System Design/1. Scalability]]
- **Vitest** — Fast unit test framework for Vite projects. [[1. React/11. Testing/5.1 Unit Testing]]

## W

- **Web Vitals** — Core metrics (LCP, INP, CLS) that measure user experience. [[1. React/12. Performance/6.5 Web Vitals]]
- **WebSocket** — Protocol for bidirectional real-time communication. [[1. React/14. Real-World Examples/8.3 Real-time Chat App]]
- **Windowing** — Same as virtualization; rendering a window of items in long lists. [[1. React/12. Performance/6.4 Virtualization]]
- **WCAG** — Web Content Accessibility Guidelines; standards for accessible web content. [[5. FED/5. Accessibility (a11y)/1. accessibility]]

## X

- **XState** — Library for state machines and statecharts in JavaScript. [[1. React/10. State Management/4.5 XState]]
- **XSS** — Cross-Site Scripting; injecting malicious scripts into pages. [[5. FED/6. Security/1. security]]

## Z

- **Zustand** — Minimal state management library with a simple API. [[1. React/10. State Management/4.3 Zustand]]
- **Zod** — TypeScript-first schema validation library. [[1. React/5. Forms/5.3 Validation Patterns]]

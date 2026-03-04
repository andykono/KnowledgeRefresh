# Design Patterns Interview Questions

Self-test questions organized by difficulty. Expand each answer to check your understanding.

---

## Easy

### Q: What is the Singleton pattern and when would you use it in a React app?

<details>
<summary>Answer</summary>

Singleton ensures only one instance of a class exists. Use it for shared resources: API client, auth service, WebSocket manager, or logger. In React, create a module that exports a single instance rather than a class with `getInstance()`.

See: [[1. Design Patterns/1.1 Singleton]]

</details>

### Q: What is the Factory pattern and give a React example?

<details>
<summary>Answer</summary>

Factory creates objects without specifying the exact class. In React: a component that renders different component types based on props (e.g. `type: 'button' | 'link' | 'icon'`). Or a function that returns the right hook/component based on configuration.

See: [[1. Design Patterns/1.2 Factory Method]]

</details>

### Q: What is the Observer pattern and how does it relate to React?

<details>
<summary>Answer</summary>

Observer defines a one-to-many dependency: when the subject changes, all observers are notified. React's Context API, custom hooks with `useState` (subscribers), and event-driven state (Zustand, Redux) all follow this pattern. Components "subscribe" to state and re-render when it changes.

See: [[1. Design Patterns/1.3 Observer]]

</details>

### Q: What is the Decorator pattern and how is it used in React?

<details>
<summary>Answer</summary>

Decorator adds behavior to an object without changing its structure. In React: **Higher-Order Components (HOCs)** like `withAuth(Component)` or `withTheme(Component)` wrap components to add props or behavior. Custom hooks can also wrap logic.

See: [[1. Design Patterns/1.4 Decorator]]

</details>

### Q: What is the Strategy pattern and when would you use it?

<details>
<summary>Answer</summary>

Strategy encapsulates algorithms in interchangeable objects. Use it when you have multiple ways to do something (sorting, filtering, validation, payment methods). Pass the strategy as a prop or function—e.g. sorting a table by different columns, or different validation rules per form field.

See: [[1. Design Patterns/1.5 Strategy]]

</details>

### Q: What is the Facade pattern?

<details>
<summary>Answer</summary>

Facade provides a simplified interface to a complex subsystem. Use it for API layers: a single `apiClient` that hides fetch, auth headers, error handling, and retries. Or a service that wraps multiple API calls into one high-level method.

See: [[1. Design Patterns/1.6 Facade]]

</details>

### Q: What is MVC and how does it differ from React's component model?

<details>
<summary>Answer</summary>

**MVC** separates Model (data), View (UI), and Controller (logic). React uses a component-based model where components combine view and logic. The "model" is often state (useState, Redux) or server state. React doesn't enforce MVC; it's more View + logic in a tree.

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: What is MVVM and how does it map to React?

<details>
<summary>Answer</summary>

**MVVM** separates Model (data), View (UI), and ViewModel (presentation logic). In React: View = components, ViewModel = custom hooks (e.g. `useUserViewModel`) that handle state and API calls, Model = services or API layer. Hooks act as the ViewModel.

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: What is an anti-pattern and why does it matter?

<details>
<summary>Answer</summary>

An anti-pattern is a common solution that causes more problems than it solves. Examples: prop drilling, missing useEffect cleanup, storing derived state. Recognizing anti-patterns helps you avoid bugs and technical debt.

See: [[3. Anti-Patterns/3. Anti-Patterns]]

</details>

### Q: What is prop drilling and how do you avoid it?

<details>
<summary>Answer</summary>

Prop drilling is passing props through many layers of components that don't use them. Avoid with: Context API, state management (Zustand, Redux), or composition (render props, compound components). Choose based on how often the data changes and who needs it.

See: [[3. Anti-Patterns/3.1 React Anti-Patterns]]

</details>

---

## Medium

### Q: When would you use Singleton vs a React Context for shared state?

<details>
<summary>Answer</summary>

**Singleton:** Stateless services (API client, logger) or shared state that doesn't need to trigger re-renders. **Context:** State that components need to react to (UI state, theme, auth). Use Context when React needs to re-render on change; use Singleton for services.

See: [[1. Design Patterns/1.1 Singleton]] | [[2. Architectural Patterns/2.2 State Management Patterns]]

</details>

### Q: How do you implement the Strategy pattern in a React form for validation?

<details>
<summary>Answer</summary>

Define validation strategies as functions: `(value: string) => string | null`. Pass different strategies per field (e.g. email validation, password strength). Use a schema (Zod, Yup) or a validation map. The form component doesn't need to know the validation logic—it just runs the strategy.

See: [[1. Design Patterns/1.5 Strategy]]

</details>

### Q: What is Clean Architecture and how does it apply to a React app?

<details>
<summary>Answer</summary>

Clean Architecture separates layers: Entities (core business rules) → Use Cases (application logic) → Interface Adapters (presenters, controllers) → Frameworks (React, API). In React: keep business logic in services; components use hooks that call services. Dependencies point inward (UI depends on logic, not vice versa).

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: What is Feature-Sliced Design (FSD) and how is it structured?

<details>
<summary>Answer</summary>

FSD organizes code into layers (app, processes, pages, features, entities, shared) and slices within features. Each slice has its own components, hooks, and types. Rules: lower layers can't import from upper layers; shared has no feature imports. Scales well for large apps.

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: How do you avoid the HOC "wrapper hell" problem?

<details>
<summary>Answer</summary>

Prefer **custom hooks** over HOCs when possible—they don't add layers to the tree. Use **composition** (render props, compound components). If you need HOCs, combine them with a utility like `compose` or use a single HOC that handles multiple concerns. Keep the component tree shallow.

See: [[1. Design Patterns/1.4 Decorator]] | [[1. React/9. React Patterns/9.2 Render Props, HOCs, Hooks]]

</details>

### Q: What are common React anti-patterns with useEffect?

<details>
<summary>Answer</summary>

Missing dependencies (causes stale closures), no cleanup (memory leaks with subscriptions/timers), using useEffect for derived state (use computation instead), and fetching in useEffect without cleanup (race conditions). Use the exhaustive-deps rule and always clean up side effects.

See: [[3. Anti-Patterns/3.1 React Anti-Patterns]]

</details>

### Q: What are state management anti-patterns?

<details>
<summary>Answer</summary>

Storing derived state (compute it instead), duplicating state across stores, putting server state in global state (use TanStack Query), storing everything in one giant context (causes unnecessary re-renders), and overusing Redux for local UI state.

See: [[3. Anti-Patterns/3.2 State Management Anti-Patterns]]

</details>

### Q: What are TypeScript anti-patterns in React?

<details>
<summary>Answer</summary>

Using `any` everywhere, `as` for unsafe type assertions instead of proper narrowing, `@ts-ignore` without fixing the root cause, overly broad types (e.g. `object`), and not typing event handlers or API responses. Prefer `unknown` and type guards over `any`.

See: [[3. Anti-Patterns/3.3 TypeScript Anti-Patterns]]

</details>

### Q: When would you use a Facade for an API layer?

<details>
<summary>Answer</summary>

When you have multiple endpoints, auth headers, error handling, retries, and caching. A facade wraps all of this into a simple API: `api.users.get(id)`, `api.users.post(data)`. The rest of the app doesn't need to know about fetch, headers, or base URLs.

See: [[1. Design Patterns/1.6 Facade]]

</details>

### Q: How does the Observer pattern relate to Redux or Zustand?

<details>
<summary>Answer</summary>

Redux/Zustand stores are subjects; components that subscribe (via `useSelector` or `useStore`) are observers. When the store updates, subscribers are notified and re-render. The pattern enables decoupled, reactive updates across the app.

See: [[1. Design Patterns/1.3 Observer]] | [[2. Architectural Patterns/2.2 State Management Patterns]]

</details>

### Q: How do you decide between Context, Zustand, and Redux for state?

<details>
<summary>Answer</summary>

**Context:** Simple, infrequent updates (theme, auth), small trees. **Zustand:** Medium complexity, no boilerplate, good DX. **Redux:** Complex state, time-travel, middleware, large teams. Consider server state separately (TanStack Query).

See: [[2. Architectural Patterns/2.2 State Management Patterns]]

</details>

---

## Hard

### Q: How would you refactor a large component that mixes UI and business logic?

<details>
<summary>Answer</summary>

Extract business logic into a custom hook (ViewModel pattern). Move API calls to a service layer. Use composition: presentational component receives data and callbacks as props. Consider splitting into smaller components (compound components) or a feature module.

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: How do you prevent a Context from causing unnecessary re-renders?

<details>
<summary>Answer</summary>

Split context: one for frequently changing data, one for stable data. Memoize the context value with `useMemo`. Use a selector pattern (subscribe to a slice of state). Consider Zustand/Jotai for granular subscriptions. Or split into multiple smaller contexts.

See: [[3. Anti-Patterns/3.1 React Anti-Patterns]] | [[2. Architectural Patterns/2.2 State Management Patterns]]

</details>

### Q: When would you use the Decorator pattern with a service vs an HOC?

<details>
<summary>Answer</summary>

**Service decorator:** Wrap a service (e.g. API client) with logging, retries, or caching. **HOC:** Wrap a component to add props (auth, theme) or behavior (loading). Use HOCs for UI concerns; use service decorators for cross-cutting infrastructure.

See: [[1. Design Patterns/1.4 Decorator]]

</details>

### Q: How do you structure a React app that will scale to 50+ features?

<details>
<summary>Answer</summary>

Use FSD or similar: strict layers (app, pages, features, entities, shared), clear boundaries. Colocate feature code. Use code splitting per route/feature. Establish conventions: no cross-feature imports, shared types in shared, API layer as facade. Document the architecture.

See: [[2. Architectural Patterns/2.1 MVC, MVVM, Architectural Patterns]]

</details>

### Q: What's the difference between an anti-pattern and a code smell?

<details>
<summary>Answer</summary>

**Code smell** suggests a potential problem (e.g. long function, too many parameters). **Anti-pattern** is a known bad solution that causes repeated issues. Smells are heuristics; anti-patterns are documented patterns to avoid. Fix smells before they become anti-patterns.

See: [[3. Anti-Patterns/3. Anti-Patterns]]

</details>

### Q: How would you implement a type-safe event bus with the Observer pattern?

<details>
<summary>Answer</summary>

Define an event map: `type Events = { userLogin: User; userLogout: void }`. The Subject is generic: `subscribe<K extends keyof Events>(event: K, handler: (payload: Events[K]) => void)`. Emit with `emit<K extends keyof Events>(event: K, payload: Events[K])`. TypeScript ensures correct payload types.

See: [[1. Design Patterns/1.3 Observer]]

</details>

### Q: What are the trade-offs of using a single global store vs multiple domain stores?

<details>
<summary>Answer</summary>

**Single store:** Single source of truth, easier to debug, but can become huge and cause re-renders. **Multiple stores:** Better isolation, smaller subscriptions, but cross-domain state is harder. Use multiple stores (Zustand slices, Redux modules) with clear boundaries; avoid shared mutable state.

See: [[2. Architectural Patterns/2.2 State Management Patterns]] | [[3. Anti-Patterns/3.2 State Management Anti-Patterns]]

</details>

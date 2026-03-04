# TypeScript Interview Questions

Self-test questions organized by difficulty. Expand each answer to check your understanding.

---

## Easy

### Q: What is the difference between `type` and `interface`?

<details>
<summary>Answer</summary>

**Interfaces** are extensible via declaration merging and use `extends`. Best for object shapes. **Types** can represent unions, intersections, primitives, and tuples. Use `interface` for object contracts; use `type` for unions, intersections, and aliases.

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: When would you use `interface` vs `type` for an object shape?

<details>
<summary>Answer</summary>

For object shapes, either works. Prefer `interface` when you expect declaration merging (e.g. extending library types) or when defining class contracts. Use `type` when you need unions, intersections, or computed properties.

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: What are TypeScript utility types and name three common ones?

<details>
<summary>Answer</summary>

Utility types transform existing types. Common ones: `Partial<T>` (all props optional), `Required<T>` (all props required), `Pick<T, K>` (subset of keys), `Omit<T, K>` (exclude keys), `Record<K, V>` (object with specific keys and value type).

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: How do you type a React component's props?

<details>
<summary>Answer</summary>

Define an interface or type for props and use it as the parameter type: `function Button({ label, onClick }: ButtonProps)`. Avoid `React.FC`—it implicitly includes `children`. Use `PropsWithChildren<Props>` or add `children?: React.ReactNode` explicitly when needed.

See: [[2.2 Typing React Components]]

</details>

### Q: How do you type `children` in a React component?

<details>
<summary>Answer</summary>

Add `children?: React.ReactNode` to your props interface, or use `PropsWithChildren<YourProps>`. `React.ReactNode` accepts elements, strings, numbers, fragments, and null. For stricter typing, use `React.ReactElement`.

See: [[2.2 Typing React Components]]

</details>

### Q: What is type narrowing and how does it work?

<details>
<summary>Answer</summary>

Type narrowing reduces a union to a more specific type. TypeScript narrows via: `typeof`, `instanceof`, truthiness checks, discriminated unions (common property), and control flow (return, throw). After a check, the type is narrowed in that branch.

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: What is a discriminated union and why is it useful?

<details>
<summary>Answer</summary>

A discriminated union has a common literal property (the discriminant) that identifies each variant. TypeScript narrows the type based on that property, giving you exhaustiveness checking and safe property access. Common for API responses and state machines.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you type a generic function?

<details>
<summary>Answer</summary>

Declare type parameters before the parameters: `function identity<T>(x: T): T { return x; }`. Call with explicit type `identity<number>(5)` or let inference work `identity(5)`. Use constraints when needed: `function first<T extends { length: number }>(arr: T)`.

See: [[2.1 TypeScript Fundamentals]]

</details>

---

## Medium

### Q: How do you type a custom hook that returns state and a setter?

<details>
<summary>Answer</summary>

Use a tuple: `function useToggle(initial: boolean): [boolean, () => void]`. Or infer from `useState`: `const [value, setValue] = useState<T>(initial)`—TypeScript infers the types. For complex returns, define an interface and return an object.

See: [[2.3 Typing Hooks]]

</details>

### Q: How do you type `forwardRef` and `useImperativeHandle`?

<details>
<summary>Answer</summary>

`forwardRef<RefType, PropsType>(...)`—RefType is what the parent gets. Use `useImperativeHandle(ref, () => ({ focus: () => {} }))` to expose methods. The ref type should match the object returned by the imperative handle.

See: [[2.2 Typing React Components]]

</details>

### Q: How do you type event handlers (onClick, onChange, etc.)?

<details>
<summary>Answer</summary>

Use `React.MouseEvent<HTMLButtonElement>`, `React.ChangeEvent<HTMLInputElement>`, etc. The generic is the element type. For `onSubmit`: `React.FormEvent<HTMLFormElement>`. Use `React.EventHandler` types when available.

See: [[2.2 Typing React Components]]

</details>

### Q: What is `satisfies` and when would you use it?

<details>
<summary>Answer</summary>

`satisfies` checks that a value matches a type without widening to that type. `const config = { ... } satisfies Config` keeps the literal types (e.g. `"admin"` instead of `string`) while ensuring it conforms to `Config`. Useful for config objects and preserving inference.

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: How do you create a type-safe API client?

<details>
<summary>Answer</summary>

Define response types for each endpoint. Use generics for fetch wrappers: `async function get<T>(url: string): Promise<T>`. Map routes to response types (e.g. with a const object or overloads). Validate at runtime with Zod or similar if the API is untrusted.

See: [[2.5 Type-Safe API Layer]]

</details>

### Q: What are conditional types and give an example?

<details>
<summary>Answer</summary>

Conditional types use `T extends U ? X : Y` to choose a type based on a condition. Example: `type Flatten<T> = T extends (infer E)[] ? E : T` extracts the element type of an array. Use `infer` to capture a type within the condition.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you type a function that accepts different prop shapes (polymorphic component)?

<details>
<summary>Answer</summary>

Use generics with constraints. Example: `function Text<C extends 'span' | 'p'>({ as, ...props }: { as: C } & (C extends 'span' ? React.HTMLAttributes<HTMLSpanElement> : React.HTMLAttributes<HTMLParagraphElement>))`. Or use a discriminated union of props per variant.

See: [[2.2 Typing React Components]]

</details>

### Q: What is `keyof` and how do you use it?

<details>
<summary>Answer</summary>

`keyof T` produces a union of all keys of `T`. Use it for: `function get<K extends keyof User>(obj: User, key: K): User[K]` to ensure type-safe property access. Combined with `in`, it powers mapped types: `[P in keyof T]: T[P]`.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you type a generic hook that fetches data?

<details>
<summary>Answer</summary>

`function useFetch<T>(url: string): { data: T | null; loading: boolean; error: Error | null }`. The caller specifies `T` (e.g. `useFetch<User>('/api/user')`). Ensure your fetch/query library returns `T` and handle the loading/error states in the type.

See: [[2.3 Typing Hooks]] | [[2.5 Type-Safe API Layer]]

</details>

### Q: What are template literal types and when are they useful?

<details>
<summary>Answer</summary>

Template literal types build string types from templates: `` type EventName = `on${Capitalize<"click" | "scroll">}` `` → `"onClick" | "onScroll"`. Useful for type-safe event handlers, API routes, or CSS class names derived from config.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you type a reducer (e.g. for useReducer)?

<details>
<summary>Answer</summary>

Define `State` and `Action` types. Action is often a discriminated union: `type Action = { type: 'increment' } | { type: 'decrement'; payload: number }`. Type the reducer: `(state: State, action: Action) => State`. `useReducer` will infer from the reducer.

See: [[2.3 Typing Hooks]]

</details>

### Q: What is the difference between `unknown` and `any`?

<details>
<summary>Answer</summary>

`any` disables type checking. `unknown` is type-safe—you must narrow (e.g. `typeof`, type guards) before using it. Prefer `unknown` for values from external sources (API, `JSON.parse`). Use type guards or assertion only after validation.

See: [[2.1 TypeScript Fundamentals]]

</details>

### Q: How do you type a context and its provider?

<details>
<summary>Answer</summary>

`const MyContext = createContext<ValueType | null>(null)`. For a required context, use `createContext<ValueType>(null!)` or provide a default. Type the hook: `function useMyContext(): ValueType { const ctx = useContext(MyContext); if (!ctx) throw new Error(...); return ctx; }`.

See: [[2.3 Typing Hooks]]

</details>

---

## Hard

### Q: How do you implement a type-safe event emitter or pub/sub?

<details>
<summary>Answer</summary>

Map event names to payload types: `type Events = { click: { x: number }; submit: FormData }`. `emit<K extends keyof Events>(event: K, payload: Events[K])` and `on<K extends keyof Events>(event: K, handler: (payload: Events[K]) => void)`. Use a generic interface for the emitter.

See: [[2.4 Advanced Types]] | [[2.5 Type-Safe API Layer]]

</details>

### Q: How do you create a type that extracts the props of a React component?

<details>
<summary>Answer</summary>

Use `React.ComponentProps<typeof MyComponent>` to get the props type. For intrinsic elements: `React.ComponentProps<'button'>`. For refs: `React.ComponentRef<typeof MyComponent>`. Useful when wrapping components or creating HOCs.

See: [[2.2 Typing React Components]]

</details>

### Q: What are branded types and when would you use them?

<details>
<summary>Answer</summary>

Branded types add a phantom property to distinguish otherwise identical types (e.g. `UserId` vs `OrderId` both as strings). `type UserId = string & { readonly brand: unique symbol }`. Prevents mixing IDs accidentally. Use for domain primitives.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you type a function with multiple overloads?

<details>
<summary>Answer</summary>

Declare overload signatures (no implementation) followed by one implementation signature that is compatible with all overloads. The implementation signature is not directly callable. Use when the function behaves differently based on argument types or count.

See: [[2.4 Advanced Types]]

</details>

### Q: How do you ensure API response types match runtime data?

<details>
<summary>Answer</summary>

Use a runtime validator (Zod, io-ts) that infers TypeScript types. Parse the response: `const user = UserSchema.parse(await response.json())`. The parsed value is typed. For external APIs, always validate—types alone don't guarantee runtime shape.

See: [[2.5 Type-Safe API Layer]]

</details>

### Q: How do you type a generic component that forwards refs and supports `as` prop?

<details>
<summary>Answer</summary>

Use `ComponentPropsWithoutRef` and `ElementType`. The `as` prop is `C extends ElementType`, and you spread `Omit<ComponentPropsWithoutRef<C>, keyof YourProps> & YourProps`. Use `forwardRef` with the correct ref type for the rendered element. Libraries like Radix use this pattern.

See: [[2.2 Typing React Components]]

</details>

# React Quick Reference

[[README.md]]

---

Quick cheat sheet for React concepts, hooks, and patterns.

## Core Concepts Cheat Sheet

### Functional Component
```typescript
function Welcome({ name }: { name: string }) {
  return <h1>Hello, {name}!</h1>;
}
```

### Props
```typescript
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
}

function Button({ label, disabled }: ButtonProps) {
  return <button disabled={disabled}>{label}</button>;
}
```

### JSX
```typescript
// Conditional rendering
<div>{condition ? <A /> : <B />}</div>

// List rendering (always use key!)
{items.map(item => <div key={item.id}>{item.name}</div>)}

// Inline styles (object)
<div style={{ color: 'red', fontSize: '16px' }}>Text</div>

// className (not class)
<div className="container">Content</div>

// htmlFor (not for)
<label htmlFor="input-id">Label</label>
```

---

## React Hooks Cheat Sheet

### useState
```typescript
const [count, setCount] = useState(0);
const [count, setCount] = useState(() => expensiveCalc());
setCount(5);
setCount(prev => prev + 1);
```

### useEffect
```typescript
// Run once on mount
useEffect(() => {
  fetchData();
}, []);

// Run when dependencies change
useEffect(() => {
  fetchData(id);
}, [id]);

// With cleanup
useEffect(() => {
  const unsubscribe = subscribe();
  return () => unsubscribe();
}, []);
```

### useContext
```typescript
const theme = useContext(ThemeContext);
```

### useReducer
```typescript
const [state, dispatch] = useReducer(reducer, initialState);
dispatch({ type: 'ACTION', payload: data });
```

### useCallback
```typescript
const handleClick = useCallback(() => {
  // Memoized function
}, [dependencies]);
```

### useMemo
```typescript
const expensiveValue = useMemo(() => {
  return calculations(data);
}, [data]);
```

### useRef
```typescript
const inputRef = useRef<HTMLInputElement>(null);
inputRef.current?.focus();
```

---

## Custom Hooks Patterns

### useAsync
```typescript
function useAsync<T>(fn: () => Promise<T>) {
  const [state, setState] = useState<{
    loading: boolean;
    data: T | null;
    error: null | Error;
  }>({ loading: true, data: null, error: null });

  useEffect(() => {
    fn()
      .then(data => setState({ loading: false, data, error: null }))
      .catch(error => setState({ loading: false, data: null, error }));
  }, [fn]);

  return state;
}

// Usage
const { loading, data, error } = useAsync(() => fetchUsers());
```

### useToggle
```typescript
function useToggle(initial = false) {
  const [state, setState] = useState(initial);
  return [state, () => setState(s => !s)] as const;
}

// Usage
const [isOpen, toggle] = useToggle();
```

### usePrevious
```typescript
function usePrevious<T>(value: T) {
  const ref = useRef<T>();
  useEffect(() => {
    ref.current = value;
  }, [value]);
  return ref.current;
}

// Usage
const prevValue = usePrevious(value);
```

### useLocalStorage
```typescript
function useLocalStorage<T>(key: string, initial: T) {
  const [state, setState] = useState<T>(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initial;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(state));
  }, [state, key]);

  return [state, setState] as const;
}

// Usage
const [user, setUser] = useLocalStorage('user', null);
```

---

## React v19 Hooks

### useActionState
```typescript
'use client'

async function submitForm(formData) {
  'use server'
  // Handle server-side
}

function Form() {
  const [state, formAction] = useActionState(submitForm, null);
  return (
    <form action={formAction}>
      <input name="email" />
      <button type="submit">Submit</button>
      {state?.error && <p>{state.error}</p>}
    </form>
  );
}
```

### useFormStatus
```typescript
'use client'

import { useFormStatus } from 'react-dom';

function SubmitButton() {
  const { pending } = useFormStatus();
  return <button disabled={pending}>{pending ? 'Saving...' : 'Save'}</button>;
}
```

### useOptimistic
```typescript
'use client'

const [optimisticItems, addOptimistic] = useOptimistic(
  items,
  (state, newItem) => [...state, newItem]
);

const handleAdd = async (data) => {
  addOptimistic(newData);
  await save(data);
};
```

### use()
```typescript
'use client'

// Unwrap promise
const data = use(fetchData());

// Unwrap context
const theme = use(ThemeContext);
```

### useTransition
```typescript
const [isPending, startTransition] = useTransition();

const handleSearch = (query) => {
  startTransition(async () => {
    const results = await search(query);
    setResults(results);
  });
};
```

### useDeferredValue
```typescript
const [query, setQuery] = useState('');
const deferredQuery = useDeferredValue(query);

// Expensive operation happens with deferredQuery
```

---

## Common Patterns

### Form Handling (v19)
```typescript
async function saveUser(formData) {
  'use server'
  const email = formData.get('email');
  await db.users.create({ email });
  return { success: true };
}

function Form() {
  const [state, formAction] = useActionState(saveUser, null);
  return (
    <form action={formAction}>
      <input name="email" type="email" required />
      <button type="submit">Save</button>
      {state?.success && <p>Saved!</p>}
    </form>
  );
}
```

### Form Handling (v18)
```typescript
function Form() {
  const [email, setEmail] = useState('');
  const [error, setError] = useState(null);
  const [isPending, setIsPending] = useState(false);

  const handleSubmit = async (e) => {
    e.preventDefault();
    setIsPending(true);
    try {
      await saveUser(email);
    } catch (err) {
      setError(err.message);
    } finally {
      setIsPending(false);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input value={email} onChange={(e) => setEmail(e.target.value)} />
      <button disabled={isPending}>{isPending ? 'Saving...' : 'Save'}</button>
      {error && <p>{error}</p>}
    </form>
  );
}
```

### API Call
```typescript
function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    (async () => {
      try {
        const data = await fetch('/api/users').then(r => r.json());
        setUsers(data);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    })();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  return <ul>{users.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

### Context API
```typescript
const ThemeContext = createContext<'light' | 'dark'>('light');

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState<'light' | 'dark'>('light');
  return (
    <ThemeContext.Provider value={theme}>
      {children}
    </ThemeContext.Provider>
  );
}

function useTheme() {
  return useContext(ThemeContext);
}

// Usage
function App() {
  const theme = useTheme();
  return <div className={theme}>Content</div>;
}
```

### Compound Components
```typescript
function Tabs() {
  const [active, setActive] = useState(0);

  return (
    <TabsContext.Provider value={{ active, setActive }}>
      <div className="tabs">
        <Tabs.List>
          <Tabs.Item index={0}>Tab 1</Tabs.Item>
          <Tabs.Item index={1}>Tab 2</Tabs.Item>
        </Tabs.List>
        <Tabs.Content index={0}>Content 1</Tabs.Content>
        <Tabs.Content index={1}>Content 2</Tabs.Content>
      </div>
    </TabsContext.Provider>
  );
}

Tabs.List = ({ children }) => <div className="tabs-list">{children}</div>;
Tabs.Item = ({ index, children }) => {
  const { active, setActive } = useContext(TabsContext);
  return (
    <button onClick={() => setActive(index)} className={active === index ? 'active' : ''}>
      {children}
    </button>
  );
};
Tabs.Content = ({ index, children }) => {
  const { active } = useContext(TabsContext);
  return active === index ? <div>{children}</div> : null;
};
```

---

## One-Liners

| Concept | TL;DR |
| :-- | :-- |
| **useState** | Manage component state |
| **useEffect** | Side effects after render |
| **useContext** | Access shared values |
| **useReducer** | Complex state logic |
| **useCallback** | Memoize callbacks |
| **useMemo** | Memoize values |
| **useRef** | Access DOM / store value |
| **useActionState** | Form submission (v19) |
| **useFormStatus** | Show form pending |
| **useOptimistic** | Optimistic UI updates |
| **use()** | Unwrap promises (v19) |
| **useTransition** | Non-blocking updates |
| **useDeferredValue** | Defer expensive updates |
| **Custom Hooks** | Reuse logic |

---

## Rules of Hooks

❌ **NEVER:**
- Don't call hooks inside loops
- Don't call hooks inside conditions
- Don't call hooks in regular functions
- Don't call hooks in event handlers

✅ **ALWAYS:**
- Call hooks at top level only
- Call hooks from React components or custom hooks
- Include dependencies in dependency arrays
- Return cleanup functions from useEffect

---

## Type Safety (TypeScript)

```typescript
// Props type
interface CardProps {
  title: string;
  onClick: (id: string) => void;
  children: React.ReactNode;
}

// State type
const [user, setUser] = useState<User | null>(null);

// Ref type
const ref = useRef<HTMLInputElement>(null);

// Event type
const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
  // ...
};

// Form event
const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
  e.preventDefault();
};
```

---

## Performance Tips

```typescript
// Memoize expensive renders
const MemoComponent = memo(Component);

// Memoize callbacks
const handleClick = useCallback(() => {
  // ...
}, [dependencies]);

// Memoize values
const value = useMemo(() => expensive(data), [data]);

// Defer updates
const deferredValue = useDeferredValue(value);

// Show pending state
const [isPending, startTransition] = useTransition();
startTransition(() => setState(new));
```

---

## See Also

- [[1. React Core Concepts/1. React Core Concepts.md]] - Detailed core concepts
- [[2. React Hooks/2. React Hooks.md]] - Detailed hooks guide
- [[2. React Hooks/2.11 React v19 Hooks/2.11 React v19 Hooks.md]] - React v19 features
- [[README.md]] - Full React guide

---

**Last Updated:** February 24, 2026
**React Version:** 18+ with v19 features

---

[[README.md]]

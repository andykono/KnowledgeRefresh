# Quick Reference - All Patterns at a Glance

Шпаргалка по всем паттернам на одной странице.

> **Note:** React Patterns have moved to [[9. React Patterns.md]], Testing to [[5. Testing.md]], and Real-World Examples to [[8. Real-World Examples.md]] -- all inside the React section.

---

## Design Patterns

### Creational (Порождающие)

#### Singleton
```typescript
// Problem: Need single global instance
class ApiClient {
  private static instance: ApiClient;
  private constructor() {}
  static getInstance() { return ApiClient.instance ??= new ApiClient(); }
}
const api = ApiClient.getInstance();
```

#### Factory Method
```typescript
// Problem: Create different types without repeating logic
class ComponentFactory {
  static create(type: 'button' | 'input') {
    return type === 'button' ? <Button /> : <Input />;
  }
}
```

---

### Behavioral (Поведенческие)

#### Observer
```typescript
// Problem: Notify many listeners on change
class Subject<T> {
  listeners = new Set();
  subscribe(fn) { this.listeners.add(fn); return () => this.listeners.delete(fn); }
  notify(data: T) { this.listeners.forEach(f => f(data)); }
}
```

#### Strategy
```typescript
// Problem: Swap algorithms at runtime
interface SortStrategy { sort(arr: number[]): number[]; }
class DataList {
  strategy: SortStrategy;
  setStrategy(s: SortStrategy) { this.strategy = s; }
  sort(data: number[]) { return this.strategy.sort(data); }
}
```

---

### Structural (Структурные)

#### Decorator
```typescript
// Problem: Add behavior without modifying class
function withLogging<T extends (...args: any[]) => any>(fn: T): T {
  return ((...args) => {
    console.log('Called:', args);
    return fn(...args);
  }) as T;
}
```

#### Facade
```typescript
// Problem: Simplify complex subsystem
class AuthFacade {
  login(email, pass) { /* orchestrates api + storage + logging */ }
  logout() { /* cleanup */ }
  isAuthenticated() { return !!this.getToken(); }
}
```

---

## Architectural Patterns

### Component-Based
```
App
├── Header
│   ├── Logo
│   ├── Navigation
│   └── UserMenu
├── MainContent
│   ├── Sidebar
│   └── PageContent
└── Footer
```
**Best for:** Small projects, learning

---

### MVVM (Model-View-ViewModel)
```typescript
// ViewModel
function useUserViewModel() {
  const [user, setUser] = useState(null);
  // Logic here
  return { user, updateUser, deleteUser };
}

// View
function UserProfile() {
  const vm = useUserViewModel();
  return <div>{vm.user.name}</div>;
}
```
**Best for:** Medium projects with complex state

---

### Clean Architecture
```
entities/      → User, Order (interfaces)
usecases/      → CreateUser, UpdateUser (business logic)
repositories/  → IUserRepository (abstraction)
presenters/    → UserPresenter (formatting)
controllers/   → UserController (entry point)
```
**Best for:** Enterprise, testability

---

### Feature-Sliced Design (FSD)
```
features/
├── Auth/
│   ├── model/      (types, interfaces)
│   ├── ui/         (components)
│   ├── api.ts      (requests)
│   └── hooks/
├── Users/
└── Orders/

entities/
├── User/
├── Order/
└── Product/

shared/        (common utilities)
app/           (routing, setup)
```
**Best for:** Scalable projects, team work

---

## React Patterns

### Compound Components
```typescript
function Tabs() {
  const [active, setActive] = useState(0);

  return (
    <Tabs.Container>
      <Tabs.List>
        <Tabs.Item index={0}>Tab 1</Tabs.Item>
        <Tabs.Item index={1}>Tab 2</Tabs.Item>
      </Tabs.List>
      <Tabs.Content index={0}>Content 1</Tabs.Content>
      <Tabs.Content index={1}>Content 2</Tabs.Content>
    </Tabs.Container>
  );
}
```

### Custom Hooks
```typescript
function useAsync<T>(fn: () => Promise<T>) {
  const [state, setState] = useState({ loading: true, data: null, error: null });
  useEffect(() => { fn().then(data => setState({loading: false, data, error: null})); }, [fn]);
  return state;
}

function MyComponent() {
  const { data, loading, error } = useAsync(() => api.getUsers());
}
```

### Context API
```typescript
const UserContext = createContext<User | null>(null);

function UserProvider({ children }) {
  const [user, setUser] = useState(null);
  return <UserContext.Provider value={user}>{children}</UserContext.Provider>;
}

function useUser() {
  return useContext(UserContext);
}
```

---

## State Management

### Redux Pattern
```typescript
// Action
const INCREMENT = 'INCREMENT';
const increment = (payload) => ({ type: INCREMENT, payload });

// Reducer
const counterReducer = (state = 0, action) => {
  return action.type === INCREMENT ? state + 1 : state;
};

// Store
const store = createStore(counterReducer);
store.subscribe(() => console.log(store.getState()));
store.dispatch(increment());
```

### Zustand (Recommended)
```typescript
const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

function Counter() {
  const { count, increment } = useStore();
  return <button onClick={increment}>{count}</button>;
}
```

### XState (State Machines)
```typescript
const toggleMachine = createMachine({
  initial: 'off',
  states: {
    off: { on: { TOGGLE: 'on' } },
    on: { on: { TOGGLE: 'off' } },
  },
});

const [state, send] = useMachine(toggleMachine);
return <button onClick={() => send('TOGGLE')}>{state.value}</button>;
```

---

## Anti-Patterns (What NOT to do)

### ❌ Prop Drilling
```typescript
// BAD
<Component user={user} onUserChange={setUser} />
  <ChildComponent user={user} onUserChange={setUser} />
    <GrandchildComponent user={user} onUserChange={setUser} />

// GOOD - Use Context
const UserContext = createContext();
```

### ❌ God Component
```typescript
// BAD - One component doing everything
function Dashboard() {
  // 500 lines of code
}

// GOOD - Split into smaller components
<Dashboard>
  <UserPanel />
  <Analytics />
  <Settings />
</Dashboard>
```

### ❌ Missing Dependencies
```typescript
// BAD
useEffect(() => {
  fetchUsers(userId); // userId not in dependency array!
}, []);

// GOOD
useEffect(() => {
  fetchUsers(userId);
}, [userId]);
```

### ❌ Mutable State
```typescript
// BAD
const user = state.user;
user.name = 'New Name'; // Mutating state!

// GOOD
const updatedUser = { ...state.user, name: 'New Name' };
setState({ user: updatedUser });
```

### ❌ useCallback Hell
```typescript
// BAD
const handleClick = useCallback(() => {
  const handleChange = useCallback(() => {
    const handleSubmit = useCallback(() => {
      // callback hell!
    }, [deps]);
  }, [deps]);
}, [deps]);

// GOOD - Use simple functions
const handleSubmit = () => { /* ... */ };
```

---

## Testing Patterns

### Unit Test
```typescript
describe('Singleton', () => {
  it('returns same instance', () => {
    const a = ApiClient.getInstance();
    const b = ApiClient.getInstance();
    expect(a).toBe(b);
  });
});
```

### Component Test
```typescript
describe('Button', () => {
  it('calls onClick when clicked', () => {
    const onClick = jest.fn();
    render(<Button onClick={onClick}>Click</Button>);
    fireEvent.click(screen.getByText('Click'));
    expect(onClick).toHaveBeenCalled();
  });
});
```

### Hook Test
```typescript
describe('useAsync', () => {
  it('loads data', async () => {
    const { result } = renderHook(() => useAsync(fetchUsers));
    await waitFor(() => {
      expect(result.current.data).toBeDefined();
    });
  });
});
```

---

## Decision Tree

```
Do you need to...

├─ Create objects?
│  └─ Different types? → Factory Method
│  └─ Single instance? → Singleton
│
├─ Add functionality?
│  └─ Wrap object? → Decorator
│  └─ Simplify complex API? → Facade
│
├─ Handle state changes?
│  └─ Notify many listeners? → Observer
│  └─ Swap algorithms? → Strategy
│
├─ Organize code?
│  └─ Small project? → Component-Based
│  └─ Medium project? → MVVM + Hooks
│  └─ Large project? → FSD
│  └─ Enterprise? → Clean Architecture
│
├─ Manage complex state?
│  └─ Global state? → Redux / Zustand
│  └─ State machine? → XState
│  └─ Local state? → useState
│
└─ Create flexible components?
   └─ Configurable? → Compound Components
   └─ Reuse logic? → Custom Hooks
   └─ Share across app? → Context API
```

---

## Checklists

### Before Adding a Pattern
- [ ] Do I really need this pattern?
- [ ] Is the problem actually solved by this?
- [ ] Is it the simplest solution?
- [ ] Can my team maintain it?
- [ ] Will it be easy to test?

### Code Review
- [ ] No prop drilling (use Context)
- [ ] No memory leaks (unsubscribe cleanup)
- [ ] No missing dependencies
- [ ] No mutable state
- [ ] No callback hell
- [ ] Types are correct

### Testing
- [ ] Unit tests written
- [ ] Component tests written
- [ ] Happy path covered
- [ ] Error cases covered
- [ ] Edge cases covered

---

## One-Liners

| Pattern | TL;DR |
| :-- | :-- |
| Singleton | One instance everywhere |
| Factory | Create objects without knowing the type |
| Observer | Tell me when something changes |
| Strategy | Swap algorithms at runtime |
| Decorator | Add features to existing objects |
| Facade | Hide complexity behind simple API |
| MVVM | Separate View from ViewModel |
| Clean Architecture | Layers with clear dependency direction |
| Onion Architecture | Domain-driven with dependency inversion |
| FSD | Organize code by features, not types |
| Compound | Components that work together |
| Custom Hooks | Share logic between components |
| Redux | Predictable state management |
| Zustand | Simple state management |
| XState | Explicit state machines |

---

**For detailed explanations, see the full guides in their respective folders!**

Last updated: February 24, 2026

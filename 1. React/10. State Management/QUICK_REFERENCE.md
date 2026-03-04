# State Management Quick Reference

---

## Decision Tree

```
What kind of state?
│
├─ UI state (toggle, modal, form field)
│  └─ useState
│
├─ Complex local state (multiple related values)
│  └─ useReducer
│
├─ Shared state (2-3 components)
│  └─ Lift state up + props
│
├─ App-wide state (theme, auth, language)
│  ├─ Small app → useContext
│  ├─ Medium app → Zustand
│  └─ Large app → Redux Toolkit
│
├─ Server state (API data)
│  └─ TanStack Query
│
├─ Fine-grained reactivity
│  └─ Jotai
│
└─ Complex workflows (multi-step, explicit transitions)
   └─ XState
```

---

## Comparison

| Feature | useState | useReducer | Context | Zustand | Redux | Jotai | XState |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| **Scope** | Local | Local | Global | Global | Global | Global | Any |
| **Boilerplate** | None | Low | Low | Low | Medium | Low | Medium |
| **DevTools** | React | React | React | Minimal | Full | Minimal | Inspector |
| **Middleware** | No | No | No | Yes | Yes | No | Built-in |
| **Async** | Manual | Manual | Manual | Built-in | Thunk/Saga | Atoms | Services |
| **Bundle** | 0 KB | 0 KB | 0 KB | ~1 KB | ~10 KB | ~3 KB | ~15 KB |
| **Best for** | Simple | Complex local | Small app | Most apps | Enterprise | Atomic | Workflows |

---

## Minimal Examples

### useState
```typescript
const [count, setCount] = useState(0);
```

### useReducer
```typescript
const [state, dispatch] = useReducer(reducer, { count: 0 });
dispatch({ type: 'INCREMENT' });
```

### Context
```typescript
const ThemeContext = createContext<Theme>('light');
const theme = useContext(ThemeContext);
```

### Zustand
```typescript
const useStore = create<Store>((set) => ({
  count: 0,
  increment: () => set((s) => ({ count: s.count + 1 })),
}));
const { count, increment } = useStore();
```

### Redux Toolkit
```typescript
const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: (state) => { state.value += 1; },
  },
});
const count = useSelector((s: RootState) => s.counter.value);
const dispatch = useDispatch();
```

### Jotai
```typescript
const countAtom = atom(0);
const [count, setCount] = useAtom(countAtom);
```

### XState
```typescript
const machine = createMachine({
  initial: 'idle',
  states: {
    idle: { on: { START: 'running' } },
    running: { on: { STOP: 'idle' } },
  },
});
const [state, send] = useMachine(machine);
```

### TanStack Query
```typescript
const { data, isLoading } = useQuery({
  queryKey: ['users'],
  queryFn: () => api.getUsers(),
});
```

---

## Server State vs Client State

| | Server State | Client State |
| :-- | :-- | :-- |
| **Source** | API / database | Browser only |
| **Staleness** | Can become stale | Always current |
| **Caching** | Required | Optional |
| **Tool** | TanStack Query | Zustand / Redux / Context |
| **Examples** | User list, products, orders | Theme, sidebar open, form |

---

## Recommended Stacks

| Project Size | Stack |
| :-- | :-- |
| **MVP / Small** | `useState` + `useContext` |
| **Medium** | Zustand + TanStack Query |
| **Large** | Redux Toolkit + TanStack Query |
| **Complex UI flows** | + XState |

---

See: [[4. State Management.md]] for full guide

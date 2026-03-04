# TypeScript Quick Reference

## Key Types at a Glance

### Primitives
```typescript
let str: string = "hello";
let num: number = 42;
let bool: boolean = true;
let undef: undefined = undefined;
let nul: null = null;
let sym: symbol = Symbol("id");
let big: bigint = 9007199254740991n;
```

### Unions & Intersections
```typescript
type Status = "idle" | "loading" | "success" | "error";
type ID = string | number;

type A = { a: number };
type B = { b: string };
type AB = A & B;  // { a: number; b: string }
```

### Generics
```typescript
function identity<T>(x: T): T { return x; }
const arr: Array<string> = ["a", "b"];
const map: Map<string, number> = new Map();
```

---

## Utility Types Cheat Sheet

| Utility | Purpose | Example |
|---------|---------|---------|
| `Partial<T>` | All props optional | `Partial<User>` |
| `Required<T>` | All props required | `Required<Partial<User>>` |
| `Readonly<T>` | All props readonly | `Readonly<User>` |
| `Pick<T, K>` | Pick specific keys | `Pick<User, "id" \| "name">` |
| `Omit<T, K>` | Exclude keys | `Omit<User, "password">` |
| `Record<K, V>` | Map keys to value type | `Record<string, number>` |
| `Exclude<T, U>` | Remove U from union T | `Exclude<"a" \| "b", "a">` → `"b"` |
| `Extract<T, U>` | Keep only U in T | `Extract<"a" \| "b", "a">` → `"a"` |
| `NonNullable<T>` | Remove null/undefined | `NonNullable<string \| null>` |
| `ReturnType<T>` | Get function return type | `ReturnType<typeof fetch>` |
| `Parameters<T>` | Get function params tuple | `Parameters<typeof fn>` |

```typescript
interface User { id: number; name: string; email?: string; }
type UserPreview = Pick<User, "id" | "name">;
type UserInput = Partial<Omit<User, "id">>;
type UserMap = Record<string, User>;
```

---

## React Component Typing Patterns

### Props
```typescript
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
  children?: React.ReactNode;
}

const Button: React.FC<ButtonProps> = ({ label, onClick, disabled }) => (
  <button onClick={onClick} disabled={disabled}>{label}</button>
);
```

### Events
```typescript
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {};
const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {};
const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {};
const handleKeyDown = (e: React.KeyboardEvent<HTMLInputElement>) => {};
```

### Refs
```typescript
const inputRef = useRef<HTMLInputElement>(null);
const divRef = useRef<HTMLDivElement>(null);
// For custom components with forwardRef:
const FancyInput = forwardRef<HTMLInputElement, InputProps>((props, ref) => (
  <input ref={ref} {...props} />
));
```

---

## Hook Typing Patterns

### useState
```typescript
const [count, setCount] = useState<number>(0);
const [user, setUser] = useState<User | null>(null);
const [items, setItems] = useState<string[]>([]);
```

### useReducer
```typescript
type State = { count: number };
type Action = { type: "increment" } | { type: "decrement"; payload: number };
const reducer = (state: State, action: Action): State => { /* ... */ };
const [state, dispatch] = useReducer(reducer, { count: 0 });
```

### useContext
```typescript
interface AuthContextType { user: User | null; login: () => void; logout: () => void; }
const AuthContext = createContext<AuthContextType | undefined>(undefined);
const auth = useContext(AuthContext);
if (!auth) throw new Error("useAuth must be within AuthProvider");
```

---

## Common Gotchas

1. **Strict null checks**: `string | undefined` ≠ `string`. Use optional chaining (`?.`) and nullish coalescing (`??`).
2. **`any` vs `unknown`**: Prefer `unknown` when type is truly unknown; narrow with type guards before use.
3. **Index signatures**: `[key: string]: any` allows any string key—use `Record<string, T>` for typed maps.
4. **Function overloads**: Order matters—most specific first, generic last.
5. **`as const`**: Use for literal inference—`["a", "b"] as const` gives `readonly ["a", "b"]`.
6. **Generic constraints**: `extends` in generics constrains, doesn't extend—`T extends User` means T must be User or subtype.

# Performance Quick Reference

## Re-render Checklist: Why Did My Component Re-render?

1. **State changed** — `useState` / `useReducer` in this component
2. **Props changed** — Parent passed new props (new reference or new value)
3. **Context changed** — A consumed context value changed
4. **Parent re-rendered** — Children re-render when parent does (unless memoized)
5. **Force update** — `forceUpdate()` or key change causing remount

**Debug**: Add `console.log` or use React DevTools Profiler to trace.

---

## memo / useMemo / useCallback Decision Guide

| Tool | Use When | Avoid When |
|------|----------|------------|
| `memo` | Expensive render, same props often | Simple components, props always change |
| `useMemo` | Expensive computation, stable deps | Cheap calculations, primitive deps |
| `useCallback` | Passing fn to memoized child | No memoized child, inline is fine |

```typescript
// memo: prevent re-render when props are referentially equal
const ExpensiveList = memo(({ items }: { items: Item[] }) => (
  <ul>{items.map(i => <li key={i.id}>{i.name}</li>)}</ul>
));

// useMemo: cache expensive computation
const sorted = useMemo(() => items.sort((a, b) => a.name.localeCompare(b.name)), [items]);

// useCallback: stable function reference for memoized children
const handleClick = useCallback(() => doSomething(id), [id]);
```

**Rule**: Don't optimize prematurely. Measure first; add memoization only where Profiler shows cost.

---

## Code Splitting Snippet

```typescript
import { lazy, Suspense } from "react";

const HeavyChart = lazy(() => import("./HeavyChart"));
const AdminPanel = lazy(() => import("./AdminPanel"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <HeavyChart />
      <AdminPanel />
    </Suspense>
  );
}
```

**Route-based splitting** (common with React Router):
```typescript
const Dashboard = lazy(() => import("./pages/Dashboard"));
<Route path="/dashboard" element={<Suspense fallback={<Spinner />}><Dashboard /></Suspense>} />
```

---

## Web Vitals Targets Table

| Metric | Good | Needs Improvement | Poor |
|--------|------|-------------------|------|
| LCP (Largest Contentful Paint) | ≤2.5s | 2.5–4s | >4s |
| FID (First Input Delay) | ≤100ms | 100–300ms | >300ms |
| CLS (Cumulative Layout Shift) | ≤0.1 | 0.1–0.25 | >0.25 |
| INP (Interaction to Next Paint) | ≤200ms | 200–500ms | >500ms |

---

## React DevTools Profiler Quick Guide

1. **Record** — Click record, perform actions, stop.
2. **Flame graph** — Component tree; bar width = render time.
3. **Ranked** — Components sorted by render duration.
4. **Why did this render?** — Check "Profiler" tab for commit details.
5. **Highlight updates** — Settings → "Highlight updates when components render" to see re-renders.

**Look for**: Components with long bars, frequent re-renders, or unnecessary child re-renders.

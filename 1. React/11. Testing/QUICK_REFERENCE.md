# Testing Quick Reference

---

## Testing Pyramid

```
        /\
       /  \     E2E (Playwright/Cypress)     5-10%
      /    \
     /------\
    /        \   Integration                  20-30%
   /          \
  /            \
 /              \ Unit Tests                  60-80%
/________________\
```

---

## RTL Query Cheat Sheet

| Query | Waits? | Fails if missing? | Use when |
| :-- | :-- | :-- | :-- |
| `getBy` | No | Yes | Element should be present |
| `queryBy` | No | No (returns null) | Element might NOT be present |
| `findBy` | Yes (async) | Yes | Element appears after async |
| `getAllBy` | No | Yes | Multiple elements |
| `queryAllBy` | No | No (returns []) | Multiple, might be absent |
| `findAllBy` | Yes | Yes | Multiple, appear async |

### Priority order (most accessible first)
1. `getByRole` -- buttons, links, headings
2. `getByLabelText` -- form fields
3. `getByPlaceholderText` -- inputs
4. `getByText` -- non-interactive text
5. `getByDisplayValue` -- filled inputs
6. `getByAltText` -- images
7. `getByTitle` -- title attributes
8. `getByTestId` -- last resort

---

## userEvent Cheat Sheet

```typescript
import userEvent from '@testing-library/user-event';
const user = userEvent.setup();

await user.click(element);
await user.dblClick(element);
await user.type(input, 'text');
await user.clear(input);
await user.selectOptions(select, 'value');
await user.hover(element);
await user.unhover(element);
await user.tab();
await user.keyboard('{Enter}');
await user.upload(fileInput, file);
await user.paste('text');
```

---

## Common jest.mock Patterns

```typescript
// Mock a module
jest.mock('./api');
import { getUser } from './api';
(getUser as jest.Mock).mockResolvedValue({ id: 1, name: 'John' });

// Mock a hook
jest.mock('react-router-dom', () => ({
  ...jest.requireActual('react-router-dom'),
  useNavigate: () => jest.fn(),
  useParams: () => ({ id: '123' }),
}));

// Spy on a method
const spy = jest.spyOn(console, 'error').mockImplementation();
// ...
spy.mockRestore();

// Mock timers
jest.useFakeTimers();
jest.advanceTimersByTime(1000);
jest.useRealTimers();
```

---

## MSW Setup (API Mocking)

```typescript
import { setupServer } from 'msw/node';
import { http, HttpResponse } from 'msw';

const handlers = [
  http.get('/api/users', () => {
    return HttpResponse.json([
      { id: 1, name: 'John' },
    ]);
  }),
];

const server = setupServer(...handlers);
beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
```

---

## Custom Render Wrapper

```typescript
function renderWithProviders(
  ui: React.ReactElement,
  options?: RenderOptions
) {
  function Wrapper({ children }: { children: React.ReactNode }) {
    return (
      <QueryClientProvider client={new QueryClient()}>
        <BrowserRouter>
          {children}
        </BrowserRouter>
      </QueryClientProvider>
    );
  }
  return render(ui, { wrapper: Wrapper, ...options });
}
```

---

## Coverage Goals

| Metric | Target |
| :-- | :-- |
| Statements | 80%+ |
| Branches | 70%+ |
| Functions | 80%+ |
| Lines | 80%+ |

---

## What to Test vs Skip

| Test | Skip |
| :-- | :-- |
| User interactions | Implementation details |
| Business logic | Library internals |
| Edge cases | Styles / CSS |
| Error states | Third-party code |
| Accessibility | Getter/setter boilerplate |
| Data transformations | Constants |

---

See: [[5. Testing.md]] for full guide

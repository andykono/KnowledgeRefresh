# Design & Architectural Patterns Guide

Руководство по паттернам проектирования для современной разработки на **React + TypeScript**.

---

## Structure

```
Patterns/
├── 1. Design Patterns/              ← Classic GoF patterns
│   ├── 1. Patterns.md               ← Index with tables
│   ├── 1.1 Singleton.md
│   ├── 1.2 Factory Method.md
│   ├── 1.3 Observer.md
│   ├── 1.4 Decorator.md
│   ├── 1.5 Strategy.md
│   └── 1.6 Facade.md
│
├── 2. Architectural Patterns/       ← Application-level patterns
│   ├── 2. Architectural Patterns.md
│   ├── 2.1 MVC, MVVM, Clean, Onion, FSD.md
│   └── 2.2 State Management Patterns.md
│
├── 3. Anti-Patterns/                ← What NOT to do
│   ├── 3. Anti-Patterns.md
│   ├── 3.1 React Anti-Patterns.md
│   ├── 3.2 State Management Anti-Patterns.md
│   └── 3.3 TypeScript Anti-Patterns.md
│
├── QUICK_REFERENCE.md               ← Cheat sheet
└── README.md                        ← This file
```

> **Note:** React-specific patterns (Compound Components, HOCs, Custom Hooks, Context API Patterns) have been moved to [[1. React/9. React Patterns/9. React Patterns.md]]. Testing content is at [[1. React/11. Testing/5. Testing.md]]. Real-World Examples are at [[1. React/14. Real-World Examples/8. Real-World Examples.md]].

---

## Recommended Learning Path

### Week 1: Design Patterns Basics
```
1. Read: 1. Design Patterns / 1. Patterns.md
2. Learn: Singleton, Factory, Observer
3. Practice: write examples for each
```

### Week 2: Structural & Behavioral
```
1. Learn: Decorator, Strategy, Facade
2. Practice: apply in real code
```

### Week 3: Architecture
```
1. Choose an approach: Component-Based → MVVM → FSD
2. Read: 2. Architectural Patterns
3. Apply to your project
```

### Week 4: Anti-Patterns
```
1. Read: 3. Anti-Patterns
2. Review your code for anti-patterns
3. Fix issues found
```

---

## Quick Pattern Selection

**Need to create different types of objects?**
→ [[1.2 Factory Method.md]]

**Global instance (API client, config)?**
→ [[1.1 Singleton.md]]

**One object notifying many about changes?**
→ [[1.3 Observer.md]]

**Add behavior without modifying a class?**
→ [[1.4 Decorator.md]]

**Choose algorithm at runtime?**
→ [[1.5 Strategy.md]]

**Hide complexity behind a simple API?**
→ [[1.6 Facade.md]]

**How to organize application code?**
→ [[2. Architectural Patterns/2. Architectural Patterns.md]]

**Code seems "wrong" but works?**
→ [[3. Anti-Patterns/3.1 React Anti-Patterns.md]]

---

## Quick Comparison Table

| Pattern | Type | Problem | Difficulty |
| :-- | :-- | :-- | :-- |
| **Singleton** | Creational | Global instance | Easy |
| **Factory** | Creational | Flexible creation | Easy |
| **Observer** | Behavioral | Pub-sub | Medium |
| **Strategy** | Behavioral | Swappable algorithms | Medium |
| **Decorator** | Structural | Add behavior | Medium |
| **Facade** | Structural | Simplify complex API | Medium |
| **MVVM** | Architectural | Separate UI from logic | Medium |
| **Clean Architecture** | Architectural | Enterprise, testability | Hard |
| **Onion Architecture** | Architectural | Domain-driven design | Hard |
| **FSD** | Architectural | Scale large projects | Medium |

---

## Resources

- [Refactoring.guru Design Patterns](https://refactoring.guru/design-patterns)
- [React Docs](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Feature-Sliced Design](https://feature-sliced.design/)

---

**Last Updated:** February 25, 2026
**Version:** 3.0

---

Start with [[QUICK_REFERENCE.md]] for a quick overview!

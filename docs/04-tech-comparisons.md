# Technology Choice Comparisons & Trade-Off Analysis

## 1. State Management: React Context API + useReducer vs Redux vs Zustand vs Recoil

| Metric | Chosen: Context API + useReducer | Redux Toolkit (RTK) | Zustand | Recoil / Jotai |
|---|---|---|---|---|
| **External Dependencies** | **0 KB (Built into React)** | ~40 KB | ~3 KB | ~14 KB |
| **Boilerplate** | Low (Single provider & reducer file) | Moderate (Slices, store setup) | Minimal | Minimal |
| **Re-render Optimization** | Context triggers re-renders on consumers | Selector-based granular subscriptions | Selective state subscriptions | Atomic subscriptions |
| **Fit with Amazon Clone** | **Optimal** (Lightweight, robust for e-commerce cart) | Overkill for single-developer app | Good modern alternative | Unnecessary complexity |

- **Why Context API Was Used**: Provides clean centralized state management for the basket and authenticated user without installing external dependencies.
- **30-Second Interview Answer**: "I chose React's built-in Context API paired with useReducer because it provides Redux-like unidirectional data flow and predictability for shopping cart operations while avoiding external dependency bloat."

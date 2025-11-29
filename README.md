# Refactor: Modernize budget viewer state with Signals

## Overview
This PR refactors the SelectBudgetPageComponent and BudgetTableComponent from RxJS observables to Angular Signals for state management. The parent component now uses `signal()` to hold data and `effect()` to react to changes, while the child component consumes these signals directly.

## Key Benefits of Signals
- **Fine-grained reactivity**: Only affected parts of the template re-render.
- **Declarative style**: Replaces imperative subscriptions with `effect()` and `computed()`.
- **Simpler memory management**: No need to unsubscribe manually.
- **Zoneless component**: Template works without `CommonModule`.

## Difference from RxJS
- **RxJS** is stream-based and pushes data reactively. You often need `subscribe` or `async` pipe.
- **Signals** are state containers; changes propagate automatically through reactive computations and effects.

## Personal experience
Previously, I have worked in React and Vue where state management also used reactive paradigms (`useState`, `computed`, `ref`). Signals provide a cleaner, Angular-native approach compared to RxJS streams for local component state.

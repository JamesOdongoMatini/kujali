# Feature: Add Note to Budget Command

## Overview
This PR adds a new backend feature to the Kujali application using the CQRS pattern. It introduces a command (`AddNoteToBudgetCommand`) and its handler (`AddNoteToBudgetHandler`) to support adding notes to budgets.

## Design Choices
- **Command** encapsulates all necessary data to add a note to a budget.
- **Handler** validates the command, then calls the repository to persist the data.
- Follows CQRS pattern: separation of command (write) logic from query (read) logic.

## Dependencies
- Uses the repository obtained via the handler’s toolkit (`getRepository`) to interact with Firestore/Postgres.

## Serverless Deployment Considerations
- Handler can be deployed as a serverless function using the existing @ngfire/functions setup.
- Each invocation is stateless, and scaling is automatic, supporting multiple concurrent budget notes submissions.
- Serverless model reduces operational overhead and provides automatic scaling.

## Backend Development Understanding
- Command-handler pattern allows for clear separation of concerns.
- Promotes testability and maintainability.
- Provides a structured way to extend additional budget operations in the future.
# Feature: Add Note to Budget Command

## Overview
This PR adds a new backend feature to the Kujali application using the CQRS pattern. It introduces a command (`AddNoteToBudgetCommand`) and its handler (`AddNoteToBudgetHandler`) to support adding notes to budgets.

## Design Choices
- **Command** encapsulates all necessary data to add a note to a budget.
- **Handler** validates the command, then calls the repository to persist the data.
- Follows CQRS pattern: separation of command (write) logic from query (read) logic.

## Dependencies
- Uses the repository obtained via the handler’s toolkit (`getRepository`) to interact with Firestore/Postgres.

## Serverless Deployment Considerations
- Handler can be deployed as a serverless function using the existing @ngfire/functions setup.
- Each invocation is stateless, and scaling is automatic, supporting multiple concurrent budget notes submissions.
- Serverless model reduces operational overhead and provides automatic scaling.

## Backend Development Understanding
- Command-handler pattern allows for clear separation of concerns.
- Promotes testability and maintainability.
- Provides a structured way to extend additional budget operations in the future.





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

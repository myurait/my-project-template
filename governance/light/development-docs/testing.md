# Testing Strategy

## 1. Test Scope

- Add tests for important paths, edge cases, and obvious failure behavior.
- Use manual testing when automation is not worth the setup cost yet.

## 2. Test Design

- Design tests from real user workflows, not only implementation details.
- Check environment differences when behavior depends on shells, containers, or external services.

## 3. Manual Tests

- Store stable manual scenarios under `reference/` or in dedicated scenario files when needed.
- Explain why a scenario is still manual.


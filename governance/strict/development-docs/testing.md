# Testing Strategy

## 1. Test Scope

- Unit tests for isolated logic
- Integration tests for module boundaries and real workflows
- Manual tests only when automation is not yet practical

## 2. Test Design

- Design tests from real user workflows, not only implementation details.
- Enumerate the real actors involved in the workflow.
- Check environment differences between developer, CI, automation, and end user.
- Verify permissions, paths, shells, containers, and network assumptions when relevant.

## 3. Manual Tests

- Store stable manual scenarios under `reference/` or dedicated scenario files.
- Record why the scenario is still manual.
- Record what would be required to automate it.


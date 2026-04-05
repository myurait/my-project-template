# Testing Strategy

## 1. Test Scope

- Unit tests for isolated logic.
- Integration tests for module boundaries and real workflows.
- Manual tests only when automation is not yet practical.

## 2. Test Coverage

- Aim for meaningful coverage rather than high percentages.
- Keep tests focused and isolated.

## 3. Test Design

- Design tests from real user workflows, not only implementation details.
- Enumerate the real actors involved in the workflow.
- Check environment differences between developer, CI, automation, and end user.
- Verify permissions, paths, shells, containers, and network assumptions when relevant.

### Test Scenario Design Checklist

- [ ] All actors who operate this feature have been identified.
- [ ] Environment differences between the tester and each actor have been checked (PATH, working directory, command resolution).
- [ ] When the scenario mixes "tester actions" and "real actor actions", both are verified.

### Execution Environment Verification

When actor analysis reveals environment differences, verify:
- Environment variable inheritance (child processes, containers, background workers).
- File permission and path resolution differences.
- Network access differences.

## 4. Test Isolation

- Use dependency injection to isolate tests from the file system and external services.
- When tests must be skipped, use categorized tags:
  - `skip('agent-driven: ...')` — depends on autonomous AI agent behavior.
  - `skip('manual: ...')` — requires real environment or long wait.
  - `skip('future: ...')` — feature not yet implemented.

## 5. Manual Tests

- Store stable manual scenarios under `reference/` or dedicated scenario files.
- Record why the scenario is still manual.
- Record what would be required to automate it.

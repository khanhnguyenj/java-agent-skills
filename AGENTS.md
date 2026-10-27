# AGENTS.md

## Project Overview

This is a Java project.

Before making changes, inspect the existing project structure, `pom.xml`, source code, tests, and configuration files to understand the current architecture and conventions.

Do not introduce a new framework, library, architectural pattern, or coding convention unless it is required by the task or already used by the project.

## Technology Stack

- Java: Use the version configured by the project.
- Build tool: Maven.
- Follow the versions defined in `pom.xml` and Maven parent/dependency management.
- If Spring Boot is used, follow the Spring Boot version already configured by the project.
- Prefer existing dependencies and utilities before introducing new ones.

Never change the Java, Spring Boot, or dependency versions unless explicitly requested.

---

## Project Structure

Follow the existing package and module structure.

Typical Maven structure:

```text
src/
├── main/
│   ├── java/
│   └── resources/
└── test/
    ├── java/
    └── resources/
```

For multi-module projects, preserve the existing module boundaries.

Do not move classes between modules or packages unless the task requires it.

---

## Java Version

Use the Java version configured in the project.

Before using a language feature or API, verify that it is supported by the configured Java version.

Prefer modern Java features when they improve readability and are compatible with the project's configured Java version.

Do not introduce preview features unless the project already uses them or the task explicitly requests them.

---

## Coding Style

Follow the existing coding style in the repository.

General preferences:

- Use clear and descriptive names.
- Prefer small, focused methods.
- Keep classes focused on a single responsibility.
- Avoid unnecessary abstraction.
- Avoid premature optimization.
- Prefer composition over inheritance where appropriate.
- Use interfaces where they provide meaningful abstraction, not simply because an implementation exists.
- Prefer immutable objects where practical.
- Use `final` when it improves clarity or prevents accidental reassignment.
- Avoid unnecessary getters/setters and boilerplate when the project already uses appropriate Java features or libraries.
- Do not add comments that merely restate what the code does.

Do not reformat unrelated code.

Keep changes focused on the requested task.

---

## Null Handling

Follow the project's existing null-handling strategy.

Do not introduce `Optional` indiscriminately.

Use `Optional` primarily for return values where it communicates that a value may be absent.

Avoid using `Optional` for:

- Entity fields
- DTO fields
- Method parameters
- Local variables where a simple null check is clearer

Do not silently change existing null semantics.

---

## Exceptions

Use meaningful exception types.

Do not catch `Exception` or `Throwable` unless there is a specific reason.

Do not swallow exceptions.

Preserve the original cause when wrapping exceptions.

Prefer domain-specific exceptions when the application already defines them.

Error messages should contain enough context to diagnose the problem without exposing sensitive information.

---

## Logging

Use the project's existing logging framework.

Do not use `System.out.println()` for application logging.

Use appropriate log levels:

- `ERROR` — unexpected failures requiring attention
- `WARN` — recoverable or potentially problematic situations
- `INFO` — important application lifecycle or business events
- `DEBUG` — diagnostic information
- `TRACE` — very detailed diagnostic information

Do not log:

- Passwords
- Access tokens
- API keys
- Secrets
- Full payment card numbers
- Sensitive personal information

Avoid logging the same exception multiple times at different layers unless there is a clear reason.

---

## Testing

Every behavior change should have appropriate tests.

Prefer:

1. Unit tests for isolated business logic.
2. Integration tests for interactions between components.
3. End-to-end tests only when necessary.

Follow the existing testing framework and conventions.

Do not modify or remove existing tests simply to make a build pass.

When fixing a bug, add a regression test whenever practical.

Tests should verify behavior rather than implementation details.

Avoid excessive mocking.

---

## Maven

Use Maven for building and testing.

Before completing a change, run the smallest appropriate verification first.

Typical commands:

```bash
./mvnw test
```

If Maven Wrapper is not available:

```bash
mvn test
```

For a full verification:

```bash
./mvnw verify
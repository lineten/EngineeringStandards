# Company Coding Guidelines

## 1. Introduction & Scope

This document outlines the coding standards, guidelines, and best practices for all software development within ***LineTen***. Our goal is to foster a consistent, readable, maintainable, and high-quality codebase across all projects.

**Purpose:**

* **Consistency:** Ensure a uniform coding style, making it easier for developers to read, understand, and contribute to any project.

* **Readability:** Improve code clarity, reducing cognitive load and accelerating comprehension.

* **Maintainability:** Facilitate easier debugging, refactoring, and feature additions over time.

* **Collaboration:** Streamline code reviews and enhance teamwork by establishing a common language and set of expectations.

* **Quality & Security:** Promote robust, secure, and performant code through adherence to proven practices.

**Audience:**
This document is intended for all developers, engineers, and **anyone** contributing code or reviewing code at ***LineTen***.

**Applicability:**
These guidelines apply to all new code developed at LineTen. For existing (legacy) codebases, apply these guidelines when significant refactoring or new feature development occurs within a module. Minor changes should generally conform to the existing style of the surrounding code to avoid unnecessary churn, but always strive for improvement where feasible.

**Deviation Policy:**
While these guidelines aim to cover most scenarios, there may be rare cases where strict adherence is impractical or detrimental. Deviations are permissible only with explicit team consensus and a clear, documented rationale (e.g., in a code comment, pull request description, or design document). Prioritize common sense and code clarity over slavish adherence to any single rule.

**How to Contribute:**
These guidelines are a living document. We encourage all team members to suggest improvements, clarifications, or additions. Please submit a pull request to the `EngineeringStandards` repository with your proposed changes.

## 2. General Principles & Best Practices

These principles are fundamental and apply regardless of the programming language.

### 2.1. Readability & Clarity

* **Self-Documenting Code:** Strive to write code that is inherently understandable through clear naming, logical structure, and concise expressions. Comments should explain *why* something is done, not *what* it does (unless the "what" is non-obvious).

* **Simplicity:** Favor the simplest, most straightforward solution that meets the requirements. Avoid unnecessary complexity, clever tricks, or over-engineering.

* **DRY (Don't Repeat Yourself):** Avoid duplicating code. Abstract common logic into reusable functions, classes, or modules.

* **YAGNI (You Aren't Gonna Need It):** Do not implement functionality that is not currently required. Build only what is needed now, allowing for future extensibility.

### 2.2. Maintainability & Modularity

* **Small, Focused Units:** Break down functions, methods, and classes into small, cohesive units that each have a single, clear responsibility.

* **Loose Coupling, High Cohesion:** Design components to be as independent as possible (low coupling) and for elements within a component to be strongly related (high cohesion).

* **Clear Interfaces:** Define clear and stable interfaces for modules and components to minimize ripple effects when changes are made.

### 2.3. Testing

* **Automated Tests:** All new features and bug fixes must be accompanied by appropriate automated tests (unit, integration, end-to-end) to ensure correctness and prevent regressions.

* **Test Coverage:** Aim for 100% test coverage on new code. Focus on testing critical paths and complex logic.

* **Meaningful Tests:** Tests should be readable, independent, and test a single piece of functionality.

### 2.4. Performance

* **Optimize When Necessary:** Optimize for performance only when a bottleneck has been identified through profiling. Premature optimization can lead to complex and unreadable code.

* **Efficient Algorithms & Data Structures:** Choose algorithms and data structures appropriate for the problem's scale and performance requirements.

### 2.5. Security

* **Secure by Design:** Consider security implications at every stage of development.

* **Input Validation:** Always validate and sanitize all external input to prevent common vulnerabilities (e.g., SQL injection, XSS).

* **Authentication & Authorization:** Implement robust authentication and authorization mechanisms. Never hardcode credentials.

* **Least Privilege:** Grant only the minimum necessary permissions to users and services.

### 2.6. Error Handling & Logging

* **Consistent Error Handling:** Establish a consistent strategy for handling errors and exceptions across the codebase (e.g., using custom exceptions, returning error objects, or graceful degradation).

* **Informative Error Messages:** Provide clear, actionable error messages that aid in debugging and troubleshooting.

* **Structured Logging:** Use structured logging with appropriate log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL). Log sufficient context to diagnose issues without exposing sensitive information.

## 3. Code Style & Formatting

These guidelines ensure visual consistency and readability.

### 3.1. Naming Conventions

* **Variables:**

  * `camelCase` for local variables and function parameters.

  * `UPPER_SNAKE_CASE` for global constants.

* **Functions/Methods:** `camelCase` for functions and methods, typically starting with a verb (e.g., `calculateTotal`, `getUserData`).

* **Classes/Interfaces:** `PascalCase` for class and interface names.

* **Files:** `kebab-case` for general files (e.g., `user-profile.js`), `snake_case` for Python files (e.g., `user_profile.py`).

* **Meaningful Names:** Names should be descriptive and convey the purpose or intent of the entity. Avoid single-letter names.

### 3.2. Indentation & Whitespace

* **Indentation:** Use **4 spaces** for indentation. **Never use tabs.**

* **Line Length:** Limit lines to a maximum of **100 characters**. Break long lines at logical points.

* **Whitespace:**

  * Use spaces around operators (`=`, `+`, `-`, `==`, `&&`, etc.).

  * Use a space after commas, colons, and semicolons (e.g., `function(arg1, arg2);`).

  * Use blank lines sparingly to separate logical blocks of code within functions or between method definitions.

### 3.3. Comments & Documentation

* **Docstrings/Docblocks:** All public classes, functions, and methods must have a docstring/docblock explaining their purpose, parameters, return values, and any side effects or exceptions.

* **Inline Comments:** Use inline comments sparingly for complex logic, workarounds, or to explain non-obvious decisions ("why" not "what").

* **No Commented-Out Code:** Do not commit commented-out code. If code is no longer needed, remove it. Version control tracks its history.

### 3.4. Imports / Includes

* **Ordering:** Imports should generally be grouped and ordered:

  1. Standard library imports.

  2. Third-party library imports.

  3. Local/project-specific imports.

* **Absolute vs. Relative:** Prefer absolute imports where possible to avoid ambiguity.

* **Unused Imports:** Remove all unused imports.

## 4. Project Structure & Organization

Consistency in project layout helps developers navigate quickly.

* **Standard Directory Layout:** Adopt a consistent top-level directory structure for common project types (e.g., `src/`, `tests/`, `docs/`, `config/`, `scripts/`).

* **Module Organization:** Group related files and components logically, either by feature or by type, depending on scale and complexity.

* **Configuration:** Store application configuration in dedicated files (e.g., `.env`, `config.json`, `appsettings.json`). Never hardcode configuration values in code.

## 5. Version Control (Git)

* **Branching Strategy:**
  * **Strategy:** Adhere to Trunk-Based Development.
    
  * **Branch Names:** should start with the Jira Ticket Number

* **Commit Messages:**

  * **Concise Subject Line:** Start with the Jira Ticket Number

  * **Detailed Body:** Provide a more detailed explanation in the body, explaining the "what" and "why" of the change.

* **Pull Requests (PRs):**

  * **Descriptive PRs:** Include a clear title and description of the changes, their purpose, and any relevant context.

  * **Self-Review:** Before requesting review, perform a self-review of your changes.

  * **Reviewers:** Request reviews from appropriate team members.

* **No Force Pushing to Shared Branches:** Never force push to shared branches (e.g., `main`, `develop`).


By adhering to these guidelines, we collectively contribute to a higher quality, more consistent, and ultimately more successful software development environment at \[Your Company Name\]

# Team Coding Standards and Best Practices

## 1. Core Philosophy

All code created needs to be robust and scalable. Aim to write clean, maintainable, and self-explanatory code that stands the test of time. Focus on clear responsibilities, separation of concerns, and highly testable code.

## 2. Architecture

*   **Style:** Our architecture is event-driven, with a strong emphasis on Domain-Driven Design (DDD) and Clean Architecture principles.
*   **Microservices:** We build our systems as a collection of focused, independent microservices.
*   **Event-Driven:** We use Azure Service Bus for asynchronous messaging between services to ensure loose coupling and scalability.
*   **CQRS:** We use the Command and Query Responsibility Segregation (CQRS) pattern, facilitated by the MediatR library, to separate read and write operations.

## 3. Design Principles

*   **SOLID:** All code MUST adhere to the SOLID principles (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
*   **Dependency Injection (DI):** We use DI extensively to manage dependencies. Dependencies SHOULD be injected via constructors and referenced through interfaces.
*   **Separation of Concerns (SoC):** Logic must be clearly separated. For example, controller actions should be minimal, delegating all business logic to a service or a MediatR handler.
*   **Avoid Unnecessary Abstractions:** Create abstractions only when they provide a clear benefit, such as decoupling major components or enabling easier testing. Avoid abstracting for the sake of abstraction.

## 4. C# and .NET Best Practices

### Naming Conventions

*   **Public Members:** `PascalCase` for all public classes, interfaces, methods, properties, and events.
*   **Local Variables & Private Fields:** `camelCase` for all local variables and private fields. Private fields SHOULD be prefixed with an underscore (e.g., `_privateField`).

### Code Style & Readability

*   **Clarity:** Code should be self-explanatory. Method names must clearly describe their purpose.
*   **Avoid Deep Nesting:** Keep methods short and focused. Minimize cognitive load by avoiding deep nesting and multiple levels of indentation.
*   **Eliminate `else` Statements:** Where possible, eliminate `else` statements by using guard clauses, early returns, or `break` statements. Aim for flat, readable code.
*   **Avoid Magic Values:** Do not use magic strings or numbers. Define them as constants with meaningful names.

### Asynchronous Programming

*   **Favor `async`:** Use `async` and `await` for all I/O-bound operations to ensure the application remains responsive and scalable.
*   **Async Suffix:** Asynchronous methods MUST be suffixed with `Async` (e.g., `DoWorkAsync`).

### Error Handling

*   **Result Pattern:** We prefer methods that return a `Result` object (containing either a success value or an error) instead of throwing exceptions for predictable business rule failures or validation errors. Exceptions should be reserved for truly exceptional, unexpected, or unrecoverable situations.

### Object-Oriented Programming

*   **Encapsulation:** Use proper encapsulation. Expose only what is necessary from a class.
*   **Interfaces:** Always use interfaces for dependencies to facilitate testing and adhere to the Dependency Inversion Principle.
*   **Single Responsibility Principle (SRP):** When creating a class, ensure it has only one reason to change.

## 5. Data and DTOs

*   **Data Storage:** We use a mix of data storage technologies based on the use case:
    *   **Entity Framework Core:** For relational data.
    *   **Azure Table Storage:** For NoSQL key-value data.
    *   **Azure Blob Storage:** For unstructured data like files and images.
*   **Data Transfer Objects (DTOs):**
    *   DTOs MUST NOT contain any domain logic.
    *   Use C# `record` types for creating immutable DTOs and models.

## 6. Documentation

*   **XML Comments:** All public members (classes, methods, properties, interfaces) MUST have XML or triple-slash (`///`) comments explaining their purpose, parameters, and return values. This is crucial for generating documentation and improving IntelliSense for all team members.

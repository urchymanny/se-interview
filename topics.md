# Interview Helpers for SE

Interviewing as a software developer, engineer, full-stack, etc., there are key concepts that make your life easier.

### 1. **Software Development Practices**

- **Agile/Scrum Methodology**:
  - Sprint Planning
  - Backlog Grooming
  - Retrospectives
- **Technical Debt**:
  Implementing quick solutions that work without taking notes of the performance, redundancies in order to go to market as quickly as possible
  - Strategies for Managing and Reducing Debt
    - Prioritization
    - Incremental Refactoring
    - Code Reviews
    - Automated Testing - to make sure the refactoring doesn't break the app
    - Documentation
  - Refactoring Practices
    - Extract Method - break down to reusable and clear code.
    - Rename Variables and Methods - to be more precise and more manageable
    - Simplify Conditionals - using polymorphism or guard clauses
    - DRY Code - Reduce Code Duplication
    - Encapsulate Classes
    - Decouple entities

### 2. **Code Quality & Testing**

- **Testing Types**:
  - **Unit Testing**: Isolating individual components.
  - **End-to-End (E2E) Testing**: Testing the entire workflow. Gitlab CI
  - **Integration Testing**: Testing interactions between components or systems. e.g. Interaction of application with the database.
  - **Performance Testing**: Ensuring scalability and responsiveness. (space complexity, time complexity)
- **Quality Assurance Tools**:
  - **Linting**: Code style consistency. (RuboCop, Pylint)
  - **Test Coverage**: Ensuring the codebase is well tested. (SimpleCov)

### 3. **Design Patterns & Principles**

- **Object-Oriented Design Principles**:
  - **SOLID Principles**:
    - **Single Responsibility**: A class should have only one reason to change, meaning it should only have one responsibility or job.
    - **Open/Closed**: A class or function should be open for extension (able to add new functionality) but closed for modification (existing code should not be altered when extending behavior).
    - **Liskov Substitution**: Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. Subclasses should uphold the behavior and properties of the parent class.
    - **Interface Segregation**: No client should be forced to depend on interfaces it does not use. Instead of one large interface, smaller, more specific interfaces should be used.
    - **Dependency Inversion**: High-level modules should not depend on low-level modules. Both should depend on abstractions. Additionally, abstractions should not depend on details, but details should depend on abstractions.
  - **Common Design Patterns**:
  - **Singleton**: Ensuring a single instance.
  - **Builder**: Step-by-step object creation.
- **OOP Concepts**:
  - **Encapsulation**: Hiding internal states.
  - **Inheritance**: Reusing code via parent-child relationships.
  - **Polymorphism**: Dynamic method dispatch.

### 4. **Code Quality & Maintainability**

- **Good Code**:
  - **Readability**: Clarity in code structure and logic.
  - **Maintainability**
  - **Coupling**: Striving for low coupling and high cohesion.

### 5. **Algorithm & Performance Analysis**

- **Big-O Notation**:
  - Time and space complexity for algorithms.

### 6. **API Design & Tools**

- **APIs**:
  - **Swagger**: API documentation.
  - **Postman**: API testing tool.

### 7. **References & Resources**

- Documentation and learning materials to solidify concepts.

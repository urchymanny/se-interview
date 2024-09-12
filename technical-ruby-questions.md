
# Senior Ruby Developer Interview Preparation

## 1. Ruby-Specific Questions

### What are the differences between `Proc` and `Lambda` in Ruby?
- `Proc` and `Lambda` are both types of closures in Ruby.
- **Lambda** checks the number of arguments passed, while **Proc** does not.
- **Lambda** returns control back to the method after execution, whereas **Proc** returns immediately to the calling code.

### How does Ruby handle garbage collection?
- Ruby uses a **mark-and-sweep** garbage collection technique to manage memory. The garbage collector marks objects that are no longer referenced and then sweeps them away to free up memory.

### Explain how blocks, procs, and lambdas work in Ruby.
- **Blocks** are anonymous chunks of code passed to methods, enclosed in `{}` or `do...end`.
- **Procs** are saved blocks, created with `Proc.new` or `proc`. They are objects and can be stored in variables.
- **Lambdas** are similar to Procs but enforce strict argument checking and return behavior.

### What are `modules`, and how are they different from classes in Ruby?
- **Modules** are collections of methods and constants, used for namespacing and mixin functionality.
- Modules cannot be instantiated like classes but can be mixed into classes via `include` or `extend`.

### How does the `Enumerable` module work? Can you implement a method using it?
- The `Enumerable` module provides collection-related methods, assuming the object implements `each`.
- Example: Implementing a custom `map` method:
  ```ruby
  class MyCollection
    include Enumerable

    def initialize(collection)
      @collection = collection
    end

    def each
      @collection.each { |item| yield item }
    end
  end
  ```

### What are `symbols`, and how do they differ from strings?
- **Symbols** are immutable, reusable constant names, while **Strings** are mutable and consume more memory. Symbols are often used as identifiers or keys.

## 2. Object-Oriented Design & Patterns

### How would you implement the Singleton pattern in Ruby?
```ruby
class MySingleton
  include Singleton
end
```

### Can you describe how to apply SOLID principles in Ruby?
- **S**ingle Responsibility: Each class should have one responsibility.
- **O**pen/Closed: Classes should be open for extension but closed for modification.
- **L**iskov Substitution: Subclasses should be replaceable with base classes without altering functionality.
- **I**nterface Segregation: Clients should not be forced to depend on interfaces they don't use.
- **D**ependency Inversion: High-level modules should not depend on low-level modules.

### Explain how inheritance and mixins work in Ruby. When would you use one over the other?
- **Inheritance**: Used for an "is-a" relationship, where a subclass inherits behavior from a superclass.
- **Mixins**: Used for code reuse across different classes without a strict inheritance hierarchy.

## 3. Rails-Specific Questions

### How does the Rails routing system work?
- Rails routes map incoming requests to controller actions based on the URL pattern. You define routes in the `config/routes.rb` file.

### Explain the difference between `has_many` and `has_many :through`.
- `has_many` sets up a direct association, while `has_many :through` creates an indirect relationship through another model.

### How would you improve the performance of a Rails application?
- Use caching (fragment, page, or action caching).
- Optimize database queries (use indexes, avoid N+1 queries).
- Reduce asset load times (e.g., compress assets, use CDNs).

## 4. Testing & TDD

### How do you approach Test-Driven Development (TDD) in Ruby or Rails?
- Write tests before writing production code, ensuring each test covers a single piece of functionality. Refactor the code to make sure all tests pass.

### What testing libraries do you prefer (e.g., RSpec, Minitest) and why?
- **RSpec**: It has a readable DSL and is very flexible for behavior-driven development (BDD).
- **Minitest**: Lightweight and comes pre-installed with Ruby.

## 5. Performance Optimization

### How would you profile a Ruby application for performance issues?
- Use profiling tools such as `ruby-prof`, `rack-mini-profiler`, or New Relic to identify slow methods and queries.

### How would you optimize a slow ActiveRecord query?
- Use eager loading to avoid N+1 queries.
- Add database indexes to speed up lookups.

## 6. Database & ActiveRecord

### What are some best practices for managing database migrations in a Rails app?
- Always write reversible migrations.
- Ensure that migrations are run in development and staging before production.

### How do you handle N+1 query problems?
- Use `includes` to eager load associated records.

## 7. Architecture & Design

### How do you handle complex business logic in a Rails app?
- Extract complex logic into service objects, concerns, or decorators to keep models and controllers slim.

### How do you design APIs in Ruby/Rails?
- Use RESTful conventions.
- Version your APIs to allow changes without breaking clients.

## 8. DevOps & Deployment

### What deployment strategies do you use for Ruby applications?
- Use tools like Capistrano, Heroku, or Docker for automated deployment.

### How do you handle scaling a Rails application?
- Scale vertically by increasing server capacity or horizontally by adding more servers and using load balancers.

## 9. Code Review/Live Coding

### Review a sample Ruby code and suggest improvements.
- During a live review, focus on readability, performance, and adherence to coding standards.

## 10. Version Control and Collaboration

### How do you handle branching and merging in Git?
- Use a feature-branch workflow (e.g., Git Flow) with pull requests to review and merge code changes.

### What is your approach to conducting or receiving code reviews?
- Be constructive and provide actionable feedback. Focus on the code and not the coder.

# Extra
### 1. **Service Objects**
   - **Purpose**: Service objects are used to encapsulate complex business logic or processes that don't naturally belong to a model or controller. They keep models and controllers slim and focused on their primary responsibilities.
   - **Use Case**: Whenever you need to perform an action that involves multiple steps or touches different parts of the application, you should consider using a service object.
   - **Example**:
     ```ruby
     class ProcessOrder
       def initialize(order)
         @order = order
       end

       def call
         charge_customer
         send_confirmation_email
         update_inventory
       end

       private

       def charge_customer
         # logic for charging customer
       end

       def send_confirmation_email
         # logic for sending email
       end

       def update_inventory
         # logic for updating inventory
       end
     end
     ```
   - **Advantage**: It organizes and reuses complex logic while keeping controllers and models cleaner.

### 2. **Concerns**
   - **Purpose**: Concerns are modules used to extract shared functionality across multiple models or controllers. They are used to avoid duplication of code by mixing in reusable methods.
   - **Use Case**: When you have shared behavior across different models or controllers (e.g., a "soft delete" feature across multiple models), a concern is a good fit.
   - **Example**:
     ```ruby
     # app/models/concerns/soft_deletable.rb
     module SoftDeletable
       def soft_delete
         update(deleted_at: Time.current)
       end

       def deleted?
         deleted_at.present?
       end
     end

     # Including concern in model
     class User < ApplicationRecord
       include SoftDeletable
     end
     ```
   - **Advantage**: DRYs up your code by allowing shared logic to be reusable across multiple places in a consistent way.

### 3. **Decorators**
   - **Purpose**: Decorators are used to extend or modify the behavior of an object, typically for presentation purposes, without changing the original object itself. They are often used to format data or add methods specifically for the view layer.
   - **Use Case**: When you need to add functionality to an object without polluting the model or controller, or when a specific view representation of an object is needed.
   - **Example**:
     ```ruby
     # app/decorators/user_decorator.rb
     class UserDecorator < SimpleDelegator
       def formatted_name
         "#{first_name.capitalize} #{last_name.capitalize}"
       end

       def last_login_display
         last_login_at.strftime("%B %d, %Y")
       end
     end

     # Usage
     decorated_user = UserDecorator.new(user)
     decorated_user.formatted_name # => "John Doe"
     ```
   - **Advantage**: Keeps models slim by moving presentation-related logic into decorators, preserving the Single Responsibility Principle.

---

### Key Differences:
- **Service Objects** are used for organizing complex business logic into isolated classes.
- **Concerns** are used to share common behavior across models or controllers by mixing in reusable code.
- **Decorators** are used to extend or modify the behavior of objects, typically for view-related tasks, without altering the original object itself.

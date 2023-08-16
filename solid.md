`SOLID` - principles

`Single responsibility principle` - One class does one thing, instead of doing too much work in a single method, separate into a new class for different or next step of work.

`Open Closed Principle` - An interface should be open for extending but closed for modification. Should be able to abstract out the work and implement different use cases not a single interface with multiple use cases within it, constantly extending or adding work to the single interface, class or module.

`Liskov Substitution Principle` - Using an inheriting class should run separate from the parent without changing parent behaviour, a class performing work that isn't accurate the expected implementation is broken, using a setter for two variables when different implementations may only use one.

`Interface Segregation Policy` - Interfaces should only be implementing if used, a class shouldn't depend on methods in an interface that it won't use. May need a separate interface for different functionalities instead of one interface for many different idea of realizing work for them, separating work to it's own interface.

`Dependency Inversion` - Abstractions shouldn't depend on details and details should be implementations of an abstraction

## Container, Dependency, and IOC

- Dependency Injection is a technique whereby a class does not instantiate its own dependencies but rather they passed to it through a constructor, factory method, or setter method.

    - Loose coupling between classes. Different implementations can be. Particularly helpful for tests.
    - Reusable object instances. This can reduce the amount of objects that need to be garbage collected.

- Interfaces can be used for designing loosely coupled systems; They are allow for multiple implementations of the same functionality.

- `ApplicationContext` is the interface that represents the Spring IoC container. The IoC container is responsible for instantiating and mananging _Spring beans_. These beans are usually config classes and service layer objects. Dependency injection is one of the functions of the IoC.

- For integration tests, `@ContextConfiguration` is a class-level annotation used to define how to load and manage an `ApplicationContext`. The annotation has attributes that can be used to specify config files where various beans are defined.

- `@PropertySource` is used to register files from which Spring environment properties can be loaded. These properties can then be injected into Spring beans using `@Value`

- Component-scanning is the process whereby the Spring searches for classes configured as beans and loads them into the IoC container. In vanilla Spring, The `@ComponentScan` is used to direct the search.

- `@Bean` is method level annotation used to define Spring beans in a class annotated with `@Configuration`.

- `@Qualifier` is used to annotate a dependency when there exists more than one bean that would satisfy it.

- `@Profile` is used to map beans to different Spring profiles. It can be used on both component classes and `@Bean` methods. E.g., when a bean class is annotated with `@Profile("dev")`, the bean is only instantiated by the Spring container when the `dev` profile was specified when launching the application. 

- The Spring `Environment` abstraction contains key-value pairs of properties that can be accessed by the applications. Sources of properties include:
    - `application.properties` or `applicatin-{profile}.properties`file
    - Operating System environment variables
    - `@PropertySource` annotations on config classes.

## Aspect Oriented Programming (AOP) 

- Aspect Oriented Programming(AOP) is a programming model used to separate cross-cutting concerns from business logic. This way additional behaviour can be added to existing code without modifying the code itself. 

- Aspect: the logic of a cross-cutting concern. E.g., logging, transaction management.
- Join Point: A point during program execution. Always represents method execution in Spring AOP.
- Point cut: A predicate that matches a join point.
- Advice: Action taken by an aspect a particular join point.

- Spring AOP supports the following advice types:
    - Before: executes before a join point
    - After: executes after a join point regardless of how the method exits.
    - After throwing: executes if an exception is thrown.
    - After returning: If method exit successfully.
    - Around: executes before and after a join point.

## Data Management: Transactions 

A database transaction is a sequence of actions that are treated as a single unit of work. If any of the individual actions fail, the effects of the previous successful actions are undone(rollback).

There are two ways to implement transaction management:
1. Programmatic: Involves writing extra code
2. Declarative: Use of the @Transactional annotation at class level or on public methods of a classes.

- Spring creates proxies for classes where the @Transactional annotation is present. This allows for logic to be inserted before and after the method is executed.

- By default there is no rollback for checked exceptions. This default rollback policy can be overriden using the `rollbackFor` attributes of @Transactional

- Transaction propagation type determines how a method will behave if it is called by another component that has an existing transaction. The default propagation type is REQUIRED, this means the method must always execute as part of a transaction. It either joins a existing transaction or creates one. others include:
    - REQUIRES_NEW : always creates a new one.
    - SUPPORTS : Join a trxn if there is one.

- When a transactional method is called by another method(transactional or not) in same class the @Transactional annotation has no effect and the method executes normally. The AOP proxy is only active the class is used from another instance.

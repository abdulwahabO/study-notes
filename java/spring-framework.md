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

TODO: start from transaction questions of section 3.


## Spring Data JPA  




## Spring MVC Basics 


Section 1-6 – Spring MVC REST 


Section 1-7 – Security 

Section 1-8 – Testing 



Section 1-9 – Spring Boot Basics 


Section 1-10 – Spring Boot Auto Configuration 


Section 1-11 – Spring Boot Actuator 


Section 1-12 – Spring Boot Testing
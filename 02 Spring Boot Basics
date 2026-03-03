1️⃣ What Confused Me Initially

What is the difference between Spring and Spring Boot?

Why are there so many annotations?

What happens when we run the main method?

How does the server start automatically?

2️⃣ What I Understood Finally
🔹 What is Spring?

Spring is a framework used to build Java applications.

But it requires:

Manual configuration

XML setup

Server configuration

🔹 What is Spring Boot?

Spring Boot is built on top of Spring.

It:

Removes complex configuration

Auto-configures dependencies

Starts embedded server (Tomcat)

Makes REST API creation simple

In short:

Spring = Powerful
Spring Boot = Powerful + Easy

3️⃣ How Spring Boot Application Starts
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}

When this runs:

Spring container starts

Dependencies are injected

Embedded Tomcat server starts

Application runs on port 8080

Default URL:

http://localhost:8080
4️⃣ Important Annotations
@SpringBootApplication

Combination of:

@Configuration

@EnableAutoConfiguration

@ComponentScan

It tells Spring:
“Start everything automatically.”

@Component

Marks a class as Spring-managed bean.

@Component
public class MyClass {
}
@Service

Used for business logic layer.

@Service
public class UserService {
}
@Repository

Used for database layer.

@Repository
public interface UserRepository {
}
@RestController

Used to create REST APIs.

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello World";
    }
}
5️⃣ Dependency Injection (VERY IMPORTANT)
What confused me

What is dependency injection?

Why use @Autowired?

What I understood

Instead of creating objects manually:

❌ Wrong way:

UserService service = new UserService();

✅ Correct way (Spring way):

@Autowired
private UserService service;

Spring automatically creates and injects the object.

This is called:
Dependency Injection (DI)

Benefits:

Loose coupling

Better testing

Cleaner architecture

6️⃣ Project Structure (Standard)
com.bank.app
 ├── controller
 ├── service
 ├── repository
 ├── entity
 └── Application.java

Why structured this way?

Because backend follows layered architecture.

7️⃣ application.properties

This file controls configuration.

Example:

server.port=8080
spring.application.name=bank-app

You can change server port:

server.port=9090

Then app runs on:

http://localhost:9090
8️⃣ Layered Architecture Flow

Client (Frontend / Postman)
↓
Controller
↓
Service
↓
Repository
↓
Database

This separation makes code:

Clean

Scalable

Maintainable

9️⃣ Key Takeaways

Spring Boot reduces configuration

Annotations control behavior

Dependency Injection is core concept

Layered architecture is industry standard

Backend runs on embedded server automatically

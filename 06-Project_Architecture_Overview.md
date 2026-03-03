06️⃣ Project Architecture Overview
1️⃣ What Confused Me Initially

How do all parts connect together?

Where does REST fit?

Where does database fit?

Where does Kafka fit?

What is the real-world backend flow?

At first, everything felt separate.

Now it makes sense as one complete system.

2️⃣ High-Level System Architecture

Backend system consists of:

Client (Frontend / Postman)
↓
Controller Layer
↓
Service Layer
↓
Repository Layer
↓
Database

With Kafka:

Service
↓
Kafka Producer
↓
Kafka Topic
↓
Kafka Consumer
↓
Another Service

3️⃣ Layered Architecture Breakdown
🔹 Controller Layer

Responsibility:

Handles HTTP requests

Returns responses

No business logic

Example:

@RestController
@RequestMapping("/users")
public class UserController {
}

Thin layer. Just routing.

🔹 Service Layer

Responsibility:

Business logic

Validations

Processing rules

Example:

@Service
public class UserService {
}

This is the brain of backend.

🔹 Repository Layer

Responsibility:

Talks to database

Uses JPA

public interface UserRepository extends JpaRepository<User, Long> {
}

No manual SQL required.

🔹 Entity Layer

Represents database table.

@Entity
public class User {
}
4️⃣ Complete Flow with Database

Step-by-step:

Client sends POST request

Controller receives request

JSON → Converted to Java Object

Service processes logic

Repository saves data

Hibernate converts object → SQL

H2 stores data

Response returned as JSON

Everything automated by Spring Boot.

5️⃣ Complete Flow with Kafka

Example: User Registration

User created in database

Service publishes event

Kafka Topic stores event

Consumer reads event

Another service processes it

This enables:

Microservices communication

Loose coupling

Asynchronous processing

6️⃣ Monolithic vs Event-Driven
Monolithic

All components inside single application.
Simple but harder to scale.

Event-Driven (Modern)

Services communicate using events.
Scalable. Flexible. Enterprise-level.

This internship exposed real industry pattern.

7️⃣ Project Folder Structure
com.project.app
 ├── controller
 ├── service
 ├── repository
 ├── entity
 ├── config
 └── Application.java

Clean structure = maintainable code.

8️⃣ Technologies Used

Java

Spring Boot

REST APIs

JPA (Hibernate)

H2 Database

Apache Kafka

Each component has clear responsibility.

9️⃣ Key Design Principles Followed

Separation of Concerns

Layered Architecture

Dependency Injection

Loose Coupling

Event-Driven Communication

These are industry standards.

🔟 Real Industry Relevance

This architecture is used in:

Banking systems

Payment gateways

E-commerce platforms

Microservices-based systems

Understanding this means understanding real backend engineering.

1️⃣1️⃣ What I Learned Overall

Backend is structured, not random

REST is entry point

Service layer controls logic

Database integration is seamless with JPA

Kafka enables scalability

Clean architecture matters more than syntax

1️⃣2️⃣ Final Takeaway

This project helped me understand:

How real backend systems are built.

From request → to database → to event-driven communication.

It shifted my thinking from:

“Writing Java code”

to

“Designing backend systems.”

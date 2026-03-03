04️⃣ Database Integration (H2 + JPA)
1️⃣ What Confused Me Initially

What is JPA?

What is Hibernate?

Why do we use @Entity?

How does Spring connect to database automatically?

What is H2 and why use it instead of MySQL?

2️⃣ What I Understood Finally
🔹 JPA (Java Persistence API)

JPA is a specification used to map Java objects to database tables.

It allows:
Java Object ↔ Database Table mapping

🔹 Hibernate

Hibernate is the implementation of JPA.

So:

JPA = rules
Hibernate = actual working engine

Spring Boot automatically configures Hibernate.

3️⃣ H2 Database

H2 is:

In-memory database

Lightweight

Used for testing/demo

Data disappears after restart

Why used?
Because it's easy and doesn’t require external installation like MySQL.

4️⃣ Database Configuration (application.properties)
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update

spring.h2.console.enabled=true

H2 Console URL:

http://localhost:8080/h2-console

JDBC URL:

jdbc:h2:mem:testdb
5️⃣ Creating an Entity
What confused me

How does a Java class become a table?

What I understood

Using @Entity

Example:

import jakarta.persistence.*;

@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private int age;

    // getters and setters
}

What happens:

Class → Converted into table
Fields → Converted into columns

Important Annotations
Annotation	Purpose
@Entity	Marks class as table
@Id	Primary key
@GeneratedValue	Auto increment
@Column	Custom column config

Example with @Column:

@Column(nullable = false)
private String name;
6️⃣ Creating Repository Layer

Instead of writing SQL manually, we use:

JpaRepository

import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
}

That’s it. No SQL needed.

Built-in Methods You Get Automatically
Method	Purpose
save()	Insert/Update
findById()	Find by primary key
findAll()	Get all records
deleteById()	Delete record

Example:

userRepository.save(user);
7️⃣ Service Layer with Database
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    public User createUser(User user) {
        return userRepository.save(user);
    }

    public List<User> getAllUsers() {
        return userRepository.findAll();
    }
}
8️⃣ Controller Layer with Database
@RestController
@RequestMapping("/users")
public class UserController {

    @Autowired
    private UserService userService;

    @PostMapping
    public User create(@RequestBody User user) {
        return userService.createUser(user);
    }

    @GetMapping
    public List<User> getAll() {
        return userService.getAllUsers();
    }
}

Now your API is connected to database.

9️⃣ Full Flow with Database

Client → Controller
↓
Service
↓
Repository
↓
Hibernate
↓
H2 Database

🔟 ddl-auto Modes (VERY IMPORTANT)
spring.jpa.hibernate.ddl-auto=update

Options:

Value	Meaning
create	Drop and recreate table
update	Update schema
validate	Only check
none	Do nothing
1️⃣1️⃣ Advantages of JPA

No need to write SQL manually

Automatic table creation

Clean and readable code

Easy CRUD operations

Scalable architecture

1️⃣2️⃣ Key Takeaways

@Entity converts class into table

JpaRepository gives CRUD automatically

H2 is for development/testing

Spring Boot auto-configures database

Layered architecture remains clean

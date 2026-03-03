03️⃣ REST API Development (Spring Boot)
1️⃣ What Confused Me Initially

How does frontend actually send data to backend?

What is @RequestBody?

What is the difference between @PathVariable and @RequestParam?

What are HTTP status codes?

Why use ResponseEntity?

2️⃣ What I Understood Finally

REST API allows client (frontend / Postman) to communicate with backend using HTTP methods.

Main HTTP Methods:

Method	Purpose
GET	Fetch data
POST	Create data
PUT	Update data
DELETE	Delete data
3️⃣ Creating a Basic REST Controller
@RestController
@RequestMapping("/users")
public class UserController {

    @GetMapping
    public String getUsers() {
        return "All Users";
    }
}

Access URL:

http://localhost:8080/users
4️⃣ GET API

Used to fetch data.

Example:
@GetMapping("/{id}")
public String getUserById(@PathVariable int id) {
    return "User id: " + id;
}

URL:

http://localhost:8080/users/5

Here:

{id} = dynamic value

@PathVariable extracts it from URL

5️⃣ POST API

Used to create new data.

Example:
@PostMapping
public String createUser(@RequestBody User user) {
    return "User created: " + user.getName();
}
JSON Body (Postman):
{
  "name": "Lavanya",
  "age": 21
}

What happens internally:

JSON → Converted to Java object

Spring uses Jackson library automatically

6️⃣ PUT API

Used to update existing data.

@PutMapping("/{id}")
public String updateUser(@PathVariable int id, @RequestBody User user) {
    return "Updated user " + id;
}
7️⃣ DELETE API

Used to remove data.

@DeleteMapping("/{id}")
public String deleteUser(@PathVariable int id) {
    return "Deleted user " + id;
}
8️⃣ @RequestParam vs @PathVariable
@PathVariable

Value comes from URL path.

/users/10
@GetMapping("/{id}")
public String get(@PathVariable int id)
@RequestParam

Value comes from query parameter.

/users?id=10
@GetMapping
public String get(@RequestParam int id)
Difference Summary
Feature	PathVariable	RequestParam
From URL path	✅	❌
From query parameter	❌	✅
Mandatory usually	Yes	Can be optional
9️⃣ ResponseEntity (IMPORTANT)
What confused me

Why return ResponseEntity instead of String?

What I understood

It allows:

Custom HTTP status

Custom headers

Better control

Example:

@GetMapping("/{id}")
public ResponseEntity<String> getUser(@PathVariable int id) {
    if (id == 1) {
        return ResponseEntity.ok("User found");
    } else {
        return ResponseEntity.status(404).body("User not found");
    }
}

Common HTTP Status Codes:

Code	Meaning
200	OK
201	Created
400	Bad Request
404	Not Found
500	Internal Server Error
🔟 Full Flow of REST API

Client (Postman / Frontend)
↓
Controller receives request
↓
Service processes logic
↓
Repository talks to database
↓
Response returned as JSON

1️⃣1️⃣ Best Practices I Learned

Always use proper HTTP methods

Use meaningful endpoint names

Return proper status codes

Never expose internal errors directly

Keep controller thin (logic in service layer)

1️⃣2️⃣ Key Takeaways

REST API is backbone of backend

Annotations define behavior

JSON is automatically converted

ResponseEntity gives full control

Layered structure keeps code clean

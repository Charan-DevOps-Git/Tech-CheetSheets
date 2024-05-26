# Introduction

REST (Representational State Transfer) is an architectural style that defines a set of constraints for creating web services. RESTful APIs are designed to use HTTP requests to perform CRUD operations (Create, Read, Update, Delete).

# Basic Principles

1. Statelessness: Each request from a client to a server must contain all the information needed to understand and process the request. No client context is stored on the server between requests.
2. Client-Server Architecture: The client and server operate independently, allowing for separation of concerns.
3. Cacheability: Responses must define themselves as cacheable or not to prevent clients from reusing stale or inappropriate data.
4. Uniform Interface: A standardized way of communicating between the client and the server, typically using HTTP methods.

# HTTP Methods

- GET: Retrieve data from the server.
- POST: Send data to the server to create a new resource.
- PUT: Update an existing resource on the server.
- DELETE: Remove a resource from the server.
- PATCH: Partially update a resource on the server.

# Status Codes

- 200 OK: Request succeeded.
- 201 Created: Resource created successfully.
- 204 No Content: Request succeeded but no content returned.
- 400 Bad Request: The server could not understand the request.
- 401 Unauthorized: Authentication is required.
- 403 Forbidden: The server understood the request but refuses to authorize it.
- 404 Not Found: The requested resource could not be found.
- 500 Internal Server Error: The server encountered an unexpected condition.

# Designing RESTful APIs

- Resources and URIs: Use nouns to represent resources and HTTP methods to operate on them.
```
GET /api/users
GET /api/users/{id}
POST /api/users
PUT /api/users/{id}
DELETE /api/users/{id}
```

- Data Format: JSON is commonly used to format data.
```
{
    "id": 1,
    "name": "John Doe",
    "email": "john.doe@example.com"
}
```

# Implementing RESTful APIs in Spring Boot

1. Add Dependencies:
Maven:
```
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
    </dependency>
</dependencies>
```
Gradle:
```
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'mysql:mysql-connector-java'
}
```
2. Create an Entity:
```
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String email;

    // Getters and setters
}
```

3. Create a Repository:
```
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
}
```

4. Create a Service:
```
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;
import java.util.Optional;

@Service
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public List<User> getAllUsers() {
        return userRepository.findAll();
    }

    public Optional<User> getUserById(Long id) {
        return userRepository.findById(id);
    }

    public User createUser(User user) {
        return userRepository.save(user);
    }

    public User updateUser(Long id, User userDetails) {
        User user = userRepository.findById(id).orElseThrow();
        user.setName(userDetails.getName());
        user.setEmail(userDetails.getEmail());
        return userRepository.save(user);
    }

    public void deleteUser(Long id) {
        userRepository.deleteById(id);
    }
}
```

5. Create a Controller:
```
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/users")
public class UserController {
    private final UserService userService;

    @Autowired
    public UserController(UserService userService) {
        this.userService = userService;
    }

    @GetMapping
    public List<User> getAllUsers() {
        return userService.getAllUsers();
    }

    @GetMapping("/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        return userService.getUserById(id)
                .map(ResponseEntity::ok)
                .orElseGet(() -> ResponseEntity.notFound().build());
    }

    @PostMapping
    public ResponseEntity<User> createUser(@RequestBody User user) {
        return new ResponseEntity<>(userService.createUser(user), HttpStatus.CREATED);
    }

    @PutMapping("/{id}")
    public ResponseEntity<User> updateUser(@PathVariable Long id, @RequestBody User user) {
        return ResponseEntity.ok(userService.updateUser(id, user));
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
        userService.deleteUser(id);
        return ResponseEntity.noContent().build();
    }
}
```

# Testing RESTful APIs with Postman

1. GET: Retrieve all users

- Method: GET
- URL: http://localhost:8080/api/users
- Response: List of users in JSON format.
  
2. POST: Create a new user

- Method: POST
- URL: http://localhost:8080/api/users
- Body:
```
{
    "name": "Jane Doe",
    "email": "jane.doe@example.com"
}
```
- Response: Created user with ID..
  
3. GET: Retrieve a user by ID

- Method: GET
- URL: http://localhost:8080/api/users/{id}
- Response: User details in JSON format.

4. PUT: Update an existing user

- Method: PUT
- URL: http://localhost:8080/api/users/{id}
- Body:
```
{
    "name": "Jane Doe Updated",
    "email": "jane.updated@example.com"
}
```
- Response: Updated user details.

5. DELETE: Delete a user by ID

- Method: DELETE
- URL: http://localhost:8080/api/users/{id}
- Response: No content.

# Best Practices

- Use Nouns for Endpoints: Use resource names in URLs, not actions.
```
GET /api/users
POST /api/users
```

- Stateless Operations: Each request should be independent and contain all necessary information.

- Versioning: Include versioning in your API endpoint to manage changes.
```
GET /api/v1/users
```

- Error Handling: Return appropriate HTTP status codes and meaningful error messages.
```
{
    "timestamp": "2023-01-01T12:00:00Z",
    "status": 404,
    "error": "Not Found",
    "message": "User not found",
    "path": "/api/users/123"
}
```

# Resources

- [RESTful API Design - Best Practices](https://restfulapi.net/rest-api-design-tutorial-with-example/)
- [Spring Boot REST API Documentation](https://spring.io/guides/tutorials/rest)
- [Postman](https://learning.postman.com/docs/introduction/overview/)

This cheat sheet provides a comprehensive overview of RESTful APIs, covering basic principles, HTTP methods, status codes, designing, and implementing RESTful APIs with Spring Boot, and testing them with Postman. Expand with specific use cases and examples as needed for your projects.

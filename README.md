# Student Management REST API

A RESTful Student Management API developed using **Java 21, Spring Boot, Spring Data JPA, Hibernate, and MySQL**. The application provides complete CRUD operations for managing student records through RESTful API endpoints.

## 📌 Project Overview

This backend application allows users to create, retrieve, update, and delete student information. It demonstrates REST API development, database integration, JPA/Hibernate, HTTP methods, status codes, API testing, environment variables, Maven, and Git/GitHub.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Java 21 | Programming Language |
| Spring Boot | Backend Framework |
| Spring Web | REST API Development |
| Spring Data JPA | Database Operations |
| Hibernate | ORM |
| MySQL | Database |
| Maven | Dependency Management |
| Eclipse | Development IDE |
| cURL | API Testing |
| Git | Version Control |
| GitHub | Source Code Repository |

## ✨ Features

- Create a new student
- Get all students
- Get student by ID
- Update student information
- Delete a student
- MySQL database integration
- Spring Data JPA and Hibernate integration
- RESTful API architecture
- Proper HTTP status codes
- Environment variable for database password
- Git and GitHub version control

## 📂 Project Structure

```text
student-rest-api
│
├── .mvn
│   └── wrapper
│       └── maven-wrapper.properties
│
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com.example.studentapi
│   │   │       ├── controller
│   │   │       │   └── StudentController.java
│   │   │       ├── entity
│   │   │       │   └── Student.java
│   │   │       ├── repository
│   │   │       │   └── StudentRepository.java
│   │   │       └── StudentRestApiApplication.java
│   │   │
│   │   └── resources
│   │       └── application.properties
│   │
│   └── test
│       └── java
│           └── com.example.studentapi
│               └── StudentRestApiApplicationTests.java
│
├── .gitattributes
├── .gitignore
├── HELP.md
├── mvnw
├── mvnw.cmd
└── pom.xml
```

## 🏗️ Application Architecture

```text
Client
   │
   │ HTTP Request
   ▼
StudentController
   │
   ▼
StudentRepository
   │
   ▼
Spring Data JPA
   │
   ▼
Hibernate
   │
   ▼
MySQL Database
```

### Controller

`StudentController` handles HTTP requests and sends HTTP responses.

### Entity

`Student` represents the student data stored in the database.

### Repository

`StudentRepository` extends `JpaRepository` and provides database operations such as `save()`, `findAll()`, `findById()`, `existsById()`, and `deleteById()`.

## 🗄️ Database

**Database Name:**

```text
student_springrest_api
```

Create the database:

```sql
CREATE DATABASE student_springrest_api;
```

### Student Fields

| Field | Type | Description |
|---|---|---|
| id | Long | Primary Key |
| name | String | Student Name |
| email | String | Student Email |
| age | Integer | Student Age |
| course | String | Course Name |

## ⚙️ Configuration

```properties
spring.application.name=student-rest-api

spring.datasource.url=jdbc:mysql://localhost:3306/student_springrest_api
spring.datasource.username=root
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8080
```

The database password is provided through the `DB_PASSWORD` environment variable and is not stored directly in the source code.

## 🔐 Environment Variable

The application uses:

```text
DB_PASSWORD
```

Spring Boot reads it using:

```properties
spring.datasource.password=${DB_PASSWORD}
```

The `.env` file is also excluded through `.gitignore`.

## 🔗 REST API Endpoints

**Base URL:**

```text
http://localhost:8080/api/students
```

| Method | Endpoint | Description | Status |
|---|---|---|---|
| POST | `/api/students` | Create Student | 201 Created |
| GET | `/api/students` | Get All Students | 200 OK |
| GET | `/api/students/{id}` | Get Student By ID | 200 OK / 404 Not Found |
| PUT | `/api/students/{id}` | Update Student | 200 OK / 404 Not Found |
| DELETE | `/api/students/{id}` | Delete Student | 204 No Content / 404 Not Found |

## 1. Create Student

**POST**

```text
http://localhost:8080/api/students
```

Request:

```json
{
  "name": "Gangothri",
  "email": "gangothri@gmail.com",
  "age": 22,
  "course": "Java"
}
```

Response:

```json
{
  "id": 1,
  "name": "Gangothri",
  "email": "gangothri@gmail.com",
  "age": 22,
  "course": "Java"
}
```

**Status:** `201 Created`

## 2. Get All Students

**GET**

```text
http://localhost:8080/api/students
```

Response:

```json
[
  {
    "id": 1,
    "name": "Gangothri",
    "email": "gangothri@gmail.com",
    "age": 22,
    "course": "Java"
  }
]
```

If there are no students:

```json
[]
```

**Status:** `200 OK`

## 3. Get Student By ID

**GET**

```text
http://localhost:8080/api/students/1
```

Response:

```json
{
  "id": 1,
  "name": "Gangothri",
  "email": "gangothri@gmail.com",
  "age": 22,
  "course": "Java"
}
```

**Status:** `200 OK`

If the student does not exist:

**Status:** `404 Not Found`

## 4. Update Student

**PUT**

```text
http://localhost:8080/api/students/1
```

Request:

```json
{
  "name": "Gangothri G",
  "email": "gangothri@gmail.com",
  "age": 23,
  "course": "Spring Boot"
}
```

Response:

```json
{
  "id": 1,
  "name": "Gangothri G",
  "email": "gangothri@gmail.com",
  "age": 23,
  "course": "Spring Boot"
}
```

**Status:** `200 OK`

If the student does not exist:

**Status:** `404 Not Found`

## 5. Delete Student

**DELETE**

```text
http://localhost:8080/api/students/1
```

**Status:** `204 No Content`

If the student does not exist:

**Status:** `404 Not Found`

## 📊 HTTP Status Codes

| Status Code | Meaning |
|---|---|
| 200 OK | Request successful |
| 201 Created | Student successfully created |
| 204 No Content | Student successfully deleted |
| 404 Not Found | Student does not exist |

## 🧪 API Testing

The API was tested using cURL.

### Get All Students

```cmd
curl http://localhost:8080/api/students
```

### Create Student

```cmd
curl -X POST http://localhost:8080/api/students ^
-H "Content-Type: application/json" ^
-d "{\"name\":\"Gangothri\",\"email\":\"gangothri@gmail.com\",\"age\":22,\"course\":\"Java\"}"
```

### Get Student

```cmd
curl http://localhost:8080/api/students/1
```

### Update Student

```cmd
curl -X PUT http://localhost:8080/api/students/1 ^
-H "Content-Type: application/json" ^
-d "{\"name\":\"Gangothri G\",\"email\":\"gangothri@gmail.com\",\"age\":23,\"course\":\"Spring Boot\"}"
```

### Delete Student

```cmd
curl -X DELETE http://localhost:8080/api/students/1
```

### Verify Deleted Student

```cmd
curl http://localhost:8080/api/students/1
```

Expected result:

```text
404 Not Found
```

## ▶️ How to Run

1. Start MySQL Server.
2. Create the `student_springrest_api` database.
3. Configure the `DB_PASSWORD` environment variable.
4. Open the project in Eclipse.
5. Run `StudentRestApiApplication.java`.
6. The application starts on port `8080`.
7. Test the API at:

```text
http://localhost:8080/api/students
```

## 📦 Maven

The project uses Maven for dependency management.

Main configuration file:

```text
pom.xml
```

Maven Wrapper:

```text
mvnw
mvnw.cmd
```

## 🔧 Git & GitHub

Git was used for version control and GitHub was used to host the source code.

```bash
git init
git add .
git commit -m "Initial commit - Student REST API"
git branch -M main
git remote add origin https://github.com/GudaGangothri/student-rest-api.git
git push -u origin main
```

## 🎯 Key Concepts Demonstrated

- Java
- Spring Boot
- REST API
- CRUD Operations
- HTTP Methods
- HTTP Status Codes
- Dependency Injection
- `@RestController`
- `@RequestMapping`
- `@GetMapping`
- `@PostMapping`
- `@PutMapping`
- `@DeleteMapping`
- `@RequestBody`
- `@PathVariable`
- `ResponseEntity`
- Spring Data JPA
- `JpaRepository`
- Hibernate
- ORM
- MySQL
- Maven
- Environment Variables
- `.gitignore`
- Git
- GitHub
- API Testing

## 📚 Learning Outcomes

Developed practical experience in building RESTful backend applications using Spring Boot, implementing CRUD operations, connecting Java applications with MySQL using JPA/Hibernate, handling HTTP requests and responses, testing REST APIs using cURL, managing dependencies with Maven, protecting database credentials using environment variables, and managing source code with Git and GitHub.

## 👩‍💻 Author

**Gangothri Guda**

B.Tech – Electronics and Communication Engineering

**Skills:** Java | Spring Boot | SQL | REST API | MySQL | Git | GitHub

**GitHub:**  
https://github.com/GudaGangothri

**Project Repository:**  
https://github.com/GudaGangothri/student-rest-api
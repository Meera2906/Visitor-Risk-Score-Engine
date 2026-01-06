# 🛡️ Visitor Risk Scoring Engine

A **Spring Boot–based backend system** that evaluates visitor risk using configurable rules, secure authentication, and role-based authorization.

---

## 📌 Overview

The **Visitor Risk Scoring Engine** is designed to help organizations **assess and manage visitor risk** in a structured and automated way.

Instead of relying on manual judgment, the system uses **admin-defined risk rules** and **visitor activity logs** to calculate a cumulative risk score. Access to features is controlled using **JWT authentication and role-based authorization**.

---

## 🎯 Key Features

* 🔐 **JWT-based Authentication & Authorization**
* 👥 **Role-Based Access Control**

  * **ADMIN**: Create and manage risk rules
  * **STAFF**: Add visitors and record visit logs
* 📊 **Rule-driven Risk Scoring Engine**
* 🧩 **Clean Layered Architecture**
* 🛠️ **RESTful APIs**
* 🗄️ **Database-backed persistence using JPA**

---

## 🧑‍💻 Tech Stack

* **Java 17**
* **Spring Boot**
* **Spring Security**
* **JWT (JSON Web Tokens)**
* **Spring Data JPA**
* **Hibernate**
* **H2 / MySQL** (configurable)
* **Maven**
* **Swagger / OpenAPI**

---

## 🏗️ Architecture

The project follows a **layered architecture**:

```
Controller  →  Service  →  Repository  →  Database
                  ↓
              Security (JWT, Roles)
```

### Layers:

* **Controller Layer** – Handles HTTP requests
* **Service Layer** – Business logic & validations
* **Repository Layer** – Database operations
* **Security Layer** – JWT validation & authorization

---

## 🔐 Security Design

* Users authenticate via login to receive a **JWT token**
* Token contains:

  * User email
  * User ID
  * Roles (ADMIN / STAFF)
* A custom **JWT Authentication Filter** validates the token for each request
* Access is restricted using **@PreAuthorize** annotations

Example:

```java
@PreAuthorize("hasRole('ADMIN')")
@PostMapping("/risk-rules")
public RiskRule createRule(...) { }
```

---

## 👤 Roles & Permissions

| Role  | Permissions                         |
| ----- | ----------------------------------- |
| ADMIN | Create, update, delete risk rules   |
| STAFF | Add visitor profiles and visit logs |
| BOTH  | View permitted resources            |

---

## 📂 Main Modules

* **Authentication**

  * Login & token generation
* **Visitor Management**

  * Create visitor profiles
  * Record visit logs
* **Risk Rule Management**

  * Define thresholds and score impact
* **Risk Evaluation**

  * Calculate total risk score per visitor

---

## ▶️ Running the Project

### 1️⃣ Clone the repository

```bash
git clone https://github.com/your-username/visitor-risk-scoring-engine.git
cd visitor-risk-scoring-engine
```

### 2️⃣ Configure application properties

Update `application.properties`:

```properties
jwt.secret=your_secret_key
jwt.expiration=86400000
```

### 3️⃣ Run the application

```bash
mvn spring-boot:run
```

The application will start on:

```
http://localhost:8080
```

---

## 🧪 Running Tests

```bash
mvn test
```

---

## 📖 API Documentation

Swagger UI is available at:

```
http://localhost:8080/swagger-ui.html
```

---

## 🚀 Future Enhancements

* Real-time alerts for high-risk visitors
* Analytics dashboard
* Integration with external access-control systems
* Role-based audit logging

---

## 📚 Learning Outcomes

This project demonstrates:

* Secure API design using JWT
* Role-based authorization with Spring Security
* Clean architecture principles
* Real-world backend problem solving

---

## 👩‍💻 Author

**Meera Fareena S**
Aspiring Software Engineer | Backend Developer
📍 Java • Spring Boot • Security • REST APIs

---

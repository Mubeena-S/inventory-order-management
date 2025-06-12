# 🛒 Inventory and Order Management System

This is a secure Java Spring Boot-based microservice that manages inventory and customer orders with role-based access using JWT authentication.

---

## 🔧 Technologies Used
- Java 17
- Spring Boot 3
- Spring Web
- Spring Security
- Spring Data JPA
- H2 Database (in-memory)
- JWT (JSON Web Token) for Authentication
- Lombok (for boilerplate reduction)
- Maven

---

## 🧑‍💻 Roles
- **ADMIN**
  - Add, update, delete inventory items
  - View all orders
- **CUSTOMER**
  - View items
  - Place orders
  - View their own orders

---

## 📦 Entities
- **User**: `username`, `password`, `role`
- **Item**: `id`, `name`, `quantity`, `price`
- **Order**: `id`, `user_id`, `items`, `total_price`, `timestamp`
- **OrderItem**: `item_id`, `quantity`

---

## 🚀 How to Run

### 🧩 Prerequisites
- Java 17+
- Maven

### ▶️ Run the app
```bash
mvn spring-boot:run

The application will start at:
http://localhost:8080

💾 H2 Database Console
URL: http://localhost:8080/h2-console

JDBC URL: jdbc:h2:mem:testdb

Username: sa

Password: (leave blank)

## 🔐 Authentication

### ✅ Register
`POST /api/auth/register`

```json
{
  "username": "mubeena",
  "password": "pass123",
  "role": "CUSTOMER"
}

### ✅ Login
**Endpoint:** `POST /api/auth/login`

**Request Body:**
```json
{
  "username": "mubeena",
  "password": "pass123"
}
Response:
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
Use this token in the Authorization header for all protected APIs.

Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
## 📮 Sample API Endpoints

### 🛍️ Items (Product/Inventory)

| Method | Endpoint            | Description       | Access Role |
|--------|---------------------|-------------------|-------------|
| GET    | `/api/items`        | View all items    | PUBLIC      |
| POST   | `/api/items`        | Add item          | ADMIN       |
| PUT    | `/api/items/{id}`   | Update item       | ADMIN       |
| DELETE | `/api/items/{id}`   | Delete item       | ADMIN       |

---

### 📦 Orders

| Method | Endpoint             | Description         | Access Role |
|--------|----------------------|---------------------|-------------|
| POST   | `/api/orders`        | Place new order     | CUSTOMER    |
| GET    | `/api/orders/my`     | View my orders      | CUSTOMER    |
| GET    | `/api/orders`        | View all orders     | ADMIN       |

---

### 🔐 Authentication

| Method | Endpoint             | Description       |
|--------|----------------------|-------------------|
| POST   | `/api/auth/register` | Register new user |
| POST   | `/api/auth/login`    | Login and get JWT |

## 📁 Project Structure

src/
├── main/
│ ├── java/
│ │ └── com/
│ │ └── mubeena/
│ │ └── inventory/
│ │ ├── controller/ # REST Controllers
│ │ ├── dto/ # DTOs for request/response
│ │ ├── entity/ # JPA Entities
│ │ ├── repository/ # Spring Data JPA Repositories
│ │ ├── security/ # JWT Security Configuration
│ │ └── service/ # Service Layer
│ └── resources/
│ ├── application.properties # App config (DB, JWT secret, etc.)
│ └── data.sql # Sample data (if any)
├── test/ # Test cases (optional)
└── pom.xml # Maven dependencies

## 🛠️ Future Improvements

- ✅ **Swagger UI** with JWT authentication support (for easy API testing)
- ✅ **Docker containerization** (to make it portable and platform-independent)
- ✅ **Integration & Unit Tests** for critical business logic and controller endpoints
- ✅ **PostgreSQL or MySQL support** instead of H2 for production-level database

---

## 📬 Contact

**Mubeena Savalagi**  
📧 [savalagimubeena@gmail.com](mailto:savalagimubeena@gmail.com)  
📞 6364115106  
🌐 [LinkedIn Profile](https://www.linkedin.com/in/mubeena-savalagi-0490a91b7)

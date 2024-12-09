## **Go Lang JWT Authentication using Gin and GORM**

### **Overview**
This project demonstrates a **JWT-based authentication system** built with the **Gin web framework** and **GORM** for database interaction. The application supports user registration, login, and protected routes accessible only with a valid JWT token.

---

### **Features**
- **User Registration**: Register new users with secure password hashing.
- **Login**: Authenticate users and issue a JWT token.
- **Protected Routes**: Access restricted to authorized users with valid tokens.
- **Token Validation**: Verify JWT tokens for secure route access.

---

### **Project Structure**
```plaintext
├── main.go           # Entry point of the application
├── models/           # Contains database models
│   └── user.go       # User model definition
├── controllers/      # Handles business logic
│   ├── auth.go       # Authentication logic
│   └── protected.go  # Logic for protected routes
├── middlewares/      # Contains middleware for authentication
│   └── auth.go       # JWT authentication middleware
├── routes/           # Contains route definitions
│   └── routes.go     # API routes
├── utils/            # Utility functions
│   └── jwt.go        # JWT generation and validation
└── go.mod            # Go module dependencies
```

---

### **Technologies Used**
- **Gin**: A fast, lightweight web framework for building APIs.  
- **GORM**: An ORM library for database interaction.  
- **JWT**: For secure token-based authentication.  
- **bcrypt**: For secure password hashing.  
- **SQLite/MySQL/PostgreSQL**: Database options (configured in GORM).

---

### **Installation Instructions**
1. **Clone the repository**:  
   ```bash
   git clone https://github.com/your-repo/go-jwt-auth.git
   cd go-jwt-auth
   ```

2. **Install dependencies**:  
   ```bash
   go mod tidy
   ```

3. **Configure environment variables**:  
   Create a `.env` file with the following:  
   ```plaintext
   DB_USER=your_db_user
   DB_PASS=your_db_password
   DB_NAME=your_db_name
   DB_HOST=localhost
   DB_PORT=3306
   JWT_SECRET=your_secret_key
   ```

4. **Run the application**:  
   ```bash
   go run main.go
   ```

---

### **Endpoints**
#### **1. User Registration**
- **Endpoint**: `/register`  
- **Method**: POST  
- **Request Body**:  
   ```json
   {
     "username": "example",
     "email": "example@example.com",
     "password": "securepassword"
   }
   ```
- **Response**:  
   ```json
   {
     "message": "User registered successfully"
   }
   ```

#### **2. User Login**
- **Endpoint**: `/login`  
- **Method**: POST  
- **Request Body**:  
   ```json
   {
     "email": "example@example.com",
     "password": "securepassword"
   }
   ```
- **Response**:  
   ```json
   {
     "token": "your_jwt_token"
   }
   ```

#### **3. Protected Route**
- **Endpoint**: `/protected`  
- **Method**: GET  
- **Headers**:  
   ```
   Authorization: Bearer <your_jwt_token>
   ```
- **Response**:  
   ```json
   {
     "message": "Access granted to protected route"
   }
   ```

---

### **Key Functions**
1. **JWT Generation and Validation**  
   - Generate a token during login.  
   - Middleware checks the validity of tokens for protected routes.  

2. **Password Hashing**  
   - Passwords are hashed using `bcrypt` before storing in the database.  

3. **GORM Models**  
   - User model with fields for `ID`, `Username`, `Email`, and `Password`.

---

### **Example Use Cases**
- Implementing user authentication in web applications.  
- Protecting sensitive APIs from unauthorized access.  
- Building scalable microservices with secure authentication.  

---

### **Future Enhancements**
- Add role-based access control (RBAC).  
- Implement token expiration and refresh mechanisms.  
- Add email verification for user registration.  

---

This repository provides a robust starting point for building secure APIs with JWT authentication using Go, Gin, and GORM.

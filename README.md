<big>JWT Authentication</big>

This project implements JWT-based authentication with Role-Based Access Control (RBAC) for securing API endpoints.

API Endpoints

Authentication

[POST] /auth/signup → Register a new user

[POST] /auth/login → Authenticate a user

User Management

[GET] /users/me → Retrieve the current authenticated user

[GET] /users → Retrieve the list of all users (Admin and Super Admin only)

[POST] /admins → Create an administrator (Super Admin only)

JWT Authentication Process

A JWT authentication filter extracts and validates the token from the request header.

Some API routes are whitelisted, while protected routes require a valid JWT.

The authentication process generates a JWT with an expiration time.

The generated JWT is used to access protected routes.

Authentication exceptions are caught and a customized response is sent to the client.

Role-Based Access Control (RBAC)

The system has three roles with different levels of access:

User: Can access their own information.

Administrator: Can do everything a User can and access the list of users.

Super Administrator: Can do everything an Admin can and create admin users.

Protected Routes

Route

Roles Allowed

Description

[GET] /users/me

User, Admin, Super Admin

Retrieve the authenticated user.

[GET] /users

Admin, Super Admin

Retrieve the list of all users.

[POST] /admins

Super Admin

Create an administrator.

Usage

Register a user via /auth/signup.

Authenticate using /auth/login to receive a JWT.

Use the received JWT as a Bearer token in the Authorization header to access protected routes.

Installation

Clone the repository:

git clone <repository-url>

Install dependencies:

npm install  # or mvn install (if using Java)

Run the application:

npm start  # or mvn spring-boot:run (for Spring Boot)

Security Considerations

Always store JWTs securely (e.g., HTTP-only cookies for web apps).

Ensure tokens have a reasonable expiration time and use refresh tokens where applicable.

Implement proper error handling to prevent exposure of sensitive information.

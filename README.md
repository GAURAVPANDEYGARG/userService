# userService

This project implements **JWT-based authentication** with **Role-Based Access Control (RBAC)** for securing API endpoints.

## API Endpoints

### Authentication

[POST] /auth/signup → Register a new user  
[POST] /auth/login → Authenticate a user  

### User Management

[GET] /users/me → Retrieve the current authenticated user  
[GET] /users → Retrieve the list of all users (Admin and Super Admin only)  
[POST] /admins → Create an administrator (Super Admin only)  

## JWT Authentication Process

1. A JWT authentication filter extracts and validates the token from the request header.
2. Some API routes are whitelisted, while protected routes require a valid JWT.
3. The authentication process generates a JWT with an expiration time.
4. The generated JWT is used to access protected routes.
5. Authentication exceptions are caught and a customized response is sent to the client.

## Role-Based Access Control (RBAC)

### The system has three roles with different levels of access:

1. **User**: Can access their own information.
2. **Administrator**: Can do everything a User can and access the list of users.
3. **Super Administrator**: Can do everything an Admin can and create admin users.

## Protected Routes

| **Route** | **Roles Allowed** | **Description** |
|---|---|---|
| **[GET] /users/me** | **User, Admin, Super Admin** | Retrieve the authenticated user. |
| **[GET] /users** | **Admin, Super Admin** | Retrieve the list of all users. |
| **[POST] /admins** | **Super Admin** | Create an administrator. |

## Usage

1. Register a user via `/auth/signup`.
2. Authenticate using `/auth/login` to receive a JWT.
3. Use the received JWT as a Bearer token in the Authorization header to access protected routes.

## Installation

1. Clone the repository:
   ```sh
   git clone <repository-url>


## Install dependencies:

    mvn clean install

## Run the application:
```sh
mvn spring-boot:run 


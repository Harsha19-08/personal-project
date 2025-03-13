# User Registration Endpoint

## Method and Endpoint
**Method:** POST  
**Endpoint:** `/users/register`

## Description
This endpoint is used to register a new user. It requires the user's first name, last name, email, and password.

## Request Body
The request body should be a JSON object with the following structure:
```json
{
  "fullname": {
    "firstname": "string",
    "lastname": "string"
  },
  "email": "string",
  "password": "string"
}
```

### Fields
- `fullname.firstname` (string, required): The first name of the user. Must be at least 3 characters long.
- `fullname.lastname` (string, optional): The last name of the user. Must be at least 3 characters long.
- `email` (string, required): The email address of the user. Must be a valid email format.
- `password` (string, required): The password for the user account. Must be at least 6 characters long.

## Responses

### Success
- **Status Code:** 201 Created
- **Response Body:**
  ```json
  {
    "token": "string",
    "user": {
      "_id": "string",
      "fullname": {
        "firstname": "string",
        "lastname": "string"
      },
      "email": "string"
    }
  }
  ```

### Error
- **Status Code:** 400 Bad Request
- **Response Body:**
  ```json
  {
    "errors": [
      {
        "msg": "string",
        "param": "string",
        "location": "string"
      }
    ]
  }
  ```

## Example Request
```bash
curl -X POST http://localhost:3000/users/register \
  -H "Content-Type: application/json" \
  -d '{
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john.doe@example.com",
    "password": "password123"
  }'
```

## Example Response
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "_id": "60d0fe4f5311236168a109ca",
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john.doe@example.com"
  }
}
```

### Response Fields for the user registration
- `token` (string): JWT token for authentication.
- `user` (object):
  - `fullname` (object):
    - `firstname` (string): User's first name (minimum 3 characters).
    - `lastname` (string): User's last name (minimum 3 characters).
  - `email` (string): User's email address (must be a valid email).
  - `_id` (string): User's unique identifier.

# User Login Endpoint

## Method and Endpoint
**Method:** POST  
**Endpoint:** `/users/login`

## Description
This endpoint is used to log in an existing user. It requires the user's email and password.

## Request Body
The request body should be a JSON object with the following structure:
```json
{
  "email": "string",
  "password": "string"
}
```

### Fields
- `email` (string, required): The email address of the user. Must be a valid email format.
- `password` (string, required): The password for the user account. Must be at least 6 characters long.

## Responses

### Success
- **Status Code:** 200 OK
- **Response Body:**
  ```json
  {
    "token": "string",
    "user": {
      "_id": "string",
      "fullname": {
        "firstname": "string",
        "lastname": "string"
      },
      "email": "string"
    }
  }
  ```

### Error
- **Status Code:** 400 Bad Request
- **Response Body:**
  ```json
  {
    "errors": [
      {
        "msg": "string",
        "param": "string",
        "location": "string"
      }
    ]
  }
  ```
- **Status Code:** 401 Unauthorized
- **Response Body:**
  ```json
  {
    "message": "Invalid email or password"
  }
  ```

## Example Request
```bash
curl -X POST http://localhost:3000/users/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john.doe@example.com",
    "password": "password123"
  }'
```

## Example Response
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "_id": "60d0fe4f5311236168a109ca",
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john.doe@example.com"
  }
}
```

### Response Fields for the user login
- `token` (string): JWT token for authentication.
- `user` (object):
  - `fullname` (object):
    - `firstname` (string): User's first name (minimum 3 characters).
    - `lastname` (string): User's last name (minimum 3 characters).
  - `email` (string): User's email address (must be a valid email).
  - `_id` (string): User's unique identifier.
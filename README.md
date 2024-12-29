# User Registration Endpoint Documentation

## Endpoint: `/user/register`

### Method: POST

### Description:
This endpoint is used to register a new user. It requires the user's first name, last name, email, and password.

### Request Body:
The request body should be a JSON object containing the following fields:
- `fullname`: An object containing:
  - `firstname`: The user's first name (minimum 3 characters).
  - `lastname`: The user's last name (optional, minimum 3 characters if provided).
- `email`: The user's email address (must be a valid email).
- `password`: The user's password (minimum 6 characters).

Example:
```json
{
  "fullname": {
    "firstname": "John",
    "lastname": "Doe"
  },
  "email": "john.doe@example.com",
  "password": "password123"
}
```

### Responses:

#### Success:
- **Status Code:** 201 Created
- **Response Body:**
  ```json
  {
    "token": "jwt-token",
    "user": {
      "_id": "user-id",
      "fullname": {
        "firstname": "John",
        "lastname": "Doe"
      },
      "email": "john.doe@example.com"
    }
  }
  ```

Example:
```json
{
    ```json
    {
      "errors": [
        {
          "msg": "Invalid Email",
          "param": "email",
          "location": "body"
        },
        {
          "msg": "First name must be at least 3 characters long",
          "param": "fullname.firstname",
          "location": "body"
        },
        {
          "msg": "Password must be at least 6 characters long",
          "param": "password",
          "location": "body"
        }
      ]
    }
    ```
  - **Response Body:** (User already exists)
    ```json
    {
      "message": "User already exist"
    }
    ```

- **Status Code:** 500 Internal Server Error
  - **Response Body:**
    ```json
    {
      "message": "Internal server error"
    }
    ```

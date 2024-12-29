---
layout: page
title: Authentication | API Documentation
---

<style>
    .image-container {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .transparent-image {
        width: 20%;
        background: none;
    }
</style>

<div class="image-container">
    <img src="/img/Logo.png" alt="RedLabs Logo" class="transparent-image" />
</div>

## Authentication APIs

This documentation outlines the APIs related to **user authentication**, specifically for **signing up** and **logging in** to the platform.

<br />

## SIGNUP API

### **Endpoint**

`/auth/signup`

### **Method**

`POST`

### **Description**

This API handles user registration for the platform. It allows users to sign up with roles restricted to either `student` or `teacher`. Upon successful signup, a JSON Web Token (JWT) is returned for authentication.

<br />

## **Request**

### **Headers**

No authentication required.

### **Body Parameters**

The request body must be a JSON object with the following fields:

| Parameter         | Type     | Required | Description                                |
| ----------------- | -------- | -------- | ------------------------------------------ |
| `firstName`       | `string` | Yes      | The user's first name.                     |
| `lastName`        | `string` | Yes      | The user's last name.                      |
| `email`           | `string` | Yes      | The user's unique email address.           |
| `password`        | `string` | Yes      | The user's password.                       |
| `confirmPassword` | `string` | Yes      | Must match the `password` field.           |
| `role`            | `string` | Yes      | Role of the user (`student` or `teacher`). |

<br />

## **Response**

### **Success Response**

**Status Code:** `201 Created`  
**Format:** `application/json`

**Example:**

```json
{
  "status": "success",
  "key": "{authentication token}",
  "data": {
    "user": {
      "firstName": "firstName",
      "lastName": "lastName",
      "email": "email"
    }
  }
}
```

<br />

### **Error Responses**

| **Status Code**   | **Description**                                                                                  |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| `400 Bad Request` | Malformed request if required parameters are missing or invalid request parameters are provided. |
| `409 Conflict`    | User already exists if a duplicate email is detected.                                            |

**Examples:**

- **400 Bad Request** (Missing parameters or invalid role):

```json
{
  "status": "fail",
  "message": "Malformed request."
}
```

- **409 Conflict** (Duplicate email):

```json
{
  "status": "fail",
  "message": "User with specified email address already exists."
}
```

<br />

## **Use Cases**

1. **Successful Registration**:  
   User provides valid input with a unique email and valid role (`student` or `teacher`). A JWT is returned in the response.

2. **Duplicate Email**:  
   If the email is already registered, a `409 Conflict` error is returned.

3. **Invalid Role**:  
   If a role other than `student` or `teacher` is provided, a `400 Bad Request` error is returned.

4. **Missing Parameters**:  
   If any required parameter is missing or invalid, a `400 Bad Request` error is returned.

<br />

## **Notes**

- Ensure `password` and `confirmPassword` match to avoid validation errors.

<br />
<br />

## **Login API**

### **Endpoint**

`/auth/login`

### **Method**

`POST`

### **Description**

The login API allows users to authenticate with their credentials (email and password) and obtain a JWT token. This token is used to authenticate further API requests that require authorization.

<br />

### **Request**

#### **Headers**

No authentication is required for this endpoint.

#### **Body Parameters**

The request body must be a JSON object with the following fields:

| Parameter  | Type     | Required | Description               |
| ---------- | -------- | -------- | ------------------------- |
| `email`    | `string` | Yes      | The user's email address. |
| `password` | `string` | Yes      | The user's password.      |

<br />

### **Response**

#### **Success Response**

**Status Code:** `200 OK`  
**Format:** `application/json`

**Example:**

```json
{
  "status": "success",
  "key": "{authentication token}",
  "data": {
    "user": {
      "firstName": "firstName",
      "lastName": "LastName",
      "email": "email"
    }
  }
}
```

| **Status Code**             | **Description**                           |
| --------------------------- | ----------------------------------------- |
| `400 Bad Request`           | Missing `email` or `password` parameters. |
| `401 Unauthorized`          | Invalid email or password.                |
| `500 Internal Server Error` | A server error occurred.                  |

**Examples:**

- **400 Bad Request** (Missing parameters):

```json
{
  "status": "fail",
  "message": "Missing email or password."
}
```

- **401 Unauthorized** (Incorrect email or password):

```json
{
  "status": "fail",
  "message": "Incorrect email or password."
}
```

<br />

## **Use Cases**

1. **Successful Login**:  
   When a user provides a valid email and password, a JWT token is returned in the response.

2. **Invalid Credentials**:  
   If the email or password is incorrect, a `401 Unauthorized` error is returned.

3. **Missing Parameters**:  
   If any required parameter (email or password) is missing, a `400 Bad Request` error is returned.

<br />

## **Notes**

- Ensure that the provided `email` and `password` are correct to receive a valid JWT token.

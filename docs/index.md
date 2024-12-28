---
layout: page
title: API Documentation
---

![RedLabs Logo](../img/Logo.svg)

## SIGNUP API

### **Endpoint**

`{{URL}}/auth/signup`

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
  "key": `authenctication token`,
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

---

## **Use Cases**

1. **Successful Registration**:  
   User provides valid input with a unique email and valid role (`student` or `teacher`). A JWT is returned in the response.

2. **Duplicate Email**:  
   If the email is already registered, a `409 Conflict` error is returned.

3. **Invalid Role**:  
   If a role other than `student` or `teacher` is provided, a `400 Bad Request` error is returned.

4. **Missing Parameters**:  
   If any required parameter is missing or invalid, a `400 Bad Request` error is returned.

---

## **Notes**

- Ensure `password` and `confirmPassword` match to avoid validation errors.

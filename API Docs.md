---
title: API documentation sample
*TOC
{:toc}
---

# User Management API

## Overview
The User Management API provides endpoints to create, retrieve, update, and delete user accounts.
It follows RESTful principles and uses standard HTTP methods and status codes.

This API is designed for integration with web and mobile applications that require centralized user management.

**Base URL**
```text
https://api.example.com/v1
```

---

## Authentication
All endpoints require **Bearer Token Authentication**.

Include the access token in the request header.

```http
Authorization: Bearer <access_token>
```

If authentication fails, the API returns `401 Unauthorized`.

---

## Create User

Creates a new user in the system.

### Endpoint
```http
POST /users
```

### Request Body
```json
{
  "firstName": "Amit",
  "lastName": "Kumar",
  "email": "amit.kumar@example.com",
  "role": "admin"
}
```

### Request Fields
| Field | Type | Required | Description |
|------|------|----------|-------------|
| firstName | string | Yes | User's first name |
| lastName | string | Yes | User's last name |
| email | string | Yes | Unique email address |
| role | string | No | User role (admin, editor, viewer) |

### Response — 201 Created
```json
{
  "id": "user_12345",
  "firstName": "Amit",
  "lastName": "Kumar",
  "email": "amit.kumar@example.com",
  "role": "admin",
  "createdAt": "2026-04-27T10:15:30Z"
}
```

### Error Responses
| Status Code | Description |
|------------|-------------|
| 400 | Invalid request payload |
| 409 | User already exists |

---

## Get User by ID

Retrieves details of a specific user.

### Endpoint
```http
GET /users/{userId}
```

### Path Parameter
| Parameter | Description |
|----------|-------------|
| userId | Unique identifier for the user |

### Response — 200 OK
```json
{
  "id": "user_12345",
  "firstName": "Amit",
  "lastName": "Kumar",
  "email": "amit.kumar@example.com",
  "role": "admin"
}
```

### Error Responses
| Status Code | Description |
|------------|-------------|
| 404 | User not found |

---

## Update User

Updates attributes of an existing user.

### Endpoint
```http
PUT /users/{userId}
```

### Request Body
```json
{
  "role": "editor"
}
```

### Response — 200 OK
```json
{
  "id": "user_12345",
  "role": "editor",
  "updatedAt": "2026-04-27T11:20:10Z"
}
```

---

## Delete User

Deletes a user permanently.

### Endpoint
```http
DELETE /users/{userId}
```

### Response — 204 No Content
No response body is returned.

---

## HTTP Status Codes

| Status Code | Meaning |
|------------|---------|
| 200 | Success |
| 201 | Resource created |
| 204 | No content |
| 400 | Bad request |
| 401 | Unauthorized |
| 404 | Not found |
| 409 | Conflict |
| 500 | Internal server error |

---

## Best Practices
- Validate request payloads before sending
- Handle API errors gracefully
- Store access tokens securely
- Avoid hardcoding credentials in applications

---

## Changelog

| Version | Date | Description |
|--------|------|-------------|
| 1.0 | 2026-04-27 | Initial sample API documentation |

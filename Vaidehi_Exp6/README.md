# Experiment 6 — Role-Based Authorization (RBAC) with Spring Boot

**Student Name:** Vaidehi Sharma  
**Course:** FullStack Development 2026  

---

## Project Overview

This project implements **Role-Based Access Control (RBAC)** using **Spring Boot** and **Spring Security** with **JWT (JSON Web Token)** authentication.

The application supports two roles:
- `ADMIN` — full access including admin-only endpoints
- `USER` — restricted access to user-level endpoints only

---

## Authentication & Authorization Flow

1. User sends `POST /login` with username and password
2. Server validates credentials and returns a **JWT token** containing the user's **role**
3. Client sends the token in `Authorization: Bearer <token>` header
4. `JwtFilter` intercepts every request, validates the token, and sets Spring Security context with the correct role
5. Spring Security's `SecurityFilterChain` enforces role-based rules on each endpoint
6. Unauthorized requests get `401 Unauthorized`; forbidden role access gets `403 Forbidden`

---

## Tech Stack

| Technology | Version |
|---|---|
| Java | 17 |
| Spring Boot | 3.2.3 |
| Spring Security | 6.2.2 |
| JWT (jjwt) | 0.11.5 |
| Maven | 3.9.x |

---

## Project Structure

```
src/main/java/com/example/jwt_demo/
├── controllers/
│   ├── AuthController.java       ← Login, Logout, /protected endpoints
│   ├── AdminController.java      ← ADMIN-only endpoints (/admin/**)
│   └── UserController.java       ← USER-accessible endpoints (/user/**)
├── security/
│   ├── JwtUtil.java              ← Token generation with role claim & validation
│   ├── JwtFilter.java            ← Intercepts requests, extracts role, sets auth context
│   ├── SecurityConfig.java       ← Role-based URL access rules
│   └── TokenBlacklist.java       ← In-memory token invalidation (logout)
├── HomeController.java
└── JwtDemoApplication.java
src/main/resources/
└── application.properties
screenshots/
├── 1_login_admin_success.png     ← Admin login → 200 OK + JWT token
├── 2_admin_dashboard_success.png ← Admin accessing /admin/dashboard → 200 OK
├── 3_login_user_success.png      ← User (vaidehi) login → 200 OK + JWT token
├── 4_user_profile_success.png    ← User accessing /user/profile → 200 OK
├── 5_user_denied_admin.png       ← User trying /admin/** → 403 Forbidden
├── 6_no_token_401.png            ← Request without token → 401 Unauthorized
└── 7_invalid_login.png           ← Wrong password → 401 Unauthorized
```

---

## How to Run

```bash
mvn spring-boot:run
```

Server starts at: `http://localhost:8083`

---

## User Credentials

| Username | Password | Role |
|---|---|---|
| `admin` | `admin123` | `ADMIN` |
| `vaidehi` | `user123` | `USER` |

---

## API Endpoints & Access Rules

| Method | Endpoint | Required Role | Description |
|---|---|---|---|
| POST | `/login` | None | Login and receive JWT token |
| POST | `/logout` | Any (with token) | Invalidate token |
| GET | `/protected` | Any authenticated | General protected route |
| GET | `/admin/dashboard` | **ADMIN only** | Admin dashboard |
| GET | `/admin/users` | **ADMIN only** | List all users |
| GET | `/user/profile` | USER or ADMIN | User profile |
| GET | `/user/dashboard` | USER or ADMIN | User dashboard |

---

## Postman Testing Guide

### Step 1 — Login as Admin
```
POST http://localhost:8083/login
Content-Type: application/json

{
  "username": "admin",
  "password": "admin123"
}
```
Response: `200 OK` with JWT token and role `ADMIN`

### Step 2 — Admin accesses Admin Dashboard
```
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <admin_token>
```
Response: `200 OK`

### Step 3 — Login as User
```
POST http://localhost:8083/login
Content-Type: application/json

{
  "username": "vaidehi",
  "password": "user123"
}
```
Response: `200 OK` with JWT token and role `USER`

### Step 4 — User accesses User Profile (allowed)
```
GET http://localhost:8083/user/profile
Authorization: Bearer <user_token>
```
Response: `200 OK`

### Step 5 — User tries Admin Dashboard (forbidden)
```
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <user_token>
```
Response: `403 Forbidden`

### Step 6 — No token sent
```
GET http://localhost:8083/admin/dashboard
(No Authorization header)
```
Response: `401 Unauthorized`

---

## Screenshots

| # | File | Description |
|---|---|---|
| 1 | `1_login_admin_success.png` | Admin login → 200 OK with token |
| 2 | `2_admin_dashboard_success.png` | ADMIN accessing `/admin/dashboard` → 200 OK |
| 3 | `3_login_user_success.png` | User login → 200 OK with token |
| 4 | `4_user_profile_success.png` | USER accessing `/user/profile` → 200 OK |
| 5 | `5_user_denied_admin.png` | USER denied access to `/admin/dashboard` → 403 Forbidden |
| 6 | `6_no_token_401.png` | Missing token → 401 Unauthorized |
| 7 | `7_invalid_login.png` | Wrong credentials → 401 Unauthorized |

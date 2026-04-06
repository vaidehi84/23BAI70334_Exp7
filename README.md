# 🔐 Experiment 7 — Role-Based Authorization (RBAC)
### Secure. Stateless. Role-Aware.

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-0.11.5-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6.2.2-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9.x-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)

👩‍💻 **Vaidehi Sharma** | **Roll No:** 23BAI70334 | FullStack Development 2026

---

## 📌 What is this?

A secure REST API backend implementing **Role-Based Access Control (RBAC)** using **Spring Boot + Spring Security + JWT**. Users log in with a role, receive a signed token, and can only access endpoints permitted for their role.

---

## ✨ Features

- 👑 ADMIN role — full access including admin-only endpoints
- 👤 USER role — restricted to user-level endpoints only
- 🔑 Login with username and password → receive signed JWT with role
- 🛡️ Protected routes enforced by Spring Security role rules
- 🚪 Logout with token blacklisting in-memory
- ⚡ Stateless — zero server-side sessions
- 🔒 Custom JWT filter chain with 401 and 403 responses

---

## ⚙️ Tech Stack

| Technology | Version | Role |
|---|---|---|
| ☕ Java | 17 | Core language |
| 🍃 Spring Boot | 3.2.3 | Backend framework |
| 🔒 Spring Security | 6.2.2 | Security and authorization layer |
| 🔑 JWT jjwt | 0.11.5 | Token generation and validation |
| 🔧 Maven | 3.9.x | Build tool |

---

## 👥 Users & Credentials

| Username | Password | Role | Access |
|:---:|:---:|:---:|:---|
| `admin` | `admin123` | 👑 ADMIN | All endpoints |
| `vaidehi` | `user123` | 👤 USER | /user/** only |

---

## 📡 API Reference

| Method | Endpoint | Auth | Description |
|:---:|:---|:---:|:---|
| POST | /login | None | Authenticate and receive JWT |
| POST | /logout | Bearer | Blacklist and invalidate token |
| GET | /admin/dashboard | 👑 ADMIN | Admin dashboard |
| GET | /admin/users | 👑 ADMIN | List all users |
| GET | /user/profile | 👤 USER or ADMIN | User profile |
| GET | /user/dashboard | 👤 USER or ADMIN | User dashboard |

---

## 🚀 Getting Started

    git clone https://github.com/vaidehi84/23BAI70334_Exp7.git
    cd 23BAI70334_Exp7/Vaidehi_Exp6
    mvn spring-boot:run

🌐 Server starts at http://localhost:8083

---

## 📸 Screenshots

### 1️⃣ Admin Login — 200 OK
![Admin Login](Vaidehi_Exp6/screenshots/1_login_admin_success.png)

### 2️⃣ Admin Accessing /admin/dashboard — 200 OK ✅
![Admin Dashboard](Vaidehi_Exp6/screenshots/2_admin_dashboard_success.png)

### 3️⃣ User Login — 200 OK
![User Login](Vaidehi_Exp6/screenshots/3_login_user_success.png)

### 4️⃣ USER Accessing /user/profile — 200 OK ✅
![User Profile](Vaidehi_Exp6/screenshots/4_user_profile_success.png)

### 5️⃣ USER Denied /admin/dashboard — 403 Forbidden ❌
![User Denied](Vaidehi_Exp6/screenshots/5_user_denied_admin.png)

### 6️⃣ No Token — 401 Unauthorized ❌
![No Token](Vaidehi_Exp6/screenshots/6_no_token_401.png)

### 7️⃣ Wrong Password — 401 Unauthorized ❌
![Invalid Login](Vaidehi_Exp6/screenshots/7_invalid_login.png)

---

## 🎯 Key Concepts

| Concept | How it works |
|---|---|
| 🔑 Token Generation | HS256 signed JWT with role claim, 1 hour expiry |
| 🛡️ Token Validation | JwtFilter intercepts every request |
| 👑 Role Enforcement | Spring Security hasRole on URL patterns |
| 🚫 Token Blacklisting | In-memory HashSet on logout |
| ⚡ Stateless Auth | No server-side sessions |
| 🔒 Route Security | 401 Unauthorized and 403 Forbidden responses |

---

<div align="center">
Experiment 7 · FullStack Development 2026 · <b>Vaidehi Sharma</b> · 23BAI70334
</div>

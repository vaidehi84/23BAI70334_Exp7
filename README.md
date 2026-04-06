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

A secure REST API backend implementing **Role-Based Access Control (RBAC)** using **Spring Boot + Spring Security + JWT**. Users log in with a role (`ADMIN` or `USER`), receive a signed token, and can only access endpoints permitted for their role.

---

## ✨ Features

- 👑 `ADMIN` role — full access including admin-only endpoints
- 👤 `USER` role — restricted to user-level endpoints only
- 🔑 Login with username & password → receive signed JWT with role
- 🛡️ Protected routes enforced by Spring Security role rules
- 🚪 Logout with token blacklisting (in-memory)
- ⚡ Stateless — zero server-side sessions
- 🔒 Custom JWT filter chain with 401 / 403 responses

---

## ⚙️ Tech Stack

| Technology | Version | Role |
|---|---|---|
| ☕ Java | 17 | Core language |
| 🍃 Spring Boot | 3.2.3 | Backend framework |
| 🔒 Spring Security | 6.2.2 | Security & authorization layer |
| 🔑 JWT (jjwt) | 0.11.5 | Token generation & validation |
| 🔧 Maven | 3.9.x | Build tool |

---

## 🗂️ Project Structure

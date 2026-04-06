---

## 👥 Users & Credentials

| Username | Password | Role | Access |
|:---:|:---:|:---:|:---|
| `admin` | `admin123` | 👑 `ADMIN` | All endpoints |
| `vaidehi` | `user123` | 👤 `USER` | `/user/**` only |

---

## 📡 API Reference

| Method | Endpoint | Auth | Description |
|:---:|:---|:---:|:---|
| `POST` | `/login` | ❌ None | Authenticate → receive JWT |
| `POST` | `/logout` | ✅ Bearer | Blacklist & invalidate token |
| `GET` | `/admin/dashboard` | 👑 ADMIN | Admin dashboard |
| `GET` | `/admin/users` | 👑 ADMIN | List all users |
| `GET` | `/user/profile` | 👤 USER or ADMIN | User profile |
| `GET` | `/user/dashboard` | 👤 USER or ADMIN | User dashboard |

---

## 🚀 Getting Started
```bash
# Clone
git clone https://github.com/vaidehi84/23BAI70334_Exp7.git
cd 23BAI70334_Exp7/Vaidehi_Exp6

# Run
mvn spring-boot:run
```

🌐 Server starts at `http://localhost:8083`

---

## 🧪 Postman Testing Guide

**1️⃣ Login as Admin**
```http
POST http://localhost:8083/login
Content-Type: application/json

{ "username": "admin", "password": "admin123" }
```

**2️⃣ Admin accesses Admin Dashboard**
```http
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <admin_token>
```

**3️⃣ Login as User**
```http
POST http://localhost:8083/login
Content-Type: application/json

{ "username": "vaidehi", "password": "user123" }
```

**4️⃣ User accesses User Profile ✅**
```http
GET http://localhost:8083/user/profile
Authorization: Bearer <user_token>
```

**5️⃣ User tries Admin Dashboard ❌**
```http
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <user_token>
→ 403 Forbidden
```

---

## 📸 Screenshots

### 1️⃣ Admin Login — 200 OK
![Admin Login](Vaidehi_Exp6/screenshots/1_login_admin_success.png)

### 2️⃣ Admin Accessing `/admin/dashboard` — 200 OK ✅
![Admin Dashboard](Vaidehi_Exp6/screenshots/2_admin_dashboard_success.png)

### 3️⃣ User Login — 200 OK
![User Login](Vaidehi_Exp6/screenshots/3_login_user_success.png)

### 4️⃣ USER Accessing `/user/profile` — 200 OK ✅
![User Profile](Vaidehi_Exp6/screenshots/4_user_profile_success.png)

### 5️⃣ USER Denied `/admin/dashboard` — 403 Forbidden ❌
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
| 👑 Role Enforcement | Spring Security `hasRole()` on URL patterns |
| 🚫 Token Blacklisting | In-memory HashSet on logout |
| ⚡ Stateless Auth | No server-side sessions |
| 🔒 Route Security | 401 Unauthorized / 403 Forbidden responses |

---

<div align="center">

Experiment 7 · FullStack Development 2026 · **Vaidehi Sharma** · 23BAI70334

</div>

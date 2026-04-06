---

## 👥 Users & Credentials

| Username | Password | Role |
|:---:|:---:|:---:|
| `admin` | `admin123` | 👑 ADMIN |
| `vaidehi` | `user123` | 👤 USER |

---

## 🛡️ API Endpoints

| Method | Endpoint | Role Required | Description |
|:---:|:---|:---:|:---|
| `POST` | `/login` | None | Get JWT token |
| `POST` | `/logout` | Any | Invalidate token |
| `GET` | `/admin/dashboard` | 👑 ADMIN only | Admin dashboard |
| `GET` | `/admin/users` | 👑 ADMIN only | List users |
| `GET` | `/user/profile` | 👤 USER or ADMIN | User profile |
| `GET` | `/user/dashboard` | 👤 USER or ADMIN | User dashboard |

---

## 📸 Screenshots

### 1️⃣ Admin Login — 200 OK
![Admin Login](screenshots/1_login_admin_success.png)

---

### 2️⃣ Admin Accessing `/admin/dashboard` — 200 OK ✅
![Admin Dashboard](screenshots/2_admin_dashboard_success.png)

---

### 3️⃣ User Login — 200 OK
![User Login](screenshots/3_login_user_success.png)

---

### 4️⃣ USER Accessing `/user/profile` — 200 OK ✅
![User Profile](screenshots/4_user_profile_success.png)

---

### 5️⃣ USER Denied `/admin/dashboard` — 403 Forbidden ❌
![User Denied](screenshots/5_user_denied_admin.png)

---

### 6️⃣ No Token — 401 Unauthorized ❌
![No Token](screenshots/6_no_token_401.png)

---

### 7️⃣ Wrong Password — 401 Unauthorized ❌
![Invalid Login](screenshots/7_invalid_login.png)

---

## ⚙️ How to Run
```bash
git clone https://github.com/vaidehi84/23BAI70334_Exp7.git
cd 23BAI70334_Exp7
mvn spring-boot:run
```

Server runs at: **`http://localhost:8083`**

---

## 🧪 Quick Postman Test
```http
# 1. Login as admin
POST http://localhost:8083/login
{ "username": "admin", "password": "admin123" }

# 2. Access admin route (paste token)
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <token>

# 3. Login as user
POST http://localhost:8083/login
{ "username": "vaidehi", "password": "user123" }

# 4. User allowed
GET http://localhost:8083/user/profile
Authorization: Bearer <user_token>

# 5. User blocked
GET http://localhost:8083/admin/dashboard
Authorization: Bearer <user_token>
→ 403 Forbidden ❌
```

---

<div align="center">
Made with ❤️ by <b>Vaidehi Sharma</b> | 23BAI70334
</div>

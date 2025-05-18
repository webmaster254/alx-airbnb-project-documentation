# 📋 Technical & Functional Requirements

This document outlines the technical and functional requirements for the following core backend features of the Airbnb Clone Project:

1. **User Authentication**
2. **Property Management**
3. **Booking System**

Each feature includes:
- **Functional description**
- **API endpoints**
- **Input/output specifications**
- **Validation rules**
- **Performance criteria**

---

## 1. 🔐 User Authentication

### ✅ Functional Description
The user authentication system allows users to register, log in, and manage their session securely. It supports JWT-based authentication and role-based access control (guest, host, admin).

### 📡 API Endpoints

| Endpoint | Method | Description |
|---------|--------|-------------|
| `/api/auth/register` | `POST` | Registers a new user |
| `/api/auth/login` | `POST` | Authenticates user and returns a JWT token |
| `/api/auth/logout` | `POST` | Logs out the user (clears token or invalidates session) |
| `/api/users/me` | `GET` | Fetches current logged-in user details |

### 📥 Input Specifications

#### Register
```json
{
  "name": "string",
  "email": "string (valid email)",
  "password": "string (min 8 chars)",
  "role": "string (optional: 'guest', 'host')"
}

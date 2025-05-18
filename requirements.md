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

### Login
```json
{
  "email": "string (valid email)",
  "password": "string"
}
```

### 📤 Output Specifications

```json
{
  "token": "string (JWT token)",
  "user": {
    "id": "string (user ID)",
    "name": "string",
    "email": "string (valid email)",
    "role": "string (guest, host, admin)"
  }
}
```

### Error Response

```json
{
  "error": "string (error message)"
}
```

### ⚠️ Validation Rules

- Email must be unique and valid.
- Password must be at least 8 characters long.
- All required fields must be provided.

### 🚀 Performance Criteria

- Registration and login should complete within 500ms under normal load.
- System should handle 100 concurrent login attempts without failure

---

## 2. 🏠 Property Management

### ✅ Functional Description

The property management system allows hosts to create, update, and delete their properties. It also provides functionality to fetch properties by host ID.

### 📡 API Endpoints

| Endpoint | Method | Description |
|---------|--------|-------------|
| `/api/properties` | `POST` | Creates a new property |
| `/api/properties/:id` | `GET` | Fetches a specific property by ID |
| `/api/properties/:id` | `PUT` | Updates a specific property by ID |
| `/api/properties/:id` | `DELETE` | Deletes a specific property by ID |
| `/api/properties` | `GET` | Fetches all properties by host ID |

### 📤 Input Specifications

```json
{
  "title": "string",
  "description": "string",
  "price_per_night": "number",
  "location": "string",
  "bedrooms": "integer",
  "amenities": ["string"],
  "images": ["url"]
}
```

### 📤 Output Specifications

```json
{
  "id": "string",
  "title": "string",
  "description": "string",
  "price_per_night": "number",
  "location": "string",
  "host_id": "string",
  "amenities": ["string"],
  "images": ["url"],
  "created_at": "date-time" 
}
```

### Error Response

```json
{
  "error": "string (error message)"
}
```

### ⚠️ Validation Rules

- Title must be at least 5 characters long.
- Description must be at least 10 characters long.
- Price per night must be a positive number.
- Location must be a valid string.
- Bedrooms must be a positive integer.
- Amenities must be an array of strings.
- Images must be an array of valid URLs.

### 🚀 Performance Criteria

- Property creation should complete within 1 second under normal load.
- System should handle 100 concurrent property creation attempts without failure.

---

## 3. 📅 Booking System

### ✅ Functional Description

The booking system allows guests to book properties and manage their bookings. It supports creating, updating, and deleting bookings, as well as fetching bookings by guest ID.

### 📡 API Endpoints

| Endpoint | Method | Description |
|---------|--------|-------------|
| `/api/bookings` | `POST` | Creates a new booking |
| `/api/bookings/:id` | `GET` | Fetches a specific booking by ID |
| `/api/bookings/:id` | `PUT` | Updates a specific booking by ID |
| `/api/bookings/:id` | `DELETE` | Deletes a specific booking by ID |
| `/api/bookings` | `GET` | Fetches all bookings by guest ID |

### 📤 Input Specifications

```json
{
  "property_id": "string",
  "check_in_date": "date",
  "check_out_date": "date",
  "guest_id": "string"
}
```

### 📤 Output Specifications

```json
{
  "id": "string",
  "property_id": "string",
  "check_in_date": "date",
  "check_out_date": "date",
  "guest_id": "string",
  "created_at": "date-time"
}
```

### Error Response

```json
{
  "error": "string (error message)"
}
```

### ⚠️ Validation Rules

- Property ID must be a valid string.
- Check-in date must be a valid date.
- Check-out date must be a valid date.
- Guest ID must be a valid string.

### 🚀 Performance Criteria

- Booking creation should complete within 1 second under normal load.
- System should handle 100 concurrent booking creation attempts without failure.

---

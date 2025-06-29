# 📋 Backend Feature Requirements – Airbnb Clone

This document outlines the **functional** and **technical specifications** for three core backend features: **User Authentication**, **Property Management**, and **Booking System**. These specifications serve as the blueprint for API development and validation enforcement.

---

## 1️⃣ User Authentication

### 🎯 Objective
Allow users (guests/hosts/admins) to securely register, log in, and manage sessions using JWT.

### 📌 Endpoints
| Method | Endpoint           | Description             |
|--------|--------------------|-------------------------|
| POST   | `/api/auth/register` | Register new user       |
| POST   | `/api/auth/login`    | Log in with credentials |
| GET    | `/api/auth/profile`  | Fetch authenticated user profile |
| PUT    | `/api/auth/profile`  | Update user profile     |

### 🧾 Input Fields
| Field         | Type    | Validation                       |
|---------------|---------|----------------------------------|
| `email`       | string  | Required, valid email, unique    |
| `password`    | string  | Required, min 8 chars, hashed    |
| `first_name`  | string  | Required                         |
| `last_name`   | string  | Required                         |
| `role`        | enum    | `guest`, `host`, `admin`         |
| `phone_number`| string  | Optional, E.164 format            |

### 🔐 Security
- Passwords hashed with bcrypt (12 salt rounds).
- JWT token returned upon login (`Authorization: Bearer <token>`).
- Auth middleware for protected routes.
- Role-based access control (RBAC).

### 📈 Performance & Rate Limits
- Login: max 5 attempts/min/IP
- Token expiration: 1 hour
- Profile read/write: < 100ms latency

---

## 2️⃣ Property Management

### 🎯 Objective
Enable hosts to create, update, delete, and retrieve property listings.

### 📌 Endpoints
| Method | Endpoint                     | Description              |
|--------|------------------------------|--------------------------|
| POST   | `/api/properties`           | Create new listing       |
| GET    | `/api/properties`           | Fetch all listings       |
| GET    | `/api/properties/:id`       | Fetch single listing     |
| PUT    | `/api/properties/:id`       | Update listing (host-only) |
| DELETE | `/api/properties/:id`       | Delete listing (host-only) |

### 🧾 Input Fields
| Field          | Type     | Validation                      |
|----------------|----------|---------------------------------|
| `name`         | string   | Required                        |
| `description`  | text     | Required                        |
| `location`     | string   | Required                        |
| `pricepernight`| decimal  | Required, > 0                   |
| `amenities`    | array    | Optional, predefined strings    |
| `images[]`     | string[] | Optional (uploaded to S3/local) |

### 🔐 Access
- Only users with `host` role can create/update/delete.
- GET endpoints are public (for guests to browse).

### 🧠 Logic & Validation
- Validate price > 0
- Max 10 images per listing
- Slug or ID must be unique

### 📈 Performance Targets
- Fetch all: paginated (limit=20, offset)
- Create/Update: < 200ms

---

## 3️⃣ Booking System

### 🎯 Objective
Allow guests to book properties, view bookings, and cancel when needed. Hosts can also manage incoming bookings.

### 📌 Endpoints
| Method | Endpoint                 | Description                |
|--------|--------------------------|----------------------------|
| POST   | `/api/bookings`         | Create a new booking       |
| GET    | `/api/bookings`         | View own bookings          |
| GET    | `/api/bookings/:id`     | View single booking        |
| PUT    | `/api/bookings/:id/cancel` | Cancel booking (if eligible) |

### 🧾 Input Fields
| Field        | Type     | Validation                      |
|--------------|----------|---------------------------------|
| `property_id`| UUID     | Required, must exist            |
| `start_date` | date     | Required, >= today              |
| `end_date`   | date     | Required, > start_date          |

### 🔐 Access
- Only users with role `guest` can book
- Only hosts or guests involved can view the booking
- Only guests can cancel before check-in date

### 🧠 Logic
- Check property availability for requested dates
- Prevent overlapping bookings
- Auto-calculate total price = `price_per_night × nights`

### 📈 Performance Criteria
- Booking creation: < 300ms (with cache on date validation)
- Booking search: indexed by `user_id`, `property_id`, and `date`

---

## ✅ Conclusion

This document ensures clarity in how backend features are structured, secured, and validated. These requirements serve as the foundation for API development and testing.


# 🍋 Little Lemon Backend Web Application

**Little Lemon Backend Web Application** is a Django-based backend system developed for a fictitious Mediterranean restaurant named *Little Lemon*. This project was created as the **final capstone** for the [Meta Back-End Developer Specialization Certificate Course](https://www.coursera.org/learn/back-end-developer-capstone/).

---

## 🚀 Project Overview

This web application is built using:

- **Django**
- **Django REST Framework (DRF)**
- **Djoser** for user authentication
- **MySQL** as the relational database backend

The project includes both static and dynamic content served via API endpoints. A sample static page is available at:

```
http://localhost:8000/restaurant/
```

---

## 🔐 User Roles and Authentication

Authentication is handled using **Djoser**, allowing:

- Secure login for users
- Token-based authentication
- Role-based access control (admin vs customer)

### Predefined Users

| Role      | Username   | Password     |
|-----------|------------|--------------|
| Admin     | `admin`    | `123`        |
| Customer  | `customer1`| `lemon@123!` |
| Customer  | `customer2`| `lemon@123!` |

---

## 📡 API Endpoints

All API endpoints are prefixed with:

```
/restaurant/api/
```

### 📋 Menu Management (`/menu`)

#### `GET /menu/`
- **Access:** Authenticated users
- **Description:** View all menu items

#### `POST /menu/`
- **Access:** Admin only
- **Description:** Add a new menu item
- **Fields:**
  - `title` (string)
  - `price` (decimal)
  - `featured` (optional, boolean, default: `false`)

#### `GET /menu/<int:pk>/`
- **Access:** Authenticated users
- **Description:** View single menu item

#### `PUT /menu/<int:pk>/`, `DELETE /menu/<int:pk>/`
- **Access:** Admin only
- **Description:** Update or delete single menu item

---

### 📖 Booking System (`/book`)

#### `POST /book/`
- **Access:** Authenticated users
- **Description:** Book a reservation using the same username as the booking name
- **Fields:**
  - `name` (string) – must match current username
  - `guest_number` (optional, integer, default: `1`)
  - `date` (string, format `YYYY-MM-DD`)
  - `comment` (optional, text)

#### `GET /book/`
- **Access:** Authenticated users
- **Description:** View all bookings made by the current user

#### `GET /book/<int:pk>/`, `DELETE /book/<int:pk>/`
- **Access:** Admin only
- **Description:** View or delete a specific booking

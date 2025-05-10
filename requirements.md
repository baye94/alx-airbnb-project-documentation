# Backend Feature Requirements - ALX Airbnb Clone

## 1. User Authentication

### Description
Handles user registration, login, and authentication using JWT. Supports different roles: guest, host, and admin.

### API Endpoints
- **POST /api/auth/register**
  - Input: `{ "first_name": "John", "last_name": "Doe", "email": "john@example.com", "password": "Pass@123", "role": "guest" }`
  - Output: `201 Created`, user object without password
  - Validation:
    - Email must be unique and valid
    - Password must meet complexity rules
    - Role must be one of: guest, host, admin

- **POST /api/auth/login**
  - Input: `{ "email": "john@example.com", "password": "Pass@123" }`
  - Output: `{ "token": "jwt_token_here", "user": { ... } }`
  - Validation:
    - Correct email/password combination

### Performance Criteria
- Login should complete in under 500ms for 95% of requests
- JWT token expiry after 24 hours

---

## 2. Property Management

### Description
Allows hosts to create, edit, view, and delete property listings.

### API Endpoints
- **POST /api/properties**
  - Input: `{ "name": "Sea View Villa", "description": "Nice view", "location": "Miami", "pricepernight": 150.00 }`
  - Output: `201 Created`, property object
  - Validation:
    - Price must be a positive number
    - Required fields: name, location, pricepernight

- **GET /api/properties**
  - Input: Optional filters (`?location=Miami&priceMin=100&priceMax=200`)
  - Output: List of properties matching filters

- **PUT /api/properties/{id}**
  - Input: JSON object with updatable fields
  - Output: `200 OK`, updated property object

- **DELETE /api/properties/{id}**
  - Output: `204 No Content`

### Performance Criteria
- Querying all properties should take < 1s for up to 10,000 entries
- Support pagination (e.g., `?page=1&limit=10`)

---

## 3. Booking System

### Description
Enables guests to book available properties for a date range and track booking status.

### API Endpoints
- **POST /api/bookings**
  - Input: `{ "property_id": "uuid", "user_id": "uuid", "start_date": "2025-06-01", "end_date": "2025-06-10" }`
  - Output: `201 Created`, booking object with status "pending"
  - Validation:
    - Dates must not overlap with existing bookings
    - start_date < end_date

- **GET /api/bookings/user/{userId}**
  - Output: List of bookings made by the user

- **PUT /api/bookings/{bookingId}/cancel**
  - Output: `200 OK`, booking status updated to "canceled"

### Performance Criteria
- Booking creation should take < 1s with validation
- Prevent race conditions with date overlap using database constraints or locks

# VoltArena Server

Backend API for VoltArena, a sports facility booking platform built with Node.js, Express.js, MongoDB, and JWT authentication.

## Features

* Facility CRUD Operations
* Facility Search & Filtering
* Featured Facilities Endpoint
* Booking Management
* MongoDB Database Integration
* JWT Authentication using JWKS
* Protected Routes
* Environment Variable Support
* RESTful API Architecture

---

## Tech Stack

* Node.js
* Express.js
* MongoDB
* JOSE (JWT Verification)
* dotenv
* cors

---

## Installation

### Clone the Repository

```bash
git clone <your-repository-url>
cd voltarena-server
```

### Install Dependencies

```bash
npm install
```

### Create Environment Variables

Create a `.env` file in the root directory.

```env
PORT=5000

MONGODB_URI=your_mongodb_connection_string

CLIENT_URL=http://localhost:3000
```

---

## Run the Server

### Development

```bash
npm run dev
```

### Production

```bash
npm start
```

Server runs at:

```text
http://localhost:5000
```

---

## API Endpoints

### Health Check

#### GET /

```http
GET /
```

Response:

```json
"Server is Serving"
```

---

## Facilities

### Get Featured Facilities

```http
GET /featured
```

Returns the first 6 featured facilities.

---

### Get All Facilities

```http
GET /facility
```

#### Query Parameters

| Parameter | Description                |
| --------- | -------------------------- |
| userId    | Filter facilities by owner |
| search    | Search facility name       |
| type      | Filter by facility type    |

Example:

```http
GET /facility?search=football&type=Indoor,Outdoor
```

---

### Get Single Facility

```http
GET /facility/:id
```

Example:

```http
GET /facility/684d6e2c5b87d72a0f1b2345
```

---

### Create Facility

Protected Route

```http
POST /facility
```

Headers:

```http
Authorization: Bearer <token>
```

---

### Update Facility

Protected Route

```http
PATCH /facility/:id
```

Headers:

```http
Authorization: Bearer <token>
```

---

### Delete Facility

Protected Route

```http
DELETE /facility/:id
```

Headers:

```http
Authorization: Bearer <token>
```

---

## Bookings

### Get User Bookings

```http
GET /booking/:userId
```

Example:

```http
GET /booking/user123
```

---

### Create Booking

```http
POST /booking
```

Sample Request:

```json
{
  "userId": "user123",
  "facilityId": "facility456",
  "date": "2026-05-31"
}
```

---

### Delete Booking

Protected Route

```http
DELETE /booking/:bookingId
```

Headers:

```http
Authorization: Bearer <token>
```

---

## Authentication

JWT tokens are verified using a JWKS endpoint.

Authorization Header:

```http
Authorization: Bearer <your_token>
```

JWKS Endpoint:

```text
${CLIENT_URL}/api/auth/jwks
```

---

## Database Collections

### facilities

Stores facility information.

### bookings

Stores user booking records.

---

## Project Structure

```text
voltarena-server/
│
├── server.js
├── package.json
├── .env
└── README.md
```

---

## Dependencies

```json
{
  "express": "^5.x",
  "mongodb": "^6.x",
  "dotenv": "^17.x",
  "cors": "^2.x",
  "jose-cjs": "^latest"
}
```

---

## License

MIT License

---

## Author

Built for the VoltArena platform.

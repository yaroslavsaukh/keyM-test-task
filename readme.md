# Booking API

This project provides an API service that supports user registration, authorization, and booking management. The service is built to ensure data validation, conflict handling, and secure authentication using JWT.

## Features

1. **User Authentication**:
    - User Registration (POST /auth/register)
    - User Login (POST /auth/login)
    - Token-based Authentication using JWT

2. **Booking Management**:
    - Create a booking
    - Fetch all bookings
    - Fetch a booking by ID
    - Delete a booking
    -  Update an existing booking

3. **Conflict Handling**:
    - Ensures no overlapping bookings for the same date and time range.

4. **Data Validation**:
    - Validates incoming request data to ensure correct format and integrity.

5. **Storage**:
    - Uses MongoDB with Mongoose for data storage.

6. **Documentation**:
    - Swagger documentation for all API endpoints.

7. **Testing**:
    - Unit tests covering at least 70% of the codebase using Jest.

8. **Deployment**:
    - Deployed to a free cloud service (e.g., Render, Vercel, or Railway).

## Endpoints

### User Authentication

#### Register User
- **Endpoint**: `POST /auth/register`
- **Request Body**:
  ```json
  {
    "username": "exampleUser",
    "password": "securePassword123"
  }
  ```
- **Response**:
  ```json
  {
    "token": "jwt-token"
  }
  ```

#### Login User
- **Endpoint**: `POST /auth/login`
- **Request Body**:
  ```json
  {
    "username": "exampleUser",
    "password": "securePassword123"
  }
  ```
- **Response**:
  ```json
  {
    "token": "jwt-token"
  }
  ```

### Booking Management

#### Create a Booking
- **Endpoint**: `POST /bookings`
- **Request Body**:
  ```json
  {
    "user": "John Doe",
    "date": "2024-12-18",
    "startTime": "10:00",
    "endTime": "11:00"
  }
  ```
- **Response**:
  ```json
  {
    "id": "bookingId",
    "user": "John Doe",
    "date": "2024-12-18",
    "startTime": "10:00",
    "endTime": "11:00"
  }
  ```
- **Conflict Handling**:
    - Returns an error if a booking overlaps with an existing one.

#### Get All Bookings
- **Endpoint**: `GET /bookings`
- **Response**:
  ```json
  [
    {
      "id": "bookingId",
      "user": "John Doe",
      "date": "2024-12-18",
      "startTime": "10:00",
      "endTime": "11:00"
    }
  ]
  ```

#### Get a Booking by ID
- **Endpoint**: `GET /bookings/:id`
- **Response**:
  ```json
  {
    "id": "bookingId",
    "user": "John Doe",
    "date": "2024-12-18",
    "startTime": "10:00",
    "endTime": "11:00"
  }
  ```

#### Delete a Booking
- **Endpoint**: `DELETE /bookings/:id`
- **Response**:
  ```json
  {
    "message": "Booking deleted successfully."
  }
  ```

#### Update a Booking (Bonus)
- **Endpoint**: `PUT /bookings/:id`
- **Request Body**:
  ```json
  {
    "date": "2024-12-19",
    "startTime": "12:00",
    "endTime": "13:00"
  }
  ```
- **Response**:
  ```json
  {
    "id": "bookingId",
    "user": "John Doe",
    "date": "2024-12-19",
    "startTime": "12:00",
    "endTime": "13:00"
  }
  ```

## Installation and Usage

### Prerequisites
- Node.js
- MongoDB instance (local or cloud)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yaroslavsaukh/keyM-test-task
   cd keyM_test
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file with the following variables:
   ```env
   PORT=3000
   MONGO_URI=your-mongodb-uri
   JWT_SECRET=your-secret-key
   ```
4. Start the application:
   ```bash
   npm run server
   ```

### Running Tests
- Run unit tests:
  ```bash
  npm test
  ```

## API Documentation

The API is documented with Swagger. After starting the application, navigate to `http://localhost:3000/api-docs` to view the documentation.

## Additional Notes

- **Assumptions**:
    - Users must be authenticated to manage bookings.
- **Technologies Used**:
    - Framework: Express.js
    - Database: MongoDB
    - Authentication: JSON Web Tokens (JWT)

## Deployment

The API is deployed at: [Live URL](https://keym-test-p4x6.onrender.com/api-docs/)

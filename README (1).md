
# Mood Sensing Backend Application

## Overview
This is a backend application for mood sensing and analysis, developed using Node.js, Express, and MongoDB. The application allows users to upload mood captures with location data, get mood frequency distributions, and find the closest location where the user has been happy.

## Features
- Register and authenticate users
- Upload mood captures with location data
- Get mood frequency distribution for a user
- Find the closest location where the user has been happy

## Getting Started

### Prerequisites
- Node.js
- MongoDB

### Installation

1. Install dependencies:
   ```
   npm install
   ```

2. Create a `.env` file in the root directory with the following content:
   ```
   PORT=5000
   MONGO_URI=mongodbconnstring
   JWT_SECRET=jwtsecretToSignToken
   ```

4. Start the server:
   ```bash
   npm start
   ```

## API Endpoints

### Register a new user
```http
POST /api/users/register
Content-Type: application/json

{
  "username": "testuser",
  "password": "password"
}
```

### Authenticate user and get JWT token
```http
POST /api/users/login
Content-Type: application/json

{
  "username": "testuser",
  "password": "password"
}
```

### Upload a mood capture
```http
POST /api/moods
Content-Type: application/json
Authorization: Bearer <jwttoken>

{
  "userId": "userid",
  "moodType": "happy",
  "location": [latitude, longitude]
}
```

### Get mood frequency distribution for a user
```http
GET /api/moods/frequency/:userId
Authorization: Bearer <jwttoken>
```

### Find the closest location where the user has been happy
```http
POST /api/moods/happy-location
Content-Type: application/json
Authorization: Bearer <jwttoken>

{
  "userId": "userid",
  "currentLocation": [latitude, longitude]
}
```

## Running the Application

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the server:
   ```bash
   npm start
   ```

3. If we use Postman to interact with the API:
   - Register a new user:
     ```http
     POST /api/users/register
     Content-Type: application/json
     {
       "username": "testuser",
       "password": "password"
     }
     ```

   - Log in to get a JWT token:
     ```http
     POST /api/users/login
     Content-Type: application/json
     {
       "username": "testuser",
       "password": "password"
     }
     ```

   - Use the token for creating mood entries:
     ```http
     POST /api/moods
     Content-Type: application/json
     Authorization: Bearer <your_jwt_token>
     {
       "userId": "userid"
       "moodType": "happy",
       "location": [latitude, longitude]
     }
     ```

   - Find the closest location where the user has been happy:
     ```http
     POST /api/moods/happy-location
     Content-Type: application/json
     Authorization: Bearer <jwttoken>
     {
       "userId": "userid",
       "currentLocation": [latitude, longitude]
     }
     ```

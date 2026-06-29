# NutriTrack

NutriTrack is a full-stack meal tracking application with a Spring Boot backend and a React frontend. It lets users register, manage their profile, create foods, build meals from foods, and track daily calorie intake.

## Project Structure

- `backend/App` - Spring Boot 3 API built with Gradle and Java 17
- `frontend` - React application created with Create React App

## Features

- User registration and login
- User profile editing
- BMI and recommended daily calorie display
- Food catalog with create, read, update, and delete operations
- Meal creation from selected foods and custom amounts
- Daily calorie total per user
- Admin user management page
- OpenAPI / Swagger UI support in the backend

## Tech Stack

### Backend

- Java 17
- Spring Boot 3.3
- Spring Web
- Spring Data JPA
- PostgreSQL
- H2 for tests
- ModelMapper
- springdoc OpenAPI

### Frontend

- React 19
- React Router
- Axios

## How It Works

The backend exposes REST endpoints under `/api` for users, foods, and meals.

Main backend routes:

- `/api/users`
- `/api/foods`
- `/api/meals`

The frontend stores the logged-in user ID in `localStorage` and sends it with API requests. Protected pages use that stored ID to gate access. The admin screen is currently unlocked for the user whose ID is `1`.

## Prerequisites

- Java 17
- Node.js and npm
- PostgreSQL

## Backend Setup

The backend is configured in `backend/App/src/main/resources/application.properties` to use PostgreSQL on:

- host: `localhost`
- port: `5432`
- database: `tjv_app`
- username: `polzemat`

Before starting the backend, create the database and update the password in the properties file if needed.

Run the backend:

```bash
cd backend/App
./gradlew bootRun
```

The backend also contains test configuration that uses an in-memory H2 database.

Run backend tests:

```bash
cd backend/App
./gradlew test
```

## Frontend Setup

Install dependencies and start the frontend:

```bash
cd frontend
npm install
npm start
```

By default, the frontend calls:

```text
http://localhost:8080/api
```

You can override this with the `REACT_APP_API_URL` environment variable.

## API Documentation

Once the backend is running, Swagger UI should be available through the springdoc default path:

```text
http://localhost:8080/swagger-ui/index.html
```

## Notes

- Meals are timestamped automatically when created.
- Daily calorie totals are calculated from foods assigned to meals for the current day.
- Foods are linked to users, and meals belong to a specific user.
- There is no full authentication system yet; login returns the user ID, which the frontend stores locally.
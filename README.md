# music-platform-backend

A Node.js/Express backend for a music application, built with a MERN-stack orientation (MongoDB, Express, Node.js). It handles user authentication, role-based access control, and management of music and album data.

## Features

- **JWT-based authentication** — secure login and signup using JSON Web Tokens
- **Role-based access control (RBAC)** — different permission levels for different user roles (e.g. admin vs regular user)
- **Music and album management** — CRUD operations for songs and albums
- **File/media storage service** — dedicated service layer for handling storage of media files
- **MongoDB with Mongoose** — schema-based data modeling for users, music, and albums

## Tech Stack

- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB (via Mongoose ODM)
- **Auth:** JSON Web Tokens (JWT)
- **Environment management:** dotenv (`.env`)

## Project Structure

```
ROLE_.../
├── node_modules/              # Installed dependencies
├── src/
│   ├── controllers/
│   │   ├── auth.controller.js     # Handles signup, login, and auth-related logic
│   │   └── music.controller.js    # Handles music/album creation, retrieval, updates, deletion
│   ├── db/
│   │   └── db.js                  # MongoDB connection setup
│   ├── middleware/
│   │   └── auth.middleware.js     # JWT verification and role-based access control checks
│   ├── models/
│   │   ├── album.model.js         # Mongoose schema for albums
│   │   ├── music.model.js         # Mongoose schema for songs/tracks
│   │   └── user.model.js          # Mongoose schema for users (roles, credentials, etc.)
│   ├── routes/
│   │   ├── auth.routes.js         # API endpoints for authentication (signup/login)
│   │   └── music.routes.js        # API endpoints for music/album operations
│   ├── services/
│   │   └── storage.service.js     # Logic for storing/retrieving media files
│   └── app.js                     # Express app configuration (middleware, routes setup)
├── .env                        # Environment variables (DB URI, JWT secret, etc.)
├── package.json                # Project dependencies and scripts
├── package-lock.json           # Locked dependency versions
└── server.js                   # Entry point — starts the Express server
```

## Folder & File Descriptions

### `src/controllers/`
Contains the business logic that runs when a route is hit.
- **auth.controller.js** — Manages user registration, login, and token generation.
- **music.controller.js** — Manages creating, reading, updating, and deleting music/album entries.

### `src/db/`
- **db.js** — Establishes and exports the connection to the MongoDB database.

### `src/middleware/`
- **auth.middleware.js** — Verifies JWT tokens on protected routes and enforces role-based access restrictions.

### `src/models/`
Mongoose schemas that define the shape of data stored in MongoDB.
- **album.model.js** — Schema for album documents.
- **music.model.js** — Schema for individual song/track documents.
- **user.model.js** — Schema for user accounts, including roles and authentication fields.

### `src/routes/`
Defines the API endpoints and maps them to controller functions.
- **auth.routes.js** — Routes for `/auth` (signup, login, etc.).
- **music.routes.js** — Routes for `/music` (CRUD operations on songs/albums).

### `src/services/`
- **storage.service.js** — Handles the logic for uploading/storing and serving media files (e.g. audio files, album art).

### Root Files
- **app.js** — Configures the Express application: middleware, route mounting, error handling.
- **server.js** — Starts the HTTP server and connects to the database.
- **.env** — Stores sensitive configuration values (MongoDB URI, JWT secret, port, etc.). Not committed to version control.
- **package.json / package-lock.json** — Project metadata, dependencies, and scripts.

## Getting Started

### Prerequisites
- Node.js installed
- MongoDB instance (local or Atlas)

### Installation
```bash
npm install
```

### Environment Variables
Create a `.env` file in the root directory with the following (example):
```
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

### Running the Server
```bash
node server.js
```

## API Overview

| Route Prefix | Description |
|---------------|-------------|
| `/auth` | User signup, login, authentication |
| `/music` | Create, read, update, delete songs and albums |

*(Exact endpoint paths and request/response formats can be documented in more detail as the API stabilizes.)*

## Roadmap

This project is still evolving. Planned additions include:
- More features (playlists, search, likes/favorites, comments, etc. — to be finalized)
- A dedicated **frontend** (likely built with React, following a MERN stack approach) to consume this backend API
- Expanded API documentation once the frontend integration begins

## License

Not yet decided.

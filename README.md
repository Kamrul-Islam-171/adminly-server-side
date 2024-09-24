# Adminly - Server Side

This is the server-side code for **Adminly**, a user management web application built with **Node.js**, **Express**, and **MongoDB**. The server handles user registration, authentication, and user management, including blocking, unblocking, and deleting users. **JWT** is used for secure authentication, and **bcrypt** is used for password hashing.

## Live Demo
[Adminly - Live Link]()

## Client-Side Repository
[Client-Side Code - GitHub](https://github.com/Kamrul-Islam-171/adminly-client-side)

---

## Features
- **User Registration**: Users can register with a unique email address.
- **User Login**: Provides JWT token after successful login.
- **User Management**: Admins can block, unblock, and delete users.
- **Password Security**: User passwords are securely hashed using bcrypt.
- **JWT Authentication**: JWT tokens are used to secure API routes.
- **Blocking**: Blocked users cannot log in.
- **Unique Email Constraint**: Ensures that emails are unique using MongoDB indexes.

---

## Technologies Used
- **Node.js**
- **Express.js**
- **MongoDB**
- **JWT (JSON Web Token)**
- **bcrypt**
- **dotenv**: For environment variables management.
- **Cors**: To allow cross-origin requests.

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Kamrul-Islam-171/adminly-server-side
cd adminly-server-side
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Environment Setup

Create a `.env` file in the project root and add the following environment variables:

```env
DB_USER=<your-mongodb-username>
DB_PASS=<your-mongodb-password>
ACCESS_TOKEN_SECRET=<your-jwt-secret>
PORT=5000
```

### 4. Start the Server

```bash
npm run server
```

The server will run on [http://localhost:5000](http://localhost:5000).

---

## API Endpoints

### Authentication

- **POST /jwt**: Generate a JWT token for a user.
  - Request body: `{ "email": "user@example.com" }`
  - Response: `{ "token": "<JWT Token>" }`

### User Registration

- **POST /users**: Registers a new user with a hashed password.
  - Request body: `{ "name": "Messi", "email": "messi@example.com", "password": "asdfgh" }`

### User Login

- **GET /userLogin**: Logs in a user and checks the password. Updates last login time.
  - Query parameters: `email`, `password`
  - Response: `{ "message": "matched" | "blocked" | "Pass not matched" }`

### User Management

- **GET /users**: Fetches all users.

- **POST /blockUsers**: Blocks selected users.
  - Request body: `{ "userIds": ["userId1", "userId2"] }`

- **POST /unblockUsers**: Unblocks selected users.
  - Request body: `{ "userIds": ["userId1", "userId2"] }`

- **POST /delete**: Deletes selected users.
  - Request body: `{ "userIds": ["userId1", "userId2"] }`

### User Status

- **GET /user-status/:email**: Returns whether the user is blocked or not.
  - Params: `email`

---


## License

This project is licensed under the MIT License.

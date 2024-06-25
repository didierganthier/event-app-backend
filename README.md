# Event App Backend

This is the backend for an event app built using MongoDB, Express, and Node.js. It provides RESTful APIs for managing events and users.

## Features

- User Registration and Authentication (JWT)
- CRUD operations for events
- Middleware for authentication
- MongoDB as the database

## Directory Structure

```
event-app-backend/
├── config/
│   └── db.js
├── controllers/
│   └── eventController.js
│   └── userController.js
├── models/
│   └── Event.js
│   └── User.js
├── routes/
│   └── eventRoutes.js
│   └── userRoutes.js
├── middlewares/
│   └── authMiddleware.js
├── utils/
│   └── utils.js
├── .env
├── .gitignore
├── package.json
├── server.js
└── README.md
```

## Getting Started

### Prerequisites

- Node.js
- MongoDB

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/event-app-backend.git
    cd event-app-backend
    ```

2. Install dependencies:

    ```bash
    npm install
    ```

3. Create a `.env` file in the root directory and add the following environment variables:

    ```env
    MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
    JWT_SECRET=your_jwt_secret
    PORT=5000
    ```

4. Start the server:

    ```bash
    npm run dev
    ```

### API Endpoints

#### User Routes

- `POST /api/users/register`: Register a new user
  - Request body: `{ "name": "John Doe", "email": "john@example.com", "password": "password123" }`

- `POST /api/users/login`: Login a user and get a token
  - Request body: `{ "email": "john@example.com", "password": "password123" }`

#### Event Routes

- `POST /api/events`: Create a new event (requires authentication)
  - Request body: `{ "title": "Event Title", "description": "Event Description", "date": "2024-07-20T18:00:00Z", "location": "Event Location" }`

- `GET /api/events`: Get all events (requires authentication)

## Middleware

### Authentication Middleware

The authentication middleware (`middlewares/authMiddleware.js`) checks for a valid JWT token in the `x-auth-token` header and adds the user to the request object.

## Models

### User Model

The user model (`models/User.js`) defines the schema for user documents in MongoDB. It includes fields for `name`, `email`, `password`, and `date`. Passwords are hashed before being saved.

### Event Model

The event model (`models/Event.js`) defines the schema for event documents in MongoDB. It includes fields for `title`, `description`, `date`, `location`, `createdBy`, and `attendees`.

## Controllers

### User Controller

The user controller (`controllers/userController.js`) handles user registration and login.

### Event Controller

The event controller (`controllers/eventController.js`) handles creating and retrieving events.

## Configuration

### Database Configuration

The database configuration (`config/db.js`) connects to MongoDB using Mongoose. The connection URI is stored in the `.env` file.

## Running the Application

To run the application in development mode with auto-reloading:

```bash
npm run dev
```

To run the application in production mode:

```bash
npm start
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes.

## Acknowledgments

- [Node.js](https://nodejs.org/)
- [Express](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/)
- [Mongoose](https://mongoosejs.com/)
- [dotenv](https://www.npmjs.com/package/dotenv)
- [bcryptjs](https://www.npmjs.com/package/bcryptjs)
- [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)

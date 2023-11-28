# Authenticket

The authenticket project is a Node.js middleware designed to simplify user authentication and management for Express applications. It offers several features, including custom protected routes, rate limiting, and user management. Below is a summary of the key points from the README:

# Features:

- User Authentication: Easy registration and login with secure password hashing using bcrypt and JWT-based authentication.
- Custom Protected Routes: Middleware to secure your endpoints and ensure only authenticated users can access them.
- Custom User Schema: You can use the default user schema or create your own to fit your application's needs.

# JWT Authentication Flow:
![image](https://github.com/mrin247/Authenticket/assets/72962881/d6336a5e-6e64-4b68-9366-8244a83d1fec)


#Setup Instructions:

- Install required packages: Express, Mongoose, dotenv.
- Create an Express app.
- Configure dotenv for environment variables.
- Add `app.use(express.json())` middleware.
- Install `authenticket` and set up the middleware by connecting to MongoDB.

  ```js
  const { authocate } = require('authenticket');
  const mongoose = require('mongoose');

  mongoose
    .connect(process.env.MONGO_URI, {
      useUnifiedTopology: true,
      useNewUrlParser: true,
    })
    .then((conn) => {
      console.log(`MongoDB connected: ${conn.connection.host}`);
      authocate(app, conn, process.env.JWT_SECRET_KEY);
    })
    .catch((error) => {
      console.error(`Error: ${error.message}`);
      process.exit(1);
    });

  ```
# Usage:
```js
authocate(app, conn, process.env.JWT_SECRET_KEY, { userSchema: customUserSchema})
```

Built-in API endpoints for user authentication and management, including login, signup, update user, and get user details.
# User Schema:

You can use the default user schema provided or create a custom schema to fit your requirements.
# Custom Protected Routes:

Protect your endpoints by using the authorize middleware, ensuring only authorized users can access them.

# Future Development
- Rate Limiting
- Forget Password
- oAuth

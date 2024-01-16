### Adding custom middleware

Absolutely, let's dive into adding custom middleware for logging in your Express application. This will enhance your understanding of middleware and give you hands-on experience.

### Step 1: Create a Logging Middleware
In your `src` directory, create a file named `loggerMiddleware.ts`. This file will contain your custom logging middleware. Write the basic structure of the middleware:

```typescript
// src/loggerMiddleware.ts

export function loggerMiddleware(req, res, next) {
  // Your logging logic goes here

  // Call the next middleware in the stack
  next();
}
```

### Step 2: Implement Basic Logging
Inside the `loggerMiddleware.ts`, implement basic logging logic. For simplicity, let's log the HTTP method and the requested URL. Update your middleware:

```typescript
// src/loggerMiddleware.ts

export function loggerMiddleware(req, res, next) {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);

  // Call the next middleware in the stack
  next();
}
```

### Step 3: Integrate Middleware with Express
Open your `server.ts` file and import the logging middleware. Add it to your Express application to ensure it's executed for every incoming request. Update your `server.ts`:

```typescript
// src/server.ts
import express from 'express';
import { loggerMiddleware } from './loggerMiddleware';

const app = express();
const port = 3000;

// Use the logging middleware for all routes
app.use(loggerMiddleware);

app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

### Step 4: Test Your Application
Run your application using `npm start` and open your browser to [http://localhost:3000](http://localhost:3000). Check your terminal where the server is running, and you should see logs for each incoming request.

### Step 5: Enhance Logging (Optional)
Feel free to enhance your logging middleware further. You can include additional information such as request headers, query parameters, or even customize the log format. Modify the `loggerMiddleware.ts` file to suit your needs.

### Notes
- Middleware in Express follows a chain-of-responsibility pattern, where each middleware function can modify the request or response and pass control to the next middleware in the stack.
- The `next()` function is crucial in middleware. It passes control to the next middleware in the stack. If it's not called, the request won't proceed beyond the current middleware.
- Custom middleware can be added to specific routes or applied globally, as demonstrated in this example.

Now you have a basic logging middleware integrated into your Express application. This experience should give you a good foundation for working with middleware in Express. Feel free to explore more advanced middleware concepts as you continue developing your application.
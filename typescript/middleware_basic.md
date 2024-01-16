### Error middleware, interfaces, types, and enums
#### Step 1: Explore TypeScript Interfaces

Let's create a TypeScript interface for our custom error handling middleware. Create a new file `interfaces.ts`:

```typescript
// src/interfaces.ts
export interface CustomError extends Error {
  statusCode?: number;
}
```

Update the error handling middleware in `index.ts`:

```typescript
// src/index.ts
// ... (existing code)

import { CustomError } from './interfaces';

// Error Handling Middleware
app.use((err: CustomError, req: Request, res: Response, next: NextFunction) => {
  console.error(err.stack);
  const statusCode = err.statusCode || 500;
  res.status(statusCode).send(`Error: ${err.message}`);
});

// ... (remaining code)
```

### Step 2: Enum and Types Exploration

Explore enums and types by creating a file `enums.ts`:

```typescript
// src/enums.ts
export enum HttpStatusCode {
  OK = 200,
  NOT_FOUND = 404,
  INTERNAL_SERVER_ERROR = 500,
}

export type UserRole = 'admin' | 'user';
```

You can then use these enums and types in your application as needed.

This tutorial provides a foundation for building a TypeScript Express server with essential features. Feel free to experiment further with TypeScript interfaces, enums, and types to enhance your server according to your project requirements.

### Step 3: Triggering an error
Certainly! Let's update the code snippet to focus on the `/trigger-error` route, assuming you're testing it using Postman:

```typescript
// src/index.ts
import express, { Request, Response, NextFunction } from 'express';
import { CustomError } from './interfaces';

const app = express();
const port = 3000;

// Error-Inducing Route
app.get('/trigger-error', (req: Request, res: Response, next: NextFunction) => {
  const error: CustomError = new Error('This is a custom error');
  error.statusCode = 418; // I'm a teapot (just for fun!)
  next(error);
});

// Error Handling Middleware
app.use((err: CustomError, req: Request, res: Response, next: NextFunction) => {
  console.error(err.stack);
  const statusCode = err.statusCode || 500;
  res.status(statusCode).send(`Error: ${err.message}`);
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

With this setup, when you send a GET request to `http://localhost:3000/trigger-error` using Postman, you'll trigger the custom error handling middleware, and Postman will display the response with the custom error message and status code. This allows you to easily test and observe the behavior of your error handling route in a controlled manner.
### Adding express
Certainly! Let's modify the tutorial to include the optional sections as essential parts of the setup.

### Step 1: Install ts-node-dev
Install `ts-node-dev` as a development dependency. Run the following command:

```bash
npm install --save-dev ts-node-dev
```

### Step 2: Update Package.json Scripts
Update your `package.json` file to include a script for running the TypeScript files with `ts-node-dev`. Open your `package.json` file and modify the `"scripts"` section like this:

```json
"scripts": {
  "start": "ts-node-dev src/index.ts"
}
```

### Step 3: Install Express
Install Express as a dependency:

```bash
npm install express
```

### Step 4: Create a Simple Express Server
Create a file `server.ts` in your `src` directory with the following content:

```typescript
import express from 'express';

const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

### Step 5: Update tsconfig.json
Update your `tsconfig.json` file to include both `index.ts` and `server.ts`. Update the `"include"` property:

```json
"include": ["src/index.ts", "src/server.ts"],
```

### Step 6: Run Your Project
Now, you can run your project with hot-reloading using the following command:

```bash
npm start
```

This will start your TypeScript application with automatic recompilation and hot-reloading. Any changes you make to your TypeScript files will trigger the server to restart automatically.

### Notes
- The `ts-node-dev` tool is great for development but should not be used in production. It's specifically designed for a faster development feedback loop.
- Hot-reloading significantly improves the development experience by eliminating the need to manually restart your server every time you make changes.
- With Express included, you now have a foundation to build a server on top of this setup.

Now, you have an essential development-friendly environment with hot-reloading and an Express server. You can continue to build and enhance your project based on this foundation.
### Creating a typescript repo

Certainly! Let's walk through the process of initializing a basic TypeScript repository step by step. We'll set `strict` to `false` for now, and I'll provide notes on what setting it to `true` would achieve.

### Step 1: Create a New Directory
Create a new directory for your TypeScript project. You can do this using the following command in your terminal or command prompt:

```bash
mkdir my-typescript-project
cd my-typescript-project
```

### Step 2: Initialize a New npm Package
Run the following command to initialize a new npm package. This will create a `package.json` file where you can manage your project dependencies.

```bash
npm init -y
```

### Step 3: Install TypeScript
Install TypeScript as a development dependency using the following command:

```bash
npm install --save-dev typescript
```

### Step 4: Create a tsconfig.json File
Create a `tsconfig.json` file in the root of your project. This file is used to configure TypeScript settings. For now, set `strict` to `false`. Your `tsconfig.json` file might look like this:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": false
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

### Step 5: Create a Source Directory
Create a `src` directory in your project to store your TypeScript source files.

```bash
mkdir src
```

### Step 6: Write a Simple TypeScript File
Create a simple TypeScript file inside the `src` directory. For example, create a file named `index.ts` with the following content:

```typescript
function greet(name: string) {
  console.log("Hello, " + name + "!");
}

greet("World");
```

### Step 7: Compile TypeScript to JavaScript
Compile your TypeScript code to JavaScript using the TypeScript compiler. Run the following command:

```bash
npx tsc
```

This will create a `dist` directory with the compiled JavaScript files.

### Notes on Setting `strict` to `true`
When you set `strict` to `true` in your `tsconfig.json`, TypeScript enables a set of strict type-checking options. This includes options like `noImplicitAny`, `strictNullChecks`, `strictFunctionTypes`, and more. Enabling strict typing helps catch potential issues in your code during development, ensuring a higher level of type safety.

To set `strict` to `true`, update the `"strict"` property in your `tsconfig.json` file:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

Feel free to experiment with strict typing as your project evolves and you become more comfortable with TypeScript.
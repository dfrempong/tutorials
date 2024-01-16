### Turn on strict typing
Certainly! Let's dive into enabling strict typing in TypeScript and exploring the concepts of types and interfaces.

### Enabling Strict Typing in TypeScript

In the previous sections, we initialized our TypeScript project with `strict` set to `false`. Now, let's explore the benefits of turning it on.

### Step 1: Update tsconfig.json

Open your `tsconfig.json` file and set the `"strict"` property to `true`:

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

### Understanding Strict Typing

Enabling strict typing in TypeScript introduces a set of options that enhance type safety in your code. Let's briefly explore some key concepts:

1. **noImplicitAny**: Previously, TypeScript allowed variables to have an implicit `any` type when their type was not specified. With strict typing, this is no longer allowed. You need to explicitly define the type of your variables.

   ```typescript
   // Before
   let myVariable; // Implicitly 'any'

   // After
   let myVariable: string; // Explicitly 'string'
   ```

2. **strictNullChecks**: TypeScript becomes more strict about handling `null` and `undefined`. You need to explicitly check for these values or use the nullable type (`string | null`, for example).

   ```typescript
   // Before
   let myString: string = null; // Allowed

   // After
   let myString: string | null = null; // Explicitly allowing null
   ```

3. **noImplicitThis**: Helps avoid issues with the `this` keyword by ensuring that it has an explicit type.

   ```typescript
   // Before
   function logMessage() {
     console.log(this); // 'this' implicitly has an 'any' type
   }

   // After
   function logMessage(this: Window) {
     console.log(this); // Explicitly specifying 'this' type
   }
   ```

### Updating Existing Code

Enabling strict typing might lead to changes in your existing code. TypeScript will now catch potential issues, promoting a more robust codebase. Review your code for implicit `any` types, handle nullability explicitly, and ensure proper `this` typing.

### Benefits of Strict Typing

- **Early Error Detection**: TypeScript catches potential errors during development, reducing runtime issues.
- **Enhanced Code Readability**: Explicit types make code more readable and self-documenting.
- **Better Refactoring Support**: The compiler provides better support for refactoring, ensuring type consistency.

Feel free to experiment with these concepts in your codebase and adapt them based on your project's needs. In the next section, we'll delve deeper into creating and using TypeScript interfaces to define complex data structures.
# Code Guidelines

## Relative vs. Absolute Imports

Always prefer absolute imports.  There are path aliases defined in `src/frontend/tsconfig.json` and `src/backend/tsconfig.json`. For example, if you wanted to write an absolute import for the file at 

```
src/backend/lib/middleware/auth.js
```

you would write

```
@/backend/lib/middleware/auth.js
```

Remember to add the `.js` suffix at the end.

## error handling
For error handling, instead of throwing exceptions, prefer using the `Result` type defined in `src/common/types.ts`. For functions that can fail, the return type should be a `Result`, and the function should return either a `Success` or a `Failure`.

## General code quality guidelines
- Avoid having excessively long functions. Split up long functions into multiple functions where it makes sense. Each function should do one thing.
- Split up a React component into sub-components when it makes sense.
- Avoid sharing state. Make as many things private as possible. This will make code much easier to reason about.
- Have no side effects, if possible. All functions should be deterministic when possible, accepting inputs and returning outputs, and avoiding modifying any shared state in between. 

## Guidance on reusable subcomponents.
Please create reusable subcomponents where it would help to reduce code duplication. If you create a subcomponent, please put it in its own directory. For example, if you create a subcomponent `Bar.tsx` for a component `Foo.tsx`, please put it at `Foo/Bar.tsx`.

## Typescript coding guidelines
- Always type your variables, function parameters, and return types explicitly. Avoid using `any`.
- Use types instead of interfaces.

Bad:

```typescript
interface User {
  id: number;
  name: string;
}
```

Good:

```typescript
type User = {
  id: number;
  name: string;
};
```

## General code guidelines

- Keep your code modular.
- Each React component should only do one thing.
- Use descriptive variable names, avoid one or two letter variable names.

If finding yourself defining the same function or type over and over again, refactor it out into a common file.

For utility functions:
- If the function will be used only on the backend, add it to `src/backend/util.ts`.
- If it will be used only on the frontend, add it to `src/frontend/util.ts`.
- If it will be used on both, add it to `src/common/util.ts`.

Similarly, for types:
- If the type will be used only on the backend, add it to `src/backend/types.ts`.
- If it will be used only on the frontend, add it to `src/frontend/types.ts`.
- If it will be used on both, add it to `src/common/types.ts`.
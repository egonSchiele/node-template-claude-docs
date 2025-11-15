## API routes
All API routes live in `src/backend/routes/api`. Routing happens with the `express-file-routing` package. Each API route exports one or more functions named after HTTP verbs like get, post, put, and del (for DELETE). So, for example, if you wanted to create a new route like

```
POST /api/users
```

you would create a file `src/backend/routes/api/users.ts` and export a function named `post`:

```typescript
import { Request, Response } from "express";
export const post = async (req: Request, res: Response) => { ... }
```

Make sure to import `Request` and `Response` from the `express` package.

To export a wildcard route, use a default export:

```typescript
export default async (req, res) => { ... }
```

See `src/backend/routes/api/moods.ts` for an example. 

Some route examples:

```
/routes/index.ts → /
/routes/posts/index.ts → /posts
/routes/posts/[id].ts → /posts/:id # dynamic parameter
/routes/users.ts → /users
```


All route functions should return a value instead of sending it to the client using `res.json`. The return value should be a `Result` type, which can be either a `Success` or a `Failure`. These types are defined in the file `"@/common/types.js"`. You can use the `success` and `failure` convenience functions to create these types. For an example of how to return a value, see src/backend/routes/api/batches.ts.

Please specify return types for all API endpoints so the generated apiClient.ts file can use them. For example, if you have a `get` route, you can specify its return type by having the file export a variable named `getType`, which should be a string. `post` routes should export a `postType` string, and so on.

All return values should be typed, and all types are stored in the `src/common/apiTypes/` directory. All input bodies should be validated using Zod, and the Zod schemas should be stored in the same file in the API types directory. You should also create a type out of the Zod schema so we can use that type on the frontend. See `src/common/apiTypes/moods.ts` for an example.

Also update `src/common/apiTypes.ts` to re-export all types in files you create under `src/common/apiTypes`.

Anytime you add an API route, a function to use that route is automatically generated in `src/frontend/generated/apiClient.ts`. When you're fetching that API route, please use the generated function. If you don't see the function generated, run `pnpm build` to update the file.
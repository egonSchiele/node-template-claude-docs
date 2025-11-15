### Middleware

You can add middleware by exporting an array of Express request handlers from your route file:

```typescript
import { isLoggedIn } from "@/backend/lib/middleware/auth.js";

export const get = [
isLoggedIn,
  async (req, res) => { ... }
]
```

All middleware lives in `src/backend/lib/middleware/`. See `src/backend/lib/middleware/auth.js` for an example.
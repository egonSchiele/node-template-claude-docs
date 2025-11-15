## styling
This repo uses a custom component library called `egon-ui` for styling. Prefer using the components exported from this package. Find the docs for these components here:
https://raw.githubusercontent.com/egonSchiele/ui/refs/heads/main/DOCS_FOR_CLAUDE.md

For other ad-hoc styling, follow these guidelines:

For smaller CSS changes, you can add them inline using Tailwind. For larger CSS styling, or CSS styling you think could be reused, please add alongside CSS files and then import them. For example, to add styling for `Posts.tsx`, you might create `posts.css` and then import it into Posts.tsx like this:

```typescript
import "./posts.css";
```

## Using Tailwind

When styling with Tailwind, you can use the custom colors in src/frontend/pages/ui.css, and the custom spacing defined in src/frontend/pages/globals.css. For example, don't say `p-3`, say `p-xs`. Similarly you can use xs, sm, md, lg, xl, 2xl, 3xl, and 4xl.

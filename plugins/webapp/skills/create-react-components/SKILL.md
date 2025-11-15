---
name: creating react components
description: Guidance on creating React components in the webapp.
---

!IMPORTANT: This repo uses a custom component library called `egon-ui` for styling. Always prefer using the components exported from this package when possible. Find the docs for these components here:
https://raw.githubusercontent.com/egonSchiele/ui/refs/heads/main/DOCS_FOR_CLAUDE.md

## Guidance on reusable subcomponents.
Please create reusable subcomponents where it would help to reduce code duplication. If you create a subcomponent for a page, please put it in its own directory. For example, if you create a subcomponent `Bar.tsx` for a component `src/frontend/pages/Foo.tsx`, please put it at `src/frontend/pages/Foo/Bar.tsx`.

If you create a component that will be used across many pages, put it in the `src/frontend/components/` directory.

Each React component should only do one thing.

## Error states

Every React component for a top-level page should have an `error` useState property that can be used to display errors to the user:

```typescript
const [error, setError] = useState<string | null>(null);
```

Errors should always be shown using the `<Banner>` component from `egon-ui`:

```typescript
{error && <Banner style="error">{error}</Banner>}
```

When making API calls, make sure to catch errors and set the error state appropriately. For example:

```typescript
  const result = await apiClient.someEndpoint();
  if (result.success) {
    // handle success
  } else {
    setError(result.error.message);
  }
```
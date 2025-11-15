## Guidance on creating a CRUD UI

For instance, if you are creating a CRUD UI for a resource "Moods", please use the following structure:

### Create
- html file: pages/moods/new.html
- react component: src/frontend/pages/Moods/New.tsx
- route: `post` function in src/backend/routes/api/moods.ts

### Read
### To read a single item
- html file: pages/moods/show.html
- react component: src/frontend/pages/Moods/Show.tsx
- route: `get` function in src/backend/routes/api/moods/[id].ts

### To read all items
- html file: pages/moods/index.html
- react component: src/frontend/pages/Moods/Index.tsx
- route: `get` function in src/backend/routes/api/moods.ts

### Update
- html file: pages/moods/edit.html
- react component: src/frontend/pages/Moods/Edit.tsx
- route: `put` function in src/backend/routes/api/moods/[id].ts

### Delete
- route: `del` function in src/backend/routes/api/moods/[id].ts

The create and update endpoints should both use the same form. Shared components like the form should be placed in `src/frontend/components/moods/`.

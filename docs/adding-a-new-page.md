## to add a new page
All the entry points are html files under `pages/`. To add a new entry point, you'll need to add a new HTML page here, add a corresponding .tsx file under `src/frontend/pages/`, add a new entry in `vite.config.ts` under `build.outDir.rollupOptions.input`, and if needed, add a new path alias in `src/backend/lib/router/entrypoints.ts`.

Note that when you link to a new page, you should not use the `.html` extension. For example, if you created a new page `foo.html` and added it to the `entrypoints.ts` file, and you wanted to add a link to that page, you would link to `/foo`, not `/foo.html`.

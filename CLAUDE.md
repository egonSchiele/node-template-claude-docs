This is a web app written in React, TypeScript, and Node. Kysely is used as the ORM, and Vite is used to build assets. All the frontend code lives in `src/frontend`, while the backend lives in `src/backend`.

## Links to important resources
This doc will help you make changes to this codebase. *Always* read this:
https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/code-guidelines.md

Here are docs for specific topics. If you are tasked with working on a topic, fetch and read its related documentation:

- adding a new page: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/adding-a-new-page.md
- creating an API route, input validation on API routes: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/api-routes.md
- creating a CRUD UI and backend: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/creating-a-crud-ui.md
- database changes such as migrations: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/database-changes.md
- styling, frontend components, react components: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/styling.md
- middleware: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/middleware.md
- writing scripts: https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/writing-scripts.md

https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/adding-a-new-page.md
https://raw.githubusercontent.com/egonSchiele/node-template-claude-docs/refs/heads/main/docs/adding-a-new-page.md

## notable files and folders
- `src/frontend/`: Contains all the frontend code, including React components, pages, and styles.
- `src/backend/`: Contains all the backend code, including API routes, database access, and middleware.
- `src/backend/routes/api/`: Contains all the API routes for the backend.
- `src/common/`: Contains code that is shared between the frontend and backend, such as types and utility functions.

## Testing changes
You can test your changes by running the following command:

```bash
pnpm run build
```

## CHANGELOG.md
Whenever you add a new feature, please add it to the top of CHANGELOG.md along with the timestamp. For example:

```
## Nov 9 2025
Started changelog
```

Please keep updates concise. It is okay to sacrifice grammar for conciseness.

## Writing tests
For backend code that doesn't touch the database, please write tests using vitest. Test files should be placed alongside the source files. See src/common/util.test.ts for an example.

## Troubleshooting
If you get errors related to apiClient.ts, you may need to recompile it. Run `pnpm run compile-client` to do so.
## database changes
In order to make a database change, you'll need to add a few things:
1. Add a migration in `db/migrations`.
1. Add seeds in `db/seeds`.
2. Add or modify types in `src/backend/db/types.ts`.
3. Add finders as needed. You can look at `src/backend/db/mood.ts` for an example.


### migrations
Migrations are done with Kysely. To run migrations, use the following commands:

```bash
pnpm run kysely migrate make <migration-name>
pnpm run kysely migrate list
pnpm run kysely migrate up
pnpm run kysely migrate down
```

When creating a new table, if the table has a primary key, please add auto-increment to that field.

Prefer using soft instead of hard deletes.

If you create a JSONB column on a table, note that you will need to JSON.stringify the data before inserting it into the table. Look for a convenience function like this one or create it yourself:

```ts
import { Kysely, RawBuilder, sql } from "kysely";

export function kyjson<T>(value: T): RawBuilder<T> {
  return sql`CAST(${JSON.stringify(value)} AS JSONB)`;
}
```
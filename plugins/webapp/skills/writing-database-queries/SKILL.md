---
name: writing database queries
description: Guidance on adding writing database queries using Kysely.
---

## n+1 queries

When writing database queries, please be mindful of n+1 query problems. Always prefer using joins or `IN` queries to fetch related data in bulk instead of making multiple queries in a loop.

## transactions

When performing multiple related database operations, please use transactions to ensure data integrity. You can use Kysely's transaction support like this:

```ts
import { Kysely } from "kysely";
import { db } from "@/backend/db/client";
await db.transaction().execute(async (trx: Kysely<any>) => {
  // perform database operations using trx
});
```

## jsonb

If you create a JSONB column on a table, note that you will need to JSON.stringify the data before inserting it into the table. Look for a convenience function like this one or create it yourself:

```ts
import { Kysely, RawBuilder, sql } from "kysely";

export function kyjson<T>(value: T): RawBuilder<T> {
  return sql`CAST(${JSON.stringify(value)} AS JSONB)`;
}
```
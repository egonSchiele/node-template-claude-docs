## Input validation
For input validation, you can use the `zod` package. This package allows you to define schemas for your input data and validate it easily. Here's an example of how to use it:

```typescript
import { z } from "zod";
import { Request, Response } from "express";
export const post = async (req: Request, res: Response) => {
  const schema = z.object({
    name: z.string().min(1),
    age: z.number().int().positive(),
  });

    const validatedData = schema.safeParse(req.body);
  if (!validatedData.success) {
    return res.status(400).json({
      error: "Invalid input",
      details: validatedData.error.issues,
    });
  }
  const { name, age } = validatedData.data;
  // Now you can use name and age safely
};
```
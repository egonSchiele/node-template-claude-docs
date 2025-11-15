## Writing scripts
All scripts are, by definition, backend scripts, so they should go in the `src/backend/scripts` folder. In here, you can import files from the backend and common directories. Please remember to use the aliases `@/backend` and `@/common`. Then to run the scripts, you just need to build using `pnpm run build` and then run the script. For example, the example script `src/backend/scripts/test.ts` can be run like this once the code has been built:

```bash
node dist/backend/scripts/test.js
```
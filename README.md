To setup:

```bash
yarn

yarn run codegen
```

It should correctly generate a `graphql.ts` file under `src/generated/graphql.ts`.

If `imported.ts` was to include a syntax error, for example not starting the template literal properly:

```typescript
import { buildSchema } from 'graphql';

export const schema = buildSchema(
  type Query {
    hello: String
  }`
  );

``` 

The error message becomes:

```
  ✔ Parse configuration
  ❯ Generate outputs
    ❯ Generate src/generated/graphql.ts
      ✖ Load GraphQL schemas
        → All found files for glob expression "index.ts" are not valid or empty, please check it and try again!
        Load GraphQL documents
        Generate


 Found 1 error

  ✖ src/generated/graphql.ts
    Error: All found files for glob expression "index.ts" are not valid or empty, please check it and try again!


Something went wrong
error Command failed with exit code 1.

```

If there is instead a syntax error in `index.ts` the error is correctly returned from the command:

```
  ✔ Parse configuration
  ❯ Generate outputs
    ❯ Generate src/generated/graphql.ts
      ✖ Load GraphQL schemas
        → Unexpected token (2:17)
        Load GraphQL documents
        Generate


 Found 1 error

  ✖ src/generated/graphql.ts
    SyntaxError: Unexpected token (2:17)



```

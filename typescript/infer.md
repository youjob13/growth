`infer` keyword can be used only in conditional types.
infer allows to define variable inside constraint.

```typescript
type Flatten<Type> = Type extends Array<infer ItemType> ? ItemType : Type;

type PromiseType<Type> = Type extends Promise<infer PromiseValue> ? PromiseValue : never; 
```

```typescript
type MyParameters<Type extends ((...args: any[]) => unknown)> = Type extends ((...args: infer Args) => unknown) ? Args : never;
```

Template Literal Types

```typescript
type ExtractWords<Sentence> = Sentence extends `${infer Word} ${infer Rest}` ? [Word, ...ExtractWords<Rest>] : [Sentence];
```

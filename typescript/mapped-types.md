# When to use?
We can use mapped types when we don't want to repeat ourself and when type needs to be based on the another type. WHEN WE WANT TO TRANSFORM EXISTING TYPE FOR ALL KEYS IMMEDIATELY.
Mapped types build on the syntax for index signatures, which are used to declare the types of properties which have not been declared ahead of time.

[Example playground](https://www.typescriptlang.org/play/?ssl=50&ssc=83&pln=50&pc=91#code/JYOwLgpgTgZghgYwgAgBIHsoGcUG8C+AUIWAJ4AOKA8iADakBC66tWAgiACYbYRbIBeZLkLJkAbQDWEUgC5kWMFFABzALryARs1oQ4IZAB80mHAG5C+C8kIJ0IRcjsgYmALZZ5NekxbsuPDj8QiJinBC08koArhAANKLIUOicIDLy8KzxlhYkFNTkYMD2WABitHAqWAA8ACr5AHyCwoniAArJlFBkyKDI0qToMMj1lBrI2ix6IBZWxGSUyKV6YNFQfM2hyJxwUJIAsikQ8gAUAJSCTQBu6MCc1shpAO4AqjhQHUPAuqcXAte3e45UR5RbLOCrdZUQrFBzNaFFErlSo1cGQvgNXIAeixyAAShA3OgrhsAOTrOCcez0UnICFKYCaaKQfgwZJuOnIBYQUn8cidaBFPiglAAYQpkH2zLgml0dUam0SAFoKVS6KQJJ8uj0+gMhiN8uNRhB2gLuqQ1LNrCLkAAZdAIaScNgIOzRcCKsSq6kau7yRTKEAqB7e9WPOBuY4KBlBq0g7nIF50B1Ol1uj1CcUrCBSsAyuX2x0QZ2u9DusCYxJias1wg4-GE4lk9Aw+xwWi0+nKJks5Bs9AcuBc-K85D8luC4DChOi+wIdaQeWUJohVpawW+gx64bGtRKgD88mNpon5stwJsCf2cFImggb2gnt6nH9MeDiRAEYgh+jgffYkqb95BAaI3DvKA40vfJE3eZpZxAecIEXa9b3vd5MVreZoIAcSQyBsCXCAVxaGsT21Td+hkfVjTpfgAAMVCQgASXBRTgchgDzWhgAALwgaoA1UZAADJkHXc0GnwOjxnOS4DUoMiNzUC9CFAfD4CQMToCwewSOrT9I1fP8HgAxjgNA8CTOQWgHQhWEjNUWZ42g204B40g2m03ShFwsB8JqTzsHsTEgA)

```typescript
type OnlyBoolsAndHorses = {
  [key: string]: boolean | Horse;
};
 
const conforms: OnlyBoolsAndHorses = {
  del: true,
  rodney: false,
};
```

### FILTRATION based on keys / value
```typescript
type StringFields<T> = {
  [K in keyof T as T[K] extends string ? K : never]: T[K];
};
```

### Mapping Modifiers
There are two additional modifiers which can be applied during mapping: readonly and ? which affect mutability and optionality respectively.
You can remove or add these modifiers by prefixing with - or +. If you don’t add a prefix, then + is assumed.

### Key Remapping via as
In TypeScript 4.1 and onwards, you can re-map keys in mapped types with an as clause in a mapped type:

```typescript
type MappedTypeWithNewProperties<Type> = {
    [Properties in keyof Type as NewKeyType]: Type[Properties]
}

type Getters<Type> = {
    [Property in keyof Type as `get${Capitalize<string & Property>}`]: () => Type[Property]
};
 
interface Person {
    name: string;
    age: number;
    location: string;
}
 
type LazyPerson = Getters<Person>;
```

### Practical Task
Implement custom Deep Readonly Optional Utility Type.

Solution:
```typescript
type Primitive = string | number | boolean | bigint | symbol | undefined | null;

type MyDeepReadonlyOptional<T> = T extends Primitive
  ? T
  : T extends Array<infer U>
    ? Array<MyDeepReadonlyOptional<U>>
    : { readonly [P in keyof T]?: MyDeepReadonlyOptional<T[P]> };


type Config = {
    name: string;
    age: number;
    address?: { street: string }
}
type OptionalConfig = MyDeepReadonlyOptional<Config>;
```

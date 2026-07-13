# When to use?
We can use mapped types when we don't want to repeat ourself and when type needs to be based on the another type.
Mapped types build on the syntax for index signatures, which are used to declare the types of properties which have not been declared ahead of time.

[Example playground](https://www.typescriptlang.org/play/?#code/JYOwLgpgTgZghgYwgAgBIHsoGcUG8C+AUIWAJ4AOKA8iADakBC66tWAgiACYbYRbIBeZLkLJkAbQDWEUgC5kWMFFABzALryARs1oQ4IZAB80mHAG5C+C8kIJ0IRcjsgYmALZZ5NekxbsuPDj8QiJinBC08koArhAANKLIUOicIDLy8KzxlmZAA)

```typescript
type OnlyBoolsAndHorses = {
  [key: string]: boolean | Horse;
};
 
const conforms: OnlyBoolsAndHorses = {
  del: true,
  rodney: false,
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

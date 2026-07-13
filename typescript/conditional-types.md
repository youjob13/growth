#When to use?
We use conditional types when we want to describe relation between INPUTS and OUTPUTS types.

[Example playground](https://www.typescriptlang.org/play/?#code/MYGwhgzhAECCB2BLAtmE0DeAoa0DmA9gBQCU2uuO0AvgNxbVZaiQwAiBe0ApgB4Au3eABMYCFGkxUA7gQIAzUlKqNGWfgE8ADt2gA5AK7JuAJ0TBoAXmgcufQSLFJU6APzR4RgEanoALmgIfjN4PHpNHWgAZWDEUMR5RG5hK2gAJW48AFFeLR4BIVE4Z0l3T2QfE39A2ND6JgjdADFwfgcAHgAVAD5UzvyHIrB4DQBtAF1od07R8srJgM76aCwAelXoHOCwYH4YAgN+aH4AC11uEG5jeCPGgDp1bV0YqusWsDahdqCQvAnu+jraAAGW4YAAbtwYKddI1oGgCPBuA84YZkKl3p94O05qYAQ0ntBMQ4AExdJ69aydQn2QpiEwmMAadpxeS+ACSgmQvXcnKu1WpOnChJeJKsxKEZJ+cT+426j0iaLFlgl8DJuJM8qAA)
```typescript
class Animal {
  go(){
  };
}

class Dog extends Animal {
  woof() {
  }
}

type Numeric = Dog extends Animal ? number : string;
type Stringified = RegExp extends Animal ? number : string;
```

### Infeting with conditional types

```typescript
type Flatten<Type> = Type extends Array<infer Item> ? Item : Type;
```

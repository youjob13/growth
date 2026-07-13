#When to use?
We use conditional types when we want to describe relation between INPUTS and OUTPUTS types.

(Example playground)[https://www.typescriptlang.org/play/?#code/MYGwhgzhAECCB2BLAtmE0DeAoa0DmA9gBQCU2uuO0AvgNxbVZaiQwAiBe0ApgB4Au3eABMYCFGkxUA7gQIAzUlIrQqjRln4BPAA7doAOQCuybgCdEwaAF5oHLn0EixSVOgD80eCYBG56ABc0BD8FvB49Np60ADKoYjhiPKI3MI20ABK3HgAorw6PAJConCukp7eyH5mgcHx4bRAA]
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

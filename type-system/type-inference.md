# Type inference

In TypeScript, it's not required to provide type annotations when initializing a variable. The compiler can deduce (infer) the type by looking at the type and shape of the initial value.

### variable initial value

#### let vs const
`let` variable can vary during program execution therefore the type is extended to `string`.
```ts
let firstname = 'Marcus' // inferred as string
```

`const` variable which is **primitive** cannot change and that is why the type is narrowed to a literal type. This rule applies only to primitives because content of objects can change.
```ts
const lastnamme = 'Rashford' // inferred as Rashfor
```

#### no initial value
TypeScript takes into account only the line where the variable is declared. Other lines, where you might assign some attributes are ignored.
```ts
let something; // any
something = 123; // any
```

#### object literal
When object literal is provided as initial value then the inferred type is also object literal. On one hand JavaScript's native object is a dictionary which allows to assign any string key to it. On the other hand, there might be no "predefined" attributes known upfront. As a result, we can access a field with an array notation, but it's not the case for dot notation.
```ts
const obj = {} // inferred as {}
obj['hello'] = 'world' // ok
obj.hello = 'world' // hello doesn not exist on type {}, 
```

#### function return value
TypeScript can infer function argument types from their default values. Function return type can also be deduced based on the expression type.
```ts
const func = ( a = 1 ) => a + 1; // (a?: number) => number
const greet = (name) => `Hello ${name}!`; // (name: any) => string
```

#### compiler flags
If we don't want to open our codebase to nasty bugs, following flags must be always enabled:
 - `--noImplicitAny` will complain about each line where TS cannot infer anything better than any. Usually that's either lines like `let foo;` or funcction parameters left alone.
 - `--noImplicitThis` places where we use the `this` reference within a function and TS has no way to infer what it is precisely, leaving it as `any`

### limitations
todo
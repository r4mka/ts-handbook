# Type assertion

**Type casting** (type conversion) converts **a value** from one type to another type. For example a ```string``` value such as ```"1"``` can be converted to a ```number``` value ```1``` using ```parseInt``` function.

**Type assertion** is a **compile-time** feature which allows you to instruct TypeScript compiler to teat **a value type** as a different type than it originally was. **It doesn't impact the type of the value at runtime** since in contrast to **type casting** it doesn't transform or mutate the value.

Assertion is helpful when we have some third party function which returns ```any``` but we know for sure that the type of the value is something else and we want to keep our type system hermetic and have all the fancy autocomplete features.

Type assertion is very powerful tool and must be used with care.

###syntax
```ts
let fruit: any = 'apple';
(fruit as string).toUpperCase();

let count: any = 123;
(<number>count).toFixed();
```
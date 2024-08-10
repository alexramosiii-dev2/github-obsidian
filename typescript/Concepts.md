## How do I use TypeScript?
A common way to use TypeScript is to use the official TypeScript compiler, which transpiles TypeScript code into JavaScript.

`npm install typescript --save-dev`

The compiler is installed in the node_modules directory and can be run with: npx tsc.

`npx tsc`


### Available Types
- `boolean`
- `number`
- `string`
- `bigint`
- `symbol`
- `any` // must be avoided
- `unknown` // variable declaration with unknown type to be used on
- `never` // throws an error whenever it is defined.
- `undefined`
- `null`

### Implicit vs Explicit Assignment
- Explicit
```js
let firstName: string = "Dylan"; //single
let familyNames: string[] = []; //array mutable
let originalNames: readonly string[] = []; //array immutable
```

- Implicit
```js
let firstName = "Dylan";
```

Array
let names = string[] = []; //
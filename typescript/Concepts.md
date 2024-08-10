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

### Implicit vs Explicit Assignment
- Explicit
```js
let firstName: string = "Dylan";
```

- Implicit
```js
let firstName = "Dylan";
```

## How do I use TypeScript?
A common way to use TypeScript is to use the official TypeScript compiler, which transpiles TypeScript code into JavaScript.

`npm install typescript --save-dev`

The compiler is installed in the node_modules directory and can be run with: npx tsc.

`npx tsc`


### Available Types
- boolean
- number
- string
- bigint
- symbol

### Implicit vs Explicit Assignment
- Explicit
	```javascript
	let firstName: string = "Dylan";`
	```

- Implicit
	`let firstName = "Dylan";`

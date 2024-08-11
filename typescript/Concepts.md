## How do I use TypeScript?
A common way to use TypeScript is to use the official TypeScript compiler, which transpiles TypeScript code into JavaScript.

`npm install typescript --save-dev`

The compiler is installed in the node_modules directory and can be run with: npx tsc.

`npx tsc`
```dataview
LIST
```


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

### Array
```js
let names1 = string[] = []; //mutable array
let names2 = readonly string[] = []; //immutable array

names1.push("John"); //no error
names2.push("Joe"); //error
```

### Tuple
- array with a pre-defined length **(immutable)** and types for each index.
- always make tuple readonly. 
```js
let firstTuple: readonly [number, string, boolean];
firstTuple = [55, "Jane", false]; // error on mistmatch

firstTuple[0]; //55
firstTuple[1]; //Jane
firstTuple[2]; //false

const [firstValue, secondValue, thirdValue] = firstTuple; //destructure
```

- named tuples, only for documentation, no change in accessing the value.
```js
const secondTuple: [x: number, y: number] = [12, 24];

secondTuple["x"]; // ERROR
secondTuple.x; // ERROR

const [x, y] = secondTuple; //destructure. correct
const [y, x] = secondTuple; // y = 12, x = 24;
```

### Typescript Objects
```js
const car: { type: string, model: string, year: number } =
{  
  type: "Toyota",  
  model: "Corolla",  
  year: 2009  
};
```

optional properties
```js
const car: { type: string, mileage?: number } = { // no error  
  type: "Toyota"  
};

car.mileage = 2000; // still works
```

Index signature
```js
// makes a property pattern that is any string key with number value.
const nameAgeMap: { [index: string]: number } = {};
nameAgeMap.Jack = 25; // no error  
nameAgeMap.Mark = "Fifty"; // error
```

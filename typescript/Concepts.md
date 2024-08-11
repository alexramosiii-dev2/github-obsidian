### How do I use TypeScript?
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
```ts
let firstName: string = "Dylan"; //single
let familyNames: string[] = []; //array mutable
let originalNames: readonly string[] = []; //array immutable
```

- Implicit
```ts
let firstName = "Dylan";
```

### Array
```ts
let names1 = string[] = []; //mutable array
let names2 = readonly string[] = []; //immutable array

names1.push("John"); //no error
names2.push("Joe"); //error
```

### Tuple
- array with a pre-defined length **(immutable)** and types for each index.
- always make tuple readonly. 
```ts
let firstTuple: readonly [number, string, boolean];
firstTuple = [55, "Jane", false]; // error on mistmatch

firstTuple[0]; //55
firstTuple[1]; //Jane
firstTuple[2]; //false

const [firstValue, secondValue, thirdValue] = firstTuple; //destructure
```

- named tuples, only for documentation, no change in accessing the value.
```ts
const secondTuple: [x: number, y: number] = [12, 24];

secondTuple["x"]; // ERROR
secondTuple.x; // ERROR

const [x, y] = secondTuple; //destructure. correct
const [y, x] = secondTuple; // y = 12, x = 24;
```

### Typescript Objects
```ts
const car: { type: string, model: string, year: number } =
{  
  type: "Toyota",  
  model: "Corolla",  
  year: 2009  
};
```

optional properties
```ts
const car: { type: string, mileage?: number } = { // no error  
  type: "Toyota"  
};

car.mileage = 2000; // still works
```

Index signature
```ts
// makes a property pattern that is any string key with number value.
const nameAgeMap: { [index: string]: number } = {};
nameAgeMap.Jack = 25; // no error  
nameAgeMap.Mark = "Fifty"; // error
```

Enums 

```ts
// special "class" that represents a group of constants

//STRING (1 of 2)
enum CardinalDirections{  
  North,  
  East,  
  South,  
  West  
}

console.log(CardinalDirections.North;); // logs 0;
//NUMERIC (2 of 2)
```
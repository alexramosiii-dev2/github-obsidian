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
- `any` - must be avoided \*\*defaults when no type is specified
- `unknown` - variable declaration with unknown type to be used on
- `never` - throws an error whenever it is defined.
- `undefined`
- `null`
- `void` - for function return

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


//NUMERIC (1 of 2) - default
enum CardinalDirections{  
  North,  
  East,  
  South,  
  West  
}

console.log(CardinalDirections.North;); // logs 0;


//NUMERIC - Initialized
enum CardinalDirections {  
  North = 1,  
  East,  
  South,  
  West  
}
console.log(CardinalDirections.North;); // logs 1;
console.log(CardinalDirections.West;); // logs 4;

//assign unique number values for each enum value
enum StatusCodes {  
  NotFound = 404,  
  Success = 200,  
  Accepted = 202,  
  BadRequest = 400  
}

//STRING (2 of 2)
enum CardinalDirections {  
  North = 'North',  
  East = "East",  
  South = "South",  
  West = "West"  
};

//Technically, you can mix and match string and numeric enum values, but it is recommended not to do so.

```

Aliases and Interfaces
	-Aliases and interfaces are similar but interfaces are only for objects while aliases can do both objects and primitive types.
	-Interfaces can be extended/inherited
```ts
//TypeScript allows types to be defined separately from the variables that use them.

//ALIAS - primitives + objects
type CarYear = number; 
type CarType = string;  
type CarModel = string;
type Car = {  
  year: CarYear,  
  type: CarType,  
  model: CarModel  
}


//INTERFACE - for objects only
interface Rectangle {  
  height: number,  
  width: number  
}

//INTERFACE EXTENSION
interface Shape {  
  color: string,
}  
  
interface Rectangle extends Shape {
  sides: number,  
}

const Rect1: Rectangle = {
	color: "Red",
	sides: 4,
}

```

Union types or "either of the two"
```ts
let color: number | string;
let color = 0000000;
let color = "Black";
```

Functions
```ts
//default and optional parameters
function pow(value: number = 10, exponent?: number) {  
  return value ** exponent;
}

//kagulu na pero balamu destructuring yamu.
function op({ dividend, divisor }:{ dividend: number, divisor: number })
{  
  return dividend / divisor;  
}

//Rest parameters using spread operator
function add(a: number, ...rest: number[]) {  
  return a + rest.reduce((p, c) => p + c, 0);  
}

//Alias for arrow function
type Negate = (value: number) => number;
```

Casting
```ts
let x: unknown = 'hello';  
console.log((x as string).length);
console.log((<string>x).length);// would not work in TSX (JSX twin)

let x: unknown = 4;
console.log((x as string).length);// undefined.


//To override type errors that TypeScript may throw when casting, first cast to `unknown`, then to the target type.
let x = 'hello';  
console.log(((x as unknown) as number).length);
// x is not actually a number so this will return undefined
```

Classes
```ts
class Person {  
	 name: string;
	 private age: number;
	 private readonly race: string; //can't be change once set
	 // declares the property skincolor
	 public constructor(private skincolor: string) {};
}

const person = new Person();  
person.name = "Jane";
person.age = 56 //ERROR

const person2 = new Person("brown");
person2.skincolor; // brown

```

Implement a interface
```ts
interface Shape {  getArea: () => number; }  

//can implement multiple
class Rectangle implements Shape {
	//interfaces makes contract for the class to include all its methods
	public getArea(): number { }  
}  

//can only extend onces
class Square extends Rectangle {  
  // inherits getArea() from rectangle
}
```

Abstract Classes
```ts
//defines methods with no body
//abstract members do not need body.
abstract class Shape {
	public abstract getArea(): number;
	public getSides(): number {
		return;
	};
}

class Rectangle extends Shape {
	public getArea() {
		return;
	}
	// it is optional to include all abstract class abstract members
}

const rect1 = new Rectangle();
rect1.getSides();
```
# Typescript

| Section                                                       | Description                         |
| ------------------------------------------------------------- | ----------------------------------- |
| [Types](#types)                                               | About Types                         |
| [Built-in Types](#built-in-types)                             | About Built-in Types                |
| [Union Type](#union-type)                                     | About Union Type                    |
| [ENUMS](#enums)                                               | About Enums                         |
| [Typed Parameter in Functions](#typed-parameter-in-functions) | About Typed Parameter in Functions. |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |
| [](#)                                                         | About .                             |

### TYPES:

```typescript
function add(x: number, y: number) {
  return x + y;
}

add(1, 2); // allowed
add(2, "2"); // not allowed
```

#### Built-in Types:

- string
- number
- boolean
- array
- undefined
- null
- any
- void

#### Defining Types:

let `let name:string = 'imam'`

### Union Type:

```typescript
let name: string | undefined | null;
```

here name could be either string or undefined or null

### ENUMS:

```typescript
enum things {
  goOut,
  sayHello,
}

let whattodo = things.goOut; // 0
```

### Typed Parameter in Functions:

```typescript
function hello(id: number, name: string) {
  console.log(id, name);
}
```

### Return Values and Types:

```typescript
function add(x: number, y: number): number {
  return x + y;
}
```

#### Using Custom Types

```typescript
type ProductType = {
  name: string;
  age: number;
};

function returnMatchData(items: ProductType[]): ProductType | undefined {
  return items.find((item) => item.age === 26);
}
```

here find method could either return the item or could not so undefined is also added;

### Async functions:

```ts
async function getProduct(): Promise<Products[]> {
  const response: Response = await fetch(url);
  const products: Products[] = await response.json();
  return products;
}
```

### Optional Parameter:

```ts
function sayHello(id: number, name?: string): Human {
  return {
    id,
    name,
  };
}

sayHello(123, "imam"); //{id:123,name:'imam'}
sayHello(123); // {id:123, name:undefined}
```

### Default Parameter:

```ts
function sayHello(id: number, name?: string = "imam"): Human {
  return {
    id,
    name,
  };
}

sayHello(123, "syed"); //{id:123,name:'syed'}
sayHello(123); // {id:123, name:imam}
```

### Interface:

```ts
interface Product {
  id: number;
  name: string;
  expiry?: number; // optional
  placeOrder(id: number): boolean; // need to implement function placeOrder which has args id and return type as boolean.
}
```

### Interface Vs Types:

Interface: Can be used to represent the shape of an object like data structure.

Type: Can be used to represent primitive types and object like data strcuture.

#### Interface:

```ts
interface Product {
  id: number;
  name: string;
  expiry?: number; // optional
}
```

#### Type:

```ts
type ProductType =
  | string
  | {
      name: string;
      age: number;
    };
```

Here Type is more flexible you can either give string value or the object value.

#### When to use what?

If you have the senario where you can expect the value to be primitive like string or object then go for type if not interface.

#### Example Scenarios

- Simple Object Structure:

Use interface when defining a straightforward object shape that might need extension.

```ts
interface User {
  name: string;
  age: number;
}
```

- Union and Intersection Types:

Use type to define complex types, such as unions or intersections.
typescript

```ts
type Status = "active" | "inactive";
type Point = { x: number } & { y: number };
```

- Extending Types:

Use interface if you need to extend the type.

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}
```

- Primitive or Complex Mappings:

Use type for creating aliases for primitives or for mapped types.

```ts
type ID = number | string;
type ReadOnly<T> = {
  readonly [P in keyof T]: T[P];
};
```

#### Conclusion

Use interface when you need to define an object type, especially if it might be extended or merged.
Use type when you need to define more complex types like unions, intersections, or use type aliases for primitives and other non-object types.

### Generics:

- When you want your function, classes or interface to be used with different types then we need to use Generics.

#### Generics in Functions:

```ts
function sendMeWhatISend<T>(args: T): T {
  return args;
}

sendMeWhatISend<number>(11); // 11
sendMeWhatISend<string>("imam"); // imam
```

#### Generics in Interface:

```ts
interface Model<T> {
  items: T[] | undefined,
  getItems: () => Promise<T[]>,
}
```



# What is the use of the keyof keyword in TypeScript? Provide an example.

The keyof keyword in TypeScript is a powerful operator that helps you work with object keys in a type-safe way. Let's break it down simply.

What Does keyof Do?
keyof creates a union type of all known, public property names (keys) of an object type.

In simpler terms: if you have an object type, keyof gives you all its keys as types.

Basic Example
typescript
interface Person {
  name: string;
  age: number;
  location: string;
}

type PersonKeys = keyof Person; 
Equivalent to: "name" | "age" | "location"
Here, PersonKeys becomes a type that can only be "name", "age", or "location".

Why Is This Useful?
Type Safety: Ensures you only use valid property names

Auto-completion: Your IDE can suggest available keys

Refactoring: If you change your interface, TypeScript will flag invalid keys

Practical Example
typescript
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}

const person: Person = {
  name: "John",
  age: 30,
  location: "New York"
};

const name = getProperty(person, "name"); 
const email = getProperty(person, "email");
Common Use Cases
Type-safe property access: Like in the example above

Mapped types: When creating new types based on existing ones

Generic utilities: Building reusable functions that work with object properties

Remember
keyof works with types, not runtime values

It only includes public, known properties

Very useful for creating type-safe utilities

The keyof operator is a small but powerful part of TypeScript that helps catch errors early and makes your code more maintainable.






# What is type inference in TypeScript? Why is it helpful?

Type inference is TypeScript's ability to automatically determine (or "guess") the types of variables, expressions, and function return values when you don't explicitly specify them. This feature makes TypeScript both powerful and convenient to use.

How Type Inference Works
TypeScript looks at how you initialize variables and use values, then figures out the appropriate types:

typescript
let age = 25;          
let name = "Alice";    
let isActive = true;   

const numbers = [1, 2, 3]; 
Why Type Inference is Helpful
Less Typing: You don't need to write types everywhere

typescript
let count: number = 0;


let count = 0;
Maintains Type Safety: Even without explicit types, you get the same protection

typescript
let score = 100;
score = "high"; 
Works with Complex Objects:

typescript
const user = {
  name: "Bob",
  age: 30
};

## Smart Function Return Types:

typescript
function add(a: number, b: number) {
  return a + b; 
}
Contextual Typing (for callbacks):

typescript
const names = ["Alice", "Bob", "Charlie"];
names.map(name => name.toUpperCase()); 
When You Might Want Explicit Types
While inference is powerful, sometimes being explicit helps:

For complex function signatures

When declaring variables without initialization

For documentation purposes

When the inferred type isn't specific enough

typescript
let items: string[]; 
items = ["apples", "oranges"];
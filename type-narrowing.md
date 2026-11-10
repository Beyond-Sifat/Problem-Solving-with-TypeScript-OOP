# Type Narrowing in TypeScript: Making Types Safer

## Introduction

Type Narrowing is an important feature in TypeScript that allows developers to determine a variable's specific type within a particular condition or code block. It helps us work safely with union types and reduces unexpected runtime errors.

## 1. Using typeof

The `typeof` operator checks the type of primitive values, such as strings, numbers, and booleans.

```typescript
function processValue(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }

  return value.toFixed(2);
}
```

TypeScript understands that `value` is a string inside the first condition and a number afterward.

## 2. Using instanceof

The `instanceof` operator checks whether an object belongs to a particular class.

```typescript
class Dog {
  bark(): string {
    return "Woof!";
  }
}

function makeSound(animal: Dog | Date): string {
  if (animal instanceof Dog) {
    return animal.bark();
  }

  return animal.toDateString();
}
```

This helps distinguish between different class instances.

## 3. Using the in Operator

The `in` operator checks whether an object contains a specific property.

```typescript
type Admin = { name: string; permissions: string[] };
type Customer = { name: string; email: string };

function getDetails(user: Admin | Customer): string {
  if ("permissions" in user) {
    return user.permissions.join(", ");
  }

  return user.email;
}
```

TypeScript narrows the object based on the property that exists.

## Conclusion

Type Narrowing makes TypeScript applications safer and easier to maintain. By using `typeof`, `instanceof`, and the `in` operator, developers can handle different data types confidently without relying on unsafe type assertions.

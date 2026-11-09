# What is Type Narrowing in TypeScript?

## Introduction

TypeScript's type system is at its most powerful when a variable can hold more than one type. A function parameter typed as `string | number`, for example, cannot safely call `.toUpperCase()` or `.toFixed()` directly, because the compiler cannot know which type it is at any given line. Type narrowing is the process of writing runtime checks that let TypeScript progressively "narrow" a broad or union type down to a more specific one within a block of code, so that type-specific operations become safe and fully type-checked.

## How It Works

The compiler watches conditional checks like `typeof`, `instanceof`, and `in`, and uses them to refine the type inside each branch. This is called control flow analysis.

**`typeof`** works well for primitives:

```ts
function describe(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toFixed(2);
}
```

**`instanceof`** narrows between classes:

```ts
class Dog { bark(): string { return "Woof"; } }
class Cat { meow(): string { return "Meow"; } }

function speak(animal: Dog | Cat): string {
  if (animal instanceof Dog) {
    return animal.bark();
  }
  return animal.meow();
}
```

**`in`** checks for a property's existence, which is useful for narrowing between object shapes that don't share a discriminant:

```ts
interface Car { drive(): void; }
interface Boat { sail(): void; }

function operate(vehicle: Car | Boat): void {
  if ("drive" in vehicle) {
    vehicle.drive();
  } else {
    vehicle.sail();
  }
}
```

## Conclusion

Type narrowing lets developers write flexible, union-typed functions without giving up compile-time safety. Instead of casting or using `any` to silence the compiler, `typeof`, `instanceof`, and `in` let TypeScript prove, branch by branch, exactly which type is in play. Mastering narrowing is essential for writing idiomatic TypeScript that stays both expressive and safe.

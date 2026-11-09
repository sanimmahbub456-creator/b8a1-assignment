# Access Modifiers in TypeScript OOP

## Introduction

Object-Oriented Programming relies on encapsulation: hiding internal details of a class so that outside code can only interact with it through a defined interface. TypeScript brings this discipline to JavaScript through four access modifiers — `public`, `private`, `protected`, and `readonly` — which are enforced at compile time, even though they disappear from the compiled JavaScript output.

## How Each Modifier Works

**`public`** is the default. Any property or method without an explicit modifier can be read or called from anywhere, inside or outside the class.

**`private`** restricts a member to the class that declares it. It cannot be accessed from an instance, nor from a subclass.

```ts
class Account {
  private balance: number;
  constructor(balance: number) { this.balance = balance; }
  getBalance(): number { return this.balance; }
}

const acc = new Account(100);
// acc.balance; // Error: 'balance' is private
```

**`protected`** behaves like `private`, except subclasses are also allowed access. This is useful when a base class needs to expose internal state to its children without exposing it publicly.

```ts
class Employee {
  protected name: string;
  constructor(name: string) { this.name = name; }
}

class Manager extends Employee {
  describe(): string {
    return `Manager: ${this.name}`; // allowed, name is protected
  }
}
```

**`readonly`** is orthogonal to the three above; it can be combined with any of them. A `readonly` property can only be assigned once, either at declaration or inside the constructor.

```ts
class Point {
  readonly x: number;
  constructor(x: number) { this.x = x; }
}
```

## Conclusion

Together these modifiers let a class author decide precisely what is part of the public contract and what is an implementation detail. `public` invites outside use, `private` locks a detail to one class, `protected` shares it down an inheritance chain, and `readonly` prevents mutation after initialization. Using them deliberately produces classes that are harder to misuse and easier to refactor safely.

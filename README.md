# B8A1 — Problem Solving with TypeScript & OOP

## Assignment Overview

This repository contains my solutions for the B8A1 assignment, covering core TypeScript concepts from Modules 1–3: basic types, optional/default/rest parameters, readonly tuples, interfaces, type narrowing, generics, Promises, and Object-Oriented Programming.

- **`solutions.ts`** — all 8 coding problems (functions, interfaces, generics, classes, and an async Promise-based function), each with explicit parameter and return types.
- **Blog posts** — two technically detailed write-ups on TypeScript concepts:
  - [Type Narrowing in TypeScript](./type-narrowing.md)
  - [Access Modifiers in TypeScript OOP](./access-modifiers.md)

## Problems Covered in `solutions.ts`

1. `multiplyValue` — optional parameter with a default multiplier
2. `processInput` — union types and `typeof` narrowing
3. `formatCoordinate` — readonly tuple parameter
4. `concatenateArrays` — generics with rest parameters
5. `Course` interface + `getPopularCourses` — filtering without mutation
6. `pluckValues` — generics with the `keyof` constraint
7. `Employee` / `Manager` — inheritance with `protected`/`private` modifiers
8. `validateAgeAsync` — a `Promise<string>`-returning async function

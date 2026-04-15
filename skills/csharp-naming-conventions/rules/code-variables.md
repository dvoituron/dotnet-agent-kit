---
title: Variable Conventions
impact: HIGH
impactDescription: Poor variable practices lead to bugs and reduced readability
tags: code, variables, var, access-modifiers
---

## Variables

- Write only **one declaration per line**.
- Use only an **explicit name** without abbreviation.
- Use **implicit typing** (`var`) for local variables when the type is obvious from the right side of the assignment.

**Correct:**

```csharp
var fullname = "Scott Guthrie";
var age = 27;
```

- **Don't use `var`** when the type is not apparent from the right side. A variable type is considered clear if it's a `new` operator or an explicit cast.
- **Don't use `dynamic`**.
- Use the correct **access modifier** (`private`, `public`, `protected`, `internal`) with `virtual` if possible.
- **Do not** provide instance fields that are `public` or `protected`. Provide properties instead.
- You can use **insignificant names** `i, j, k, x, y, z` with local loops or very short lambda expressions.
- **Initialize local variables as soon as possible**: `var name = string.Empty`.
- Use `string.Empty` and not `""` to represent an empty string.

**Incorrect:**

```csharp
string x = "";
public int counter;
dynamic value = GetSomething();
```

**Correct:**

```csharp
var name = string.Empty;
public int Counter { get; set; }
var value = GetSomething();  // only when type is obvious
```

Reference: [Microsoft Field Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/field)

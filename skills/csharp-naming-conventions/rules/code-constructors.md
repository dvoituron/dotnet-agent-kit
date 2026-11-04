---
title: Prefer Traditional Constructors
impact: MEDIUM
impactDescription: Explicit constructor declarations keep initialization separate from the class declaration
tags: code, constructors, primary-constructors, initialization
---

## Prefer Traditional Constructors for Classes

Declare constructors explicitly inside the class body. Do not use primary constructors for classes.
This convention does not apply to positional records.

**Correct:**

```csharp
public class Manager
{
    public Manager(int initialData)
    {
        InitialData = initialData;
    }

    public int InitialData { get; }
}
```

**Incorrect:**

```csharp
public class Manager(int initialData)
{
    public int InitialData { get; } = initialData;
}
```
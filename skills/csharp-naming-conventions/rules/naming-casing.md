---
title: Pascal Case and Camel Case
impact: CRITICAL
impactDescription: Inconsistent casing makes code harder to read and maintain
tags: naming, casing, pascal, camel
---

## Pascal Case and Camel Case

Use two casing practices consistently: `PascalCasing` and `camelCasing`.

1. **Pascal Case** — Use when naming a `namespace`, `class`, `record`, `struct`, method, property, event, enum, or constant.
2. **Camel Case** — Use when naming `private` or `internal` fields (prefixed with `_`), local variables, and parameters.

**Correct:**

```csharp
public class DataService
{
    private IWorkerQueue _workerQueue;

    public bool IsValid;

    public event Action EventProcessing;

    public int Add(int first, int second)
    {
        return first + second;
    }
}
```

**Complete reference table:**

| Item              | Case   | Example                              |
| ----------------- | ------ | ------------------------------------ |
| Namespace         | Pascal | `System.File.Directory`              |
| Class             | Pascal | `AppDomain`                          |
| Class Exception   | Pascal | `WebException` (suffix `Exception`)  |
| Interface         | Pascal | `IDisposable` (prefix `I`)           |
| Event             | Pascal | `ValueChange`                        |
| Enum Type         | Pascal | `ErrorLevel`                         |
| Enum Value        | Pascal | `FatalError`                         |
| Variable Private  | Camel  | `_lastName` (prefix `_`)             |
| Variable Local    | Camel  | `lastName`                           |
| Read Only         | Pascal | `RedColor`                           |
| Constant          | UPPER  | `BLUE`                               |
| Method            | Pascal | `ToString()`                         |
| Property          | Pascal | `BackColor`                          |
| Parameter         | Camel  | `typeName`                           |

Reference: [CSharp Coding Guidelines](https://csharpcodingguidelines.com/)

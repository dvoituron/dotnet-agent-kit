---
title: Blazor Methods and Properties
impact: MEDIUM-HIGH
impactDescription: Inconsistent property ordering and nullable handling causes warnings and confusion
tags: blazor, properties, inject, parameter, nullable
---

## Methods and Properties

### Member Order in Blazor Components

1. Private **variables** (using `readonly` if possible) and **constants**
2. The **[Inject]** properties
3. **[Parameter]** properties
4. **Public** methods and properties
5. **Internal** and **Protected** methods/properties
6. **Private** methods/properties

### Attributes Placement

Place attributes (`Inject`, `Parameter`, ...) **above** the property:

```csharp
[Inject]
public IJSRuntime JsRuntime { get; set; } = default!;
```

### Nullable Handling

Since projects accept nullables, define non-null variables and properties with `default!` to avoid compile warnings:

```csharp
public IConnectionManager Connection { get; set; } = default!;
```

For properties that accept null values, use `?`:

```csharp
public string? Name { get; set; }
public int? Count { get; set; }
public object? Data { get; set; }
```

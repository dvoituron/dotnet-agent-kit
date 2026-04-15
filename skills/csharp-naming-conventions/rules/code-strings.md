---
title: String Data Type
impact: MEDIUM
impactDescription: Inefficient string handling impacts performance in loops
tags: code, string, interpolation, stringbuilder
---

## String Data Type

Use **string interpolation** to concatenate short strings:

```csharp
string displayName = $"{nameList[n].LastName}, {nameList[n].FirstName}";
```

To append strings in loops, especially with large amounts of text, use a **StringBuilder**:

```csharp
var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
    manyPhrases.Append(phrase);
}
```

**Incorrect:**

```csharp
var result = "";
for (var i = 0; i < 10000; i++)
{
    result += phrase;  // Creates a new string every iteration
}
```

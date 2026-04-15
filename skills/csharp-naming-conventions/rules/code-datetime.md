---
title: DateTimeProvider
impact: HIGH
impactDescription: Direct DateTime.Now usage makes unit tests non-deterministic
tags: code, datetime, testing, mock
---

## DateTime

Always use **DateTimeProvider** (and not `DateTime`) to allow unit testing and date mocks.

**Incorrect:**

```csharp
int trimester = (DateTime.Now.Month - 1) / 3 + 1;
```

**Correct:**

```csharp
int trimester = (DateTimeProvider.Today.Month - 1) / 3 + 1;
```

Reference: [UnitTest DateTime](https://dvoituron.com/2020/01/22/UnitTest-DateTime)

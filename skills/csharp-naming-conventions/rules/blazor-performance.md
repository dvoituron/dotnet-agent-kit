---
title: Blazor Performance
impact: MEDIUM-HIGH
impactDescription: Poor rendering patterns cause slow, unresponsive Blazor applications
tags: blazor, performance, rendering, optimization
---

## Blazor Performance

Reference: [Blazor Performance](https://docs.microsoft.com/en-us/aspnet/core/blazor/performance)

### Avoid Unnecessary Rendering
1. Ensure child component parameters are of **primitive immutable types**.
2. Override [ShouldRender](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.components.componentbase.shouldrender) when appropriate.

### Create Lightweight Components
- Avoid thousands of **component instances** — inline child components into their parents when needed.

### Minimize Parameters
- Don't receive too many parameters. Bundle them in a custom class:

```csharp
[Parameter]
public GridOptions? Options { get; set; }
```

### Fix Cascading Parameters

```xml
<CascadingValue Value="this" IsFixed="true">
    <SomeOtherComponents>
</CascadingValue>
```

### Events
- Don't trigger events too rapidly (e.g., `onmousemove`, `onscroll`).
- **Avoid rerendering** after handling events without state changes (by default `StateHasChanged` is called automatically).

### Other Guidelines
- Avoid attribute splatting with **CaptureUnmatchedValues**.
- Avoid recreating **delegates** for repeated elements.
- Optimize **JavaScript** interop speed — minimize calls between .NET and JS.

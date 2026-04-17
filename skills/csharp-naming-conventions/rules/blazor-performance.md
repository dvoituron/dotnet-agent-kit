---
title: Blazor Performance
impact: MEDIUM-HIGH
impactDescription: Poor rendering patterns cause slow, unresponsive Blazor applications
tags: blazor, performance, rendering, optimization, parameters
---

## Blazor Performance

Reference: [Blazor Performance](https://docs.microsoft.com/en-us/aspnet/core/blazor/performance)

### Avoid Overriding OnParametersSet

Do not override `OnParametersSetAsync` or `OnParametersSet` for initialization logic. These methods are called **every time a parameter changes**, not just once. 
Place initialization code in `OnInitializedAsync` or `OnAfterRenderAsync` instead.

```csharp
// Incorrect: called on every parameter change
protected override async Task OnParametersSetAsync()
{
    _data = await DataService.LoadAsync();
}

// Correct: called only once during initialization
protected override async Task OnInitializedAsync()
{
    _data = await DataService.LoadAsync();
}
```

Reference: [ASP.NET Core Blazor component lifecycle](https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle)

### Use SetParametersAsync instead of OnParametersSet

Prefer overriding `SetParametersAsync` over `OnParametersSet` or `OnParametersSetAsync` when you need to react to parameter changes. 
`OnParametersSet` is called **every time any parameter changes**, with no way to know which specific parameter was updated.
`SetParametersAsync` gives you direct access to the incoming `ParameterView`, allowing you to check exactly which parameters changed before applying logic or triggering a re-render.

```csharp
// Incorrect: no way to know which parameter changed
protected override void OnParametersSet()
{
    _data = ComputeExpensiveResult(Value);
}

// Correct: inspect which parameters actually changed
public override async Task SetParametersAsync(ParameterView parameters)
{
    if (parameters.TryGetValue<int>(nameof(Value), out var newValue) && newValue != Value)
    {
        _data = ComputeExpensiveResult(newValue);
    }

    await base.SetParametersAsync(parameters);
}
```

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

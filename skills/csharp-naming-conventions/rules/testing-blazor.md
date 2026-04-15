---
title: Blazor Unit Tests with bUnit
impact: HIGH
impactDescription: Untested Blazor components break silently on refactoring
tags: testing, blazor, bunit, verifier
---

## Blazor Unit Tests

All Blazor unit tests use [bUnit](https://bunit.dev/) and [Verifier.Blazor](https://github.com/VerifyTests/Verify.Blazor).

With bUnit, you can:
- Setup and define components under tests using C# or Razor syntax
- Verify outcomes using semantic HTML comparer
- Interact with and inspect components as well as trigger event handlers
- Pass parameters, cascading values and inject services
- Mock `IJSRuntime`, Blazor authentication and authorization

### Example with a Simple Parameter

```csharp
[Fact]
public void MyButton_Basic_Width()
{
    // Arrange
    using var ctx = new Bunit.TestContext();

    // Act
    var button = ctx.RenderComponent<MyButton>(parameters =>
    {
        parameters.Add(p => p.Width, "100px");
    });

    // Assert
    button.MarkupMatches(@"<fluent-button appearance=""neutral"" style=""width: 100px;"" />");
}
```

### Example Using Verifier

```csharp
[UsesVerify]
public class MyToolbarTests
{
    [Fact]
    public Task MyToolbar_Render_TwoButtons()
    {
        // Arrange
        using var ctx = new Bunit.TestContext();

        // Act
        var toolbar = ctx.RenderComponent<MyToolbar>(parameters =>
        {
            parameters.AddChildContent<MyButton>(item =>
            {
                item.AddChildContent("Button 1");
            });
            parameters.AddChildContent<MyButton>(item =>
            {
                item.AddChildContent("Button 2");
            });
        });

        // Assert
        return Verifier.Verify(toolbar);
    }
}
```

This generates a `.received.html` file compared to `.verified.html`:

```html
<!-- MyToolbar_Render_TwoButtons.verified.html -->
<div class="stack-horizontal">
    <div class="my-toolbar">
        <fluent-button appearance="neutral">Button 1</fluent-button>
        <fluent-button appearance="neutral">Button 2</fluent-button>
    </div>
</div>
```

> Using **Verifier**, when a test fails, Visual Studio automatically opens the Diff Compare Tool.
> Disable with the environment variable `DiffEngine_Disabled=True`.

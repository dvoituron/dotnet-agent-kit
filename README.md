# csharp-agent-kit

A collection of skills for AI coding agents working with C# / .NET / Blazor projects.
Skills are packaged instructions and best practices that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

See this [documentation](https://dvoituron.com/naming-conventions/) for more details.

## Available Skills

### csharp-naming-conventions

C# and .NET naming conventions and best practices containing 22+ rules across
6 categories, prioritized by impact.

**Use when:**
- Writing new C# / .NET / Blazor code
- Reviewing or refactoring existing C# code
- Naming classes, methods, variables, properties, or parameters
- Formatting and laying out source files
- Writing or reviewing unit tests (xUnit, bUnit)
- Building Blazor components and pages

**Categories covered:**
- Naming & Casing (Critical)
- Code Layout & Formatting (High)
- Code Patterns (High)
- Unit Testing (High)
- Blazor Conventions (Medium-High)

## Installation

### GitHub CLI

1. Install the [WinGet Package Manage](https://github.com/microsoft/winget-cli) if you haven't already.
2. Install or update the [GitHub CLI](https://github.com/cli/cli) to version 2.90 or more:
   - `winget install --id GitHub.cli`
   - `winget upgrade --id GitHub.cli`
3. In your repo folder, run this command:
   ```bash
   gh skill install dvoituron/dotnet-agent-kit
   ```

   You can then run the `gh skill update` command to get the latest version.

### Manually

Copy the `skills/csharp-naming-conventions` folder into your agent's skill directory.
Refer to your agent's documentation for the exact location.

## Usage

Skills are automatically available once installed. The agent will use them when
relevant tasks are detected.

**Examples:**
```
Review my C# code for naming convention issues
```
```
Create a new Blazor component following best practices
```
```
Write unit tests for my service class
```

## Skill Structure

Each skill contains:
- `SKILL.md` - Instructions for the agent (triggers activation)
- `rules/` - Individual rule files organized by category
- `metadata.json` - Version and metadata
- `README.md` - Human-readable documentation

```
skills/csharp-naming-conventions/
├── SKILL.md
├── metadata.json
├── README.md
└── rules/
    ├── _sections.md
    ├── naming-*.md       # Naming and casing rules
    ├── layout-*.md       # Code layout rules
    ├── code-*.md         # Code pattern rules
    ├── testing-*.md      # Unit testing rules
    └── blazor-*.md       # Blazor convention rules
```

## Compatibility

Works with Claude Code, GitHub Copilot, Gemini CLI, and other Agent
Skills-compatible tools.

## References

- [CSharp Coding Guidelines](https://csharpcodingguidelines.com/)
- [Microsoft Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- [Unit Testing Best Practices](https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)
- [Blazor Components](https://docs.microsoft.com/en-us/aspnet/core/blazor/components)

## Contributing

Contributions are welcome. To add or update a rule:

1. Create or edit a rule file in `skills/csharp-naming-conventions/rules/`
2. Follow the existing frontmatter format (`title`, `impact`, `tags`)
3. Include correct and incorrect code examples
4. Update `SKILL.md` quick reference if adding a new rule
5. Submit a pull request

## License

MIT

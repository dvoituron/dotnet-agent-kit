---
title: Code Coverage
impact: MEDIUM
impactDescription: Low code coverage allows regressions to slip through
tags: testing, coverage, coverlet, reportgenerator
---

## Code Coverage

Code coverage measures the amount of code run by unit tests — lines, branches, or methods. Use **Coverlet** and **ReportGenerator**.

### 1. Requirements

Include NuGet packages in your unit tests project:

```xml
<PackageReference Include="coverlet.msbuild" Version="3.1.2" />
<PackageReference Include="coverlet.collector" Version="3.1.2" />
```

### 2. Install Tools

```bash
dotnet tool install --global coverlet.console --version 3.1.2
dotnet tool install --global dotnet-reportgenerator-globaltool --version 5.1.10
```

Verify with:
```bash
dotnet tool list --global
```

### 3. Run Code Coverage

```bash
dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=cobertura
```

### 4. Generate HTML Report

```bash
reportgenerator "-reports:**/*.cobertura.xml" "-targetdir:C:\Temp\Coverage" -reporttypes:HtmlInline_AzurePipelines
```

Reference: [Unit Testing Code Coverage](https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-code-coverage)

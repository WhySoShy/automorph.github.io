---
title: Installation
---

## Installing AutoMorph
> [!IMPORTANT]
> Your project must support [.NET Standard 2.0](https://learn.microsoft.com/en-us/dotnet/standard/net-standard?tabs=net-standard-2-0)

### Install via NuGet
Run the following command in your `CLI`:
```
dotnet add package AutoMorph
```

### Installation via IDE (Visual Studio / Rider)
1. Open the **NuGet Package Manager** (`Tools` > `NuGet Package Manager` > `Manage NuGet Packages for Solution`)
2. Search for `AutoMorph`
3. Click **Install**


### Manual Installation
Add AutoMorph to your `.csproj` file manually:

```xml
<ItemGroup>
    <PackageReference Include="AutoMorph" Version="LATEST_VERSION" />
</ItemGroup>
```
> [!IMPORTANT]
> Replace `LATEST_VERSION` to the desired version that is compatible with your project.

### Getting started
When you've installed AutoMorph in your project, you can begin with the [Getting Started](getting-started.md) that gives you a small sample of the generator.
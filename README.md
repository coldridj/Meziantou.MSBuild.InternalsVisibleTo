# Meziantou.MSBuild.InternalsVisibleTo

> The code is an adaptation of https://github.com/thomaslevesque/InternalsVisibleTo.MSBuild to fit my needs. It adds the notion of suffix and the default suffix.

[![NuGet version](https://img.shields.io/nuget/v/Meziantou.MSBuild.InternalsVisibleTo.svg?logo=nuget)](https://www.nuget.org/packages/Meziantou.MSBuild.InternalsVisibleTo)

Allow to declare `InternalsVisibleTo` in the csproj file, rather than declaring them to an `AssemblyInfo.cs` file.

## How to use

1. Install the `Meziantou.MSBuild.InternalsVisibleTo` NuGet package.
2. Edit your csproj file:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  
  <ItemGroup>
    <InternalsVisibleTo Include="CustomTest1" /> <!-- [assembly: InternalsVisibleTo("CustomTest1")] -->
    <InternalsVisibleTo Include="CustomTest2, PublicKey=abc" /> <!-- [assembly: InternalsVisibleTo("CustomTest2, PublicKey=abc")] -->
    <InternalsVisibleTo Include="$(AssemblyName).Custom" /> <!-- [assembly: InternalsVisibleTo("ClassLibrary1.Custom")] -->

    <InternalsVisibleToSuffix Include=".Tests" /> <!-- [assembly: InternalsVisibleTo("ClassLibrary1.Tests")] -->
    <InternalsVisibleToSuffix Include=".FunctionalTests" /> <!-- [assembly: InternalsVisibleTo("ClassLibrary1.FunctionalTests")] -->
  </ItemGroup>

</Project>
```

This will generate the appropriate `InternalsVisibleTo` attributes for your assembly.

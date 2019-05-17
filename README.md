# InternalsVisibleTo.MSBuild

Enables declaring `InternalsVisibleTo` items in a .NET project file, rather than declaring them to an AssemblyInfo.cs file.

## How to use

1. Install the `InternalsVisibleTo.MSBuild` NuGet package.
2. Edit your csproj file and add `<InternalsVisibleTo>` items in your project for each assembly that should have access
to the internals of the current project:

```xml
  <ItemGroup>
    <InternalsVisibleTo Include="$(AssemblyName).UnitTests" />
    <InternalsVisibleTo Include="SomeOtherAssembly" />
    <InternalsVisibleTo Include="StronglyNamedAssembly, PublicKey=0123....." />
  </ItemGroup>
```

This will generate the appropriate `InternalsVisibleTo` attributes for your assembly.

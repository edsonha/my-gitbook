# Project Note

1. Add projects \(csproj file\) to solution file \(Code: **dotnet sln add ${File Folder}**\)
2. Add project dependencies \(between different projects\) \(Code: **dotnet add reference ${File Folder path}**\)

```text
<ItemGroup>
    <ProjectReference Include="..\Domain\Domain.csproj" />
</ItemGroup>
```




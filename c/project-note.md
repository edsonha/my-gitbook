# Project Note

1. Add projects \(csproj file\) to solution file \(Code: **dotnet sln add ${File Folder}**\)
2. Add project dependencies \(between different projects\) \(Code: **dotnet add reference ${File Folder path}**\)

```text
<ItemGroup>
    <ProjectReference Include="..\Domain\Domain.csproj" />
</ItemGroup>
```

3. Now our API project needs to be hosted and dot net comes with a Web server called Kestrel that's going to host our API application and that's responsible for running it and serving it over 5000 on localhost.


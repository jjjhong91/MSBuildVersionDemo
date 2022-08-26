# MS Build 版本問題

## Visual Studio Code

- C# v1.24.4

## 開發環境

執行 `dotnet --list-sdks` 結果如下：

```shell
3.1.405 [/usr/local/share/dotnet/sdk]
```

### .NET CLI 執行 `dotnet build` 結果

```shell
Microsoft (R) Build Engine version 16.7.2+b60ddb6f4 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Determining projects to restore...
  All projects are up-to-date for restore.
/Users/joe/.nuget/packages/microsoft.web.librarymanager.build/2.0.96/build/Microsoft.Web.LibraryManager.Build.targets(35,9): warning : libman.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
/Users/joe/.nuget/packages/buildbundlerminifier/3.2.435/build/BuildBundlerMinifier.targets(12,5): warning : /Users/joe/projects/MSBuildVersionDemo/MVCProject/bundleconfig.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
  ConsoleProject -> /Users/joe/projects/MSBuildVersionDemo/ConsoleProject/bin/Debug/netcoreapp3.1/ConsoleProject.dll
  MVCProject -> /Users/joe/projects/MSBuildVersionDemo/MVCProject/bin/Debug/netcoreapp3.1/MVCProject.dll
  MVCProject -> /Users/joe/projects/MSBuildVersionDemo/MVCProject/bin/Debug/netcoreapp3.1/MVCProject.Views.dll

Build succeeded.

/Users/joe/.nuget/packages/microsoft.web.librarymanager.build/2.0.96/build/Microsoft.Web.LibraryManager.Build.targets(35,9): warning : libman.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
/Users/joe/.nuget/packages/buildbundlerminifier/3.2.435/build/BuildBundlerMinifier.targets(12,5): warning : /Users/joe/projects/MSBuildVersionDemo/MVCProject/bundleconfig.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
    2 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.38
```

### Visual Studio Code 執行 build 結果

```shell
*  正在執行的工作: dotnet build /Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj /property:GenerateFullPaths=true /consoleloggerparameters:NoSummary 

Microsoft (R) Build Engine version 16.7.2+b60ddb6f4 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Determining projects to restore...
  All projects are up-to-date for restore.
/Users/joe/.nuget/packages/microsoft.web.librarymanager.build/2.0.96/build/Microsoft.Web.LibraryManager.Build.targets(35,9): warning : libman.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
/Users/joe/.nuget/packages/buildbundlerminifier/3.2.435/build/BuildBundlerMinifier.targets(12,5): warning : /Users/joe/projects/MSBuildVersionDemo/MVCProject/bundleconfig.json does not exist [/Users/joe/projects/MSBuildVersionDemo/MVCProject/MVCProject.csproj]
  MVCProject -> /Users/joe/projects/MSBuildVersionDemo/MVCProject/bin/Debug/netcoreapp3.1/MVCProject.dll
  MVCProject -> /Users/joe/projects/MSBuildVersionDemo/MVCProject/bin/Debug/netcoreapp3.1/MVCProject.Views.dll
 *  工作將被重新啟用.按任意鍵關閉. 
```

tasks.json 資訊

```json
{
    "label": "build",
    "command": "dotnet",
    "type": "process",
    "args": [
        "build",
        "${workspaceFolder}/MVCProject/MVCProject.csproj",
        "/property:GenerateFullPaths=true",
        "/consoleloggerparameters:NoSummary"
    ],
    "problemMatcher": "$msCompile"
}
```

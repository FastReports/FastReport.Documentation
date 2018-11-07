## Compiling the source code

1. Install latest .Net Core SDK for your OS from https://www.microsoft.com/net/download
2. Follow the commands

```sh
# for windows users
git clone https://github.com/FastReports/FastReport.git
cd FastReport
Tools\pack.bat
```

```sh
# for linux users
git clone https://github.com/FastReports/FastReport.git
cd FastReport
chmod 777 Tools/pack.sh && ./Tools/pack.sh
```

The package is located at `fr_nuget` directory.

## Installing from NuGet

You can add FastReport to your current project via NuGet package manager:
```
Install-Package FastReport.OpenSource
Install-Package FastReport.OpenSource.Web
```

## Compiling solution in Visual Studio

Open the FastReport.OpenSource.sln file in Visual Studio and choice the Build -> Build Solution.
Then you can set as StartUp any project from Demos folder and run it.

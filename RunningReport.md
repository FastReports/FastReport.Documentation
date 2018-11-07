# 7.2. Running a Report

To run a report, use one of the following methods of the Report object:

`bool Prepare()`  - Runs a report. If the report was prepared successfully, returns true.

`bool Prepare(bool append)`  - Runs a report. If the append parameter is set to true, the prepared report will be added to the existing one. So you can build several reports and display them in the preview as one report: 
```csharp
report1.Load("report1.frx");
report1.Prepare();
report1.Load("report2.frx");
report1.Prepare(true);
```
 
---

[Storing and Loading a Report](StoringLoadingReport.md) | [Top Page](README.md) | [Configuring the Environment](ConfiguringEnvironment.md)
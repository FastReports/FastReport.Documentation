# 7. Using the Report

## Working with Report in a code

To work with Report component in a code, you need to do the following:

- create a report instance; 
- load a report file into it; 
- register the application-defined data in a report; 
- pass the values into the report parameters, if needed; 
- run the report. 

The following example demonstrates how to do this:

```csharp
using (Report report = new Report())
{
  report.Load("report1.frx");
  report.RegisterData(dataSet1, "NorthWind");
  report.Show();
}
```

---

[Creating a Report by Using Code](CreatingReportUsingCode.md) | [Top Page](README.md) | [Storing and Loading a Report](StoringLoadingReport.md)
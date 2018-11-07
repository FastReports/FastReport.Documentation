# 7.5. Passing Custom SQL

The report may contain data sources that are added using the Data Wizard in Designer (via "Data\|Add Data Source..." menu). 

Sometimes it is needed to pass custom SQL to that data source from your application. To do this, use the following code: 

```csharp
using FastReport.Data;
...
report1.Load(...); 
// do it after loading the report, before running it
// find the table by its alias
TableDataSource table = report1.GetDataSource("MyTable") as TableDataSource;
table.SelectCommand = "new SQL text";
report1.Show();
```

---

[Passing Own Connection String](PassingOwnConnectionString.md) | [Top Page](README.md) | [Reference to a Report Object](ReferenceReportObject.md)

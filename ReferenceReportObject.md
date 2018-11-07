# 7.6. Reference to a Report Object

When you work with a report as a class (see the ["Storing a report and loading it"](StoringLoadingReport.md)), 
you may refer to the report objects directly. 
The following example demonstrates how to change the font of the "Text1" object contained in a report:

```csharp
SimpleListReport report = new SimpleListReport();
report.Text1.Font = new Font("Arial", 12);
```
In other cases, you have to use the FindObject method of the Report object, if you need to get a reference to an object:

```csharp
TextObject text1 = report1.FindObject("Text1") as TextObject;
text1.Font = new Font("Arial", 12);
```

To reference to a data source defined in a report, use the GetDataSource method of the Report object. 
This method takes a data source's alias as a parameter:

```csharp
DataSourceBase ds = report1.GetDataSource("Products");
```

---

[Passing Custom SQL](PassingCustomSQL.md) | [Top Page](README.md) | [Exporting](Exporting.md)
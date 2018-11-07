# 3.1. Registering Data

If your report uses data from an application (for example, the typed dataset or a business-object), 
you have to register such data in a report. This can be done using the RegisterData method of the Report object.

The RegisterData method must be called after you have loaded the report:

```csharp
report1 = new Report();
report1.Load("report.frx");
report1.RegisterData(dataSet1, "NorthWind");
```
 
The RegisterData method is overloaded and allows to register the following data:

| Method | Description |
|:-|:-|
| `void RegisterData(DataSet data)` | Registers the dataset. This method registers all tables, views and relations as well. Attention: if you register more than one dataset, use the RegisterData(DataSet data, string name) method instead. |
| `void RegisterData(DataSet data, string name)` | Registers the dataset. Specify any name in the name parameter (it must be persistent and unique if you register more than one dataset). |
| `void RegisterData(DataTable data, string name)` | Registers the data table. |
| `void RegisterData(DataView data, string name)` |  Registers the data view. |
| `void RegisterDataAsp(IDataSource data, string name)` | Registers the ASP.NET data source such as AccessDataSource. |
| `void RegisterData(DataRelation data, string name)` | Registers the relation. |
| `void RegisterData(IEnumerable data, string name, BOConverterFlags flags, int maxNestingLevel)` | Registers the business object. Specify what items (properties, fields) should be used, in the flags parameter. Specify the maximum nesting level in the maxNestingLevel parameter (typically you need no more than 3 levels). Several nested objects may slow down the report. |

---

[Data](Data.md) | [Top Page](README.md) | [Report Parameters](ReportParameters.md)
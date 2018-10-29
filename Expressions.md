# 4. Expressions

In many places in FastReport, expressions are used. For example, the "Text" object can contain expressions in square brackets.

An expression is a code in C# or VB.Net language, which returns any value. For example:

```
2 + 2
```

An expression should be written in a language chosen as a script in a report. By default, it is C#.

## Reference to report objects

For referring to report objects, use the object's name. The following example will return the height of the Text1 object:

```
Text1.Height
```
 
For referring to report properties, use Report variable. The following example returns file name from which a report was loaded.
 
```
Report.FileName
```

Besides, you can refer to nested object properties. The following example will return a report name:
 
```
Report.ReportInfo.Name
```
 
## Using .Net functions

You can use any.Net objects in expressions. The following example demonstrates Max function use:

``` 
Math.Max(5, 10)
```

By default a report uses the following .Net assemblies:

```
System.dll
System.Drawing.dll
System.Windows.Forms.dll
System.Data.dll
System.Xml.dll
```

You have access to all .Net objects declared in these assemblies. If you need to have access to another assembly, add its name in report assemblies list.

For example, if you want to use a function in your report which was declared in your application, add application assembly (.exe or .dll) in a report assemblies list. After that you can call the function by using namespace of your application. For example, if the following function is defined in application:

```csharp
namespace Demo
{
  public static class MyFunctions
  {
    public static string Func1()
    {
      return "Hello!";
    }
  }
}
```

You can use it in your report in the following way:

```csharp
Demo.MyFunctions.Func1()
```

## Reference to data elements

Apart from standard language elements, you can use the following report elements in expressions:
 
- data source columns;
- system variables;
- total values;
- report parameters.

All these elements are contained in the "Data" window. See more details in the "Data" chapter. Any of these elements can be used in an expression, by including it in square brackets. For example:
 
```
[Page] + 1
```

This expression returns next printed page number. A system variable "Page", which returns current report page number, is used in the expression. It is enclosed in square brackets. 

## Reference to data sources

For reference to data source columns, the following format is used:

```
[DataSource.Column]
```

Source name is separated from column name by a period, for example:

```
[Employees.FirstName]
```

Source name can be compound in case, if we refer to a data source by using a relation. See more details in the "Data" section. For example, this is how you can refer to a related data source column:

```
[Products.Categories.CategoryName]
```

Let us look at the following example of using columns in an expression:

```
[Employees.FirstName] + " " + [Employees.LastName]
```

Here it should be noted that: every column has a definite data type, which is set in the "DataType" property (you can see it in the "Properties" window if to choose data column in the "Data" window beforehand). How a column can be used in an expression depends on its type. For instance, in above mentioned example, both columns - first name and last name - have got a string type and that is why they can be used in such a way. In the following example, we will try to use "Employees.Age" column of numeric type, which will lead to an error:

```
[Employees.FirstName] + " " + [Employees.Age]
```

The error occurs because, you never mix strings with numbers. For this, you need to convert the number into a string:

```
[Employees.FirstName] + " " + [Employees.Age].ToString()
```

In this case, we refer to the "Employees.Age" column as if it is an integer variable. And it is so. We know that all expressions are compiled. All non-standard things (like referring to data columns) from a compiler's point of view are converted into another type, which is understandable to a compiler. So, the last expression will be turned into the following form:

```csharp
(string)(Report.GetColumnValue("Employees.FirstName")) + " " + 
(int)(Report.GetColumnValue("Employees.Age")).ToString()
```
 
As seen, FastReport changes reference to data columns in the following way:

```csharp
[Employees.FirstName] --> (string)(Report.GetColumnValue("Employees.FirstName"))
[Employees.Age] --> (int)(Report.GetColumnValue("Employees.Age"))
```

That is, we can use data column in an expressions as if it is a variable having a definite type. For example, the following expression will return the first symbol of an employee's name:

```csharp
[Employees.FirstName].Substring(0, 1)
```

## Reference to system variables

You can use the following system variables in expressions:

| Variable | .Net data type | Description
|:-|:-|:-|
| Date | DateTime | Date and time of the report's start. |
| Page | int | Current page number. |
| TotalPages | int | Total number of pages in the report. To use this variable, you need to enable the report's double pass. You can do this in "Report|Properties..." menu. |
| PageN | string | Page number in the form: "Page N". |
| PageNofM | string | Page number in the form: "Page N of M". |
| Row# | int | Data row number inside the group. This value is reset at the start of a new group. |
| AbsRow# | int | Absolute number of data row. This value is never reset at the start of a new group. |


Every variable has a definite data type. And on this, depends how it will be used in the expression. Here is an example of an expression where date is being used:

```
[Date].Year
```

This expression returns the current year. As "Date" variable has DateTime type, we can refer to its "Year" property. We can get the current month similarly ([Date].Month).

FastReport converts reference to system variable into the following form (for example, the "Date" variable):

```csharp 
((DateTime)Report.GetVariableValue("Date"))
```

## Reference to total values

In order to refer to a total value, use its name:
 
```
[TotalSales]
```
 
FastReport converts reference to totals into the following form:

```csharp
Report.GetTotalValue("TotalSales")
```
 
As you can see, the data type is not used here. It is so, because the total value is of FastReport.Variant type. It can be used directly in any expressions because it is automatically converted to any type. For example:

```
[TotalSales] * 0.2f
```

## Reference to report parameters

In order to refer to report parameters, you should use its name:
 
```
[Parameter1]
```

Parameters can be nested. In this case, you should use both parent and child parameter names in the following form:
 
```
[ParentParameter.ChildParameter]
```

Parameters have a definite data type. It is set in the "DataType" property of the parameter. The way it can be used in an expression depends on parameter's data type.

FastReport converts reference to a report parameter into the following way:

```csharp
((string)Report.GetParameterValue("Parameter1"))
```

---

[Data](Data.md) | [Top Page](README.md) | [Script](Script.md)

# 3.2. Report Parameters

You can define parameters in a report. Parameter is a variable, the value of which can be defined both in a report itself and outside of it. A parameter can be used in expressions and be displayed in report objects like the "Text" object.

Most common methods of using parameters:

- data filtering by condition set in a parameter;
- printing parameter value in a report.

A parameter has the following properties:

| Property | Description |
|:-|:-|
| Name | Parameter's name can have any symbols except dot ".". |
| DataType | Parameter data type. |
| Expression | Expression which returns parameter's value. More details about expressions can be found in the "Expression" chapter. This expression will be processed when calling a parameter. |
| Value | Parameter value. This property is not available in the designer and can be filled programmatically. |

You have to set up "Name" and "DataType" properties. The "Expression" property can be left empty. In this case parameter's value should be passed programmatically. 

You can refer to a parameter from an expression using square brackets:

```
[Parameter name]
```

To a nested parameter you need to refer using this method:
 
```
[Parent parameter.Child parameter]
```

Since a parameter has got a definite type (it is given in the DataType property), then with parameters, you can perform those actions which are allowed for data type. So, string type parameters can be used in an expression the following way:

```
[StringParameter].Substring(0, 2)
```

Let us see one example of using parameters. Assuming we have a report which prints "Employees" table. We want to modify the report to print information about an employee with an indicated number. To do this, we need to filter the data on the "EmployeeID" data column. Create a parameter with "EmployeeID" name. Indicate parameter's type - Int32, as exactly this type has the "EmployeeID" data column. To filter an employee with an indicated ID we need to enter "Data" band editor and indicate the following expression in "Filter" tab:

```
[Employees.EmployeeID] == [EmployeeID]
```

## Passing a Value to a Report Parameter

To pass a value to the parameter, use the SetParameterValue method of the Report object:

```csharp
report1.Load("report.frx");
report1.SetParameterValue("MyParam", 10);
report1.Prepare();
```
This method is declared as follows:

```csharp
public void SetParameterValue(string complexName, object value)
```

Specify the parameter's name in the complexName parameter. To access a nested parameter, use its full name, for example:

```csharp 
"ParentParameter.ChildParameter"
```

---

[Registering Data](RegisteringData.md) | [Top Page](README.md) | [Query Parameters](QueryParameters.md)
# 3. Data
Any report prints some data. In FastReport, you can operate with the following data:
 
- data sources;
- system variables;
- total values;
- report parameters;
- expressions, containing any of the above mentioned data.

## Data sources

Ordinarily, the data source represents a DB table or SQL query. There can be several data sources in a report. For most of reports, only one data source is needed. A report like Master-Detail needs two data sources which are connected to each other using a relation.
 
Data source has one or several data columns. Each column has a definite data type. Column type is indicated in the "DataType" property.

DB table content is not saved in a report file. Instead, the connection string and the data source schema are stored. A connection string can contain such data as login and password, that is why it is kept ciphered in a report file. When needed, you may increase the safety by using own key for data ciphering. In this case a report file can be opened correctly only in your program. 

## Query parameters

There can be parameters in a query text. Let us see the following query:
 
```sql
select * from DVDs
where Title = @param1
```

This is the query to MS SQL demonstration database. The parameter with "param1" name is defined in a query. Here it should be noted: method of describing parameters in a query differs for different DBMS. For MS SQL a parameter is marked by a "@" symbol, MS Access parameters do not have names and are marked by the "?" symbol.

If your SQL query contains parameters, you have to declare them. It can be done in the third step of the "Query Wizard" which we have looked at above. To create a parameter, press the "Add parameter" button.

The following parameter's properties should be set in the properties window:
 
| Property | Description | 
|:-|:-|
| Name | Parameter name. Here you need to indicate the same name which you use in the query text. Some DBMS (for example, MS Access) do not support named parameters. In this case do not change this property. |
| DataType | Parameter data type. |
| DefaultValue | Value which will be used if the "Expression" property is not specified, or if it is impossible to calculate it (for example, when operating with the query in the report design mode). |
| Expression | Expression which returns parameter's value. This expression will be processed when you run the report. You can indicate any expression in this property (see details in the "Expressions" chapter). |
| Size | Parameter data size. This property should be indicated if the parameter is of "string" data type. |

## Passing a value to the parameter

Parameters are often used to ask a value from the user. Let us look at two ways to pass a value to the query parameter.

In the first way, you pass a value programmatically. Since there is no easy way to pass a value directly to the query parameter, you need to use the report parameter, which can be easily set via code. You should do the following:

- Create the report parameter (we will discuss the report parameters later in this chapter). Set the same DataType for the report parameter, as it is used in the query parameter.

- In the "Expression" property of the query parameter, refer to a report parameter, for example:

```
[MyReportParameter]
```

- Pass a value to the report parameter:

```csharp
report1.SetParameterValue("MyReportParameter", 10);
```

## Aliases

Every data element (data sources and columns) has got its own name. By default, this is the name defined in the database. In some cases, it can be difficult to understand what is hidden behind such name, for example, ProdID.

Data elements have got a second name - alias. By using an alias, you can rename an element. For example, if we have got a data source CATEGORY_TABLE with a column called "PROD_ID", you can give the following alias:

```
CATEGORY_TABLE --> Categories
PROD_ID --> Product ID
```

You can refer to such a data column in the following way:

```
[Categories.Product ID]
```

When referring to the data element, you must use the alias, if it has been defined. Never refer to an element by using its original name in this case. 

## Hierarchical data sources

The data sources we have looked at, are relational, that is, they come from a relational DBMS (often called RDBMS). FastReport also supports other kinds of data - the hierarchical data sources. Such data sources come from so-called business objects, which are often used in applications to represent a relational data sources as a .Net classes.

The only way to add a hierarchical data source in your report is to register it programmatically. It will be discussed in the "Programmer's manual". Now we will look at some differences between ordinal and hierarchical data sources. In the figure below you can see two data sources, "Categories BusinessObject" and "Products". As you can see, the "Products" data source is contained within its parent, "Categories BusinessObject":

![](images/businessobject.png)

This means that, these two data sources are related to each other and can be used in the "master-detail" report type. You can also use each of these data sources separately in a "simple list" report type.

## System Variables

There is a list of system variables that can be used in a report:

| Variable | Description |
|:-|:-|
| Date | Date and time of the report's start. |
| Page | Current page number. |
| TotalPages | Total number of pages in the report. To use this variable, you need to enable the report's double pass. You can do this in "Report|Properties..." menu. |
| PageN | Page number in the form: "Page N". |
| PageNofM | Page number in the form: "Page N of M". | 
| Row# | Data row number inside the group. This value is reset at the start of a new group. |
| AbsRow# | Absolute number of data row. This value is never reset at the start of a new group. |
| Page# | Current page number. If you join several prepared reports into one package, this variable will return current page number in a package. This variable is actually a macro. It value is substituted when the component is viewed in the preview window. That means you cannot use it in an expression. |
| TotalPages# | Total number of pages in the report. If you join several prepared reports into one package, this variable will return the number of pages in a package. You don't need to use double pass to get the correct value. This variable is actually a macro. It value is substituted when the component is viewed in the preview window. That means you cannot use it in an expression. |
| HierarchyLevel | Current level of hierarchy in a hierarchical report (see "Printing hierarchy"). The top level is equal to 1. |
| HierarchyRow# | Full row number like "1.2.1" in a hierarchical report. |

## Totals

In many reports, we may need to show some total information: sum of the group, number of rows in the list, and many others. FastReport uses totals to perform this task. For the total, you need to indicate the following parameters:
 
- The total function type;
- The expression, which is supposed to be calculated. For the "Count" function, you do not need to indicate the expression;
- The condition. The function will be calculated if the condition is met. It's not obligatory to set up the condition.
- The data band, for which the function will be processed;
- The band, in which the total value will be printed.

The list of total functions is given below:

| Function | Description |
|:-|:-|
| Sum | Calculates the sum of the expression. |
| Min | Calculates the minimum value of the expression. |
| Max | Calculates the maximum value of the expression. |
| Average | Calculates the average value of the expression. |
| Count | Returns the number of rows. |

## Report parameters

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

To pass parameter value from your program to the report, use the following code:

```csharp
report1.SetParameterValue("EmployeeID", 2);
```

---

[Report Objects](ReportObjects.md) | [Top Page](README.md) | [Expressions](Expressions.md)
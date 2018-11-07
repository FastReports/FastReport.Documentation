# 7.1. Storing and Loading a Report

You may store a report in the following ways:

 
## In the .FRX file

To load the report from a file, use the `Load` method of the `Report` object:

```csharp
report1.Load("filename.frx");
``` 
 
## In the database

You may store a report in the database, either as a string or in a blob-stream. 
To load the report from a string, use the `LoadFromString` method of the `Report` object. 
To load the report from a stream, use the overloaded version of the Load method:

```csharp
report1.Load(stream);
```
 
## As a C#/VB.NET class
To work with a report as a class, design your report and save in to the .cs/.vb file. 
To do this, select "file type" in the "Save" dialog. The file type maybe either .cs or .vb - it depends on the script language in the report (it may be changed in the "Report|Options..." menu). 
Include that file into your project. This method has the following Pros:
 
- you can work with a report as a class;
- you may debug a report;
- this is the only way to use a report in ASP.NET project running on medium trust environment;

and Cons:

- you cannot edit such a report. To do this, you need the original .FRX file;
- if you need to change a report, you have to recompile your application.

To work with a report, create an instance of the report's class:

```csharp
SimpleListReport report = new SimpleListReport();
report.Show();
```
 
---

[Using the Report](UsingReport.md) | [Top Page](README.md) | [Running a Report](RunningReport.md)

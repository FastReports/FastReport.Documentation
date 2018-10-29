# Report Template File Structure

The following is an example of the structure of a report template file.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Report ScriptLanguage="CSharp" TextQuality="Regular" ReportInfo.Name="Simple List" ReportInfo.Author="Fast Reports Inc" ReportInfo.Description="Demonstrates simple list report. To create it:&#13;&#10;- go to &quot;Data&quot; menu and select &quot;Choose Report Data...&quot; item to select datasource;&#13;&#10;- go to &quot;Report|Configure Bands...&quot; menu to create the band structure;&#13;&#10;- return to the report page, doubleclick the data band to show its editor;&#13;&#10;- choose the datasource;&#13;&#10;- drag data from the Data Dictionary window to the band." ReportInfo.Created="01/17/2008 03:05:57" ReportInfo.Modified="07/26/2018 12:14:37" ReportInfo.CreatorVersion="1.0.0.0">
  <Dictionary>
    <TableDataSource Name="Employees" ReferenceName="NorthWind.Employees" DataType="System.Int32" Enabled="true">
      <Column Name="EmployeeID" DataType="System.Int32"/>
      <Column Name="LastName" DataType="System.String"/>
      <Column Name="FirstName" DataType="System.String"/>
      <Column Name="Title" DataType="System.String"/>
      <Column Name="TitleOfCourtesy" DataType="System.String"/>
      <Column Name="BirthDate" DataType="System.DateTime"/>
      <Column Name="HireDate" DataType="System.DateTime"/>
      <Column Name="Address" DataType="System.String"/>
      <Column Name="City" DataType="System.String"/>
      <Column Name="Region" DataType="System.String"/>
      <Column Name="PostalCode" DataType="System.String"/>
      <Column Name="Country" DataType="System.String"/>
      <Column Name="HomePhone" DataType="System.String"/>
      <Column Name="Extension" DataType="System.String"/>
      <Column Name="Photo" DataType="System.Byte[]" BindableControl="Picture"/>
      <Column Name="Notes" DataType="System.String"/>
      <Column Name="ReportsTo" DataType="System.Int32"/>
    </TableDataSource>
  </Dictionary>
  <ReportPage Name="Page1">
    <ReportTitleBand Name="ReportTitle1" Width="718.2" Height="75.6" CanGrow="true">
      <TextObject Name="Text1" Top="47.25" Width="718.2" Height="28.35" Text="EMPLOYEES" HorzAlign="Center" VertAlign="Center" Font="Tahoma, 14pt, style=Bold"/>
      <TextObject Name="Text11" Width="718.2" Height="28.35" Anchor="Top, Left, Right" Fill.Color="WhiteSmoke" CanGrow="true" CanShrink="true" Text="[Report.ReportInfo.Description]&#13;&#10;" Padding="4, 4, 4, 4" Font="Tahoma, 8pt"/>
      <ChildBand Name="Child2" Top="79.6" Width="718.2" Height="18.9"/>
    </ReportTitleBand>
    <DataBand Name="Data1" Top="102.5" Width="718.2" Height="219.24" Border.Lines="All" Border.Color="Maroon" CanGrow="true" DataSource="Employees">
      <TextObject Name="Text3" Left="9.45" Top="66.15" Width="103.95" Height="18.9" Text="Birth date:" VertAlign="Center" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text4" Left="113.4" Top="66.15" Width="453.6" Height="18.9" Text="[Employees.BirthDate]" Format="Date" Format.Format="D" VertAlign="Center" Font="Tahoma, 9pt"/>
      <TextObject Name="Text5" Left="9.45" Top="103.95" Width="103.95" Height="18.9" Text="Address:" VertAlign="Center" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text6" Left="113.4" Top="103.95" Width="453.6" Height="18.9" CanGrow="true" Text="[Employees.Address]" VertAlign="Center" Font="Tahoma, 9pt"/>
      <TextObject Name="Text7" Left="9.45" Top="122.85" Width="103.95" Height="18.9" Text="Phone:" VertAlign="Center" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text8" Left="113.4" Top="122.85" Width="453.6" Height="18.9" Text="[Employees.HomePhone]" VertAlign="Center" Font="Tahoma, 9pt"/>
      <TextObject Name="Text9" Left="113.4" Top="151.2" Width="453.6" Height="56.7" CanGrow="true" CanShrink="true" Text="[Employees.Notes]" Padding="2, 0, 2, 10" HorzAlign="Justify" Font="Tahoma, 9pt"/>
      <PictureObject Name="Picture1" Left="576.45" Top="47.25" Width="132.3" Height="162.54" Border.Lines="All" Border.Color="Maroon" CanGrow="true" CanShrink="true" DataColumn="Employees.Photo"/>
      <TextObject Name="Text13" Left="113.4" Top="47.25" Width="453.6" Height="18.9" Text="[Employees.HireDate]" Format="Date" Format.Format="d" VertAlign="Center" Font="Tahoma, 9pt"/>
      <TextObject Name="Text14" Left="113.4" Top="85.05" Width="453.6" Height="18.9" Text="[Employees.City]" VertAlign="Center" Font="Tahoma, 9pt"/>
      <TextObject Name="Text15" Left="9.45" Top="47.25" Width="103.95" Height="18.9" Text="Hire date:" VertAlign="Center" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text16" Left="9.45" Top="85.05" Width="103.95" Height="18.9" Text="City:" VertAlign="Center" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text17" Left="9.45" Top="151.2" Width="103.95" Height="18.9" Text="Notes:" Font="Tahoma, 9pt, style=Bold"/>
      <TextObject Name="Text2" Width="718.2" Height="37.8" Border.Lines="All" Border.Color="Maroon" Fill="LinearGradient" Fill.StartColor="IndianRed" Fill.EndColor="Maroon" Fill.Angle="90" Fill.Focus="0.52" Fill.Contrast="1" Text="[Employees.FirstName] [Employees.LastName]" Padding="10, 0, 2, 0" VertAlign="Center" Font="Tahoma, 12pt, style=Bold" TextFill.Color="White"/>
      <ChildBand Name="Child1" Top="325.74" Width="718.2" Height="18.9"/>
      <Sort>
        <Sort Expression="[Employees.FirstName]"/>
        <Sort Expression="[Employees.LastName]"/>
      </Sort>
    </DataBand>
    <PageFooterBand Name="PageFooter1" Top="348.64" Width="718.2" Height="28.35" Fill.Color="WhiteSmoke" CanGrow="true">
      <TextObject Name="Text10" Left="614.25" Width="94.5" Height="28.35" Text="[PageN]" HorzAlign="Right" VertAlign="Center" Font="Tahoma, 8pt"/>
      <TextObject Name="Text12" Left="9.45" Width="217.35" Height="28.35" Cursor="Hand" Hyperlink.Value="https://www.fast-report.com/en/product/fast-report-net/" Text="Generated by FastReport .NET" VertAlign="Center" Font="Tahoma, 8pt, style=Underline" TextFill.Color="Blue"/>
    </PageFooterBand>
  </ReportPage>
</Report>
```

[The original file can be downloaded here.](https://github.com/FastReports/FastReport/blob/master/Demos/Reports/Simple%20List.frx)

---

[FastReport Online Designer](FastReportOnlineDesigner.md) | [Top Page](README.md) | [Creating Report Using Code](CreatingReportUsingCode.md)
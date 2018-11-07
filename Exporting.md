# 8. Exporting

FastReport Open Source can save documents in HTML, BMP, PNG, JPEG, GIF, TIFF, EMF.

The following is an example of exporting a report in Jpeg file.

```csharp
using FastReport;
using FastReport.Utils;
using FastReport.Export.Image;
            ...
            // Create new Report 
            Report report = new Report();
            // Load report from file
            report.Load("report.frx");
            // Set the parameter
            report.SetParameterValue("MYPARAMETER", 1024);
            // Prepare the report
            report.Prepare();
            // Export in Jpeg
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Jpeg;
            // Set up the quality
            image.JpegQuality = 90;
            // Decrease a resolution
            image.Resolution = 72;
            // We need all pages in one big single file
            image.SeparateFiles = false;
            report.Export(image, "report.jpg");
```

The following is an example of exporting a report in PNG file.

```csharp
            // Export in PNG
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Png;
            // Increase a resolution
            image.Resolution = 300;
            // We need separate file for each report page, they will be numbered: report.png, report.2.png, report.3.png, etc.
            image.SeparateFiles = true;
            report.Export(image, "report.png");
```

The following is an example of exporting a report in HTML file.

```csharp
using FastReport;
using FastReport.Utils;
using FastReport.Export.Html;
            ...
            // Export in HTML
            HTMLExport html = new HTMLExport();
            // We need embedded pictures inside html
            html.EmbedPictures = true;
            // Enable all report pages in one html file
            html.SinglePage = true;
            // We don't need a subfolder for pictures and additional files
            html.SubFolder = false;
            // Enable layered HTML
            html.Layers = true;
            // Turn off the toolbar with navigation
            html.Navigator = false;
            // Save the report in html
            report.Export(html, "report.html");
```

The following is an example of exporting a report in multiple streams.

```csharp
            // Creatint the Report object
            using (Report report = new Report())
            {
                // Loading a report
                report.Load("report.frx");
                // Preparing a report
                report.Prepare();

                // Creating the HTML export
                using (HTMLExport html = new HTMLExport())
                {
                    // Choose the Jpeg pictures
                    html.ImageFormat = ImageFormat.Jpeg;
                    // We need the saving in multiple streams
                    html.SaveStreams = true;
                    // Exporting with fake null stream object, html export will keep all files inside
                    report.Export(html, (Stream)null);
                    // Checking for the exporting
                    if (html.GeneratedFiles.Count > 0)
                    {
                        // Loop for generated files 
                        for (int i = 0; i < html.GeneratedFiles.Count; i++)
                        {
                            // We have several streams, let's save it in files
                            using (FileStream file = new FileStream("export_path/" + html.GeneratedFiles[i], FileMode.Create))
                            {
                                // You need reset the internal stream position
                                html.GeneratedStreams[i].Position = 0;
                                // Saving a stream in the file
                                html.GeneratedStreams[i].CopyTo(file);
                            }                             
                        }
                    }
                }
            }

```
The result of the code above:
```
1.html
3D8711F2B3E0CB27B4ABB3B008100944.jpeg
8ADC69235827736FEFD905D29F1BA3C3.jpeg
A4310A5FEB8A9D6D4FFDC4F3747940F4.jpeg
D040CA1257EC42CE08EA369E5101E2D1.jpeg
E9376AC431359E9A088B9F104665ABE9.jpeg
EA63D4A0288B3841CD552CA0DC3845DB.jpeg
EC5F2B95E3DA517ED1244012D77901BC.jpeg
```

---

[Reference to a Report Object](ReferenceReportObject.md) | [Top Page](README.md) | [Reports in Web](WebReport.md)
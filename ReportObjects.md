# 2.4. Report Objects

A wide variety of objects can be used in a report.

| Name | Description |
|:-|:-|
| `TextObject` | Displays one or several text lines. |
| `PictureObject` | Displays a picture. |
| `LineObject` | Displays a line. A line can be vertical, horizontal or diagonal. |
| `ShapeObject` | Displays one of the geometrical shapes - rectangle, ellipse, triangle and others. |
| `BarcodeObject` | Displays a barcode. |
| `CheckBoxObject` | Displays a checkbox which can have two states - "Enabled" or "Disabled". |
| `TableObject` | Displays a table containing rows, columns and  cells. |
| `MatrixObject` | Displays a matrix (also known as "Cross-tab"). |
| `ZipCodeObject` | Displays a zip code. |
| `CellularTextObject` | Displays each character of a text in its individual cell. |
| `PolyLineObject` | Displays a composite line. |
| `PolygonObject` | Displays a polygon shape. |
| `LinearGauge` | Displays a linear gauge. |
| `SimpleGauge` | Displays a simple gauge. |
| `RadialGauge` | Displays a radial gauge. |
| `SimpleProgressGauge` | Displays a simple progress gauge. |

An object can be used to display an information ("Text", etc objects) or to improve the report appearance ("Picture", "Line", "Shape" objects). Complex objects like "Table" and "Matrix" can contain other simple objects.

## Common object properties

All report objects are inherited from one basic class (ReportComponentBase) and have got certain set of common properties. Before studying each object, we will look at these properties.

You can change the value of properties with the help of the "Properties" window. Some properties can be changed using the object's context menu or toolbars (for example, border and fill).

| Property | Description |
|:-|:-|
| `Left`, `Top`, `Width`, `Height` | A report object, as a rule, is a rectangle. It has coordinates (properties `Left`, `Top`) and size (properties `Width`, `Height`). |
| `Anchor` | This property determines how the object will be changing its position and/or its size when the container on which it is laying grows or shrinks. By using Anchor, it can be done in such a way that, the object expands or moves synchronously with container. Read more about this property in the "Dynamic layout" chapter. |
| `Dock` | This property determines on which side of the container the object will be docked. Read more about this property in the "Dynamic layout" chapter. |
| `Border`, `Fill` | These properties control the object's border and fill. They can be changed using the "Border and Fill" toolbar. |
| `CanGrow`, `CanShrink` | These properties allow fitting the height of the object in such a way that it fits the whole text. Read more about this property in the "Dynamic layout" chapter. |
| `ShiftMode` | An object, whose property is enabled, will be moving up and down, if the object above on can either grow or shrink. Read more about this property in the "Dynamic layout" chapter. |
| `GrowToBottom` | An object, whose property is enabled, will be stretched to the bottom of a band. Read more about this property in the "Dynamic layout" chapter. |
| `CanBreak` | Objects "Text" and "Rich Text" have this property. It determines whether the object’s contents can be broken into parts. |
| `PrintOn` | This property determines on which pages the object can be printed. Read more about this property in the "Booklet-type report" chapter. |
| `Cursor` | This property determines the type of mouse cursor when it is located over an object. The property works only in the preview window. |
| `Visible` | This property determines whether the object will be displayed in the report. Invisible object is never displayed in the preview window and is never printed on the printer as well. |
| `Printable` | This property determines whether the object will be printed on the printer. If this property is disabled, then the object will be visible in the preview window but it will not be printed. |
| `Hyperlink` | This property makes it possible to make the report object interactive. Read more about this property in the "Interactive reports" chapter. |
| `Bookmark` | This property is used together with the `Hyperlink` property. It can contain any expression. The expression will be calculated when the report will be working, and its value will be used as bookmark's name.
| `Restrictions` | This property restricts certain operations, such as moving, resizing, deleting the object. |
| `Style` | You can assign the style name to this property. When this is done, the object will become like it has been indicated in the style. If the parameters of the style changes, the appearance of the object changes as well. |

---

[Report Pages](ReportPages.md) | [Top Page](README.md) | [Data](Data.md)
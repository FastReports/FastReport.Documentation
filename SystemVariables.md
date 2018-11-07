# 3.4. System Variables

There is a list of system variables that can be used in a report:

| Variable | Description |
|:-|:-|
| `Date` | Date and time of the report's start. |
| `Page` | Current page number. |
| `TotalPages` | Total number of pages in the report. To use this variable, you need to enable the report's double pass. You can do this in "Report\|Properties..." menu. |
| `PageN` | Page number in the form: "Page N". |
| `PageNofM` | Page number in the form: "Page N of M". | 
| `Row#` | Data row number inside the group. This value is reset at the start of a new group. |
| `AbsRow#` | Absolute number of data row. This value is never reset at the start of a new group. |
| `Page#` | Current page number. If you join several prepared reports into one package, this variable will return current page number in a package. This variable is actually a macro. It value is substituted when the component is viewed in the preview window. That means you cannot use it in an expression. |
| `TotalPages#` | Total number of pages in the report. If you join several prepared reports into one package, this variable will return the number of pages in a package. You don't need to use double pass to get the correct value. This variable is actually a macro. It value is substituted when the component is viewed in the preview window. That means you cannot use it in an expression. |
| `HierarchyLevel` | Current level of hierarchy in a hierarchical report. The top level is equal to 1. |
| `HierarchyRow#` | Full row number like "1.2.1" in a hierarchical report. |

---

[Query Parameters](QueryParameters.md) | [Top Page](README.md) | [Totals](Totals.md)

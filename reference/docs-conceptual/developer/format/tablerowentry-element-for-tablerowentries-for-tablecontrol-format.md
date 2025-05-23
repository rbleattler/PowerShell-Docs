---
description: TableRowEntry Element
ms.date: 08/25/2021
title: TableRowEntry Element
---
# TableRowEntry Element

Defines the data that is displayed in a row of the table.

## Schema

- Configuration Element
- ViewDefinitions Element
- View Element
- TableControl Element
- TableRowEntries Element for TableControl
- TableRowEntry Element for TableRowEntries

## Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## Attributes and Elements

The following sections describe attributes, child elements, and parent element of the
`TableRowEntry` element.

### Attributes

None.

### Child Elements

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy Element for TableRowEntry for TableControl](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Required element.<br /><br /> Defines the objects whose property values are displayed in the row.|
|[TableColumnItems Element for TableRowEntry for TableControl](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Required element.<br /><br /> Defines the properties or scripts whose values are displayed.|
|[Wrap Element for TableRowEntry for TableControl](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Optional element.<br /><br /> Specifies that text that exceeds the column width is displayed on the next line.|

### Parent Elements

|Element|Description|
|-------------|-----------------|
|[TableRowEntries Element for TableControl](./tablerowentries-element-for-tablecontrol-format.md)|Defines the rows of the table.|

## Remarks

One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.

For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).

## Example

The following example shows a `TableRowEntry` element that defines a row that displays the values of
two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## See Also

[Creating a Table View](./creating-a-table-view.md)

[EntrySelectedBy Element for TableRowEntry for TableControl](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems Element for TableRowEntry for TableControl](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries Element for TableControl](./tablerowentries-element-for-tablecontrol-format.md)

[Wrap Element for TableRowEntry for TableControl](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Writing a PowerShell Formatting File](./writing-a-powershell-formatting-file.md)

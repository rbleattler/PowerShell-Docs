---
description: SelectionSetName Element for EntrySelectedBy for WideControl
ms.date: 08/25/2021
title: SelectionSetName Element for EntrySelectedBy for WideControl
---
# SelectionSetName Element for EntrySelectedBy for WideControl

Specifies a set of .NET objects for the definition. The definition is used whenever one of these
objects is displayed.

## Schema

- Configuration Element
- ViewDefinitions Element
- View Element
- WideControl Element
- WideEntries Element
- WideEntry Element
- EntrySelectedBy Element
- SelectionSetName Element

## Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## Attributes and Elements

The following sections describe the attributes, child elements, and the parent element of the
`SelectionSetName` element.

### Attributes

None.

### Child Elements

None.

### Parent Elements

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy Element for WideEntry](./entryselectedby-element-for-wideentry-format.md)|Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.|

## Text Value

Specify the name of the selection set.

## Remarks

Each definition must specify one type name, selection set, or selection condition.

Selection sets are typically used when you want to define a group of objects that are used in
multiple views. For example, you might want to create a table view and a list view for the same set
of objects. For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).

For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).

## See Also

[Creating a Wide View](./creating-a-wide-view.md)

[Defining Selection Sets](./defining-selection-sets.md)

[EntrySelectedBy Element for WideEntry](./entryselectedby-element-for-wideentry-format.md)

[Writing a PowerShell Formatting File](./writing-a-powershell-formatting-file.md)

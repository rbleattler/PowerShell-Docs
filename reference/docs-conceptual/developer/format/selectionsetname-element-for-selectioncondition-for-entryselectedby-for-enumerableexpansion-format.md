---
description: SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion
ms.date: 08/25/2021
title: SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion
---
# SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion

Specifies the set of .NET types that trigger the condition. When any of the types in this set are
present, the condition is met.

## Schema

- Configuration Element
- DefaultSettings Element
- EnumerableExpansions Element
- EnumerableExpansions Element
- EntrySelectedBy Element
- SelectionCondition Element
- SelectionSetName Element

## Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## Attributes and Elements

The following sections describe attributes, child elements, and parent element of the
`SelectionSetName` element.

### Attributes

None.

### Child Elements

None.

### Parent Elements

|Element|Description|
|-------------|-----------------|
|[SelectionCondition Element for EntrySelectedBy for EnumerableExpansion](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Defines the condition that must exist to expand the collection objects of this definition.|

## Text Value

Specify the name of the selection set.

## Remarks

The selection condition can specify a selection set or .NET type, but cannot specify both. For more
information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).

Selection sets are common groups of .NET objects that can be used by any view that the formatting
file defines. For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).

## See Also

[Defining Selection Sets](./defining-selection-sets.md)

[SelectionCondition Element for EntrySelectedBy for EnumerableExpansion](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Writing a PowerShell Formatting File](./writing-a-powershell-formatting-file.md)

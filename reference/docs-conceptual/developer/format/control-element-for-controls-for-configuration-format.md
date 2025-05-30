---
description: Control Element for Controls for Configuration
ms.date: 08/20/2021
title: Control Element for Controls for Configuration
---
# Control Element for Controls for Configuration

Defines a common control that can be used by all the views of the formatting file and the name that
is used to reference the control.

## Schema

- Configuration Element
- Controls Element
- Control Element

## Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## Attributes and Elements

The following sections describe the attributes, child elements, and the parent element for the
`Control` element. You must specify only one of each child element.

### Attributes

None.

### Child Elements

|Element|Description|
|-------------|-----------------|
|[CustomControl Element for Control for Controls for Configuration](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Required element.<br /><br /> Defines the control.|
|[Name Element for Control for Configuration](./name-element-for-control-for-controls-for-configuration-format.md)|Required element.<br /><br /> Specifies the name used to reference the control.|

### Parent Elements

|Element|Description|
|-------------|-----------------|
|[Controls Element of Configuration](./controls-element-for-configuration-format.md)|Defines the common controls that can be used by all views of the formatting file or by other controls.|

## Remarks

The name given to this control can be referenced in the following elements:

- [ExpressionBinding Element for CustomItem](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy Element for View](./groupby-element-for-view-format.md)

## See Also

[Controls Element of Configuration](./controls-element-for-configuration-format.md)

[CustomControl element for Control for Configuration](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding Element for CustomItem](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy Element for View(Format)](./groupby-element-for-view-format.md)

[Name Element for Control for Controls for Configuration](./name-element-for-control-for-controls-for-configuration-format.md)

[Writing a PowerShell Formatting File](./writing-a-powershell-formatting-file.md)

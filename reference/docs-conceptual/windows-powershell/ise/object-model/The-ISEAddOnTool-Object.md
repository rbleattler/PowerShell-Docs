---
description: An ISEAddonTool object represents an installed add-on tool that provides additional functionality to Windows PowerShell ISE.
ms.date: 03/27/2025
title: The ISEAddOnTool Object
---

# The ISEAddOnTool Object

An **ISEAddonTool** object represents an installed add-on tool that provides additional
functionality to Windows PowerShell ISE. An example is the **Commands** tool that you can display by
clicking **View**, then **Show Command Add-on**. This tool is then accessible to you by manipulating
the various available **ISEAddOnTool** objects.

Each add-on tool can be associated with either the vertical pane or the horizontal pane. The
vertical pane is docked to the right edge of Windows PowerShell ISE. The horizontal pane is docked
to the bottom edge.

Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed. See
[$psISE.CurrentPowerShellTab.HorizontalAddOnTools][04] and
[$psISE.CurrentPowerShellTab.VerticalAddOnTools][04] to access the collection of tools available to
the currently selected tab or the same properties on any of the **PowerShellTab** objects in the
[$psISE.PowerShellTabs][05] collection object.

## Methods

There are no Windows PowerShell ISE-specific methods available for objects of this class.

## Properties

### Control

Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.

The **Control** property provides read access to many of the details of the Commands add-on tool.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it's visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
```

```Output
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### IsVisible

Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.

The Boolean property that indicates whether the add-on tool is currently visible in its assigned
pane. If it's visible, you can set the **IsVisible** property to `$false` to hide the tool, or set
the **IsVisible** property to `$true` to make an add-on tool visible on its PowerShell tab. Note
that after an add-on tool is hidden, it's no longer accessible through the
**CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore can't be
made visible by using this property on that object.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### Name

Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.

The read-only property that gets the name of the add-on tool.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
```

```Output
Commands
```

## See Also

- [The ISEAddOnToolCollection Object][03]
- [Purpose of the Windows PowerShell ISE Scripting Object Model][01]
- [The ISE Object Model Hierarchy][02]

<!-- link references -->
[01]: Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md
[02]: The-ISE-Object-Model-Hierarchy.md
[03]: The-ISEAddOnToolCollection-Object.md
[04]: The-PowerShellTab-Object.md
[05]: The-PowerShellTabCollection-Object.md

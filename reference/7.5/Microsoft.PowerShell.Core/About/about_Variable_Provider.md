---
description: Variable
Locale: en-US
ms.date: 10/18/2018
online version: https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.5&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variable_Provider
---
# about_Variable_Provider

## Provider name

Variable

## Drives

`Variable:`

## Capabilities

**ShouldProcess**

## Short description

Provides access to the PowerShell variables and to their values.

## Detailed description

The PowerShell **Variable** provider lets you get, add, change, clear, and
delete PowerShell variables in the current console.

The PowerShell **Variable** provider supports the variables that PowerShell
creates, including the automatic variables, the preference variables, and the
variables that you create.

The **Variable** drive is a flat namespace that contains only the variable
objects. The variables have no child items.

The **Variable** provider supports the following cmdlets, which are covered
in this article.

- [Get-Location][01]
- [Set-Location][02]
- [Get-Item][03]
- [New-Item][04]
- [Remove-Item][05]
- [Clear-Item][06]

PowerShell also includes a set of cmdlets designed especially to view and to
change variables. When you use **Variable** cmdlets, you do not need to specify
the `Variable:` drive in the name. This article does not cover working with
**Variable** cmdlets.

- [Get-Variable][07]
- [New-Variable][08]
- [Set-Variable][09]
- [Remove-Variable][10]
- [Clear-Variable][11]

> [!NOTE]
> You can also use the PowerShell expression parser to create, view, and change
> the values of variables without using the cmdlets. When working with
> variables directly, use a dollar sign (`$`) to identify the name as a
> variable and the assignment operator (`=`)to establish and change its value.
> For example, `$p = Get-Process` creates the `p` variable and stores the
> results of a `Get-Process` command in it.

## Types exposed by this provider

Variables can be one of several different types. Most variables will be
instances of the `PSVariable` class. Other variables and their types are
listed below.

- The `?` variable is an instance of the `QuestionMarkVariable` class.
- The `null` variable is an instance of the `NullVariable` class.
- The maximum count variables are instances of the
  `SessionStateCapacityVariable` class.
- `LocalVariable` instances contain information about current execution,
  such as:
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## Navigating the Variable drives

The **Variable** provider exposes its data store in the `Variable:` drive. To
work with variables, you can change your location to the `Variable:` drive
(`Set-Location Variable:`), or you can work from any other PowerShell drive. To
reference a variable from another location, use the drive name (`Variable:`) in
the path.

```powershell
Set-Location Variable:
```

To return to a file system drive, type the drive name. For example, type:

```powershell
Set-Location C:
```

You can also work with the **Variable** provider from any other PowerShell
drive. To reference a variable from another location, use the drive name
`Variable:` in the path.

> [!NOTE]
> PowerShell uses aliases to allow you a familiar way to work with provider
> paths. Commands such as `dir` and `ls` are now aliases for
> [Get-ChildItem][12], `cd` is an alias for [Set-Location][13]. and `pwd` is
> an alias for [Get-Location][14].

## Displaying the value of variables

### Get all variables in the current session

This command gets the list of all the variables and their values in the current
session. You can use this command from any PowerShell drive.

```powershell
Get-ChildItem -Path Variable:
```

### Get a variable using its provider path

This command retrieves a variables value using its provider path prefixed by
the dollar sign (`$`). This has the same effect as prefixing the variables name
with the dollar sign (`$`).

```powershell
$Variable:HOME
```

### Get variables using wildcards

This command gets the variables with names that begin with "Max". You can use
this command from any PowerShell drive.

```powershell
Get-ChildItem -Path Variable:Max*
```

### Get the value of the ? variable

This command uses the `-LiteralPath` parameter of [Get-ChildItem][12] to get
the value of the `?` variable from within the `Variable:` drive. The `?` is
a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any
wildcards in the values of the `-LiteralPath` parameter.

```powershell
Get-ChildItem -LiteralPath ?
```

### Get ReadOnly and Constant variables

This command gets the variables that have the values of `ReadOnly` or
`Constant` for their **Options** property.

```powershell
Get-ChildItem -Path Variable: |
    Where-Object {
        $_.Options -match 'Constant' -or 
        $_.Options -match 'ReadOnly'
    } | 
    Format-List -Property Name, Value, Options
```

## Creating variables

### Create a new variable

This command creates the `services` variable and stores the results of a
`Get-Service` command in it. Because the current location is in the `Variable:`
drive, the value of the `-Path` parameter is a dot (`.`), which represents the
current location.

The parentheses around the `Get-Service` command ensure that the command is
executed before the variable is created. Without the parentheses, the value of
the new variable is a "Get-Service" string.

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### Create a variable using an absolute path

This command creates a `services` variable and stores the result of a
`Get-Service` command in it.

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 To create a variable without a value, omit the assignment operator.

## Changing variables

### Rename a variable

This command uses the `Rename-Item` cmdlet to change the name of the `a`
variable to `processes`.

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### Change the value of a variable

This command uses the `Set-Item` cmdlet to change the value of the
`ErrorActionPreference` variable to "Stop".

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## Copy a variable

This command uses the `Copy-Item` cmdlet to copy the `processes` variable to
`old_processes`. This creates a new variable named `old_processes` that has the
same value as the `processes` variable.

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## Delete a variable

This command deletes the `serv` variable from the current session. You can use
this command in any PowerShell drive.

```powershell
Remove-Variable -Path Variable:serv
```

### Delete variables using the -Force parameter

This command deletes all variables from the current session except for the
variables whose **Options** property has a value of `Constant`. Without the
`-Force` parameter, the command does not delete variables whose **Options**
property has a value of `ReadOnly`.

```powershell
Remove-Item Variable:* -Force
```

## Setting the value of a variable to NULL

This command uses the `Clear-Item` cmdlet to change the value of the
`processes` variable to NULL.

```powershell
Clear-Item -Path Variable:processes
```

## Using the pipeline

Provider cmdlets accept pipeline input. You can use the pipeline to simplify
task by sending provider data from one cmdlet to another provider cmdlet.
To read more about how to use the pipeline with provider cmdlets, see the
cmdlet references provided throughout this article.

## Getting help

Beginning in Windows PowerShell 3.0, you can get customized help topics for
provider cmdlets that explain how those cmdlets behave in a file system drive.

To get the help topics that are customized for the file system drive, run a
[Get-Help][15] command in a file system drive or use the `-Path` parameter of
[Get-Help][15] to specify a file system drive.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path Variable:
```

## See also

- [about_Automatic_Variables][16]
- [about_Providers][17]
- [about_Variables][18]

<!-- link references -->
[01]: xref:Microsoft.PowerShell.Management.Get-Location
[02]: xref:Microsoft.PowerShell.Management.Set-Location
[03]: xref:Microsoft.PowerShell.Management.Get-Item
[04]: xref:Microsoft.PowerShell.Management.New-Item
[05]: xref:Microsoft.PowerShell.Management.Remove-Item
[06]: xref:Microsoft.PowerShell.Management.Clear-Item
[07]: xref:Microsoft.PowerShell.Utility.Get-Variable
[08]: xref:Microsoft.PowerShell.Utility.New-Variable
[09]: xref:Microsoft.PowerShell.Utility.Set-Variable
[10]: xref:Microsoft.PowerShell.Utility.Remove-Variable
[11]: xref:Microsoft.PowerShell.Utility.Clear-Variable
[12]: xref:Microsoft.PowerShell.Management.Get-ChildItem
[13]: xref:Microsoft.PowerShell.Management.Set-Location
[14]: xref:Microsoft.PowerShell.Management.Get-Location
[15]: xref:Microsoft.PowerShell.Core.Get-Help
[16]: about_Automatic_Variables.md
[17]: about_Providers.md
[18]: about_Variables.md

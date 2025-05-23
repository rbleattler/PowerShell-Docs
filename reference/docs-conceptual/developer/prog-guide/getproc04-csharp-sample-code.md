---
description: GetProc04 (C#) Sample Code
ms.date: 09/13/2016
title: GetProc04 (C#) Sample Code
---
# GetProc04 (C#) Sample Code

The following code shows the implementation of a `Get-Process` cmdlet that reports non-terminating
errors. This implementation calls the
[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)
method to report non-terminating errors.

> [!NOTE]
> You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft
> Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components. For
> download instructions, see
> [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> The downloaded source files are available in the **&lt;PowerShell Samples&gt;** directory.

## Code Sample

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## See Also

- [Windows PowerShell Programmer's Guide](./windows-powershell-programmer-s-guide.md)

- [Windows PowerShell SDK](../windows-powershell-reference.md)

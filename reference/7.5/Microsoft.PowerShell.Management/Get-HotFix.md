---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/23/2024
online version: https://learn.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.5&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
---

# Get-HotFix

## SYNOPSIS
Gets the hotfixes that are installed on local or remote computers.

## SYNTAX

### Default (Default)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### DESCRIPTION

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

## DESCRIPTION

> **This cmdlet is only available on the Windows platform.**

The `Get-HotFix` cmdlet uses the **Win32_QuickFixEngineering** WMI class to list hotfixes that are
installed on the local computer or specified remote computers.

## EXAMPLES

### Example 1: Get all hotfixes on the local computer

The `Get-HotFix` cmdlet gets all hotfixes installed on the local computer.

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### Example 2: Get hotfixes from multiple computers filtered by a string

The `Get-HotFix` command uses parameters to get hotfixes installed on remote computers. The results
are filtered by a specified description string.

```powershell
$hotFixParams = @{
    Description = "Security*"
    ComputerName = "Server01, Server02"
    Credential = "Domain01\admin01"
}
Get-HotFix @hotFixParams
```

`Get-HotFix` filters the output with the **Description** parameter and the string **Security** that
includes the asterisk (`*`) wildcard. The **ComputerName** parameter includes a comma-separated
string of remote computer names. The **Credential** parameter specifies a user account that has
permission to access the remote computers and run commands.

### Example 3: Verify if an update is installed and write computer names to a file

The commands in this example verify whether a particular update installed. If the update isn't
installed, the computer name is written to a text file.

```powershell
$A = Get-Content -Path ./Servers.txt
$A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
    { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

The `$A` variable contains computer names that were obtained by `Get-Content` from a text file. The
objects in `$A` are sent down the pipeline to `ForEach-Object`. An `if` statement uses the
`Get-HotFix` cmdlet with the **Id** parameter and a specific Id number for each computer name. If a
computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the
computer name to a file.

### Example 4: Get the most recent hotfix on the local computer

This example gets the most recent hotfix installed on a computer.

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-HotFix` sends the objects down the pipeline to the `Sort-Object` cmdlet. `Sort-Object` sorts
objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn**
date. The array notation `[-1]` selects the most recent installed hotfix.

## PARAMETERS

### -ComputerName

Specifies a remote computer. Type the NetBIOS name, an Internet Protocol (IP) address, or a fully
qualified domain name (FQDN) of a remote computer.

When the **ComputerName** parameter isn't specified, `Get-HotFix` runs on the local computer.

The **ComputerName** parameter doesn't rely on Windows PowerShell remoting. If your computer isn't
configured to run remote commands, use the **ComputerName** parameter.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Specifies a user account that has permission to access the computer and run commands. The default is
the current user

Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object
generated by the `Get-Credential` cmdlet. If you type a user name, you're prompted to enter the
password.

Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential)
object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> For more information about **SecureString** data protection, see
> [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

`Get-HotFix` uses the **Description** parameter to specify hotfix types. Wildcards are permitted.

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

Filters the `Get-HotFix` results for specific hotfix Ids. Wildcards aren't accepted.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable,
-InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose,
-WarningAction, and -WarningVariable. For more information, see
[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### String

You can pipe a string containing a computer name to this cmdlet.

## OUTPUTS

### System.Management.ManagementObject#root\cimv2\Win32_QuickFixEngineering

This cmdlet returns objects representing the hotfixes on the computer.

## NOTES

This cmdlet is only available on Windows platforms.

The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents
a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to
the current operating system. This class returns only the updates supplied by Component Based
Servicing (CBS). These updates aren't listed in the registry. Updates supplied by Microsoft Windows
Installer (MSI) or the [Windows Update](https://www.catalog.update.microsoft.com/) site aren't
returned by **Win32_QuickFixEngineering**. For more information, see
[Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).

The `Get-HotFix` output might vary on different operating systems.

## RELATED LINKS

[about_Arrays](/powershell/module/microsoft.powershell.core/About/about_Arrays)

[Add-Content](Add-Content.md)

[Get-Credential](xref:Microsoft.PowerShell.Security.Get-Credential)

[Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)

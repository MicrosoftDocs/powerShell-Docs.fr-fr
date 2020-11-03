---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: dbbbb352d1b3af8a0f05d2805fb42b7bb3ed27d3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201657"
---
# Get-CimSession

## SYNOPSIS
Obtient les objets de session CIM de la session active.

## SYNTAX

### ComputerNameSet (par défaut)

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### NameSet

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## Description

Par défaut, l’applet de commande obtient toutes les sessions CIM créées dans la session PowerShell active. Vous pouvez utiliser les paramètres de `Get-CimSession` pour obtenir les sessions qui sont destinées à des ordinateurs particuliers, ou vous pouvez identifier les sessions à l’aide de leurs noms ou d’autres identificateurs. `Get-CimSession` n’obtient pas les sessions CIM qui ont été créées dans d’autres sessions PowerShell ou qui ont été créées sur d’autres ordinateurs.

Pour plus d’informations sur les sessions CIM, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

## EXEMPLES

### Exemple 1 : récupérer des sessions CIM à partir de la session PowerShell active

Cet exemple crée des sessions CIM à l’aide [de New-CimSession](New-CimSession.md), puis obtient les sessions CIM à l’aide de `Get-CimSession` .

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exemple 2 : obtenir les sessions CIM sur un ordinateur spécifique

Cet exemple obtient les sessions CIM qui sont connectées à l’ordinateur nommé **Server02** .

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exemple 3 : obtenir la liste des sessions CIM, puis mettre en forme la liste

Cet exemple obtient toutes les sessions CIM dans la session PowerShell en cours et affiche une table contenant uniquement les propriétés **ComputerName** et **InstanceID** .

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### Exemple 4 : obtenir toutes les sessions CIM qui ont des noms spécifiques

Cet exemple obtient toutes les sessions CIM dont les noms commencent par **serv** .

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exemple 5 : obtenir une session CIM spécifique

Cet exemple obtient la session CIM dont l' **ID** est 2.

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETERS

### -ComputerName

Spécifie le nom de l’ordinateur auquel les sessions CIM doivent être connectées. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

Spécifie l’identificateur de la session CIM à récupérer. Pour plusieurs ID, utilisez des virgules pour séparer les ID ou utilisez l’opérateur de plage ( `..` ) pour spécifier une plage d’ID. Un **ID** est un entier qui identifie de façon unique la session CIM au sein de la session PowerShell active.

Pour plus d’informations sur l’opérateur de plage, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie les ID d’instance de la session CIM à récupérer.

**InstanceID** est un identificateur global unique (Guid) qui identifie de façon unique une session CIM. L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.

L' **InstanceID** est stocké dans la propriété **InstanceID** de l’objet qui représente une session CIM.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Obtient une ou plusieurs sessions CIM qui contiennent les noms conviviaux spécifiés. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### Microsoft.Management.Infrastructure.CimSession

## REMARQUES

## LIENS CONNEXES

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

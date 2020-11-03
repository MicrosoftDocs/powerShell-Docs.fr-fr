---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: eae279aa9c5d3a99a9a522254c5b792970f74297
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205186"
---
# Remove-CimSession

## SYNOPSIS
Supprime une ou plusieurs sessions CIM.

## SYNTAX

### CimSessionSet (par défaut)

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameSet

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-CimSession` applet de commande supprime un ou plusieurs objets de session CIM de la session PowerShell locale.

## EXEMPLES

### Exemple 1 : supprimer toutes les sessions CIM

Cet exemple récupère toutes les sessions CIM disponibles sur l’ordinateur local à l’aide de l’applet de commande [CimSession](Get-CimSession.md) , puis les supprime à l’aide de l’applet de commande `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

### Exemple 2 : supprimer une session CIM spécifique

Cet exemple supprime la session CIM qui a une valeur d' **ID** de 5.

```powershell
Remove-CimSession -Id 5
```

### Exemple 3 : afficher la liste des sessions CIM à supprimer à l’aide du paramètre WhatIf

Cet exemple utilise le paramètre commun **WhatIf** pour spécifier que la suppression ne doit pas être effectuée, mais uniquement en cas de résultat.

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETERS

### -CimSession

Spécifie les objets de session des sessions CIM à fermer.

Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les [`New-CimSession`](New-CimSession.md) applets de commande ou [`Get-CimSession`](Get-CimSession.md) .
Pour plus d’informations, consultez [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

Spécifie un tableau de noms d’ordinateurs. Supprime les sessions qui se connectent aux ordinateurs spécifiés. Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

Spécifie l’ID de la session CIM à supprimer. Spécifiez un ou plusieurs ID séparés par des virgules, ou utilisez l’opérateur de plage ( `..` ) pour spécifier une plage d’ID. Un **ID** est un entier qui identifie de façon unique la session CIM dans la session PowerShell active.

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

Spécifie l’ID d’instance de la session CIM à supprimer. **InstanceID** est un identificateur global unique (Guid) qui identifie de façon unique une session CIM. L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.

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

Spécifie le nom convivial de la session CIM à supprimer. Vous pouvez utiliser des caractères génériques avec ce paramètre.

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

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucun objet d’entrée.

## SORTIES

### System.Object

Cette applet de commande retourne un objet qui contient des informations de session CIM.

## REMARQUES

## LIENS CONNEXES

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)


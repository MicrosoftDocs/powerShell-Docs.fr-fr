---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204026"
---
# Get-ComputerRestorePoint

## SYNOPSIS
Obtient les points de restauration présents sur l'ordinateur local.

## SYNTAX

### ID (par défaut)

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### LastStatus

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## Description

L' `Get-ComputerRestorePoint` applet de commande obtient les points de restauration système de l’ordinateur local. De plus, il peut afficher l’état de la dernière tentative de restauration de l’ordinateur.

Vous pouvez utiliser les informations de `Get-ComputerRestorePoint` pour sélectionner un point de restauration. Par exemple, utilisez un numéro de séquence pour identifier un point de restauration pour l’applet de commande `Restore-Computer` .

Les points de restauration système et l' `Get-ComputerRestorePoint` applet de commande sont pris en charge uniquement sur les systèmes d’exploitation clients tels que Windows 10, Windows 7, Windows Vista et Windows XP.

## EXEMPLES

### Exemple 1 : récupération de tous les points de restauration du système

Dans cet exemple, `Get-ComputerRestorePoint` obtient tous les points de restauration du système de l’ordinateur local.

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### Exemple 2 : récupérer des numéros de séquence spécifiques

Cet exemple obtient les points de restauration du système pour des numéros de séquence spécifiques.

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

`Get-ComputerRestorePoint` utilise le paramètre **RestorePoint** pour spécifier un tableau de numéros séquentiels séparés par des virgules.

### Exemple 3 : afficher l’état d’une restauration du système

Cet exemple affiche l’état de la restauration système la plus récente sur l’ordinateur local.

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

`Get-ComputerRestorePoint` utilise le paramètre **LastStatus** pour afficher le résultat de la restauration système la plus récente.

### Exemple 4 : utiliser une expression pour convertir CreationTime

`Get-ComputerRestorePoint` génère le **CreationTime** sous forme de chaîne de date et d’heure de Windows Management Instrumentation (WMI).

Dans cet exemple, une variable stocke une expression qui convertit la chaîne **CreationTime** en un objet **DateTime** . Pour afficher les chaînes **CreationTime** avant qu’elles ne soient converties, utilisez une commande telle que `((Get-ComputerRestorePoint).CreationTime)` . Pour plus d’informations sur la chaîne de date et d’heure WMI, consultez [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

La `$date` variable stocke une table de hachage avec l’expression qui utilise la méthode **ConvertToDateTime** . L’expression convertit la valeur de la propriété **CreationTime** d’une chaîne WMI en objet **DateTime** .

`Get-ComputerRestorePoint` envoie les objets du point de restauration système vers le dessous du pipeline. `Select-Object` utilise le paramètre **Property** pour spécifier les propriétés à afficher. Pour chaque objet dans le pipeline, l’expression dans `$date` convertit le **CreationTime** et renvoie le résultat dans la propriété **Date** .

### Exemple 5 : utiliser une propriété pour obtenir un numéro de séquence

Cet exemple obtient un numéro de séquence à l’aide **de la propriété de numéro** de séquence et d’un index de tableau. La sortie contient uniquement le numéro de séquence.

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

`Get-ComputerRestorePoint` utilise la **propriété de l'** appel de fonction avec un index de tableau. L’index de tableau de `-1` obtient le numéro de séquence le plus récent dans le tableau.

## PARAMETERS

### -LastStatus

Indique que `Get-ComputerRestorePoint` obtient l’état de la dernière opération de restauration du système.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePoint

Spécifie les numéros de séquence des points de restauration du système. Vous pouvez spécifier un numéro de séquence unique ou un tableau de numéros séquentiels séparés par des virgules.

Si le paramètre **RestorePoint** n’est pas spécifié, `Get-ComputerRestorePoint` retourne tous les points de restauration du système de l’ordinateur local.

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Get-ComputerRestorePoint` .

## SORTIES

### System. Management. ManagementObject # root\default\SystemRestore ou chaîne

`Get-ComputerRestorePoint` retourne un objet **SystemRestore** , qui est une instance de la classe **SystemRestore** Windows Management Instrumentation (WMI).

Quand vous utilisez le paramètre **LastStatus** , `Get-ComputerRestorePoint` retourne une chaîne.

## REMARQUES

Pour exécuter une `Get-ComputerRestorePoint` commande sur Windows Vista et les versions ultérieures de Windows, ouvrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

`Get-ComputerRestorePoint` utilise la classe WMI **SystemRestore** .

## LIENS CONNEXES

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[SystemRestore](/windows/win32/sr/systemrestore)

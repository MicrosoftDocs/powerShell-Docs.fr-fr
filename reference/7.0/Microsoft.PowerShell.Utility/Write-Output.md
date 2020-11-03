---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: be2c506a928a96f66fd7318bdb0da1c57c5474b8
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208498"
---
# Write-Output

## SYNOPSIS
Envoie les objets spécifiés à la commande suivante du pipeline. Si la commande est la dernière commande du pipeline, les objets sont affichés sur la console.

## SYNTAX

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## Description

L' `Write-Output` applet de commande envoie l’objet spécifié dans le pipeline vers la commande suivante.
Si la commande est la dernière commande du pipeline, l'objet est affiché sur la console.

`Write-Output` envoie des objets vers le pipeline principal, également appelé « flux de sortie » ou « pipeline de réussite ». Pour envoyer des objets d'erreur dans le pipeline d'erreur, utilisez Write-Error.

Cette applet de commande est généralement utilisée dans les scripts pour afficher les chaînes et autres objets sur la console. L’un des alias intégrés pour `Write-Output` est `echo` et similaire aux autres interpréteurs de fonctionnalités qui utilisent `echo` , le comportement par défaut consiste à afficher la sortie à la fin d’un pipeline. Dans PowerShell, il n’est généralement pas nécessaire d’utiliser l’applet de commande dans les instances où la sortie est affichée par défaut. Par exemple, `Get-Process | Write-Output` équivaut à `Get-Process`. Ou, `echo "Home directory: $HOME"` peut être écrit `"Home directory: $HOME"` .

Par défaut, `Write-Output` énumère les collections fournies à l’applet de commande. Toutefois, `Write-Output` peut également être utilisé pour passer des collections dans le pipeline en tant qu’objet unique avec le paramètre **noenumerate** .

## EXEMPLES

### Exemple 1 : récupérer des objets et les écrire dans la console

```powershell
$P = Get-Process
Write-Output $P
```

La première commande récupère les processus en cours d’exécution sur l’ordinateur et les stocke dans la `$P` variable.

La deuxième et la troisième commande affichent les objets processus dans `$P` sur la console.

### Exemple 2 : passer la sortie à une autre applet de commande

```powershell
Write-Output "test output" | Get-Member
```

Cette commande dirige la chaîne « test output » vers l' `Get-Member` applet de commande, qui affiche les membres de la classe **System. String** , ce qui démontre que la chaîne a été passée le long du pipeline.

### Exemple 3 : supprimer l’énumération dans la sortie

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

Cette commande ajoute le paramètre **noenumerate** pour traiter une collection ou un tableau en tant qu’objet unique via le pipeline.

## PARAMETERS

### -InputObject

Spécifie les objets à envoyer dans le pipeline. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Noenumerate

Par défaut, l' `Write-Output` applet de commande énumère toujours sa sortie. Le paramètre **noenumerate** supprime le comportement par défaut et empêche l' `Write-Output` énumération de la sortie. Le paramètre **Noenumerate** n’a aucun effet si la commande est placée entre parenthèses, car les parenthèses forcent l’énumération. Par exemple, `(Write-Output 1,2,3)` énumère toujours le tableau.

> [!NOTE]
> Ce commutateur fonctionne correctement avec PowerShell Core 6,2 et versions ultérieures. Dans les versions antérieures de PowerShell Core, la collection est toujours énumérée, même avec l’utilisation de ce commutateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets vers `Write-Output` .

## SORTIES

### System. Management. Automation. PSObject

`Write-Output` retourne les objets qui sont envoyés en tant qu’entrée.

## REMARQUES

## LIENS CONNEXES

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Tee-Object](Tee-Object.md)

[Write-Debug](Write-Debug.md)

[Écriture-erreur](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

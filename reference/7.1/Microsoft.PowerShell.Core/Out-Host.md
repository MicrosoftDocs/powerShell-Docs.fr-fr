---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 9f53f137ecdd415e0185e380cba6ff817972b82e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205002"
---
# Out-Host

## SYNOPSIS
Envoie la sortie vers la ligne de commande.

## SYNTAX

### Tous

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L' `Out-Host` applet de commande envoie la sortie à l’hôte PowerShell pour l’affichage. L'hôte affiche la sortie sur la ligne de commande. Étant donné que `Out-Host` est la valeur par défaut, vous n’êtes pas obligé de la spécifier, sauf si vous souhaitez utiliser ses paramètres.

`Out-Host` est ajouté automatiquement à chaque commande exécutée. Elle transmet la sortie du pipeline à l’hôte qui exécute la commande. `Out-Host` ignore les séquences d’échappement ANSI. Les séquences d’échappement sont gérées par l’hôte. `Out-Host` passe des séquences d’échappement ANSI à l’hôte sans tenter de les interpréter ou de les modifier.

## EXEMPLES

### Exemple 1 : afficher la sortie une page à la fois

Cet exemple affiche les processus système une page à la fois.

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` Obtient le système traite et envoie les objets dans le pipeline. `Out-Host` utilise le paramètre de **pagination** pour afficher une page de données à la fois.

### Exemple 2 : utiliser une variable comme entrée

Cet exemple utilise des objets stockés dans une variable comme entrée pour `Out-Host` .

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` Obtient l’historique de la session PowerShell et stocke les objets dans la `$io` variable.
`Out-Host` utilise le paramètre **InputObject** pour spécifier la `$io` variable et afficher l’historique.

## PARAMETERS

### -InputObject

Spécifie les objets qui sont écrits dans la console. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Pagination

Indique que `Out-Host` affiche une page de sortie à la fois et attend une entrée utilisateur avant l’affichage des pages restantes. Par défaut, toute la sortie est affichée sur une seule page. La taille de la page est déterminée par les caractéristiques de l'hôte.

Appuyez sur la barre d' <kbd>espace</kbd> pour afficher la page de sortie suivante ou la touche <kbd>entrée</kbd> pour afficher la ligne de sortie suivante. Appuyez sur <kbd>Q</kbd> pour quitter.

La **pagination** est semblable à la commande **More** .

> [!NOTE]
> Le paramètre de **pagination** n’est pas pris en charge par l’hôte ISE PowerShell.

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

Vous pouvez envoyer des objets vers le dessous du pipeline `Out-Host` .

## SORTIES

### Aucun

`Out-Host` ne génère aucune sortie. Elle envoie des objets à l’hôte pour l’affichage.

## REMARQUES

Le paramètre de **pagination** n’est pas pris en charge par tous les hôtes PowerShell. Par exemple, si vous utilisez le paramètre de **pagination** dans PowerShell ISE, l’erreur suivante s’affiche : `out-lineoutput : The method or operation is not implemented.`

Les applets de commande qui contiennent le verbe **out** , `Out-` , ne mettent pas en forme les objets. Ils affichent les objets et les envoient à la destination d’affichage spécifiée. Si vous envoyez un objet non mis en forme à une applet de commande `Out-` , l’applet de commande l’envoie à une applet de commande de mise en forme avant de le restituer.

Les `Out-` applets de commande n’ont pas de paramètres pour les noms ou les chemins d’accès de fichier. Pour envoyer des données à une `Out-` applet de commande, utilisez le pipeline pour envoyer la sortie d’une commande PowerShell à l’applet de commande. Ou vous pouvez stocker des données dans une variable et utiliser le paramètre **InputObject** pour transmettre les données à l’applet de commande.

`Out-Host` envoie des données, mais ne produit pas d’objet de sortie. Si vous dirigez la sortie de `Out-Host` vers l’applet de commande `Get-Member` , `Get-Member` signale qu’aucun objet n’a été spécifié.

## LIENS CONNEXES

[Clear-Host](Clear-Host.md)

[Out-Default](Out-Default.md)

[Out-File](../Microsoft.PowerShell.Utility/Out-File.md)

[Out-Null](Out-Null.md)

[Out-Printer](../Microsoft.PowerShell.Utility/Out-Printer.md)

[Out-String](../Microsoft.PowerShell.Utility/Out-String.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)


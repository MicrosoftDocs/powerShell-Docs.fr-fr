---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: f2b3e20685ee52a7f9ca1bfd23af5fc5bca24001
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599164"
---
# Out-Printer

## SYNOPSIS
Envoie la sortie vers une imprimante.

## SYNTAXE

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L' `Out-Printer` applet de commande envoie la sortie vers l’imprimante par défaut ou vers une autre imprimante, si celle-ci est spécifiée.

> [!NOTE]
> Cette applet de commande a été réintroduite dans PowerShell 7. Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.

## EXEMPLES

### Exemple 1 : envoyer un fichier à imprimer sur l’imprimante par défaut

Cet exemple montre comment imprimer un fichier, même si `Out-Printer` n’a pas de paramètre **path** .

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content`Obtient le contenu du `readme.txt` fichier dans le répertoire actif et le `Out-Printer` dirige vers, ce qui l’envoie à l’imprimante par défaut.

### Exemple 2 : imprimer une chaîne sur une imprimante distante

Cet exemple imprime `Hello, World` sur l’imprimante de **couleur PRT-6B** sur SERVEUR01.

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

Le paramètre **Name** sélectionne une imprimante spécifique, plutôt que la valeur par défaut.

### Exemple 3 : imprimer une rubrique d’aide sur l’imprimante par défaut

Cet exemple imprime la version complète de la rubrique d’aide pour `Get-CimInstance` .

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` Obtient la version complète de la rubrique d’aide de `Get-CimInstance` et la stocke dans la `$H` variable. Le paramètre **InputObject** passe la valeur de `$H` à `Out-Printer` .

## PARAMETERS

### -InputObject

Spécifie les objets à envoyer à l'imprimante. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

### -Name

Envoie la sortie vers l’imprimante spécifiée. Le **nom du paramètre est facultatif** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers `Out-Printer` .

## SORTIES

### None

`Out-Printer` ne retourne aucun objet.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Les applets de commande qui contiennent le `Out` verbe ne mettent pas en forme les objets. Ils les affichent et les envoient à la destination d’affichage spécifiée. Si vous envoyez un objet non mis en forme à une applet de commande `Out` , l’applet de commande l’envoie à une applet de commande de mise en forme avant de le restituer.

`Out-Printer` envoie des données à l’imprimante, mais n’émet pas d’objets de sortie au pipeline. Si vous dirigez la sortie de `Out-Printer` vers `Get-Member` , `Get-Member` signale qu’aucun objet n’a été spécifié.

## LIENS CONNEXES

[Out-File](Out-File.md)

[Out-String](Out-String.md)

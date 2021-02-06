---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: d2c0abb0e6742de3e316fe964d5945375591ef4d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598757"
---
# Add-History

## SYNOPSIS
Ajoute des entrées à l'historique de session.

## SYNTAXE

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## Description

L' `Add-History` applet de commande ajoute des entrées à la fin de l’historique de session, autrement dit, la liste des commandes entrées pendant la session active.

L'historique de session est une liste des commandes entrées pendant la session. L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande. Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser. Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).

L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .
Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé. Cette applet de commande fonctionne uniquement avec l’historique de session. Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

Vous pouvez utiliser l' `Get-History` applet de commande pour obtenir les commandes et les passer à `Add-History` , ou vous pouvez exporter les commandes vers un fichier CSV ou XML, puis importer les commandes et transmettre le fichier importé à `Add-History` . Vous pouvez utiliser cette applet de commande pour ajouter des commandes spécifiques à l'historique ou pour créer un fichier d'historique unique qui inclut des commandes issues de plusieurs sessions.

## EXEMPLES

### Exemple 1 : ajouter des commandes à l’historique d’une autre session

Cet exemple ajoute les commandes entrées dans une session PowerShell à l’historique d’une autre session PowerShell.

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

La première commande récupère les objets qui représentent les commandes dans l’historique et les exporte dans le `History.csv` fichier.

La seconde commande est entrée sur la ligne de commande d'une autre session. Elle utilise l' `Import-Csv` applet de commande pour importer les objets dans le `History.csv` fichier. L’opérateur de pipeline ( `|` ) passe les objets à l' `Add-History` applet de commande, ce qui ajoute les objets représentant les commandes du `History.csv` fichier à l’historique de session actuel.

### Exemple 2 : importer et exécuter des commandes

Cet exemple importe des commandes à partir du `History.xml` fichier, les ajoute à l’historique de session actuel, puis exécute les commandes dans l’historique combiné.

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

La première commande utilise l' `Import-Clixml` applet de commande pour importer un historique de commandes qui a été exporté dans le `History.xml` fichier. L’opérateur de pipeline passe les commandes à l’applet de commande `Add-History` , qui ajoute les commandes à l’historique de session actuel. Le paramètre **PassThru** passe les objets représentant les commandes ajoutées dans le pipeline.

La commande utilise ensuite l' `ForEach-Object` applet de commande pour appliquer la `Invoke-History` commande à chacune des commandes de l’historique combiné. La `Invoke-History` commande est mise en forme comme un bloc de script, placé entre accolades ( `{}` ), comme requis par le paramètre **Process** de l’applet de commande `ForEach-Object` .

### Exemple 3 : ajouter des commandes dans l’historique à la fin de l’historique

Cet exemple ajoute les cinq premières commandes dans l’historique à la fin de la liste d’historique.

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

L' `Get-History` applet de commande obtient les cinq commandes se terminant par la commande 5. L’opérateur de pipeline les transmet à l’applet de commande `Add-History` , qui les ajoute à l’historique actuel. La `Add-History` commande n’inclut aucun paramètre, mais PowerShell associe les objets transmis via le pipeline au paramètre **InputObject** de `Add-History` .

### Exemple 4 : ajouter des commandes dans un fichier. csv à l’historique actuel

Cet exemple ajoute les commandes du `History.csv` fichier à l’historique de session actuel.

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

L' `Import-Csv` applet de commande importe les commandes dans le `History.csv` fichier et stocke son contenu dans la variable `$a` .

La deuxième commande utilise l' `Add-History` applet de commande pour ajouter les commandes de `History.csv` à l’historique de session actuel. Elle utilise le paramètre **InputObject** pour spécifier la `$a` variable et le paramètre **PassThru** pour générer un objet à afficher sur la ligne de commande. Sans le paramètre **PassThru** , l' `Add-History` applet de commande ne génère pas de sortie.

### Exemple 5 : ajouter des commandes dans un fichier. XML à l’historique actuel

Cet exemple ajoute les commandes du `history.xml` fichier à l’historique de session actuel.

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

Le paramètre **InputObject** passe les résultats de la commande entre parenthèses à l' `Add-History` applet de commande. La commande entre parenthèses, qui est exécutée en premier, importe le `history.xml` fichier dans PowerShell. L' `Add-History` applet de commande ajoute ensuite les commandes du fichier à l’historique de session.

## PARAMETERS

### -InputObject

Spécifie un tableau d’entrées à ajouter à l’historique en tant qu’objet **HistoryInfo** dans l’historique de session.
Vous pouvez utiliser ce paramètre pour envoyer un objet **HistoryInfo** , tel que ceux qui sont retournés par `Get-History` les `Import-Clixml` `Import-Csv` applets de commande, ou, à `Add-History` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PassThru

Indique que cette applet de commande retourne un objet **HistoryInfo** pour chaque entrée d’historique. Par défaut, cette applet de commande ne génère aucun résultat.

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

### Microsoft. PowerShell. Commands. HistoryInfo

Vous pouvez diriger un objet **HistoryInfo** vers cette applet de commande.

## SORTIES

### None ou Microsoft. PowerShell. Commands. HistoryInfo

Cette applet de commande retourne un objet **HistoryInfo** si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

L’historique de session est une liste des commandes entrées pendant la session avec l’ID. L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande. Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser. Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).

Pour spécifier les commandes à ajouter à l'historique, utilisez le paramètre **InputObject**. La `Add-History` commande accepte uniquement les objets **HistoryInfo** , tels que ceux retournés pour chaque commande par l’applet de commande `Get-History` . Vous ne pouvez pas lui passer un chemin d'accès et un nom de fichier, ni une liste de commandes.

Vous pouvez utiliser le paramètre **InputObject** pour passer un fichier d’objets **HistoryInfo** à `Add-History` . Pour ce faire, exportez les résultats d’une `Get-History` commande dans un fichier à l’aide de l’applet de commande `Export-Csv` ou `Export-Clixml` , puis importez le fichier à l’aide des `Import-Csv` applets de commande ou `Import-Clixml` . Vous pouvez ensuite passer le fichier d’objets **HistoryInfo** importés à `Add-History` via un pipeline ou dans une variable. Pour plus d'informations, consultez les exemples.

Le fichier d’objets **HistoryInfo** que vous transmettez à l’applet de commande `Add-History` doit inclure les informations de type, les en-têtes de colonne et toutes les propriétés des objets **HistoryInfo** . Si vous envisagez de renvoyer les objets à `Add-History` , n’utilisez pas le paramètre **NoTypeInformation** de l’applet de commande `Export-Csv` et ne supprimez pas les informations de type, les en-têtes de colonne ni les champs dans le fichier.

Pour modifier l’historique de session, exportez la session dans un fichier CSV ou XML, modifiez le fichier, importez le fichier et utilisez `Add-History` pour l’ajouter à l’historique de session actuel.

## LIENS CONNEXES

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)


---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: ae9cc8b0daf9a3c25d4385fbca156e8a146334da
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "93206365"
---
# Get-History

## SYNOPSIS
Obtient une liste des commandes entrées pendant la session active.

## SYNTAX

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## Description

L' `Get-History` applet de commande obtient l’historique de session, autrement dit, la liste des commandes entrées pendant la session active.

PowerShell gère automatiquement un historique de chaque session. Le nombre d’entrées dans l’historique de session est déterminé par la valeur de la `$MaximumHistoryCount` variable de préférence. À compter de Windows PowerShell 3,0, la valeur par défaut est `4096` . Par défaut, les fichiers d'historique sont enregistrés dans le répertoire de base, mais vous pouvez enregistrer le fichier à n'importe quel emplacement. Pour plus d’informations sur les fonctionnalités de l’historique dans PowerShell, consultez [about_History](About/about_History.md).

L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .
Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé. Cette applet de commande fonctionne uniquement avec l’historique de session. Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPLES

### Exemple 1 : afficher l’historique de la session

Cet exemple obtient les entrées de l’historique de session. L’affichage par défaut montre chaque commande et son ID, qui indique l’ordre dans lequel elles ont été exécutées.

```powershell
Get-History
```

### Exemple 2 : obtenir des entrées qui incluent une chaîne

Cet exemple obtient les entrées de l’historique de commandes qui incluent le service de chaîne. La première commande obtient toutes les entrées de l'historique de session. L’opérateur de pipeline ( `|` ) passe les résultats à l' `Where-Object` applet de commande, qui sélectionne uniquement les commandes qui incluent le service.

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### Exemple 3 : exporter les entrées de l’historique jusqu’à un ID spécifique

Cet exemple obtient les cinq entrées d’historique les plus récentes se terminant par l’entrée 7. L’opérateur de pipeline passe le résultat à l’applet de commande `Export-Csv` , qui met en forme l’historique sous forme de texte séparé par des virgules et l’enregistre dans le fichier History.csv. Le fichier comprend les données qui s’affichent lorsque vous mettez en forme l’historique sous forme de liste. Cela comprend l’État et les heures de début et de fin de la commande.

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### Exemple 4 : afficher la commande la plus récente

Cet exemple obtient la dernière commande de l’historique de commande. La dernière commande est la dernière commande entrée. Cette commande utilise le paramètre **Count** pour afficher une seule commande. Par défaut, `Get-History` obtient les commandes les plus récentes. Cette commande peut être abrégée en « h -c 1 » et équivaut à appuyer sur la touche flèche vers le haut.

```powershell
Get-History -Count 1
```

### Exemple 5 : afficher toutes les propriétés des entrées de l’historique

Cet exemple affiche toutes les propriétés des entrées de l’historique de session. L’opérateur de pipeline passe les résultats d’une `Get-History` commande à l’applet de commande `Format-List` , qui affiche toutes les propriétés de chaque entrée d’historique. Cela comprend l’ID, l’État et les heures de début et de fin de la commande.

```powershell
Get-History | Format-List -Property *
```

## PARAMETERS

### -Nombre

Spécifie le nombre d’entrées d’historique les plus récentes que cette applet de commande obtient. Par défaut, `Get-History` obtient toutes les entrées dans l’historique de session. Si vous utilisez à la fois les paramètres **Count** et **Id** dans une commande, l'affichage se termine par la commande spécifiée par le paramètre **Id** .

Dans Windows PowerShell 2,0, par défaut, `Get-History` obtient les inscriptions les plus récentes de 32.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie un tableau des ID d’entrées dans l’historique de session. `Get-History` Obtient uniquement les entrées spécifiées. Si vous utilisez à la fois les paramètres **ID** et **Count** dans une commande, `Get-History` obtient les entrées les plus récentes se terminant par l’entrée spécifiée par le paramètre **ID** .

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Int64

Vous pouvez diriger un ID d’historique vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. HistoryInfo

Cette applet de commande retourne un objet d’historique pour chaque élément de l’historique qu’il obtient.

## REMARQUES

L'historique de session est une liste des commandes entrées pendant la session. L’historique de session représente l’ordre d’exécution, l’État et les heures de début et de fin de la commande. Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser. Pour plus d’informations sur l’historique des commandes, consultez [about_History](About/about_History.md).

À compter de Windows PowerShell 3,0, la valeur par défaut de la `$MaximumHistoryCount` variable de préférence est `4096` . Dans Windows PowerShell 2,0, la valeur par défaut est `64` . Pour plus d’informations sur la `$MaximumHistoryCount` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

## LIENS CONNEXES

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Invoke-History](Invoke-History.md)

[about_History](About/about_History.md)

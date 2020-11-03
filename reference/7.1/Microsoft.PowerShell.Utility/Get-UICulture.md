---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 3e1ae99f3e2bd52d26e9c567fcc8184b07c71a4a
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200973"
---
# Get-UICulture

## SYNOPSIS
Obtient les paramètres de culture d’interface utilisateur actuels dans le système d’exploitation.

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## Description

L' `Get-UICulture` applet de commande obtient des informations sur les paramètres de culture de l’interface utilisateur (IU) actuelle pour Windows.
La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.

Vous pouvez également utiliser l' `Get-Culture` applet de commande, qui obtient la culture actuelle sur le système.
La culture détermine le format d'affichage d'éléments tels que nombres, devises et dates.

## EXEMPLES

### Exemple 1 : récupération de la culture de l’interface utilisateur

```powershell
Get-UICulture
```

Cette commande obtient les informations sur la culture d'interface utilisateur actuelle.

### Exemple 2 : obtenir la culture de l’interface utilisateur et mettre en forme les résultats

```powershell
Get-UICulture | Format-List *
```

Cette commande affiche les valeurs de toutes les propriétés de la culture d'interface utilisateur actuelle dans une liste.

### Exemple 3 : récupération de la valeur de la propriété Calendar

```powershell
(Get-UICulture).Calendar
```

Cette commande affiche les valeurs actuelles de la propriété **Calendar** de la culture d’interface utilisateur actuelle.
Calendar n'est qu'une des propriétés de la culture d'interface utilisateur.
Pour afficher toutes les propriétés, tapez `Get-UICulture | Get-Member` .

### Exemple 4 : récupération du modèle de date abrégée

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

Cette commande affiche le modèle de date courte de la culture d'interface utilisateur actuelle.
Pour afficher toutes les sous-propriétés de la propriété **DateTimeFormat** de la culture d’interface utilisateur, tapez `(Get-UICulture).DateTimeFormat | gm` .

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Globalization. CultureInfo, Microsoft. PowerShell. VistaCultureInfo

`Get-UICulture` retourne un objet qui représente la culture d’interface utilisateur actuelle.
Dans Windows PowerShell 3,0, elle retourne un objet **CultureInfo** .
Dans Windows PowerShell 2,0, elle retourne un objet **VistaCultureInfo** .

## REMARQUES

- Vous pouvez également utiliser les `$PsCulture` `$PsUICulture` variables et. La `$PsCulture` variable stocke le nom de la culture actuelle et la `$PsUICulture` variable stocke le nom de la culture d’interface utilisateur actuelle.

## LIENS CONNEXES


---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 08ff101019db6baa8b84f56e862f140a028e9539
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204646"
---
# Get-Alias

## SYNOPSIS
Obtient l'alias pour la session active.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### Définition

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-alias** obtient les alias de la session active.
Cela comprend les alias intégrés, les alias que vous avez définis ou importés, et les alias que vous avez ajoutés à votre profil PowerShell.

Par **défaut, l’alias d'** accès prend un alias et retourne le nom de la commande.
Quand vous utilisez le paramètre de *définition* , la commande **obtenir un alias** prend un nom de commande et retourne ses alias.

À compter de Windows PowerShell 3,0, la tâche **obtenir un alias** affiche les noms d’alias sans trait d’Union dans un `<alias> -> <definition>` format pour faciliter encore la recherche des informations dont vous avez besoin.

## EXEMPLES

### Exemple 1 : récupérer tous les alias dans la session active

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

Cette commande obtient tous les alias dans la session active.

La sortie indique le `<alias> -> <definition>` format qui a été introduit dans Windows PowerShell 3,0.
Ce format est utilisé uniquement pour les alias qui n'incluent pas de traits d'union, étant donné que les alias avec des traits d'union sont des noms généralement préférés aux surnoms pour les applets de commande et les fonctions.

### Exemple 2 : récupérer des alias par nom

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

Cette commande obtient tous les alias qui commencent par GP ou SP, à l’exception des alias qui se terminent par PS.

### Exemple 3 : obtenir des alias pour une applet de commande

```powershell
Get-Alias -Definition Get-ChildItem
```

Cette commande obtient les alias de l'applet de commande Get-ChildItem.

Par défaut, l’applet de commande **obtenir-alias** obtient le nom de l’élément lorsque vous connaissez l’alias.
Le paramètre de *définition* obtient l’alias quand vous connaissez le nom de l’élément.

### Exemple 4 : récupérer des alias par propriété

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

Cette commande obtient tous les alias dans lesquels la valeur de la propriété Options est ReadOnly.
Cette commande offre un moyen rapide de rechercher les alias intégrés à PowerShell, car ils possèdent l’option ReadOnly.

Options n’est qu’une des propriétés des objets AliasInfo que obtient **-alias** .
Pour rechercher toutes les propriétés et méthodes des objets AliasInfo, tapez `Get-Alias | get-member` .

### Exemple 5 : récupérer des alias par nom et filtrer par lettre initiale

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

Cet exemple obtient les alias des commandes qui ont des noms se terminant par « -PSSession », à l'exception de ceux qui commencent par « e ».

La commande utilise le paramètre *scope* pour appliquer la commande dans l’étendue globale.
Cela est utile dans les scripts quand vous souhaitez obtenir les alias figurant dans la session.

## PARAMETERS

### -Definition

Obtient les alias pour l'élément spécifié.
Entrez le nom d'une applet de commande, d'une fonction, d'un script, d'un fichier ou d'un fichier exécutable.

Ce paramètre est appelé *définition* , car il recherche le nom de l’élément dans la propriété de définition de l’objet alias.

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

Omet les éléments spécifiés.
La valeur de ce paramètre qualifie les paramètres Name et Definition.
Entrez un nom, une définition ou un modèle, tel que « s* ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Spécifie les alias que cette applet de commande obtient.
Les caractères génériques sont autorisés.
Par défaut, `Get-Alias` récupère tous les alias définis pour la session active.
Le **nom du paramètre est facultatif** .
Vous pouvez également diriger les noms d’alias vers `Get-Alias` .

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Étendue

Spécifie l’étendue pour laquelle cette applet de commande obtient des alias.
Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)

Local est la valeur par défaut.
Pour plus d'informations, consultez about_Scopes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger les noms d’alias vers la valeur de l' **alias** .

## SORTIES

### System. Management. Automation. AliasInfo

La **fonction de récupération d’alias** retourne un objet qui représente chaque alias.
L' **alias « obtenir »** retourne le même objet pour chaque alias, mais PowerShell utilise un format basé sur les flèches pour afficher les noms des alias sans trait d’Union.

## REMARQUES

- Pour créer un alias, utilisez Set-Alias ou New-Alias. Pour supprimer un alias, utilisez Remove-Item.
- Le format de nom d'alias basé sur les flèches n'est pas utilisé pour les alias qui comportent un trait d'union. Ceux-ci sont susceptibles d'être des noms de remplacement par défaut pour les applets de commande et les fonctions, au lieu d'être des abréviations ou des surnoms standard.

## LIENS CONNEXES

[Export-Alias](Export-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Fournisseur Alias](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

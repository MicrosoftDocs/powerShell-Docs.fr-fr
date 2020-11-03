---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: cb3b851b9634c052cf9d680fcb7f7e1215f9870d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201382"
---
# Get-PSProvider

## SYNOPSIS
Obtient des informations sur le fournisseur PowerShell spécifié.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## Description

L' `Get-PSProvider` applet de commande obtient les fournisseurs PowerShell dans la session active.
Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.

Les fournisseurs PowerShell vous permettent d’accéder à divers magasins de données comme s’ils étaient des lecteurs de système de fichiers.
Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## EXEMPLES

### Exemple 1 : afficher la liste de tous les fournisseurs disponibles

```powershell
Get-PSProvider
```

Cette commande affiche la liste de tous les fournisseurs PowerShell disponibles.

### Exemple 2 : afficher la liste de tous les fournisseurs PowerShell qui commencent par des lettres spécifiées

```powershell
Get-PSProvider f*, r* | Format-List
```

Cette commande affiche la liste de tous les fournisseurs PowerShell dont le nom commence par la lettre f ou r.

### Exemple 3 : Rechercher les composants logiciels enfichables ou les modules qui ont ajouté des fournisseurs à votre session

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Ces commandes recherchent les modules ou composants logiciels enfichables PowerShell qui ont ajouté des fournisseurs à votre session.
Tous les éléments PowerShell, y compris les fournisseurs, proviennent d’un composant logiciel enfichable ou d’un module.

Ces commandes utilisent les propriétés PSSnapin et module de l’objet **providerinfo retourné par** qui `Get-PSProvider` retourne.
Les valeurs de ces propriétés contiennent le nom du module ou du composant logiciel enfichable qui ajoute le fournisseur.

La première commande obtient tous les fournisseurs présents dans la session et les présente sous forme de tableau indiquant les valeurs de leurs propriétés Name, Module et PSSnapin.

La deuxième commande utilise l' `Where-Object` applet de commande pour récupérer les fournisseurs qui proviennent du composant logiciel enfichable **Microsoft. PowerShell. Security** .

### Exemple 4 : résolution du chemin d’accès de la propriété de démarrage du fournisseur de système de fichiers

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

Cet exemple montre que le symbole tilde (~) représente la valeur de la propriété de **démarrage** du fournisseur FileSystem.
La valeur de la propriété de **démarrage** est facultative, mais pour le fournisseur **FileSystem** , elle est définie en tant que `$env:homedrive\$env:homepath` ou `$home` .

## PARAMETERS

### -PSProvider

Spécifie le nom ou les noms des fournisseurs PowerShell sur lesquels cette applet de commande obtient des informations.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### String[]

Vous pouvez diriger une ou plusieurs chaînes de nom de fournisseur vers cette applet de commande.

## SORTIES

### System. Management. Automation. Providerinfo retourné par

Cette applet de commande retourne des objets qui représentent les fournisseurs PowerShell dans la session.

## REMARQUES

## LIENS CONNEXES

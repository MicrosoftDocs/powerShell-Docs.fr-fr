---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203986"
---
# Get-PSProvider

## SYNOPSIS
Obtient des informations se rapportant au fournisseur Windows PowerShell spécifié.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-PSProvider** obtient les fournisseurs Windows PowerShell dans la session active.
Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.

Les fournisseurs Windows PowerShell vous permettent d’accéder à divers magasins de données, comme s’ils étaient des lecteurs de système de fichiers.
Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez about_Providers.

## EXEMPLES

### Exemple 1 : afficher la liste de tous les fournisseurs disponibles

```
PS C:\> Get-PSProvider
```

Cette commande affiche la liste de tous les fournisseurs Windows PowerShell disponibles.

### Exemple 2 : afficher une liste de tous les fournisseurs Windows PowerShell qui commencent par des lettres spécifiées

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

Cette commande affiche une liste de tous les fournisseurs Windows PowerShell dont le nom commence par la lettre f ou r.

### Exemple 3 : Rechercher les composants logiciels enfichables ou les modules qui ont ajouté des fournisseurs à votre session

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Ces commandes recherchent les modules ou les composants logiciels enfichables Windows PowerShell qui ont ajouté des fournisseurs à votre session.
Tous les éléments Windows PowerShell, y compris les fournisseurs, proviennent d’un module ou d’un composant logiciel enfichable.

Ces commandes utilisent les propriétés PSSnapin et module de l’objet **providerinfo retourné par** retourné par la méthode **-PSProvider** .
Les valeurs de ces propriétés contiennent le nom du module ou du composant logiciel enfichable qui ajoute le fournisseur.

La première commande obtient tous les fournisseurs présents dans la session et les présente sous forme de tableau indiquant les valeurs de leurs propriétés Name, Module et PSSnapin.

La deuxième commande utilise l’applet de commande Where-Object pour récupérer les fournisseurs qui proviennent du composant logiciel enfichable **Microsoft. PowerShell. Security** .

### Exemple 4 : résolution du chemin d’accès de la propriété de démarrage du fournisseur de système de fichiers

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

Cet exemple montre que le symbole tilde (~) représente la valeur de la propriété Home du fournisseur de système de fichiers.
La valeur de la propriété de démarrage est facultative, mais pour le fournisseur FileSystem, elle est définie comme $env : HomeDrive \$ env : homepath ou $Home.

## PARAMETERS

### -PSProvider
Spécifie le nom ou les noms des fournisseurs Windows PowerShell à propos desquels cette applet de commande obtient des informations.

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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### String[]

Vous pouvez diriger une ou plusieurs chaînes de nom de fournisseur vers cette applet de commande.

## SORTIES

### System. Management. Automation. Providerinfo retourné par
Cette applet de commande retourne des objets qui représentent les fournisseurs Windows PowerShell dans la session.

## REMARQUES

## LIENS CONNEXES

## LIENS CONNEXES

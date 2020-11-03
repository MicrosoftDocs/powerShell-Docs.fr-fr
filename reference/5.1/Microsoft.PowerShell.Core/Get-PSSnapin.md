---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202286"
---
# Get-PSSnapin

## SYNOPSIS
Obtient les composants logiciels enfichables Windows PowerShell sur l'ordinateur.

## SYNTAX

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-PSSnapin** obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session active ou qui ont été inscrits sur le système.
Cette applet de commande répertorie les composants logiciels enfichables dans l’ordre dans lequel ils sont détectés.

L’option **obtenir-PSSnapin** obtient uniquement les composants logiciels enfichables inscrits. Pour inscrire un composant logiciel enfichable Windows PowerShell, utilisez l’outil InstallUtil inclus dans le Microsoft .NET Framework 2,0.
Pour plus d’informations, voir [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://go.microsoft.com/fwlink/?LinkID=143619) dans MSDN Library.

À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans Windows PowerShell sont empaquetées dans des modules.
L'exception est **Microsoft.PowerShell.Core** , qui est un composant logiciel enfichable (PSSnapin).
Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session.
Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l’applet de commande Import-Module pour les importer.

## EXEMPLES

### Exemple 1 : récupérer les composants logiciels enfichables qui sont actuellement chargés

```
PS C:\> Get-PSSnapIn
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell qui sont actuellement chargés dans la session.
Cela inclut les composants logiciels enfichables qui sont installés avec Windows PowerShell et ceux qui ont été ajoutés à la session.

### Exemple 2 : obtenir les composants logiciels enfichables qui ont été inscrits

```
PS C:\> get-PSSnapIn -Registered
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell qui ont été inscrits sur l'ordinateur, y compris ceux qui ont déjà été ajoutés à la session.
La sortie n'inclut pas les composants logiciels enfichables qui sont installés avec Windows PowerShell ni les bibliothèques de liens dynamiques (DLL) de composants logiciels enfichables Windows PowerShell qui n'ont pas encore été inscrites sur le système.

### Exemple 3 : obtenir les composants logiciels enfichables actuels qui correspondent à une chaîne

```
PS C:\> Get-PSSnapIn -Name smp*
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell dans la session active dont les noms commencent par SMP.

## PARAMETERS

### -Name
Spécifie un tableau de noms de composants logiciels enfichables.
Cette applet de commande obtient uniquement les composants logiciels enfichables Windows PowerShell spécifiés. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Inscrit
Indique que cette applet de commande obtient les composants logiciels enfichables Windows PowerShell qui ont été inscrits sur le système, même s’ils n’ont pas encore été ajoutés à la session.

Les composants logiciels enfichables qui sont installés avec Windows PowerShell n'apparaissent pas dans cette liste.

Sans ce paramètre, l’option **obtenir-PSSnapin** obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session.

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

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSSnapInInfo
Get-PSSnapin retourne un objet pour chaque composant logiciel enfichable qu'il obtient.

## REMARQUES

* À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec Windows PowerShell sont empaquetées dans des modules. Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de Windows PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables ( **PSSnapin** ). L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable. En outre, les sessions à distance, telles que celles démarrées par l’applet de commande New-PSSession, sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.

  Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) dans MSDN Library.

## LIENS CONNEXES

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)

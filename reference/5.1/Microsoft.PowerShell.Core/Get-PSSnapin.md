---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 156cadecd87910e3c3312e84929b16709770641d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388669"
---
# Get-PSSnapin

## SYNOPSIS
Obtient les composants logiciels enfichables Windows PowerShell sur l'ordinateur.

## SYNTAXE

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## DESCRIPTION

L' `Get-PSSnapin` applet de commande obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session active ou qui ont été inscrits sur le système. Cette applet de commande répertorie les composants logiciels enfichables dans l’ordre dans lequel ils sont détectés.

`Get-PSSnapin` Obtient uniquement les composants logiciels enfichables inscrits. Pour inscrire un composant logiciel enfichable Windows PowerShell, utilisez l’outil InstallUtil inclus dans le Microsoft .NET Framework 2,0. Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans Windows PowerShell sont empaquetées dans des modules. L'exception est **Microsoft.PowerShell.Core** , qui est un composant logiciel enfichable (PSSnapin).
Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session. Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l' `Import-Module` applet de commande pour les importer.

## EXEMPLES

### Exemple 1 : récupérer les composants logiciels enfichables qui sont actuellement chargés

```
PS C:\> Get-PSSnapIn
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell qui sont actuellement chargés dans la session. Cela inclut les composants logiciels enfichables qui sont installés avec Windows PowerShell et ceux qui ont été ajoutés à la session.

### Exemple 2 : obtenir les composants logiciels enfichables qui ont été inscrits

```
PS C:\> get-PSSnapIn -Registered
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell qui ont été inscrits sur l'ordinateur, y compris ceux qui ont déjà été ajoutés à la session. La sortie n'inclut pas les composants logiciels enfichables qui sont installés avec Windows PowerShell ni les bibliothèques de liens dynamiques (DLL) de composants logiciels enfichables Windows PowerShell qui n'ont pas encore été inscrites sur le système.

### Exemple 3 : obtenir les composants logiciels enfichables actuels qui correspondent à une chaîne

```
PS C:\> Get-PSSnapIn -Name smp*
```

Cette commande obtient les composants logiciels enfichables Windows PowerShell dans la session active dont les noms commencent par SMP.

## PARAMÈTRES

### -Name

Spécifie un tableau de noms de composants logiciels enfichables. Cette applet de commande obtient uniquement les composants logiciels enfichables Windows PowerShell spécifiés. Les caractères génériques sont autorisés.

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

Sans ce paramètre, `Get-PSSnapin` obtient les composants logiciels enfichables Windows PowerShell qui ont été ajoutés à la session.

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

`Get-PSSnapin` retourne un objet pour chaque composant logiciel enfichable qu’il obtient.

## REMARQUES

À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec Windows PowerShell sont empaquetées dans des modules. Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de Windows PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables ( **PSSnapin** ). L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable. En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.

 Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).

## LIENS CONNEXES

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)

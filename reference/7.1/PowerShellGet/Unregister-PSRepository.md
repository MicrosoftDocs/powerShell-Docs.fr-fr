---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 769d1ac91cbbc580b3488ba84d14a759b6ef65d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203629"
---
# Unregister-PSRepository

## SYNOPSIS
Annule l’enregistrement d’un référentiel.

## SYNTAX

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## Description

L' `Unregister-PSRepository` applet de commande annule l’inscription d’un référentiel pour l’utilisateur actuel.

## EXEMPLES

### Exemple 1 : annuler l’inscription d’un référentiel

Cet exemple annule l’inscription du dépôt nommé myNuGetSource.

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### Exemple 2 : annuler l’inscription de tous les référentiels

Cet exemple utilise `Get-PSRepository` pour récupérer tous les dépôts inscrits et utilise l’opérateur de pipeline pour les transmettre à `Unregister-PSRepository` pour annuler leur inscription.

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETERS

### -Name

Spécifie un tableau de noms des référentiels à supprimer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Get-PSRepository](Get-PSRepository.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

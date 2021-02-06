---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: df7f9000cf66cebce83e3146cd5c95a7d1a78bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599005"
---
# New-Guid

## SYNOPSIS
Crée un GUID.

## SYNTAXE

```
New-Guid [<CommonParameters>]
```

## Description

L’applet **de commande New-GUID** crée un identificateur global unique (Guid) aléatoire.
Si vous avez besoin d’un ID unique dans un script, vous pouvez créer un GUID, si nécessaire.

## EXEMPLES

### Exemple 1 : créer un GUID

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

Cette commande crée un GUID aléatoire.
Vous pouvez également stocker la sortie de cette applet de commande dans une variable à utiliser ailleurs dans un script.

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### System.Guid

Cette applet de commande retourne un GUID.

## REMARQUES

## LIENS CONNEXES


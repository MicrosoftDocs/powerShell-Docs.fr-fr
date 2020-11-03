---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 6e8903d6ee1b9bb38c42abd866a1657e86d2f3ac
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200806"
---
# New-Guid

## SYNOPSIS
Crée un GUID.

## SYNTAX

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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

## SORTIES

### System.Guid
Cette applet de commande retourne un GUID.

## REMARQUES

## LIENS CONNEXES

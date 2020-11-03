---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: a9d5c47eaf189e37f7f16b11cd48101f7b0e584d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204485"
---
# Out-Null

## SYNOPSIS
Masque la sortie au lieu de l’envoyer dans le pipeline ou de l’afficher.

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L’applet de commande **out-NULL** envoie sa sortie à null, en effet, en la supprimant du pipeline et en empêchant l’affichage de la sortie à l’écran.

## EXEMPLES

### Exemple 1 : supprimer la sortie

```powershell
Get-ChildItem | Out-Null
```

Cette commande obtient les éléments de l’emplacement/répertoire actuel, mais sa sortie n’est pas transmise via le pipeline ni affichée sur la ligne de commande.
Cela est utile pour masquer la sortie dont vous n’avez pas besoin.

## PARAMETERS

### -InputObject

Spécifie l’objet à envoyer à NULL (supprimé du pipeline).
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Les applets de commande qui contiennent le verbe **out** (applets de commande **out** ) n’ont pas de paramètres pour les noms ou les chemins d’accès de fichier. Pour envoyer des données à une applet de commande **out** , utilisez un opérateur de pipeline (|) pour envoyer la sortie d’une commande PowerShell à l’applet de commande. Vous pouvez également stocker les données dans une variable et utiliser le paramètre *InputObject* pour passer les données à l'applet de commande. Pour plus d'informations, consultez les exemples.
* **Out-NULL** ne retourne aucun objet de sortie. Si vous dirigez la sortie de **out-NULL** vers l’applet de commande Get-Member, la commande **obtenir-Member** signale qu’aucun objet n’a été spécifié.

## LIENS CONNEXES

[Out-Default](Out-Default.md)

[Out-Host](Out-Host.md)

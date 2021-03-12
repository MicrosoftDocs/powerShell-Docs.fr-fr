---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: b31d12f06a8d2e8e226908db9663446baf09a124
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194258"
---
# Import-BinaryMiLog

## SYNOPSIS
Utilisé pour recréer les objets enregistrés en fonction du contenu d’un fichier d’exportation.

## SYNTAX

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## Description

Utilisez cette applet de commande pour recréer des objets enregistrés en fonction du contenu d’un fichier d’exportation créé par `Export-BinaryMILog` . Cette applet de commande est semblable à `Import-Clixml` , à ceci près que `Export-BinaryMILog` stocke l’objet résultant dans un fichier encodé binaire.

## EXEMPLES

### Exemple 1 : restaurer les objets exportés vers un fichier

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## PARAMETERS

### -Path

Spécifie le chemin d’accès du fichier dans lequel stocker la représentation binaire de l’objet. Le paramètre **path** prend en charge les caractères génériques et les chemins d’accès relatifs. Cette applet de commande génère une erreur si le chemin d’accès correspond à plusieurs fichiers.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

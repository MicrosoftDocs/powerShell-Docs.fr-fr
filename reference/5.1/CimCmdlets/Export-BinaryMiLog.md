---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: cf03ad884121c6cf8cf65cdb791cbdc4e587c3b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202514"
---
# Export-BinaryMiLog

## SYNOPSIS
Crée une représentation codée en binaire d’un ou de tous les objets et le stocke dans un fichier.

## SYNTAX

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## Description

L' `Export-BinaryMILog` applet de commande crée une représentation binaire d’un ou de tous les objets et la stocke dans un fichier. Vous pouvez ensuite utiliser l' `Import-BinaryMiLog` applet de commande pour recréer l’objet enregistré en fonction du contenu de ce fichier.

Cette applet de commande est semblable à `Import-Clixml` , à ceci près que `Export-BinaryMILog` stocke l’objet résultant dans un fichier encodé binaire.

## EXEMPLES

### Exemple 1 : créer une représentation binaire de CimInstances

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

Cette commande exporte **CimInstances** dans un fichier journal mi binaire spécifié par le paramètre Path. Consultez l’exemple de Import-BinaryMiLog pour voir comment recréer le **CimInstances** en important ce fichier.

## PARAMETERS

### -InputObject

Spécifie l'entrée de cette applet de commande. Vous pouvez utiliser ce paramètre ou vous adresser l'entrée à cette applet de commande.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

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

### Microsoft.Management.Infrastructure.CimInstance

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 406675d8bde1b6b9a28913c09d5374393705f93b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204978"
---
# New-TemporaryFile

## SYNOPSIS
Crée un fichier temporaire.

## SYNTAX

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

Cette applet de commande crée des fichiers temporaires que vous pouvez utiliser dans les scripts.

L' `New-TemporaryFile` applet de commande crée un fichier vide qui a l' `.tmp` extension de nom de fichier.
Cette applet de commande nomme le fichier `tmp<NNNN>.tmp` , où `<NNNN>` est un nombre hexadécimal aléatoire.
L’applet de commande crée le fichier dans votre dossier **temp** .

Cette applet de commande utilise la méthode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) pour rechercher votre dossier **temp** . Cette méthode vérifie l’existence de variables d’environnement dans l’ordre suivant et utilise le premier chemin d’accès trouvé :

- Sur les plateformes Windows :

  1. Chemin d’accès spécifié par la variable d’environnement TMP.
  1. Chemin d’accès spécifié par la variable d’environnement TEMP.
  1. Chemin d’accès spécifié par la variable d’environnement USERPROFILE.
  1. Répertoire Windows.

- Sur les plateformes non-Windows : utilise le chemin d’accès spécifié par la variable d’environnement TMPDIR.

## EXEMPLES

### Exemple 1 : créer un fichier temporaire

```powershell
$TempFile = New-TemporaryFile
```

Cette commande génère un `.tmp` fichier dans votre dossier temporaire, puis stocke une référence au fichier dans la `$TempFile` variable. Vous pouvez utiliser ce fichier plus tard dans votre script.

## PARAMETERS

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

## SORTIES

### System. IO. FileInfo

Cette applet de commande retourne un objet **FileInfo** qui représente le fichier temporaire.

## REMARQUES

## LIENS CONNEXES


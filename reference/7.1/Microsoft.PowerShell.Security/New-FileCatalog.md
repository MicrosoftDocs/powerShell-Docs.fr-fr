---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: eb753ea7713f3a8577aba6751a284b989c798d18
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202470"
---
# New-FileCatalog

## SYNOPSIS
`New-FileCatalog` crée un fichier catalogue de hachages de fichiers qui peuvent être utilisés pour valider l’authenticité d’un fichier.

## SYNTAX

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

`New-FileCatalog` crée un [fichier catalogue Windows](/windows-hardware/drivers/install/catalog-files) pour un ensemble de dossiers et de fichiers.
Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins d’accès fournis.
Les utilisateurs peuvent ensuite distribuer le catalogue avec leurs fichiers afin que les utilisateurs puissent valider si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.

Les versions de catalogues 1 et 2 sont prises en charge. La version 1 utilise l’algorithme de hachage SHA1 (déconseillé) pour créer des hachages de fichier, et la version 2 utilise SHA256.
La version de catalogue 2 n’est pas prise en charge sur Windows Server 2008 R2 ni Windows 7.
Vous devez utiliser la version de catalogue 2 sur Windows 8, Windows Server 2012 et les systèmes d’exploitation ultérieurs.

## EXEMPLES

### Exemple 1 : créer un catalogue de fichiers pour `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETERS

### -CatalogFilePath

Chemin d’accès à un fichier ou dossier dans lequel le fichier catalogue (. cat) doit être placé.
Si un chemin d’accès au dossier est spécifié, le nom de fichier par défaut est `catalog.cat` utilisé.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

Accepte `1.0` ou `2.0` en tant que valeurs possibles pour la spécification de la version du catalogue.
`1.0` doit être utilisé dans la mesure du possible, car il utilise l’algorithme de hachage SHA-1 non sécurisé, tandis que `2.0` utilise l’algorithme SHA-256 sécurisé Toutefois, `1.0` est le seul algorithme pris en charge sur Windows 7 et le serveur 2008R2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Le pipeline prend une chaîne qui est utilisée comme nom de fichier du catalogue.

## SORTIES

### System. IO. FileInfo

## REMARQUES

## LIENS CONNEXES

[Test-FileCatalog](Test-FileCatalog.md)

[PowerShellGet](/powerShell/module/powershellget)


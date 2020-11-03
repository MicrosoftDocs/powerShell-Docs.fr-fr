---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: c4d2e01305e198e9c38ffe09e9ac06cff4d358cf
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "93205317"
---
# Expand-Archive

## SYNOPSIS
Extrait des fichiers à partir d’un fichier d’archive (zippé) spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description

L' `Expand-Archive` applet de commande extrait les fichiers d’un fichier d’archive compressé spécifié dans un dossier de destination spécifié. Un fichier d’archive permet d’empaqueter plusieurs fichiers et éventuellement de les compresser dans un seul fichier zippé pour faciliter la distribution et le stockage.

## EXEMPLES

### Exemple 1 : extraire le contenu d’une archive

Cet exemple extrait le contenu d’un fichier d’archive existant dans le dossier spécifié par le paramètre **DestinationPath** .

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

Dans cet exemple, le paramètre **LiteralPath** est utilisé, car le nom de fichier contient des caractères qui peuvent être interprétés comme des caractères génériques.

### Exemple 2 : extraire le contenu d’une archive dans le dossier actif

Cet exemple extrait le contenu d’un fichier d’archive existant dans le dossier actif dans le dossier spécifié par le paramètre **DestinationPath** .

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETERS

### -DestinationPath

Par défaut, `Expand-Archive` crée un dossier à l’emplacement actuel qui est le même nom que le fichier zip. Le paramètre vous permet de spécifier le chemin d’accès à un autre dossier. Le dossier cible est créé s’il n’existe pas.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

### -LiteralPath

Spécifie le chemin d’accès à un fichier d’archive. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez. Les caractères génériques ne sont pas pris en charge. Si le chemin d’accès comprend des caractères d’échappement, mettez chaque caractère d’échappement entre des guillemets simples pour indiquer à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Fait en sorte que l’applet de commande génère une liste des fichiers développés à partir de l’archive.

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

### -Path

Spécifie le chemin d’accès au fichier d’archive.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers un fichier d’archive existant.

## SORTIES

### System. IO. FileSystemInfo

Lorsque le `-PassThru` paramètre est utilisé, l’applet de commande génère une liste des fichiers qui ont été développés à partir de l’archive.

## REMARQUES

La [spécification du fichier zip](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ne spécifie pas de méthode standard d’encodage des noms de fichiers qui contiennent des caractères non-ASCII. L' `Compress-Archive` applet de commande utilise l’encodage UTF-8. D’autres outils d’archive ZIP peuvent utiliser un schéma d’encodage différent. Lorsque vous extrayez des fichiers dont les noms de fichiers ne sont pas stockés à l’aide de l’encodage UTF-8, `Expand-Archive` utilise la valeur brute trouvée dans l’archive. Cela peut entraîner un nom de fichier différent du nom de fichier source stocké dans l’archive.

## LIENS CONNEXES

[Compress-Archive](compress-archive.md)

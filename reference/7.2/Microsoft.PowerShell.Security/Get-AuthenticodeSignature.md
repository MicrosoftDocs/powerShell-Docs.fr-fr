---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: de039877825a15f0ddf48ba7095b9cce710ec22b
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685562"
---
# Get-AuthenticodeSignature

## SYNOPSIS
Obtient des informations sur la signature Authenticode d’un fichier.

## SYNTAX

### ByPath (par défaut)

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## Description

L' `Get-AuthenticodeSignature` applet de commande obtient des informations sur la signature Authenticode pour un fichier ou un contenu de fichier sous la forme d’un tableau d’octets.
Si le fichier est signé avec une signature signée et que le catalogue Windows est signé, la signature du catalogue Windows est utilisée.
Si le fichier n'est pas signé, les informations sont récupérées, mais les champs sont vides.

## EXEMPLES

### Exemple 1 : obtenir la signature Authenticode d’un fichier

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

Cette commande obtient des informations sur la signature Authenticode dans le fichier NewScript.ps1. Elle utilise le paramètre **filePath** pour spécifier le fichier.

### Exemple 2 : obtenir la signature Authenticode pour plusieurs fichiers

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

Cette commande obtient des informations sur la signature Authenticode pour les quatre fichiers listés sur la ligne de commande. Dans cet exemple, le nom du paramètre **filePath** , qui est facultatif, est omis.

### Exemple 3 : obtenir uniquement des signatures Authenticode valides pour plusieurs fichiers

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

Cette commande répertorie tous les fichiers du `$PSHOME` répertoire qui ont une signature Authenticode valide. La `$PSHOME` variable automatique contient le chemin d’accès au répertoire d’installation de PowerShell.

La commande utilise l' `Get-ChildItem` applet de commande pour récupérer les fichiers dans le `$PSHOME` répertoire. Elle utilise un modèle de *.* pour exclure des répertoires (bien qu’il exclue également les fichiers sans point dans le nom de fichier).

La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les fichiers dans `$PSHOME` l’applet de commande `ForEach-Object` , où `Get-AuthenticodeSignature` est appelé pour chaque fichier.

Les résultats de la `Get-AuthenticodeSignature` commande sont envoyés à une `Where-Object` commande qui sélectionne uniquement les objets de signature dont l’État est valide.

### Exemple 4 : obtenir la signature Authenticode pour un contenu de fichier spécifié en tant que tableau d’octets

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

Cette commande obtient des informations sur la signature Authenticode pour le contenu d’un fichier. Dans cet exemple, l’extension de fichier est spécifiée en même temps que le contenu du fichier.

## PARAMETERS

### -Contenu

Contenu d’un fichier sous la forme d’un tableau d’octets pour lequel la signature Authenticode est récupérée. Ce paramètre doit être utilisé avec le paramètre **SourcePathOrExtension** . Le contenu du fichier doit être au format Unicode (UTF-16LE).

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FilePath

Spécifie le chemin d’accès au fichier à examiner. Les caractères génériques sont autorisés, mais ils doivent conduire à un seul fichier. Il n’est pas nécessaire de taper **filePath** sur la ligne de commande lorsque vous spécifiez une valeur pour ce paramètre.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

Spécifie le chemin d'accès au fichier à examiner. Contrairement à **FilePath**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès contient un caractère d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des caractères d’échappement.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

Chemin d’accès au type de fichier ou de fichier du contenu pour lequel la signature Authenticode est récupérée. Ce paramètre est utilisé avec le **contenu** où le contenu du fichier est passé en tant que tableau d’octets.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès de fichier vers `Get-AuthenticodeSignature` .

## SORTIES

### System. Management. Automation. signature

`Get-AuthenticodeSignature` retourne un objet de signature pour chaque signature qu’il obtient.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Pour plus d’informations sur les signatures Authenticode dans PowerShell, consultez [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).

## LIENS CONNEXES

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 498620ee79285f0c0fe2a001b99fe5dc179ea0ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205085"
---
# Convert-Path

## SYNOPSIS
Convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.

## SYNTAX

### Chemin d’accès (par défaut)

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## Description

L' `Convert-Path` applet de commande convertit un chemin d’accès PowerShell en chemin d’accès du fournisseur PowerShell.

## EXEMPLES

### Exemple 1 : convertir le répertoire de travail en chemin d’accès au système de fichiers standard

Cet exemple convertit le répertoire de travail actuel, représenté par un point ( `.` ), en chemin d’accès standard au système de fichiers.

```
PS C:\> Convert-Path .
C:\
```

### Exemple 2 : convertir un chemin d’accès de fournisseur en chemin d’accès au registre standard

Cet exemple convertit le chemin d’accès du fournisseur PowerShell en chemin d’accès au registre standard.

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### Exemple 3 : convertir un chemin en chaîne

Cet exemple convertit le chemin d’accès au répertoire de départ du fournisseur actuel, qui est le fournisseur FileSystem, en une chaîne.

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETERS

### -LiteralPath

Spécifie, sous la forme d’un tableau de chaînes, le chemin d’accès à convertir. La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès PowerShell à convertir.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.

## SORTIES

### System.String

Cette applet de commande retourne une chaîne qui contient le chemin d’accès converti.

## REMARQUES

Les applets de commande qui contiennent le nom de chemin d’accès manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter. Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier. Utilisez-les de la même façon que vous utilisez **dirname** , **Normpath** , **realpath** , **join** ou d’autres manipulateurs de chemin d’accès.

Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les fournisseurs de système de fichiers, de Registre et de certificats.

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

`Convert-Path` convertit uniquement les chemins d’accès existants. Elle ne peut pas être utilisée pour convertir un emplacement qui n’existe pas encore.

## LIENS CONNEXES

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)


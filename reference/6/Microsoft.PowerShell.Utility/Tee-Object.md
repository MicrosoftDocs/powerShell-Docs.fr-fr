---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 1f892ece313ddc0074afbeaf3f3243c0bb9f31d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204393"
---
# Tee-Object

## SYNOPSIS
Enregistre la sortie de la commande dans un fichier ou dans une variable, puis l'envoie dans le pipeline.

## SYNTAX

### Fichier (par défaut)

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### Variable

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## Description

L' `Tee-Object` applet de commande redirige la sortie, autrement dit, elle envoie la sortie d’une commande dans deux directions (comme la lettre T). Elle stocke la sortie dans un fichier ou dans une variable, puis l'envoie dans le pipeline. Si `Tee-Object` est la dernière commande du pipeline, le résultat de la commande s’affiche à l’invite.

## EXEMPLES

### Exemple 1 : traiter les processus dans un fichier et dans la console

Cet exemple obtient la liste des processus en cours d’exécution sur l’ordinateur et envoie le résultat vers un fichier.
Étant donné qu'un deuxième chemin n'est pas spécifié, les processus sont également affichés dans la console.

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### Exemple 2 : traiter les processus dans une variable et `Select-Object`

Cet exemple obtient la liste des processus en cours d’exécution sur l’ordinateur, les enregistre dans la `$proc` variable et les dirige vers `Select-Object` .

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

L' `Select-Object` applet de commande sélectionne les propriétés **ProcessName** et **Handles** . Notez que la `$proc` variable comprend les informations par défaut retournées par `Get-Process` .

### Exemple 3 : fichiers système de sortie vers deux fichiers journaux

Cet exemple enregistre une liste de fichiers système dans deux fichiers journaux, un fichier cumulatif et un fichier actif.

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

La commande utilise l' `Get-ChildItem` applet de commande pour effectuer une recherche récursive des fichiers système sur le lecteur D :. Un opérateur de pipeline (|) envoie la liste à `Tee-Object` , qui ajoute la liste au fichier AllSystemFiles.txt et transmet la liste dans le pipeline à l’applet de commande, ce qui permet d' `Out-File` enregistrer la liste dans le fichier NewSystemFiles.txt.

## PARAMETERS

### -Append

Indique que l’applet de commande ajoute la sortie au fichier spécifié. Sans ce paramètre, le nouveau contenu remplace tout contenu existant dans le fichier sans avertissement.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un fichier dont cette applet de commande enregistre l’objet dans les caractères génériques, mais qui doit être résolu en un seul fichier.

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

Spécifie l'objet à enregistrer et à afficher. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient. Vous pouvez également diriger un objet vers `Tee-Object` .

Quand vous utilisez le paramètre **InputObject** avec `Tee-Object` , au lieu de rediriger les résultats de la commande vers `Tee-Object` , la valeur **InputObject** est traitée comme un objet unique, même si la valeur est une collection.

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

### -LiteralPath

Spécifie un fichier dans lequel cette applet de commande enregistre l’objet. Contrairement à **FilePath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

Spécifie une variable dans laquelle l’applet de commande enregistre l’objet. Entrez un nom de variable sans le signe dollar précédent ( `$` ).

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets vers `Tee-Object` .

## SORTIES

### System. Management. Automation. PSObject

`Tee-Object` retourne l’objet qu’il redirige.

## REMARQUES

Vous pouvez également utiliser l' `Out-File` applet de commande ou l’opérateur de redirection, qui enregistrent la sortie dans un fichier, mais ne l’envoient pas dans le pipeline.

À compter de PowerShell 6, `Tee-Object` utilise l’encodage UTF-8 sans nomenclature lorsqu’il écrit dans des fichiers. Si vous avez besoin d’un encodage différent, utilisez l' `Out-File` applet de commande avec le paramètre **Encoding** .

## LIENS CONNEXES

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203978"
---
# Invoke-Item

## SYNOPSIS
Exécute l'action par défaut sur l'élément spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## Description

L' `Invoke-Item` applet de commande effectue l’action par défaut sur l’élément spécifié.
Par exemple, elle exécute un fichier exécutable ou ouvre un fichier de document dans l’application associée au type de fichier de document.
L’action par défaut dépend du type d’élément et est déterminée par le fournisseur PowerShell qui fournit l’accès aux données.

## EXEMPLES

### Exemple 1 : ouvrir un fichier

Cette commande ouvre le fichier « aliasApr04.doc » dans Microsoft Office Word.
Dans ce cas, l’ouverture dans Word est l’action par défaut pour les fichiers « . doc ».

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### Exemple 2 : ouvrir tous les fichiers d’un type spécifique

Cette commande ouvre toutes les feuilles de calcul Microsoft Office Excel dans le dossier « C:\Documents and Settings\Lister\My documents ».
Chaque feuille de calcul est ouverte dans une nouvelle instance d’Excel.
Dans ce cas, l’ouverture dans Excel est l’action par défaut pour les fichiers « . xls ».

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## PARAMETERS

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.
Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

> [!WARNING]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut de l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Spécifie un filtre dans le format ou la langue du fournisseur.
La valeur de ce paramètre qualifie le paramètre **Path** .

La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie un chemin d’accès à l’élément.
Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès à l’élément sélectionné.

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

### -UseTransaction

Inclut la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d’informations, consultez about_transactions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### Aucun

La commande ne génère pas de sortie.
Toutefois, la sortie peut être générée par l’élément appelé.

## REMARQUES

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez about_Providers.

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

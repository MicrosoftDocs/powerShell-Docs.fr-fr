---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 5f964cec2458309eb736bf2d2930fc65a72b0fe4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201866"
---
# Start-Transcript

## SYNOPSIS
Crée un enregistrement de tout ou partie d’une session PowerShell dans un fichier texte.

## SYNTAX

### ByPath (par défaut)

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## Description

L' `Start-Transcript` applet de commande crée un enregistrement de tout ou partie d’une session PowerShell dans un fichier texte. La transcription inclut toutes les commandes que l'utilisateur saisit et toutes les sorties qui s'affichent sur la console.

À compter de Windows PowerShell 5,0, `Start-Transcript` comprend le nom d’hôte dans le nom de fichier généré de toutes les transcriptions. Cela s’avère particulièrement utile lorsque la journalisation de votre entreprise est centralisée.
Les fichiers créés par l’applet de commande `Start-Transcript` incluent des caractères aléatoires dans les noms pour éviter les remplacements ou les doublons potentiels lorsque deux transcriptions ou plus sont démarrées simultanément.
Cela empêche également la découverte non autorisée des transcriptions stockées dans un partage de fichiers centralisé.

## EXEMPLES

### Exemple 1 : démarrer un fichier de transcription avec les paramètres par défaut

```powershell
Start-Transcript
```

Cette commande démarre une transcription à l'emplacement du fichier par défaut.

### Exemple 2 : démarrer un fichier de transcription à un emplacement spécifique

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

Cette commande démarre une transcription dans le `Transcript0.txt` fichier dans `C:\transcripts` . Étant donné que le paramètre **NoClobber** est utilisé, la commande empêche tout remplacement des fichiers existants. Si le `Transcript0.txt` fichier existe déjà, la commande échoue.

## PARAMETERS

### -Append

Indique que cette applet de commande ajoute la nouvelle transcription à la fin d’un fichier existant. Utilisez le paramètre **path** pour spécifier le fichier.

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

### -Force

Permet à l'applet de commande d'ajouter la transcription à un fichier en lecture seule existant. Lorsqu'elle est utilisée sur un fichier en lecture seule, l'applet de commande modifie l'autorisation du fichier en lecture-écriture. L’applet de commande ne peut pas remplacer les restrictions de sécurité lorsque ce paramètre est utilisé.

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

### -IncludeInvocationHeader

Indique que cette applet de commande enregistre l’horodatage lorsque des commandes sont exécutées.

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

### -UseMinimalHeader

Ajoutez un bref en-tête à la transcription, au lieu de l’en-tête détaillé inclus par défaut. Ce paramètre a été ajouté dans PowerShell 6,2.

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

Spécifie un emplacement pour le fichier de transcription. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Indique que cette applet de commande ne remplacera pas un fichier existant. Par défaut, si un fichier de transcription existe dans le chemin d’accès spécifié, `Start-Transcript` remplace le fichier sans avertissement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputDirectory

Spécifie un chemin d’accès spécifique et un dossier dans lequel enregistrer une transcription. PowerShell attribue automatiquement le nom de la transcription.

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie un emplacement pour le fichier de transcription. Entrez un chemin d’accès à un `.txt` fichier. Les caractères génériques ne sont pas autorisés.

Si vous ne spécifiez pas de chemin d’accès, `Start-Transcript` utilise le chemin d’accès dans la valeur de la `$Transcript` variable globale. Si vous n’avez pas créé cette variable, `Start-Transcript` stocke les transcriptions dans les `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` fichiers.

Si un répertoire du chemin d'accès n'existe pas, la commande échoue.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### System.String

Cette applet de commande retourne une chaîne qui contient un message de confirmation et le chemin d’accès au fichier de sortie.

## REMARQUES

Pour arrêter une transcription, utilisez l' `Stop-Transcript` applet de commande.

Pour enregistrer une session entière, ajoutez la `Start-Transcript` commande à votre profil. Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

## LIENS CONNEXES

[Stop-Transcript](Stop-Transcript.md)

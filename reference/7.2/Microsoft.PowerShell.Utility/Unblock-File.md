---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 8bbfe761a71b38b541f23730d84eb0023a059318
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596116"
---
# Unblock-File

## SYNOPSIS
Débloque les fichiers téléchargés depuis Internet.

## SYNTAXE

### ByPath (par défaut)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Unblock-File` applet de commande vous permet d’ouvrir des fichiers qui ont été téléchargés à partir d’Internet. Il débloque les fichiers de script PowerShell qui ont été téléchargés à partir d’Internet afin que vous puissiez les exécuter, même lorsque la stratégie d’exécution de PowerShell est **RemoteSigned**. Par défaut, ces fichiers sont bloqués pour protéger l'ordinateur contre les fichiers non approuvés.

Avant d’utiliser l’applet de commande `Unblock-File` , examinez le fichier et sa source, puis vérifiez qu’il peut être ouvert en toute sécurité.

En interne, l' `Unblock-File` applet de commande supprime le flux de données de remplacement de la zone. identifier, qui a la valeur « 3 » pour indiquer qu’il a été téléchargé à partir d’Internet.

Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : débloquer un fichier

Cette commande débloque le fichier PowerShellTips.chm.

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### Exemple 2 : débloquer plusieurs fichiers

Cette commande débloque tous les fichiers du `C:\Downloads` répertoire dont les noms incluent « PowerShell ». N'exécutez pas une commande similaire à celle-ci tant que vous n'avez pas vérifié que tous les fichiers étaient sûrs.

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### Exemple 3 : Rechercher et débloquer des scripts

Cette commande montre comment rechercher et débloquer des scripts PowerShell.

La première commande utilise le paramètre **Stream** de l’applet de commande *obten-Item* pour récupérer les fichiers avec le flux de zone. identifier.

La deuxième commande montre ce qui se passe lorsque vous exécutez un script bloqué dans une session PowerShell dans laquelle la stratégie d’exécution est **RemoteSigned**. La stratégie RemoteSigned vous empêche d'exécuter des scripts qui sont téléchargés à partir d'Internet, sauf s'ils sont signés numériquement.

La troisième commande utilise l' `Unblock-File` applet de commande pour débloquer le script afin qu’il puisse s’exécuter dans la session.

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETERS

### -LiteralPath

Spécifie les fichiers à débloquer. Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie les fichiers à débloquer. Les caractères génériques sont pris en charge.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
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

Vous pouvez diriger un chemin de fichier vers `Unblock-File` .

## SORTIES

### None

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- La prise en charge de macOS a été ajoutée dans PowerShell 7.
- L' `Unblock-File` applet de commande fonctionne uniquement dans les lecteurs du système de fichiers.
- `Unblock-File` effectue la même opération que le bouton **débloquer** de la boîte de dialogue **Propriétés** de l’Explorateur de fichiers.
- Si vous utilisez l' `Unblock-File` applet de commande sur un fichier qui n’est pas bloqué, la commande n’a aucun effet sur le fichier débloqué et l’applet de commande ne génère pas d’erreurs.

## LIENS CONNEXES

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[Fournisseur FileSystem](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)

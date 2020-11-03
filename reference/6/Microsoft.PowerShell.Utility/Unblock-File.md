---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 617d36f61434d8b779d1161610cc7757c6a7725d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204386"
---
# Unblock-File

## SYNOPSIS
Débloque les fichiers téléchargés depuis Internet.

## SYNTAX

### ByPath (par défaut)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L'applet de commande **Unblock-File** vous permet d'ouvrir des fichiers téléchargés depuis Internet.
Il débloque les fichiers de script PowerShell qui ont été téléchargés à partir d’Internet afin que vous puissiez les exécuter, même lorsque la stratégie d’exécution de PowerShell est **RemoteSigned** .
Par défaut, ces fichiers sont bloqués pour protéger l'ordinateur contre les fichiers non approuvés.

Avant d'utiliser l'applet de commande **Unblock-File** , vérifiez le fichier et sa source, puis assurez-vous qu'il peut s'ouvrir sans risque.

En interne, l'applet de commande **Unblock-File** supprime le flux de données alternatif Zone.Identifier, dont la valeur est égale à « 3 » pour indiquer qu'il a été téléchargé à partir d'Internet.

Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : débloquer un fichier

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

Cette commande débloque le fichier PowerShellTips.chm.

### Exemple 2 : débloquer plusieurs fichiers

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

Cette commande débloque tous les fichiers du répertoire C:\Downloads dont le nom contient « PowerShell ».
N'exécutez pas une commande similaire à celle-ci tant que vous n'avez pas vérifié que tous les fichiers étaient sûrs.

### Exemple 3 : Rechercher et débloquer des scripts

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

Cette commande montre comment rechercher et débloquer des scripts PowerShell.

## PARAMETERS

### -LiteralPath
Spécifie les fichiers à débloquer.
Contrairement au paramètre *Path* , la valeur du paramètre *LiteralPath* est utilisée exactement telle qu'elle est tapée.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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
Spécifie les fichiers à débloquer.
Les caractères génériques sont pris en charge.

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

Vous pouvez diriger un chemin d'accès vers **Unblock-File** .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

* L'applet de commande **Unblock-File** ne fonctionne que dans les lecteurs de système de fichiers.
* **Unblock-file** effectue la même opération que le bouton **débloquer** de la boîte de dialogue **Propriétés** dans l’Explorateur de fichiers.
* Si vous utilisez l'applet de commande **Unblock-File** sur un fichier qui n'est pas bloqué, la commande n'a aucun effet sur le fichier débloqué et l'applet de commande ne génère pas d'erreurs.

## LIENS CONNEXES

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[Fournisseur FileSystem](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)

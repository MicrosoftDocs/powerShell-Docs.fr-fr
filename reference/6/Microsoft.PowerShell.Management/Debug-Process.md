---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 05075a00074eb69a0fe492da95c28c2ad912c291
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389043"
---
# Debug-Process

## SYNOPSIS
Débogue un ou plusieurs processus en cours d'exécution sur l'ordinateur local.

## SYNTAXE

### Nom (par défaut)

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Debug-Process` applet de commande joint un débogueur à un ou plusieurs processus en cours d’exécution sur un ordinateur local.
Vous pouvez spécifier les processus en fonction de leur nom de processus ou de leur ID de processus (PID), ou vous pouvez diriger les objets de processus vers cette applet de commande.

Cette applet de commande attache le débogueur actuellement inscrit pour le processus. Avant d'utiliser cette applet de commande, vérifiez qu'un débogueur est téléchargé et correctement configuré.

## EXEMPLES

### Exemple 1 : attacher un débogueur à un processus sur l’ordinateur

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

Cette commande joint un débogueur au processus PowerShell sur l'ordinateur.

### Exemple 2 : attacher un débogueur à tous les processus qui commencent par la chaîne spécifiée

```
PS C:\> Debug-Process -Name "SQL*"
```

Cette commande joint un débogueur à tous les processus dont le nom commence par SQL.

### Exemple 3 : attacher un débogueur à plusieurs processus

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

Cette commande joint un débogueur aux processus Winlogon, Explorer et Outlook.

### Exemple 4 : attacher un débogueur à plusieurs ID de processus

```
PS C:\> Debug-Process -Id 1132, 2028
```

Cette commande joint un débogueur aux processus dont les identificateurs sont 1132 et 2028.

### Exemple 5 : utiliser Get-Process pour obtenir un processus, puis y attacher un débogueur

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur. Elle utilise l' `Get-Process` applet de commande pour obtenir les processus PowerShell sur l’ordinateur, et elle utilise un opérateur de pipeline ( `|` ) pour envoyer les processus à l’applet de commande `Debug-Process` .

Pour spécifier un processus PowerShell particulier, utilisez le paramètre ID de `Get-Process` .

### Exemple 6 : attacher un débogueur à un processus en cours sur l’ordinateur local

```
PS C:\> $PID | Debug-Process
```

Cette commande joint un débogueur aux processus PowerShell actifs sur l'ordinateur.

La commande utilise la `$PID` variable automatique, qui contient l’ID de processus du processus PowerShell en cours. Ensuite, il utilise un opérateur de pipeline ( `|` ) pour envoyer l’ID de processus à l’applet de commande `Debug-Process` .

Pour plus d’informations sur la `$PID` variable automatique, consultez about_Automatic_Variables.

### Exemple 7 : attacher un débogueur à un processus qui utilise le paramètre InputObject

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur local.

La première commande utilise l' `Get-Process` applet de commande pour récupérer les processus PowerShell sur l’ordinateur. Elle enregistre l’objet processus résultant dans la variable nommée `$P` .

La deuxième commande utilise le paramètre **InputObject** de l' `Debug-Process` applet de commande pour envoyer l’objet processus dans la `$P` variable.

## PARAMÈTRES

### -Id

Spécifie l'identificateur des processus à déboguer. Le nom du paramètre **ID** est facultatif.

Pour Rechercher l’ID de processus d’un processus, tapez `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets processus qui représentent les processus à déboguer. Entrez une variable qui contient les objets processus ou une commande qui obtient les objets processus, tels que l' `Get-Process` applet de commande. Vous pouvez également diriger les objets de processus vers cette applet de commande.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie le nom des processus à déboguer. S’il existe plusieurs processus portant le même nom, cette applet de commande joint un débogueur à tous les processus portant ce nom. Le paramètre **Name** est facultatif.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Int32, System. Diagnostics. Process, System. String

Vous pouvez diriger un ID de processus (Int32), un objet de processus (System. Diagnostics. Process) ou un nom de processus (String) vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande utilise la méthode AttachDebugger de la classe WMI (Windows Management Instrumentation) Win32_Process. Pour plus d’informations sur cette méthode, consultez la [méthode AttachDebugger](https://go.microsoft.com/fwlink/?LinkId=143640) dans MSDN Library.

## LIENS CONNEXES

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)

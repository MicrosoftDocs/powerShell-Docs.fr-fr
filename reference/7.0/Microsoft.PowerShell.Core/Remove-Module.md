---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: b8577db1d44f0e7bd4571a080133fecaa282770b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201482"
---
# Remove-Module

## SYNOPSIS
Supprime des modules de la session active.

## SYNTAX

### name

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L'applet de commande **Remove-Module** supprime les membres d'un module, tels que les applets de commande et les fonctions, dans la session active.

Si le module inclut un assembly (.dll), tous les membres implémentés par l'assembly sont supprimés, mais l'assembly n'est pas déchargé.

Cette applet de commande ne désinstalle pas le module et ne le supprime pas non plus de l'ordinateur.
Elle affecte uniquement la session PowerShell active.

## EXEMPLES

### Exemple 1 : supprimer un module

```powershell
Remove-Module -Name "BitsTransfer"
```

Cette commande supprime le module BitsTransfer de la session active.

### Exemple 2 : supprimer tous les modules

```powershell
Get-Module | Remove-Module
```

Cette commande supprime tous les modules de la session active.

### Exemple 3 : supprimer des modules à l’aide du pipeline

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

Cette commande supprime les modules BitsTransfer et PSDiagnostics de la session active.

La commande utilise un opérateur de pipeline (|) pour envoyer les noms de module à **Remove-Module** .
Elle utilise le paramètre commun *Verbose* pour obtenir des informations détaillées sur les membres qui sont supprimés.

Les messages *détaillés* affichent les éléments qui sont supprimés.
Les messages diffèrent car le module BitsTransfer inclut un assembly qui implémente ses applets de commande et un module imbriqué avec son propre assembly.
Le module PSDiagnostics inclut un fichier de script de module (.psm1) qui exporte des fonctions.

### Exemple 4 : supprimer un module à l’aide de ModuleInfo

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

Cette commande utilise le paramètre *ModuleInfo* pour supprimer le module BitsTransfer.

## PARAMETERS

### -Force

Indique que cette applet de commande supprime les modules en lecture seule.
Par défaut, **Remove-Module** supprime uniquement les modules en lecture-écriture.

Les valeurs **ReadOnly** et **ReadWrite** sont stockées dans la propriété **AccessMode** d'un module.

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

### -FullyQualifiedName

Spécifie les noms complets des modules à supprimer.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

Spécifie les objets de module à supprimer.
Entrez une variable qui contient un objet de module ( **PSModuleInfo** ) ou une commande qui obtient un objet de module, tel qu’une commande Get-Module.
Vous pouvez également diriger les objets vers **Remove-Module** .

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des modules à supprimer.
Les caractères génériques sont autorisés.
Vous pouvez également diriger les chaînes de nom vers **Remove-Module** .

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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

### System. String, System. Management. Automation. PSModuleInfo

Vous pouvez diriger les noms de module et les objets de module vers **Remove-Module** .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

Lors de la suppression d’un module, il existe un événement sur le module qui s’exécutera.
Cet événement permet à un module de réagir en cours de suppression et d’effectuer un nettoyage, par exemple la libération de ressources. Exemple :

$OnRemoveScript = {

  \# effectuer un nettoyage

  $cachedSessions | Remove-PSSession

}

$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript

Pour une cohérence totale, il peut être également utile de réagir à la fermeture du processus PowerShell :

Register-EngineEvent-SourceIdentifier ([System. Management. Automation. PsEngineEvent] :: sortie)-action $OnRemoveScript

## LIENS CONNEXES

[Get-Module](Get-Module.md)

[Module d’importation](Import-Module.md)

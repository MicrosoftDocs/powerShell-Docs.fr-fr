---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: 04f8da7042d6bf07c6af893aa3601ed572c94e38
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201426"
---
# Remove-PSBreakpoint

## SYNOPSIS
Supprime les points d'arrêt de la console active.

## SYNTAX

### Point d’arrêt (par défaut)

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Remove-PSBreakpoint** supprime un point d’arrêt.
Entrez un objet de point d'arrêt ou un ID de point d'arrêt.

Quand vous supprimez un point d'arrêt, l'objet de point d'arrêt n'est plus disponible ou fonctionnel.
Si vous avez enregistré un objet de point d'arrêt dans une variable, la référence existe toujours, mais le point d'arrêt ne fonctionne pas.

**Remove-PSBreakpoint** est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.
Pour plus d’informations sur le débogueur PowerShell, consultez about_Debuggers.

## EXEMPLES

### Exemple 1 : supprimer tous les points d’arrêt

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

Cette commande supprime tous les points d'arrêt de la console active.

### Exemple 2 : supprimer un point d’arrêt spécifié

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

Cette commande supprime un point d'arrêt.

La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la variable Name dans le script Sample.ps1.
Ensuite, il enregistre l’objet de point d’arrêt dans la variable $B.

La deuxième commande utilise l’applet de commande **Remove-PSBreakpoint** pour supprimer le nouveau point d’arrêt.
Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de point d’arrêt dans la variable $B à l’applet de commande **Remove-PSBreakpoint** .

Si vous exécutez le script, cette commande s'exécute jusqu'à son achèvement sans interruption.
En outre, l’applet de commande **PSBreakpoint** ne retourne pas ce point d’arrêt.

### Exemple 3 : supprimer un point d’arrêt par ID

```
PS C:\> Remove-PSBreakpoint -Id 2
```

Cette commande supprime le point d'arrêt ayant l'ID de point d'arrêt 2.

### Exemple 4 : utiliser une fonction pour supprimer tous les points d’arrêt

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

Cette simple fonction supprime tous les points d'arrêt de la console active.
Elle utilise l'applet de commande Get-PSBreakpoint pour obtenir les points d'arrêt.
Ensuite, il utilise un opérateur de pipeline (|) pour envoyer les points d’arrêt à l’applet de commande **Remove-PSBreakpoint** , qui les supprime.

Par conséquent, vous pouvez taper à `del-psb` la place de la commande la plus longue.

Pour enregistrer la fonction, ajoutez-la à votre profil PowerShell.

## PARAMETERS

### -Point d’arrêt
Spécifie les points d'arrêt à supprimer.
Entrez une variable qui contient des objets de point d’arrêt ou une commande qui obtient des objets de point d’arrêt, comme une commande **PSBreakpoint** .
Vous pouvez également diriger les objets point d’arrêt vers **Remove-PSBreakpoint** .

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id
Spécifie les ID de point d’arrêt pour lesquels cette applet de commande supprime les points d’arrêt.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

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

### System. Management. Automation. Breakpoint
Vous pouvez diriger les objets point d’arrêt vers **Remove-PSBreakpoint** .

## SORTIES

### Aucun
L'applet de commande ne génère pas de résultat.

## REMARQUES

## LIENS CONNEXES

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

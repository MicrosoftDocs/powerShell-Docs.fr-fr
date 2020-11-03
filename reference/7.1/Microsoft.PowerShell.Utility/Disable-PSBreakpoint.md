---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2f89be6b2ae9973b060a8562b5815b4e44b56ad8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204213"
---
# Disable-PSBreakpoint

## SYNOPSIS
Désactive les points d'arrêt dans la console active.

## SYNTAX

### Point d’arrêt (par défaut)

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **Disable-PSBreakpoint** désactive les points d’arrêt, ce qui garantit qu’ils ne sont pas atteints lors de l’exécution du script.
Vous pouvez l'utiliser pour désactiver tous les points d'arrêt, ou vous pouvez spécifier des points d'arrêt en envoyant des objets de point d'arrêt ou des ID de point d'arrêt.

Techniquement, cette applet de commande affecte la valeur False à la propriété Enabled d'un objet de point d'arrêt.
Pour réactiver un point d'arrêt, utilisez l'applet de commande Enable-PSBreakpoint.
Les points d'arrêt sont activés par défaut quand vous les créez à l'aide de l'applet de commande Set-PSBreakpoint.

Un point d'arrêt est un point dans un script auquel l'exécution s'arrête temporairement afin que vous puissiez examiner les instructions comprises dans le script.
**Disable-PSBreakpoint** est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.
Pour plus d’informations sur le débogueur PowerShell, consultez about_Debuggers.

## EXEMPLES

### Exemple 1 : définir un point d’arrêt et le désactiver

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

Ces commandes désactivent un point d'arrêt nouvellement créé.

La première commande utilise l’applet de commande Set-PSBreakpoint pour créer un point d’arrêt sur la variable *Name* dans le script Sample.ps1.
Ensuite, il enregistre l’objet de point d’arrêt dans la variable $B.

La deuxième commande utilise l’applet de commande **Disable-PSBreakpoint** pour désactiver le nouveau point d’arrêt.
Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de point d’arrêt dans $B à l’applet de commande **Disable-PSBreakpoint** .

En raison de cette commande, la valeur de la propriété Enabled de l’objet Breakpoint dans $B est false.

### Exemple 2 : désactiver un point d’arrêt

```
PS C:\> Disable-PSBreakpoint -Id 0
```

Cette commande désactive le point d'arrêt avec l'ID de point d'arrêt 0.

### Exemple 3 : créer un point d’arrêt désactivé

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

Cette commande crée un nouveau point d'arrêt qui est désactivé jusqu'à ce que vous l'activiez.

Elle utilise l’applet de commande **Disable-PSBreakpoint** pour désactiver le point d’arrêt.
La valeur du paramètre de *point d’arrêt* est une commande Set-PSBreakpoint qui définit un nouveau point d’arrêt, génère un objet de point d’arrêt et enregistre l’objet dans la variable $B.

Les paramètres d'applet de commande qui acceptent des objets comme valeurs peuvent accepter une variable qui contient l'objet, ou une commande qui obtient ou génère l'objet.
Dans ce cas, étant donné que **Set-PSBreakpoint** génère un objet de point d’arrêt, il peut être utilisé comme valeur du paramètre de *point d’arrêt* .

La deuxième commande affiche l’objet de point d’arrêt dans la valeur de la variable $B.

### Exemple 4 : désactiver tous les points d’arrêt dans la console actuelle

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

Cette commande désactive tous les points d'arrêt dans la console active.
Vous pouvez abréger cette commande comme suit : «GBP | DBP ".

## PARAMETERS

### -Point d’arrêt

Spécifie les points d'arrêt à désactiver.
Entrez une variable qui contient des objets point d'arrêt ou une commande qui obtient des objets point d'arrêt (commande Get-PSBreakpoint, par exemple).
Vous pouvez également diriger les objets de point d’arrêt vers l’applet de commande **Disable-PSBreakpoint** .

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

Désactive les points d'arrêt avec l'ID de point d'arrêt spécifié.
Entrez les ID ou une variable qui contient les ID.
Vous ne pouvez pas diriger d’ID vers **Disable-PSBreakpoint** .

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

### -PassThru

Retourne un objet qui représente les points d'arrêt activés.
Par défaut, cette applet de commande ne génère aucun résultat.

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

Vous pouvez diriger un objet point d’arrêt vers **Disable-PSBreakpoint** .

## SORTIES

### Aucun ou System. Management. Automation. Breakpoint

Quand vous utilisez le paramètre *PassThru* , **Disable-PSBreakpoint** retourne un objet qui représente le point d’arrêt désactivé.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)


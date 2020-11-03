---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 20e79fe561862912269e716c40ebe91194ea8b6e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204669"
---
# Enable-PSBreakpoint

## SYNOPSIS
Active les points d'arrêt dans la console active.

## SYNTAX

### ID (par défaut)

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Point d’arrêt

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Enable-PSBreakpoint` applet de commande réactive les points d’arrêt désactivés. Vous pouvez l’utiliser pour activer tous les points d’arrêt, ou des points d’arrêt spécifiques en fournissant des objets ou des ID de point d’arrêt.

Un point d’arrêt est un point dans un script où l’exécution s’arrête temporairement afin que vous puissiez examiner l’état du script. Les points d’arrêt nouvellement créés sont activés automatiquement, mais peuvent être désactivés à l’aide de `Disable-PSBreakpoint` .

Techniquement, cette applet de commande modifie la valeur de la propriété **Enabled** d’un objet point d’arrêt en **true** .

`Enable-PSBreakpoint` est l’une des différentes applets de commande conçues pour le débogage de scripts PowerShell. Pour plus d’informations sur le débogueur PowerShell, consultez [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).

## EXEMPLES

### Exemple 1 : activer tous les points d’arrêt

Cet exemple active tous les points d’arrêt de la session active.

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

À l’aide des alias, cet exemple peut être abrégé en `gbp | ebp` .

### Exemple 2 : activer les points d’arrêt par ID

Cet exemple active plusieurs points d’arrêt à l’aide de leurs ID de point d’arrêt.

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### Exemple 3 : activer un point d’arrêt désactivé

Cet exemple réactive un point d’arrêt qui a été désactivé.

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint` crée un point d’arrêt sur la variable **Name** dans le `Sample.ps1` script en enregistrant l’objet point d’arrêt dans la `$B` variable. Le paramètre **PassThru** affiche la valeur de la propriété **Enabled** du point d’arrêt est **false** .

`Enable-PSBreakpoint` réactive le point d’arrêt. Là encore, en utilisant le paramètre **PassThru** , nous voyons que la valeur de la propriété **Enabled** est **true** .

### Exemple 4 : activer des points d’arrêt à l’aide d’une variable

Cet exemple active un ensemble de points d’arrêt à l’aide des objets de point d’arrêt.

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` Obtient les points d’arrêt et les enregistre dans la `$B` variable. L’utilisation du paramètre de **point d’arrêt** `Enable-PSBreakpoint` active les points d’arrêt.

Cet exemple est équivalent à l’exécution de `Enable-PSBreakpoint -Id 3, 5` .

## PARAMETERS

### -Point d’arrêt

Spécifie les points d'arrêt à activer. Fournissez une variable contenant des points d’arrêt ou une commande qui obtient des objets de point d’arrêt, tels que `Get-PSBreakpoint` . Vous pouvez également diriger les objets de point d’arrêt vers `Enable-PSBreakpoint` .

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

Spécifie les numéros d' **identification** des points d’arrêt à activer. La valeur par défaut est tous les points d'arrêt.
Fournissez l' **ID** par numéro ou dans une variable. Vous ne pouvez pas diriger les numéros d' **identification** vers `Enable-PSBreakpoint` . Pour Rechercher l' **ID** d’un point d’arrêt, utilisez l’applet de commande `Get-PSBreakpoint` .

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

Retourne un objet représentant le point d’arrêt en cours d’activation. Par défaut, cette applet de commande ne génère pas de sortie.

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

### System. Management. Automation. Breakpoint

Vous pouvez diriger un objet point d’arrêt vers `Enable-PSBreakpoint` .

## SORTIES

### Aucun ou System. Management. Automation. Breakpoint

Quand vous utilisez le paramètre **PassThru** , `Enable-PSBreakpoint` retourne un objet de point d’arrêt qui représente ce point d’arrêt qui a été activé. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- L' `Enable-PSBreakpoint` applet de commande ne génère pas d’erreur si vous essayez d’activer un point d’arrêt déjà activé. Par conséquent, vous pouvez activer tous les points d'arrêt sans erreur, même si seuls quelques-uns sont désactivés.

- Les points d’arrêt sont activés lorsque vous les créez à l’aide de l’applet de commande `Set-PSBreakpoint` . Vous n’avez pas besoin d’activer les points d’arrêt nouvellement créés.

## LIENS CONNEXES

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

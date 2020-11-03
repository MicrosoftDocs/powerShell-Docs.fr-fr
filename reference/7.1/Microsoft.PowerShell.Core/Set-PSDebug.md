---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: a0b5d7e86f9d63b487bc093feb18ecc7a4496999
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204789"
---
# Set-PSDebug

## SYNOPSIS
Active et désactive les fonctionnalités de débogage de script, définit le niveau de suivi et bascule en mode strict.

## SYNTAX

### sur

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### arrêt

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## Description

L' `Set-PSDebug` applet de commande active et désactive les fonctionnalités de débogage de script, définit le niveau de suivi et bascule en mode strict. Par défaut, les fonctionnalités de débogage PowerShell sont désactivées.

Lorsque le paramètre **trace** a la valeur `1` , chaque ligne de script est tracée lors de son exécution. Lorsque le paramètre a la valeur `2` , les attributions de variables, les appels de fonction et les appels de script sont également suivis. Si le paramètre **Step** est spécifié, vous êtes invité à confirmer l’exécution de chaque ligne du script.

## EXEMPLES

### Exemple 1 : définir le niveau de suivi

Cet exemple définit le niveau de suivi sur `2` , puis exécute un script qui affiche les nombres 1, 2 et
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### Exemple 2 : activer l’exécution pas à pas

Cet exemple active l’exécution pas à pas, puis exécute un script qui affiche les nombres 1, 2 et 3.

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### Exemple 3 : utiliser le mode strict

Cet exemple met PowerShell en mode strict et tente d’accéder à une variable qui n’a pas de valeur assignée.

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### Exemple 4 : désactiver les fonctionnalités de débogage

Cet exemple désactive toutes les fonctionnalités de débogage, puis exécute un script qui affiche les nombres 1, 2 et 3.

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## PARAMETERS

### -Désactivé

Désactive toutes les fonctionnalités de débogage du script.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Étape

Active l'exécution pas à pas du script. Avant l’exécution de chaque ligne, PowerShell vous invite à arrêter, continuer ou entrer un nouveau niveau d’interpréteur pour inspecter l’état du script.

La spécification du paramètre **Step** définit automatiquement le niveau de trace `1` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

Spécifie qu’une valeur doit être assignée aux variables avant d’être référencées dans un script. Si une variable est référencée avant qu’une valeur ne soit affectée, PowerShell retourne une erreur d’exception. Ceci équivaut à `Set-StrictMode -Version 1`. Pour plus d’informations, consultez [Set-StrictMode](Set-StrictMode.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trace

Spécifie le niveau de trace pour chaque ligne dans un script. Chaque ligne est tracée au fur et à mesure de son exécution.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- 0 : désactivez le suivi de script.
- 1 : suivre les lignes de script à mesure qu’elles s’exécutent.
- 2 : suivi des lignes de script, des affectations de variables, des appels de fonction et des scripts.

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas effectuer de pipeline d’entrée pour cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

## LIENS CONNEXES

[about_Debuggers](./About/about_Debuggers.md)

[Debug-Process](../Microsoft.PowerShell.Management/Debug-Process.md)

[Set-PSBreakpoint](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[Set-StrictMode](Set-StrictMode.md)

[Write-Debug](../Microsoft.PowerShell.Utility/Write-Debug.md)


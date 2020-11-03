---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 859738998de9d2a61a5fb7d9f39ff6ef8b74ad4d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203842"
---
# Clear-History

## SYNOPSIS
Supprime des entrées de l’historique de commande de session PowerShell.

## SYNTAX

### IDParameter (par défaut)

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## Description

`Clear-History` supprime l’historique de commande d’une session PowerShell. Chaque session PowerShell a son propre historique de commande. Pour afficher l’historique des commandes, utilisez l’applet de commande `Get-History` .

Par défaut, `Clear-History` supprime l’intégralité de l’historique des commandes d’une session PowerShell. Vous pouvez utiliser des paramètres avec `Clear-History` pour supprimer des commandes sélectionnées.

`Clear-History` n’efface pas le `PSReadLine` fichier d’historique de commandes. Le `PSReadLine` module stocke un fichier d’historique qui contient chaque commande PowerShell de chaque session PowerShell. À partir d’une invite PowerShell, utilisez les flèches vers le haut et vers le bas de votre clavier pour faire défiler l’historique des commandes. Pour afficher la `PSReadLine` configuration de l’historique des commandes, utilisez `Get-PSReadLineOption` .
`PSReadLine` fourni avec PowerShell 5,0 et versions ultérieures. Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPLES

### Exemple 1 : supprimer l’historique de commande d’une session PowerShell

Cette commande supprime toutes les commandes de l’historique d’une session PowerShell.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

L' `Get-History` applet de commande affiche l’historique de la session PowerShell. `Clear-History` supprime l’intégralité de l’historique de la commande. `Get-History` affiche l’historique de commande mis à jour et confirme que l’historique précédent a été supprimé.

### Exemple 2 : supprimer les commandes les plus récentes

Cette commande utilise les paramètres **Count** et latentes les plus **récents** pour supprimer les commandes les plus récentes de l’historique d’une session PowerShell.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

L' `Get-History` applet de commande affiche l’historique de la session PowerShell. `Clear-History` est utilisé pour supprimer l’historique de la commande. Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. Le paramètre le plus **récent** spécifie que les commandes les plus récentes sont effacées de l’historique. `Get-History`affiche l’historique de commande mis à jour et confirme que les cinq commandes les plus récentes ont été supprimées, **ID 6**  -  **ID 10** .

### Exemple 3 : supprimer des commandes qui correspondent à des critères spécifiques

Cette commande supprime les commandes qui correspondent à des critères spécifiques définis par le paramètre **CommandLine** .

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

L' `Get-History` applet de commande affiche l’historique de la session PowerShell. `Clear-History` supprime l’historique de la commande. Le paramètre **CommandLine** spécifie les commandes qui contiennent de **l’aide** ou terminent la **syntaxe** . `Get-History` affiche l’historique de commande mis à jour et confirme que les commandes **ID 3** , **ID 5** , **ID 6** et **ID 7** ont été supprimées.

### Exemple 4 : supprimer des commandes par numéro d’identification

Cette commande supprime les éléments d’historique spécifiques à l’aide de l' **ID** . Pour supprimer plusieurs commandes, soumettez une liste de numéros d' **ID** séparés par des virgules.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

L' `Get-History` applet de commande affiche l’historique de la session PowerShell. `Clear-History` supprime l’historique de la commande. Le paramètre **ID** spécifie les commandes à supprimer. `Get-History` affiche l’historique de commande mis à jour et confirme que l' **ID 3** et l' **ID 5** ont été supprimés.

### Exemple 5 : supprimer les commandes par numéro et nombre d’ID

Cette commande utilise les paramètres **ID** et **Count** pour supprimer l’historique des commandes. Les commandes sont supprimées de l' **ID** spécifié dans l’ordre inverse, du plus récent au plus ancien.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

L' `Get-History` applet de commande affiche l’historique de la session PowerShell. `Clear-History` supprime l’historique de la commande. Le paramètre **ID** spécifie de commencer par l' **ID 7** . Le paramètre **Count** spécifie de supprimer cinq commandes, y compris l' **ID** spécifié. `Get-History`affiche l’historique de commande mis à jour et confirme que cinq commandes ont été supprimées, **ID 3**  -  **ID 7** .

## PARAMETERS

### -CommandLine

Supprime l’historique de commande d’une session PowerShell. La chaîne doit être une correspondance exacte ou utiliser des caractères génériques pour faire correspondre les commandes dans l’historique de session PowerShell affiché par `Get-History` . Si vous entrez plusieurs chaînes, supprime les `Clear-History` commandes qui correspondent à l’une des chaînes. Le paramètre **CommandLine** peut être utilisé avec **Count** .

Pour les chaînes avec un espace, utilisez des guillemets simples. Pour plus d’informations, consultez [about_Quoting_Rules](About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Nombre

Spécifie le nombre d’entrées d’historique que `Clear-History` supprime. Les commandes sont supprimées dans l’ordre, en commençant par l’entrée la plus ancienne dans l’historique.

Les paramètres **Count** et **ID** peuvent être utilisés ensemble. Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. À partir de l' **ID** spécifié, les commandes sont supprimées dans l’ordre séquentiel inverse. Par exemple, si l' **ID** est 30 et que le **nombre** est 10, `Clear-History` supprime les éléments 21 à 30.

Les paramètres **Count** et **CommandLine** peuvent être utilisés ensemble. **Nombre** spécifie le nombre de commandes à supprimer qui correspondent à la valeur du paramètre de **ligne** de commande. Les commandes sont supprimées dans un ordre séquentiel.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie l' **ID** d’historique de commande que `Clear-History` supprime. Pour afficher les numéros d' **identification** , utilisez l’applet de commande `Get-History` . Les numéros d' **identification** sont séquentiels et les commandes conservent leur numéro d' **identification** tout au long d’une session PowerShell. Le paramètre **ID** peut être utilisé avec **Count** et le plus **récent** .

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Plus récent

Lorsque le paramètre le plus **récent** est utilisé, `Clear-History` supprime les entrées les plus récentes de l’historique. Par défaut, `Clear-History` supprime les entrées les plus anciennes dans l’historique.

Le paramètre le plus **récent** peut être utilisé avec l' **ID** et le **nombre** . Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. À partir de l' **ID** spécifié, les commandes sont supprimées dans l’ordre séquentiel. Par exemple, si l' **ID** est 30 et que le **nombre** est 10, `Clear-History` supprime les éléments de 30 à 39.

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

Vous invite à confirmer l’exécution de l' `Clear-History` applet de commande.

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

Montre ce qui se passe si l’applet de commande `Clear-History` s’exécute. L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers `Clear-History` .

## SORTIES

### Aucun

`Clear-History` ne génère pas de sortie.

## REMARQUES

L’historique de session PowerShell est une liste des commandes entrées au cours d’une session PowerShell. Vous pouvez afficher l'historique, ajouter et supprimer des commandes, et exécuter des commandes à partir de l'historique. Pour plus d’informations, consultez [about_History](About/about_History.md).

L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .
Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé. Cette applet de commande fonctionne uniquement avec l’historique de session. Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## LIENS CONNEXES

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Add-History](Add-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)

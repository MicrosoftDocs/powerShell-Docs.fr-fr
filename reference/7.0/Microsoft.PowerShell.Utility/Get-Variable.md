---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 128bdd997e006723a69997e1419efd2f012e97f6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93202013"
---
# Get-Variable

## SYNOPSIS
Obtient les variables dans la console active.

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## Description

L' `Get-Variable` applet de commande obtient les variables PowerShell dans la console active.
Vous pouvez récupérer seulement les valeurs des variables en spécifiant le paramètre **ValueOnly** , et vous pouvez filtrer les variables retournées par nom.

## EXEMPLES

### Exemple 1 : récupérer les variables par lettre

Cette commande obtient les variables dont le nom commence par la lettre m.
La commande obtient également la valeur des variables.

```powershell
Get-Variable m*
```

### Exemple 2 : récupérer des valeurs de variables par lettre

Cette commande obtient uniquement les valeurs des variables dont le nom commence par m.

```powershell
Get-Variable m* -ValueOnly
```

### Exemple 3 : récupération de variables à l’aide de deux lettres

Cette commande obtient des informations sur les variables qui commencent par la lettre M ou par la lettre P.

```powershell
Get-Variable -Include M*,P*
```

### Exemple 4 : récupération des variables par étendue

La première commande obtient seulement les variables définies dans l'étendue locale.
Elle est équivalente à `Get-Variable -Scope Local` et peut être abrégée en `gv -s 0` .

La deuxième commande utilise l' `Compare-Object` applet de commande pour rechercher les variables définies dans l’étendue parente (étendue 1), mais uniquement dans l’étendue locale (étendue 0).

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETERS

### -Exclude

Spécifie un tableau d’éléments que cette applet de commande exclut de l’opération.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie un tableau d’éléments sur lesquels l’applet de commande agira, en excluant tous les autres.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Spécifie le nom de la variable.
Les caractères génériques sont autorisés.
Vous pouvez également diriger un nom de variable vers `Get-Variable` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Étendue

Spécifie les variables dans l’étendue. Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Global**
- **Local**
- **Script**
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)

**Local** est la valeur par défaut.
Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ValueOnly

Indique que cette applet de commande obtient uniquement la valeur de la variable.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient le nom de la variable vers `Get-Variable` .

## SORTIES

### System. Management. Automation. PSVariable

Cette applet de commande retourne un objet **System. Management. AutomationPSVariable** pour chaque variable qu’il obtient. Le type d'objet dépend de la variable.

### System. Object []

Lorsque vous spécifiez le paramètre **ValueOnly** , si la valeur de la variable spécifiée est une collection, `Get-Variable` retourne un `[System.Object[]]` . Ce comportement empêche l’opération de pipeline normale de traiter les valeurs de la variable une à la fois. Une solution de contournement pour forcer l’énumération de collections consiste à placer la `Get-Variable` commande entre parenthèses.

## REMARQUES

- Cette applet de commande ne gère pas les variables d'environnement. Pour gérer les variables d'environnement, vous pouvez utiliser le fournisseur de variables d'environnement.

## LIENS CONNEXES

[Clear-Variable](Clear-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

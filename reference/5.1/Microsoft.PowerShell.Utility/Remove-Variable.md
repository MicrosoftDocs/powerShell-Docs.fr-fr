---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: c6347ea9ca2169c6379871131bc98001bcdb5d25
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205729"
---
# Remove-Variable

## SYNOPSIS
Supprime une variable et sa valeur.

## SYNTAX

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-Variable` applet de commande supprime une variable et sa valeur de l’étendue dans laquelle elle est définie, telle que la session active. Vous ne pouvez pas utiliser cette applet de commande pour supprimer des variables qui sont définies en tant que constantes ou celles qui sont détenues par le système.

## EXEMPLES

### Exemple 1 : supprimer une variable

```powershell
Remove-Variable Smp
```

Cette commande supprime la `$Smp` variable.

## PARAMETERS

### -Exclude

Spécifie un tableau d’éléments que cette applet de commande omet de l’opération. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que « s* ». Les caractères génériques sont autorisés.

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

### -Force

Indique que l’applet de commande supprime une variable, même si elle est en lecture seule. Même en utilisant le paramètre **force** , l’applet de commande ne peut pas supprimer une constante.

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

### -Include

Spécifie un tableau d’éléments que cette applet de commande supprime dans l’opération. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que s *. Les caractères génériques sont autorisés.

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

Spécifie le nom de la variable à supprimer. Le nom du paramètre ( **Name** ) est facultatif.
Les caractères génériques sont autorisés

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Étendue

Obtient seulement les variables de l'étendue spécifiée. Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)

Local est la valeur par défaut. Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

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

### System. Management. Automation. PSVariable

Vous pouvez diriger un objet de variable vers `Remove-Variable` .

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

- Les modifications affectent uniquement l'étendue actuelle, par exemple une session. Pour supprimer une variable de toutes les sessions, ajoutez une `Remove-Variable` commande à votre profil PowerShell.

- Vous pouvez également faire référence à `Remove-Variable` par son alias intégré, `rv` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

## LIENS CONNEXES

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Set-Variable](Set-Variable.md)

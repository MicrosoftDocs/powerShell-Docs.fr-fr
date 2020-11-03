---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: e42371a58b49a25a9aaf0cc60551ff4bf27e2ec4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205106"
---
# Clear-Variable

## SYNOPSIS
Supprime la valeur d'une variable.

## SYNTAX

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet **de commande Clear-variable** supprime les données stockées dans une variable, mais elle ne supprime pas la variable.
Par conséquent, la valeur de la variable est NULL (vide).
Si la variable a un type de données ou d’objet spécifié, cette applet de commande conserve le type de l’objet stocké dans la variable.

## EXEMPLES

### Exemple 1 : supprimer la valeur des variables globales qui commencent par une chaîne de recherche

```
PS C:\> Clear-Variable my* -Scope Global
```

Cette commande supprime la valeur des variables globales dont le nom commence par My.

### Exemple 2 : effacer une variable dans une étendue enfant, mais pas à l’étendue parente

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

Ces commandes montrent qu'effacer une variable dans une étendue enfant n'efface pas la valeur dans l'étendue parente.
La première commande définit la valeur de la variable $A sur 3.
La deuxième commande utilise l’opérateur d’appel (&) pour exécuter la commande **Clear-variable** dans une nouvelle étendue.
La variable est effacée dans l'étendue enfant (même si elle n'existait pas), mais elle n'est pas effacée dans l'étendue locale.
La troisième commande, qui obtient la valeur de $A, indique que la valeur 3 n’est pas affectée.

### Exemple 3 : supprimer la valeur de la variable spécifiée

```
PS C:\> Clear-Variable -Name "Processes"
```

Cette commande supprime la valeur de la variable named Processes.
Une fois que l’applet de commande a terminé l’opération, la variable nommée Processes existe toujours, mais la valeur est null.

## PARAMETERS

### -Exclude

Spécifie un tableau d’éléments que cette applet de commande omet dans l’opération.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que « s* ».
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

### -Force

Permet à l'applet de commande d'effacer une variable, même si elle est en lecture seule.
Même en utilisant le paramètre Force, l'applet de commande ne peut pas effacer des constantes.

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

Spécifie un tableau d’éléments que cette applet de commande comprend dans l’opération.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que « s* ».
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

Spécifie le nom de la variable à effacer.
Les caractères génériques sont autorisés.
Ce paramètre est requis, mais le nom du paramètre (« Name ») est facultatif.

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

### -PassThru

Retourne un objet représentant l’élément que vous utilisez.
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

### -Étendue

Spécifie l'étendue dans laquelle cet alias est valide.

Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script

Vous pouvez également utiliser un nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est l’étendue actuelle et 1 est son parent).
Local est la valeur par défaut.
Pour plus d'informations, consultez about_Scopes.

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

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### None ou System. Management. Automation. PSVariable

Quand vous utilisez le paramètre *PassThru* , cette applet de commande génère un objet **System. Management. Automation. PSVariable** représentant la variable effacée.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour supprimer une variable, ainsi que sa valeur, utilisez Remove-Variable ou Remove-Item.

  Cette applet de commande ne supprime pas les valeurs des variables qui sont définies en tant que constantes ou détenues par le système, même si vous utilisez le paramètre *force* .

  Si la variable que vous effacez n'existe pas, l'applet de commande n'a aucun effet.
Elle ne crée pas de variable avec une valeur null.

  Vous pouvez également faire référence à **Clear-variable** par son alias intégré, CLV.
Pour plus d'informations, consultez about_Aliases.

*

## LIENS CONNEXES

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)


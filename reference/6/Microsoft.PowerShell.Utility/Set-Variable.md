---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 12184f3f7e629c86b587c68b4472ffaf4c46db3b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204398"
---
# Set-Variable

## SYNOPSIS
Définit la valeur d'une variable.
Crée la variable si celle avec le nom demandé n'existe pas.

## SYNTAX

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **Set-variable** affecte une valeur à une variable spécifiée ou modifie la valeur actuelle.
Si la variable n'existe pas, l'applet de commande la crée.

## EXEMPLES

### Exemple 1 : définir une variable et obtenir sa valeur

```
PS C:\> Set-Variable -Name "desc" -Value "A description"
PS C:\> Get-Variable -Name "desc"
```

Ces commandes définissent la valeur de la variable DESC sur une description, puis obtient la valeur de la variable.

### Exemple 2 : définir une variable globale en lecture seule

```
PS C:\> Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru | Format-List -Property *
```

Cette commande crée une variable globale, variable en lecture seule qui contient tous les processus sur le système, puis affiche toutes les propriétés de la variable.

La commande utilise l’applet de commande **Set-variable** pour créer la variable.
Elle utilise le paramètre *PassThru* pour créer un objet représentant la nouvelle variable, et elle utilise l’opérateur de pipeline (|) pour passer l’objet à l’applet de commande Format-List.
Elle utilise le paramètre *Property* de Format-List avec la valeur All (*) pour afficher toutes les propriétés de la variable nouvellement créée.

La valeur, « (Get-Process) », est placée entre parenthèses pour qu'elle soit exécutée avant d'être stockée dans la variable.
Sinon, la variable contient les mots « Get-Process ».

### Exemple 3 : comprendre les variables publiques et les variables privées

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26 

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

 PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

Cette commande montre comment modifier la visibilité d’une variable en private.
Cette variable peut être lue et modifiée par les scripts avec les autorisations requises, mais elle n'est pas visible par l'utilisateur.

L'exemple de sortie montre la différence de comportement entre les variables publiques et les variables privées.

## PARAMETERS

### Description

Spécifie la description de la variable.

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

### -Exclude

Spécifie un tableau d’éléments que cette applet de commande exclut de l’opération.
La valeur de ce paramètre qualifie le paramètre *Path* .
Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .
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

Vous permet de créer une variable portant le même nom qu'une variable en lecture seule existante ou de modifier la valeur d'une variable en lecture seule.

Par défaut, vous pouvez remplacer une variable, sauf si la variable a la valeur d’option ReadOnly ou constant.
Pour plus d’informations, consultez le paramètre *option* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

Spécifie un tableau d’éléments que cette applet de commande comprend dans l’opération.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un nom ou un modèle de nom, tel que `c*` .
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

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

Spécifie la valeur de la propriété **options** de la variable.

Les valeurs autorisées sont :

- None : ne définit aucune option. (« None » est la valeur par défaut.)
- ReadOnly : peut être supprimé. Ne peut pas être modifié, sauf en utilisant le paramètre force.
- Constante : ne peut pas être supprimé ou modifié. « Constant » est valide uniquement quand vous créez une variable. Vous ne pouvez pas remplacer les options d'une variable existante par « Constant ».
- Privé : la variable est disponible uniquement dans l’étendue actuelle.
- Options AllScope : la variable est copiée vers toutes les nouvelles étendues créées.

Pour afficher la propriété **options** de toutes les variables dans la session, tapez `Get-Variable | Format-Table -Property name, options -Autosize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Retourne un objet représentant la nouvelle variable.
Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue de la variable. Les valeurs acceptables pour ce paramètre sont les suivantes :

- Global
- Local
- Script
- Privées
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).

Local est la valeur par défaut.

Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

Spécifie la valeur de la variable.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Visibilité

Détermine si la variable est visible en dehors de la session dans laquelle elle a été créée.
Ce paramètre est conçu pour une utilisation dans les scripts et les commandes qui seront remis à d'autres utilisateurs.

Les valeurs autorisées sont :

- Public : la variable est visible. (« Public » est la valeur par défaut.)
- Privé : la variable n’est pas visible.

Quand une variable est privée, elle n'apparaît pas dans les listes de variables, telles que celles retournées par Get-Variable, ni dans les affichages du lecteur Variable:.
Les commandes pour lire ou modifier la valeur d'une variable privée retournent une erreur.
Toutefois, l'utilisateur peut exécuter des commandes qui utilisent une variable privée si les commandes ont été écrites dans la session dans laquelle la variable a été définie.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
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

### System.Object

Vous pouvez diriger un objet qui représente la valeur de la variable vers **Set-variable** .

## SORTIES

### None ou System. Management. Automation. PSVariable

Quand vous utilisez le paramètre *PassThru* , **Set-variable** génère un objet **System. Management. Automation. PSVariable** qui représente la variable nouvelle ou modifiée.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

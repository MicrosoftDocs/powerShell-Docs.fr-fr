---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: faf8bc399185da402bebb678b02927e0e5628662
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204321"
---
# New-Variable

## SYNOPSIS
Crée une variable.

## SYNTAX

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description
L’applet **de commande New-variable** crée une variable dans PowerShell.
Vous pouvez assigner une valeur à la variable durant sa création, ou changer sa valeur après sa création.

Vous pouvez utiliser les paramètres de **New-variable** pour définir les propriétés de la variable, définir l’étendue d’une variable et déterminer si les variables sont publiques ou privées.

En général, vous créez une variable en tapant le nom de la variable et sa valeur, tel que `$Var = 3` , mais vous pouvez utiliser l’applet de commande **New-variable** pour utiliser ses paramètres.

## EXEMPLES

### Exemple 1 : créer une variable

```
PS C:\> New-Variable days
```

Cette commande crée une variable nommée Days.
Vous n’êtes pas obligé de taper le paramètre *Name* .

### Exemple 2 : créer une variable et lui assigner une valeur

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

Cette commande crée une variable nommée zipcode et lui attribue la valeur 98033.

### Exemple 3 : créer une variable avec l’option ReadOnly

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

Cet exemple montre comment utiliser l’option ReadOnly de **New-variable** pour empêcher une variable d’être remplacée.

La première commande crée une variable nommée Max et lui affecte la valeur 256.
Elle utilise le paramètre *option* avec la valeur ReadOnly.

La deuxième commande tente de créer une deuxième variable portant le même nom.
Cette commande retourne une erreur, car l'option lecture seule est définie sur la variable.

La troisième commande utilise le paramètre *force* pour remplacer la protection en lecture seule sur la variable.
Dans ce cas, la commande qui permet de créer une variable portant le même nom aboutit.

### Exemple 4 : créer une variable privée

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

Cette commande montre le comportement d'une variable privée dans un module.
Le module contient l’applet de commande Get-Counter, qui comporte une variable privée nommée Counter.
La commande utilise le paramètre *Visibility* avec la valeur Private pour créer la variable.

L'exemple de sortie montre le comportement d'une variable privée.
L'utilisateur qui a chargé le module ne peut pas afficher ou changer la valeur de la variable Counter. Toutefois, la variable Counter peut être lue et changée par les commandes du module.

### Exemple 5 : créer une variable avec un espace

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

Cette commande montre que les variables avec des espaces peuvent être créées.
Vous pouvez accéder aux variables à l’aide de l’applet de commande **« obtenir-variable »** ou directement en délimitant une variable à l’aide d’accolades.

## PARAMETERS

### Description
Spécifie une description de la variable.

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

### -Force
Indique que l’applet de commande crée une variable portant le même nom qu’une variable en lecture seule existante.

Par défaut, vous pouvez remplacer une variable, sauf si elle a la valeur d'option ReadOnly ou Constant.
Pour plus d’informations, consultez le paramètre *option* .

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

### -Name
Spécifie le nom de la nouvelle variable.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option
Spécifie la valeur de la propriété **options** de la variable. Les valeurs acceptables pour ce paramètre sont les suivantes :

- Aucun.
ne définit aucune option.
(None est la valeur par défaut.)
- Seulement.
peut être supprimé.
Ne peut pas être modifié, sauf en utilisant le paramètre *force* .
- Privé.
la variable est disponible uniquement dans l'étendue actuelle.
- Options AllScope.
la variable est copiée vers toutes les nouvelles étendues créées.
- Constante.
ne peut pas être supprimé ni modifié.
La constante n’est valide que lorsque vous créez une variable.
Vous ne pouvez pas modifier les options d’une variable existante en constant.

Pour afficher la propriété **options** de toutes les variables dans la session, tapez `Get-Variable | Format-Table -Property name, options -autosize` .

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
Spécifie la portée de la nouvelle variable.
Les valeurs valides pour ce paramètre sont :

- Généralités.
Les variables créées dans l’étendue globale sont accessibles partout dans un processus PowerShell.
- Local.
La portée locale fait référence à l’étendue actuelle. il peut s’agir de n’importe quelle portée en fonction du contexte.
- Script.
Les variables créées dans la portée du script sont accessibles uniquement dans le fichier de script ou le module dans lequel elles sont créées.
- Privé.
Les variables créées dans l’étendue privée ne sont pas accessibles en dehors de l’étendue dans laquelle elles existent.
Vous pouvez utiliser une étendue privée pour créer une version privée d’un élément portant le même nom dans une autre étendue.
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est l’étendue actuelle, 1 est son parent, 2 le parent de l’étendue parente, et ainsi de suite).
Les nombres négatifs ne peuvent pas être utilisés.

Local est l’étendue par défaut lorsque le paramètre d’étendue n’est pas spécifié.

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

### -Value
Spécifie la valeur initiale de la variable.

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
Les valeurs valides pour ce paramètre sont :

- Public.
la variable est visible.
(Public est la valeur par défaut).
- Privé.
la variable n'est pas visible.

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

### System.Object
Vous pouvez diriger une valeur vers **New-variable** .

## SORTIES

### None ou System. Management. Automation. PSVariable
Quand vous utilisez le paramètre *PassThru* , **New-variable** génère un objet **System. Management. Automation. PSVariable** représentant la nouvelle variable.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

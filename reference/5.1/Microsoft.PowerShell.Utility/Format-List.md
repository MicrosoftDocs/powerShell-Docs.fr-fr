---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: 7817384f077c58b46aed1dba552f89ac431891f0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205938"
---
# Format-List

## SYNOPSIS
Organise la sortie sous la forme d'une liste de propriétés dont chaque élément apparaît sur sa propre ligne.

## SYNTAX

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## Description

L' `Format-List` applet de commande met en forme la sortie d’une commande sous la forme d’une liste de propriétés dans laquelle chaque propriété est affichée sur une ligne distincte. Vous pouvez utiliser `Format-List` pour mettre en forme et afficher toutes les propriétés ou les propriétés sélectionnées d’un objet sous forme de liste (format-list *).

Étant donné que de l’espace est disponible pour chaque élément d’une liste, PowerShell affiche plus de propriétés de l’objet dans la liste, et les valeurs de propriété sont moins susceptibles d’être tronquées.

## EXEMPLES

### Exemple 1 : mettre en forme les services informatiques

```powershell
Get-Service | Format-List
```

Cette commande met en forme des informations sur des services sur l'ordinateur sous forme de liste. Par défaut, les services sont mis en forme en tant que table. L' `Get-Service` applet de commande obtient les objets représentant les services sur l’ordinateur. L’opérateur de pipeline (|) passe les résultats dans le pipeline à `Format-List` .
Ensuite, la `Format-List` commande met en forme les informations de service dans une liste et les envoie à l’applet de commande de sortie par défaut pour l’affichage.

### Exemple 2 : mettre en forme les fichiers PS1XML

Ces commandes affichent des informations sur les fichiers PS1XML dans le répertoire PowerShell sous la forme d’une liste.

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

La première commande récupère les objets qui représentent les fichiers et les stocke dans la `$A` variable.

La deuxième commande utilise `Format-List` pour mettre en forme les informations sur les objets stockés dans `$A` . Cette commande utilise le paramètre **InputObject** pour passer la variable à `Format-List` , qui envoie ensuite la sortie mise en forme à l’applet de commande de sortie par défaut pour l’affichage.

### Exemple 3 : mettre en forme les propriétés de processus par nom

Cette commande affiche le nom, la priorité de base et la classe de priorité de chaque processus sur l'ordinateur.

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

Elle utilise l' `Get-Process` applet de commande pour récupérer un objet représentant chaque processus. L’opérateur de pipeline (|) passe les objets de processus via le pipeline à `Format-List` . `Format-List` met en forme les processus en tant que liste des propriétés spécifiées. Le nom du paramètre de *propriété* est facultatif, vous pouvez donc l’omettre.

### Exemple 4 : mettre en forme toutes les propriétés d’un processus

Cette commande affiche toutes les propriétés du processus Winlogon.

```powershell
Get-Process winlogon | Format-List -Property *
```

Elle utilise l'applet de commande Get-Process pour obtenir un objet représentant le processus Winlogon. L’opérateur de pipeline (|) passe l’objet de processus Winlogon via le pipeline à `Format-List` . La commande utilise le paramètre *Property* pour spécifier les propriétés et \* pour indiquer toutes les propriétés.
Étant donné que le nom du paramètre *Property* est facultatif, vous pouvez l’omettre et taper la commande comme `Format-List *` . `Format-List` envoie automatiquement les résultats à l’applet de commande de sortie par défaut pour l’affichage.

### Exemple 5 : dépannage des erreurs de format

Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -DisplayError

Indique que cette applet de commande affiche les erreurs sur la ligne de commande. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.

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

### -Développer

Spécifie l’objet de collection mis en forme, ainsi que les objets de la collection. Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections). La valeur par défaut est EnumOnly. Les valeurs valides pour ce paramètre sont :

- EnumOnly. Affiche les propriétés des objets dans la collection.
- CoreOnly. Affiche les propriétés de l'objet de collection.
- Les deux. Affiche les propriétés de l'objet de collection et les propriétés des objets contenus dans la collection.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande affiche toutes les informations sur l’erreur. Utilisez avec le paramètre **DisplayError** ou **ShowError** . Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.

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

### -GroupBy

Spécifie la sortie dans des groupes en fonction d’une valeur ou d’une propriété partagée. Entrez une expression ou une propriété de la sortie.

La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Nom (ou étiquette)- `<string>`
- Expression `<string>` ou `<script block>`
- FormatString `<string>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à mettre en forme. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Propriété

Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.
Les caractères génériques sont autorisés.

Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché. Le nom de paramètre « Property » est facultatif. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Nom (ou étiquette)- `<string>`
- Expression `<string>` ou `<script block>`
- FormatString `<string>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

Indique que l’applet de commande envoie des erreurs par le biais du pipeline. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.

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

### -Afficher

Spécifie le nom d’une vue ou d’un format de liste secondaire. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers `Format-List` .

## SORTIES

### Microsoft. PowerShell. Commands. Internal. format

`Format-List` retourne les objets de format qui représentent la liste.

## REMARQUES

Vous pouvez également faire référence à Format-List par son alias intégré, FL. Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Les applets de commande format, telles que `Format-List` , organisent les données à afficher, mais ne les affichent pas.
Les données sont affichées par les fonctionnalités de sortie de PowerShell et par les applets de commande qui contiennent le verbe out (applets de commande Out), telles que `Out-Host` ou `Out-File` .

Si vous n’utilisez pas d’applet de commande format, PowerShell applique ce format par défaut pour chaque objet qu’il affiche.

Le paramètre **GroupBy** suppose que les objets sont triés. Utilisez Sort-Object avant `Format-List` d’utiliser pour regrouper les objets.

Le paramètre **View** vous permet de spécifier un autre format pour la table. Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers dans le répertoire PowerShell, ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l’applet de commande Update-FormatData pour les inclure dans PowerShell.

L’autre vue pour le paramètre **View** doit utiliser le format de liste ; sinon, la commande échoue. Si l’autre vue est une table, utilisez `Format-Table` . Si l’autre vue n’est ni une liste ni une table, utilisez `Format-Custom` .

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

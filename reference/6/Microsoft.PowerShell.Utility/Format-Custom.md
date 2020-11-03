---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 28914b86c86d5c16f09c81a5dc70ed1e05123b3e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205913"
---
# Format-Custom

## SYNOPSIS
Utilise un affichage personnalisé pour mettre en forme la sortie.

## SYNTAX

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## Description

L' `Format-Custom` applet de commande met en forme la sortie d’une commande telle qu’elle est définie dans une autre vue.
`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes. Vous pouvez utiliser les affichages définis dans PowerShell, ou vous pouvez créer vos propres vues dans un nouveau `format.ps1xml` fichier et utiliser l' `Update-FormatData` applet de commande pour les ajouter à PowerShell.

## EXEMPLES

### Exemple 1 : mettre en forme la sortie avec une vue personnalisée

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

Cette commande met en forme les informations sur l' `Start-Transcript` applet de commande dans le format défini par la vue MyView, un affichage personnalisé créé par l’utilisateur. Pour exécuter cette commande avec succès, vous devez d’abord créer un nouveau fichier PS1XML, définir la vue **MyView** , puis utiliser la `Update-FormatData` commande pour ajouter le fichier ps1xml à PowerShell.

### Exemple 2 : mettre en forme la sortie avec la vue par défaut

```powershell
Get-Process Winlogon | Format-Custom
```

Cette commande met en forme des informations sur le processus **Winlogon** dans un autre affichage personnalisé.
Étant donné que la commande n’utilise pas le paramètre **View** , `Format-Custom` utilise une vue personnalisée par défaut pour mettre en forme les données.

### Exemple 3 : dépannage des erreurs de format

Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -Profondeur

Spécifie le nombre de colonnes dans l'affichage.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayError

Affiche les erreurs sur la ligne de commande. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.

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

Met en forme l'objet de collection, ainsi que les objets de la collection. Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface **System. Collections. ICollection** . La valeur par défaut est **EnumOnly** .

Les valeurs autorisées sont :

- EnumOnly : affiche les propriétés des objets dans la collection.
- CoreOnly : affiche les propriétés de l’objet de collection.
- Both : affiche les propriétés de l’objet de collection et les objets de la collection.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique à l'applet de commande d'afficher toutes les informations sur l'erreur. Utilisez avec les paramètres **DisplayError** ou **ShowError** . Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.

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

Formate la sortie dans des groupes basés sur une valeur ou propriété partagée. Entrez une expression ou une propriété de la sortie.

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

Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché. La **propriété** nom du paramètre est facultative. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Expression `<string>` ou `<script block>`
- Profondeur `<int32>`

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

Envoie les erreurs via le pipeline. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.

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

Spécifie le nom d’un autre format ou d’une autre vue. Si vous omettez ce paramètre, `Format-Custom` utilise une vue personnalisée par défaut. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

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

Vous pouvez diriger n’importe quel objet vers `Format-Custom` .

## SORTIES

### Microsoft. PowerShell. Commands. Internal. format

`Format-Custom` retourne les objets de format qui représentent l’affichage.

## REMARQUES

`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes. Pour afficher une autre vue de table, utilisez `Format-Table` . Pour afficher un autre affichage de liste, utilisez `Format-List` .

Vous pouvez également faire référence à `Format-Custom` par son alias intégré, `fc` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Le paramètre **GroupBy** suppose que les objets sont triés. Avant `Format-Custom` d’utiliser pour regrouper les objets, utilisez `Sort-Object` pour les trier.

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

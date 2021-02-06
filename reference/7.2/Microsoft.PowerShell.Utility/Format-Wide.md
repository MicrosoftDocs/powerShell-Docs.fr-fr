---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: ba61c2d24d85256c55a7409fc368de4407aad5a9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598972"
---
# Format-Wide

## SYNOPSIS
Met en forme des objets en tant que tableau large affichant une seule propriété de chaque objet.

## SYNTAXE

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## Description

L' `Format-Wide` applet de commande met en forme les objets sous la forme d’un tableau étendu qui n’affiche qu’une seule propriété de chaque objet. Vous pouvez utiliser le paramètre **Property** pour déterminer la propriété qui s’affiche.

## EXEMPLES

### Exemple 1 : mettre en forme les noms des fichiers dans le répertoire actif

Cette commande affiche les noms des fichiers du répertoire actif sous forme de trois colonnes à l'écran.

```powershell
Get-ChildItem | Format-Wide -Column 3
```

L'applet de commande Get-ChildItem obtient les objets représentant chaque fichier dans le répertoire. L’opérateur de pipeline (|) passe les objets fichier via le pipeline à `Format-Wide` , qui les met en forme pour la sortie. Le paramètre **Column** spécifie le nombre de colonnes.

### Exemple 2 : mettre en forme les noms des clés de Registre

Cette commande affiche les noms des clés de Registre de la clé HKEY_CURRENT_USER\Software\Microsoft.

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

L'applet de commande Get-ChildItem obtient les objets représentant les clés. Le chemin d’accès est spécifié sous la forme HKCU :, l’un des lecteurs exposés par le fournisseur de Registre PowerShell, suivi du chemin d’accès de la clé. L’opérateur de pipeline (|) passe les objets de clé de Registre à `Format-Wide` , qui les formate pour la sortie. Le paramètre **Property** spécifie le nom de la propriété et le paramètre **AutoSize** ajuste les colonnes pour améliorer la lisibilité.

### Exemple 3 : dépannage des erreurs de format

Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

Ajuste la taille et le nombre de colonnes en fonction de la largeur des données. Par défaut, la vue détermine la taille et le nombre de colonnes. Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.

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

### -Colonne

Spécifie le nombre de colonnes dans l'affichage. Vous ne pouvez pas utiliser les paramètres **AutoSize** et **Column** dans la même commande.

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

Affiche les erreurs sur la ligne de commande. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.

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

Met en forme l'objet de collection, ainsi que les objets de la collection. Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections). La valeur par défaut est **EnumOnly**.

Les valeurs autorisées sont :

- EnumOnly : affiche les propriétés des objets dans la collection.
- CoreOnly : affiche les propriétés de l’objet de collection.
- Both : affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.

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

Indique que cette applet de commande remplace les restrictions qui empêchent la commande de s’exécuter correctement, de sorte que les modifications ne compromettent pas la sécurité. Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.

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

Spécifie les objets à mettre en forme. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

- Expression `<string>` ou `<script block>`
- FormatString `<string>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

Envoie les erreurs via le pipeline. Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Wide` commande et que les expressions ne semblent pas fonctionner.

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

Spécifie le nom d’un autre format de table ou d’une autre vue. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

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

Vous pouvez diriger n’importe quel objet vers `Format-Wide` .

## SORTIES

### Microsoft. PowerShell. Commands. Internal. format

`Format-Wide` retourne les objets de format représentant la table.

## REMARQUES

Vous pouvez également faire référence à `Format-Wide` par son alias intégré, `fw` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Le paramètre **GroupBy** suppose que les objets sont triés. Utilisez `Sort-Object` avant `Format-Custom` d’utiliser pour regrouper les objets.

Le paramètre **View** vous permet de spécifier un autre format pour la table. Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers du répertoire PowerShell ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l' `Update-FormatData` applet de commande pour les inclure dans PowerShell.

L’autre vue pour le paramètre **View** doit utiliser le format de table ; Si ce n’est pas le cas, la commande échoue. Si l’autre vue est une liste, utilisez `Format-List` . Si l'autre vue n'est ni une liste ni une table, utilisez Format-Custom.

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

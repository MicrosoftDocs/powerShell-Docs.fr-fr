---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 06f0573496f04d6790d7899afa5809ede720adee
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205989"
---
# Format-Table

## SYNOPSIS
Met en forme la sortie en tant que table.

## SYNTAX

### Tous

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L' `Format-Table` applet de commande met en forme la sortie d’une commande en tant que table avec les propriétés sélectionnées de l’objet dans chaque colonne. Le type d’objet détermine la disposition et les propriétés par défaut qui sont affichées dans chaque colonne. Vous pouvez utiliser le paramètre **Property** pour sélectionner les propriétés que vous souhaitez afficher.

PowerShell utilise des formateurs par défaut pour définir le mode d’affichage des types d’objets. Vous pouvez utiliser `.ps1xml` des fichiers pour créer des vues personnalisées qui affichent une table de sortie avec les propriétés spécifiées. Après avoir créé une vue personnalisée, utilisez le paramètre **View** pour afficher la table avec votre vue personnalisée. Pour plus d’informations sur les affichages, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

Vous pouvez utiliser une table de hachage pour ajouter des propriétés calculées à un objet avant de l’afficher et pour spécifier les en-têtes de colonne dans la table. Pour ajouter une propriété calculée, utilisez le paramètre **Property** ou **GroupBy** . Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

## EXEMPLES

### Exemple 1 : mettre en forme l’hôte PowerShell

Cet exemple affiche des informations sur le programme hôte pour PowerShell dans une table.

```powershell
Get-Host | Format-Table -AutoSize
```

L' `Get-Host` applet de commande obtient les objets **System. Management. Automation. Internal. Host. InternalHost** qui représentent l’hôte. Les objets sont envoyés dans le pipeline vers `Format-Table` et affichés dans une table. Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.

### Exemple 2 : mettre en forme les processus par BasePriority

Dans cet exemple, les processus sont affichés dans des groupes qui ont la même propriété **BasePriority** .

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

L' `Get-Process` applet de commande obtient les objets qui représentent chaque processus sur l’ordinateur et les envoie vers le pipeline `Sort-Object` . Les objets sont triés dans l’ordre de leur propriété **BasePriority** .

Les objets triés sont envoyés dans le pipeline à `Format-Table` . Le paramètre **GroupBy** organise les données de processus en groupes en fonction de la valeur de leur propriété **BasePriority** . Le paramètre **Wrap** garantit que les données ne sont pas tronquées.

### Exemple 3 : mettre en forme les processus par date de début

Cet exemple affiche des informations sur les processus en cours d’exécution sur l’ordinateur. Les objets sont triés et `Format-Table` utilisent une vue pour regrouper les objets en fonction de leur date de début.

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` Obtient les objets **System. Diagnostics. Process** qui représentent les processus en cours d’exécution sur l’ordinateur. Les objets sont envoyés dans le pipeline à `Sort-Object` , et sont triés en fonction de la propriété **StartTime** .

Les objets triés sont envoyés dans le pipeline à `Format-Table` . Le paramètre **View** spécifie la vue **StartTime** définie dans le fichier PowerShell `DotNetTypes.format.ps1xml` pour les objets **System. Diagnostics. Process** . La vue **StartTime** convertit l’heure de début de chaque processus en une date brève, puis regroupe les processus par date de début.

Le `DotNetTypes.format.ps1xml` fichier contient une vue de **priorité** pour les processus. Vous pouvez créer vos propres `format.ps1xml` fichiers avec des vues personnalisées.

### Exemple 4 : utiliser une vue personnalisée pour la sortie de table

Dans cet exemple, une vue personnalisée affiche le contenu d’un répertoire. La vue personnalisée ajoute la colonne **CreationTime** à la sortie de table pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` .

La vue personnalisée de cet exemple a été créée à partir de la vue définie dans le code source PowerShell. Pour plus d’informations sur les vues et le code utilisé pour créer l’affichage de cet exemple, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` Obtient le contenu du répertoire actif, `C:\Test` . Les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** sont envoyés dans le pipeline.
`Format-Table` utilise le paramètre **View** pour spécifier la vue personnalisée **mygciview** qui comprend la colonne **CreationTime** .

La sortie par défaut `Format-Table` pour `Get-ChildItem` n’inclut pas la colonne **CreationTime** .

### Exemple 5 : utiliser les propriétés de la sortie de table

Cet exemple utilise le paramètre **Property** pour afficher tous les services de l’ordinateur dans une table à deux colonnes qui affiche les propriétés **Name** et **DependentServices** .

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` Obtient tous les services sur l’ordinateur et envoie les objets **System. ServiceProcess. ServiceController** dans le pipeline. `Format-Table` utilise le paramètre **Property** pour spécifier que les propriétés **Name** et **DependentServices** sont affichées dans la table.

**Name** et **DependentServices** sont deux des propriétés du type d’objet. Pour afficher toutes les propriétés : `Get-Service | Get-Member -MemberType Properties` .

### Exemple 6 : mettre en forme un processus et calculer son temps d’exécution

Cet exemple affiche une table avec le nom du processus et la durée d’exécution totale pour les processus du **bloc-notes** de l’ordinateur local. La durée d'exécution totale est calculée en soustrayant l'heure de début de chaque processus de l'heure actuelle.

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` Obtient tous les processus du **bloc-notes** de l’ordinateur local et les envoie dans le pipeline. `Format-Table` affiche une table avec deux colonnes : **ProcessName** , `Get-Process` Property et **TotalRunningTime** , une propriété calculée.

La propriété **TotalRunningTime** est spécifiée par une table de hachage avec deux clés, **label** et **expression** . La clé de l' **étiquette** spécifie le nom de la propriété. La clé d' **expression** spécifie le calcul. L’expression obtient la propriété **StartTime** de chaque objet processus et la soustrait du résultat d’une `Get-Date` commande, qui obtient la date et l’heure actuelles.

### Exemple 7 : mettre en forme les processus Notepad

Cet exemple utilise `Get-CimInstance` pour obtenir le temps d’exécution de tous les processus du **bloc-notes** sur l’ordinateur local. Vous pouvez utiliser `Get-CimInstance` avec le paramètre **ComputerName** pour récupérer des informations à partir d’ordinateurs distants.

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance` obtient des instances de la classe de **WIN32_PROCESS** WMI qui décrit tous les processus de l’ordinateur local nommés **notepad.exe** . Les objets processus sont stockés dans la `$Processes` variable.

Les objets processus de la `$Processes` variable sont envoyés dans le pipeline à `Format-Table` , qui affiche la propriété **ProcessName** et une nouvelle propriété calculée, **durée totale d’exécution** .

La commande attribue le nom de la nouvelle propriété calculée, **durée totale d’exécution** , à la clé de l' **étiquette** . Le bloc de script de la clé d' **expression** calcule la durée d’exécution du processus en soustrayant la date de création du processus de la date actuelle. L' `Get-Date` applet de commande obtient la date actuelle. La date de création est soustraite de la date actuelle. Le résultat est la valeur de la **durée d’exécution totale** .

### Exemple 8 : dépannage des erreurs de format

Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday
Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (11/27/2019 12:52:38:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

Indique que l’applet de commande ajuste la taille de la colonne et le nombre de colonnes en fonction de la largeur des données. Par défaut, la vue détermine la taille et le nombre de colonnes.

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

### -DisplayError

Indique que l’applet de commande affiche les erreurs sur la ligne de commande. Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.

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

### -Développer

Spécifie le format de l’objet de collection et les objets de la collection. Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface [ICollection](/dotnet/api/system.collections.icollection) ([System. Collections](/dotnet/api/system.collections)). La valeur par défaut est **EnumOnly** .
Les valeurs acceptables pour ce paramètre sont les suivantes :

- **EnumOnly** : affiche les propriétés des objets dans la collection.
- **CoreOnly** : affiche les propriétés de l’objet de collection.
- **Both** : affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.

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

Indique que l’applet de commande ordonne à l’applet de commande d’afficher toutes les informations sur l’erreur. Utilisez avec le paramètre **DisplayError** ou **ShowError** . Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.

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

### -GroupBy

Spécifie la sortie triée dans des tables distinctes en fonction d’une valeur de propriété. Par exemple, vous pouvez utiliser **GroupBy** pour répertorier les services dans des tables distinctes en fonction de leur état.

Entrez une expression ou une propriété. Le paramètre **GroupBy** s’attend à ce que les objets soient triés.
Utilisez l' `Sort-Object` applet de commande avant `Format-Table` d’utiliser pour regrouper les objets.

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

### -HideTableHeaders

Omet les en-têtes de colonne de la table.

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

Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent. Tapez un ou plusieurs noms de propriété, en les séparant par des virgules, ou utilisez une table de hachage pour afficher une propriété calculée. Les caractères génériques sont autorisés.

Si vous omettez ce paramètre, les propriétés qui s’affichent dans l’affichage dépendent des propriétés du premier objet. Par exemple, si le premier objet a **PropertyA** et **PropertyB** , mais que les objets suivants possèdent **PropertyA** , **PropertyB** et **PropertyC** , seuls les en-têtes **PropertyA** et **PropertyB** s’afficheront.

Le paramètre **Property** est facultatif. Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Nom (ou étiquette) `<string>`
- Expression `<string>` ou `<script block>`
- FormatString `<string>`
- Largeur- `<int32>` -doit être supérieur à `0`
- Alignment : la valeur peut être `Left` , `Center` ou `Right`

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

### -RepeatHeader

Répète l’affichage de l’en-tête d’un tableau après chaque écran complet. L’en-tête répété est utile lorsque la sortie est dirigée vers un récepteur de radiomessagerie tel que `less` ou, `more` ou en utilisant un lecteur d’écran.

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

### -ShowError

Ce paramètre envoie des erreurs via le pipeline. Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.

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

### -Afficher

À compter de PowerShell 6, les vues par défaut sont définies dans le `C#` code source PowerShell. Les `*.format.ps1xml` fichiers de powershell 5,1 et versions antérieures n’existent pas dans PowerShell 6 et versions ultérieures.

Le paramètre **View** vous permet de spécifier un autre format ou une autre vue personnalisée pour la table. Vous pouvez utiliser les vues PowerShell par défaut ou créer des vues personnalisées. Pour plus d’informations sur la création d’un affichage personnalisé, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

Les vues alternatives et personnalisées pour le paramètre **View** doivent utiliser le format de table ; sinon, `Format-Table` échoue. Si l’autre vue est une liste, utilisez l' `Format-List` applet de commande. Si l’autre vue n’est ni une liste ni une table, utilisez l’applet de commande `Format-Custom` .

Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.

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

### -Wrap

Affiche le texte qui dépasse de la largeur de colonne sur la ligne suivante. Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez envoyer n’importe quel objet dans le pipeline à `Format-Table` .

## SORTIES

### Microsoft. PowerShell. Commands. Internal. format

`Format-Table` retourne les objets de format représentant la table.

## REMARQUES

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Export-FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Get-Member](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Update-FormatData](Update-FormatData.md)

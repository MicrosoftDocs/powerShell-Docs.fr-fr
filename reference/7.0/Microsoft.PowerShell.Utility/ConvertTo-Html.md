---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 21ef51476ccee8efc5c7c13d273ef8a7811f33c4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205918"
---
# ConvertTo-Html

## SYNOPSIS
Convertit les objets .NET en code HTML qui peut être affiché dans un navigateur web.

## SYNTAX

### Page (par défaut)

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### Fragment

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## Description

L' `ConvertTo-Html` applet de commande convertit les objets .net en HTML qui peuvent être affichés dans un navigateur Web. Vous pouvez utiliser cette applet de commande pour afficher la sortie d'une commande dans une page web.

Vous pouvez utiliser les paramètres de `ConvertTo-Html` pour sélectionner des propriétés d’objet, pour spécifier un format de table ou de liste, pour spécifier le titre de la page HTML, pour ajouter du texte avant et après l’objet et pour retourner uniquement le fragment de table ou de liste, au lieu d’une page DTD stricte.

Lorsque vous envoyez plusieurs objets à `ConvertTo-Html` , PowerShell crée la table (ou la liste) en fonction des propriétés du premier objet que vous envoyez. Si les objets restants n'ont pas l'une des propriétés spécifiées, la valeur de propriété de cet objet est une cellule vide. Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété ne sont pas incluses dans le fichier.

## EXEMPLES

### Exemple 1 : créer une page Web pour afficher la date

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

Cette commande crée une page HTML qui affiche les propriétés de la date actuelle. Elle utilise le paramètre **InputObject** pour envoyer les résultats d’une `Get-Date` commande à l' `ConvertTo-Html` applet de commande.

### Exemple 2 : créer une page Web pour afficher des alias PowerShell

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

Cette commande crée une page HTML qui répertorie les alias PowerShell dans la console active.

La commande utilise l' `Get-Alias` applet de commande pour récupérer les alias. Elle utilise l’opérateur de pipeline ( `|` ) pour envoyer les alias à l’applet de commande `ConvertTo-Html` , qui crée la page html. La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `aliases.htm` fichier.

### Exemple 3 : créer une page Web pour afficher les événements PowerShell

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

Cette commande crée une page HTML appelée `pslog.htm` qui affiche les événements dans le journal des événements Windows PowerShell sur l’ordinateur local.

Elle utilise l' `Get-EventLog` applet de commande pour récupérer les événements dans le journal Windows PowerShell, puis utilise l’opérateur de pipeline ( `|` ) pour envoyer les événements à l’applet de commande `ConvertTo-Html` . La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `pslog.htm` fichier.

La commande utilise également l' `Out-File` applet de commande pour envoyer le code HTML au `pslog.htm` fichier.

### Exemple 4 : créer une page Web pour afficher des processus

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

Ces commandes créent et ouvrent une page HTML qui répertorie le nom, le chemin d'accès et la société des processus sur l'ordinateur local.

La première commande utilise l' `Get-Process` applet de commande pour récupérer des objets qui représentent les processus en cours d’exécution sur l’ordinateur. La commande utilise l’opérateur de pipeline ( `|` ) pour envoyer les objets de processus à l’applet de commande `ConvertTo-Html` .

La commande utilise le paramètre **Property** pour sélectionner trois propriétés des objets Process à inclure dans la table. La commande utilise le paramètre **title** pour spécifier un titre pour la page html. La commande utilise également l' `Out-File` applet de commande pour envoyer le code html résultant vers un fichier nommé Proc.htm.

La deuxième commande utilise l' `Invoke-Item` applet de commande pour ouvrir le `Proc.htm` dans le navigateur par défaut.

### Exemple 5 : créer une page Web pour afficher des objets de service

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

Cette commande crée une page HTML des objets de service `Get-Service` retournées par l’applet de commande. La commande utilise le paramètre **CssUri** pour spécifier une feuille de style en cascade pour la page html.

Le paramètre **CssUri** ajoute une `<link rel="stylesheet" type="text/css" href="test.css">` balise supplémentaire au code html résultant. L'attribut HREF de la balise contient le nom de la feuille de style.

### Exemple 6 : créer une page Web pour afficher des objets de service

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

Cette commande crée une page HTML des objets de service `Get-Service` retournées par l’applet de commande. La commande utilise le paramètre **As** pour spécifier un format de liste. L’applet `Out-File` de commande envoie le code html résultant au `Services.htm` fichier.

### Exemple 7 : créer une table Web pour la date du jour

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

Cette commande utilise `ConvertTo-Html` pour générer une table HTML de la date actuelle. La commande utilise l' `Get-Date` applet de commande pour récupérer la date actuelle. Elle utilise un opérateur de pipeline (|) pour envoyer les résultats à l’applet de commande `ConvertTo-Html` .

La `ConvertTo-Html` commande comprend le paramètre **fragment** , qui limite la sortie à une table HTML. Par conséquent, les autres éléments d'une page HTML, tels que les balises `<HEAD>` et `<BODY>`, sont omis.

### Exemple 8 : créer une page Web pour afficher les événements PowerShell

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

Cette commande utilise la `Get-EventLog` cmdlet pour récupérer des événements à partir du journal des événements Windows PowerShell.

Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les événements à l’applet de commande `ConvertTo-Html` , qui convertit les événements au format html.

La `ConvertTo-Html` commande utilise le paramètre **Property** pour sélectionner uniquement les propriétés **ID** , **Level** et **Task** de l’événement.

### Exemple 9 : créer une page Web pour afficher les services spécifiés

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

Cette commande crée et ouvre une page Web qui affiche les services sur l’ordinateur qui commencent par. Elle utilise le **titre** , le **corps** , le **prétexte** et les paramètres **PostContent** de `ConvertTo-Html` pour personnaliser la sortie.

La première partie de la commande utilise l' `Get-Service` applet de commande pour obtenir les services sur l’ordinateur qui commencent par. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats à l’applet de commande `ConvertTo-Html` . La commande utilise également l' `Out-File` applet de commande pour envoyer la sortie vers le fichier Services.htm.

Un point-virgule ( `;` ) termine la première commande et démarre une deuxième commande, qui utilise l' `Invoke-Item` applet de commande pour ouvrir le `Services.htm` fichier dans le navigateur par défaut.

### Exemple 10 : définir les propriétés méta et le charset du code HTML

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

Cette commande crée le code HTML pour une page Web avec les balises méta pour l’actualisation, l’auteur et les mots clés.
Le jeu de caractères de la page est défini sur UTF-8

### Exemple 11 : définir la DTD transitoire du code HTML sur XHTML

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

Cette commande définit le DOCTYPE du HTML retourné sur la DTD transitoire XHTML

## PARAMETERS

### -As

Détermine si l'objet est dans un format de table ou de liste. Les valeurs valides sont **table** et **List** . La valeur par défaut est **table** .

La valeur de **table** génère une table HTML qui ressemble au format de table PowerShell. La ligne d'en-tête affiche les noms des propriétés. Chaque ligne de la table représente un objet et affiche les valeurs de l'objet pour chaque propriété.

La valeur **List** génère une table HTML à deux colonnes pour chaque objet qui ressemble au format de liste PowerShell. La première colonne affiche le nom de la propriété. La deuxième colonne affiche la valeur de la propriété.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Corps

Spécifie le texte à ajouter après la balise ouvrante `<BODY>`. Par défaut, il n'y a pas de texte à cette position.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Charset

Spécifie le texte à ajouter à la `<charset>` balise d’ouverture. Par défaut, il n'y a pas de texte à cette position.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CssUri

Spécifie l'URI (Uniform Resource Identifier) de la feuille de style en cascade (CSS) qui est appliquée au fichier HTML. L'URI est inclus dans un lien de feuille de style dans la sortie.

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fragment

Génère uniquement une table HTML. Les balises HTML, HEAD, TITLE et BODY sont omises.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Head

Spécifie le contenu de la balise `<HEAD>`. La valeur par défaut est `<title\>HTML TABLE</title>`. Si vous utilisez le paramètre **Head** , le paramètre **title** est ignoré.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à représenter au format HTML. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.

Si vous utilisez ce paramètre pour envoyer plusieurs objets, tels que tous les services sur un ordinateur, `ConvertTo-Html` crée une table qui affiche les propriétés d’une collection ou d’un tableau d’objets. Pour créer une table des objets individuels, utilisez l’opérateur de pipeline pour diriger les objets vers `ConvertTo-Html` .

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

### -Méta

Spécifie le texte à ajouter à la `<meta>` balise d’ouverture. Par défaut, il n'y a pas de texte à cette position.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PostContent

Spécifie le texte à ajouter après la balise fermante `</TABLE>`. Par défaut, il n'y a pas de texte à cette position.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prétexte

Spécifie le texte à ajouter avant la balise ouvrante `<TABLE>`. Par défaut, il n'y a pas de texte à cette position.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Inclut les propriétés spécifiées des objets dans le code HTML. La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Nom (ou étiquette)- `<string>` (ajouté dans PowerShell 6. x)
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
Accept wildcard characters: False
```

### -Title

Spécifie un titre pour le fichier HTML, c'est-à-dire le texte qui apparaît entre les balises `<TITLE>`.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Transitionnel

Change la Déclaration **DOCTYPE** en **DTD transitoire XHTML** , le **DOCTYPE** par défaut est **xhtml strict DTD** .

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
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

Vous pouvez diriger n’importe quel objet .NET vers `ConvertTo-Html` .

## SORTIES

### Document System. String ou System.Xml.Xml

`ConvertTo-Html` retourne une série de chaînes qui comprennent du code HTML valide.

## REMARQUES

Pour utiliser cette applet de commande, dirigez un ou plusieurs objets vers l’applet de commande ou utilisez le paramètre **InputObject** pour spécifier l’objet. Quand l'entrée comporte plusieurs objets, la sortie de ces deux méthodes est assez différente.

- Lorsque vous dirigez plusieurs objets vers une applet de commande, PowerShell envoie les objets à l’applet de commande, l’un après l’autre. Par conséquent, `ConvertTo-Html` crée une table qui affiche les objets individuels. Par exemple, si vous dirigez les processus sur un ordinateur vers `ConvertTo-Html` , la table résultante affiche tous les processus.

- Quand vous utilisez le paramètre **InputObject** pour envoyer plusieurs objets, `ConvertTo-Html` reçoit ces objets sous la forme d’une collection ou d’un tableau. Par conséquent, l'applet de commande crée une table qui affiche le tableau et ses propriétés, pas les éléments du tableau. Par exemple, si vous utilisez **InputObject** pour envoyer les processus sur un ordinateur à `ConvertTo-Html` , la table résultante affiche un tableau d’objets et ses propriétés.

  Pour se conformer à la DTD strict XHTML, la balise DOCTYPE est modifiée en conséquence :

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Clixml](Export-Clixml.md)

[Import-Clixml](Import-Clixml.md)

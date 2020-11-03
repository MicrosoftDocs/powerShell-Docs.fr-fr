---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206185"
---
# ConvertFrom-String

## SYNOPSIS
Extrait et analyse les propriétés structurées à partir du contenu de chaîne.

## SYNTAX

### ByDelimiter (par défaut)

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### TemplateParsing

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## Description

L’applet de commande **ConvertFrom-String** extrait et analyse les propriétés structurées à partir du contenu de chaîne.
Cette applet de commande génère un objet en analysant du texte à partir d’un flux de texte traditionnel.
Pour chaque chaîne dans le pipeline, l’applet de commande fractionne l’entrée par un délimiteur ou une expression d’analyse, puis assigne des noms de propriété à chacun des éléments fractionnés résultants.
Vous pouvez fournir ces noms de propriétés. Si vous ne le faites pas, ils sont automatiquement générés pour vous.

Le jeu de paramètres par défaut de l’applet de commande, **ByDelimiter** , se divise exactement par le délimiteur d’expression régulière.
Il n’effectue pas de correspondance de guillemets ou de délimiteurs dans le cadre de l’applet de commande `Import-Csv` .

Le jeu de paramètres alternatif de l’applet de commande, **TemplateParsing** , génère des éléments à partir des groupes capturés par une expression régulière. Pour plus d’informations sur les expressions régulières, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).

Cette applet de commande prend en charge deux modes : l’analyse de base délimitée et l’analyse basée sur les exemples générées automatiquement.

Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.

Vous pouvez personnaliser le délimiteur en canalisant les `ConvertFrom-String` résultats dans l’une des `Format-*` applets de commande, ou vous pouvez utiliser le paramètre **Delimiter** .

L’applet de commande prend également en charge l’analyse générée automatiquement, basée sur des exemples, basée sur le [FlashExtract, la recherche effectuée par Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).

## EXEMPLES

### Exemple 1 : générer un objet avec des noms de propriétés par défaut

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

Cette commande génère un objet avec des noms de propriétés par défaut, **P1** et **P2** .

### Exemple 1A : découverte de l’objet généré

Cette commande génère un objet avec les propriétés **P1** , **P2** ; par défaut, les deux propriétés sont de type **chaîne** .

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### Exemple 2 : générer un objet avec des noms de propriétés par défaut à l’aide d’un délimiteur

Cette commande génère un objet avec un domaine et un nom d’utilisateur en utilisant la barre oblique inverse ( `\` ) comme délimiteur. La barre oblique inverse doit être placée dans une séquence d’échappement avec une autre barre oblique inverse lors de l’utilisation d’expressions régulières.

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### Exemple 3 : générer un objet qui contient deux propriétés nommées

L’exemple suivant crée des objets à partir de Windows héberge des entrées de fichier.

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

L' `Get-Content` applet de commande stocke le contenu d’un fichier d’hôtes Windows dans `$content` . La deuxième commande supprime tous les commentaires au début du fichier hosts à l’aide d’une expression régulière qui correspond à une ligne qui ne commence pas par ( `#` ). La dernière commande convertit le texte restant en objets avec les propriétés **Server** et **IP** .

### Exemple 4 : utilisez une expression comme valeur du paramètre TemplateContent, puis enregistrez les résultats dans une variable.

Cette commande utilise une expression comme valeur du paramètre **TemplateContent** .
L’expression est enregistrée dans une variable pour des raisons de simplicité.
Windows PowerShell comprend maintenant que la chaîne utilisée sur le pipeline `ConvertFrom-String` possède trois propriétés :

- **Nom**
- **phone**
- **vieillissement**

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

Chaque ligne de l’entrée est évaluée par les correspondances d’échantillon. Si la ligne correspond aux exemples fournis dans le modèle, les valeurs sont extraites et transmises à la variable de sortie.

Les exemples de données, `$template` , fournissent deux formats de téléphone différents :

- `425-123-6789`
- `(206) 987-4321`

Les exemples de données fournissent également deux formats d’âge différents :

- `6`
- `12`

Cela implique que les téléphones comme `(206) 987 4321` ne seront pas reconnus, car il n’y a pas d’exemple de données correspondant à ce modèle, car il n’y a pas de trait d’Union.

### Exemple 5 : spécification des types de données pour les propriétés générées

Il s’agit du même exemple que l’exemple 4, ci-dessus.
La différence est que la chaîne de modèle comprend un type de données pour chaque propriété souhaitée.

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

L' `Get-Member` applet de commande est utilisée pour indiquer que la propriété **Age** est un entier.

## PARAMETERS

### -Délimiteur

Spécifie une expression régulière qui identifie la limite entre les éléments.
Les éléments créés par le fractionnement deviennent des propriétés dans l’objet résultant.
Le délimiteur est finalement utilisé dans un appel à la méthode **Split** du type `[System.Text.RegularExpressions.RegularExpression]` .

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Paramètre includeextent

Indique que cette applet de commande comprend une propriété de texte d’étendue qui est supprimée par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les chaînes reçues du pipeline, ou une variable qui contient un objet String.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PropertyNames

Spécifie un tableau de noms de propriétés auquel assigner des valeurs de fractionnement dans l’objet résultant.
Chaque ligne de texte que vous fractionnez ou analysez génère des éléments qui représentent des valeurs de propriété.
Si l’élément est le résultat d’un groupe de capture et que ce groupe de capture est nommé (par exemple, `(?<name>)` ou `(?'name')` ), le nom de ce groupe de capture est assigné à la propriété.

Si vous fournissez des éléments dans le tableau **PropertyName** , ces noms sont assignés à des propriétés qui n’ont pas encore été nommées.

Si vous fournissez plus de noms de propriétés qu’il n’y a de champs, PowerShell ignore les noms de propriété supplémentaires. Si vous ne spécifiez pas un nombre de noms de propriété suffisant pour nommer tous les champs, PowerShell attribue automatiquement des noms de propriété numériques à toutes les propriétés qui ne sont pas nommées : **P1** , **P2** , etc.

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContent

Spécifie une expression ou une expression enregistrée en tant que variable, qui décrit les propriétés auxquelles cette applet de commande affecte des chaînes. La syntaxe d’une spécification de champ de modèle est la suivante : `{[optional-typecast]<name>:<example-value>}` .

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateFile

Spécifie un fichier, sous la forme d’un tableau, qui contient un modèle pour l’analyse souhaitée de la chaîne.
Dans le fichier de modèle, les propriétés et leurs valeurs sont placées entre crochets, comme indiqué ci-dessous.
Si une propriété, telle que la propriété **nom** et les autres propriétés qui lui sont associées, apparaît plusieurs fois, vous pouvez ajouter un astérisque ( `*` ) pour indiquer que cela génère plusieurs enregistrements. Cela évite l’extraction de plusieurs propriétés dans un seul enregistrement.

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UpdateTemplate

Indique que cette applet de commande enregistre les résultats d’un algorithme d’apprentissage dans un commentaire dans le fichier de modèle.
Le processus d’apprentissage de l’algorithme est ainsi plus rapide.
Pour utiliser ce paramètre, vous devez également spécifier un fichier de modèle avec le paramètre **TemplateFile** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

## SORTIES

## REMARQUES

## LIENS CONNEXES

[ConvertFrom-String : analyse de texte basée sur des exemples](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[ConvertFrom-StringData](ConvertFrom-StringData.md)

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

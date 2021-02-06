---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: c95ebca6307d58668c31faf3e492617f49ddebf4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597547"
---
# ConvertFrom-StringData

## SYNOPSIS
Convertit une chaîne contenant une ou plusieurs paires clé/valeur en une table de hachage.

## SYNTAXE

### Tous

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## Description

L' `ConvertFrom-StringData` applet de commande convertit une chaîne qui contient une ou plusieurs paires clé/valeur en une table de hachage. Étant donné que chaque paire clé-valeur doit se trouver sur une ligne distincte, les chaînes sont souvent utilisées comme format d’entrée. Par défaut, la **clé** doit être séparée de la **valeur** par un caractère signe égal ( `=` ).

L' `ConvertFrom-StringData` applet de commande est considérée comme une applet de commande sécurisée qui peut être utilisée dans la `DATA` section d’un script ou d’une fonction. Lorsqu’il est utilisé dans une `DATA` section, le contenu de la chaîne doit se conformer aux règles d’une section de données. Pour plus d’informations, consultez [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).

`ConvertFrom-StringData` prend en charge les séquences de caractères d’échappement qui sont autorisées par les outils de traduction automatique conventionnels. Autrement dit, l’applet de commande peut interpréter les barres obliques inverses ( `\` ) comme des caractères d’échappement dans les données de chaîne à l’aide de la [méthode Regex. Unescape](/dotnet/api/system.text.regularexpressions.regex.unescape), au lieu du caractère de \` soulignement () PowerShell qui signalerait normalement la fin d’une ligne dans un script. À l'intérieur de la chaîne « ici-même », le caractère de guillemet inversé ne fonctionne pas. Vous pouvez également conserver une barre oblique inverse littérale dans vos résultats en l’plaçant dans une séquence d’échappement avec une barre oblique inverse précédente, comme suit : `\\` . Les caractères de barre oblique inverse sans séquence d'échappement, comme celles qui sont couramment utilisées dans les chemins d'accès, peuvent apparaître comme des séquences d'échappement non autorisées dans vos résultats.

PowerShell 7 ajoute le paramètre **Delimiter** .

## EXEMPLES

### Exemple 1 : convertir une chaîne « here » entre guillemets simples en une table de hachage

Cet exemple convertit une chaîne « ici- » en une seule citation de messages utilisateur en une table de hachage. Dans une chaîne entre guillemets simples, les variables ne sont pas remplacées par les valeurs et les expressions ne sont pas évaluées.
L' `ConvertFrom-StringData` applet de commande convertit la valeur de la `$Here` variable en une table de hachage.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### Exemple 2 : convertir des données de type chaîne à l’aide d’un séparateur différent

Cet exemple montre comment convertir des données de type chaîne qui utilisent un caractère différent comme délimiteur. Dans cet exemple, les données de chaîne utilisent le caractère de barre verticale ( `|` ) comme délimiteur.

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### Exemple 3 : convertir une chaîne here contenant un commentaire

Cet exemple convertit une chaîne « here » qui contient un commentaire et plusieurs paires clé-valeur en une table de hachage.

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

La valeur du paramètre **StringData** est une chaîne ici, au lieu d’une variable qui contient une chaîne ici. Les deux formats sont valides. La chaîne « ici-même » contient un commentaire sur une des chaînes.
`ConvertFrom-StringData` ignore les commentaires sur une seule ligne, mais le `#` caractère doit être le premier caractère autre qu’un espace blanc sur la ligne. Tous les caractères de la ligne après `#` sont ignorés.

### Exemple 4 : convertir une chaîne en une table de hachage

Cet exemple convertit une chaîne entre guillemets standard (pas une chaîne ici) en une table de hachage et l’enregistre dans la `$A` variable.

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

Pour satisfaire la condition selon laquelle chaque paire clé-valeur doit se trouver sur une ligne distincte, la chaîne utilise le caractère de saut de ligne de PowerShell ( \` n) pour séparer les paires.

### Exemple 5 : utiliser ConvertFrom-StringData dans la section de données d’un script

Cet exemple montre une `ConvertFrom-StringData` commande utilisée dans la section Data d’un script.
Les instructions sous la section DATA affichent le texte à l'utilisateur.

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

Comme le texte comprend des noms de variables, il doit figurer dans une chaîne entre guillemets simples pour que les variables soient interprétées littéralement et non pas développées. Les variables ne sont pas autorisées dans la section **Data** .

### Exemple 6 : utilisation de l’opérateur pipeline pour passer une chaîne

Cet exemple montre que vous pouvez utiliser un opérateur de pipeline ( `|` ) pour envoyer une chaîne à `ConvertFrom-StringData` . La valeur de la `$Here` variable est dirigée vers `ConvertFrom-StringData` et le résultat dans la `$Hash` variable.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### Exemple 7 : utiliser des caractères d’échappement pour ajouter de nouvelles lignes et retourner des caractères

Cet exemple illustre l’utilisation de caractères d’échappement pour créer des lignes et retourner des caractères dans les données sources. La séquence `\n` d’échappement est utilisée pour créer de nouvelles lignes au sein d’un bloc de texte associé à un nom ou à un élément dans la table de hachage résultante.

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### Exemple 8 : utiliser un caractère d’échappement barre oblique inverse pour restituer correctement un chemin d’accès de fichier

Cet exemple montre comment utiliser le caractère d’échappement barre oblique inverse dans les données de chaîne pour permettre le rendu correct d’un chemin d’accès de fichier dans la table de hachage résultante `ConvertFrom-StringData` . La double barre oblique inverse fait que les caractères de barre oblique inverse littérale s'affichent correctement dans la sortie de table de hachage.

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETERS

### -StringData

Spécifie la chaîne à convertir. Vous pouvez utiliser ce paramètre ou diriger une chaîne vers `ConvertFrom-StringData` . Le nom de paramètre est facultatif.

La valeur de ce paramètre doit être une chaîne qui contient une ou plusieurs paires clé-valeur. Chaque paire clé-valeur doit se trouver sur une ligne distincte, ou chaque paire doit être séparée par des caractères de saut de ligne ( \` n).

Vous pouvez inclure des commentaires dans la chaîne, mais les commentaires ne peuvent pas se trouver sur la même ligne qu’une paire clé-valeur. `ConvertFrom-StringData` ignore les commentaires sur une seule ligne. Le `#` caractère doit être le premier caractère autre qu’un espace blanc sur la ligne. Tous les caractères de la ligne après `#` sont ignorés. Les commentaires ne sont pas inclus dans la table de hachage.

Une chaîne ici est une chaîne composée d’une ou de plusieurs lignes. Les guillemets dans la chaîne ici sont interprétés littéralement comme faisant partie des données de chaîne. Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).

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

### -Délimiteur

Caractère utilisé pour séparer la **clé** des données de **valeur** dans la chaîne en cours de conversion.
Le délimiteur par défaut est le signe égal ( `=` ). Ce paramètre a été ajouté dans PowerShell 7.

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne contenant une paire clé-valeur vers `ConvertFrom-StringData` .

## SORTIES

### System.Collections.Hashtable

Cette applet de commande retourne une table de hachage qu’elle crée à partir des paires clé-valeur.

## REMARQUES

Une chaîne « ici-même » est une chaîne composée d'une ou plusieurs lignes, dans laquelle les guillemets sont interprétés littéralement.

Cette applet de commande peut être utile dans les scripts qui affichent des messages utilisateur dans plusieurs langues parlées. Vous pouvez utiliser les tables de hachage de type dictionnaire pour isoler les chaînes de texte du code, comme dans des fichiers de ressources, et pour mettre en forme les chaînes de texte pour qu'elles soient utilisables dans des outils de traduction.

## LIENS CONNEXES


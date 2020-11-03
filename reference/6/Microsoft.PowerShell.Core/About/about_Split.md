---
description: Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: 520aac1fd1aae4f1f0f4a12a10bc4f5c7f258731
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206850"
---
# <a name="about-split"></a>À propos du fractionnement

## <a name="short-description"></a>DESCRIPTION COURTE
Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L’opérateur split fractionne une ou plusieurs chaînes en sous-chaînes. Vous pouvez modifier les éléments suivants de l’opération de fractionnement :

- Limite. La valeur par défaut est l’espace blanc, mais vous pouvez spécifier des caractères, des chaînes, des modèles ou des blocs de script qui spécifient le délimiteur. L’opérateur split dans PowerShell utilise une expression régulière dans le délimiteur, plutôt qu’un caractère simple.
- Nombre maximal de sous-chaînes. La valeur par défaut consiste à retourner toutes les sous-chaînes. Si vous spécifiez un nombre inférieur au nombre de sous-chaînes, les sous-chaînes restantes sont concaténées dans la dernière sous-chaîne.
- Options qui spécifient les conditions sous lesquelles le délimiteur est mis en correspondance, par exemple SimpleMatch et Multiline.

## <a name="syntax"></a>SYNTAX

Le diagramme suivant illustre la syntaxe de l’opérateur-Split.

Les noms de paramètres n’apparaissent pas dans la commande. N’incluez que les valeurs des paramètres. Les valeurs doivent apparaître dans l’ordre spécifié dans le diagramme de syntaxe.

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

Vous pouvez remplacer `-iSplit` ou `-cSplit` par `-split` n’importe quelle instruction de fractionnement binaire (instruction Split incluant un délimiteur ou un bloc de script). Les `-iSplit` `-split` opérateurs et ne respectent pas la casse. L' `-cSplit` opérateur respecte la casse, ce qui signifie que la casse est prise en compte lors de l’application des règles de délimiteur.

## <a name="parameters"></a>PARAMETERS

### <a name="string-or-string"></a>\<String\> ou \<String[]\>

Spécifie une ou plusieurs chaînes à fractionner. Si vous envoyez plusieurs chaînes, toutes les chaînes sont fractionnées à l’aide des mêmes règles de délimiteur.

Exemple :

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

Caractères qui identifient la fin d’une sous-chaîne. Le délimiteur par défaut est l’espace blanc, y compris les espaces et les caractères non imprimables, tels que les sauts de ligne ( \` n) et TAB ( \` t). Lorsque les chaînes sont fractionnées, le délimiteur est omis dans toutes les sous-chaînes. Exemple :

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

Par défaut, le délimiteur est omis des résultats. Pour conserver tout ou partie du délimiteur, mettez entre parenthèses le composant que vous souhaitez conserver.
Si le \<Max-substrings\> paramètre est ajouté, il est prioritaire lorsque votre commande fractionne la collection. Si vous choisissez d’inclure un délimiteur dans le cadre de la sortie, la commande renvoie le délimiteur dans le cadre de la sortie ; Toutefois, le fractionnement de la chaîne pour retourner le délimiteur dans le cadre de la sortie n’est pas compté comme une division.

Exemples :

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

Dans l’exemple suivant, \<Max-substrings\> a la valeur 3. Il en résulte trois fractionnements des valeurs de chaîne, mais un total de cinq chaînes dans le résultat obtenu ; le délimiteur est inclus après les fractionnements, jusqu’à ce que le nombre maximal de trois sous-chaînes soit atteint. Les délimiteurs supplémentaires dans la sous-chaîne finale deviennent partie intégrante de la sous-chaîne.

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

Spécifie le nombre maximal de fois où une chaîne est fractionnée. La valeur par défaut est toutes les sous-chaînes fractionnées par le délimiteur. S’il y a plus de sous-chaînes, elles sont concaténées à la sous-chaîne finale. S’il y a moins de sous-chaînes, toutes les sous-chaînes sont retournées. La valeur 0 et les valeurs négatives retournent toutes les sous-chaînes.

Max-substrings ne spécifie pas le nombre maximal d’objets retournés ; sa valeur est égale au nombre maximal de fois où une chaîne est fractionnée.
Si vous envoyez plusieurs chaînes (un tableau de chaînes) à l’opérateur de fractionnement, la limite de nombre maximal de sous-chaînes est appliquée séparément à chaque chaîne.

Exemple :

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

Expression qui spécifie les règles d’application du délimiteur. L’expression doit prendre la valeur $true ou $false. Placez le bloc de script entre accolades.

Exemple :

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

Placez le nom de l’option entre guillemets. Les options ne sont valides que lorsque le \<Max-substrings\> paramètre est utilisé dans l’instruction.

La syntaxe du paramètre options est la suivante :

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

Les options SimpleMatch sont les suivantes :

- **SimpleMatch** : utilisez une comparaison de chaînes simple lors de l’évaluation du délimiteur. Ne peut pas être utilisé avec RegexMatch.
- **IgnoreCase** : force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.

Les options RegexMatch sont les suivantes :

- **RegexMatch** : utilisez la correspondance d’expression régulière pour évaluer le délimiteur. Il s'agit du comportement par défaut. Ne peut pas être utilisé avec SimpleMatch.
- **IgnoreCase** : force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.
- **CultureInvariant** : ignore les différences culturelles dans la langue lorsque vous permettant évaluer le délimiteur. Valide uniquement avec RegexMatch.
- **IgnorePatternWhitespace** : ignore les espaces blancs sans séquence d’échappement et les commentaires marqués avec le signe dièse (#). Valide uniquement avec RegexMatch.
- **Multiligne** : le mode multiligne force `^` et `$` correspond à la fin de chaque ligne au lieu du début et de la fin de la chaîne d’entrée.
- **Singleline** : le mode Singleline traite la chaîne d’entrée comme un *Singleline* .
  Elle force le `.` caractère à correspondre à chaque caractère (y compris les nouvelles lignes), au lieu de faire correspondre tous les caractères à l’exception du saut de ligne `\n` .
- **ExplicitCapture** : ignore les groupes de correspondances sans nom afin que seuls les groupes de capture explicites soient retournés dans la liste de résultats. Valide uniquement avec RegexMatch.

## <a name="unary-and-binary-split-operators"></a>OPÉRATEURS unaires et de FRACTIONNEment binaire

L’opérateur de fractionnement unaire ( `-split <string>` ) a une priorité plus élevée qu’une virgule. Par conséquent, si vous soumettez une liste de chaînes séparées par des virgules à l’opérateur de fractionnement unaire, seule la première chaîne (avant la première virgule) est fractionnée.

Utilisez l’un des modèles suivants pour fractionner plus d’une chaîne :

- Utiliser l’opérateur de fractionnement binaire ( \<string[]\> -Split \<delimiter\> )
- Placez toutes les chaînes entre parenthèses
- Stocke les chaînes dans une variable, puis soumet la variable à l’opérateur Split

Prenons l’exemple suivant :

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>EXEMPLES

L’instruction suivante fractionne la chaîne à l’espace blanc.

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

L’instruction suivante fractionne la chaîne à n’importe quelle virgule.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

L’instruction suivante fractionne la chaîne au modèle « er ».

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

L’instruction suivante effectue un fractionnement sensible à la casse à la lettre « N ».

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

L’instruction suivante fractionne la chaîne à « e » et « t ».

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

L’instruction suivante fractionne la chaîne à « e » et « r », mais limite les sous-chaînes résultantes à six sous-chaînes.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

L’instruction suivante fractionne une chaîne en trois sous-chaînes.

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

L’instruction suivante fractionne deux chaînes en trois sous-chaînes.
(La limite est appliquée indépendamment à chaque chaîne.)

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

L’instruction suivante fractionne chaque ligne de la chaîne ici au premier chiffre. Elle utilise l’option Multiline pour reconnaître le début de chaque ligne et chaîne.

Le 0 représente la valeur « Return All » du paramètre Max-substrings. Vous pouvez utiliser des options, telles que Multiline, uniquement lorsque la valeur Max-substrings est spécifiée.

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

L’instruction suivante utilise la barre oblique inverse pour échapper le séparateur de points (.).

Avec la valeur par défaut, RegexMatch, le point placé entre guillemets (".") est interprété pour correspondre à n’importe quel caractère, à l’exception d’un caractère de saut de ligne. Par conséquent, l’instruction Split retourne une ligne vide pour chaque caractère à l’exception de NewLine.

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

L’instruction suivante utilise l’option SimpleMatch pour indiquer à l’opérateur-split d’interpréter le délimiteur de point (.) littéralement.

Le 0 représente la valeur « Return All » du paramètre Max-substrings. Vous pouvez utiliser des options, telles que SimpleMatch, uniquement lorsque la valeur Max-substrings est spécifiée.

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

L’instruction suivante fractionne la chaîne à l’un des deux délimiteurs, en fonction de la valeur d’une variable.

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>VOIR AUSSI

[Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Join](about_Join.md)

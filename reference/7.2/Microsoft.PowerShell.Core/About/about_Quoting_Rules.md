---
description: Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: ba4111937245939961689935181be5d547c8e112
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "99603477"
---
# <a name="about-quoting-rules"></a>À propos des règles de Quotation

## <a name="short-description"></a>Description courte
Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.

## <a name="long-description"></a>Description longue

Des guillemets sont utilisés pour spécifier une chaîne littérale. Vous pouvez placer une chaîne entre guillemets simples ( `'` ) ou guillemets doubles ( `"` ).

Des guillemets sont également utilisés pour créer une _chaîne ici-_. Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement. Une chaîne ici peut s’étendre sur plusieurs lignes. Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes, même si elles ne sont pas placées entre guillemets.

Dans les commandes des ordinateurs distants, les guillemets définissent les parties de la commande qui sont exécutées sur l’ordinateur distant. Dans une session à distance, les guillemets déterminent également si les variables d’une commande sont d’abord interprétées sur l’ordinateur local ou sur l’ordinateur distant.

## <a name="single-and-double-quoted-strings"></a>Chaînes entre guillemets simples et doubles

Une chaîne placée entre guillemets doubles est une chaîne _pouvant être développée_ . Les noms de variables précédés d’un signe dollar ( `$` ) sont remplacés par la valeur de la variable avant que la chaîne soit transmise à la commande à des fins de traitement.

Par exemple :

```powershell
$i = 5
"The value of $i is $i."
```

La sortie de cette commande est la suivante :

```Output
The value of 5 is 5.
```

En outre, dans une chaîne entre guillemets doubles, les expressions sont évaluées et le résultat est inséré dans la chaîne. Par exemple :

```powershell
"The value of $(2+3) is 5."
```

La sortie de cette commande est la suivante :

```Output
The value of 5 is 5.
```

Une chaîne placée entre guillemets simples est une chaîne _textuelle_ . La chaîne est passée à la commande exactement telle que vous la tapez. Aucune substitution n’est effectuée.
Par exemple :

```powershell
$i = 5
'The value of $i is $i.'
```

La sortie de cette commande est la suivante :

```Output
The value $i is $i.
```

De même, les expressions des chaînes entre guillemets simples ne sont pas évaluées. Ils sont interprétés comme des littéraux. Par exemple :

```powershell
'The value of $(2+3) is 5.'
```

La sortie de cette commande est la suivante :

```Output
The value of $(2+3) is 5.
```

Pour empêcher la substitution d’une valeur de variable dans une chaîne entre guillemets doubles, utilisez le caractère de soulignement ( `` ` `` ) (ASCII 96), qui est le caractère d’échappement PowerShell.

Dans l’exemple suivant, le caractère d’impulsion qui précède la première `$i` variable empêche PowerShell de remplacer le nom de la variable par sa valeur.
Par exemple :

```powershell
$i = 5
"The value of `$i is $i."
```

La sortie de cette commande est la suivante :

```Output
The value $i is 5.
```

Pour faire apparaître les guillemets doubles dans une chaîne, placez la totalité de la chaîne entre guillemets simples. Par exemple :

```powershell
'As they say, "live and learn."'
```

La sortie de cette commande est la suivante :

```Output
As they say, "live and learn."
```

Vous pouvez également placer une chaîne entre guillemets simples dans une chaîne entre guillemets. Par exemple :

```powershell
"As they say, 'live and learn.'"
```

La sortie de cette commande est la suivante :

```Output
As they say, 'live and learn.'
```

Ou, doublez les guillemets autour d’une expression entre guillemets doubles. Par exemple :

```powershell
"As they say, ""live and learn."""
```

La sortie de cette commande est la suivante :

```Output
As they say, "live and learn."
```

Pour inclure un guillemet simple dans une chaîne entre guillemets simples, utilisez un deuxième guillemet simple consécutif. Par exemple :

```powershell
'don''t'
```

La sortie de cette commande est la suivante :

```Output
don't
```

Pour forcer PowerShell à interpréter littéralement un guillemet double, utilisez un caractère de soulignement. Cela empêche PowerShell d’interpréter le guillemet comme un délimiteur de chaîne. Par exemple :

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

Étant donné que le contenu des chaînes entre guillemets simples est interprété littéralement, vous êtes considéré comme un caractère littéral et affiché dans la sortie.

## <a name="here-strings"></a>Ici-chaînes

Les règles de quotation pour les chaînes ici sont légèrement différentes.

Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement. Une chaîne ici peut s’étendre sur plusieurs lignes. Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes même si elles ne sont pas placées entre guillemets.

À l’instar des chaînes régulières, les variables sont remplacées par leurs valeurs dans des chaînes here à deux guillemets. Dans les chaînes ici à guillemets simples, les variables ne sont pas remplacées par leurs valeurs.

Vous pouvez utiliser des chaînes here pour tout texte, mais elles sont particulièrement utiles pour les genres de texte suivants :

- Texte qui contient des guillemets littéraux
- Plusieurs lignes de texte, telles que le texte dans un fichier HTML ou XML
- Texte d’aide d’un script ou d’un document de fonction

Une chaîne « here » peut avoir l’un des formats suivants, où `<Enter>` représente le caractère masqué de saut de ligne ou de saut de ligne qui est ajouté lorsque vous appuyez sur la touche <kbd>entrée</kbd> .

Guillemets doubles :

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

Guillemets simples :

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

Dans les deux formats, le guillemet fermant doit être le premier caractère de la ligne.

Une chaîne ici contient tout le texte entre les deux caractères masqués. Dans la chaîne here, tous les guillemets sont interprétés littéralement. Par exemple :

```powershell
@"
For help, type "get-help"
"@
```

La sortie de cette commande est la suivante :

```Output
For help, type "get-help"
```

L’utilisation d’une chaîne « here » peut simplifier l’utilisation d’une chaîne dans une commande. Par exemple :

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

La sortie de cette commande est la suivante :

```Output
Use a quotation mark (') to begin a string.
```

Dans les chaînes ici à guillemets simples, les variables sont interprétées littéralement et reproduites exactement. Par exemple :

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

La sortie de cette commande est la suivante :

```Output
The $profile variable contains the path
of your PowerShell profile.
```

Dans les chaînes à deux guillemets (), les variables sont remplacées par leurs valeurs. Par exemple :

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

La sortie de cette commande est la suivante :

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

Ici-les chaînes sont généralement utilisées pour assigner plusieurs lignes à une variable. Par exemple, le texte suivant-String affecte une page XML à la variable $page.

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

Ici-les chaînes sont également un format pratique pour l’entrée de l’applet de commande `ConvertFrom-StringData` , qui convertit les chaînes ici en tables de hachage.
Pour plus d’informations, consultez `ConvertFrom-StringData`.

## <a name="see-also"></a>Voir aussi

[about_Special_Characters](about_Special_Characters.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

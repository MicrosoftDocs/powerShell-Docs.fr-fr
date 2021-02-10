---
description: Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.
Locale: en-US
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: b21ec1eb5ed0da52cf5eff01eaf3c220d117cf55
ms.sourcegitcommit: 364c3fe46b2069b810107d840be59fe519ea7b4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100714"
---
# <a name="about-special-characters"></a>À propos des caractères spéciaux

## <a name="short-description"></a>Description courte

Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.

## <a name="long-description"></a>Description longue

PowerShell prend en charge un ensemble de séquences de caractères spéciaux utilisés pour représenter des caractères qui ne font pas partie du jeu de caractères standard. Les séquences sont communément appelées _séquences d’échappement_.

Les séquences d’échappement commencent par le caractère « accent grave » (ASCII 96) et respectent la casse. Le caractère d’échappement est également appelé _caractère d’échappement_.

Les séquences d’échappement sont interprétées uniquement lorsqu’elles sont contenues dans des chaînes entre guillemets ( `"` ).

PowerShell reconnaît ces séquences d’échappement :

|  Séquence   |       Description       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | Alerte                   |
| `` `b ``    | Retour arrière               |
| `` `e ``    | Caractère d'échappement                  |
| `` `f ``    | Saut de page               |
| `` `n ``    | Nouvelle ligne                |
| `` `r ``    | Retour chariot         |
| `` `t ``    | Tabulation horizontale          |
| `` `u{x} `` | Séquence d’échappement Unicode |
| `` `v ``    | Tabulation verticale            |

PowerShell a également un jeton spécial pour marquer l’endroit où vous souhaitez que l’analyse s’arrête. Tous les caractères qui suivent ce jeton sont utilisés comme valeurs littérales qui ne sont pas interprétées.

Jeton d’analyse spécial :

| Séquence |            Description             |
| -------- | ---------------------------------- |
| `--%`    | Arrêter l’analyse de tout ce qui suit |

## <a name="null-0"></a>Null (' 0)

Le caractère null ( `` `0 `` ) apparaît comme un espace vide dans la sortie PowerShell.
Cette fonctionnalité vous permet d’utiliser PowerShell pour lire et traiter des fichiers texte qui utilisent des caractères null, tels que la terminaison de chaîne ou les indicateurs de fin d’enregistrement. Le caractère spécial NULL n’est pas équivalent à la `$null` variable, qui stocke une valeur **null** .

## <a name="alert-a"></a>Alerte ('a')

Le caractère alerte ( `` `a `` ) envoie un signal sonore au haut-parleur de l’ordinateur.
Vous pouvez utiliser ce caractère pour avertir l’utilisateur d’une action imminente. L’exemple suivant envoie deux signaux sonores au haut-parleur de l’ordinateur local.

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>Retour arrière ('b)

Le `` `b `` caractère retour arrière () déplace le curseur d’un caractère vers l’arrière, mais il ne supprime aucun caractère.

L’exemple écrit le mot **sauvegarde** , puis replace le curseur à deux reprises.
Ensuite, à la nouvelle position, écrit un espace suivi du mot **out**.

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a>Escape ('e)

Le `` `e `` caractère d’échappement () est le plus souvent utilisé pour spécifier une séquence de terminaux virtuels (séquence d’échappement ANSI) qui modifie la couleur du texte et d’autres attributs de texte tels que le gras et le soulignement. Ces séquences peuvent également être utilisées pour le positionnement et le défilement des curseurs. L’hôte PowerShell doit prendre en charge les séquences de terminaux virtuels. Vous pouvez vérifier la valeur booléenne de `$Host.UI.SupportsVirtualTerminal` pour déterminer si ces séquences ANSI sont prises en charge.

Pour plus d’informations sur les séquences d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).

L’exemple suivant génère le texte avec une couleur de premier plan verte.

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a>Flux de formulaire ('f')

Le caractère de saut de `` `f `` page () est une instruction d’impression qui éjecte la page actuelle et poursuit l’impression sur la page suivante. Le caractère de saut de formulaire affecte uniquement les documents imprimés. Elle n’affecte pas la sortie écran.

## <a name="new-line-n"></a>Nouvelle ligne ('n)

Le caractère de nouvelle ligne ( `` `n `` ) insère un saut de ligne immédiatement après le caractère.

Cet exemple montre comment utiliser le caractère de nouvelle ligne pour créer des sauts de ligne dans une `Write-Host` commande.

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>Retour chariot ('r)

Le caractère retour chariot ( `` `r `` ) déplace le curseur de sortie au début de la ligne active et poursuit l’écriture. Tous les caractères de la ligne active sont remplacés.

Dans cet exemple, le texte avant le retour chariot est remplacé.

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

Notez que le texte avant le `` `r `` caractère n’est pas supprimé, il est remplacé.

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>Tabulation horizontale (t)

Le caractère de tabulation horizontale ( `` `t `` ) passe au taquet de tabulation suivant et poursuit l’écriture à ce stade. Par défaut, la console PowerShell a un taquet de tabulation à chaque huitième espace.

Cet exemple insère deux onglets entre chaque colonne.

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a>Caractère Unicode ('u {x}]

La séquence d’échappement Unicode ( `` `u{x} `` ) vous permet de spécifier n’importe quel caractère Unicode à l’aide de la représentation hexadécimale de son point de code. Cela comprend les caractères Unicode au-dessus du plan multilingue de base (>), y `0xFFFF` compris les caractères Emoji tels que le caractère **pouce** ( `` `u{1F44D} `` ). La séquence d’échappement Unicode requiert au moins un chiffre hexadécimal et prend en charge jusqu’à six chiffres hexadécimaux. La valeur hexadécimale maximale pour la séquence est `10FFFF` .

Cet exemple génère le symbole de **flèche vers le bas** (&#x2195;).

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a>Tabulation verticale ('v)

Le caractère de tabulation verticale ( `` `v `` ) passe au taquet de tabulation vertical suivant et écrit la sortie restante à ce stade. Le rendu de la tabulation verticale est dépendant du périphérique et du terminal.

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

Les exemples suivants illustrent la sortie rendue de l’onglet vertical dans certains environnements courants.

L’application hôte de la console Windows interprète ( `` `v `` ) comme un caractère spécial sans ajout d’espacement supplémentaire.

```Output
There is a vertical tab♂between the words.
```

Le [terminal Windows](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) affiche le caractère de tabulation verticale sous la forme d’un retour chariot et d’un saut de ligne. Le reste de la sortie est imprimé au début de la ligne suivante.

```Output
There is a vertical tab
between the words.
```

Sur les imprimantes ou dans une console Unix, le caractère de tabulation verticale passe à la ligne suivante et écrit la sortie restante à ce stade.

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>Jeton d’analyse d’arrêt (--%)

Le jeton Stop-Analysing ( `--%` ) empêche PowerShell d’interpréter les chaînes comme des commandes et des expressions PowerShell. Cela permet de transmettre ces chaînes à d’autres programmes pour les interpréter.

Placez le jeton d’analyse d’arrêt après le nom du programme et avant les arguments du programme qui peuvent provoquer des erreurs.

Dans cet exemple, la `Icacls` commande utilise le jeton d’analyse d’arrêt.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell envoie la chaîne suivante à `Icacls` .

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Voici un autre exemple. La fonction **showArgs** génère les valeurs qui lui sont passées. Dans cet exemple, nous passons `$HOME` à deux fois la variable nommée à la fonction.

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

Dans la sortie, vous pouvez voir que, pour le premier paramètre, la variable `$HOME` est interprétée par PowerShell afin que la valeur de la variable soit transmise à la fonction. La deuxième utilisation de `$HOME` vient après le jeton d’analyse d’arrêt, donc la chaîne « $Home » est transmise à la fonction sans interprétation.

```Output
$args = C:\Users\username|--%|$HOME
```

Pour plus d’informations sur le jeton d’analyse d’arrêt, consultez [about_Parsing](about_Parsing.md).

## <a name="see-also"></a>Voir également

[about_Quoting_Rules](about_Quoting_Rules.md)


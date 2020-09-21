---
title: Tout ce que vous avez toujours voulu savoir sur la substitution de variable dans les chaînes
description: Il existe de nombreuses façons d’utiliser des variables dans des chaînes pour créer du texte mis en forme.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301316"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>Tout ce que vous avez toujours voulu savoir sur la substitution de variable dans les chaînes

Il existe de nombreuses façons d’utiliser des variables dans les chaînes. J’appelle ceci « substitution de variable », mais je fais référence à chaque fois que vous voulez mettre en forme une chaîne pour y inclure des valeurs provenant de variables. C’est quelque chose que j’explique souvent aux personnes qui débutent dans l’écriture de scripts.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous. Consultez son blog sur [PowerShellExplained.com][].

## <a name="concatenation"></a>Concaténation

La première catégorie de méthodes est celle des méthodes de concaténation. En gros, elles prennent plusieurs chaînes et les assemblent. La concaténation est utilisée depuis longtemps pour construire des chaînes mises en forme.

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

La concaténation est une bonne solution quand il n’y a que quelques valeurs à ajouter. Cela peut cependant devenir rapidement compliqué.

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

Ce simple exemple est déjà plus difficile à lire.

## <a name="variable-substitution"></a>Substitution de variables

PowerShell a une autre option plus facile. Vous pouvez spécifier vos variables directement dans les chaînes.

```powershell
$message = "Hello, $first $last."
```

Le type de guillemets que vous utilisez autour des chaînes fait la différence. Une chaîne entre guillemets doubles permet la substitution, mais pas une chaîne entre guillemets simples. Selon les moments, vous avez besoin de l’une ou de l’autre, et vous avez donc un choix à faire.

## <a name="command-substitution"></a>Substitution dans les commandes

Les choses deviennent un peu plus compliquées quand vous voulez obtenir les valeurs de propriétés dans une chaîne. C’est là que beaucoup de débutants ont des difficultés. Laissez-moi d’abord vous montrer ce qu’ils pensent devoir fonctionner (et à première vue, ce devrait bien être le cas).

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

Vous vous attendez à obtenir `CreationTime` de `$directory`, mais au lieu de cela, vous obtenez `Time: c:\windows.CreationTime` comme valeur. La raison en est que ce type de substitution voit seulement la variable de base. Elle considère le point comme faisant partie de la chaîne : elle arrête donc la résolution de la valeur à cet endroit.

Il arrive que cet objet donne une chaîne comme valeur par défaut quand il est placé dans une chaîne.
Certains objets vous donnent à la place le nom du type, comme `System.Collections.Hashtable`. Juste quelque chose à rechercher.

PowerShell vous permet de demander l’exécution de commandes à l’intérieur de la chaîne avec une syntaxe spéciale. Ce qui nous permet d’obtenir les propriétés de ces objets et d’exécuter n’importe quelle autre commande pour obtenir une valeur.

```powershell
$message = "Time: $($directory.CreationTime)"
```

Cela fonctionne bien pour certaines situations, mais ce peut-être aussi compliqué que la concaténation si vous avez seulement quelques variables.

### <a name="command-execution"></a>Exécution de commande

Vous pouvez exécuter des commandes à l’intérieure d’une chaîne. Même si j’ai cette option, je ne l’aime pas. Cela devient rapidement compliqué et difficile à déboguer. Je peux exécuter la commande et enregistrer dans une variable ou utiliser une chaîne de format.

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>Chaîne de format

.NET a un moyen de mettre en forme les chaînes que je trouve facile à utiliser. Laissez-moi d’abord vous montrer la méthode statique avant de vous montrer le raccourci PowerShell pour faire la même chose.

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

Ce qui se passe ici est que la chaîne est analysée à la recherche des jetons `{0}` et `{1}`, puis elle utilise ce numéro pour choisir parmi les valeurs fournies. Si vous voulez répéter une valeur à un certain endroit dans la chaîne, vous pouvez réutiliser le numéro de cette valeur.

Plus la chaîne est complexe, plus cette approche est pratique.

### <a name="format-values-as-arrays"></a>Mettre en forme des valeurs en tant que tableaux

Si votre ligne de mise en forme est trop longue, vous pouvez d’abord placer vos valeurs dans un tableau.

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

Ce n’est pas du splatting, car je passe en entrée l’ensemble du tableau, mais l’idée est similaire.

## <a name="advanced-formatting"></a>Mise en forme avancée

Je les ai intentionnellement appelées comme provenant de .NET, car de nombreuses options de mise en forme y sont déjà bien [documentées][]. Il existe plusieurs moyens intégrés de mettre en forme différents types de données.

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

Je ne vais pas les détailler, mais je voulais simplement vous dire qu’il s’agit d’un moteur de mise en forme très puissant si vous en avez besoin.

## <a name="joining-strings"></a>Jonction de chaînes

Parfois, vous voulez concaténer une liste de valeurs. Il existe un opérateur `-join` qui peut le faire pour vous. Il vous permet même de spécifier un caractère à joindre entre les chaînes.

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

Si vous utilisez `-join` avec des chaînes mais sans séparateur, vous devez spécifier une chaîne vide `''`.
Mais si c’est tout ce dont vous avez besoin, il y a une option plus rapide.

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

Il est intéressant de noter que vous pouvez aussi appliquer `-split` pour décomposer des chaînes.

## <a name="join-path"></a>Join-Path

Bien que souvent négligée, il s’agit d’une applet de commande intéressante pour créer un chemin de fichier.

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

L’avantage est qu’elle traite correctement les barres obliques inverses quand elle place les valeurs ensemble. C’est particulièrement important si vous prenez des valeurs provenant d’utilisateurs ou de fichiers de configuration.

Cela fonctionne également bien avec `Split-Path` et `Test-Path`. J’en parle aussi dans mon billet sur [la lecture et l’enregistrement dans des fichiers][].

## <a name="strings-are-arrays"></a>Les chaînes sont des tableaux

Je dois parler ici de l’ajout de chaînes avant de continuer. Rappelez-vous qu’une chaîne est simplement un tableau de caractères. Quand vous ajoutez plusieurs chaînes ensemble, un nouveau tableau est créé chaque fois.

Regardez cet exemple :

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

Il semble très simple, mais ce que vous ne voyez pas, c’est qu’à chaque fois qu’une chaîne est ajoutée à `$message`, une chaîne entièrement nouvelle est créée. La mémoire est allouée, les données sont copiées et les anciennes sont supprimées.
Ce n’est pas problématique quand ce n’est fait que quelques fois, mais une boucle comme celle-ci ferait apparaître le problème.

### <a name="stringbuilder"></a>StringBuilder

StringBuilder est également très utilisée pour créer de grandes chaînes à partir d’un grand nombre de chaînes plus petites. La raison en est qu’elle collecte simplement toutes les chaînes que vous y ajoutez et les concatène seulement à la fin quand vous récupérez la valeur.

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

À nouveau, c’est quelque chose qui me vient de .NET. Je ne l’utilise plus très souvent, mais il est bon de savoir qu’elle existe.

## <a name="delineation-with-braces"></a>Délimitation avec des crochets

Ils sont utilisés pour la concaténation de suffixes dans la chaîne. Parfois, votre variable n’a pas de limite de mot claire.

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

Merci à [/u/real_parbold][] pour ceci.

Voici une alternative à cette approche :

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

J’utilise personnellement pour cela la chaîne de mise en forme, mais il est néanmoins bon de la connaître au cas où vous la rencontrez.

## <a name="find-and-replace-tokens"></a>Rechercher et remplacer des jetons

Bien que la plupart de ces fonctionnalités limitent votre besoin de déployer votre propre solution, il peut arriver que vous ayez de grands fichiers modèles où vous voulez remplacer des chaînes.

Supposons que vous ayez extrait un modèle à partir d’un fichier contenant beaucoup de texte.

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

Vous pouvez avoir beaucoup de jetons à remplacer. L’astuce consiste à utiliser un jeton très spécifique facile à trouver et à remplacer. J’ai tendance à utiliser un caractère spécial aux deux extrémités pour le distinguer plus facilement.

J’ai récemment trouvé une nouvelle façon d’approcher ce problème. J’ai décidé de conserver cette section ici, car il s’agit d’un modèle couramment utilisé.

### <a name="replace-multiple-tokens"></a>Remplacer plusieurs jetons

Quand j’ai une liste de jetons que je dois remplacer, j’adopte une approche plus générique. Je les place dans une table de hachage et j’itère dessus pour effectuer le remplacement.

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

Ces jetons peuvent être chargés si nécessaire depuis un fichier JSON ou CSV.

### <a name="executioncontext-expandstring"></a>ExecutionContext ExpandString

Il existe un moyen intelligent de définir une chaîne de substitution avec des guillemets simples et de développer les variables plus tard . Regardez cet exemple :

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

L’appel à `.InvokeCommand.ExpandString` sur le contexte d’exécution actif utilise les variables dans l’étendue actuelle pour la substitution. L’élément clé est ici que `$message` peut être défini très tôt avant même que les variables n’existent.

Si nous développons cela juste un peu, nous pouvons effectuer cette substitution de façon répétée avec différentes valeurs.

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

Pour continuer sur cette idée, vous pourriez importer un grand modèle d’e-mail à partir d’un fichier texte pour faire cela. Je dois remercier [Mark Kraus][] pour cette [suggestion][].

## <a name="whatever-works-the-best-for-you"></a>Ce qui fonctionne le mieux pour vous

Je suis partisan de l’approche des chaînes de mise en forme. Je fais toujours ainsi avec les chaînes les plus compliquées ou s’il y a plusieurs variables. Sur quelque chose de très court, je peux utiliser l’une de ces méthodes.

## <a name="anything-else"></a>Autre chose ?

J’ai abordé beaucoup de choses dans ce billet. J’espère que vous avez pu apprendre quelque chose de nouveau.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[la lecture et l’enregistrement dans des fichiers]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[documentées]: /dotnet/api/system.string.format#overloads

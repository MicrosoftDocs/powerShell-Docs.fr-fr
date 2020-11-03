---
description: Décrit les opérateurs pris en charge par PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 9668e635b17f8cbe9f6639e8a13b95d4b9387fbb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208941"
---
# <a name="about-operators"></a>À propos des opérateurs

## <a name="short-description"></a>Description courte
Décrit les opérateurs pris en charge par PowerShell.

## <a name="long-description"></a>Description longue

Un opérateur est un élément de langage que vous pouvez utiliser dans une commande ou une expression.
PowerShell prend en charge plusieurs types d’opérateurs pour vous aider à manipuler des valeurs.

### <a name="arithmetic-operators"></a>Opérateurs arithmétiques

Utilisez les opérateurs arithmétiques ( `+` , `-` ,, `*` `/` , `%` ) pour calculer des valeurs dans une commande ou une expression. À l’aide de ces opérateurs, vous pouvez ajouter, soustraire, multiplier ou diviser des valeurs, et calculer le reste (modulo) d’une opération de division.

L’opérateur d’addition concatène les éléments. L’opérateur de multiplication retourne le nombre spécifié de copies de chaque élément. Vous pouvez utiliser des opérateurs arithmétiques sur tout type .net qui les implémente, tels que les tableaux suivants : `Int` ,,,, `String` `DateTime` `Hashtable` et.

Les opérateurs au niveau du bit ( `-band` , `-bor` ,, `-bxor` `-bnot` , `-shl` , `-shr` ) manipulent les modèles binaires dans les valeurs.

Pour plus d’informations, consultez [about_Arithmetic_Operators](about_Arithmetic_Operators.md).

### <a name="assignment-operators"></a>Opérateurs d'assignation

Utilisez les opérateurs d’assignation ( `=` , `+=` , `-=` , `*=` , `/=` , `%=` ) pour assigner, modifier ou ajouter des valeurs à des variables. Vous pouvez combiner des opérateurs arithmétiques avec l’assignation pour assigner le résultat de l’opération arithmétique à une variable.

Pour plus d’informations, consultez [about_Assignment_Operators](about_Assignment_Operators.md).

### <a name="comparison-operators"></a>Opérateurs de comparaison

Utilisez des opérateurs de comparaison ( `-eq` , `-ne` , `-gt` , `-lt` , `-le` , `-ge` ) pour comparer des valeurs et des conditions de test. Par exemple, vous pouvez comparer deux valeurs de chaîne pour déterminer si elles sont égales.

Les opérateurs de comparaison incluent également des opérateurs qui recherchent ou remplacent des modèles dans du texte. Les `-match` opérateurs (, `-notmatch` , `-replace` ) utilisent des expressions régulières, et ( `-like` , `-notlike` ) utilisent des caractères génériques `*` .

Les opérateurs de comparaison de relation contenant-contenu déterminent si une valeur de test apparaît dans un jeu de référence ( `-in` , `-notin` , `-contains` , `-notcontains` ).

Les opérateurs de comparaison `-is` de type (, `-isnot` ) déterminent si un objet est d’un type donné.

Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md).

### <a name="logical-operators"></a>Opérateurs logiques

Utilisez des opérateurs logiques ( `-and` , `-or` ,, `-xor` `-not` , `!` ) pour connecter des instructions conditionnelles à un seul conditionnel complexe. Par exemple, vous pouvez utiliser un `-and` opérateur logique pour créer un filtre d’objets avec deux conditions différentes.

Pour plus d’informations, consultez [about_Logical_Operators](about_logical_operators.md).

### <a name="redirection-operators"></a>Opérateurs de redirection

Utilisez les opérateurs de redirection ( `>` , `>>` ,, `2>` `2>>` et `2>&1` ) pour envoyer la sortie d’une commande ou d’une expression à un fichier texte. Les opérateurs de redirection fonctionnent comme l' `Out-File` applet de commande (sans paramètres), mais ils vous permettent également de rediriger la sortie d’erreur vers les fichiers spécifiés. Vous pouvez également utiliser l' `Tee-Object` applet de commande pour rediriger la sortie.

Pour plus d’informations, consultez [about_Redirection](about_Redirection.md)

### <a name="split-and-join-operators"></a>Opérateurs Split et Join

Les `-split` `-join` opérateurs et divisent et combinent des sous-chaînes. L' `-split` opérateur fractionne une chaîne en sous-chaînes. L' `-join` opérateur concatène plusieurs chaînes en une seule chaîne.

Pour plus d’informations, consultez [about_Split](about_Split.md) et [about_Join](about_Join.md).

### <a name="type-operators"></a>Opérateurs de type

Utilisez les opérateurs de type ( `-is` , `-isnot` , `-as` ) pour rechercher ou modifier le type de .NET Framework d’un objet.

Pour plus d’informations, consultez [about_Type_Operators](about_Type_Operators.md).

### <a name="unary-operators"></a>Opérateurs unaires

Utilisez des opérateurs unaires pour incrémenter ou décrémenter des variables ou des propriétés d’objet et pour définir des entiers avec des nombres positifs ou négatifs. Par exemple, pour incrémenter la variable `$a` de `9` à `10` , vous tapez `$a++` .

### <a name="special-operators"></a>Opérateurs spéciaux

Les opérateurs spéciaux ont des cas d’usage spécifiques qui ne rentrent dans aucun autre groupe d’opérateurs. Par exemple, les opérateurs spéciaux vous permettent d’exécuter des commandes, de modifier le type de données d’une valeur ou de récupérer des éléments d’un tableau.

#### <a name="grouping-operator--"></a>Opérateur de regroupement `( )`

Comme dans d’autres langages, `(...)` sert à remplacer la priorité des opérateurs dans les expressions. Par exemple : `(1 + 2) / 3`

Toutefois, dans PowerShell, il existe des comportements supplémentaires.

- `(...)` vous permet de laisser la sortie d’une _commande_ participer à une expression. Par exemple :

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- Lorsqu’il est utilisé comme premier segment d’un pipeline, l’encapsulation d’une commande ou d’une expression entre parenthèses provoque invariablement l' _énumération_ du résultat de l’expression. Si les parenthèses encapsulent une _commande_ , elles sont exécutées jusqu’à la fin avec toute la sortie _collectée en mémoire_ avant que les résultats ne soient envoyés via le pipeline.

> [!NOTE]
> Si vous encapsulez une commande entre parenthèses, la variable automatique `$?` est définie sur `$true` , même lorsque la commande placée elle-même a la valeur `$?` `$false` .
> Par exemple, `(Get-Item /Nosuch); $?` génère de façon inattendue la **valeur true**. Pour plus d’informations sur `$?` , consultez [about_Automatic_Variables](about_Automatic_Variables.md).

#### <a name="subexpression-operator--"></a>Opérateur de sous-expression `$( )`

Retourne le résultat d’une ou plusieurs instructions. Pour un résultat unique, retourne un scalaire. Pour plusieurs résultats, retourne un tableau. Utilisez cette valeur lorsque vous souhaitez utiliser une expression dans une autre expression. Par exemple, pour incorporer les résultats de la commande dans une expression de chaîne.

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Opérateur de sous-expression de tableau `@( )`

Retourne le résultat d’une ou plusieurs instructions sous la forme d’un tableau. S’il n’y a qu’un seul élément, le tableau ne possède qu’un seul membre.

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a>Opérateur d’appel `&`

Exécute une commande, un script ou un bloc de script. L’opérateur d’appel, également appelé « opérateur d’appel », vous permet d’exécuter des commandes qui sont stockées dans des variables et représentées par des chaînes ou des blocs de script. L’opérateur d’appel s’exécute dans une portée enfant. Pour plus d’informations sur les étendues, consultez [about_Scopes](about_Scopes.md).

Cet exemple stocke une commande dans une chaîne et l’exécute à l’aide de l’opérateur d’appel.

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

L’opérateur d’appel n’analyse pas les chaînes. Cela signifie que vous ne pouvez pas utiliser de paramètres de commande dans une chaîne lorsque vous utilisez l’opérateur d’appel.

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

L’applet de commande [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) peut exécuter du code qui provoque des erreurs d’analyse lors de l’utilisation de l’opérateur d’appel.

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

Vous pouvez utiliser l’opérateur d’appel pour exécuter des scripts à l’aide de leurs noms de fichiers. L’exemple ci-dessous montre un nom de fichier de script qui contient des espaces. Lorsque vous essayez d’exécuter le script, PowerShell affiche à la place le contenu de la chaîne entre guillemets contenant le nom de fichier. L’opérateur d’appel vous permet d’exécuter le contenu de la chaîne contenant le nom de fichier.

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

Pour plus d’informations sur les blocs de script, consultez [about_Script_Blocks](about_Script_Blocks.md).

#### <a name="background-operator-"></a>Opérateur d’arrière-plan `&`

Exécute le pipeline avant de l’exécuter en arrière-plan, dans un travail PowerShell. Cet opérateur agit de la même façon que l’opérateur de contrôle UNIX perluète ( `&` ), qui exécute la commande avant de l’exécuter de manière asynchrone dans subshell en tant que tâche.

Cet opérateur est fonctionnellement équivalent à `Start-Job` . L’exemple suivant illustre l’utilisation de base de l’opérateur de travail en arrière-plan.

```powershell
Get-Process -Name pwsh &
```

Cette commande est fonctionnellement équivalente à l’utilisation suivante de `Start-Job` :

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

Tout comme `Start-Job` , l' `&` opérateur d’arrière-plan retourne un `Job` objet. Cet objet peut être utilisé avec `Receive-Job` et `Remove-Job` , comme si vous aviez utilisé `Start-Job` pour démarrer le travail.

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

L' `&` opérateur d’arrière-plan est également un terminateur d’instruction, tout comme l’opérateur de contrôle UNIX perluète ( `&` ). Cela vous permet d’appeler des commandes supplémentaires après l' `&` opérateur d’arrière-plan. L’exemple suivant illustre l’appel de commandes supplémentaires après l' `&` opérateur d’arrière-plan.

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

Cela équivaut au script suivant :

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

Si vous souhaitez exécuter plusieurs commandes, chacune dans son propre processus en arrière-plan, mais sur une seule ligne, placez- `&` la simplement entre et après chacune des commandes.

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

Pour plus d’informations sur les travaux PowerShell, consultez [about_Jobs](about_Jobs.md).

#### <a name="cast-operator--"></a>Cast, opérateur `[ ]`

Convertit ou limite les objets au type spécifié. Si les objets ne peuvent pas être convertis, PowerShell génère une erreur.

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

Un cast peut également être effectué quand une variable est assignée à l’aide d’une [notation de cast](about_Variables.md).

#### <a name="comma-operator-"></a>Virgule (opérateur) `,`

En tant qu’opérateur binaire, la virgule crée un tableau ou ajoute au tableau en cours de création. En mode expression, en tant qu’opérateur unaire, la virgule crée un tableau avec un seul membre. Placez la virgule avant le membre.

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

Étant donné que `Write-Object` attend un argument, vous devez placer l’expression entre parenthèses.

#### <a name="dot-sourcing-operator-"></a>Opérateur d’approvisionnement en points `.`

Exécute un script dans l’étendue actuelle afin que toutes les fonctions, tous les alias et toutes les variables créés par le script soient ajoutés à la portée actuelle, en substituant ceux qui existent déjà. Les paramètres déclarés par le script deviennent des variables. Les paramètres pour lesquels aucune valeur n’a été donnée deviennent des variables sans valeur. Toutefois, la variable automatique `$args` est conservée.

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> L’opérateur de source de points est suivi d’un espace. Utilisez l’espace pour distinguer le point du symbole point ( `.` ) qui représente le répertoire actif.
>
> Dans l’exemple suivant, le script Sample.ps1 dans le répertoire actif est exécuté dans l’étendue actuelle.
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Format, opérateur `-f`

Met en forme des chaînes à l’aide de la méthode format des objets String. Entrez la chaîne de format sur le côté gauche de l’opérateur et les objets à mettre en forme à droite de l’opérateur.

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

Si vous devez conserver les accolades ( `{}` ) dans la chaîne mise en forme, vous pouvez les placer dans une séquence d’échappement en doublant les accolades.

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

Pour plus d’informations, consultez la méthode [String. format](/dotnet/api/system.string.format) et la [mise en forme composite](/dotnet/standard/base-types/composite-formatting).

#### <a name="index-operator--"></a>Index (opérateur) `[ ]`

Sélectionne des objets dans des collections indexées, telles que des tableaux et des tables de hachage. Les index de tableau sont de base zéro, donc le premier objet est indexé en tant que `[0]` . Pour les tableaux (uniquement), vous pouvez également utiliser des index négatifs pour obtenir les dernières valeurs. Les tables de hachage sont indexées par valeur de clé.

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a>Opérateur de pipeline `|`

Envoie (« Pipes ») la sortie de la commande qui la précède à la commande qui la suit. Lorsque la sortie comprend plusieurs objets (une « collection »), l’opérateur de pipeline envoie les objets un par un.

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a>Opérateur de plage `..`

Représente les entiers séquentiels dans un tableau d’entiers, en fonction d’une limite supérieure et inférieure.

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

Vous pouvez également créer des plages dans l’ordre inverse.

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

À compter de PowerShell 6, l’opérateur Range fonctionne avec des **caractères** et des **entiers**.

Pour créer une plage de caractères, placez les caractères de la limite entre guillemets.

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a>Opérateur d’accès aux membres `.`

Accède aux propriétés et aux méthodes d’un objet. Le nom de membre peut être une expression.

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>Opérateur de membre statique `::`

Appelle les propriétés et les méthodes statiques d’une classe .NET Framework. Pour rechercher les propriétés et les méthodes statiques d’un objet, utilisez le paramètre static de l’applet de commande `Get-Member` .  Le nom de membre peut être une expression.

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a>Voir aussi

[about_Arithmetic_Operators](about_Arithmetic_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Split](about_Split.md)

[about_Join](about_Join.md)

[about_Redirection](about_Redirection.md)

---
description: Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 2149a1dec14e4de9c6ff1021e98689ca93307cb8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206594"
---
# <a name="about-scopes"></a>À propos des étendues

## <a name="short-description"></a>Description courte
Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.

## <a name="long-description"></a>Description longue

PowerShell protège l’accès aux variables, aux alias, aux fonctions et aux lecteurs PowerShell (PSDrives) en limitant l’emplacement où ils peuvent être lus et modifiés. PowerShell utilise des règles d’étendue pour s’assurer que vous ne modifiez pas par inadvertance un élément qui ne doit pas être modifié.

Voici les règles de base de l’étendue :

- Les étendues peuvent s’imbriquer. Une étendue externe est appelée étendue parente. Toutes les étendues imbriquées sont des portées enfants de ce parent.

- Un élément est visible dans l’étendue dans laquelle il a été créé et dans toutes les portées enfants, sauf si vous le rendez explicitement privé. Vous pouvez placer des variables, des alias, des fonctions ou des lecteurs PowerShell dans une ou plusieurs étendues.

- Un élément que vous avez créé dans une étendue peut être modifié uniquement dans l’étendue dans laquelle il a été créé, sauf si vous spécifiez explicitement une autre portée.

Si vous créez un élément dans une étendue et que l’élément partage son nom avec un élément dans une étendue différente, l’élément d’origine peut être masqué sous le nouvel élément, mais il n’est pas substitué ou modifié.

## <a name="powershell-scopes"></a>Étendues PowerShell

PowerShell prend en charge les étendues suivantes :

- Global : étendue en vigueur au démarrage de PowerShell. Les variables et les fonctions qui sont présentes au démarrage de PowerShell ont été créées dans la portée globale, telles que les variables automatiques et les variables de préférence. Les variables, les alias et les fonctions de vos profils PowerShell sont également créés dans l’étendue globale.

- Local : étendue actuelle. La portée locale peut être la portée globale ou toute autre étendue.

- Script : étendue créée pendant l’exécution d’un fichier de script. Seules les commandes du script s’exécutent dans l’étendue du script. Pour les commandes dans un script, la portée de script est l’étendue locale.

> [!NOTE]
> **Private** n’est pas une étendue. Il s’agit d’une [option](#private-option) qui modifie la visibilité d’un élément en dehors de la portée dans laquelle l’élément est défini.

## <a name="parent-and-child-scopes"></a>Étendues parent et enfant

Vous pouvez créer une nouvelle étendue en exécutant un script ou une fonction, en créant une session ou en démarrant une nouvelle instance de PowerShell. Lorsque vous créez une étendue, le résultat est une étendue parente (étendue d’origine) et une étendue enfant (l’étendue que vous avez créée).

Dans PowerShell, toutes les étendues sont des étendues enfants de l’étendue globale, mais vous pouvez créer de nombreuses étendues et de nombreuses étendues récursives.

Sauf si vous rendez explicitement les éléments privés, les éléments de l’étendue parente sont disponibles pour l’étendue enfant. Toutefois, les éléments que vous créez et modifiez dans l’étendue enfant n’affectent pas l’étendue parente, sauf si vous spécifiez explicitement l’étendue lors de la création des éléments.

## <a name="inheritance"></a>Héritage

Une étendue enfant n’hérite pas des variables, des alias et des fonctions de l’étendue parente. À moins qu’un élément ne soit privé, l’étendue enfant peut afficher les éléments dans l’étendue parente. De plus, il peut modifier les éléments en spécifiant explicitement l’étendue parent, mais les éléments ne font pas partie de l’étendue enfant.

Toutefois, une étendue enfant est créée avec un ensemble d’éléments. En règle générale, il comprend tous les alias qui ont l’option **options AllScope** . Cette option est décrite plus loin dans cet article. Elle comprend toutes les variables qui ont l’option **options AllScope** , ainsi que certaines variables automatiques.

Pour rechercher les éléments dans une étendue particulière, utilisez le paramètre scope de `Get-Variable` ou `Get-Alias` .

Par exemple, pour obtenir toutes les variables dans la portée locale, tapez :

```powershell
Get-Variable -Scope local
```

Pour récupérer toutes les variables dans la portée globale, tapez :

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>Modificateurs d’étendue

Une variable, un alias ou un nom de fonction peut inclure l’un des modificateurs d’étendue facultatifs suivants :

- `global:` : Spécifie que le nom existe dans la portée **globale** .
- `local:` : Spécifie que le nom existe dans l’étendue **locale** . La portée actuelle est toujours l’étendue **locale** .
- `private:` : Spécifie que le nom est **privé** et visible uniquement pour l’étendue actuelle.
- `script:` : Spécifie que le nom existe dans l’étendue du **script** .
  La portée du **script** est l’étendue du fichier de script ancêtre le plus proche ou **globale** s’il n’existe pas de fichier de script ancêtre le plus proche.
- `using:` -Utilisé pour accéder aux variables définies dans une autre portée lors de l’exécution de scripts via des applets de commande telles que `Start-Job` et `Invoke-Command` .
- `workflow:` : Spécifie que le nom existe dans un flux de travail. Remarque : les flux de travail ne sont pas pris en charge dans PowerShell Core.
- `<variable-namespace>` -Modificateur créé par un fournisseur de PowerShell PSDrive.
  Par exemple :

  |  Espace de noms  |                    Description                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | Alias définis dans l’étendue actuelle               |
  | `Env:`      | Variables d’environnement définies dans la portée actuelle |
  | `Function:` | Fonctions définies dans l’étendue actuelle             |
  | `Variable:` | Variables définies dans la portée actuelle             |

L’étendue par défaut des scripts est l’étendue du script. L’étendue par défaut des fonctions et des alias est l’étendue locale, même si elles sont définies dans un script.

### <a name="using-scope-modifiers"></a>Utilisation de modificateurs d’étendue

Pour spécifier l’étendue d’une nouvelle variable, d’un alias ou d’une fonction, utilisez un modificateur d’étendue.

La syntaxe d’un modificateur de portée dans une variable est la suivante :

```
$[<scope-modifier>:]<name> = <value>
```

La syntaxe d’un modificateur de portée dans une fonction est la suivante :

```
function [<scope-modifier>:]<name> {<function-body>}
```

La commande suivante, qui n’utilise pas de modificateur de portée, crée une variable dans l’étendue actuelle ou **locale** :

```powershell
$a = "one"
```

Pour créer la même variable dans la portée **globale** , utilisez le `global:` modificateur de portée :

```powershell
$global:a = "one"
```

Pour créer la même variable dans la portée de **script** , utilisez le `script:` modificateur de portée :

```powershell
$script:a = "one"
```

Vous pouvez également utiliser un modificateur d’étendue avec des fonctions. La définition de fonction suivante crée une fonction dans la portée **globale** :

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

Vous pouvez également utiliser des modificateurs de portée pour faire référence à une variable dans une étendue différente.
La commande suivante fait référence à la `$test` variable, d’abord dans l’étendue locale, puis dans la portée globale :

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>`Using:`Modificateur de portée

L’utilisation de est un modificateur d’étendue spécial qui identifie une variable locale dans une commande à distance. Sans modificateur, PowerShell s’attend à ce que les variables des commandes distantes soient définies dans la session à distance.

Le `Using` modificateur de portée est introduit dans PowerShell 3,0.

Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder. Le `Using` modificateur de portée est pris en charge dans les contextes suivants :

- Exécuter des commandes à distance, démarré avec `Invoke-Command` à l’aide des paramètres **ComputerName** , **hostname** , **SSHConnection** ou **session** (session à distance)
- Travaux en arrière-plan, démarrés avec `Start-Job` (session hors processus)
- Travaux de thread, démarrés via `Start-ThreadJob` ou `ForEach-Object -Parallel` (session de threads distincte)

Selon le contexte, les valeurs des variables incorporées sont soit des copies indépendantes des données dans la portée de l’appelant, soit des références à celles-ci. Dans les sessions à distance et hors processus, il s’agit toujours de copies indépendantes.

Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).

Dans les sessions de thread, elles sont passées par référence. Cela signifie qu’il est possible de modifier les variables d’étendue d’appel dans un thread différent. La modification en toute sécurité des variables requiert la synchronisation des threads.

Pour plus d’informations, consultez les pages suivantes :

- [Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
- [ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a>Sérialisation de valeurs de variables

Les commandes exécutées à distance et les travaux en arrière-plan s’exécutent hors processus.
Les sessions hors processus utilisent la sérialisation et la désérialisation basées sur XML pour rendre les valeurs des variables disponibles dans les limites du processus. Le processus de sérialisation convertit des objets en **PSObject** qui contient les propriétés des objets d’origine, mais pas ses méthodes.

Pour un ensemble limité de types, la désérialisation réalimente les objets dans le type d’origine. L’objet réalimenté est une copie de l’instance d’objet d’origine.
Il a les propriétés et les méthodes de type. Pour les types simples, tels que **System. version** , la copie est exacte. Pour les types complexes, la copie n’est pas parfaite. Par exemple, les objets de certificat réalimentés n’incluent pas la clé privée.

Les instances de tous les autres types sont des instances **PSObject** . La propriété **PSTypeNames** contient le nom du type d’origine préfixé avec **désérialisé** , par exemple, **Deserialized.SysTEM. Data. DataTable**

### <a name="the-allscope-option"></a>Option Options AllScope

Les variables et les alias ont une propriété **option** qui peut prendre la valeur **options AllScope** . Les éléments qui ont la propriété **options AllScope** deviennent partie intégrante des portées enfants que vous créez, bien qu’elles ne soient pas héritées rétroactivement par les étendues parentes.

Un élément qui a la propriété **options AllScope** est visible dans la portée enfant et fait partie de cette étendue. Les modifications apportées à l’élément dans toute portée affectent toutes les étendues dans lesquelles la variable est définie.

### <a name="managing-scope"></a>Gestion de l’étendue

Plusieurs applets de commande ont un paramètre d' **étendue** qui vous permet d’obtenir ou de définir (créer et modifier) des éléments dans une étendue particulière. Utilisez la commande suivante pour rechercher toutes les applets de commande de votre session qui ont un paramètre d' **étendue** :

```powershell
Get-Help * -Parameter scope
```

Pour rechercher les variables qui sont visibles dans une étendue particulière, utilisez le `Scope` paramètre de `Get-Variable` . Les variables visibles incluent des variables globales, des variables dans l’étendue parente et des variables dans l’étendue actuelle.

Par exemple, la commande suivante obtient les variables qui sont visibles dans l’étendue locale :

```powershell
Get-Variable -Scope local
```

Pour créer une variable dans une étendue particulière, utilisez un modificateur d’étendue ou le paramètre **scope** de `Set-Variable` . La commande suivante crée une variable dans la portée globale :

```powershell
New-Variable -Scope global -Name a -Value "One"
```

Vous pouvez également utiliser le paramètre scope des `New-Alias` applets de commande, `Set-Alias` ou `Get-Alias` pour spécifier l’étendue. La commande suivante crée un alias dans l’étendue globale :

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

Pour obtenir les fonctions dans une portée particulière, utilisez l' `Get-Item` applet de commande lorsque vous êtes dans l’étendue. L' `Get-Item` applet de commande n’a pas de paramètre d' **étendue** .

> [!NOTE]
> Pour les applets de commande qui utilisent le paramètre **scope** , vous pouvez également faire référence aux étendues par numéro. Le nombre décrit la position relative d’une étendue à une autre. La portée 0 représente l’étendue actuelle, ou locale. L’étendue 1 indique l’étendue parente immédiate. L’étendue 2 indique le parent de l’étendue parent, et ainsi de suite. Les étendues numérotées sont utiles si vous avez créé de nombreuses étendues récursives.

### <a name="using-dot-source-notation-with-scope"></a>Utilisation de la notation de source de point avec l’étendue

Les scripts et les fonctions suivent toutes les règles de portée. Vous les créez dans une étendue particulière, et elles affectent uniquement cette étendue, sauf si vous utilisez un paramètre d’applet de commande ou un modificateur de portée pour modifier cette étendue.

Toutefois, vous pouvez ajouter un script ou une fonction à l’étendue actuelle à l’aide de la notation par point source. Ensuite, lorsqu’un script s’exécute dans l’étendue actuelle, toutes les fonctions, tous les alias et toutes les variables créés par le script sont disponibles dans l’étendue actuelle.

Pour ajouter une fonction à l’étendue actuelle, tapez un point (.) et un espace avant le chemin d’accès et le nom de la fonction dans l’appel de fonction.

Par exemple, pour exécuter le script Sample.ps1 à partir du répertoire C:\Scripts dans l’étendue du script (par défaut pour les scripts), utilisez la commande suivante :

```powershell
c:\scripts\sample.ps1
```

Pour exécuter le script de Sample.ps1 dans l’étendue locale, utilisez la commande suivante :

```powershell
. c:\scripts.sample.ps1
```

Lorsque vous utilisez l’opérateur d’appel (&) pour exécuter une fonction ou un script, il n’est pas ajouté à l’étendue actuelle. L’exemple suivant utilise l’opérateur d’appel :

```powershell
& c:\scripts.sample.ps1
```

Vous pouvez en savoir plus sur l’opérateur d’appel dans [about_Operators](about_operators.md).

Les alias, fonctions ou variables créés par le script de Sample.ps1 ne sont pas disponibles dans l’étendue actuelle.

## <a name="restricting-without-scope"></a>Restriction sans étendue

Quelques concepts de PowerShell sont similaires à l’étendue ou à l’interaction avec l’étendue. Ces concepts peuvent être confondus avec l’étendue ou le comportement de l’étendue.

Les sessions, les modules et les invites imbriquées sont des environnements autonomes, mais il ne s’agit pas de portées enfants de la portée globale dans la session.

### <a name="sessions"></a>Sessions

Une session est un environnement dans lequel PowerShell s’exécute. Lorsque vous créez une session sur un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant. La connexion persistante vous permet d’utiliser la session pour plusieurs commandes associées.

Étant donné qu’une session est un environnement contenu, elle a sa propre étendue, mais une session n’est pas une étendue enfant de la session dans laquelle elle a été créée. La session commence par sa propre étendue globale. Cette étendue est indépendante de l’étendue globale de la session. Vous pouvez créer des étendues enfants dans la session. Par exemple, vous pouvez exécuter un script pour créer une étendue enfant dans une session.

### <a name="modules"></a>Modules

Vous pouvez utiliser un module PowerShell pour partager et fournir des outils PowerShell. Un module est une unité qui peut contenir des applets de commande, des scripts, des fonctions, des variables, des alias et d’autres éléments utiles. Sauf définition explicite, les éléments d’un module ne sont pas accessibles à l’extérieur du module. Par conséquent, vous pouvez ajouter le module à votre session et utiliser les éléments publics sans vous soucier que les autres éléments peuvent remplacer les applets de commande, les scripts, les fonctions et d’autres éléments de votre session.

Par défaut, les modules sont chargés dans le niveau supérieur de l' _État de session_ actuel et non dans l' _étendue_ actuelle. L’état actuel de la session peut être un état de session de module ou l’état de session global. L’ajout d’un module à une session ne modifie pas l’étendue. Si vous êtes dans la portée globale, les modules sont chargés dans l’état de session global. Toutes les exportations sont placées dans les tables globales.
Si vous chargez Module2 _à partir_ de Module1, Module2 est chargé dans l’état de session de Module1, et non dans l’état de session global. Toutes les exportations à partir de Module2 sont placées en haut de l’état de la session Module1. Si vous utilisez `Import-Module -Scope local` , les exportations sont placées dans l’objet de portée actuel plutôt que au niveau supérieur. Si vous êtes _dans un module_ et utilisez `Import-Module -Scope global` (ou `Import-Module -Global` ) pour charger un autre module, ce module et ses exportations sont chargés dans l’état de session global, et non dans l’état de session local du module. Cette fonctionnalité a été conçue pour écrire un module qui manipule des modules. Le module **WindowsCompatibility** effectue cette importation pour importer des modules de proxy dans l’état de session global.

Dans l’état de session, les modules ont leur propre étendue. Prenons le module suivant `C:\temp\mod1.psm1` :

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

Maintenant, nous créons une variable globale `$a` , lui attribuons une valeur et appelons la fonction **foo** .

```powershell
$a = "Goodbye"
foo
```

Le module déclare la variable `$a` dans la portée du module, puis la fonction **foo** génère la valeur de la variable dans les deux étendues.

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>Invites imbriquées

Les invites imbriquées n’ont pas leur propre étendue. Lorsque vous entrez une invite imbriquée, l’invite imbriquée est un sous-ensemble de l’environnement. Toutefois, vous restez dans l’étendue locale.

Les scripts ont leur propre étendue. Si vous déboguez un script et que vous atteignez un point d’arrêt dans le script, vous entrez la portée du script.

### <a name="private-option"></a>Option privée

Les alias et les variables ont une propriété **option** qui peut prendre la valeur **Private** . Les éléments qui ont l’option **Private** peuvent être affichés et modifiés dans l’étendue dans laquelle ils sont créés, mais ils ne peuvent pas être affichés ou modifiés en dehors de cette étendue.

Par exemple, si vous créez une variable qui a une option privée dans l’étendue globale, puis exécutez un script, `Get-Variable` les commandes du script n’affichent pas la variable privée. L’utilisation du modificateur de portée globale dans cette instance n’affiche pas la variable privée.

Vous pouvez utiliser le paramètre option des applets de commande,, `New-Variable` `Set-Variable` `New-Alias` et `Set-Alias` pour définir la valeur de la propriété option sur Private.

### <a name="visibility"></a>Visibilité

La propriété **Visibility** d’une variable ou d’un alias détermine si vous pouvez voir l’élément en dehors du conteneur, dans lequel il a été créé. Un conteneur peut être un module, un script ou un composant logiciel enfichable. La visibilité est conçue pour les conteneurs de la même façon que la valeur **privée** de la propriété **option** est conçue pour les étendues.

La propriété **Visibility** prend les valeurs **publiques** et **privées** . Les éléments qui ont une visibilité privée peuvent être affichés et modifiés uniquement dans le conteneur dans lequel ils ont été créés. Si le conteneur est ajouté ou importé, les éléments qui ont une visibilité privée ne peuvent pas être affichés ou modifiés.

Étant donné que la visibilité est conçue pour les conteneurs, elle fonctionne différemment dans une étendue.

- Si vous créez un élément qui a une visibilité privée dans l’étendue globale, vous ne pouvez pas afficher ou modifier l’élément dans une étendue.
- Si vous essayez d’afficher ou de modifier la valeur d’une variable qui a une visibilité privée, PowerShell retourne un message d’erreur.

Vous pouvez utiliser les `New-Variable` applets de commande et `Set-Variable` pour créer une variable qui a une visibilité privée.

## <a name="examples"></a>Exemples

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>Exemple 1 : modifier une valeur de variable uniquement dans un script

La commande suivante modifie la valeur de la `$ConfirmPreference` variable dans un script. La modification n’affecte pas la portée globale.

Tout d’abord, pour afficher la valeur de la `$ConfirmPreference` variable dans l’étendue locale, utilisez la commande suivante :

```
PS>  $ConfirmPreference
High
```

Créez un script de Scope.ps1 qui contient les commandes suivantes :

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

Exécutez le script. Le script modifie la valeur de la `$ConfirmPreference` variable, puis indique sa valeur dans la portée du script. La sortie doit ressembler à la sortie suivante :

```output
The value of $ConfirmPreference is Low.
```

Ensuite, testez la valeur actuelle de la `$ConfirmPreference` variable dans la portée actuelle.

```
PS>  $ConfirmPreference
High
```

Cet exemple montre que les modifications apportées à la valeur d’une variable dans la portée du script n’affectent pas la valeur de la variable dans l’étendue parente.

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>Exemple 2 : afficher une valeur de variable dans différentes portées

Vous pouvez utiliser les modificateurs d’étendue pour afficher la valeur d’une variable dans la portée locale et dans une étendue parente.

Tout d’abord, définissez une `$test` variable dans l’étendue globale.

```powershell
$test = "Global"
```

Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable. Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.

Dans Sample.ps1 :

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

Lorsque vous exécutez Sample.ps1, la sortie doit ressembler à la sortie suivante :

```output
The local value of $test is Local.
The global value of $test is Global.
```

Une fois le script terminé, seule la valeur globale de `$test` est définie dans la session.

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>Exemple 3 : modifier la valeur d’une variable dans une étendue parente

Sauf si vous protégez un élément à l’aide de l’option Private ou d’une autre méthode, vous pouvez afficher et modifier la valeur d’une variable dans une étendue parente.

Tout d’abord, définissez une `$test` variable dans l’étendue globale.

```powershell
$test = "Global"
```

Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable. Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.

Dans Sample.ps1 :

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

Une fois le script terminé, la valeur globale de `$test` est modifiée.

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>Exemple 4 : création d’une variable privée

Une variable privée est une variable qui a une propriété **option** dont la valeur est *Private* . Les variables *privées* sont héritées par l’étendue enfant, mais elles ne peuvent être affichées ou modifiées que dans l’étendue dans laquelle elles ont été créées.

La commande suivante crée une variable privée appelée `$ptest` dans l’étendue locale.

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

Vous pouvez afficher et modifier la valeur de `$ptest` dans l’étendue locale.

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

Ensuite, créez un Sample.ps1 script qui contient les commandes suivantes. La commande tente d’afficher et de modifier la valeur de `$ptest` .

Dans Sample.ps1 :

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

La `$ptest` variable n’est pas visible dans l’étendue du script, la sortie est vide.

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>Exemple 5 : utilisation d’une variable locale dans une commande à distance

Pour les variables d’une commande distante créée dans la session locale, utilisez le `Using` modificateur de portée. PowerShell suppose que les variables des commandes distantes ont été créées dans la session à distance.

La syntaxe est :

```
$Using:<VariableName>
```

Par exemple, les commandes suivantes créent une `$Cred` variable dans la session locale, puis utilisent la `$Cred` variable dans une commande distante :

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

L’étendue using a été introduite dans PowerShell 3,0. Dans PowerShell 2,0, pour indiquer qu’une variable a été créée dans la session locale, utilisez le format de commande suivant.

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>Voir aussi

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)

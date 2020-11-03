---
description: Décrit les mots clés dans le langage de script PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 2eff6d41e8688a53e9983893356dd3692bfa407f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206525"
---
# <a name="about-language-keywords"></a>À propos des mots clés de langage

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les mots clés dans le langage de script PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PowerShell a les mots clés de langage suivants. Pour plus d’informations, consultez la rubrique about pour le mot clé et les informations qui suivent le tableau.

Mot clé     | Informations de référence
---         | ---
Début       | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Détection       | [about_Break](about_Break.md), [about_Trap](about_Trap.md)
Intercepter       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Classe       | [À propos des classes](about_Classes.md)
Continuer    | [about_Continue](about_Continue.md), [about_Trap](about_Trap.md)
Données        | [about_Data_Sections](about_Data_Sections.md)
Définir      | Paramètres réservés pour un usage ultérieur
Do          | [about_Do](about_Do.md), [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Else        | [about_If](about_If.md)
ElseIf      | [about_If](about_If.md)
End         | [about_Functions](about_Functions.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Énumération        | [À propos de l’énumération](about_Enum.md)
Quitter        | [Décrit dans cette rubrique](#exit)
Filtrer      | [about_Functions](about_Functions.md)
Finalement     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
For         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
À partir        | Paramètres réservés pour un usage ultérieur
Fonction    | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Hidden      | [about_Hidden](about_Hidden.md)
If          | [about_If](about_If.md)
Dans          | [about_ForEach](about_ForEach.md)
Paramètre       | [about_Functions](about_Functions.md)
Process     | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Renvoie      | [about_Return](about_Return.md)
statique      | [À propos des classes](about_Classes.md)
Commutateur      | [about_Switch](about_Switch.md)
Throw       | [about_Throw](about_Throw.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Trap        | [about_Trap](about_Trap.md), [about_Break](about_Break.md) [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Essai         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Until       | [about_Do](about_Do.md)
Utilisation       | [about_Using](about_Using.md), [about_Classes](about_Classes.md)
Var         | Paramètres réservés pour un usage ultérieur
While       | [about_While](about_While.md), [about_Do](about_Do.md)

Mots clés de langage

### <a name="begin"></a>Début

Spécifie une partie du corps d’une fonction, ainsi que les `DynamicParam` `Process` `End` Mots clés, et. La `Begin` liste des instructions s’exécute une fois avant que les objets ne soient reçus du pipeline.

Syntaxe :

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>Détection

Provoque la sortie d’un script d’une boucle.

Syntaxe :

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>Intercepter

Spécifie une liste d’instructions à exécuter si une erreur se produit dans la liste des instructions Try qui l’accompagne. Un type d’erreur requiert des crochets. La deuxième paire de crochets indique que le type d’erreur est facultatif.

Syntaxe :

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>Classe

Spécifie une nouvelle classe dans PowerShell.

Syntaxe :

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>Continuer

Provoque l’arrêt de l’exécution d’une boucle par un script et le retour à la condition. Si la condition est remplie, le script recommence la boucle.

Syntaxe :

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>Données

Dans un script, définit une section qui isole les données de la logique de script. Peut également inclure `If` des instructions et certaines commandes limitées.

Syntaxe :

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>Do

Utilisé avec le `While` `Until` mot clé ou en tant que construction de bouclage. PowerShell exécute la liste d’instructions au moins une fois, contrairement à une boucle qui utilise `While` .

Syntaxe pour `While` :

```Syntax
do {<statement list>} while (<condition>)
```

Syntaxe pour `Until` :

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

Spécifie une partie du corps d’une fonction, ainsi que les `Begin` `Process` `End` Mots clés, et. Les paramètres dynamiques sont ajoutés au moment de l’exécution.

Syntaxe :

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Else

Utilisé avec le `If` mot clé pour spécifier la liste d’instructions par défaut.

Syntaxe :

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>ElseIf

Utilisé avec les `If` `Else` Mots clés et pour spécifier des conditions supplémentaires. Le `Else` mot clé est facultatif.

Syntaxe :

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>End

Spécifie une partie du corps d’une fonction, ainsi que les `DynamicParam` `Begin` `End` Mots clés, et. La `End` liste des instructions est exécutée une fois après que tous les objets ont été reçus du pipeline.

Syntaxe :

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>Énumération

`enum` est utilisé pour déclarer une énumération ; type distinct qui se compose d’un ensemble d’étiquettes nommées appelé liste d’énumérateurs.

Syntaxe :

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>Quitter

Fait en sorte que PowerShell quitte un script ou une instance PowerShell.

Syntaxe :

```Syntax
exit
exit <exitcode>
```

Quand vous utilisez `pwsh` avec le paramètre **file** , le `.ps1` fichier (script) lui-même doit inclure des instructions pour la gestion des erreurs ou des exceptions qui se produisent pendant l’exécution du script. Vous devez uniquement utiliser l' `exit` instruction pour indiquer l’état de la suite de l’exécution du script.

Sur Windows, toute valeur comprise entre `[int]::MinValue` et `[int]::MaxValue` est autorisée.

Sur UNIX, seuls les nombres positifs entre `[byte]::MinValue` et `[byte]::MaxValue` sont autorisés. Un nombre négatif dans la plage comprise entre `-1` et `-255` est automatiquement converti en nombre positif en ajoutant 256. Par exemple, `-2` est transformé en `254` .

Dans PowerShell, l' `exit` instruction définit la valeur de la `$LASTEXITCODE` variable. Dans l’interface de commande Windows (cmd.exe), l’instruction Exit définit la valeur de la `%ERRORLEVEL%` variable d’environnement.

Tout argument qui n’est pas numérique ou qui se trouve en dehors de la plage spécifique à la plateforme est traduit en valeur de `0` .

Dans l’exemple suivant, l’utilisateur définit la valeur de la variable de niveau d’erreur sur 4 en ajoutant `exit 4` au fichier de script `test.ps1` .

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>pwsh -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

Lorsque vous exécutez `pwsh.exe -File <path to a script>` et que le fichier de script se termine par une `exit` commande, le code de sortie est défini sur l’argument numérique utilisé avec la `exit` commande. Si le script n’a pas d' `exit` instruction, le code de sortie est toujours `0` lorsque le script se termine sans erreur ou `1` lorsque le script se termine à partir d’une exception non gérée.

### <a name="filter"></a>Filtrer

Spécifie une fonction dans laquelle la liste d’instructions est exécutée une fois pour chaque objet d’entrée. Il a le même effet qu’une fonction qui contient uniquement un bloc de processus.

Syntaxe :

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>Finalement

Définit une liste d’instructions qui s’exécute après les instructions associées à try et catch. Une `Finally` liste d’instructions s’exécute même si vous appuyez sur `CTRL+C` pour quitter un script ou si vous utilisez le mot clé Exit dans le script.

Syntaxe :

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>For

Définit une boucle à l’aide d’une condition.

Syntaxe :

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

Définit une boucle à l’aide de chaque membre d’une collection.

Syntaxe :

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>À partir

Réservé à un usage ultérieur.

### <a name="function"></a>Fonction

Crée une liste d’instructions nommées de code réutilisable. Vous pouvez nommer l’étendue à laquelle appartient une fonction. Et vous pouvez spécifier un ou plusieurs paramètres nommés à l’aide du `Param` mot clé. Dans la liste des instructions de fonction, vous pouvez inclure des `DynamicParam` listes d’instructions,, `Begin` `Process` et `End` .

Syntaxe :

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

Vous avez également la possibilité de définir un ou plusieurs paramètres à l’extérieur de la liste d’instructions après le nom de la fonction.

Syntaxe :

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>If

Définit un conditionnel.

Syntaxe :

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>Hidden

Masque les membres de la classe des résultats par défaut de l’applet de commande `Get-Member` , et des résultats IntelliSense et de la saisie semi-automatique par tabulation.

Syntaxe :

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>Dans

Utilisé dans une `ForEach` instruction pour créer une boucle qui utilise chaque membre d’une collection.

Syntaxe :

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

Exécute des commandes de workflow dans une session PowerShell partagée. Ce mot clé est valide uniquement dans un flux de travail PowerShell.

Syntaxe :

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

Le `InlineScript` mot clé indique une `InlineScript` activité qui exécute des commandes dans une session partagée standard (sans flux de travail). Vous pouvez utiliser le `InlineScript` mot clé pour exécuter des commandes qui ne sont pas valides dans un flux de travail, et pour exécuter des commandes qui partagent des données. Par défaut, les commandes dans un bloc de script InlineScript s’exécutent dans un processus distinct.

Pour plus d’informations, consultez [exécution de commandes PowerShell dans un flux de travail](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11)).

### <a name="param"></a>Paramètre

Définit les paramètres dans une fonction.

Syntaxe :

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>Process

Spécifie une partie du corps d’une fonction, ainsi que les `DynamicParam` `Begin` `End` Mots clés, et. Lorsqu’une `Process` liste d’instructions reçoit une entrée du pipeline, la `Process` liste des instructions s’exécute une fois pour chaque élément du pipeline. Si le pipeline ne fournit aucun objet, la `Process` liste des instructions ne s’exécute pas. Si la commande est la première commande du pipeline, la `Process` liste des instructions est exécutée une fois.

Syntaxe :

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>Renvoie

Fait en sorte que PowerShell laisse la portée actuelle, telle qu’un script ou une fonction, et écrive l’expression facultative dans la sortie.

Syntaxe :

```Syntax
return [<expression>]
```

### <a name="static"></a>statique

Spécifie que la propriété ou la méthode définie est commune à toutes les instances de la classe dans laquelle est défini.

`Class`Pour obtenir des exemples d’utilisation, consultez.

### <a name="switch"></a>Commutateur

Pour vérifier plusieurs conditions, utilisez une `Switch` instruction. L' `Switch` instruction est équivalente à une série d' `If` instructions, mais elle est plus simple.

L' `Switch` instruction répertorie chaque condition et une action facultative. Si une condition est obtenue, l’action est effectuée.

Syntaxe 1 :

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

Syntaxe 2 :

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Throw

Lève un objet en tant qu’erreur.

Syntaxe :

```Syntax
throw [<object>]
```

### <a name="trap"></a>Trap

Définit une liste d’instructions à exécuter si une erreur est rencontrée. Un type d’erreur requiert des crochets. La deuxième paire de crochets indique que le type d’erreur est facultatif.

Syntaxe :

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>Essai

Définit une liste d’instructions pour laquelle des erreurs sont recherchées pendant l’exécution des instructions. Si une erreur se produit, PowerShell continue de s’exécuter dans une `Catch` `Finally` instruction ou. Un type d’erreur requiert des crochets. La deuxième paire de crochets indique que le type d’erreur est facultatif.

Syntaxe :

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>Until

Utilisé dans une `Do` instruction en tant que construction de bouclage où la liste d’instructions est exécutée au moins une fois.

Syntaxe :

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>Utilisation

Permet d’indiquer les espaces de noms qui sont utilisés dans la session. Les classes et les membres nécessitent moins de saisie pour les mentionner. Vous pouvez également inclure des classes à partir de modules.

#1 de syntaxe :

```Syntax
using namespace <.Net-framework-namespace>
```

#2 de syntaxe :

```Syntax
using module <module-name>
```

### <a name="while"></a>While

L' `while` instruction est une construction de bouclage dans laquelle la condition est testée avant l’exécution des instructions. Si la condition est FALSe, les instructions ne s’exécutent pas.

Syntaxe de l’instruction :

```Syntax
while (<condition>) {
   <statements>
 }
```

En cas d’utilisation dans une `Do` instruction, `while` fait partie d’une construction de bouclage dans laquelle la liste d’instructions est exécutée au moins une fois.

Syntaxe de la boucle do :

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>VOIR AUSSI

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)


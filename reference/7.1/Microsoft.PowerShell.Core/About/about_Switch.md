---
description: Explique comment utiliser un commutateur pour gérer plusieurs `If` instructions.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 4d70d765086ad49ed0e5cd955fc3be3094fc79a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208297"
---
# <a name="about-switch"></a>À propos du commutateur

## <a name="short-description"></a>Description courte
Explique comment utiliser un commutateur pour gérer plusieurs `If` instructions.

## <a name="long-description"></a>Description longue

Pour vérifier une condition dans un script ou une fonction, utilisez une `If` instruction. L' `If` instruction peut vérifier de nombreux types de conditions, y compris la valeur des variables et les propriétés des objets.

Pour vérifier plusieurs conditions, utilisez une `Switch` instruction. L' `Switch` instruction est équivalente à une série d' `If` instructions, mais elle est plus simple. L' `Switch` instruction répertorie chaque condition et une action facultative. Si une condition est obtenue, l’action est effectuée.

L' `Switch` instruction peut utiliser les `$_` `$switch` variables automatiques et. Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

Une instruction de base `Switch` a le format suivant :

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

Par exemple, l' `Switch` instruction suivante compare la valeur de test, 3, à chacune des conditions. Lorsque la valeur de test correspond à la condition, l’action est effectuée.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

Dans cet exemple simple, la valeur est comparée à chaque condition de la liste, même s’il existe une correspondance pour la valeur 3. L' `Switch` instruction suivante a deux conditions pour la valeur 3. Il montre que, par défaut, toutes les conditions sont testées.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

Pour indiquer `Switch` à d’arrêter la comparaison après une correspondance, utilisez l' `Break` instruction. L' `Break` instruction termine l' `Switch` instruction.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

Si la valeur de test est une collection, telle qu’un tableau, chaque élément de la collection est évalué dans l’ordre dans lequel il apparaît. Les exemples suivants évaluent 4, puis 2.

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

Toutes les `Break` instructions s’appliquent à la collection, et non à chaque valeur, comme indiqué dans l’exemple suivant. L’instruction `Switch` se termine par l' `Break` instruction dans la condition de valeur 4.

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>Syntaxe

La syntaxe complète de l' `Switch` instruction est la suivante :

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

ou

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

Si aucun paramètre n’est utilisé, `Switch` se comporte de la même façon que l’utilisation du paramètre **exact** . Elle effectue une correspondance qui ne respecte pas la casse pour la valeur. Si la valeur est une collection, chaque élément est évalué dans l’ordre dans lequel il apparaît.

L' `Switch` instruction doit inclure au moins une instruction de condition.

La `Default` clause est déclenchée lorsque la valeur ne correspond à aucune des conditions. Elle est équivalente à une `Else` clause dans une `If` instruction. Une seule `Default` clause est autorisée dans chaque `Switch` instruction.

`Switch` a les paramètres suivants :

- **Caractère générique** : indique que la condition est une chaîne de caractères génériques. Si la clause match n’est pas une chaîne, le paramètre est ignoré. La comparaison ne respecte pas la casse.
- **Exact** -indique que la clause match, s’il s’agit d’une chaîne, doit correspondre exactement. Si la clause match n’est pas une chaîne, ce paramètre est ignoré. La comparaison ne respecte pas la casse.
- **CaseSensitive** -effectue une correspondance respectant la casse. Si la clause match n’est pas une chaîne, ce paramètre est ignoré.
- **Fichier** : prend une entrée à partir d’un fichier plutôt qu’une instruction de valeur. Si plusieurs paramètres de **fichier** sont inclus, seul le dernier est utilisé. Chaque ligne du fichier est lue et évaluée par l' `Switch` instruction. La comparaison ne respecte pas la casse.
- **Regex** : effectue la correspondance d’expression régulière de la valeur avec la condition. Si la clause match n’est pas une chaîne, ce paramètre est ignoré.
  La comparaison ne respecte pas la casse. La `$matches` variable automatique est disponible pour une utilisation dans le bloc d’instructions correspondant.

> [!NOTE]
> Lorsque vous spécifiez des valeurs conflictuelles, comme **Regex** et **caractère générique** , le dernier paramètre spécifié est prioritaire et tous les paramètres en conflit sont ignorés. Plusieurs instances de paramètres sont également autorisées. Toutefois, seul le dernier paramètre utilisé est effectif.

Dans cet exemple, un objet qui n’est pas une chaîne ou des données numériques est passé à l' `Switch` . `Switch`Effectue une contrainte de chaîne sur l’objet et évalue le résultat.

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

Dans cet exemple, il n’y a pas de casse correspondante et il n’y a pas de sortie.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

En ajoutant la `Default` clause, vous pouvez effectuer une action quand aucune autre condition ne parvient.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

Pour que le mot « quatorze » corresponde à un cas, vous devez utiliser le `-Wildcard` `-Regex` paramètre ou.

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

L’exemple suivant utilise le `-Regex` paramètre.

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

Une condition de l’instruction switch peut être :

- Expression dont la valeur est comparée à la valeur d’entrée
- Bloc de script qui doit retourner `$true` si une condition est remplie.

La `$_` variable automatique contient la valeur transmise à l’instruction switch et est disponible à des fins d’évaluation et d’utilisation dans l’étendue des instructions de condition.

L’action pour chaque condition est indépendante des actions dans d’autres conditions.

L’exemple suivant illustre l’utilisation de blocs de script comme `Switch` conditions d’instruction.

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

Si la valeur correspond à plusieurs conditions, l’action de chaque condition est exécutée. Pour modifier ce comportement, utilisez les `Break` `Continue` Mots clés ou.

Le `Break` mot clé arrête le traitement et quitte l' `Switch` instruction.

Le `Continue` mot clé arrête le traitement de la valeur actuelle, mais continue le traitement des valeurs suivantes.

L’exemple suivant traite un tableau de nombres et s’affiche s’ils sont impairs ou pairs. Les nombres négatifs sont ignorés par le `Continue` mot clé. Si aucun nombre n’est rencontré, l’exécution se termine par le `Break` mot clé.

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>Voir aussi

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

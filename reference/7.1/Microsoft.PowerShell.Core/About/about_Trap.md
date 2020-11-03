---
description: Décrit un mot clé qui gère une erreur de fin.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: a0e852f63e37bd18e769943f98bca264ab360d3a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207714"
---
# <a name="about-trap"></a>À propos de l’interruption

## <a name="short-description"></a>Description courte

Décrit un mot clé qui gère une erreur de fin.

## <a name="long-description"></a>Description longue

Une erreur d’arrêt empêche l’exécution d’une instruction. Si PowerShell ne gère pas une erreur de fin d’une certaine façon, PowerShell arrête également l’exécution de la fonction ou du script dans le pipeline actuel. Dans d’autres langages, tels que C#, les erreurs de fin sont connues sous le nom d’exceptions.

Le `trap` mot clé spécifie une liste d’instructions à exécuter lorsqu’une erreur d’arrêt se produit. `trap` les instructions traitent les erreurs de fin de la façon suivante :

- Affichez l’erreur après le traitement du `trap` bloc d’instructions et la poursuite de l’exécution du script ou de la fonction contenant `trap` . Il s'agit du comportement par défaut.

- Affichez l’erreur et annulez l’exécution du script ou de la fonction contenant le `trap` à l’aide `break` de dans l' `trap` instruction.

- Interrompez l’erreur, mais poursuivez l’exécution du script ou de la fonction contenant le `trap` en utilisant `continue` dans l' `trap` instruction.

La liste des instructions de `trap` peut inclure plusieurs conditions ou appels de fonction. Un `trap` peut écrire des journaux, des conditions de test ou même exécuter un autre programme.

### <a name="syntax"></a>Syntaxe

L' `trap` instruction a la syntaxe suivante :

```powershell
trap [[<error type>]] {<statement list>}
```

L' `trap` instruction contient une liste d’instructions à exécuter lorsqu’une erreur se termine. Une `trap` instruction se compose du `trap` mot clé, éventuellement suivi d’une expression de type et du bloc d’instructions contenant la liste des instructions à exécuter lorsqu’une erreur est interceptée. L’expression de type affine les types d’erreurs `trap` interceptés.

Un script ou une commande peut avoir plusieurs `trap` instructions. `trap` les instructions peuvent apparaître n’importe où dans le script ou la commande.

### <a name="trapping-all-terminating-errors"></a>Récupération de toutes les erreurs de fin

Lorsqu’une erreur d’arrêt se produit qui n’est pas gérée d’une autre façon dans un script ou une commande, PowerShell recherche une `trap` instruction qui gère l’erreur. Si une `trap` instruction est présente, PowerShell continue à exécuter le script ou la commande dans l' `trap` instruction.

L’exemple suivant est une instruction très simple `trap` :

```powershell
trap {"Error found."}
```

Cette `trap` instruction intercepte toute erreur qui se termine.

Dans l’exemple suivant, la fonction contient une chaîne incompréhensible qui provoque une erreur d’exécution.

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

L’exécution de cette fonction retourne ce qui suit :

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

L’exemple suivant comprend une `trap` instruction qui affiche l’erreur à l’aide de la `$_` variable automatique :

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

L’exécution de cette version de la fonction retourne ce qui suit :

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` les instructions peuvent être définies n’importe où dans une étendue donnée, mais s’appliquent toujours à toutes les instructions de cette étendue. Lors de l’exécution, `trap` les instructions d’un bloc sont définies avant l’exécution de toute autre instruction. En JavaScript, c’est ce qu’on appelle le « [levage](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)». Cela signifie que `trap` les instructions s’appliquent à toutes les instructions de ce bloc, même si l’exécution n’a pas avancé au-delà du point auquel elles sont définies. Par exemple, la définition d’un `trap` à la fin d’un script et la génération d’une erreur dans la première instruction déclenche toujours cela `trap` .

### <a name="trapping-specific-errors"></a>Interception des erreurs spécifiques

Un script ou une commande peut avoir plusieurs `trap` instructions. Une `trap` peut être définie pour gérer des erreurs spécifiques.

L’exemple suivant est une `trap` instruction qui intercepte l’erreur spécifique **CommandNotFoundException** :

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

Lorsqu’une fonction ou un script rencontre une chaîne qui ne correspond pas à une commande connue, cette `trap` instruction affiche la chaîne « erreur de commande interceptée ».
Après l’exécution de la `trap` liste d’instructions, PowerShell écrit l’objet d’erreur dans le flux d’erreurs, puis continue le script.

PowerShell utilise les types d’exceptions .NET. L’exemple suivant spécifie le type d’erreur **System. exception** :

```powershell
trap [System.Exception] {"An error trapped"}
```

Le type d’erreur **CommandNotFoundException** hérite du type **System. exception** . Cette instruction intercepte une erreur créée par une commande inconnue. Il intercepte également d’autres types d’erreur.

Vous pouvez avoir plusieurs `trap` instructions dans un script. Chaque type d’erreur peut être intercepté par une seule `trap` instruction. Lorsqu’une erreur se termine, PowerShell recherche le `trap` avec la correspondance la plus spécifique, en commençant par la portée d’exécution actuelle.

L’exemple de script suivant contient une erreur. Le script contient une `trap` instruction générale qui intercepte toutes les erreurs de fin et une `trap` instruction spécifique qui spécifie le type **CommandNotFoundException** .

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

L’exécution de ce script produit le résultat suivant :

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Étant donné que PowerShell ne reconnaît pas « nonsenseString » comme une applet de commande ou un autre élément, il renvoie une erreur **CommandNotFoundException** . Cette erreur de fin est interceptée par l' `trap` instruction spécifique.

L’exemple de script suivant contient les mêmes `trap` instructions avec une erreur différente :

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

L’exécution de ce script produit le résultat suivant :

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

La tentative de division par zéro ne crée pas d’erreur **CommandNotFoundException** . Au lieu de cela, cette erreur est interceptée par l’autre `trap` instruction, qui intercepte toutes les erreurs qui se terminent.

### <a name="trapping-errors-and-scope"></a>Interception des erreurs et de la portée

Si une erreur d’arrêt se produit dans la même portée que l' `trap` instruction, PowerShell exécute la liste des instructions définies par le `trap` . L’exécution se poursuit à l’instruction qui suit l’erreur. Si l' `trap` instruction se trouve dans une étendue différente de celle de l’erreur, l’exécution se poursuit à l’instruction suivante qui se trouve dans la même portée que l' `trap` instruction.

Par exemple, si une erreur se produit dans une fonction et que l' `trap` instruction se trouve dans la fonction, le script se poursuit à l’instruction suivante. Le script suivant contient une erreur et une `trap` instruction :

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

L’exécution de ce script produit le résultat suivant :

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

L' `trap` instruction dans la fonction intercepte l’erreur. Après l’affichage du message, PowerShell reprend l’exécution de la fonction. Notez que `Function1` a été terminé.

Comparez ceci avec l’exemple suivant, qui a la même erreur et la même `trap` instruction. Dans cet exemple, l' `trap` instruction se trouve en dehors de la fonction :

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

L’exécution de la `Function2` fonction produit le résultat suivant :

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Dans cet exemple, la commande « fonction2 is Completed » n’a pas été exécutée. Dans les deux exemples, l’erreur d’arrêt se produit dans la fonction. Dans cet exemple, cependant, l' `trap` instruction est en dehors de la fonction. PowerShell ne revient pas à la fonction après l’exécution de l' `trap` instruction.

> [!CAUTION]
> Lorsque plusieurs interruptions sont définies pour la même condition d’erreur, la première `trap` définie lexicalement (la plus élevée dans l’étendue) est utilisée.

Dans l’exemple suivant, seul le `trap` avec « whoops 1 » est exécuté.

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> Une instruction Trap est limitée à l’emplacement où elle est compilée. Si vous avez une `trap` instruction à l’intérieur d’une fonction ou d’un script de code source point, lorsque le script de la fonction ou du point s’arrête, toutes les `trap` instructions à l’intérieur de sont supprimées.

### <a name="using-the-break-and-continue-keywords"></a>Utilisation des mots clés Break et continue

Vous pouvez utiliser les `break` `continue` Mots clés et dans une `trap` instruction pour déterminer si un script ou une commande continue à s’exécuter après une erreur d’arrêt.

Si vous incluez une `break` instruction dans une `trap` liste d’instructions, PowerShell arrête la fonction ou le script. L’exemple de fonction suivant utilise le `break` mot clé dans une `trap` instruction :

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

Étant donné que l' `trap` instruction incluait le `break` mot clé, la fonction ne continue pas de s’exécuter et la ligne « fonction terminée » n’est pas exécutée.

Si vous incluez un `continue` mot clé dans une `trap` instruction, PowerShell reprend après l’instruction qui a provoqué l’erreur, comme c’est le cas sans `break` ou `continue` . `continue`Toutefois, avec le mot clé, PowerShell n’écrit pas d’erreur dans le flux d’erreurs.

L’exemple de fonction suivant utilise le `continue` mot clé dans une `trap` instruction :

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

La fonction reprend après que l’erreur a été interceptée et l’instruction « Function Completed » s’exécute. Aucune erreur n’est écrite dans le flux d’erreurs.

## <a name="notes"></a>Notes

`trap` les instructions offrent un moyen simple de s’assurer que toutes les erreurs de fin au sein d’une étendue sont gérées. Pour une gestion des erreurs plus fine, utilisez des `try` / `catch` blocs où les interruptions sont définies à l’aide d' `catch` instructions. Les `catch` instructions s’appliquent uniquement au code à l’intérieur de l' `try` instruction associée. Pour plus d’informations, consultez [about_Try_Catch_Finally](about_Try_Catch_Finally.md).

## <a name="see-also"></a>Voir aussi

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

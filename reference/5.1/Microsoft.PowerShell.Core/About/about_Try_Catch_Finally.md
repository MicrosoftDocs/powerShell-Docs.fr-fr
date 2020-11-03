---
description: Décrit comment utiliser les `Try` blocs, `Catch` et `Finally` pour gérer les erreurs de fin.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: 4cb392df950184feeee1fe2e3567004b94d14b36
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207525"
---
# <a name="about-try-catch-finally"></a>À propos de try catch finally

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment utiliser les `Try` blocs, `Catch` et `Finally` pour gérer les erreurs de fin.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Utilisez `Try` des `Catch` blocs, et `Finally` pour répondre à ou gérer les erreurs de fin dans les scripts. L' `Trap` instruction peut également être utilisée pour gérer les erreurs de fin dans les scripts. Pour plus d’informations, consultez [about_Trap](about_Trap.md).

Une erreur d’arrêt empêche l’exécution d’une instruction. Si PowerShell ne gère pas une erreur de fin d’une certaine façon, PowerShell arrête également l’exécution de la fonction ou du script à l’aide du pipeline actuel. Dans d’autres langages, tels que C \# , les erreurs de fin sont appelées exceptions.

Utilisez le `Try` bloc pour définir une section d’un script dans laquelle vous souhaitez que PowerShell surveille les erreurs. Lorsqu’une erreur se produit dans le `Try` bloc, l’erreur est d’abord enregistrée dans la `$Error` variable automatique. PowerShell recherche ensuite un `Catch` bloc pour gérer l’erreur. Si l' `Try` instruction n’a pas de `Catch` bloc correspondant, PowerShell continue de rechercher un `Catch` bloc ou une instruction appropriés `Trap` dans les étendues parentes. Une fois qu’un `Catch` bloc est terminé ou qu’aucun `Catch` bloc ou `Trap` instruction approprié n’a été trouvé, le `Finally` bloc est exécuté. Si l’erreur ne peut pas être gérée, l’erreur est écrite dans le flux d’erreurs.

Un `Catch` bloc peut inclure des commandes pour le suivi de l’erreur ou pour la récupération du déroulement attendu du script. Un `Catch` bloc peut spécifier les types d’erreurs qu’il intercepte. Une `Try` instruction peut inclure plusieurs `Catch` blocs pour différents genres d’erreurs.

Un `Finally` bloc peut être utilisé pour libérer toutes les ressources qui ne sont plus nécessaires à votre script.

`Try`, et `Catch` `Finally` ressemblent aux `Try` `Catch` Mots clés, et `Finally` utilisés dans le \# langage de programmation C.

### <a name="syntax"></a>SYNTAX

Une `Try` instruction contient un `Try` bloc, zéro, un ou plusieurs `Catch` blocs, et zéro ou un `Finally` bloc. Une `Try` instruction doit avoir au moins un bloc `Catch` ou un `Finally` bloc.

L’exemple suivant illustre la `Try` syntaxe de bloc :

```powershell
try {<statement list>}
```

Le `Try` mot clé est suivi d’une liste d’instructions entre accolades. Si une erreur d’arrêt se produit pendant l’exécution des instructions de la liste d’instructions, le script passe l’objet d’erreur du `Try` bloc à un `Catch` bloc approprié.

L’exemple suivant illustre la `Catch` syntaxe de bloc :

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

Les types d’erreurs apparaissent entre crochets. Les crochets les plus éloignés indiquent que l’élément est facultatif.

Le `Catch` mot clé est suivi d’une liste facultative de spécifications de type d’erreur et d’une liste d’instructions. Si une erreur se termine dans le `Try` bloc, PowerShell recherche un bloc approprié `Catch` . Si un est trouvé, les instructions du `Catch` bloc sont exécutées.

Le `Catch` bloc peut spécifier un ou plusieurs types d’erreurs. Un type d’erreur est une exception Microsoft .NET Framework ou une exception dérivée d’une exception .NET Framework. Un `Catch` bloc gère les erreurs de la classe d’exception .NET Framework spécifiée ou de toute classe qui dérive de la classe spécifiée.

Si un `Catch` bloc spécifie un type d’erreur, ce `Catch` bloc gère ce type d’erreur. Si un `Catch` bloc ne spécifie pas de type d’erreur, ce `Catch` bloc gère toutes les erreurs rencontrées dans le `Try` bloc. Une `Try` instruction peut inclure plusieurs `Catch` blocs pour les différents types d’erreur spécifiés.

L’exemple suivant illustre la `Finally` syntaxe de bloc :

```powershell
finally {<statement list>}
```

Le `Finally` mot clé est suivi d’une liste d’instructions qui s’exécute chaque fois que le script est exécuté, même si l' `Try` instruction a été exécutée sans erreur ou si une erreur a été interceptée dans une `Catch` instruction.

Notez que la <kbd>combinaison de touches Ctrl</kbd> + <kbd>+</kbd> arrête le pipeline. Les objets qui sont envoyés au pipeline ne seront pas affichés en tant que sortie. Par conséquent, si vous incluez une instruction à afficher, par exemple « le bloc finally a été exécuté », elle ne s’affichera pas une fois que vous aurez appuyé sur <kbd>CTRL</kbd> + <kbd>C</kbd>, même si le `Finally` bloc s’exécutait.

### <a name="catching-errors"></a>INTERCEPTION DES ERREURS

L’exemple de script suivant illustre un `Try` bloc avec un `Catch` bloc :

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

Le `Catch` mot clé doit suivre immédiatement le `Try` bloc ou un autre `Catch` bloc.

PowerShell ne reconnaît pas « NonsenseString » comme une applet de commande ou un autre élément.
L’exécution de ce script renvoie le résultat suivant :

```powershell
An error occurred.
```

Quand le script rencontre « NonsenseString », il provoque une erreur de fin. Le `Catch` bloc gère l’erreur en exécutant la liste d’instructions à l’intérieur du bloc.

### <a name="using-multiple-catch-statements"></a>UTILISATION DE PLUSIEURS INSTRUCTIONS CATCH

Une `Try` instruction peut comporter un nombre quelconque de `Catch` blocs. Par exemple, le script suivant contient un `Try` bloc qui est téléchargé `MyDoc.doc` et contient deux `Catch` blocs :

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

Le premier `Catch` bloc gère les erreurs des types **System .net. WebException** et **System. IO. IOException** . Le deuxième `Catch` bloc ne spécifie pas de type d’erreur. Le deuxième `Catch` bloc gère toutes les autres erreurs de fin qui se produisent.

PowerShell met en correspondance les types d’erreurs par héritage. Un `Catch` bloc gère les erreurs de la classe d’exception .NET Framework spécifiée ou de toute classe qui dérive de la classe spécifiée. L’exemple suivant contient un `Catch` bloc qui intercepte une erreur « commande introuvable » :

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

Le type d’erreur spécifié, **CommandNotFoundException** , hérite du type de **temExceptionSystem.Sys** . L’exemple suivant intercepte également une erreur de commande introuvable :

```powershell
catch [System.SystemException] {"Base Exception" }
```

Ce `Catch` bloc gère l’erreur « commande introuvable » et les autres erreurs qui héritent du type **SystemException** .

Si vous spécifiez une classe d’erreur et l’une de ses classes dérivées, placez le `Catch` bloc de la classe dérivée avant le `Catch` bloc de la classe générale.

### <a name="using-traps-in-a-try-catch"></a>Utilisation d’interruptions dans une tentative catch

Lorsqu’une erreur d’arrêt se produit dans un `Try` bloc avec un `Trap` défini dans le `Try` bloc, même s’il existe un `Catch` bloc correspondant, l' `Trap` instruction prend le contrôle.

Si un `Trap` existe dans un bloc supérieur à `Try` , et qu’il n’existe pas de `Catch` bloc correspondant dans la portée actuelle, le prend le `Trap` contrôle, même si une portée parente a un `Catch` bloc correspondant.

### <a name="accessing-exception-information"></a>ACCÈS AUX INFORMATIONS SUR LES EXCEPTIONS

Dans un `Catch` bloc, l’erreur actuelle est accessible à l’aide de `$_` , qui est également connu sous le nom de `$PSItem` . L’objet est de type **ErrorRecord** .

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

L’exécution de ce script renvoie le résultat suivant :

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

Des propriétés supplémentaires sont accessibles, telles que **ScriptStackTrace** , **exception** et **ErrorDetails** .  Par exemple, si nous modifions le script comme suit :

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

Le résultat sera semblable à ce qui suit :

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>LIBÉRATION DE RESSOURCES À L’AIDE DE FINALLY

Pour libérer les ressources utilisées par un script, ajoutez un `Finally` bloc après `Try` les `Catch` blocs et. Les `Finally` instructions de bloc s’exécutent indépendamment du fait que le `Try` bloc rencontre une erreur de fin d’exécution. PowerShell exécute le `Finally` bloc avant que le script ne se termine ou avant que le bloc actuel ne soit hors de portée.

Un `Finally` bloc s’exécute même si vous utilisez <kbd>CTRL</kbd> + <kbd>C</kbd> pour arrêter le script. Un `Finally` bloc s’exécute également si un mot clé Exit arrête le script dans un `Catch` bloc.

### <a name="see-also"></a>VOIR AUSSI

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

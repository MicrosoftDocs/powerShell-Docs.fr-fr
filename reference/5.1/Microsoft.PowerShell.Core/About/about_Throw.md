---
description: Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194171"
---
# <a name="about-throw"></a>À propos de Throw

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le mot clé throw provoque une erreur d’arrêt. Vous pouvez utiliser le mot clé throw pour arrêter le traitement d’une commande, d’une fonction ou d’un script.

Par exemple, vous pouvez utiliser le mot clé throw dans le bloc de script d’une instruction if pour répondre à une condition ou dans le bloc catch d’une instruction try-catch-finally. Vous pouvez également utiliser le mot clé throw dans une déclaration de paramètre pour rendre un paramètre de fonction obligatoire.

Le mot clé throw peut lever n’importe quel objet, tel qu’une chaîne de message utilisateur ou l’objet qui a provoqué l’erreur.

## <a name="syntax"></a>SYNTAX

La syntaxe du mot clé throw est la suivante :

```powershell
throw [<expression>]
```

L’expression dans la syntaxe Throw est facultative. Lorsque l’instruction throw n’apparaît pas dans un bloc catch et qu’elle n’inclut pas d’expression, elle génère une erreur ScriptHalted.

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

Si le mot clé throw est utilisé dans un bloc catch sans expression, il lève à nouveau le RuntimeException actuel. Pour plus d’informations, consultez about_Try_Catch_Finally.

## <a name="throwing-a-string"></a>LEVÉE D’UNE CHAÎNE

L’expression facultative dans une instruction throw peut être une chaîne, comme illustré dans l’exemple suivant :

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>LEVÉE D’AUTRES OBJETS

L’expression peut également être un objet qui lève l’objet qui représente le processus PowerShell, comme indiqué dans l’exemple suivant :

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

Vous pouvez utiliser la propriété TargetObject de l’objet ErrorRecord dans la variable automatique $error pour examiner l’erreur.

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

Vous pouvez également lever un objet ErrorRecord ou une exception Microsoft .NET Framework. L’exemple suivant utilise le mot clé throw pour lever un objet System. FormatException.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>ERREUR RÉSULTANTE

Le mot clé throw peut générer un objet ErrorRecord. La propriété d’exception de l’objet ErrorRecord contient un objet RuntimeException. Le reste de l’objet ErrorRecord et l’objet RuntimeException varient avec l’objet que le mot clé throw lève.

L’objet RunTimeException est encapsulé dans un objet ErrorRecord, et l’objet ErrorRecord est automatiquement enregistré dans la variable automatique $Error.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>UTILISATION DE THROW POUR CRÉER UN PARAMÈTRE OBLIGATOIRE

Vous pouvez utiliser le mot clé throw pour rendre un paramètre de fonction obligatoire.

Il s’agit d’une alternative à l’utilisation du paramètre obligatoire du mot clé Parameter. Quand vous utilisez le paramètre obligatoire, le système demande à l’utilisateur la valeur de paramètre obligatoire. Lorsque vous utilisez le mot clé throw, la commande s’arrête et affiche l’enregistrement d’erreur.

Par exemple, le mot clé throw dans le paramètre sous-expression fait du paramètre Path un paramètre obligatoire dans la fonction.

Dans ce cas, le mot clé throw lève une chaîne de message, mais il s’agit de la présence du mot clé throw qui génère l’erreur de fin si le paramètre Path n’est pas spécifié. L’expression qui suit Throw est facultative.

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>VOIR AUSSI

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

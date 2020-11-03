---
description: Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: d4bf0ea00145c03522d4db952be201c877c9d50c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207722"
---
# <a name="about-throw"></a>À propos de Throw

## <a name="short-description"></a>Description courte
Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.

## <a name="long-description"></a>Description longue

Le mot clé throw provoque une erreur d’arrêt. Vous pouvez utiliser le mot clé throw pour arrêter le traitement d’une commande, d’une fonction ou d’un script.

Par exemple, vous pouvez utiliser le mot clé throw dans le bloc de script d’une instruction if pour répondre à une condition ou dans le bloc catch d’une instruction try-catch-finally. Vous pouvez également utiliser le mot clé throw dans une déclaration de paramètre pour rendre un paramètre de fonction obligatoire.

Le mot clé throw peut lever n’importe quel objet, tel qu’une chaîne de message utilisateur ou l’objet qui a provoqué l’erreur.

## <a name="syntax"></a>Syntaxe

La syntaxe du mot clé throw est la suivante :

```powershell
throw [<expression>]
```

L’expression dans la syntaxe Throw est facultative. Lorsque l’instruction throw n’apparaît pas dans un bloc catch et qu’elle n’inclut pas d’expression, elle génère une erreur ScriptHalted.

```powershell
C:\PS> throw

Exception: ScriptHalted
```

Si le mot clé throw est utilisé dans un bloc catch sans expression, il lève à nouveau le RuntimeException actuel. Pour plus d’informations, consultez about_Try_Catch_Finally.

## <a name="throwing-a-string"></a>Levée d’une chaîne

L’expression facultative dans une instruction throw peut être une chaîne, comme illustré dans l’exemple suivant :

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a>Levée d’autres objets

L’expression peut également être un objet qui lève l’objet qui représente le processus PowerShell, comme indiqué dans l’exemple suivant :

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

Vous pouvez utiliser la propriété TargetObject de l’objet ErrorRecord dans la variable automatique $error pour examiner l’erreur.

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

Vous pouvez également lever un objet ErrorRecord ou une exception .NET. L’exemple suivant utilise le mot clé throw pour lever un objet System. FormatException.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a>L’erreur résultante

Le mot clé throw peut générer un objet ErrorRecord. La propriété d’exception de l’objet ErrorRecord contient un objet RuntimeException. Le reste de l’objet ErrorRecord et l’objet RuntimeException varient avec l’objet que le mot clé throw lève.

L’objet RunTimeException est encapsulé dans un objet ErrorRecord, et l’objet ErrorRecord est automatiquement enregistré dans la variable automatique $Error.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>Utilisation de Throw pour créer un paramètre obligatoire

Contrairement aux versions précédentes de PowerShell, n’utilisez pas le mot clé throw pour la validation des paramètres. Consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) pour obtenir la bonne méthode.

## <a name="see-also"></a>Voir aussi

- [about_Break](about_Break.md)
- [about_Continue](about_Continue.md)
- [about_Scopes](about_Scopes.md)
- [about_Trap](about_Trap.md)
- [about_Try_Catch_Finally](about_Try_Catch_Finally.md)

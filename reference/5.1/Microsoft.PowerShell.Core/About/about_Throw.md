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
# <a name="about-throw"></a><span data-ttu-id="2c697-103">À propos de Throw</span><span class="sxs-lookup"><span data-stu-id="2c697-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="2c697-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="2c697-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2c697-105">Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.</span><span class="sxs-lookup"><span data-stu-id="2c697-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="2c697-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="2c697-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2c697-107">Le mot clé throw provoque une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="2c697-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="2c697-108">Vous pouvez utiliser le mot clé throw pour arrêter le traitement d’une commande, d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="2c697-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="2c697-109">Par exemple, vous pouvez utiliser le mot clé throw dans le bloc de script d’une instruction if pour répondre à une condition ou dans le bloc catch d’une instruction try-catch-finally.</span><span class="sxs-lookup"><span data-stu-id="2c697-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="2c697-110">Vous pouvez également utiliser le mot clé throw dans une déclaration de paramètre pour rendre un paramètre de fonction obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2c697-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="2c697-111">Le mot clé throw peut lever n’importe quel objet, tel qu’une chaîne de message utilisateur ou l’objet qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c697-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c697-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c697-112">SYNTAX</span></span>

<span data-ttu-id="2c697-113">La syntaxe du mot clé throw est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2c697-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="2c697-114">L’expression dans la syntaxe Throw est facultative.</span><span class="sxs-lookup"><span data-stu-id="2c697-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="2c697-115">Lorsque l’instruction throw n’apparaît pas dans un bloc catch et qu’elle n’inclut pas d’expression, elle génère une erreur ScriptHalted.</span><span class="sxs-lookup"><span data-stu-id="2c697-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="2c697-116">Si le mot clé throw est utilisé dans un bloc catch sans expression, il lève à nouveau le RuntimeException actuel.</span><span class="sxs-lookup"><span data-stu-id="2c697-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="2c697-117">Pour plus d’informations, consultez about_Try_Catch_Finally.</span><span class="sxs-lookup"><span data-stu-id="2c697-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="2c697-118">LEVÉE D’UNE CHAÎNE</span><span class="sxs-lookup"><span data-stu-id="2c697-118">THROWING A STRING</span></span>

<span data-ttu-id="2c697-119">L’expression facultative dans une instruction throw peut être une chaîne, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2c697-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="2c697-120">LEVÉE D’AUTRES OBJETS</span><span class="sxs-lookup"><span data-stu-id="2c697-120">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="2c697-121">L’expression peut également être un objet qui lève l’objet qui représente le processus PowerShell, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2c697-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

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

<span data-ttu-id="2c697-122">Vous pouvez utiliser la propriété TargetObject de l’objet ErrorRecord dans la variable automatique $error pour examiner l’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c697-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="2c697-123">Vous pouvez également lever un objet ErrorRecord ou une exception Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c697-123">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="2c697-124">L’exemple suivant utilise le mot clé throw pour lever un objet System. FormatException.</span><span class="sxs-lookup"><span data-stu-id="2c697-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

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

## <a name="resulting-error"></a><span data-ttu-id="2c697-125">ERREUR RÉSULTANTE</span><span class="sxs-lookup"><span data-stu-id="2c697-125">RESULTING ERROR</span></span>

<span data-ttu-id="2c697-126">Le mot clé throw peut générer un objet ErrorRecord.</span><span class="sxs-lookup"><span data-stu-id="2c697-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="2c697-127">La propriété d’exception de l’objet ErrorRecord contient un objet RuntimeException.</span><span class="sxs-lookup"><span data-stu-id="2c697-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="2c697-128">Le reste de l’objet ErrorRecord et l’objet RuntimeException varient avec l’objet que le mot clé throw lève.</span><span class="sxs-lookup"><span data-stu-id="2c697-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="2c697-129">L’objet RunTimeException est encapsulé dans un objet ErrorRecord, et l’objet ErrorRecord est automatiquement enregistré dans la variable automatique $Error.</span><span class="sxs-lookup"><span data-stu-id="2c697-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="2c697-130">UTILISATION DE THROW POUR CRÉER UN PARAMÈTRE OBLIGATOIRE</span><span class="sxs-lookup"><span data-stu-id="2c697-130">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="2c697-131">Vous pouvez utiliser le mot clé throw pour rendre un paramètre de fonction obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2c697-131">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="2c697-132">Il s’agit d’une alternative à l’utilisation du paramètre obligatoire du mot clé Parameter.</span><span class="sxs-lookup"><span data-stu-id="2c697-132">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="2c697-133">Quand vous utilisez le paramètre obligatoire, le système demande à l’utilisateur la valeur de paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2c697-133">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="2c697-134">Lorsque vous utilisez le mot clé throw, la commande s’arrête et affiche l’enregistrement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c697-134">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="2c697-135">Par exemple, le mot clé throw dans le paramètre sous-expression fait du paramètre Path un paramètre obligatoire dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="2c697-135">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="2c697-136">Dans ce cas, le mot clé throw lève une chaîne de message, mais il s’agit de la présence du mot clé throw qui génère l’erreur de fin si le paramètre Path n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="2c697-136">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="2c697-137">L’expression qui suit Throw est facultative.</span><span class="sxs-lookup"><span data-stu-id="2c697-137">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="2c697-138">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="2c697-138">SEE ALSO</span></span>

[<span data-ttu-id="2c697-139">about_Break</span><span class="sxs-lookup"><span data-stu-id="2c697-139">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="2c697-140">about_Continue</span><span class="sxs-lookup"><span data-stu-id="2c697-140">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="2c697-141">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="2c697-141">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="2c697-142">about_Trap</span><span class="sxs-lookup"><span data-stu-id="2c697-142">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="2c697-143">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="2c697-143">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

---
description: Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: 2984e0a9e5f470594dd1e5987b69b92f91ce4913
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193951"
---
# <a name="about-throw"></a><span data-ttu-id="4841a-103">À propos de Throw</span><span class="sxs-lookup"><span data-stu-id="4841a-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="4841a-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="4841a-104">Short description</span></span>
<span data-ttu-id="4841a-105">Décrit le mot clé Throw qui génère une erreur avec fin d'exécution.</span><span class="sxs-lookup"><span data-stu-id="4841a-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="4841a-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="4841a-106">Long description</span></span>

<span data-ttu-id="4841a-107">Le mot clé throw provoque une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="4841a-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="4841a-108">Vous pouvez utiliser le mot clé throw pour arrêter le traitement d’une commande, d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="4841a-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="4841a-109">Par exemple, vous pouvez utiliser le mot clé throw dans le bloc de script d’une instruction if pour répondre à une condition ou dans le bloc catch d’une instruction try-catch-finally.</span><span class="sxs-lookup"><span data-stu-id="4841a-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="4841a-110">Vous pouvez également utiliser le mot clé throw dans une déclaration de paramètre pour rendre un paramètre de fonction obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4841a-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="4841a-111">Le mot clé throw peut lever n’importe quel objet, tel qu’une chaîne de message utilisateur ou l’objet qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="4841a-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="4841a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4841a-112">Syntax</span></span>

<span data-ttu-id="4841a-113">La syntaxe du mot clé throw est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4841a-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="4841a-114">L’expression dans la syntaxe Throw est facultative.</span><span class="sxs-lookup"><span data-stu-id="4841a-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="4841a-115">Lorsque l’instruction throw n’apparaît pas dans un bloc catch et qu’elle n’inclut pas d’expression, elle génère une erreur ScriptHalted.</span><span class="sxs-lookup"><span data-stu-id="4841a-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="4841a-116">Si le mot clé throw est utilisé dans un bloc catch sans expression, il lève à nouveau le RuntimeException actuel.</span><span class="sxs-lookup"><span data-stu-id="4841a-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="4841a-117">Pour plus d’informations, consultez about_Try_Catch_Finally.</span><span class="sxs-lookup"><span data-stu-id="4841a-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="4841a-118">Levée d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="4841a-118">Throwing a string</span></span>

<span data-ttu-id="4841a-119">L’expression facultative dans une instruction throw peut être une chaîne, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4841a-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="4841a-120">Levée d’autres objets</span><span class="sxs-lookup"><span data-stu-id="4841a-120">Throwing other objects</span></span>

<span data-ttu-id="4841a-121">L’expression peut également être un objet qui lève l’objet qui représente le processus PowerShell, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4841a-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="4841a-122">Vous pouvez utiliser la propriété TargetObject de l’objet ErrorRecord dans la variable automatique $error pour examiner l’erreur.</span><span class="sxs-lookup"><span data-stu-id="4841a-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="4841a-123">Vous pouvez également lever un objet ErrorRecord ou une exception .NET.</span><span class="sxs-lookup"><span data-stu-id="4841a-123">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="4841a-124">L’exemple suivant utilise le mot clé throw pour lever un objet System. FormatException.</span><span class="sxs-lookup"><span data-stu-id="4841a-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="4841a-125">L’erreur résultante</span><span class="sxs-lookup"><span data-stu-id="4841a-125">The resulting error</span></span>

<span data-ttu-id="4841a-126">Le mot clé throw peut générer un objet ErrorRecord.</span><span class="sxs-lookup"><span data-stu-id="4841a-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="4841a-127">La propriété d’exception de l’objet ErrorRecord contient un objet RuntimeException.</span><span class="sxs-lookup"><span data-stu-id="4841a-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="4841a-128">Le reste de l’objet ErrorRecord et l’objet RuntimeException varient avec l’objet que le mot clé throw lève.</span><span class="sxs-lookup"><span data-stu-id="4841a-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="4841a-129">L’objet RunTimeException est encapsulé dans un objet ErrorRecord, et l’objet ErrorRecord est automatiquement enregistré dans la variable automatique $Error.</span><span class="sxs-lookup"><span data-stu-id="4841a-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="4841a-130">Utilisation de Throw pour créer un paramètre obligatoire</span><span class="sxs-lookup"><span data-stu-id="4841a-130">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="4841a-131">Contrairement aux versions précédentes de PowerShell, n’utilisez pas le mot clé throw pour la validation des paramètres.</span><span class="sxs-lookup"><span data-stu-id="4841a-131">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="4841a-132">Consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) pour obtenir la bonne méthode.</span><span class="sxs-lookup"><span data-stu-id="4841a-132">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="4841a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4841a-133">See also</span></span>

- [<span data-ttu-id="4841a-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="4841a-134">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="4841a-135">about_Continue</span><span class="sxs-lookup"><span data-stu-id="4841a-135">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="4841a-136">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="4841a-136">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="4841a-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="4841a-137">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="4841a-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="4841a-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

---
description: Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598759"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="44853-103">À propos des fonctions avancées</span><span class="sxs-lookup"><span data-stu-id="44853-103">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="44853-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="44853-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="44853-105">Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.</span><span class="sxs-lookup"><span data-stu-id="44853-105">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="44853-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="44853-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="44853-107">Une applet de commande est une commande unique qui participe à la sémantique de pipeline de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44853-107">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="44853-108">Cela comprend les applets de commande binaires, les fonctions de script avancées, le CDXML et les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="44853-108">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="44853-109">Les fonctions avancées vous permettent de créer des applets de commande qui sont écrites en tant que fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44853-109">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="44853-110">Les fonctions avancées facilitent la création d’applets de commande sans avoir à écrire et compiler une applet de commande binaire.</span><span class="sxs-lookup"><span data-stu-id="44853-110">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="44853-111">Les applets de commande binaires sont des classes .NET qui sont écrites dans un langage .NET tel que C#.</span><span class="sxs-lookup"><span data-stu-id="44853-111">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="44853-112">Les fonctions avancées utilisent l' `CmdletBinding` attribut pour les identifier en tant que fonctions qui agissent comme des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="44853-112">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="44853-113">L' `CmdletBinding` attribut est semblable à l’attribut d’applet de commande utilisé dans les classes d’applet de commande compilées pour identifier la classe en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="44853-113">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="44853-114">Pour plus d’informations sur cet attribut, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="44853-114">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="44853-115">L’exemple suivant montre une fonction qui accepte un nom, puis imprime un message d’accueil à l’aide du nom fourni.</span><span class="sxs-lookup"><span data-stu-id="44853-115">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="44853-116">Notez également que cette fonction définit un nom qui comprend une paire verbe (envoi) et substantif (salutation) comme la paire verbe-substantif d’une applet de commande compilée.</span><span class="sxs-lookup"><span data-stu-id="44853-116">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="44853-117">Toutefois, il n’est pas nécessaire que les fonctions aient un nom de verbe-substantif.</span><span class="sxs-lookup"><span data-stu-id="44853-117">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="44853-118">Les paramètres de la fonction sont déclarés à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="44853-118">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="44853-119">Cet attribut peut être utilisé seul ou il peut être combiné avec l’attribut alias ou avec plusieurs autres attributs de validation de paramètre.</span><span class="sxs-lookup"><span data-stu-id="44853-119">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="44853-120">Pour plus d’informations sur la façon de déclarer des paramètres (y compris des paramètres dynamiques ajoutés au moment de l’exécution), consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="44853-120">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="44853-121">Le travail réel de la fonction précédente est effectué dans le bloc Process, qui est l’équivalent de la méthode ProcessingRecord utilisée par les applets de commande compilées pour traiter les données transmises à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="44853-121">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="44853-122">Ce bloc, ainsi que les blocs de début et de fin, sont décrits dans la rubrique [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) .</span><span class="sxs-lookup"><span data-stu-id="44853-122">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="44853-123">Les fonctions avancées diffèrent des applets de commande compilées des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="44853-123">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="44853-124">La liaison de paramètre de fonction avancée ne lève pas d’exception lorsqu’un tableau de chaînes est lié à un paramètre booléen.</span><span class="sxs-lookup"><span data-stu-id="44853-124">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="44853-125">L’attribut ValidateSet et l’attribut ValidatePattern ne peuvent pas passer de paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="44853-125">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="44853-126">Les fonctions avancées ne peuvent pas être utilisées dans les transactions.</span><span class="sxs-lookup"><span data-stu-id="44853-126">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="44853-127">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="44853-127">SEE ALSO</span></span>

[<span data-ttu-id="44853-128">about_Functions</span><span class="sxs-lookup"><span data-stu-id="44853-128">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="44853-129">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="44853-129">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="44853-130">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="44853-130">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="44853-131">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="44853-131">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="44853-132">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="44853-132">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

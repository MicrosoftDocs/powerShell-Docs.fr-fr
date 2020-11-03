---
description: Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: f7e100122169b3ecb25be4d32fc72a67fea7b7cf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207090"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="331ab-104">À propos des fonctions avancées</span><span class="sxs-lookup"><span data-stu-id="331ab-104">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="331ab-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="331ab-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="331ab-106">Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.</span><span class="sxs-lookup"><span data-stu-id="331ab-106">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="331ab-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="331ab-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="331ab-108">Une applet de commande est une commande unique qui participe à la sémantique de pipeline de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="331ab-108">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="331ab-109">Cela comprend les applets de commande binaires, les fonctions de script avancées, le CDXML et les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="331ab-109">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="331ab-110">Les fonctions avancées vous permettent de créer des applets de commande qui sont écrites en tant que fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="331ab-110">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="331ab-111">Les fonctions avancées facilitent la création d’applets de commande sans avoir à écrire et compiler une applet de commande binaire.</span><span class="sxs-lookup"><span data-stu-id="331ab-111">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="331ab-112">Les applets de commande binaires sont des classes .NET qui sont écrites dans un langage .NET tel que C#.</span><span class="sxs-lookup"><span data-stu-id="331ab-112">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="331ab-113">Les fonctions avancées utilisent l' `CmdletBinding` attribut pour les identifier en tant que fonctions qui agissent comme des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="331ab-113">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="331ab-114">L' `CmdletBinding` attribut est semblable à l’attribut d’applet de commande utilisé dans les classes d’applet de commande compilées pour identifier la classe en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="331ab-114">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="331ab-115">Pour plus d’informations sur cet attribut, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="331ab-115">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="331ab-116">L’exemple suivant montre une fonction qui accepte un nom, puis imprime un message d’accueil à l’aide du nom fourni.</span><span class="sxs-lookup"><span data-stu-id="331ab-116">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="331ab-117">Notez également que cette fonction définit un nom qui comprend une paire verbe (envoi) et substantif (salutation) comme la paire verbe-substantif d’une applet de commande compilée.</span><span class="sxs-lookup"><span data-stu-id="331ab-117">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="331ab-118">Toutefois, il n’est pas nécessaire que les fonctions aient un nom de verbe-substantif.</span><span class="sxs-lookup"><span data-stu-id="331ab-118">However, functions are not required to have a verb-noun name.</span></span>

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

<span data-ttu-id="331ab-119">Les paramètres de la fonction sont déclarés à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="331ab-119">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="331ab-120">Cet attribut peut être utilisé seul ou il peut être combiné avec l’attribut alias ou avec plusieurs autres attributs de validation de paramètre.</span><span class="sxs-lookup"><span data-stu-id="331ab-120">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="331ab-121">Pour plus d’informations sur la façon de déclarer des paramètres (y compris des paramètres dynamiques ajoutés au moment de l’exécution), consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="331ab-121">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="331ab-122">Le travail réel de la fonction précédente est effectué dans le bloc Process, qui est l’équivalent de la méthode ProcessingRecord utilisée par les applets de commande compilées pour traiter les données transmises à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="331ab-122">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="331ab-123">Ce bloc, ainsi que les blocs de début et de fin, sont décrits dans la rubrique [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) .</span><span class="sxs-lookup"><span data-stu-id="331ab-123">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="331ab-124">Les fonctions avancées diffèrent des applets de commande compilées des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="331ab-124">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="331ab-125">La liaison de paramètre de fonction avancée ne lève pas d’exception lorsqu’un tableau de chaînes est lié à un paramètre booléen.</span><span class="sxs-lookup"><span data-stu-id="331ab-125">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="331ab-126">L’attribut ValidateSet et l’attribut ValidatePattern ne peuvent pas passer de paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="331ab-126">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="331ab-127">Les fonctions avancées ne peuvent pas être utilisées dans les transactions.</span><span class="sxs-lookup"><span data-stu-id="331ab-127">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="331ab-128">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="331ab-128">SEE ALSO</span></span>

[<span data-ttu-id="331ab-129">about_Functions</span><span class="sxs-lookup"><span data-stu-id="331ab-129">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="331ab-130">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="331ab-130">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="331ab-131">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="331ab-131">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="331ab-132">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="331ab-132">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="331ab-133">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="331ab-133">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

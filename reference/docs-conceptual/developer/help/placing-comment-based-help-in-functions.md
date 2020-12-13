---
ms.date: 09/12/2016
ms.topic: reference
title: Mise en place de l’aide basée sur les commentaires dans les fonctions
description: Mise en place de l’aide basée sur les commentaires dans les fonctions
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658206"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="ef16f-103">Mise en place de l’aide basée sur les commentaires dans les fonctions</span><span class="sxs-lookup"><span data-stu-id="ef16f-103">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="ef16f-104">Cette rubrique explique où placer l’aide basée sur des commentaires pour une fonction afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur les commentaires à la fonction correcte.</span><span class="sxs-lookup"><span data-stu-id="ef16f-104">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="ef16f-105">Où placer Comment-Based aide pour une fonction</span><span class="sxs-lookup"><span data-stu-id="ef16f-105">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="ef16f-106">Au début du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-106">At the beginning of the function body.</span></span>

- <span data-ttu-id="ef16f-107">À la fin du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-107">At the end of the function body.</span></span>

- <span data-ttu-id="ef16f-108">Avant le `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="ef16f-108">Before the `Function` keyword.</span></span> <span data-ttu-id="ef16f-109">Lorsque la fonction se trouve dans un script ou un module de script, il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide basée sur les commentaires et le `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="ef16f-109">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="ef16f-110">Sinon, `Get-Help` associe l’aide au script, et non à la fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-110">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="ef16f-111">Exemples de placement d’aide dans une fonction</span><span class="sxs-lookup"><span data-stu-id="ef16f-111">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="ef16f-112">Les exemples suivants montrent chacune des trois options de placement pour une aide basée sur des commentaires pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-112">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="ef16f-113">Aide au début du corps d’une fonction</span><span class="sxs-lookup"><span data-stu-id="ef16f-113">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="ef16f-114">L’exemple suivant illustre la base de commentaires au début d’un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-114">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell
function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}
```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="ef16f-115">Aide à la fin du corps d’une fonction</span><span class="sxs-lookup"><span data-stu-id="ef16f-115">Help at the End of a Function Body</span></span>

 <span data-ttu-id="ef16f-116">L’exemple suivant illustre la base de commentaires à la fin d’un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="ef16f-116">The following example shows comment-based at the end of a function body.</span></span>

```powershell
function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}
```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="ef16f-117">Aide avant le mot clé function</span><span class="sxs-lookup"><span data-stu-id="ef16f-117">Help Before the Function Keyword</span></span>

 <span data-ttu-id="ef16f-118">Les exemples suivants illustrent les commentaires basés sur la ligne précédant le mot clé function.</span><span class="sxs-lookup"><span data-stu-id="ef16f-118">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```

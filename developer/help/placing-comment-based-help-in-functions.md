---
title: Placer l’aide basée sur un commentaire dans les fonctions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857945"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="a4dbe-102">Mise en place de l’aide basée sur les commentaires dans les fonctions</span><span class="sxs-lookup"><span data-stu-id="a4dbe-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="a4dbe-103">Cette rubrique explique où placer aide basée sur une fonction afin que le `Get-Help` applet de commande associe la rubrique d’aide en fonction du commentaire à la fonction correcte.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="a4dbe-104">Où placer l’aide basée sur une fonction</span><span class="sxs-lookup"><span data-stu-id="a4dbe-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="a4dbe-105">Au début du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="a4dbe-106">À la fin du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-106">At the end of the function body.</span></span>

- <span data-ttu-id="a4dbe-107">Avant du `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-107">Before the `Function` keyword.</span></span> <span data-ttu-id="a4dbe-108">Lorsque la fonction est dans un script ou d’un module de script, il ne peut pas être plus d’une ligne vide entre la dernière ligne de l’aide de commentaire et le `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="a4dbe-109">Sinon, `Get-Help` associe l’aide avec le script, et non avec la fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="a4dbe-110">Exemples de sélection élective d’aide dans une fonction</span><span class="sxs-lookup"><span data-stu-id="a4dbe-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="a4dbe-111">Les exemples suivants montrent chacun des options trois positionnement pour l’aide basée sur une fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="a4dbe-112">Aide au début du corps d’une fonction</span><span class="sxs-lookup"><span data-stu-id="a4dbe-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="a4dbe-113">L’exemple suivant montre les commentaires au début du corps d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="a4dbe-114">Aide à la fin d’un corps de fonction</span><span class="sxs-lookup"><span data-stu-id="a4dbe-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="a4dbe-115">L’exemple suivant montre en fonction de commentaire à la fin d’un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="a4dbe-116">Aide avant le mot clé (fonction)</span><span class="sxs-lookup"><span data-stu-id="a4dbe-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="a4dbe-117">Les exemples suivants montrent des commentaires sur la ligne avant le mot clé function.</span><span class="sxs-lookup"><span data-stu-id="a4dbe-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```
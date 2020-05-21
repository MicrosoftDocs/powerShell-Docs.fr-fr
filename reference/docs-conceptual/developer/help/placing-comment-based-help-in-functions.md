---
title: Placement de l’aide basée sur des commentaires dans les fonctions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: 898225a582c7ed25f746dec7f84012db1ae60b98
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557060"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="349ef-102">Mise en place de l’aide basée sur les commentaires dans les fonctions</span><span class="sxs-lookup"><span data-stu-id="349ef-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="349ef-103">Cette rubrique explique où placer l’aide basée sur des commentaires pour une fonction afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur les commentaires à la fonction correcte.</span><span class="sxs-lookup"><span data-stu-id="349ef-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="349ef-104">Où placer l’aide basée sur les commentaires pour une fonction</span><span class="sxs-lookup"><span data-stu-id="349ef-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="349ef-105">Au début du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="349ef-106">À la fin du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-106">At the end of the function body.</span></span>

- <span data-ttu-id="349ef-107">Avant le `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="349ef-107">Before the `Function` keyword.</span></span> <span data-ttu-id="349ef-108">Lorsque la fonction se trouve dans un script ou un module de script, il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide basée sur les commentaires et le `Function` mot clé.</span><span class="sxs-lookup"><span data-stu-id="349ef-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="349ef-109">Sinon, `Get-Help` associe l’aide au script, et non à la fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="349ef-110">Exemples de placement d’aide dans une fonction</span><span class="sxs-lookup"><span data-stu-id="349ef-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="349ef-111">Les exemples suivants montrent chacune des trois options de placement pour une aide basée sur des commentaires pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="349ef-112">Aide au début du corps d’une fonction</span><span class="sxs-lookup"><span data-stu-id="349ef-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="349ef-113">L’exemple suivant illustre la base de commentaires au début d’un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="349ef-114">Aide à la fin du corps d’une fonction</span><span class="sxs-lookup"><span data-stu-id="349ef-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="349ef-115">L’exemple suivant illustre la base de commentaires à la fin d’un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="349ef-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="349ef-116">Aide avant le mot clé function</span><span class="sxs-lookup"><span data-stu-id="349ef-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="349ef-117">Les exemples suivants illustrent les commentaires basés sur la ligne précédant le mot clé function.</span><span class="sxs-lookup"><span data-stu-id="349ef-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```

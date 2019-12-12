---
title: Placement de l’aide basée sur des commentaires dans des scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361178"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="bba16-102">Mise en place de l’aide basée sur les commentaires dans les scripts</span><span class="sxs-lookup"><span data-stu-id="bba16-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="bba16-103">Cette rubrique explique où placer l’aide basée sur les commentaires pour un script afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur des commentaires à des scripts et non à des fonctions qui peuvent être dans le script.</span><span class="sxs-lookup"><span data-stu-id="bba16-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="bba16-104">Où placer l’aide basée sur les commentaires pour un script</span><span class="sxs-lookup"><span data-stu-id="bba16-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="bba16-105">Au début du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="bba16-105">At the beginning of the script file.</span></span> <span data-ttu-id="bba16-106">L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.</span><span class="sxs-lookup"><span data-stu-id="bba16-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="bba16-107">À la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="bba16-107">At the end of the script file.</span></span>

  <span data-ttu-id="bba16-108">Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction.</span><span class="sxs-lookup"><span data-stu-id="bba16-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="bba16-109">Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.</span><span class="sxs-lookup"><span data-stu-id="bba16-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="bba16-110">Exemples de placement d’aide dans un script</span><span class="sxs-lookup"><span data-stu-id="bba16-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="bba16-111">Les exemples suivants montrent chacune des options de positionnement pour l’aide basée sur des commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="bba16-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="bba16-112">Aide au début d’un script</span><span class="sxs-lookup"><span data-stu-id="bba16-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="bba16-113">L’exemple suivant illustre la base de commentaires au début d’un script.</span><span class="sxs-lookup"><span data-stu-id="bba16-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="bba16-114">Aide à la fin d’un script</span><span class="sxs-lookup"><span data-stu-id="bba16-114">Help at the End of a Script</span></span>

 <span data-ttu-id="bba16-115">L’exemple suivant illustre la base de commentaires à la fin d’un script.</span><span class="sxs-lookup"><span data-stu-id="bba16-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```
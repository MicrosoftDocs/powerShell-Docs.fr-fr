---
title: Placer l’aide basée sur les commentaires dans les Scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860765"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="cc00f-102">Mise en place de l’aide basée sur les commentaires dans les scripts</span><span class="sxs-lookup"><span data-stu-id="cc00f-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="cc00f-103">Cette rubrique explique où placer aide basée sur un script afin que le `Get-Help` applet de commande associe la rubrique d’aide en fonction du commentaire avec des scripts et pas avec toutes les fonctions qui peuvent être dans le script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="cc00f-104">Où placer l’aide basée sur un Script</span><span class="sxs-lookup"><span data-stu-id="cc00f-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="cc00f-105">Au début du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-105">At the beginning of the script file.</span></span> <span data-ttu-id="cc00f-106">Aide du script peut être précédée dans le script uniquement les lignes vides et les commentaires.</span><span class="sxs-lookup"><span data-stu-id="cc00f-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="cc00f-107">À la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-107">At the end of the script file.</span></span>

  <span data-ttu-id="cc00f-108">Si le premier élément dans le corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide sur le script et la déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="cc00f-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="cc00f-109">Sinon, l’aide est considérée comme étant aide à l’aide de la fonction, pas pour le script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="cc00f-110">Exemples de sélection élective d’aide dans un Script</span><span class="sxs-lookup"><span data-stu-id="cc00f-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="cc00f-111">Les exemples suivants montrent chacun des options de sélection élective de l’aide de commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="cc00f-112">Aide au début d’un Script</span><span class="sxs-lookup"><span data-stu-id="cc00f-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="cc00f-113">L’exemple suivant montre des commentaires au début d’un script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="cc00f-114">Aide à la fin d’un Script</span><span class="sxs-lookup"><span data-stu-id="cc00f-114">Help at the End of a Script</span></span>

 <span data-ttu-id="cc00f-115">L’exemple suivant montre en fonction de commentaire à la fin d’un script.</span><span class="sxs-lookup"><span data-stu-id="cc00f-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```
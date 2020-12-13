---
ms.date: 09/12/2016
ms.topic: reference
title: Mise en place de l’aide basée sur les commentaires dans les scripts
description: Mise en place de l’aide basée sur les commentaires dans les scripts
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645446"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="aebb5-103">Mise en place de l’aide basée sur les commentaires dans les scripts</span><span class="sxs-lookup"><span data-stu-id="aebb5-103">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="aebb5-104">Cette rubrique explique où placer l’aide basée sur les commentaires pour un script afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur des commentaires à des scripts et non à des fonctions qui peuvent être dans le script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-104">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="aebb5-105">Où placer Comment-Based aide pour un script</span><span class="sxs-lookup"><span data-stu-id="aebb5-105">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="aebb5-106">Au début du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-106">At the beginning of the script file.</span></span>

  <span data-ttu-id="aebb5-107">L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.</span><span class="sxs-lookup"><span data-stu-id="aebb5-107">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="aebb5-108">À la fin du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-108">At the end of the script file.</span></span>

  <span data-ttu-id="aebb5-109">Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction.</span><span class="sxs-lookup"><span data-stu-id="aebb5-109">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="aebb5-110">Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-110">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="aebb5-111">Exemples de placement d’aide dans un script</span><span class="sxs-lookup"><span data-stu-id="aebb5-111">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="aebb5-112">Les exemples suivants montrent chacune des options de positionnement pour l’aide basée sur des commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-112">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="aebb5-113">Aide au début d’un script</span><span class="sxs-lookup"><span data-stu-id="aebb5-113">Help at the Beginning of a Script</span></span>

<span data-ttu-id="aebb5-114">L’exemple suivant illustre la base de commentaires au début d’un script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-114">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="aebb5-115">Aide à la fin d’un script</span><span class="sxs-lookup"><span data-stu-id="aebb5-115">Help at the End of a Script</span></span>

 <span data-ttu-id="aebb5-116">L’exemple suivant illustre la base de commentaires à la fin d’un script.</span><span class="sxs-lookup"><span data-stu-id="aebb5-116">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```

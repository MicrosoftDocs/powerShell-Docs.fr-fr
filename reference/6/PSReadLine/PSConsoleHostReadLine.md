---
external help file: PSReadLine-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 339c1b0c4f241c243e7c526f3353a614c3bfd6d2
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208729"
---
# <span data-ttu-id="52549-103">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="52549-103">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="52549-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="52549-104">SYNOPSIS</span></span>
<span data-ttu-id="52549-105">Cette fonction est le point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="52549-105">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="52549-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52549-106">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="52549-107">Description</span><span class="sxs-lookup"><span data-stu-id="52549-107">DESCRIPTION</span></span>

<span data-ttu-id="52549-108">`PSConsoleHostReadLine` est le point d’entrée principal pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="52549-108">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="52549-109">L’hôte de la console PowerShell charge automatiquement le module PSReadLine et appelle cette fonction.</span><span class="sxs-lookup"><span data-stu-id="52549-109">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="52549-110">Dans des conditions de fonctionnement normales, cette fonction n’est pas destinée à être utilisée à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="52549-110">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="52549-111">Le point `PSConsoleHostReadLine` d’extension est spécial pour l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="52549-111">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="52549-112">L’hôte appelle un alias, une fonction ou un script portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="52549-112">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="52549-113">PSReadLine définit cette fonction de manière à ce qu’elle soit appelée à partir de l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="52549-113">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="52549-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="52549-114">EXAMPLES</span></span>

### <span data-ttu-id="52549-115">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="52549-115">Example 1</span></span>

<span data-ttu-id="52549-116">Cette fonction n’est pas destinée à être utilisée à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="52549-116">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="52549-117">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="52549-117">PARAMETERS</span></span>

## <span data-ttu-id="52549-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="52549-118">INPUTS</span></span>

### <span data-ttu-id="52549-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="52549-119">None</span></span>

## <span data-ttu-id="52549-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="52549-120">OUTPUTS</span></span>

### <span data-ttu-id="52549-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="52549-121">None</span></span>

## <span data-ttu-id="52549-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="52549-122">NOTES</span></span>

## <span data-ttu-id="52549-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="52549-123">RELATED LINKS</span></span>

[<span data-ttu-id="52549-124">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="52549-124">about_PSReadLine</span></span>](./About/about_PSReadLine.md)
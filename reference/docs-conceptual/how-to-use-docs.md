---
ms.date: 09/25/2019
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281655"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="52633-103">Guide pratique pour utiliser la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="52633-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="52633-104">Bienvenue dans la documentation en ligne de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52633-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="52633-105">Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="52633-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="52633-106">PowerShell 7 (préversion)</span><span class="sxs-lookup"><span data-stu-id="52633-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="52633-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="52633-107">PowerShell 6</span></span>
- <span data-ttu-id="52633-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="52633-108">PowerShell 5.1</span></span>
- <span data-ttu-id="52633-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="52633-109">PowerShell 5.0</span></span>
- <span data-ttu-id="52633-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="52633-110">PowerShell 4.0</span></span>
- <span data-ttu-id="52633-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="52633-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="52633-112">Sélection de votre version</span><span class="sxs-lookup"><span data-stu-id="52633-112">Selecting your version</span></span>

<span data-ttu-id="52633-113">Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52633-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="52633-114">Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre.</span><span class="sxs-lookup"><span data-stu-id="52633-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="52633-115">Veillez à consulter la documentation de la version de PowerShell que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="52633-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="52633-116">Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52633-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![sélecteur de version](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="52633-118">Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="52633-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="52633-119">L’exemple suivant montre la sortie pour Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="52633-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="52633-120">Recherche d’articles</span><span class="sxs-lookup"><span data-stu-id="52633-120">Searching for articles</span></span>

<span data-ttu-id="52633-121">Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version.</span><span class="sxs-lookup"><span data-stu-id="52633-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="52633-122">Il vous suffit d’entrer un mot qui figure dans le titre d’un article.</span><span class="sxs-lookup"><span data-stu-id="52633-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="52633-123">La page affiche une liste d’articles correspondants.</span><span class="sxs-lookup"><span data-stu-id="52633-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="52633-124">Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.</span><span class="sxs-lookup"><span data-stu-id="52633-124">You can also select the option to search the entire site from that list.</span></span>

![zone de filtre](images/how-to-use-docs/filter-search.gif)

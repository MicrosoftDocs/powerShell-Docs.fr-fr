---
ms.date: 07/29/2020
keywords: powershell,applet de commande
ms.topic: how-to
title: Guide pratique pour utiliser la documentation PowerShell
description: Cet article explique comment utiliser les fonctionnalités de ce site, notamment le filtrage des recherches et la sélection de version.
ms.openlocfilehash: 4779e6e4b17c461d71e9d613d1184b9ce2e7ab7b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216080"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="c76de-104">Guide pratique pour utiliser la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="c76de-104">How to use the PowerShell documentation</span></span>

<span data-ttu-id="c76de-105">Bienvenue dans la documentation en ligne de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c76de-105">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="c76de-106">Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c76de-106">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="c76de-107">PowerShell 7.2 (préversion)</span><span class="sxs-lookup"><span data-stu-id="c76de-107">PowerShell 7.2 (prerelease)</span></span>
- <span data-ttu-id="c76de-108">PowerShell 7.1 (actuel)</span><span class="sxs-lookup"><span data-stu-id="c76de-108">PowerShell 7.1 (current)</span></span>
- <span data-ttu-id="c76de-109">PowerShell 7.0 (LTS)</span><span class="sxs-lookup"><span data-stu-id="c76de-109">PowerShell 7.0 (LTS)</span></span>
- <span data-ttu-id="c76de-110">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c76de-110">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="c76de-111">Recherche d’articles et sélection de version</span><span class="sxs-lookup"><span data-stu-id="c76de-111">Finding articles and selecting a version</span></span>

<span data-ttu-id="c76de-112">Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version.</span><span class="sxs-lookup"><span data-stu-id="c76de-112">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="c76de-113">Il vous suffit d’entrer un mot qui figure dans le titre d’un article.</span><span class="sxs-lookup"><span data-stu-id="c76de-113">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="c76de-114">La page affiche une liste d’articles correspondants.</span><span class="sxs-lookup"><span data-stu-id="c76de-114">The page displays a list of matching articles.</span></span> <span data-ttu-id="c76de-115">Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.</span><span class="sxs-lookup"><span data-stu-id="c76de-115">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="c76de-116">Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c76de-116">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="c76de-117">Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre.</span><span class="sxs-lookup"><span data-stu-id="c76de-117">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="c76de-118">Veillez à consulter la documentation de la version de PowerShell que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="c76de-118">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="c76de-119">Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c76de-119">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Utilisation du sélecteur de version](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="c76de-121">Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="c76de-121">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="c76de-122">L’exemple suivant montre la sortie pour Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="c76de-122">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="c76de-123">Si vous débutez avec PowerShell et avez besoin d’aide pour comprendre la syntaxe des commandes, consultez [À propos de la syntaxe des commandes](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span><span class="sxs-lookup"><span data-stu-id="c76de-123">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="c76de-124">Recherche d’articles pour les versions précédentes</span><span class="sxs-lookup"><span data-stu-id="c76de-124">Finding articles for previous versions</span></span>

<span data-ttu-id="c76de-125">La documentation des versions antérieures de PowerShell a été archivée dans notre site [Versions précédentes](https://aka.ms/PSLegacyDocs).</span><span class="sxs-lookup"><span data-stu-id="c76de-125">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="c76de-126">Ce site contient la documentation pour les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c76de-126">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="c76de-127">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c76de-127">PowerShell 3.0</span></span>
- <span data-ttu-id="c76de-128">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="c76de-128">PowerShell 4.0</span></span>
- <span data-ttu-id="c76de-129">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c76de-129">PowerShell 5.0</span></span>
- <span data-ttu-id="c76de-130">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c76de-130">PowerShell 6</span></span>
- <span data-ttu-id="c76de-131">Flux de travail PowerShell</span><span class="sxs-lookup"><span data-stu-id="c76de-131">PowerShell Workflows</span></span>
- <span data-ttu-id="c76de-132">Accès web PowerShell</span><span class="sxs-lookup"><span data-stu-id="c76de-132">PowerShell Web Access</span></span>

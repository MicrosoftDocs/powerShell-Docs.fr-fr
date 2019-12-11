---
ms.date: 10/20/2019
keywords: powershell,applet de commande
title: Guide pratique pour utiliser la documentation PowerShell
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72676159"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="30e60-103">Guide pratique pour utiliser la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="30e60-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="30e60-104">Bienvenue dans la documentation en ligne de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30e60-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="30e60-105">Ce site contient des informations de référence sur les applets de commande des versions suivantes de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="30e60-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="30e60-106">PowerShell 7 (préversion)</span><span class="sxs-lookup"><span data-stu-id="30e60-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="30e60-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="30e60-107">PowerShell 6</span></span>
- <span data-ttu-id="30e60-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="30e60-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="30e60-109">Recherche d’articles et sélection de version</span><span class="sxs-lookup"><span data-stu-id="30e60-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="30e60-110">Il existe deux façons de rechercher du contenu dans la documentation. Le plus simple est d’utiliser la zone de filtre située en dessous du sélecteur de version.</span><span class="sxs-lookup"><span data-stu-id="30e60-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="30e60-111">Il vous suffit d’entrer un mot qui figure dans le titre d’un article.</span><span class="sxs-lookup"><span data-stu-id="30e60-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="30e60-112">La page affiche une liste d’articles correspondants.</span><span class="sxs-lookup"><span data-stu-id="30e60-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="30e60-113">Vous pouvez aussi sélectionner l’option permettant d’effectuer une recherche sur tout le site à partir de cette liste.</span><span class="sxs-lookup"><span data-stu-id="30e60-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="30e60-114">Par défaut, ce site affiche la documentation de la dernière version publiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30e60-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="30e60-115">Certaines applets de commande fonctionnent différemment d’une version de PowerShell à l’autre.</span><span class="sxs-lookup"><span data-stu-id="30e60-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="30e60-116">Veillez à consulter la documentation de la version de PowerShell que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="30e60-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="30e60-117">Utilisez le sélecteur de version en haut de la page pour sélectionner la version souhaitée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30e60-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![sélecteur de version](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="30e60-119">Vous pouvez vérifier la version de PowerShell que vous utilisez en inspectant la valeur `$PSversionTable.PSVersion`.</span><span class="sxs-lookup"><span data-stu-id="30e60-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="30e60-120">L’exemple suivant montre la sortie pour Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="30e60-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

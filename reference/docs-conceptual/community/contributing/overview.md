---
title: Contribution à la documentation de PowerShell
description: Cet article explique dans les grandes lignes comment bien démarrer en tant que contributeur de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3ea08c3acf4a31cbb7262aac57bf28b75388275d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158154"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="e0ef0-103">Contribution à la documentation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0ef0-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="e0ef0-104">Nous vous remercions de contribuer à la documentation de PowerShell !</span><span class="sxs-lookup"><span data-stu-id="e0ef0-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="e0ef0-105">Le Guide du contributeur est un ensemble d’articles qui expliquent les outils et les processus que nous utilisons pour créer la documentation de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="e0ef0-106">Certains de ces guides comportent des informations communes à tous les ensembles de documentation publiés sur [docs.microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="e0ef0-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="e0ef0-107">D’autres sont propres à la rédaction de la documentation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="e0ef0-108">Les articles communs sont disponibles dans notre [Guide du contributeur][contribute] centralisé.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="e0ef0-109">Les guides propres à PowerShell sont disponibles ici.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="e0ef0-110">Comment contribuer ?</span><span class="sxs-lookup"><span data-stu-id="e0ef0-110">Ways to contribute</span></span>

<span data-ttu-id="e0ef0-111">Il existe deux manières d’apporter sa contribution.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-111">There are two ways to contribute.</span></span> <span data-ttu-id="e0ef0-112">Les deux nous sont utiles.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="e0ef0-113">Les [problèmes][file-an-issue] nous aident à identifier les points problématiques et les lacunes de notre documentation.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="e0ef0-114">Certains sont difficiles à résoudre et demandent davantage d’investigation et de recherches.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="e0ef0-115">Le processus nous permet d’échanger au sujet du problème et d’y apporter une solution satisfaisante.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="e0ef0-116">Envoyer de nouveaux contenus ou des modifications d’articles existants dans la documentation représente un processus plus complexe.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="e0ef0-117">Ci-dessous sont détaillés les outils, les processus et les normes à suivre.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="e0ef0-118">Préparation de la contribution</span><span class="sxs-lookup"><span data-stu-id="e0ef0-118">Prepare to make a contribution</span></span>

<span data-ttu-id="e0ef0-119">Vous devez avoir un compte GitHub.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="e0ef0-120">Référez-vous à la liste de contrôle ci-dessous pour connaître les outils et comprendre les processus que nous suivons pour effectuer des contributions.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. <span data-ttu-id="e0ef0-121">[Inscrivez-vous à GitHub](/contribute/get-started-setup-github).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-121">[Sign up for GitHub](/contribute/get-started-setup-github)</span></span>
1. <span data-ttu-id="e0ef0-122">[Installez les outils Git et Markdown](/contribute/get-started-setup-tools).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-122">[Install Git and Markdown tools](/contribute/get-started-setup-tools)</span></span>
1. <span data-ttu-id="e0ef0-123">[Installez Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-123">[Install the Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack)</span></span>
1. <span data-ttu-id="e0ef0-124">[Installez Posh-Git][posh-git] (non obligatoire, mais recommandé).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. <span data-ttu-id="e0ef0-125">[Configurez un référentiel Git local](/contribute/get-started-setup-local).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-125">[Set up a local Git repository](/contribute/get-started-setup-local)</span></span>
1. <span data-ttu-id="e0ef0-126">[Consultez les notions de base de Git et de GitHub](/contribute/git-github-fundamentals).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-126">[Review Git and GitHub fundamentals](/contribute/git-github-fundamentals)</span></span>

## <a name="get-started-writing-docs"></a><span data-ttu-id="e0ef0-127">Commencer à écrire de la documentation</span><span class="sxs-lookup"><span data-stu-id="e0ef0-127">Get started writing docs</span></span>

<span data-ttu-id="e0ef0-128">Il existe deux façons de contribuer aux modifications de la documentation :</span><span class="sxs-lookup"><span data-stu-id="e0ef0-128">There are two ways to contribute changes to the documentation:</span></span>

1. <span data-ttu-id="e0ef0-129">[Modification rapide de documents existants](/contribute/#quick-edits-to-existing-documents) :</span><span class="sxs-lookup"><span data-stu-id="e0ef0-129">[Quick edits to existing docs](/contribute/#quick-edits-to-existing-documents)</span></span>
   - <span data-ttu-id="e0ef0-130">Corrections mineures, correction de fautes de frappe ou petits ajouts.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-130">Minor corrections, fixing typos, or small additions</span></span>
1. <span data-ttu-id="e0ef0-131">[Flux de travail GitHub complet pour Docs](/contribute/how-to-write-workflows-major) :</span><span class="sxs-lookup"><span data-stu-id="e0ef0-131">[Full GitHub workflow for docs](/contribute/how-to-write-workflows-major)</span></span>
   - <span data-ttu-id="e0ef0-132">Modifications importantes, versions multiples, ajout ou modification d’images ou contribution à de nouveaux articles.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="e0ef0-133">Lisez également la section [Notions de base de la rédaction](/contribute/style-quick-start) du Guide du contributeur centralisé.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="e0ef0-134">Une autre excellente ressource est le [Guide de style de rédaction Microsoft][style-guide].</span><span class="sxs-lookup"><span data-stu-id="e0ef0-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="e0ef0-135">L’objectif de ce guide est d’aider les éditeurs, les rédacteurs techniques, les développeurs, les responsables marketing et tous les autres professionnels des technologies de l’information à écrire du contenu de meilleure qualité.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="e0ef0-136">Les corrections mineures et clarifications de la documentation ainsi que les exemples de code des référentiels publics sont couverts par les [Conditions d’utilisation][terms-of-use] du site docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="e0ef0-137">Suivez le flux de travail GitHub complet lorsque vous apportez des modifications importantes.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="e0ef0-138">Si vous n’êtes pas un employé de Microsoft, les modifications significatives génèrent un commentaire dans la demande de tirage (pull request) qui vous demande de soumettre un [Contrat de licence de contribution (CLA)][cla] en ligne.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="e0ef0-139">Vous devez remplir le formulaire en ligne pour que nous puissions examiner ou accepter votre demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="e0ef0-140">Code de conduite</span><span class="sxs-lookup"><span data-stu-id="e0ef0-140">Code of conduct</span></span>

<span data-ttu-id="e0ef0-141">Tous les référentiels comportant des contenus publiés sur docs.microsoft.com ont adopté le [Code de conduite Open Source Microsoft](https://opensource.microsoft.com/codeofconduct/) ou le [Code de conduite .NET Foundation](https://dotnetfoundation.org/code-of-conduct).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="e0ef0-142">Pour plus d'informations, consultez la [FAQ du Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/).</span><span class="sxs-lookup"><span data-stu-id="e0ef0-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e0ef0-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e0ef0-143">Next steps</span></span>

<span data-ttu-id="e0ef0-144">Les articles suivants comportent des informations propres à la documentation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="e0ef0-145">En cas de conflit avec les indications du Guide du contributeur centralisé, nous précisons la façon dont ces règles diffèrent pour le contenu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0ef0-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="e0ef0-146">Consultez les documents suivants :</span><span class="sxs-lookup"><span data-stu-id="e0ef0-146">Review the following documents:</span></span>

- [<span data-ttu-id="e0ef0-147">Guide pratique pour signaler un problème</span><span class="sxs-lookup"><span data-stu-id="e0ef0-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="e0ef0-148">Bien démarrer avec la rédaction de la documentation</span><span class="sxs-lookup"><span data-stu-id="e0ef0-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="e0ef0-149">Envoi d’une demande de tirage</span><span class="sxs-lookup"><span data-stu-id="e0ef0-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="e0ef0-150">Guide de style PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="e0ef0-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="e0ef0-151">Informations de référence sur la modification des cmdlets</span><span class="sxs-lookup"><span data-stu-id="e0ef0-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="e0ef0-152">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="e0ef0-152">Additional resources</span></span>

- [<span data-ttu-id="e0ef0-153">Liste de contrôle éditoriale</span><span class="sxs-lookup"><span data-stu-id="e0ef0-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="e0ef0-154">Processus de gestion des problèmes</span><span class="sxs-lookup"><span data-stu-id="e0ef0-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="e0ef0-155">Processus de gestion des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="e0ef0-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse

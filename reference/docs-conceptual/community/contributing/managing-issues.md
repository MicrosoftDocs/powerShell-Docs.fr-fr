---
title: Processus de gestion des problèmes
description: Cet article explique comment l’équipe PowerShell-Docs gère les demandes de tirage (pull request).
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 018200f1a9384f1ea956c9b27a7605db21f2da9e
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692536"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="85a9d-103">Processus de gestion des problèmes</span><span class="sxs-lookup"><span data-stu-id="85a9d-103">How we manage issues</span></span>

<span data-ttu-id="85a9d-104">Cet article explique comment nous gérons les problèmes dans le référentiel PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="85a9d-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="85a9d-105">Cet article est conçu pour servir d’aide-mémoire aux membres de l’équipe PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="85a9d-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="85a9d-106">Il est publié ici dans un souci de transparence des processus pour nos contributeurs publics.</span><span class="sxs-lookup"><span data-stu-id="85a9d-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="85a9d-107">Sources des problèmes</span><span class="sxs-lookup"><span data-stu-id="85a9d-107">Sources of issues</span></span>

- <span data-ttu-id="85a9d-108">Contributeurs de la communauté</span><span class="sxs-lookup"><span data-stu-id="85a9d-108">Community contributors</span></span>
- <span data-ttu-id="85a9d-109">Contributeurs internes</span><span class="sxs-lookup"><span data-stu-id="85a9d-109">Internal contributors</span></span>
- <span data-ttu-id="85a9d-110">Transcriptions de commentaires provenant des réseaux sociaux</span><span class="sxs-lookup"><span data-stu-id="85a9d-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="85a9d-111">Commentaires envoyés par le biais du formulaire de commentaires sur Docs</span><span class="sxs-lookup"><span data-stu-id="85a9d-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="85a9d-112">Objectifs de temps de réponse</span><span class="sxs-lookup"><span data-stu-id="85a9d-112">Response time targets</span></span>

- <span data-ttu-id="85a9d-113">Triage : 5 jours ouvrés</span><span class="sxs-lookup"><span data-stu-id="85a9d-113">Triaged - 5 business days</span></span>
- <span data-ttu-id="85a9d-114">Correction ou modification : pas d’objectif particulier, le plus rapidement possible</span><span class="sxs-lookup"><span data-stu-id="85a9d-114">Fix or change - no specific target - best effort only</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="85a9d-115">Étiquetage et jalons</span><span class="sxs-lookup"><span data-stu-id="85a9d-115">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="85a9d-116">Types d’étiquettes</span><span class="sxs-lookup"><span data-stu-id="85a9d-116">Label Types</span></span>

|<span data-ttu-id="85a9d-117">Préfixe</span><span class="sxs-lookup"><span data-stu-id="85a9d-117">Prefix</span></span>  | <span data-ttu-id="85a9d-118">Description</span><span class="sxs-lookup"><span data-stu-id="85a9d-118">Description</span></span>                                                         |
|------- | --------------------------------------------------------------------|
|<span data-ttu-id="85a9d-119">Domaine</span><span class="sxs-lookup"><span data-stu-id="85a9d-119">Area</span></span>    | <span data-ttu-id="85a9d-120">Permet d’indiquer sur quelle partie de PowerShell ou de Docs porte le problème.</span><span class="sxs-lookup"><span data-stu-id="85a9d-120">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="85a9d-121">Utile aux propriétaires de fonctionnalités pour trouver les problèmes relatifs à leur fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="85a9d-121">Useful for feature owners to find issues for their feature.</span></span>|
|<span data-ttu-id="85a9d-122">Pri</span><span class="sxs-lookup"><span data-stu-id="85a9d-122">Pri</span></span>     | <span data-ttu-id="85a9d-123">Permet d’indiquer le niveau de priorité du problème.</span><span class="sxs-lookup"><span data-stu-id="85a9d-123">Used to indicate the priority of the issue.</span></span> <span data-ttu-id="85a9d-124">Plage de valeurs : 0-4.</span><span class="sxs-lookup"><span data-stu-id="85a9d-124">Value range 0-4.</span></span>        |
|<span data-ttu-id="85a9d-125">Problème</span><span class="sxs-lookup"><span data-stu-id="85a9d-125">Issue</span></span>   | <span data-ttu-id="85a9d-126">Permet de classer le type de commentaires relatifs au problème.</span><span class="sxs-lookup"><span data-stu-id="85a9d-126">Used to classify the type of feedback for issue</span></span>                     |
|<span data-ttu-id="85a9d-127">Révision</span><span class="sxs-lookup"><span data-stu-id="85a9d-127">Review</span></span>  | <span data-ttu-id="85a9d-128">Permet d’indiquer que le problème exige une vérification supplémentaire de la part de l’équipe.</span><span class="sxs-lookup"><span data-stu-id="85a9d-128">Used for issue that require further review by the team</span></span>              |
|<span data-ttu-id="85a9d-129">Statut</span><span class="sxs-lookup"><span data-stu-id="85a9d-129">Status</span></span>  | <span data-ttu-id="85a9d-130">Permet d’indiquer l’état de l’élément de travail.</span><span class="sxs-lookup"><span data-stu-id="85a9d-130">Used to indicate the status of the work item</span></span>                        |
|<span data-ttu-id="85a9d-131">En attente</span><span class="sxs-lookup"><span data-stu-id="85a9d-131">Waiting</span></span> | <span data-ttu-id="85a9d-132">Permet d’indiquer que nous attendons quelque chose.</span><span class="sxs-lookup"><span data-stu-id="85a9d-132">Used to indicate that we are waiting on something</span></span>                   |

#### <a name="milestones"></a><span data-ttu-id="85a9d-133">Milestones</span><span class="sxs-lookup"><span data-stu-id="85a9d-133">Milestones</span></span>

<span data-ttu-id="85a9d-134">Les problèmes et demandes de tirage doivent être marqués du jalon correspondant.</span><span class="sxs-lookup"><span data-stu-id="85a9d-134">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="85a9d-135">Si le problème ne porte pas sur une version spécifique, aucun jalon n’est utilisé.</span><span class="sxs-lookup"><span data-stu-id="85a9d-135">If the issue is not targeted for a specific version then no milestone is used.</span></span> <span data-ttu-id="85a9d-136">Les problèmes liés aux demandes de tirage Docs et portant sur des modifications qui n’ont pas encore été fusionnées dans le codebase PowerShell doivent comporter le jalon **Future** (À venir).</span><span class="sxs-lookup"><span data-stu-id="85a9d-136">Issues for Docs PRs for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="85a9d-137">Une fois la modification du code fusionnée, remplacez la valeur du jalon par la version correspondante.</span><span class="sxs-lookup"><span data-stu-id="85a9d-137">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="85a9d-138">Jalon</span><span class="sxs-lookup"><span data-stu-id="85a9d-138">Milestone</span></span>     |                    <span data-ttu-id="85a9d-139">Description</span><span class="sxs-lookup"><span data-stu-id="85a9d-139">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="85a9d-140">6.x</span><span class="sxs-lookup"><span data-stu-id="85a9d-140">6.x</span></span>              | <span data-ttu-id="85a9d-141">Éléments de travail entre la version 6.0 et la version 6.2.x de PowerShell</span><span class="sxs-lookup"><span data-stu-id="85a9d-141">Work items related to PowerShell 6.0 through 6.2.x</span></span> |
| <span data-ttu-id="85a9d-142">7.0.0</span><span class="sxs-lookup"><span data-stu-id="85a9d-142">7.0.0</span></span>            | <span data-ttu-id="85a9d-143">Éléments de travail liés à la version 7.0 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="85a9d-143">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="85a9d-144">7.1.0</span><span class="sxs-lookup"><span data-stu-id="85a9d-144">7.1.0</span></span>            | <span data-ttu-id="85a9d-145">Éléments de travail liés à la version 7.1 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="85a9d-145">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="85a9d-146">À l’avenir</span><span class="sxs-lookup"><span data-stu-id="85a9d-146">Future</span></span>           | <span data-ttu-id="85a9d-147">Éléments de travail d’une future version de PowerShell</span><span class="sxs-lookup"><span data-stu-id="85a9d-147">Work items a future version of PowerShell</span></span>          |
| <span data-ttu-id="85a9d-148">PSReadline-vNext</span><span class="sxs-lookup"><span data-stu-id="85a9d-148">PSReadline-vNext</span></span> | <span data-ttu-id="85a9d-149">Éléments de travail d’une future version de PSReadline</span><span class="sxs-lookup"><span data-stu-id="85a9d-149">Work items a future version of PSReadline</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="85a9d-150">Processus de triage</span><span class="sxs-lookup"><span data-stu-id="85a9d-150">Triage process</span></span>

<span data-ttu-id="85a9d-151">L’équipe PowerShell-Docs se réunit une fois par semaine pour discuter des problèmes ajoutés depuis la dernière réunion.</span><span class="sxs-lookup"><span data-stu-id="85a9d-151">The PowerShell docs team meets once per week to discuss any issues added since last meeting.</span></span> <span data-ttu-id="85a9d-152">Un problème est considéré comme trié lorsque des étiquettes ont été attribuées ou qu’un propriétaire a été affecté.</span><span class="sxs-lookup"><span data-stu-id="85a9d-152">An issue is considered to have been triaged when labels have been assigned or an owner has been assigned.</span></span> <span data-ttu-id="85a9d-153">Les membres de l’équipe PowerShell-Docs sont encouragés à examiner les problèmes quotidiennement et à les trier au fur et à mesure qu’ils arrivent.</span><span class="sxs-lookup"><span data-stu-id="85a9d-153">PowerShell docs team members are encouraged to review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="85a9d-154">La réunion de triage hebdomadaire peut alors permettre de discuter des nouveaux problèmes plus en détail si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="85a9d-154">The weekly triage meeting can then be used to discuss the new issues in more detail, as needed.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="85a9d-155">Commentaires produits mal placés</span><span class="sxs-lookup"><span data-stu-id="85a9d-155">Misplaced product feedback</span></span>

- <span data-ttu-id="85a9d-156">Entrez un commentaire pour le client indiquant qu’il s’agit de commentaires sur le produit et fournissez un lien vers le canal de commentaires correspondant.</span><span class="sxs-lookup"><span data-stu-id="85a9d-156">Enter a comment for the customer indicating it is product feedback and provide a link to the appropriate feedback channel.</span></span>
- <span data-ttu-id="85a9d-157">Facultatif : Copiez le problème à l’emplacement de commentaires sur le produit correspondant, ajoutez un lien vers l’élément copié, puis fermez le problème.</span><span class="sxs-lookup"><span data-stu-id="85a9d-157">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="85a9d-158">NE copiez PAS les problèmes sur UserVoice.</span><span class="sxs-lookup"><span data-stu-id="85a9d-158">DO NOT copy issues to UserVoice.</span></span>

  | <span data-ttu-id="85a9d-159">Ensemble de documents</span><span class="sxs-lookup"><span data-stu-id="85a9d-159">DocSet</span></span>    | <span data-ttu-id="85a9d-160">URL de commentaires sur le produit</span><span class="sxs-lookup"><span data-stu-id="85a9d-160">Product Feedback URL</span></span>                                           |
  | --------- | -------------------------------------------------------------- |
  | <span data-ttu-id="85a9d-161">developer</span><span class="sxs-lookup"><span data-stu-id="85a9d-161">developer</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="85a9d-162">dsc</span><span class="sxs-lookup"><span data-stu-id="85a9d-162">dsc</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | <span data-ttu-id="85a9d-163">galerie</span><span class="sxs-lookup"><span data-stu-id="85a9d-163">gallery</span></span>   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | <span data-ttu-id="85a9d-164">jea</span><span class="sxs-lookup"><span data-stu-id="85a9d-164">jea</span></span>       | `https://github.com/powershell/jea/issues/new`                 |
  | <span data-ttu-id="85a9d-165">reference</span><span class="sxs-lookup"><span data-stu-id="85a9d-165">reference</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="85a9d-166">wmf</span><span class="sxs-lookup"><span data-stu-id="85a9d-166">wmf</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a><span data-ttu-id="85a9d-167">Demandes de support</span><span class="sxs-lookup"><span data-stu-id="85a9d-167">Support requests</span></span>

- <span data-ttu-id="85a9d-168">Si la question de support est simple, répondez-y poliment et fermez le problème.</span><span class="sxs-lookup"><span data-stu-id="85a9d-168">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="85a9d-169">Si la question est plus compliquée ou que le demandeur répond par d’autres questions, redirigez-le vers des forums et des canaux de support.</span><span class="sxs-lookup"><span data-stu-id="85a9d-169">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="85a9d-170">Texte suggéré pour la redirection vers des forums :</span><span class="sxs-lookup"><span data-stu-id="85a9d-170">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="85a9d-171">Violation du code de conduite</span><span class="sxs-lookup"><span data-stu-id="85a9d-171">Code of conduct violations</span></span>

- <span data-ttu-id="85a9d-172">Modifiez le problème de façon à supprimer tout contenu choquant si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="85a9d-172">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="85a9d-173">Entrez un commentaire indiquant que le problème est indésirable, fermez le problème, puis verrouillez-le pour éviter d’autres commentaires.</span><span class="sxs-lookup"><span data-stu-id="85a9d-173">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="85a9d-174">Chaque événement de ce type doit être abordé dans le triage hebdomadaire pour déterminer si une action supplémentaire est nécessaire (envoi d’un rapport à GitHub ou au service juridique de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="85a9d-174">Each occurrence of this should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>

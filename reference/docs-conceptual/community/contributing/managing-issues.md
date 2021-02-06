---
title: Processus de gestion des problèmes
description: Cet article explique comment l’équipe PowerShell-Docs gère les problèmes.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99597518"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="fc218-103">Processus de gestion des problèmes</span><span class="sxs-lookup"><span data-stu-id="fc218-103">How we manage issues</span></span>

<span data-ttu-id="fc218-104">Cet article explique comment nous gérons les problèmes dans le référentiel PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="fc218-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="fc218-105">Cet article est conçu pour servir d’aide-mémoire aux membres de l’équipe PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="fc218-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="fc218-106">Il est publié ici pour assurer la transparence des processus pour nos contributeurs publics.</span><span class="sxs-lookup"><span data-stu-id="fc218-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="fc218-107">Sources des problèmes</span><span class="sxs-lookup"><span data-stu-id="fc218-107">Sources of issues</span></span>

- <span data-ttu-id="fc218-108">Contributeurs de la communauté</span><span class="sxs-lookup"><span data-stu-id="fc218-108">Community contributors</span></span>
- <span data-ttu-id="fc218-109">Contributeurs internes</span><span class="sxs-lookup"><span data-stu-id="fc218-109">Internal contributors</span></span>
- <span data-ttu-id="fc218-110">Transcriptions de commentaires provenant des réseaux sociaux</span><span class="sxs-lookup"><span data-stu-id="fc218-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="fc218-111">Commentaires envoyés par le biais du formulaire de commentaires sur Docs</span><span class="sxs-lookup"><span data-stu-id="fc218-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="fc218-112">Objectifs de temps de réponse</span><span class="sxs-lookup"><span data-stu-id="fc218-112">Response time targets</span></span>

<span data-ttu-id="fc218-113">80% des nouveaux problèmes sont clos dans les 3 jours ouvrables.</span><span class="sxs-lookup"><span data-stu-id="fc218-113">80% of new issues are closed within 3 business days.</span></span>

- <span data-ttu-id="fc218-114">Triage-1 jour ouvrable</span><span class="sxs-lookup"><span data-stu-id="fc218-114">Triaged - 1 business days</span></span>
- <span data-ttu-id="fc218-115">Correction ou modification-10 jours ouvrables</span><span class="sxs-lookup"><span data-stu-id="fc218-115">Fix or change - 10 business days</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="fc218-116">Étiquetage et jalons</span><span class="sxs-lookup"><span data-stu-id="fc218-116">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="fc218-117">Types d’étiquettes</span><span class="sxs-lookup"><span data-stu-id="fc218-117">Label Types</span></span>

|   <span data-ttu-id="fc218-118">Type</span><span class="sxs-lookup"><span data-stu-id="fc218-118">Type</span></span>   | <span data-ttu-id="fc218-119">Description</span><span class="sxs-lookup"><span data-stu-id="fc218-119">Description</span></span>                                                         |
| -------- | ------------------------------------------------------------------- |
| <span data-ttu-id="fc218-120">Domaine</span><span class="sxs-lookup"><span data-stu-id="fc218-120">Area</span></span>     | <span data-ttu-id="fc218-121">Permet d’indiquer sur quelle partie de PowerShell ou de Docs porte le problème.</span><span class="sxs-lookup"><span data-stu-id="fc218-121">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="fc218-122">Utile aux propriétaires de fonctionnalités pour trouver les problèmes relatifs à leur fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="fc218-122">Useful for feature owners to find issues for their feature.</span></span> |
| <span data-ttu-id="fc218-123">Problème</span><span class="sxs-lookup"><span data-stu-id="fc218-123">Issue</span></span>    | <span data-ttu-id="fc218-124">Indique le type de problème</span><span class="sxs-lookup"><span data-stu-id="fc218-124">Indicates the type of issue</span></span>                                         |
| <span data-ttu-id="fc218-125">Priorité</span><span class="sxs-lookup"><span data-stu-id="fc218-125">Priority</span></span> | <span data-ttu-id="fc218-126">Indique la priorité du problème.</span><span class="sxs-lookup"><span data-stu-id="fc218-126">Indicates the priority of the issue.</span></span> <span data-ttu-id="fc218-127">Plage de valeurs 0 (haute)-4 (faible)</span><span class="sxs-lookup"><span data-stu-id="fc218-127">Value range 0 (high) -4 (low)</span></span>  |
| <span data-ttu-id="fc218-128">Statut</span><span class="sxs-lookup"><span data-stu-id="fc218-128">Status</span></span>   | <span data-ttu-id="fc218-129">Indique l’état de l’élément de travail ou la raison pour laquelle il a été fermé</span><span class="sxs-lookup"><span data-stu-id="fc218-129">Indicates the status of the work item or why it was closed</span></span>          |
| <span data-ttu-id="fc218-130">Étiquette</span><span class="sxs-lookup"><span data-stu-id="fc218-130">Tag</span></span>      | <span data-ttu-id="fc218-131">Étiquettes utilisées pour une classification supplémentaire</span><span class="sxs-lookup"><span data-stu-id="fc218-131">Labels used to for additional classification</span></span>                        |
| <span data-ttu-id="fc218-132">En attente</span><span class="sxs-lookup"><span data-stu-id="fc218-132">Waiting</span></span>  | <span data-ttu-id="fc218-133">Indique que nous attendons une personne ou un autre événement</span><span class="sxs-lookup"><span data-stu-id="fc218-133">Indicates that we're waiting on someone or some other event</span></span>         |

#### <a name="milestones"></a><span data-ttu-id="fc218-134">Milestones</span><span class="sxs-lookup"><span data-stu-id="fc218-134">Milestones</span></span>

<span data-ttu-id="fc218-135">Les problèmes et demandes de tirage doivent être marqués du jalon correspondant.</span><span class="sxs-lookup"><span data-stu-id="fc218-135">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="fc218-136">Si le problème ne s’applique pas à une version spécifique, aucune étape majeure n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="fc218-136">If the issue doesn't apply to a specific version, then no milestone is used.</span></span> <span data-ttu-id="fc218-137">Les problèmes de la fonction PRs et les problèmes liés aux modifications qui n’ont pas encore été fusionnées dans la base de code PowerShell doivent être affectés à la **prochaine** étape majeure.</span><span class="sxs-lookup"><span data-stu-id="fc218-137">PRs and related issues for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="fc218-138">Une fois la modification du code fusionnée, remplacez la valeur du jalon par la version correspondante.</span><span class="sxs-lookup"><span data-stu-id="fc218-138">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="fc218-139">Jalon</span><span class="sxs-lookup"><span data-stu-id="fc218-139">Milestone</span></span>     |                    <span data-ttu-id="fc218-140">Description</span><span class="sxs-lookup"><span data-stu-id="fc218-140">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="fc218-141">7.0.0</span><span class="sxs-lookup"><span data-stu-id="fc218-141">7.0.0</span></span>            | <span data-ttu-id="fc218-142">Éléments de travail liés à la version 7.0 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc218-142">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="fc218-143">7.1.0</span><span class="sxs-lookup"><span data-stu-id="fc218-143">7.1.0</span></span>            | <span data-ttu-id="fc218-144">Éléments de travail liés à la version 7.1 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc218-144">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="fc218-145">7.2.0</span><span class="sxs-lookup"><span data-stu-id="fc218-145">7.2.0</span></span>            | <span data-ttu-id="fc218-146">Éléments de travail liés à PowerShell 7,2</span><span class="sxs-lookup"><span data-stu-id="fc218-146">Work items related to PowerShell 7.2</span></span>               |
| <span data-ttu-id="fc218-147">À l’avenir</span><span class="sxs-lookup"><span data-stu-id="fc218-147">Future</span></span>           | <span data-ttu-id="fc218-148">Éléments de travail d’une future version de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc218-148">Work items a future version of PowerShell</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="fc218-149">Processus de triage</span><span class="sxs-lookup"><span data-stu-id="fc218-149">Triage process</span></span>

<span data-ttu-id="fc218-150">Les membres de l’équipe de documentation PowerShell examinent les problèmes quotidiennement et hiérarchisent les nouveaux problèmes à mesure qu’ils arrivent.</span><span class="sxs-lookup"><span data-stu-id="fc218-150">PowerShell docs team members review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="fc218-151">L’équipe respecte chaque semaine pour discuter des problèmes qui doivent être triés ou rester non résolus.</span><span class="sxs-lookup"><span data-stu-id="fc218-151">The team meets weekly to discuss issues that need triage or remain unresolved.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="fc218-152">Commentaires produits mal placés</span><span class="sxs-lookup"><span data-stu-id="fc218-152">Misplaced product feedback</span></span>

- <span data-ttu-id="fc218-153">Entrez un commentaire pour rediriger le client vers le bon canal de commentaires.</span><span class="sxs-lookup"><span data-stu-id="fc218-153">Enter a comment redirecting the customer to the correct feedback channel.</span></span>
- <span data-ttu-id="fc218-154">Facultatif : Copiez le problème à l’emplacement de commentaires sur le produit correspondant, ajoutez un lien vers l’élément copié, puis fermez le problème.</span><span class="sxs-lookup"><span data-stu-id="fc218-154">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="fc218-155">NE copiez PAS les problèmes sur UserVoice.</span><span class="sxs-lookup"><span data-stu-id="fc218-155">DO NOT copy issues to UserVoice.</span></span>

  <span data-ttu-id="fc218-156">L’emplacement par défaut pour les problèmes PowerShell est [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .</span><span class="sxs-lookup"><span data-stu-id="fc218-156">The default location for PowerShell issues is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

  <span data-ttu-id="fc218-157">Les sujets suivants ont des emplacements différents pour les problèmes :</span><span class="sxs-lookup"><span data-stu-id="fc218-157">The following subject areas have different locations for issues:</span></span>

  | <span data-ttu-id="fc218-158">Sujets</span><span class="sxs-lookup"><span data-stu-id="fc218-158">Subjects</span></span> |                                                     <span data-ttu-id="fc218-159">URL de commentaires sur le produit</span><span class="sxs-lookup"><span data-stu-id="fc218-159">Product Feedback URL</span></span>                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | <span data-ttu-id="fc218-160">dsc</span><span class="sxs-lookup"><span data-stu-id="fc218-160">dsc</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | <span data-ttu-id="fc218-161">galerie</span><span class="sxs-lookup"><span data-stu-id="fc218-161">gallery</span></span>  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | <span data-ttu-id="fc218-162">jea</span><span class="sxs-lookup"><span data-stu-id="fc218-162">jea</span></span>      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | <span data-ttu-id="fc218-163">wmf</span><span class="sxs-lookup"><span data-stu-id="fc218-163">wmf</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a><span data-ttu-id="fc218-164">Demandes de support</span><span class="sxs-lookup"><span data-stu-id="fc218-164">Support requests</span></span>

- <span data-ttu-id="fc218-165">Si la question de support est simple, répondez-y poliment et fermez le problème.</span><span class="sxs-lookup"><span data-stu-id="fc218-165">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="fc218-166">Si la question est plus compliquée ou que le demandeur répond par d’autres questions, redirigez-le vers des forums et des canaux de support.</span><span class="sxs-lookup"><span data-stu-id="fc218-166">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="fc218-167">Texte suggéré pour la redirection vers des forums :</span><span class="sxs-lookup"><span data-stu-id="fc218-167">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="fc218-168">Violation du code de conduite</span><span class="sxs-lookup"><span data-stu-id="fc218-168">Code of conduct violations</span></span>

- <span data-ttu-id="fc218-169">Modifiez le problème de façon à supprimer tout contenu choquant si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fc218-169">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="fc218-170">Entrez un commentaire indiquant que le problème est indésirable, fermez le problème, puis verrouillez-le pour éviter d’autres commentaires.</span><span class="sxs-lookup"><span data-stu-id="fc218-170">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="fc218-171">Chaque violation doit être discutée dans le triage hebdomadaire pour déterminer la nécessité d’une action supplémentaire (rapport à GitHub ou Microsoft Legal).</span><span class="sxs-lookup"><span data-stu-id="fc218-171">Each violation should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>

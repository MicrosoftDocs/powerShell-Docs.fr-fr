---
title: Guide pratique pour envoyer des demandes de tirage
description: Cet article explique comment envoyer des demandes de tirage au référentiel PowerShell-Docs.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "99595896"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="51eda-103">Guide pratique pour envoyer des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="51eda-103">How to submit pull requests</span></span>

<span data-ttu-id="51eda-104">Pour apporter des modifications au contenu, envoyez une demande de tirage (pull request) à partir de votre duplication (fork).</span><span class="sxs-lookup"><span data-stu-id="51eda-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="51eda-105">Une requête de tirage doit être vérifiée avant de pouvoir être fusionnée.</span><span class="sxs-lookup"><span data-stu-id="51eda-105">A pull request must be reviewed before it can be merged.</span></span> <span data-ttu-id="51eda-106">Pour de meilleurs résultats, passez en revue la [liste de contrôle éditoriale](editorial-checklist.md) avant de soumettre votre demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="51eda-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="using-git-branches"></a><span data-ttu-id="51eda-107">Utilisation de branches git</span><span class="sxs-lookup"><span data-stu-id="51eda-107">Using git branches</span></span>

<span data-ttu-id="51eda-108">La branche par défaut pour PowerShell-Docs est la `staging` branche.</span><span class="sxs-lookup"><span data-stu-id="51eda-108">The default branch for PowerShell-Docs is the `staging` branch.</span></span> <span data-ttu-id="51eda-109">Les modifications apportées aux branches de travail sont fusionnées dans la `staging` branche avant d’être publiées.</span><span class="sxs-lookup"><span data-stu-id="51eda-109">Changes made in working branches are merged into the `staging` branch before then being published.</span></span> <span data-ttu-id="51eda-110">La `staging` branche est fusionnée dans la `live` branche tous les jours ouvrables à 3:00 h 00 (heure du Pacifique).</span><span class="sxs-lookup"><span data-stu-id="51eda-110">The `staging` branch is merged into the `live` branch every weekday at 3:00 PM (Pacific Time).</span></span> <span data-ttu-id="51eda-111">La `live` branche contient le contenu publié sur docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="51eda-111">The `live` branch contains the content that is published to docs.microsoft.com.</span></span>

<span data-ttu-id="51eda-112">Avant de commencer les modifications, créez une branche de travail dans votre copie locale du référentiel PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="51eda-112">Before starting any changes, create a working branch in your local copy of the PowerShell-Docs repository.</span></span> <span data-ttu-id="51eda-113">Lorsque vous travaillez localement, veillez à synchroniser votre dépôt local avant de créer votre branche de travail.</span><span class="sxs-lookup"><span data-stu-id="51eda-113">When working locally, be sure to synchronize your local repository before creating your working branch.</span></span> <span data-ttu-id="51eda-114">La branche de travail doit être créée à partir d’une copie mise à jour de la `staging` branche.</span><span class="sxs-lookup"><span data-stu-id="51eda-114">The working branch should be created from an update-to-date copy of the `staging` branch.</span></span>

<span data-ttu-id="51eda-115">Toutes les demandes de tirage doivent porter sur la branche `staging`.</span><span class="sxs-lookup"><span data-stu-id="51eda-115">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="51eda-116">N’envoyez pas de modification à la `live` branche.</span><span class="sxs-lookup"><span data-stu-id="51eda-116">Don't submit change to the `live` branch.</span></span>
<span data-ttu-id="51eda-117">Les modifications apportées à la branche `staging` sont fusionnées dans `live`, remplaçant toutes les modifications apportées à `live`.</span><span class="sxs-lookup"><span data-stu-id="51eda-117">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="51eda-118">Amélioration du processus de demande de tirage pour tout le monde</span><span class="sxs-lookup"><span data-stu-id="51eda-118">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="51eda-119">Plus la demande de tirage est simple et précise, plus vite elle peut être vérifiée et fusionnée.</span><span class="sxs-lookup"><span data-stu-id="51eda-119">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="51eda-120">Évitez les requêtes de tirage qui mettent à jour un grand nombre de fichiers ou qui contiennent des modifications non liées</span><span class="sxs-lookup"><span data-stu-id="51eda-120">Avoid pull requests that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="51eda-121">Évitez de créer des demandes de tirage qui contiennent des modifications sans lien les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="51eda-121">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="51eda-122">Séparez les mises à jour mineures d’articles existants des nouveaux articles et réécritures majeures.</span><span class="sxs-lookup"><span data-stu-id="51eda-122">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="51eda-123">Travaillez sur ces modifications dans des branches de travail distinctes.</span><span class="sxs-lookup"><span data-stu-id="51eda-123">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="51eda-124">Les modifications en bloc créent des demandes de tirage avec modification d’un grand nombre de fichiers.</span><span class="sxs-lookup"><span data-stu-id="51eda-124">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="51eda-125">Limitez votre demandes de tirage à 50 fichiers modifiés maximum.</span><span class="sxs-lookup"><span data-stu-id="51eda-125">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="51eda-126">Les grandes demandes de tirage sont difficiles à vérifier et plus sujettes aux erreurs.</span><span class="sxs-lookup"><span data-stu-id="51eda-126">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="51eda-127">Renommer ou supprimer des fichiers</span><span class="sxs-lookup"><span data-stu-id="51eda-127">Renaming or deleting files</span></span>

<span data-ttu-id="51eda-128">Lorsque vous renommez ou supprimez des fichiers, il doit y avoir un problème lié à la demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="51eda-128">When renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="51eda-129">qui aborde le caractère nécessaire du renommage ou de la suppression.</span><span class="sxs-lookup"><span data-stu-id="51eda-129">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="51eda-130">Évitez de mélanger les ajouts et modifications de contenu avec des changements de nom et suppressions de fichiers.</span><span class="sxs-lookup"><span data-stu-id="51eda-130">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="51eda-131">Tout fichier renommé ou supprimé doit être ajouté au fichier de redirection globale.</span><span class="sxs-lookup"><span data-stu-id="51eda-131">Any file that is renamed or deleted must be added to the global redirection file.</span></span> <span data-ttu-id="51eda-132">Lorsque cela est possible, mettez à jour tous les fichiers qui sont liés au contenu renommé ou supprimé, y compris les fichiers TOC.</span><span class="sxs-lookup"><span data-stu-id="51eda-132">When possible, update any files that link to the renamed or deleted content, including any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="51eda-133">Service de validation des demandes de tirage Docs</span><span class="sxs-lookup"><span data-stu-id="51eda-133">Docs PR validation service</span></span>

<span data-ttu-id="51eda-134">Le service de validation docs PR est une application GitHub qui exécute des règles de validation sur vos modifications.</span><span class="sxs-lookup"><span data-stu-id="51eda-134">The Docs PR validation service is a GitHub app that runs validation rules on your changes.</span></span> <span data-ttu-id="51eda-135">Vous devez corriger toutes les erreurs ou tous les avertissements signalés par le service de validation.</span><span class="sxs-lookup"><span data-stu-id="51eda-135">You must fix any errors or warnings reported by the validation service.</span></span>

<span data-ttu-id="51eda-136">Le comportement se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="51eda-136">You'll see the following behavior:</span></span>

1. <span data-ttu-id="51eda-137">Vous soumettez une demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="51eda-137">You submit a PR.</span></span>
1. <span data-ttu-id="51eda-138">Le commentaire GitHub indiquant l’état de votre demande de tirage présente l’état des « vérifications » activées sur le dépôt.</span><span class="sxs-lookup"><span data-stu-id="51eda-138">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="51eda-139">Dans cet exemple, deux vérifications sont activées, « validation validée » et « OpenPublishing. Build » :</span><span class="sxs-lookup"><span data-stu-id="51eda-139">In this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![État de validation : certaines vérifications ont échoué](media/pull-requests/validation-failed.png)

   <span data-ttu-id="51eda-141">Le build peut aboutir même si la validation commit échoue.</span><span class="sxs-lookup"><span data-stu-id="51eda-141">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="51eda-142">Pour plus d’informations, cliquez sur **Détails**.</span><span class="sxs-lookup"><span data-stu-id="51eda-142">Click **Details** for more information.</span></span>
1. <span data-ttu-id="51eda-143">Sur la page Détails figurent tous les contrôles de validation qui ont échoué, avec des informations indiquant comment résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="51eda-143">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="51eda-144">Une fois la validation réussie, le commentaire suivant est ajouté à la demande de tirage :</span><span class="sxs-lookup"><span data-stu-id="51eda-144">When validation succeeds, the following comment is added to the PR:</span></span>

   ![État de validation : réussite](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="51eda-146">Si vous êtes un contributeur externe (et non un employé Microsoft), vous n’avez pas accès aux rapports de build détaillés ni aux liens d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="51eda-146">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="51eda-147">Une fois la demande de tirage vérifiée, vous pouvez être invité à apporter des modifications ou à corriger les messages d’avertissement de validation.</span><span class="sxs-lookup"><span data-stu-id="51eda-147">When the PR is reviewed, you may be asked to make changes or fix validation warning messages.</span></span> <span data-ttu-id="51eda-148">L’équipe PowerShell-Docs peut vous aider à comprendre les erreurs de validation et les exigences éditoriales.</span><span class="sxs-lookup"><span data-stu-id="51eda-148">The PowerShell-Docs team can help you understand validation errors and editorial requirements.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51eda-149">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="51eda-149">Next steps</span></span>

[<span data-ttu-id="51eda-150">Guide de style PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="51eda-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="51eda-151">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="51eda-151">Additional resources</span></span>

[<span data-ttu-id="51eda-152">Processus de gestion des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="51eda-152">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository

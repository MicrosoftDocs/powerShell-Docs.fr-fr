---
title: Guide pratique pour envoyer des demandes de tirage
description: Cet article explique comment envoyer des demandes de tirage au référentiel PowerShell-Docs.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060234"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="404db-103">Guide pratique pour envoyer des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="404db-103">How to submit pull requests</span></span>

<span data-ttu-id="404db-104">Pour apporter des modifications au contenu, envoyez une demande de tirage (pull request) à partir de votre duplication (fork).</span><span class="sxs-lookup"><span data-stu-id="404db-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="404db-105">Il est nécessaire de revoir la demande de tirage pour pouvoir la fusionner.</span><span class="sxs-lookup"><span data-stu-id="404db-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="404db-106">Pour de meilleurs résultats, passez en revue la [liste de contrôle éditoriale](editorial-checklist.md) avant de soumettre votre demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="404db-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="404db-107">Choisir la bonne branche</span><span class="sxs-lookup"><span data-stu-id="404db-107">Target the correct branch</span></span>

<span data-ttu-id="404db-108">Toutes les demandes de tirage doivent porter sur la branche `staging`.</span><span class="sxs-lookup"><span data-stu-id="404db-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="404db-109">Les modifications ne doivent jamais être envoyées à la branche `live`.</span><span class="sxs-lookup"><span data-stu-id="404db-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="404db-110">Les modifications apportées à la branche `staging` sont fusionnées dans `live`, remplaçant toutes les modifications apportées à `live`.</span><span class="sxs-lookup"><span data-stu-id="404db-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="404db-111">Si vous soumettez une modification qui s’applique uniquement à une version non publiée de PowerShell, regardez s’il existe une branche pour cette version.</span><span class="sxs-lookup"><span data-stu-id="404db-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="404db-112">Votre demande de tirage doit porter sur la branche de version.</span><span class="sxs-lookup"><span data-stu-id="404db-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="404db-113">Les branches de version suivent le modèle de nom `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="404db-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="404db-114">Amélioration du processus de demande de tirage pour tout le monde</span><span class="sxs-lookup"><span data-stu-id="404db-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="404db-115">Plus la demande de tirage est simple et précise, plus vite elle peut être vérifiée et fusionnée.</span><span class="sxs-lookup"><span data-stu-id="404db-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="404db-116">Éviter les branches qui mettent à jour de nombreux fichiers ou qui contiennent des modifications sans lien les unes avec les autres</span><span class="sxs-lookup"><span data-stu-id="404db-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="404db-117">Évitez de créer des demandes de tirage qui contiennent des modifications sans lien les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="404db-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="404db-118">Séparez les mises à jour mineures d’articles existants des nouveaux articles et réécritures majeures.</span><span class="sxs-lookup"><span data-stu-id="404db-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="404db-119">Travaillez sur ces modifications dans des branches de travail distinctes.</span><span class="sxs-lookup"><span data-stu-id="404db-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="404db-120">Les modifications en bloc créent des demandes de tirage avec modification d’un grand nombre de fichiers.</span><span class="sxs-lookup"><span data-stu-id="404db-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="404db-121">Limitez votre demandes de tirage à 50 fichiers modifiés maximum.</span><span class="sxs-lookup"><span data-stu-id="404db-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="404db-122">Les grandes demandes de tirage sont difficiles à vérifier et plus sujettes aux erreurs.</span><span class="sxs-lookup"><span data-stu-id="404db-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="404db-123">Renommer ou supprimer des fichiers</span><span class="sxs-lookup"><span data-stu-id="404db-123">Renaming or deleting files</span></span>

<span data-ttu-id="404db-124">Si vous renommez ou supprimez des fichiers, la demande de tirage doit être accompagnée d’un problème</span><span class="sxs-lookup"><span data-stu-id="404db-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="404db-125">qui aborde le caractère nécessaire du renommage ou de la suppression.</span><span class="sxs-lookup"><span data-stu-id="404db-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="404db-126">Évitez de mélanger les ajouts et modifications de contenu avec des changements de nom et suppressions de fichiers.</span><span class="sxs-lookup"><span data-stu-id="404db-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="404db-127">Tout fichier renommé ou supprimé doit être ajouté au fichier de redirection maître.</span><span class="sxs-lookup"><span data-stu-id="404db-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="404db-128">Si possible, mettez également à jour tous les fichiers liés au contenu renommé ou supprimé,</span><span class="sxs-lookup"><span data-stu-id="404db-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="404db-129">notamment tous les fichiers TOC.</span><span class="sxs-lookup"><span data-stu-id="404db-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="404db-130">Service de validation des demandes de tirage Docs</span><span class="sxs-lookup"><span data-stu-id="404db-130">Docs PR validation service</span></span>

<span data-ttu-id="404db-131">Le service de validation des demandes de tirage Docs est une application GitHub qui exécute des règles de validation sur les fichiers d’une demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="404db-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="404db-132">Vous devez corriger toutes les erreurs et tous les avertissements (voir les exceptions) signalés par le service de validation.</span><span class="sxs-lookup"><span data-stu-id="404db-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="404db-133">Les avertissements suivants peuvent être ignorés :</span><span class="sxs-lookup"><span data-stu-id="404db-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="404db-134">Le comportement se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="404db-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="404db-135">Vous soumettez une demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="404db-135">You submit a PR.</span></span>
1. <span data-ttu-id="404db-136">Le commentaire GitHub indiquant l’état de votre demande de tirage présente l’état des « vérifications » activées sur le référentiel.</span><span class="sxs-lookup"><span data-stu-id="404db-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="404db-137">Dans cet exemple, deux vérifications sont activées, « Commit Validation » (Validation commit) et « OpenPublishing.Build » :</span><span class="sxs-lookup"><span data-stu-id="404db-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![Certaines vérifications ont échoué](media/pull-requests/validation-failed.png)

   <span data-ttu-id="404db-139">Le build peut aboutir même si la validation commit échoue.</span><span class="sxs-lookup"><span data-stu-id="404db-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="404db-140">Pour plus d’informations, cliquez sur **Détails**.</span><span class="sxs-lookup"><span data-stu-id="404db-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="404db-141">Sur la page Détails figurent tous les contrôles de validation qui ont échoué, avec des informations indiquant comment résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="404db-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="404db-142">Une fois la validation réussie, le commentaire suivant est ajouté à la demande de tirage :</span><span class="sxs-lookup"><span data-stu-id="404db-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Validation du build](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="404db-144">Si vous êtes un contributeur externe (et non un employé Microsoft), vous n’avez pas accès aux rapports de build détaillés ni aux liens d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="404db-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="404db-145">Lorsque la demande de tirage est examinée par un membre de l’équipe PowerShell-Docs, il peut vous être demandé d’apporter des modifications ou de résoudre les problèmes signalés par le rapport de validation.</span><span class="sxs-lookup"><span data-stu-id="404db-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="404db-146">L’équipe PowerShell-Docs peut vous aider à comprendre comment résoudre et éviter ces problèmes pour les soumissions à venir.</span><span class="sxs-lookup"><span data-stu-id="404db-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="404db-147">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="404db-147">Next steps</span></span>

[<span data-ttu-id="404db-148">Guide de style PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="404db-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="404db-149">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="404db-149">Additional resources</span></span>

[<span data-ttu-id="404db-150">Processus de gestion des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="404db-150">How we manage pull requests</span></span>](managing-pull-requests.md)

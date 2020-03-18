---
title: Processus de gestion des demandes de tirage
description: Cet article explique comment l’équipe PowerShell-Docs gère les demandes de tirage (pull request).
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060384"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="e2384-103">Gestion des demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="e2384-103">Managing pull requests</span></span>

<span data-ttu-id="e2384-104">Cet article explique comment nous gérons les demandes de tirage (pull request) dans le référentiel PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="e2384-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="e2384-105">Cet article est conçu pour servir d’aide-mémoire aux membres de l’équipe PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="e2384-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="e2384-106">Il est publié ici dans un souci de transparence des processus pour nos contributeurs publics.</span><span class="sxs-lookup"><span data-stu-id="e2384-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="e2384-107">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="e2384-107">Best practices</span></span>

- <span data-ttu-id="e2384-108">La personne qui soumet la demande de tirage ne doit pas fusionner la demande de tirage sans évaluation par les pairs.</span><span class="sxs-lookup"><span data-stu-id="e2384-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="e2384-109">Affectez le réviseur lors de l’envoi de la demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="e2384-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="e2384-110">Le fait d’anticiper l’affectation permet au réviseur d’envoyer plus rapidement ses remarques éditoriales.</span><span class="sxs-lookup"><span data-stu-id="e2384-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="e2384-111">Utilisez les commentaires pour décrire la nature de la modification ou le type de révision demandé.</span><span class="sxs-lookup"><span data-stu-id="e2384-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="e2384-112">Veillez à utiliser une @mention pour faire référence au réviseur.</span><span class="sxs-lookup"><span data-stu-id="e2384-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="e2384-113">Par exemple, s’il s’agit d’une modification mineure et que vous n’avez pas besoin d’une révision technique complète, expliquez-le en commentaire.</span><span class="sxs-lookup"><span data-stu-id="e2384-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="e2384-114">Étapes du processus de demande de tirage</span><span class="sxs-lookup"><span data-stu-id="e2384-114">PR Process steps</span></span>

1. <span data-ttu-id="e2384-115">Rédacteur : Crée la demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="e2384-115">Writer: Create PR</span></span>
   - <span data-ttu-id="e2384-116">Lie tous les problèmes résolus par la demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="e2384-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="e2384-117">Utilise la fonctionnalité de [fermeture automatique](https://help.github.com/en/articles/closing-issues-using-keywords) de GitHub pour fermer le problème.</span><span class="sxs-lookup"><span data-stu-id="e2384-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="e2384-118">Rédacteur : Affecte un réviseur.</span><span class="sxs-lookup"><span data-stu-id="e2384-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="e2384-119">Réviseur : Révise et commente (si nécessaire).</span><span class="sxs-lookup"><span data-stu-id="e2384-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="e2384-120">Rédacteur : Incorpore les commentaires de révision.</span><span class="sxs-lookup"><span data-stu-id="e2384-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="e2384-121">Les deux : Examinent le rendu de la préversion.</span><span class="sxs-lookup"><span data-stu-id="e2384-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="e2384-122">Les deux : Vérifient le rapport de validation et corrigent les avertissements et les erreurs.</span><span class="sxs-lookup"><span data-stu-id="e2384-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="e2384-123">Rédacteur : Ajoute un commentaire de signature (informations Acrolinx incluses).</span><span class="sxs-lookup"><span data-stu-id="e2384-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="e2384-124">Réviseur : Marque la révision de la mention « Approuvée ».</span><span class="sxs-lookup"><span data-stu-id="e2384-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="e2384-125">Administrateur du référentiel : Fusionne la demande de tirage (voir critères ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="e2384-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="e2384-126">Liste de contrôle du réviseur de contenu</span><span class="sxs-lookup"><span data-stu-id="e2384-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="e2384-127">Pour une liste plus complète, consultez la [liste de vérification éditoriale](editorial-checklist.md).</span><span class="sxs-lookup"><span data-stu-id="e2384-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="e2384-128">Corriger la grammaire, le style, la concision et la précision technique.</span><span class="sxs-lookup"><span data-stu-id="e2384-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="e2384-129">Vérifier que les exemples s’appliquent toujours à la version cible.</span><span class="sxs-lookup"><span data-stu-id="e2384-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="e2384-130">Examiner le rendu de la préversion.</span><span class="sxs-lookup"><span data-stu-id="e2384-130">Check Preview rendering</span></span>
- <span data-ttu-id="e2384-131">Vérifier les métadonnées (ms.date, suppression de ms.assetid, vérification des champs obligatoires).</span><span class="sxs-lookup"><span data-stu-id="e2384-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="e2384-132">Valider l’exactitude du Markdown.</span><span class="sxs-lookup"><span data-stu-id="e2384-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="e2384-133">Voir le guide de style pour la mise en forme des contenus spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e2384-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="e2384-134">Réorganiser les exemples :</span><span class="sxs-lookup"><span data-stu-id="e2384-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="e2384-135">phrase(s) d’introduction ;</span><span class="sxs-lookup"><span data-stu-id="e2384-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="e2384-136">code et sortie ;</span><span class="sxs-lookup"><span data-stu-id="e2384-136">Code and output</span></span>
  - <span data-ttu-id="e2384-137">explication détaillée du code (si nécessaire).</span><span class="sxs-lookup"><span data-stu-id="e2384-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="e2384-138">Vérifier l’exactitude des liens hypertextes.</span><span class="sxs-lookup"><span data-stu-id="e2384-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="e2384-139">Remplacer ou supprimer les liens TechNet/MSDN.</span><span class="sxs-lookup"><span data-stu-id="e2384-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="e2384-140">Garantir un nombre minimal de redirections vers la cible.</span><span class="sxs-lookup"><span data-stu-id="e2384-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="e2384-141">Vérifier le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e2384-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="e2384-142">Type de lien correct :</span><span class="sxs-lookup"><span data-stu-id="e2384-142">Correct link type</span></span>
    - <span data-ttu-id="e2384-143">liens de fichiers pour les fichiers locaux ;</span><span class="sxs-lookup"><span data-stu-id="e2384-143">File links for local files</span></span>
    - <span data-ttu-id="e2384-144">liens URL pour les fichiers extérieurs à l’ensemble de documents.</span><span class="sxs-lookup"><span data-stu-id="e2384-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="e2384-145">Supprimer les paramètres régionaux des URL.</span><span class="sxs-lookup"><span data-stu-id="e2384-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="e2384-146">Simplifier les URL pointant vers `docs.microsoft.com`.</span><span class="sxs-lookup"><span data-stu-id="e2384-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="e2384-147">Processus de fusion des branches</span><span class="sxs-lookup"><span data-stu-id="e2384-147">Branch Merge Process</span></span>

<span data-ttu-id="e2384-148">La branche intermédiaire est la seule branche qui sera fusionnée dans live.</span><span class="sxs-lookup"><span data-stu-id="e2384-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="e2384-149">Les branches à courte durée de vie (branches de travail) doivent faire l’objet d’une fusion Squash.</span><span class="sxs-lookup"><span data-stu-id="e2384-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="e2384-150">*Fusion à partir de/vers*</span><span class="sxs-lookup"><span data-stu-id="e2384-150">*Merge from/to*</span></span>  | <span data-ttu-id="e2384-151">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="e2384-151">*release-branch*</span></span> | <span data-ttu-id="e2384-152">*staging*</span><span class="sxs-lookup"><span data-stu-id="e2384-152">*staging*</span></span>        | <span data-ttu-id="e2384-153">*live*</span><span class="sxs-lookup"><span data-stu-id="e2384-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="e2384-154">*working-branch*</span><span class="sxs-lookup"><span data-stu-id="e2384-154">*working-branch*</span></span> | <span data-ttu-id="e2384-155">fusion Squash et fusion</span><span class="sxs-lookup"><span data-stu-id="e2384-155">squash and merge</span></span> | <span data-ttu-id="e2384-156">fusion Squash et fusion</span><span class="sxs-lookup"><span data-stu-id="e2384-156">squash and merge</span></span> | <span data-ttu-id="e2384-157">Non autorisé</span><span class="sxs-lookup"><span data-stu-id="e2384-157">Not allowed</span></span> |
| <span data-ttu-id="e2384-158">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="e2384-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="e2384-159">fusion</span><span class="sxs-lookup"><span data-stu-id="e2384-159">merge</span></span>            | <span data-ttu-id="e2384-160">Non autorisé</span><span class="sxs-lookup"><span data-stu-id="e2384-160">Not allowed</span></span> |
| <span data-ttu-id="e2384-161">*staging*</span><span class="sxs-lookup"><span data-stu-id="e2384-161">*staging*</span></span>        | <span data-ttu-id="e2384-162">rebaser</span><span class="sxs-lookup"><span data-stu-id="e2384-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="e2384-163">fusion</span><span class="sxs-lookup"><span data-stu-id="e2384-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="e2384-164">Liste de contrôle des fusions de demandes de tirage</span><span class="sxs-lookup"><span data-stu-id="e2384-164">PR Merger checklist</span></span>

- <span data-ttu-id="e2384-165">Révision du contenu terminée.</span><span class="sxs-lookup"><span data-stu-id="e2384-165">Content review complete</span></span>
- <span data-ttu-id="e2384-166">Branche cible correcte pour la modification.</span><span class="sxs-lookup"><span data-stu-id="e2384-166">Correct target branch for the change</span></span>
- <span data-ttu-id="e2384-167">Aucun conflit de fusion.</span><span class="sxs-lookup"><span data-stu-id="e2384-167">No merge conflicts</span></span>
- <span data-ttu-id="e2384-168">Réussite de toutes les étapes de validation et de build.</span><span class="sxs-lookup"><span data-stu-id="e2384-168">All validation and build step pass</span></span>
  - <span data-ttu-id="e2384-169">Correction des avertissements et des suggestions (pour connaître les exceptions, consultez [Notes](#notes))</span><span class="sxs-lookup"><span data-stu-id="e2384-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="e2384-170">Pas de liens rompus.</span><span class="sxs-lookup"><span data-stu-id="e2384-170">No broken links</span></span>
- <span data-ttu-id="e2384-171">Fusion en fonction de la table.</span><span class="sxs-lookup"><span data-stu-id="e2384-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="e2384-172">Notes</span><span class="sxs-lookup"><span data-stu-id="e2384-172">Notes</span></span>

<span data-ttu-id="e2384-173">Les avertissements suivants peuvent être ignorés :</span><span class="sxs-lookup"><span data-stu-id="e2384-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="e2384-174">Lors de la fusion d’une demande de tirage, le début (HEAD) de la branche cible est modifié.</span><span class="sxs-lookup"><span data-stu-id="e2384-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="e2384-175">Les demandes de tirage ouvertes qui étaient basées sur le début précédent sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e2384-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="e2384-176">Il est possible de fusionner la demande de tirage obsolète avec des droits d’administrateur pour remplacer les avertissements de fusion dans GitHub.</span><span class="sxs-lookup"><span data-stu-id="e2384-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="e2384-177">Cela peut être fait sans risque si la ou les demandes de tirage fusionnées précédemment n’ont pas touché les mêmes fichiers.</span><span class="sxs-lookup"><span data-stu-id="e2384-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="e2384-178">L’option la plus sûre est cependant de cliquer sur le bouton **Mettre à jour la branche**.</span><span class="sxs-lookup"><span data-stu-id="e2384-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="e2384-179">Il peut exister des conflits non résolus qui doivent être corrigés.</span><span class="sxs-lookup"><span data-stu-id="e2384-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="e2384-180">Publier sur live</span><span class="sxs-lookup"><span data-stu-id="e2384-180">Publishing to Live</span></span>

<span data-ttu-id="e2384-181">Régulièrement, les modifications accumulées dans la branche `staging` doivent être publiées sur le site web en ligne.</span><span class="sxs-lookup"><span data-stu-id="e2384-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="e2384-182">Cela implique de fusionner la branche `staging` dans la branche `live`.</span><span class="sxs-lookup"><span data-stu-id="e2384-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="e2384-183">La branche `staging` doit être fusionnée dans `live` au moins une fois par semaine.</span><span class="sxs-lookup"><span data-stu-id="e2384-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="e2384-184">La branche `staging` doit être fusionnée dans `live` après toute modification significative :</span><span class="sxs-lookup"><span data-stu-id="e2384-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="e2384-185">modification d’au moins 50 fichiers ;</span><span class="sxs-lookup"><span data-stu-id="e2384-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="e2384-186">après la fusion d’une branche de version ;</span><span class="sxs-lookup"><span data-stu-id="e2384-186">After merging a release branch</span></span>
  - <span data-ttu-id="e2384-187">modification des configurations du référentiel ou de l’ensemble de documents (docfx.json, configurations OPS, scripts de build, etc.) ;</span><span class="sxs-lookup"><span data-stu-id="e2384-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="e2384-188">modification du fichier de redirection ;</span><span class="sxs-lookup"><span data-stu-id="e2384-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="e2384-189">modification de la table des matières ;</span><span class="sxs-lookup"><span data-stu-id="e2384-189">Changes to the TOC</span></span>
  - <span data-ttu-id="e2384-190">après la fusion d’une branche de « projet » (réorganisation de contenu, mise à jour en bloc, etc.).</span><span class="sxs-lookup"><span data-stu-id="e2384-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>

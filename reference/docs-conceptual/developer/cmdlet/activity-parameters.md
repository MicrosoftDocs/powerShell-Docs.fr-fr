---
title: Paramètres d’activité | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364638"
---
# <a name="activity-parameters"></a><span data-ttu-id="6b60a-102">Paramètres d’activité</span><span class="sxs-lookup"><span data-stu-id="6b60a-102">Activity Parameters</span></span>

<span data-ttu-id="6b60a-103">Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres d’activité.</span><span class="sxs-lookup"><span data-stu-id="6b60a-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

|<span data-ttu-id="6b60a-104">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6b60a-104">Parameter</span></span>|<span data-ttu-id="6b60a-105">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="6b60a-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="6b60a-106">**Parenthèse**</span><span class="sxs-lookup"><span data-stu-id="6b60a-106">**Append**</span></span><br><span data-ttu-id="6b60a-107">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-107">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-108">Implémentez ce paramètre pour permettre à l’utilisateur d’ajouter du contenu à la fin d’une ressource lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-108">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-109">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="6b60a-109">**CaseSensitive**</span></span><br><span data-ttu-id="6b60a-110">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-110">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-111">Implémentez ce paramètre afin que l’utilisateur puisse exiger le respect de la casse lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-111">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-112">**Commande**</span><span class="sxs-lookup"><span data-stu-id="6b60a-112">**Command**</span></span><br><span data-ttu-id="6b60a-113">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6b60a-113">Data type: String</span></span>|<span data-ttu-id="6b60a-114">Implémentez ce paramètre afin que l’utilisateur puisse spécifier une chaîne de commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="6b60a-114">Implement this parameter so the user can specify a command string to run.</span></span>|
|<span data-ttu-id="6b60a-115">**CompatibleVersion**</span><span class="sxs-lookup"><span data-stu-id="6b60a-115">**CompatibleVersion**</span></span><br><span data-ttu-id="6b60a-116">Type de données : objet System. version</span><span class="sxs-lookup"><span data-stu-id="6b60a-116">Data type: System.Version object</span></span>|<span data-ttu-id="6b60a-117">Implémentez ce paramètre afin que l’utilisateur puisse spécifier la sémantique avec laquelle l’applet de commande doit être compatible pour la compatibilité avec les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="6b60a-117">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>|
|<span data-ttu-id="6b60a-118">**Dens**</span><span class="sxs-lookup"><span data-stu-id="6b60a-118">**Compress**</span></span><br><span data-ttu-id="6b60a-119">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-120">Implémentez ce paramètre afin que la compression des données soit utilisée lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-120">Implement this parameter so that data compression is used when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-121">**Dens**</span><span class="sxs-lookup"><span data-stu-id="6b60a-121">**Compress**</span></span><br><span data-ttu-id="6b60a-122">Type de données : mot clé</span><span class="sxs-lookup"><span data-stu-id="6b60a-122">Data type: Keyword</span></span>|<span data-ttu-id="6b60a-123">Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’algorithme à utiliser pour la compression des données.</span><span class="sxs-lookup"><span data-stu-id="6b60a-123">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>|
|<span data-ttu-id="6b60a-124">**Propositions**</span><span class="sxs-lookup"><span data-stu-id="6b60a-124">**Continuous**</span></span><br><span data-ttu-id="6b60a-125">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-125">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-126">Implémentez ce paramètre afin que les données soient traitées jusqu’à ce que l’utilisateur mette fin à l’applet de commande lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-126">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="6b60a-127">Si le paramètre n’est pas spécifié, l’applet de commande traite une quantité de données prédéfinie, puis termine l’opération.</span><span class="sxs-lookup"><span data-stu-id="6b60a-127">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>|
|<span data-ttu-id="6b60a-128">**Créés**</span><span class="sxs-lookup"><span data-stu-id="6b60a-128">**Create**</span></span><br><span data-ttu-id="6b60a-129">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-129">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-130">Implémentez ce paramètre pour indiquer qu’une ressource est créée s’il n’en existe pas déjà une lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-130">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-131">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-131">**Delete**</span></span><br><span data-ttu-id="6b60a-132">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-132">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-133">Implémentez ce paramètre afin que les ressources soient supprimées lorsque l’applet de commande a terminé son opération lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-133">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-134">**Vidé**</span><span class="sxs-lookup"><span data-stu-id="6b60a-134">**Drain**</span></span><br><span data-ttu-id="6b60a-135">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-135">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-136">Implémentez ce paramètre pour indiquer que les éléments de travail en suspens sont traités avant que l’applet de commande traite les nouvelles données lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-136">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="6b60a-137">Si le paramètre n’est pas spécifié, les éléments de travail sont traités immédiatement.</span><span class="sxs-lookup"><span data-stu-id="6b60a-137">If the parameter is not specified, the work items are processed immediately.</span></span>|
|<span data-ttu-id="6b60a-138">**Effacer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-138">**Erase**</span></span><br><span data-ttu-id="6b60a-139">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="6b60a-139">Data type: Int32</span></span>|<span data-ttu-id="6b60a-140">Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre de fois où une ressource est effacée avant d’être supprimée.</span><span class="sxs-lookup"><span data-stu-id="6b60a-140">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>|
|<span data-ttu-id="6b60a-141">**Appuie**</span><span class="sxs-lookup"><span data-stu-id="6b60a-141">**ErrorLevel**</span></span><br><span data-ttu-id="6b60a-142">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="6b60a-142">Data type: Int32</span></span>|<span data-ttu-id="6b60a-143">Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le niveau d’erreurs à signaler.</span><span class="sxs-lookup"><span data-stu-id="6b60a-143">Implement this parameter so that the user can specify the level of errors to report.</span></span>|
|<span data-ttu-id="6b60a-144">**Exclus**</span><span class="sxs-lookup"><span data-stu-id="6b60a-144">**Exclude**</span></span><br><span data-ttu-id="6b60a-145">Type de données : String []</span><span class="sxs-lookup"><span data-stu-id="6b60a-145">Data type: String[]</span></span>|<span data-ttu-id="6b60a-146">Implémentez ce paramètre afin que l’utilisateur puisse exclure des éléments d’une activité.</span><span class="sxs-lookup"><span data-stu-id="6b60a-146">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="6b60a-147">Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b60a-147">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="6b60a-148">**Filtres**</span><span class="sxs-lookup"><span data-stu-id="6b60a-148">**Filter**</span></span><br><span data-ttu-id="6b60a-149">Type de données : mot clé</span><span class="sxs-lookup"><span data-stu-id="6b60a-149">Data type: Keyword</span></span>|<span data-ttu-id="6b60a-150">Implémentez ce paramètre afin que l’utilisateur puisse spécifier un filtre qui sélectionne les ressources sur lesquelles exécuter l’action d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b60a-150">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="6b60a-151">Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b60a-151">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="6b60a-152">**Suivez**</span><span class="sxs-lookup"><span data-stu-id="6b60a-152">**Follow**</span></span><br><span data-ttu-id="6b60a-153">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-153">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-154">Implémentez ce paramètre afin que la progression soit suivie lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-154">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-155">**Appliqués**</span><span class="sxs-lookup"><span data-stu-id="6b60a-155">**Force**</span></span><br><span data-ttu-id="6b60a-156">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-156">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-157">Implémentez ce paramètre pour indiquer que l’utilisateur peut exécuter une action même si des restrictions sont rencontrées lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-157">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="6b60a-158">Le paramètre ne permet pas de compromettre la sécurité.</span><span class="sxs-lookup"><span data-stu-id="6b60a-158">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="6b60a-159">Par exemple, ce paramètre permet à un utilisateur de remplacer un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="6b60a-159">For example, this parameter lets a user overwrite a read-only file.</span></span>|
|<span data-ttu-id="6b60a-160">**Inclusion**</span><span class="sxs-lookup"><span data-stu-id="6b60a-160">**Include**</span></span><br><span data-ttu-id="6b60a-161">Type de données : String []</span><span class="sxs-lookup"><span data-stu-id="6b60a-161">Data type: String[]</span></span>|<span data-ttu-id="6b60a-162">Implémentez ce paramètre pour permettre à l’utilisateur d’inclure des éléments dans une activité.</span><span class="sxs-lookup"><span data-stu-id="6b60a-162">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="6b60a-163">Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b60a-163">For more information about how to use input filters, see [Input Filter Parameters](input-filter-parameters.md).</span></span>|
|<span data-ttu-id="6b60a-164">**Incrémentielle**</span><span class="sxs-lookup"><span data-stu-id="6b60a-164">**Incremental**</span></span><br><span data-ttu-id="6b60a-165">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-165">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-166">Implémentez ce paramètre pour indiquer que le traitement est effectué de façon incrémentielle lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-166">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="6b60a-167">Par exemple, ce paramètre permet à un utilisateur d’effectuer des sauvegardes incrémentielles qui sauvegardent des fichiers uniquement depuis la dernière sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6b60a-167">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>|
|<span data-ttu-id="6b60a-168">**InputObject**</span><span class="sxs-lookup"><span data-stu-id="6b60a-168">**InputObject**</span></span><br><span data-ttu-id="6b60a-169">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="6b60a-169">Data type: Object</span></span>|<span data-ttu-id="6b60a-170">Implémentez ce paramètre lorsque l’applet de commande prend en entrée d’autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="6b60a-170">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="6b60a-171">Quand vous définissez un paramètre **InputObject** , spécifiez toujours le mot clé **ValueFromPipeline** lorsque vous déclarez l’attribut de **paramètre** .</span><span class="sxs-lookup"><span data-stu-id="6b60a-171">When you define an **InputObject** parameter, always specify the **ValueFromPipeline** keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="6b60a-172">Pour plus d’informations sur l’utilisation des filtres d’entrée, consultez [paramètres de filtre d’entrée](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b60a-172">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>|
|<span data-ttu-id="6b60a-173">**Insérer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-173">**Insert**</span></span><br><span data-ttu-id="6b60a-174">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-174">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-175">Implémentez ce paramètre afin que l’applet de commande insère un élément lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-175">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-176">**Non**</span><span class="sxs-lookup"><span data-stu-id="6b60a-176">**Interactive**</span></span><br><span data-ttu-id="6b60a-177">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-177">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-178">Implémentez ce paramètre afin que l’applet de commande fonctionne de manière interactive avec l’utilisateur lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-178">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-179">**Défini**</span><span class="sxs-lookup"><span data-stu-id="6b60a-179">**Interval**</span></span><br><span data-ttu-id="6b60a-180">Type de données : HashTable</span><span class="sxs-lookup"><span data-stu-id="6b60a-180">Data type: HashTable</span></span>|<span data-ttu-id="6b60a-181">Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une table de hachage de mots clés qui contient les valeurs.</span><span class="sxs-lookup"><span data-stu-id="6b60a-181">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="6b60a-182">L’exemple suivant montre des exemples de valeurs pour le paramètre **Interval** : `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="6b60a-182">The following example shows sample values for the **Interval** parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>|
|<span data-ttu-id="6b60a-183">**Log**</span><span class="sxs-lookup"><span data-stu-id="6b60a-183">**Log**</span></span><br><span data-ttu-id="6b60a-184">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-184">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-185">Implémentez ce paramètre pour auditer les actions de l’applet de commande lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-185">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-186">**NoClobber**</span><span class="sxs-lookup"><span data-stu-id="6b60a-186">**NoClobber**</span></span><br><span data-ttu-id="6b60a-187">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-187">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-188">Implémentez ce paramètre afin que la ressource ne soit pas remplacée lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-188">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="6b60a-189">Ce paramètre s’applique généralement aux applets de commande qui créent des objets, afin qu’ils puissent empêcher le remplacement des objets existants portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="6b60a-189">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>|
|<span data-ttu-id="6b60a-190">**Indiquer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-190">**Notify**</span></span><br><span data-ttu-id="6b60a-191">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-191">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-192">Implémentez ce paramètre afin que l’utilisateur soit informé que l’activité est terminée lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-192">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-193">**NotifyAddress**</span><span class="sxs-lookup"><span data-stu-id="6b60a-193">**NotifyAddress**</span></span><br><span data-ttu-id="6b60a-194">Type de données : adresse de messagerie</span><span class="sxs-lookup"><span data-stu-id="6b60a-194">Data type: Email address</span></span>|<span data-ttu-id="6b60a-195">Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’adresse de messagerie à utiliser pour envoyer une notification lorsque le paramètre **Notify** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-195">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the **Notify** parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-196">**Remplacer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-196">**Overwrite**</span></span><br><span data-ttu-id="6b60a-197">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-197">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-198">Implémentez ce paramètre afin que l’applet de commande remplace toutes les données existantes lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-198">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-199">**Prompt**</span><span class="sxs-lookup"><span data-stu-id="6b60a-199">**Prompt**</span></span><br><span data-ttu-id="6b60a-200">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6b60a-200">Data type: String</span></span>|<span data-ttu-id="6b60a-201">Implémentez ce paramètre afin que l’utilisateur puisse spécifier une invite pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b60a-201">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>|
|<span data-ttu-id="6b60a-202">**Silencieux**</span><span class="sxs-lookup"><span data-stu-id="6b60a-202">**Quiet**</span></span><br><span data-ttu-id="6b60a-203">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-203">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-204">Implémentez ce paramètre afin que l’applet de commande supprime les commentaires de l’utilisateur pendant ses actions lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-204">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-205">**Recurse**</span><span class="sxs-lookup"><span data-stu-id="6b60a-205">**Recurse**</span></span><br><span data-ttu-id="6b60a-206">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-206">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-207">Implémentez ce paramètre afin que l’applet de commande effectue ses actions de manière récursive sur les ressources lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-207">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-208">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="6b60a-208">**Repair**</span></span><br><span data-ttu-id="6b60a-209">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-209">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-210">Implémentez ce paramètre afin que l’applet de commande tente de corriger un état de rupture lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-210">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-211">**RepairString**</span><span class="sxs-lookup"><span data-stu-id="6b60a-211">**RepairString**</span></span><br><span data-ttu-id="6b60a-212">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6b60a-212">Data type: String</span></span>|<span data-ttu-id="6b60a-213">Implémentez ce paramètre afin que l’utilisateur puisse spécifier une chaîne à utiliser lorsque le paramètre de **réparation** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-213">Implement this parameter so that the user can specify a string to use when the **Repair** parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-214">**Réessayez**</span><span class="sxs-lookup"><span data-stu-id="6b60a-214">**Retry**</span></span><br><span data-ttu-id="6b60a-215">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="6b60a-215">Data type: Int32</span></span>|<span data-ttu-id="6b60a-216">Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nombre de fois où l’applet de commande tentera une action.</span><span class="sxs-lookup"><span data-stu-id="6b60a-216">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>|
|<span data-ttu-id="6b60a-217">**Sélectionné**</span><span class="sxs-lookup"><span data-stu-id="6b60a-217">**Select**</span></span><br><span data-ttu-id="6b60a-218">Type de données : tableau de mots clés</span><span class="sxs-lookup"><span data-stu-id="6b60a-218">Data type: Keyword array</span></span>|<span data-ttu-id="6b60a-219">Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un tableau des types d’éléments.</span><span class="sxs-lookup"><span data-stu-id="6b60a-219">Implement this parameter so that the user can specify an array of the types of items.</span></span>|
|<span data-ttu-id="6b60a-220">**Train**</span><span class="sxs-lookup"><span data-stu-id="6b60a-220">**Stream**</span></span><br><span data-ttu-id="6b60a-221">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-221">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-222">Implémentez ce paramètre afin que l’utilisateur puisse diffuser plusieurs objets de sortie via le pipeline lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-222">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-223">**Interdire**</span><span class="sxs-lookup"><span data-stu-id="6b60a-223">**Strict**</span></span><br><span data-ttu-id="6b60a-224">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-224">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-225">Implémentez ce paramètre afin que toutes les erreurs soient traitées comme des erreurs d’arrêt lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-225">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-226">**TempLocation**</span><span class="sxs-lookup"><span data-stu-id="6b60a-226">**TempLocation**</span></span><br><span data-ttu-id="6b60a-227">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6b60a-227">Data type: String</span></span>|<span data-ttu-id="6b60a-228">Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’emplacement des données temporaires utilisées pendant l’opération de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b60a-228">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>|
|<span data-ttu-id="6b60a-229">**Expiré**</span><span class="sxs-lookup"><span data-stu-id="6b60a-229">**Timeout**</span></span><br><span data-ttu-id="6b60a-230">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="6b60a-230">Data type: Int32</span></span>|<span data-ttu-id="6b60a-231">Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’intervalle de délai d’attente (en millisecondes).</span><span class="sxs-lookup"><span data-stu-id="6b60a-231">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>|
|<span data-ttu-id="6b60a-232">**Tronquer**</span><span class="sxs-lookup"><span data-stu-id="6b60a-232">**Truncate**</span></span><br><span data-ttu-id="6b60a-233">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-233">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-234">Implémentez ce paramètre afin que l’applet de commande tronque ses actions lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-234">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="6b60a-235">Si le paramètre n’est pas spécifié, l’applet de commande effectue une autre action.</span><span class="sxs-lookup"><span data-stu-id="6b60a-235">If the parameter is not specified, the cmdlet performs another action.</span></span>|
|<span data-ttu-id="6b60a-236">**Confirmation**</span><span class="sxs-lookup"><span data-stu-id="6b60a-236">**Verify**</span></span><br><span data-ttu-id="6b60a-237">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-237">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-238">Implémentez ce paramètre afin que l’applet de commande effectue un test pour déterminer si une action a eu lieu lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-238">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>|
|<span data-ttu-id="6b60a-239">**Qu'**</span><span class="sxs-lookup"><span data-stu-id="6b60a-239">**Wait**</span></span><br><span data-ttu-id="6b60a-240">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="6b60a-240">Data type: SwitchParameter</span></span>|<span data-ttu-id="6b60a-241">Implémentez ce paramètre afin que l’applet de commande attende l’entrée de l’utilisateur avant de continuer lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-241">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>
|<span data-ttu-id="6b60a-242">**Délai**</span><span class="sxs-lookup"><span data-stu-id="6b60a-242">**WaitTime**</span></span><br><span data-ttu-id="6b60a-243">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="6b60a-243">Data type: Int32</span></span>|<span data-ttu-id="6b60a-244">Implémentez ce paramètre afin que l’utilisateur puisse spécifier la durée (en secondes) pendant laquelle l’applet de commande attendra l’entrée de l’utilisateur lorsque le paramètre **Wait** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b60a-244">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the **Wait** parameter is specified.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6b60a-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b60a-245">See Also</span></span>

[<span data-ttu-id="6b60a-246">Paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="6b60a-246">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="6b60a-247">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b60a-247">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="6b60a-248">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6b60a-248">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
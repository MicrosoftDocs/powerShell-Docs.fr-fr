---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093879"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="dfcda-102">État unifié et cohérent et représentation de l’état</span><span class="sxs-lookup"><span data-stu-id="dfcda-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="dfcda-103">Une série d’améliorations ont été apportées dans cette version pour l’état du gestionnaire de configuration local et le statut DSC générés par des automatisations.</span><span class="sxs-lookup"><span data-stu-id="dfcda-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="dfcda-104">Il s’agit notamment de représentations de l’état et du statut unifiées et cohérentes, d’une propriété d’heure et de date facile à gérer pour les objets de statut retournés par l’applet de commande `Get-DscConfigurationStatus`, et d’une propriété améliorée pour les détails sur l’état du gestionnaire de configuration local retournés par l’applet de commande `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="dfcda-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="dfcda-105">La représentation de l’état du gestionnaire de configuration local et du statut de l’opération DSC a été revisitée et unifiée conformément aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfcda-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="dfcda-106">La ressource NotProcessed n’affecte pas l’état du gestionnaire de configuration local et le statut DSC.</span><span class="sxs-lookup"><span data-stu-id="dfcda-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="dfcda-107">Le gestionnaire de configuration local cesse de traiter les ressources dès qu’il en rencontre une qui demande un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="dfcda-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="dfcda-108">Une ressource qui demande un redémarrage n’est pas à l’état souhaité tant que le redémarrage n’a pas eu lieu.</span><span class="sxs-lookup"><span data-stu-id="dfcda-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="dfcda-109">Après avoir rencontré une ressource qui échoue, le gestionnaire de configuration local continue à traiter les ressources tant qu’elles ne sont pas dépendantes de celle qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="dfcda-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="dfcda-110">Le statut global retourné par l’applet de commande `Get-DscConfigurationStatus` est le surensemble du statut de toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="dfcda-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="dfcda-111">L’état PendingReboot est un surensemble de l’état PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="dfcda-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="dfcda-112">Le tableau ci-dessous illustre les propriétés d’état et de statut résultantes dans quelques scénarios classiques.</span><span class="sxs-lookup"><span data-stu-id="dfcda-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="dfcda-113">Scénario</span><span class="sxs-lookup"><span data-stu-id="dfcda-113">Scenario</span></span>                    | <span data-ttu-id="dfcda-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="dfcda-114">LCMState</span></span>       | <span data-ttu-id="dfcda-115">Statut</span><span class="sxs-lookup"><span data-stu-id="dfcda-115">Status</span></span> | <span data-ttu-id="dfcda-116">Redémarrage demandé</span><span class="sxs-lookup"><span data-stu-id="dfcda-116">Reboot Requested</span></span>  | <span data-ttu-id="dfcda-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="dfcda-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="dfcda-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="dfcda-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="dfcda-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="dfcda-119">S**^**</span></span>                          | <span data-ttu-id="dfcda-120">Idle</span><span class="sxs-lookup"><span data-stu-id="dfcda-120">Idle</span></span>                 | <span data-ttu-id="dfcda-121">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="dfcda-121">Success</span></span>    | <span data-ttu-id="dfcda-122">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-122">$false</span></span>        | <span data-ttu-id="dfcda-123">S</span><span class="sxs-lookup"><span data-stu-id="dfcda-123">S</span></span>                            | <span data-ttu-id="dfcda-124">$null</span><span class="sxs-lookup"><span data-stu-id="dfcda-124">$null</span></span>                          |
   | <span data-ttu-id="dfcda-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="dfcda-125">F**^**</span></span>                          | <span data-ttu-id="dfcda-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfcda-126">PendingConfiguration</span></span> | <span data-ttu-id="dfcda-127">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-127">Failure</span></span>    | <span data-ttu-id="dfcda-128">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-128">$false</span></span>        | <span data-ttu-id="dfcda-129">$null</span><span class="sxs-lookup"><span data-stu-id="dfcda-129">$null</span></span>                        | <span data-ttu-id="dfcda-130">F</span><span class="sxs-lookup"><span data-stu-id="dfcda-130">F</span></span>                              |
   | <span data-ttu-id="dfcda-131">S,F</span><span class="sxs-lookup"><span data-stu-id="dfcda-131">S,F</span></span>                             | <span data-ttu-id="dfcda-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfcda-132">PendingConfiguration</span></span> | <span data-ttu-id="dfcda-133">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-133">Failure</span></span>    | <span data-ttu-id="dfcda-134">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-134">$false</span></span>        | <span data-ttu-id="dfcda-135">S</span><span class="sxs-lookup"><span data-stu-id="dfcda-135">S</span></span>                            | <span data-ttu-id="dfcda-136">F</span><span class="sxs-lookup"><span data-stu-id="dfcda-136">F</span></span>                              |
   | <span data-ttu-id="dfcda-137">F,S</span><span class="sxs-lookup"><span data-stu-id="dfcda-137">F,S</span></span>                             | <span data-ttu-id="dfcda-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfcda-138">PendingConfiguration</span></span> | <span data-ttu-id="dfcda-139">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-139">Failure</span></span>    | <span data-ttu-id="dfcda-140">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-140">$false</span></span>        | <span data-ttu-id="dfcda-141">S</span><span class="sxs-lookup"><span data-stu-id="dfcda-141">S</span></span>                            | <span data-ttu-id="dfcda-142">F</span><span class="sxs-lookup"><span data-stu-id="dfcda-142">F</span></span>                              |
   | <span data-ttu-id="dfcda-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="dfcda-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="dfcda-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfcda-144">PendingConfiguration</span></span> | <span data-ttu-id="dfcda-145">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-145">Failure</span></span>    | <span data-ttu-id="dfcda-146">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-146">$false</span></span>        | <span data-ttu-id="dfcda-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="dfcda-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="dfcda-148">F</span><span class="sxs-lookup"><span data-stu-id="dfcda-148">F</span></span>                              |
   | <span data-ttu-id="dfcda-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="dfcda-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="dfcda-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfcda-150">PendingConfiguration</span></span> | <span data-ttu-id="dfcda-151">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-151">Failure</span></span>    | <span data-ttu-id="dfcda-152">$false</span><span class="sxs-lookup"><span data-stu-id="dfcda-152">$false</span></span>        | <span data-ttu-id="dfcda-153">S</span><span class="sxs-lookup"><span data-stu-id="dfcda-153">S</span></span>                            | <span data-ttu-id="dfcda-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="dfcda-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="dfcda-155">S, r</span><span class="sxs-lookup"><span data-stu-id="dfcda-155">S, r</span></span>                            | <span data-ttu-id="dfcda-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="dfcda-156">PendingReboot</span></span>        | <span data-ttu-id="dfcda-157">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="dfcda-157">Success</span></span>    | <span data-ttu-id="dfcda-158">$true</span><span class="sxs-lookup"><span data-stu-id="dfcda-158">$true</span></span>         | <span data-ttu-id="dfcda-159">S</span><span class="sxs-lookup"><span data-stu-id="dfcda-159">S</span></span>                            | <span data-ttu-id="dfcda-160">r</span><span class="sxs-lookup"><span data-stu-id="dfcda-160">r</span></span>                              |
   | <span data-ttu-id="dfcda-161">F, r</span><span class="sxs-lookup"><span data-stu-id="dfcda-161">F, r</span></span>                            | <span data-ttu-id="dfcda-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="dfcda-162">PendingReboot</span></span>        | <span data-ttu-id="dfcda-163">Échec</span><span class="sxs-lookup"><span data-stu-id="dfcda-163">Failure</span></span>    | <span data-ttu-id="dfcda-164">$true</span><span class="sxs-lookup"><span data-stu-id="dfcda-164">$true</span></span>         | <span data-ttu-id="dfcda-165">$null</span><span class="sxs-lookup"><span data-stu-id="dfcda-165">$null</span></span>                        | <span data-ttu-id="dfcda-166">F, r</span><span class="sxs-lookup"><span data-stu-id="dfcda-166">F, r</span></span>                           |
   | <span data-ttu-id="dfcda-167">r, S</span><span class="sxs-lookup"><span data-stu-id="dfcda-167">r, S</span></span>                            | <span data-ttu-id="dfcda-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="dfcda-168">PendingReboot</span></span>        | <span data-ttu-id="dfcda-169">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="dfcda-169">Success</span></span>    | <span data-ttu-id="dfcda-170">$true</span><span class="sxs-lookup"><span data-stu-id="dfcda-170">$true</span></span>         | <span data-ttu-id="dfcda-171">$null</span><span class="sxs-lookup"><span data-stu-id="dfcda-171">$null</span></span>                        | <span data-ttu-id="dfcda-172">r</span><span class="sxs-lookup"><span data-stu-id="dfcda-172">r</span></span>                              |
   | <span data-ttu-id="dfcda-173">r, F</span><span class="sxs-lookup"><span data-stu-id="dfcda-173">r, F</span></span>                            | <span data-ttu-id="dfcda-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="dfcda-174">PendingReboot</span></span>        | <span data-ttu-id="dfcda-175">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="dfcda-175">Success</span></span>    | <span data-ttu-id="dfcda-176">$true</span><span class="sxs-lookup"><span data-stu-id="dfcda-176">$true</span></span>         | <span data-ttu-id="dfcda-177">$null</span><span class="sxs-lookup"><span data-stu-id="dfcda-177">$null</span></span>                        | <span data-ttu-id="dfcda-178">r</span><span class="sxs-lookup"><span data-stu-id="dfcda-178">r</span></span>                              |

   <span data-ttu-id="dfcda-179">^
   S<sub>i</sub> : série de ressources appliquée avec succès F<sub>i</sub> : série de ressources appliquée sans succès r : ressource qui nécessite un redémarrage \*</span><span class="sxs-lookup"><span data-stu-id="dfcda-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="dfcda-180">Améliorations apportées à l’applet de commande Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="dfcda-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="dfcda-181">Quelques améliorations ont été apportées à l’applet de commande `Get-DscConfigurationStatus` dans cette version.</span><span class="sxs-lookup"><span data-stu-id="dfcda-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="dfcda-182">Auparavant, la propriété StartDate des objets retournés par l’applet de commande était de type String.</span><span class="sxs-lookup"><span data-stu-id="dfcda-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="dfcda-183">Elle est désormais de type Datetime, ce qui simplifie la sélection et le filtrage complexes basés sur les propriétés intrinsèques d’un objet Datetime.</span><span class="sxs-lookup"><span data-stu-id="dfcda-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="dfcda-184">Voici un exemple qui retourne tous les enregistrements d’opérations DSC qui se sont produits, à ce jour, le même jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="dfcda-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="dfcda-185">Les enregistrements d’opérations qui ne modifient pas la configuration du nœud (par exemple les opérations en lecture seule) sont éliminés.</span><span class="sxs-lookup"><span data-stu-id="dfcda-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="dfcda-186">Par conséquent, les opérations `Test-DscConfiguration` et `Get-DscConfiguration` ne sont plus altérées dans les objets retournés par l’applet de commande `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="dfcda-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="dfcda-187">Les enregistrements de l’opération de définition de métaconfiguration sont ajoutés au retour de l’applet de commande `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="dfcda-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="dfcda-188">Voici un exemple de résultat retourné par l’applet de commande `Get-DscConfigurationStatus` –All.</span><span class="sxs-lookup"><span data-stu-id="dfcda-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="dfcda-189">Amélioration apportée à l’applet de commande Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dfcda-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="dfcda-190">Un nouveau champ LCMStateDetail a été ajouté à l’objet retourné par l’applet de commande `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="dfcda-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="dfcda-191">Ce champ est renseigné quand LCMState est « Occupé ».</span><span class="sxs-lookup"><span data-stu-id="dfcda-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="dfcda-192">Vous pouvez le récupérer avec l’applet de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="dfcda-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="dfcda-193">Voici un exemple de sortie d’une surveillance continue sur une configuration qui nécessite deux redémarrages sur un nœud distant.</span><span class="sxs-lookup"><span data-stu-id="dfcda-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
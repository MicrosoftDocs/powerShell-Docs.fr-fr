---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058979"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="6fbce-102">État unifié et cohérent et représentation de l’état</span><span class="sxs-lookup"><span data-stu-id="6fbce-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="6fbce-103">Une série d’améliorations ont été apportées dans cette version pour l’état du gestionnaire de configuration local et le statut DSC générés par des automatisations.</span><span class="sxs-lookup"><span data-stu-id="6fbce-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="6fbce-104">Il s’agit notamment de représentations de l’état et du statut unifiées et cohérentes, d’une propriété d’heure et de date facile à gérer pour les objets de statut retournés par l’applet de commande `Get-DscConfigurationStatus`, et d’une propriété améliorée pour les détails sur l’état du gestionnaire de configuration local retournés par l’applet de commande `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="6fbce-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="6fbce-105">La représentation de l’état du gestionnaire de configuration local et du statut de l’opération DSC a été revisitée et unifiée conformément aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="6fbce-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="6fbce-106">La ressource NotProcessed n’affecte pas l’état du gestionnaire de configuration local et le statut DSC.</span><span class="sxs-lookup"><span data-stu-id="6fbce-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="6fbce-107">Le gestionnaire de configuration local cesse de traiter les ressources dès qu’il en rencontre une qui demande un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="6fbce-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="6fbce-108">Une ressource qui demande un redémarrage n’est pas à l’état souhaité tant que le redémarrage n’a pas eu lieu.</span><span class="sxs-lookup"><span data-stu-id="6fbce-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="6fbce-109">Après avoir rencontré une ressource qui échoue, le gestionnaire de configuration local continue à traiter les ressources tant qu’elles ne sont pas dépendantes de celle qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="6fbce-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="6fbce-110">Le statut global retourné par l’applet de commande `Get-DscConfigurationStatus` est le surensemble du statut de toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="6fbce-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="6fbce-111">L’état PendingReboot est un surensemble de l’état PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="6fbce-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="6fbce-112">Le tableau ci-dessous illustre les propriétés d’état et de statut résultantes dans quelques scénarios classiques.</span><span class="sxs-lookup"><span data-stu-id="6fbce-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="6fbce-113">Scénario</span><span class="sxs-lookup"><span data-stu-id="6fbce-113">Scenario</span></span>                        | <span data-ttu-id="6fbce-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="6fbce-114">LCMState</span></span>             | <span data-ttu-id="6fbce-115">Statut</span><span class="sxs-lookup"><span data-stu-id="6fbce-115">Status</span></span>     | <span data-ttu-id="6fbce-116">Redémarrage demandé</span><span class="sxs-lookup"><span data-stu-id="6fbce-116">Reboot Requested</span></span> | <span data-ttu-id="6fbce-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="6fbce-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="6fbce-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="6fbce-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="6fbce-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="6fbce-120">Idle</span><span class="sxs-lookup"><span data-stu-id="6fbce-120">Idle</span></span>                 | <span data-ttu-id="6fbce-121">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="6fbce-121">Success</span></span>    | <span data-ttu-id="6fbce-122">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-122">$false</span></span>        | <span data-ttu-id="6fbce-123">S</span><span class="sxs-lookup"><span data-stu-id="6fbce-123">S</span></span>                            | <span data-ttu-id="6fbce-124">$null</span><span class="sxs-lookup"><span data-stu-id="6fbce-124">$null</span></span>                          |
| <span data-ttu-id="6fbce-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="6fbce-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fbce-126">PendingConfiguration</span></span> | <span data-ttu-id="6fbce-127">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-127">Failure</span></span>    | <span data-ttu-id="6fbce-128">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-128">$false</span></span>        | <span data-ttu-id="6fbce-129">$null</span><span class="sxs-lookup"><span data-stu-id="6fbce-129">$null</span></span>                        | <span data-ttu-id="6fbce-130">F</span><span class="sxs-lookup"><span data-stu-id="6fbce-130">F</span></span>                              |
| <span data-ttu-id="6fbce-131">S,F</span><span class="sxs-lookup"><span data-stu-id="6fbce-131">S,F</span></span>                             | <span data-ttu-id="6fbce-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fbce-132">PendingConfiguration</span></span> | <span data-ttu-id="6fbce-133">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-133">Failure</span></span>    | <span data-ttu-id="6fbce-134">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-134">$false</span></span>        | <span data-ttu-id="6fbce-135">S</span><span class="sxs-lookup"><span data-stu-id="6fbce-135">S</span></span>                            | <span data-ttu-id="6fbce-136">F</span><span class="sxs-lookup"><span data-stu-id="6fbce-136">F</span></span>                              |
| <span data-ttu-id="6fbce-137">F,S</span><span class="sxs-lookup"><span data-stu-id="6fbce-137">F,S</span></span>                             | <span data-ttu-id="6fbce-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fbce-138">PendingConfiguration</span></span> | <span data-ttu-id="6fbce-139">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-139">Failure</span></span>    | <span data-ttu-id="6fbce-140">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-140">$false</span></span>        | <span data-ttu-id="6fbce-141">S</span><span class="sxs-lookup"><span data-stu-id="6fbce-141">S</span></span>                            | <span data-ttu-id="6fbce-142">F</span><span class="sxs-lookup"><span data-stu-id="6fbce-142">F</span></span>                              |
| <span data-ttu-id="6fbce-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="6fbce-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fbce-144">PendingConfiguration</span></span> | <span data-ttu-id="6fbce-145">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-145">Failure</span></span>    | <span data-ttu-id="6fbce-146">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-146">$false</span></span>        | <span data-ttu-id="6fbce-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="6fbce-148">F</span><span class="sxs-lookup"><span data-stu-id="6fbce-148">F</span></span>                              |
| <span data-ttu-id="6fbce-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="6fbce-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fbce-150">PendingConfiguration</span></span> | <span data-ttu-id="6fbce-151">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-151">Failure</span></span>    | <span data-ttu-id="6fbce-152">$false</span><span class="sxs-lookup"><span data-stu-id="6fbce-152">$false</span></span>        | <span data-ttu-id="6fbce-153">S</span><span class="sxs-lookup"><span data-stu-id="6fbce-153">S</span></span>                            | <span data-ttu-id="6fbce-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fbce-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="6fbce-155">S, r</span><span class="sxs-lookup"><span data-stu-id="6fbce-155">S, r</span></span>                            | <span data-ttu-id="6fbce-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fbce-156">PendingReboot</span></span>        | <span data-ttu-id="6fbce-157">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="6fbce-157">Success</span></span>    | <span data-ttu-id="6fbce-158">$true</span><span class="sxs-lookup"><span data-stu-id="6fbce-158">$true</span></span>         | <span data-ttu-id="6fbce-159">S</span><span class="sxs-lookup"><span data-stu-id="6fbce-159">S</span></span>                            | <span data-ttu-id="6fbce-160">r</span><span class="sxs-lookup"><span data-stu-id="6fbce-160">r</span></span>                              |
| <span data-ttu-id="6fbce-161">F, r</span><span class="sxs-lookup"><span data-stu-id="6fbce-161">F, r</span></span>                            | <span data-ttu-id="6fbce-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fbce-162">PendingReboot</span></span>        | <span data-ttu-id="6fbce-163">Échec</span><span class="sxs-lookup"><span data-stu-id="6fbce-163">Failure</span></span>    | <span data-ttu-id="6fbce-164">$true</span><span class="sxs-lookup"><span data-stu-id="6fbce-164">$true</span></span>         | <span data-ttu-id="6fbce-165">$null</span><span class="sxs-lookup"><span data-stu-id="6fbce-165">$null</span></span>                        | <span data-ttu-id="6fbce-166">F, r</span><span class="sxs-lookup"><span data-stu-id="6fbce-166">F, r</span></span>                           |
| <span data-ttu-id="6fbce-167">r, S</span><span class="sxs-lookup"><span data-stu-id="6fbce-167">r, S</span></span>                            | <span data-ttu-id="6fbce-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fbce-168">PendingReboot</span></span>        | <span data-ttu-id="6fbce-169">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="6fbce-169">Success</span></span>    | <span data-ttu-id="6fbce-170">$true</span><span class="sxs-lookup"><span data-stu-id="6fbce-170">$true</span></span>         | <span data-ttu-id="6fbce-171">$null</span><span class="sxs-lookup"><span data-stu-id="6fbce-171">$null</span></span>                        | <span data-ttu-id="6fbce-172">r</span><span class="sxs-lookup"><span data-stu-id="6fbce-172">r</span></span>                              |
| <span data-ttu-id="6fbce-173">r, F</span><span class="sxs-lookup"><span data-stu-id="6fbce-173">r, F</span></span>                            | <span data-ttu-id="6fbce-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fbce-174">PendingReboot</span></span>        | <span data-ttu-id="6fbce-175">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="6fbce-175">Success</span></span>    | <span data-ttu-id="6fbce-176">$true</span><span class="sxs-lookup"><span data-stu-id="6fbce-176">$true</span></span>         | <span data-ttu-id="6fbce-177">$null</span><span class="sxs-lookup"><span data-stu-id="6fbce-177">$null</span></span>                        | <span data-ttu-id="6fbce-178">r</span><span class="sxs-lookup"><span data-stu-id="6fbce-178">r</span></span>                              |

- <span data-ttu-id="6fbce-179">S<sub>i</sub> : série de ressources appliquée avec succès</span><span class="sxs-lookup"><span data-stu-id="6fbce-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="6fbce-180">F<sub>i</sub> : série de ressources appliquée sans succès</span><span class="sxs-lookup"><span data-stu-id="6fbce-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="6fbce-181">r : ressource qui nécessite un redémarrage</span><span class="sxs-lookup"><span data-stu-id="6fbce-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="6fbce-182">Améliorations apportées à l’applet de commande Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6fbce-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="6fbce-183">Quelques améliorations ont été apportées à l’applet de commande `Get-DscConfigurationStatus` dans cette version.</span><span class="sxs-lookup"><span data-stu-id="6fbce-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="6fbce-184">Auparavant, la propriété StartDate des objets retournés par l’applet de commande était de type String.</span><span class="sxs-lookup"><span data-stu-id="6fbce-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="6fbce-185">Elle est désormais de type Datetime, ce qui simplifie la sélection et le filtrage complexes basés sur les propriétés intrinsèques d’un objet Datetime.</span><span class="sxs-lookup"><span data-stu-id="6fbce-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="6fbce-186">L’exemple suivant retourne tous les enregistrements d’opérations DSC qui ont eu lieu le même jour de la semaine que le jour actuel.</span><span class="sxs-lookup"><span data-stu-id="6fbce-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="6fbce-187">Les enregistrements d’opérations qui ne modifient pas la configuration du nœud (par exemple les opérations en lecture seule) sont éliminés.</span><span class="sxs-lookup"><span data-stu-id="6fbce-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="6fbce-188">Par conséquent, les opérations `Test-DscConfiguration` et `Get-DscConfiguration` ne sont plus altérées dans les objets retournés par l’applet de commande `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="6fbce-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="6fbce-189">Les enregistrements de l’opération de définition de métaconfiguration sont ajoutés au retour de l’applet de commande `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="6fbce-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="6fbce-190">Voici un exemple de résultat retourné par l’applet de commande `Get-DscConfigurationStatus –All`.</span><span class="sxs-lookup"><span data-stu-id="6fbce-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="6fbce-191">Amélioration apportée à l’applet de commande Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6fbce-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="6fbce-192">Un nouveau champ LCMStateDetail a été ajouté à l’objet retourné par l’applet de commande `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="6fbce-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="6fbce-193">Ce champ est renseigné quand LCMState est « Occupé ».</span><span class="sxs-lookup"><span data-stu-id="6fbce-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="6fbce-194">Vous pouvez le récupérer avec l’applet de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6fbce-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="6fbce-195">Voici un exemple de sortie d’une surveillance continue sur une configuration qui nécessite deux redémarrages sur un nœud distant.</span><span class="sxs-lookup"><span data-stu-id="6fbce-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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

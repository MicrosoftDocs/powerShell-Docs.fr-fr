---
description: Windows PowerShell crée un journal des événements Windows nommé « Windows PowerShell » pour enregistrer les événements Windows PowerShell. Vous pouvez consulter ce journal dans observateur d’événements ou en utilisant des applets de commande qui obtiennent des événements, tels que l’applet de commande `Get-EventLog` . Par défaut, les événements du moteur et du fournisseur Windows PowerShell sont enregistrés dans le journal des événements, mais vous pouvez utiliser les variables de préférence du journal des événements pour personnaliser le journal des événements. Par exemple, vous pouvez ajouter des événements sur les commandes Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208041"
---
# <a name="about-eventlogs"></a><span data-ttu-id="58560-107">À propos des EventLog</span><span class="sxs-lookup"><span data-stu-id="58560-107">About Eventlogs</span></span>

## <a name="short-description"></a><span data-ttu-id="58560-108">Description courte</span><span class="sxs-lookup"><span data-stu-id="58560-108">Short Description</span></span>

<span data-ttu-id="58560-109">Windows PowerShell crée un journal des événements Windows nommé « Windows PowerShell » pour enregistrer les événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-109">Windows PowerShell creates a Windows event log that is named "Windows PowerShell" to record Windows PowerShell events.</span></span> <span data-ttu-id="58560-110">Vous pouvez consulter ce journal dans observateur d’événements ou en utilisant des applets de commande qui obtiennent des événements, tels que l’applet de commande `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="58560-110">You can view this log in Event Viewer or by using cmdlets that get events, such as the `Get-EventLog` cmdlet.</span></span> <span data-ttu-id="58560-111">Par défaut, les événements du moteur et du fournisseur Windows PowerShell sont enregistrés dans le journal des événements, mais vous pouvez utiliser les variables de préférence du journal des événements pour personnaliser le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="58560-111">By default, Windows PowerShell engine and provider events are recorded in the event log, but you can use the event log preference variables to customize the event log.</span></span> <span data-ttu-id="58560-112">Par exemple, vous pouvez ajouter des événements sur les commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-112">For example, you can add events about Windows PowerShell commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="58560-113">Description longue</span><span class="sxs-lookup"><span data-stu-id="58560-113">Long Description</span></span>

<span data-ttu-id="58560-114">Le journal des événements Windows PowerShell enregistre les détails des opérations Windows PowerShell, telles que le démarrage et l’arrêt du moteur du programme, ainsi que le démarrage et l’arrêt des fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-114">The Windows PowerShell event log records details of Windows PowerShell operations, such as starting and stopping the program engine and starting and stopping the Windows PowerShell providers.</span></span> <span data-ttu-id="58560-115">Vous pouvez également consigner des détails sur les commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-115">You can also log details about Windows PowerShell commands.</span></span>

<span data-ttu-id="58560-116">Le journal des événements Windows PowerShell se trouve dans le groupe journaux des applications et des services.</span><span class="sxs-lookup"><span data-stu-id="58560-116">The Windows PowerShell event log is in the Application and Services Logs group.</span></span> <span data-ttu-id="58560-117">Le journal Windows PowerShell est un journal des événements classique qui n’utilise pas la technologie d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="58560-117">The Windows PowerShell log is a classic event log that does not use the Windows Eventing technology.</span></span> <span data-ttu-id="58560-118">Pour afficher le journal, utilisez les applets de commande conçues pour les journaux des événements classiques, tels que `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="58560-118">To view the log, use the cmdlets designed for classic event logs, such as `Get-EventLog`.</span></span>

## <a name="viewing-the-windows-powershell-event-log"></a><span data-ttu-id="58560-119">Affichage du journal des événements Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-119">Viewing the Windows PowerShell Event Log</span></span>

<span data-ttu-id="58560-120">Vous pouvez consulter le journal des événements Windows PowerShell dans observateur d’événements ou à l’aide des `Get-EventLog` applets de commande et `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="58560-120">You can view the Windows PowerShell event log in Event Viewer or by using the `Get-EventLog` and `Get-WmiObject` cmdlets.</span></span> <span data-ttu-id="58560-121">Pour afficher le contenu du journal Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-121">To view the contents of the Windows PowerShell log, type:</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

<span data-ttu-id="58560-122">Pour examiner les événements et leurs propriétés, utilisez l' `Sort-Object` applet de commande, l’applet de commande `Group-Object` et les applets de commande qui contiennent le `Format` verbe (les `Format` applets de commande).</span><span class="sxs-lookup"><span data-stu-id="58560-122">To examine the events and their properties, use the `Sort-Object` cmdlet, the `Group-Object` cmdlet, and the cmdlets that contain the `Format` verb (the `Format` cmdlets).</span></span>

<span data-ttu-id="58560-123">Par exemple, pour afficher les événements du journal regroupés par ID d’événement, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-123">For example, to view the events in the log grouped by the event ID, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

<span data-ttu-id="58560-124">Ou tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-124">Or, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

<span data-ttu-id="58560-125">Pour afficher tous les journaux des événements classiques, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-125">To view all the classic event logs, type:</span></span>

```powershell
Get-EventLog -List
```

<span data-ttu-id="58560-126">Vous pouvez également utiliser l' `Get-WmiObject` applet de commande pour utiliser les classes de Windows Management Instrumentation d’événements (WMI) pour examiner le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="58560-126">You can also use the `Get-WmiObject` cmdlet to use the event-related Windows Management Instrumentation (WMI) classes to examine the event log.</span></span> <span data-ttu-id="58560-127">Par exemple, pour afficher toutes les propriétés du fichier journal des événements, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-127">For example, to view all the properties of the event log file, type:</span></span>

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

<span data-ttu-id="58560-128">Pour rechercher les classes WMI liées aux événements Win32, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-128">To find the Win32 event-related WMI classes, type:</span></span>

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

<span data-ttu-id="58560-129">Pour plus d’informations, tapez « obtenir-Help obtenir-EventLog » et « obtenir-Help obtenir-WmiObject ».</span><span class="sxs-lookup"><span data-stu-id="58560-129">For more information, type "Get-Help Get-EventLog" and "Get-Help Get-WmiObject".</span></span>

## <a name="selecting-events-for-the-windows-powershell-event-log"></a><span data-ttu-id="58560-130">Sélection d’événements pour le journal des événements Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-130">Selecting Events for the Windows PowerShell Event Log</span></span>

<span data-ttu-id="58560-131">Vous pouvez utiliser les variables de préférence du journal des événements pour déterminer les événements qui sont enregistrés dans le journal des événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-131">You can use the event log preference variables to determine which events are recorded in the Windows PowerShell event log.</span></span>

<span data-ttu-id="58560-132">Il existe six variables de préférence du journal des événements : deux variables pour chacun des trois composants de journalisation : le moteur (le programme Windows PowerShell), les fournisseurs et les commandes.</span><span class="sxs-lookup"><span data-stu-id="58560-132">There are six event log preference variables; two variables for each of the three logging components: the engine (the Windows PowerShell program), the providers, and the commands.</span></span> <span data-ttu-id="58560-133">Les variables LifeCycleEvent journalisent les événements de démarrage et d’arrêt normaux.</span><span class="sxs-lookup"><span data-stu-id="58560-133">The LifeCycleEvent variables log normal starting and stopping events.</span></span> <span data-ttu-id="58560-134">Les variables d’intégrité journalisent les événements d’erreur.</span><span class="sxs-lookup"><span data-stu-id="58560-134">The Health variables log error events.</span></span>

<span data-ttu-id="58560-135">Le tableau suivant répertorie les variables de préférence du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="58560-135">The following table lists the event log preference variables.</span></span>

|<span data-ttu-id="58560-136">Variable</span><span class="sxs-lookup"><span data-stu-id="58560-136">Variable</span></span>                  |<span data-ttu-id="58560-137">Description</span><span class="sxs-lookup"><span data-stu-id="58560-137">Description</span></span>                                    |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="58560-138">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="58560-138">$LogEngineLifeCycleEvent</span></span>  |<span data-ttu-id="58560-139">Enregistre le démarrage et l’arrêt de PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-139">Logs the start and stop of PowerShell</span></span>          |
|<span data-ttu-id="58560-140">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="58560-140">$LogEngineHealthEvent</span></span>     |<span data-ttu-id="58560-141">Journalise les erreurs de programme PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-141">Logs PowerShell program errors</span></span>                 |
|<span data-ttu-id="58560-142">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="58560-142">$LogProviderLifeCycleEvent</span></span>|<span data-ttu-id="58560-143">Enregistre le démarrage et l’arrêt des fournisseurs PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-143">Logs the start and stop of PowerShell providers</span></span>|
|<span data-ttu-id="58560-144">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="58560-144">$LogProviderHealthEvent</span></span>   |<span data-ttu-id="58560-145">Journalise les erreurs du fournisseur PowerShell</span><span class="sxs-lookup"><span data-stu-id="58560-145">Logs PowerShell provider errors</span></span>                |
|<span data-ttu-id="58560-146">$LogCommandLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="58560-146">$LogCommandLifeCycleEvent</span></span> |<span data-ttu-id="58560-147">Enregistre le début et la fin des commandes</span><span class="sxs-lookup"><span data-stu-id="58560-147">Logs the starting and completion of commands</span></span>   |
|<span data-ttu-id="58560-148">$LogCommandHealthEvent</span><span class="sxs-lookup"><span data-stu-id="58560-148">$LogCommandHealthEvent</span></span>    |<span data-ttu-id="58560-149">Journalise les erreurs de commande</span><span class="sxs-lookup"><span data-stu-id="58560-149">Logs command errors</span></span>                            |

<span data-ttu-id="58560-150">(Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [about_Providers](about_Providers.md).)</span><span class="sxs-lookup"><span data-stu-id="58560-150">(For information about Windows PowerShell providers, see [about_Providers](about_Providers.md).)</span></span>

<span data-ttu-id="58560-151">Par défaut, seuls les types d’événements suivants sont activés :</span><span class="sxs-lookup"><span data-stu-id="58560-151">By default, only the following event types are enabled:</span></span>

* <span data-ttu-id="58560-152">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="58560-152">$LogEngineLifeCycleEvent</span></span>
* <span data-ttu-id="58560-153">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="58560-153">$LogEngineHealthEvent</span></span>
* <span data-ttu-id="58560-154">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="58560-154">$LogProviderLifeCycleEvent</span></span>
* <span data-ttu-id="58560-155">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="58560-155">$LogProviderHealthEvent</span></span>

<span data-ttu-id="58560-156">Pour activer un type d’événement, définissez la variable de préférence pour ce type d’événement sur $true.</span><span class="sxs-lookup"><span data-stu-id="58560-156">To enable an event type, set the preference variable for that event type to $true.</span></span> <span data-ttu-id="58560-157">Par exemple, pour activer les événements de cycle de vie de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-157">For example, to enable command life-cycle events, type:</span></span>

```powershell
$LogCommandLifeCycleEvent
```

<span data-ttu-id="58560-158">Ou tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-158">Or, type:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="58560-159">Pour désactiver un type d’événement, définissez la variable de préférence pour ce type d’événement sur $false.</span><span class="sxs-lookup"><span data-stu-id="58560-159">To disable an event type, set the preference variable for that event type to $false.</span></span> <span data-ttu-id="58560-160">Par exemple, pour désactiver les événements de cycle de vie de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="58560-160">For example, to disable command life-cycle events, type:</span></span>

```powershell
$LogProviderLifeCycleEvent = $false
```

<span data-ttu-id="58560-161">Vous pouvez désactiver n’importe quel événement, à l’exception des événements qui indiquent que le moteur Windows PowerShell et les fournisseurs de base sont démarrés.</span><span class="sxs-lookup"><span data-stu-id="58560-161">You can disable any event, except for the events that indicate that the Windows PowerShell engine and the core providers are started.</span></span> <span data-ttu-id="58560-162">Ces événements sont générés avant l’exécution des profils Windows PowerShell et avant que le programme hôte soit prêt à accepter les commandes.</span><span class="sxs-lookup"><span data-stu-id="58560-162">These events are generated before the Windows PowerShell profiles are run and before the host program is ready to accept commands.</span></span>

<span data-ttu-id="58560-163">Les paramètres de variable s’appliquent uniquement à la session Windows PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="58560-163">The variable settings apply only for the current Windows PowerShell session.</span></span>
<span data-ttu-id="58560-164">Pour les appliquer à toutes les sessions Windows PowerShell, ajoutez-les à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58560-164">To apply them to all Windows PowerShell sessions, add them to your Windows PowerShell profile.</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="58560-165">Journalisation des événements du module</span><span class="sxs-lookup"><span data-stu-id="58560-165">Logging Module Events</span></span>

<span data-ttu-id="58560-166">À compter de Windows PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande et des fonctions dans les modules et les composants logiciels enfichables Windows PowerShell en affectant la valeur TRUE à la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="58560-166">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets and functions in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="58560-167">Dans Windows PowerShell 2,0, cette fonctionnalité est disponible uniquement pour les composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="58560-167">In Windows PowerShell 2.0, this feature is available only for snap-ins.</span></span>

<span data-ttu-id="58560-168">Lorsque la valeur de la propriété LogPipelineExecutionDetails est TRUE ( `$true` ), Windows PowerShell écrit les événements d’exécution des applets de commande et des fonctions dans la session dans le journal Windows PowerShell dans observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="58560-168">When the LogPipelineExecutionDetails property value is TRUE (`$true`), Windows PowerShell writes cmdlet and function execution events in the session to the Windows PowerShell log in Event Viewer.</span></span> <span data-ttu-id="58560-169">Le paramètre est effectif uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="58560-169">The setting is effective only in the current session.</span></span>

<span data-ttu-id="58560-170">Pour activer la journalisation des événements d’exécution des applets de commande et des fonctions dans un module, utilisez la séquence de commandes suivante.</span><span class="sxs-lookup"><span data-stu-id="58560-170">To enable logging of execution events of cmdlets and functions in a module, use the following command sequence.</span></span>

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

<span data-ttu-id="58560-171">Pour activer la journalisation des événements d’exécution des applets de commande dans un composant logiciel enfichable, utilisez la séquence de commandes suivante.</span><span class="sxs-lookup"><span data-stu-id="58560-171">To enable logging of execution events of cmdlets in a snap-in, use the following command sequence.</span></span>

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

<span data-ttu-id="58560-172">Pour désactiver la journalisation, utilisez la même séquence de commandes pour définir la valeur de la propriété sur FALSe ( `$false` ).</span><span class="sxs-lookup"><span data-stu-id="58560-172">To disable logging, use the same command sequence to set the property value to FALSE (`$false`).</span></span>

<span data-ttu-id="58560-173">Vous pouvez également utiliser le paramètre de stratégie de groupe activer la journalisation des modules pour activer et désactiver la journalisation des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="58560-173">You can also use the "Turn on Module Logging" Group Policy setting to enable and disable module and snap-in logging.</span></span> <span data-ttu-id="58560-174">La valeur de la stratégie comprend une liste de noms de modules et de composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="58560-174">The policy value includes a list of module and snap-in names.</span></span> <span data-ttu-id="58560-175">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="58560-175">Wildcards are supported.</span></span>

<span data-ttu-id="58560-176">Lorsque l’opération « activer la journalisation des modules » est définie pour un module, la valeur de la propriété LogPipelineExecutionDetails du module est TRUE dans toutes les sessions et ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="58560-176">When "Turn on Module Logging" is set for a module, the value of the LogPipelineExecutionDetails property of the module is TRUE in all sessions and it cannot be changed.</span></span>

<span data-ttu-id="58560-177">Le paramètre de stratégie de groupe activer la journalisation du module se trouve dans les chemins d’accès stratégie de groupe suivants :</span><span class="sxs-lookup"><span data-stu-id="58560-177">The Turn On Module Logging group policy setting is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="58560-178">La stratégie de configuration utilisateur est prioritaire sur la stratégie de configuration de l’ordinateur, et les deux stratégies prennent la préférence sur la valeur de la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="58560-178">The User Configuration policy takes precedence over the Computer Configuration policy, and both policies take preference over the value of the LogPipelineExecutionDetails property of modules and snap-ins.</span></span>

<span data-ttu-id="58560-179">Pour plus d’informations sur ce paramètre de stratégie de groupe, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="58560-179">For more information about this Group Policy setting, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="security-and-auditing"></a><span data-ttu-id="58560-180">Sécurité et audit</span><span class="sxs-lookup"><span data-stu-id="58560-180">Security and Auditing</span></span>

<span data-ttu-id="58560-181">Le journal des événements Windows PowerShell est conçu pour indiquer l’activité et pour fournir des détails opérationnels pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="58560-181">The Windows PowerShell event log is designed to indicate activity and to provide operational details for troubleshooting.</span></span>

<span data-ttu-id="58560-182">Toutefois, comme la plupart des journaux des événements des applications Windows, le journal des événements de Windows PowerShell n’est pas conçu pour être sécurisé.</span><span class="sxs-lookup"><span data-stu-id="58560-182">However, like most Windows-based application event logs, the Windows PowerShell event log is not designed to be secure.</span></span> <span data-ttu-id="58560-183">Elle ne doit pas être utilisée pour auditer la sécurité ou pour enregistrer des informations confidentielles ou propriétaires.</span><span class="sxs-lookup"><span data-stu-id="58560-183">It should not be used to audit security or to record confidential or proprietary information.</span></span>

<span data-ttu-id="58560-184">Les journaux d’événements sont conçus pour être lus et compris par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="58560-184">Event logs are designed to be read and understood by users.</span></span> <span data-ttu-id="58560-185">Les utilisateurs peuvent lire et écrire dans le journal.</span><span class="sxs-lookup"><span data-stu-id="58560-185">Users can read from and write to the log.</span></span> <span data-ttu-id="58560-186">Un utilisateur malveillant peut lire un journal des événements sur un ordinateur local ou distant, enregistrer les fausses données, puis empêcher la journalisation de leurs activités.</span><span class="sxs-lookup"><span data-stu-id="58560-186">A malicious user could read an event log on a local or remote computer, record false data, and then prevent the logging of their activities.</span></span>

## <a name="notes"></a><span data-ttu-id="58560-187">Notes</span><span class="sxs-lookup"><span data-stu-id="58560-187">Notes</span></span>

<span data-ttu-id="58560-188">Les auteurs des auteurs de module peuvent ajouter des fonctionnalités de journalisation à leurs modules.</span><span class="sxs-lookup"><span data-stu-id="58560-188">Authors of module authors can add logging features to their modules.</span></span> <span data-ttu-id="58560-189">Pour plus d’informations, consultez [écriture d’un module Windows PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="58560-189">For more information, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="see-also"></a><span data-ttu-id="58560-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58560-190">See Also</span></span>

[<span data-ttu-id="58560-191">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="58560-191">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="58560-192">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="58560-192">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="58560-193">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="58560-193">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="58560-194">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="58560-194">about_Preference_Variables</span></span>](about_Preference_Variables.md)

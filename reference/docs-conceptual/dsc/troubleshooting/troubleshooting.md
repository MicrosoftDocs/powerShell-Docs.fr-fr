---
ms.date: 10/30/2018
keywords: dsc,powershell,configuration,installation
title: Résolution des problèmes liés à DSC
ms.openlocfilehash: 83e59b9f7148b52071d4782522ca7642027d795a
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692309"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="37b34-103">Résolution des problèmes liés à DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-103">Troubleshooting DSC</span></span>

<span data-ttu-id="37b34-104">_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="37b34-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="37b34-105">Cette rubrique décrit comment résoudre les problèmes liés à DSC quand ils se produisent.</span><span class="sxs-lookup"><span data-stu-id="37b34-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="37b34-106">Dépendance de WinRM</span><span class="sxs-lookup"><span data-stu-id="37b34-106">WinRM Dependency</span></span>

<span data-ttu-id="37b34-107">Windows PowerShell Desired State Configuration (DSC) dépend de WinRM.</span><span class="sxs-lookup"><span data-stu-id="37b34-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="37b34-108">WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7.</span><span class="sxs-lookup"><span data-stu-id="37b34-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="37b34-109">Exécutez `Set-WSManQuickConfig` dans une session Windows PowerShell avec élévation des privilèges pour activer WinRM.</span><span class="sxs-lookup"><span data-stu-id="37b34-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="37b34-110">Utilisation de l’applet de commande Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="37b34-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="37b34-111">L’applet de commande, [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) obtient des informations sur l’état de configuration à partir d’un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="37b34-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="37b34-112">Un objet enrichi est retourné. Il comprend des informations générales indiquant si l’exécution de la configuration a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="37b34-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="37b34-113">Vous pouvez explorer l’objet pour obtenir des détails sur l’exécution de la configuration, notamment :</span><span class="sxs-lookup"><span data-stu-id="37b34-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="37b34-114">Toutes les ressources qui ont échoué</span><span class="sxs-lookup"><span data-stu-id="37b34-114">All of the resources that failed</span></span>
- <span data-ttu-id="37b34-115">Toute ressource ayant demandé un redémarrage</span><span class="sxs-lookup"><span data-stu-id="37b34-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="37b34-116">Les paramètres de métaconfiguration au moment de l’exécution de la configuration</span><span class="sxs-lookup"><span data-stu-id="37b34-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="37b34-117">Etc.</span><span class="sxs-lookup"><span data-stu-id="37b34-117">Etc.</span></span>

<span data-ttu-id="37b34-118">Le jeu de paramètres suivant retourne les informations d’état pour la dernière exécution de configuration :</span><span class="sxs-lookup"><span data-stu-id="37b34-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

<span data-ttu-id="37b34-119">Le jeu de paramètres suivant retourne les informations d’état pour toutes les exécutions de configuration précédentes :</span><span class="sxs-lookup"><span data-stu-id="37b34-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="37b34-120"> Exemple</span><span class="sxs-lookup"><span data-stu-id="37b34-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="37b34-121">Mon script ne s’exécute pas : Utilisation des journaux DSC pour diagnostiquer les erreurs de script</span><span class="sxs-lookup"><span data-stu-id="37b34-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="37b34-122">Comme tous les logiciels Windows, DSC enregistre les erreurs et les événements dans des [journaux](/windows/desktop/EventLog/about-event-logging) qui peuvent être consultés dans l’[Observateur d’événements](https://support.microsoft.com/hub/4338813/windows-help).</span><span class="sxs-lookup"><span data-stu-id="37b34-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="37b34-123">L’examen de ces journaux peut vous aider à comprendre pourquoi une opération particulière a échoué et comment éviter que cela se reproduise.</span><span class="sxs-lookup"><span data-stu-id="37b34-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="37b34-124">L’écriture de scripts de configuration peut être compliquée. Ainsi, pour faciliter le suivi des erreurs pendant le processus de création, utilisez la ressource Log dans DSC pour suivre la progression de votre configuration dans le journal des événements d’analyse DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="37b34-125">Où se trouvent les journaux des événements DSC ?</span><span class="sxs-lookup"><span data-stu-id="37b34-125">Where are DSC event logs?</span></span>

<span data-ttu-id="37b34-126">Dans l’Observateur d’événements, les événements DSC se trouvent dans : **Journaux des applications et des services/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="37b34-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="37b34-127">L’applet de commande PowerShell correspondante [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) peut également être exécutée pour afficher les journaux des événements :</span><span class="sxs-lookup"><span data-stu-id="37b34-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="37b34-128">Comme indiqué ci-dessus, le nom du journal DSC principal est **Microsoft->Windows->DSC** (les autres noms de journaux dans Windows ne sont pas cités ici, par souci de concision).</span><span class="sxs-lookup"><span data-stu-id="37b34-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="37b34-129">Le nom principal est ajouté au nom du canal pour créer le nom complet du journal.</span><span class="sxs-lookup"><span data-stu-id="37b34-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="37b34-130">Le moteur DSC écrit principalement dans trois types de journaux : [les journaux des opérations, d’analyse et de débogage](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="37b34-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="37b34-131">Les journaux d’analyse et de débogage étant désactivés par défaut, vous devez les activer dans l’Observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="37b34-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="37b34-132">Pour ce faire, ouvrez l’Observateur d’événements en tapant Show-EventLog dans Windows PowerShell ou cliquez sur le bouton **Démarrer**, sur **Panneau de configuration**, **Outils d’administration**, puis **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="37b34-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="37b34-133">Dans le menu **Affichage** de l’Observateur d’événements, cliquez sur **Afficher les journaux d’analyse et de débogage**.</span><span class="sxs-lookup"><span data-stu-id="37b34-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="37b34-134">Le nom du journal du canal d’analyse est **Microsoft-Windows-Dsc/Analytic** et celui du canal de débogage est **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="37b34-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="37b34-135">Vous pouvez également utiliser l’utilitaire [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) pour activer les journaux, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="37b34-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="37b34-136">Que contiennent les journaux DSC ?</span><span class="sxs-lookup"><span data-stu-id="37b34-136">What do DSC logs contain?</span></span>

<span data-ttu-id="37b34-137">Les journaux DSC sont répartis sur les trois canaux de journal en fonction de l’importance du message.</span><span class="sxs-lookup"><span data-stu-id="37b34-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="37b34-138">Le journal des opérations dans DSC contient tous les messages d’erreur et peut être utilisé pour identifier un problème.</span><span class="sxs-lookup"><span data-stu-id="37b34-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="37b34-139">Le journal d’analyse contient un plus grand volume d’événements et peut identifier où se sont produites les erreurs.</span><span class="sxs-lookup"><span data-stu-id="37b34-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="37b34-140">Ce canal contient également des messages détaillés (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="37b34-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="37b34-141">Le journal de débogage contient des journaux qui peuvent vous aider à comprendre comment les erreurs se sont produites.</span><span class="sxs-lookup"><span data-stu-id="37b34-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="37b34-142">Les messages d’événement DSC sont structurés de telle sorte que chaque message d’événement commence par un ID de tâche représentant de façon unique une opération DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="37b34-143">L’exemple ci-dessous tente d’obtenir le message du premier événement enregistré dans le journal des opérations DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="37b34-144">Les événements DSC sont enregistrés dans une structure particulière qui permet à l’utilisateur de regrouper les événements d’une seule tâche DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="37b34-145">La structure est comme suit :</span><span class="sxs-lookup"><span data-stu-id="37b34-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="37b34-146">Collecte des événements d’une seule opération DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="37b34-147">Les journaux des événements DSC contiennent des événements générés par diverses opérations DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="37b34-148">Toutefois, vous êtes généralement intéressé par les détails d’une seule opération en particulier.</span><span class="sxs-lookup"><span data-stu-id="37b34-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="37b34-149">Tous les journaux DSC peuvent être regroupés par la propriété d’ID de tâche, qui est unique pour chaque opération DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="37b34-150">L’ID de tâche est affiché comme première valeur de propriété de tous les événements DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="37b34-151">Les étapes suivantes décrivent comment regrouper tous les événements dans une structure de tableau groupée.</span><span class="sxs-lookup"><span data-stu-id="37b34-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="37b34-152">Ici, la variable `$SeparateDscOperations` contient les journaux regroupés par ID de tâche.</span><span class="sxs-lookup"><span data-stu-id="37b34-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="37b34-153">Chaque élément du tableau de cette variable représente un groupe d’événements enregistrés par une opération DSC différente, ce qui donne accès à davantage d’informations sur les journaux.</span><span class="sxs-lookup"><span data-stu-id="37b34-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="37b34-154">Vous pouvez extraire les données de la variable `$SeparateDscOperations` à l’aide de [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="37b34-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="37b34-155">Voici cinq scénarios dans lesquels vous pouvez extraire les données pour résoudre les problèmes liés à DSC :</span><span class="sxs-lookup"><span data-stu-id="37b34-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="37b34-156">1 : Échecs des opérations</span><span class="sxs-lookup"><span data-stu-id="37b34-156">1: Operations failures</span></span>

<span data-ttu-id="37b34-157">Tous les événements sont associés à des [niveaux de gravité](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="37b34-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="37b34-158">Ces informations peuvent être utilisées pour identifier les événements d’erreur :</span><span class="sxs-lookup"><span data-stu-id="37b34-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="37b34-159">2 : Détails des opérations exécutées au cours de la dernière demi-heure</span><span class="sxs-lookup"><span data-stu-id="37b34-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="37b34-160">`TimeCreated`, une propriété de chaque événement Windows, indique l’heure de création de l’événement.</span><span class="sxs-lookup"><span data-stu-id="37b34-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="37b34-161">Vous pouvez comparer cette propriété avec un objet date/heure particulier pour filtrer tous les événements :</span><span class="sxs-lookup"><span data-stu-id="37b34-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="37b34-162">3 : Messages de la dernière opération</span><span class="sxs-lookup"><span data-stu-id="37b34-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="37b34-163">La dernière opération est stockée dans le premier index du groupe de tableaux `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="37b34-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="37b34-164">L’interrogation des messages du groupe pour l’index 0 retourne tous les messages de la dernière opération :</span><span class="sxs-lookup"><span data-stu-id="37b34-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="37b34-165">4 : Messages d’erreur enregistrés pour les dernières opérations ayant échoué</span><span class="sxs-lookup"><span data-stu-id="37b34-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="37b34-166">`$SeparateDscOperations[0].Group` contient un ensemble d’événements pour la dernière opération.</span><span class="sxs-lookup"><span data-stu-id="37b34-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="37b34-167">Exécutez l’applet de commande `Where-Object` pour filtrer les événements selon le nom d’affichage du niveau.</span><span class="sxs-lookup"><span data-stu-id="37b34-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="37b34-168">Les résultats sont stockés dans la variable `$myFailedEvent`, qui peut être examinée pour obtenir le message d’événement :</span><span class="sxs-lookup"><span data-stu-id="37b34-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="37b34-169">5 : Tous les événements générés pour un ID de tâche en particulier.</span><span class="sxs-lookup"><span data-stu-id="37b34-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="37b34-170">`$SeparateDscOperations` est un tableau de groupes, chacun d’eux a comme nom l’ID de tâche unique.</span><span class="sxs-lookup"><span data-stu-id="37b34-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="37b34-171">En exécutant l’applet de commande `Where-Object`, vous pouvez extraire les groupes d’événements qui ont un ID de tâche particulier :</span><span class="sxs-lookup"><span data-stu-id="37b34-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="37b34-172">Utilisation de xDscDiagnostics pour analyser les journaux DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="37b34-173">**xDscDiagnostics** est un module PowerShell qui se compose de plusieurs fonctions permettant d’analyser les échecs DSC sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37b34-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="37b34-174">Ces fonctions peuvent vous aider à identifier tous les événements locaux des dernières opérations DSC ou les événements DSC sur des ordinateurs distants (avec des informations d’identification valides).</span><span class="sxs-lookup"><span data-stu-id="37b34-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="37b34-175">Ici, le terme opération DSC est utilisé pour définir une exécution DSC unique du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="37b34-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="37b34-176">Par exemple, `Test-DscConfiguration` est une opération DSC à part entière.</span><span class="sxs-lookup"><span data-stu-id="37b34-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="37b34-177">De même, chaque autre applet de commande dans DSC (telle que `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) peut être identifiée comme une opération DSC à part entière.</span><span class="sxs-lookup"><span data-stu-id="37b34-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="37b34-178">Les fonctions sont expliquées dans [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="37b34-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="37b34-179">Vous accédez à l’aide en exécutant `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="37b34-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="37b34-180">Obtention de détails des opérations DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-180">Getting details of DSC operations</span></span>

<span data-ttu-id="37b34-181">La fonction `Get-xDscOperation` vous permet de rechercher les résultats des opérations DSC qui s’exécutent sur un ou plusieurs ordinateurs, et de retourner un objet qui contient la collection d’événements produits par chaque opération DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="37b34-182">Par exemple, dans la sortie suivante, trois commandes ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="37b34-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="37b34-183">La première a réussi et les deux autres ont échoué.</span><span class="sxs-lookup"><span data-stu-id="37b34-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="37b34-184">Ces résultats sont résumés dans la sortie de `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="37b34-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="37b34-185">Vous pouvez également spécifier que vous voulez uniquement les résultats des opérations les plus récentes à l’aide du paramètre `Newest` :</span><span class="sxs-lookup"><span data-stu-id="37b34-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="37b34-186">Obtention des détails des événements DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-186">Getting details of DSC events</span></span>

<span data-ttu-id="37b34-187">L’applet de commande `Trace-xDscOperation`retourne un objet qui contient une collection d’événements, leur type et la sortie de message générée à partir d’une opération DSC particulière.</span><span class="sxs-lookup"><span data-stu-id="37b34-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="37b34-188">En règle générale, quand vous trouvez une erreur dans une opération à l’aide de `Get-xDscOperation`, vous tracez l’opération pour déterminer lequel des événements a entraîné un échec.</span><span class="sxs-lookup"><span data-stu-id="37b34-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="37b34-189">Utilisez le paramètre `SequenceID` afin d’obtenir les événements d’une opération spécifique pour un ordinateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="37b34-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="37b34-190">Par exemple, si vous spécifiez une valeur de 9 pour `SequenceID`, `Trace-xDscOperaion` obtient la trace de la neuvième opération DSC à partir de la dernière opération :</span><span class="sxs-lookup"><span data-stu-id="37b34-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="37b34-191">Passez le **GUID** affecté à une opération DSC spécifique (comme retourné par l’applet de commande `Get-xDscOperation`) pour obtenir les détails de l’événement pour cette opération DSC :</span><span class="sxs-lookup"><span data-stu-id="37b34-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="37b34-192">Notez qu’étant donné que `Trace-xDscOperation` regroupe les événements des journaux d’analyse, de débogage et des opérations, vous êtes invité à activer ces journaux comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="37b34-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="37b34-193">Vous pouvez aussi collecter des informations sur les événements en enregistrant la sortie de `Trace-xDscOperation` dans une variable.</span><span class="sxs-lookup"><span data-stu-id="37b34-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="37b34-194">Vous pouvez utiliser les commandes suivantes pour afficher tous les événements d’une opération DSC particulière.</span><span class="sxs-lookup"><span data-stu-id="37b34-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="37b34-195">Cette commande génère les mêmes résultats que l’applet de commande `Get-WinEvent`, comme dans la sortie ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="37b34-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="37b34-196">Idéalement, commencez par utiliser `Get-xDscOperation` pour répertorier les dernières exécutions de configuration DSC sur vos ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="37b34-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="37b34-197">Ensuite, vous pouvez examiner chaque opération (à l’aide de son ID de séquence ou de tâche) avec `Trace-xDscOperation` pour découvrir ce qu’elle a effectué en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="37b34-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="37b34-198">Obtention des événements d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="37b34-198">Getting events for a remote computer</span></span>

<span data-ttu-id="37b34-199">Utilisez le paramètre `ComputerName` de l’applet de commande `Trace-xDscOperation` pour obtenir les détails des événements d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="37b34-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="37b34-200">Avant cela, vous devez créer une règle de pare-feu pour autoriser l’administration à distance sur l’ordinateur distant :</span><span class="sxs-lookup"><span data-stu-id="37b34-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="37b34-201">Vous pouvez maintenant spécifier cet ordinateur dans votre appel à `Trace-xDscOperation` :</span><span class="sxs-lookup"><span data-stu-id="37b34-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="37b34-202">Mes ressources ne sont pas mises à jour : Comment réinitialiser le cache</span><span class="sxs-lookup"><span data-stu-id="37b34-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="37b34-203">Le moteur DSC met en cache les ressources implémentées comme module PowerShell pour des raisons d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="37b34-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="37b34-204">Toutefois, cela peut entraîner des problèmes quand vous créez et testez une ressource simultanément, car DSC charge la version mise en cache tant que le processus n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="37b34-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="37b34-205">La seule façon pour que DSC charge la version la plus récente est d’arrêter explicitement le processus qui héberge le moteur DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="37b34-206">De même, quand vous exécutez `Start-DscConfiguration`, une fois que vous avez ajouté et modifié une ressource personnalisée, la modification peut ne pas s’exécuter tant que l’ordinateur n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="37b34-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="37b34-207">Ce comportement s’explique par le fait que DSC s’exécute dans le processus hôte du fournisseur WMI (WmiPrvSE) et qu’en général, il existe plusieurs instances de WmiPrvSE qui s’exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="37b34-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="37b34-208">Quand vous redémarrez, le processus hôte est redémarré et le cache est effacé.</span><span class="sxs-lookup"><span data-stu-id="37b34-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="37b34-209">Pour recycler la configuration et effacer le cache sans redémarrer l’ordinateur, vous devez arrêter, puis redémarrer le processus hôte.</span><span class="sxs-lookup"><span data-stu-id="37b34-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="37b34-210">Vous pouvez le faire pour chaque instance : vous identifiez le processus, l’arrêtez et le redémarrez.</span><span class="sxs-lookup"><span data-stu-id="37b34-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="37b34-211">Vous pouvez également utiliser `DebugMode`, comme illustré ci-dessous, pour recharger la ressource DSC PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37b34-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="37b34-212">Pour identifier le processus qui héberge le moteur DSC et l’arrêter pour chaque instance, vous pouvez répertorier les ID de processus de WmiPrvSE, qui héberge le moteur DSC.</span><span class="sxs-lookup"><span data-stu-id="37b34-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="37b34-213">Ensuite, pour mettre à jour le fournisseur, arrêtez le processus WmiPrvSE à l’aide des commandes ci-dessous, puis exécutez **Start-DscConfiguration** de nouveau.</span><span class="sxs-lookup"><span data-stu-id="37b34-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="37b34-214">Utilisation de DebugMode</span><span class="sxs-lookup"><span data-stu-id="37b34-214">Using DebugMode</span></span>

<span data-ttu-id="37b34-215">Vous pouvez configurer le gestionnaire de configuration local DSC de façon à utiliser `DebugMode` pour toujours effacer le cache lors du redémarrage du processus hôte.</span><span class="sxs-lookup"><span data-stu-id="37b34-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="37b34-216">Quand la valeur est **TRUE**, elle force le moteur à toujours recharger la ressource DSC PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37b34-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="37b34-217">Une fois que vous avez écrit votre ressource, vous pouvez la redéfinir avec la valeur **FALSE** pour que le moteur mette de nouveau en cache les modules.</span><span class="sxs-lookup"><span data-stu-id="37b34-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="37b34-218">La démonstration suivante explique comment `DebugMode` peut actualiser le cache de façon automatique.</span><span class="sxs-lookup"><span data-stu-id="37b34-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="37b34-219">Tout d’abord, examinons la configuration par défaut :</span><span class="sxs-lookup"><span data-stu-id="37b34-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="37b34-220">Vous pouvez voir que `DebugMode` a la valeur **« None »**.</span><span class="sxs-lookup"><span data-stu-id="37b34-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="37b34-221">Pour configurer la démonstration de `DebugMode`, utilisez la ressource PowerShell suivante :</span><span class="sxs-lookup"><span data-stu-id="37b34-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="37b34-222">Maintenant, créez une configuration à l’aide de la ressource ci-dessus et appelez-la `TestProviderDebugMode` :</span><span class="sxs-lookup"><span data-stu-id="37b34-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="37b34-223">Vous voyez que le contenu du fichier `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` est **1**.</span><span class="sxs-lookup"><span data-stu-id="37b34-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="37b34-224">Ensuite, mettez à jour le code du fournisseur à l’aide du script suivant :</span><span class="sxs-lookup"><span data-stu-id="37b34-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="37b34-225">Ce script génère un nombre aléatoire et met à jour le code du fournisseur en conséquence.</span><span class="sxs-lookup"><span data-stu-id="37b34-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="37b34-226">Quand `DebugMode` a la valeur false, le contenu du fichier «  **$env :SystemDrive\OutputFromTestProviderDebugMode.txt** » est toujours le même.</span><span class="sxs-lookup"><span data-stu-id="37b34-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="37b34-227">À présent, définissez `DebugMode` sur **« ForceModuleImport »** dans votre script de configuration :</span><span class="sxs-lookup"><span data-stu-id="37b34-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="37b34-228">Quand vous réexécutez le script ci-dessus, le contenu du fichier change à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="37b34-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="37b34-229">(Vous pouvez exécuter `Get-DscConfiguration` pour le vérifier.)</span><span class="sxs-lookup"><span data-stu-id="37b34-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="37b34-230">Voici le résultat de deux exécutions supplémentaires (les résultats peuvent être différents quand vous exécutez le script) :</span><span class="sxs-lookup"><span data-stu-id="37b34-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="37b34-231">DSC retourne « code de réponse inattendu InternalServerError » lors de l’inscription auprès du serveur Pull Windows</span><span class="sxs-lookup"><span data-stu-id="37b34-231">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="37b34-232">Lorsque vous appliquez une métaconfiguration à un serveur pour l’inscrire auprès d’une instance de serveur Pull Windows, vous risquez de rencontrer l’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="37b34-232">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="37b34-233">Ce cas peut se produire lorsque le certificat utilisé sur le serveur pour chiffrer le trafic a un nom commun (CN) qui est différent du nom DNS utilisé par le nœud pour résoudre l’URL.</span><span class="sxs-lookup"><span data-stu-id="37b34-233">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span>
<span data-ttu-id="37b34-234">Mettez à jour l’instance du serveur Pull Windows pour utiliser un certificat avec un nom correct.</span><span class="sxs-lookup"><span data-stu-id="37b34-234">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a><span data-ttu-id="37b34-235">Erreur lors de l’exécution de Sysprep après l’application d’une configuration DSC</span><span class="sxs-lookup"><span data-stu-id="37b34-235">Error when running Sysprep after applying a DSC Configuration</span></span>

<span data-ttu-id="37b34-236">Lorsque vous tentez d’exécuter Sysprep pour généraliser un serveur Windows après l’application d’une configuration DSC, vous pouvez rencontrer l’erreur suivante.</span><span class="sxs-lookup"><span data-stu-id="37b34-236">When attempting to run Sysprep to generalize a Windows Server after applying a DSC configuration, you might encounter the following error.</span></span>

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

<span data-ttu-id="37b34-237">La généralisation d’un serveur une fois qu’il a été configuré avec Windows PowerShell Desired State Configuration n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="37b34-237">Generalizing a server after it has been configured using Windows PowerShell Desired State Configuration is not a supported scenario.</span></span>  <span data-ttu-id="37b34-238">Appliquez plutôt des configurations à Windows à l’issue de la phase Spécialiser du programme d’installation Windows.</span><span class="sxs-lookup"><span data-stu-id="37b34-238">Instead, apply configurations to Windows after the Specialize phase of Windows Setup has completed.</span></span>

## <a name="see-also"></a><span data-ttu-id="37b34-239"> Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37b34-239">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="37b34-240">Concepts</span><span class="sxs-lookup"><span data-stu-id="37b34-240">Concepts</span></span>

- [<span data-ttu-id="37b34-241">Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="37b34-241">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="37b34-242">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="37b34-242">Other Resources</span></span>

- [<span data-ttu-id="37b34-243">Windows PowerShell Desired State Configuration Cmdlets</span><span class="sxs-lookup"><span data-stu-id="37b34-243">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)

---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205430"
---
# <span data-ttu-id="b8d6a-103">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="b8d6a-103">New-PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="b8d6a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b8d6a-104">SYNOPSIS</span></span>

<span data-ttu-id="b8d6a-105">Crée un objet qui contient les options de configuration de session pour les sessions de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-105">Creates an object that contains session configuration options for workflow sessions.</span></span>

## <span data-ttu-id="b8d6a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8d6a-106">SYNTAX</span></span>

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="b8d6a-107">Description</span><span class="sxs-lookup"><span data-stu-id="b8d6a-107">DESCRIPTION</span></span>

<span data-ttu-id="b8d6a-108">L' `New-PSWorkflowExecutionOption` applet de commande crée un objet qui contient des options avancées pour les configurations de session de workflow, c’est-à-dire des configurations de session conçues pour exécuter des flux de travail Windows PowerShell Workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-108">The `New-PSWorkflowExecutionOption` cmdlet creates an object that contains advanced options for workflow session configurations, that is session configurations designed to run Windows PowerShell Workflow workflows.</span></span>

<span data-ttu-id="b8d6a-109">Vous pouvez utiliser l’objet **PSWorkflowExecutionOption** qui `New-PSWorkflowExecutionOption` génère comme valeur du paramètre **SessionTypeOption** des applets de commande qui créent ou modifient une configuration de session, comme `Register-PSSessionConfiguration` les `Set-PSSessionConfiguration` applets de commande et.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-109">You can use the **PSWorkflowExecutionOption** object that `New-PSWorkflowExecutionOption` generates as the value of the **SessionTypeOption** parameter of cmdlets that create or change a session configuration, such as the `Register-PSSessionConfiguration` and `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="b8d6a-110">Chaque paramètre de l' `New-PSWorkflowExecutionOption` applet de commande représente une propriété de l’objet d’option de configuration de session de workflow que l’applet de commande retourne.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-110">Each parameter of the `New-PSWorkflowExecutionOption` cmdlet represents a property of the workflow session configuration option object that the cmdlet returns.</span></span> <span data-ttu-id="b8d6a-111">Si vous omettez un paramètre, l'applet de commande crée l'objet avec une valeur par défaut pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-111">If you omit a parameter, the cmdlet creates the object with a default value for the property.</span></span>

<span data-ttu-id="b8d6a-112">L' `New-PSWorkflowExecutionOption` applet de commande fait partie de la fonctionnalité de flux de travail Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-112">The `New-PSWorkflowExecutionOption` cmdlet is part of the Windows PowerShell Workflow feature.</span></span>

<span data-ttu-id="b8d6a-113">Vous pouvez également ajouter des paramètres communs de workflow à cette commande.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-113">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="b8d6a-114">Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b8d6a-114">For more information about workflow common parameters, see [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span></span>

<span data-ttu-id="b8d6a-115">Cette applet de commande est introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-115">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b8d6a-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b8d6a-116">EXAMPLES</span></span>

### <span data-ttu-id="b8d6a-117">Exemple 1 : créer un objet d’options de workflow</span><span class="sxs-lookup"><span data-stu-id="b8d6a-117">Example 1: Create a Workflow Options Object</span></span>

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

<span data-ttu-id="b8d6a-118">Cette commande utilise la `New-PSWorkflowExecutionOption` cmdlet pour augmenter la valeur de **MaxSessionsPerWorkflow** à 10 et réduire la valeur de **MaxDisconnectedSessions** à 200.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-118">This command uses the `New-PSWorkflowExecutionOption` cmdlet to increase the **MaxSessionsPerWorkflow** value to 10 and decrease the **MaxDisconnectedSessions** value to 200.</span></span>

<span data-ttu-id="b8d6a-119">La sortie illustre l'objet retourné par l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-119">The output shows the object that the cmdlet returns.</span></span>

### <span data-ttu-id="b8d6a-120">Exemple 2 : utilisation d’un objet d’options de workflow</span><span class="sxs-lookup"><span data-stu-id="b8d6a-120">Example 2: Using a Workflow Options Object</span></span>

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="b8d6a-121">Les deux premières commandes créent un nouvel objet de configuration de session et l’inscrivent.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-121">The first two commands create a new session configuration object and registers it.</span></span>

<span data-ttu-id="b8d6a-122">La troisième commande utilise l' `Get-PSSessionConfiguration` applet de commande pour obtenir la configuration de session ITWorkflows et le `Format-List` pour afficher toutes les propriétés de la configuration de session dans une liste. La sortie montre les options de flux de travail dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-122">The third command uses the `Get-PSSessionConfiguration` cmdlet to the get the ITWorkflows session configuration and the `Format-List` to display all properties of the session configuration in a list.The output shows that the workflow options in the session configuration.</span></span> <span data-ttu-id="b8d6a-123">Plus précisément, la configuration de session a une propriété **MaxSessionsPerWorkflow** avec la valeur 10 et une propriété **MaxDisconnectedSessions** avec la valeur 200.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-123">Specifically, the session configuration has a **MaxSessionsPerWorkflow** property with a value of 10 and a **MaxDisconnectedSessions** property with a value of 200.</span></span>

## <span data-ttu-id="b8d6a-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8d6a-124">PARAMETERS</span></span>

### <span data-ttu-id="b8d6a-125">-ActivityProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b8d6a-125">-ActivityProcessIdleTimeoutSec</span></span>

<span data-ttu-id="b8d6a-126">Détermine la durée pendant laquelle chaque processus hôte d'activité est maintenu une fois que le processus est devenu inactif.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-126">Determines how long each activity host process is maintained after the process becomes idle.</span></span> <span data-ttu-id="b8d6a-127">Quand le délai expire, le processus se ferme.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-127">When the interval expires, the process closes.</span></span>

<span data-ttu-id="b8d6a-128">Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-128">Enter a value in seconds.</span></span> <span data-ttu-id="b8d6a-129">La valeur par défaut est 60.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-129">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-130">-AllowedActivity</span><span class="sxs-lookup"><span data-stu-id="b8d6a-130">-AllowedActivity</span></span>

<span data-ttu-id="b8d6a-131">Spécifie les activités autorisées à s'exécuter dans la session.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-131">Specifies the activities that are permitted to run in the session.</span></span>

<span data-ttu-id="b8d6a-132">Entrez les noms d’activité qualifiés par un espace de noms, tels que `Microsoft.Powershell.HyperV.Activities.*` .</span><span class="sxs-lookup"><span data-stu-id="b8d6a-132">Enter namespace-qualified activity names, such as `Microsoft.Powershell.HyperV.Activities.*`.</span></span>
<span data-ttu-id="b8d6a-133">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-133">Wildcard characters are supported.</span></span> <span data-ttu-id="b8d6a-134">La valeur par défaut, **PSDefaultActivities** , inclut les activités Windows Workflow Foundation intégrées et les activités qui représentent les applets de commande Windows PowerShell principales.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-134">The default value, **PSDefaultActivities** , includes the built-in Windows Workflow Foundation activities and the activities that represent the Windows PowerShell Core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-135">-EnableValidation</span><span class="sxs-lookup"><span data-stu-id="b8d6a-135">-EnableValidation</span></span>

<span data-ttu-id="b8d6a-136">Vérifie que toutes les activités de workflow dans la session sont incluses dans la liste des activités autorisées.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-136">Verifies that all workflow activities in the session are included in the allowed activities list.</span></span>

<span data-ttu-id="b8d6a-137">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-137">The default value is True.</span></span> <span data-ttu-id="b8d6a-138">Pour désactiver la validation, utilisez le format de commande suivant : `-EnableValidation:$false` .</span><span class="sxs-lookup"><span data-stu-id="b8d6a-138">To disable validation, use the following command format: `-EnableValidation:$false`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-139">-MaxActivityProcesses</span><span class="sxs-lookup"><span data-stu-id="b8d6a-139">-MaxActivityProcesses</span></span>

<span data-ttu-id="b8d6a-140">Spécifie le nombre maximal de processus qui peuvent être créés dans la session pour prendre en charge des activités de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-140">Specifies the maximum number of processes that can be created in the session to support workflow activities.</span></span> <span data-ttu-id="b8d6a-141">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-141">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-142">-MaxConnectedSessions</span><span class="sxs-lookup"><span data-stu-id="b8d6a-142">-MaxConnectedSessions</span></span>

<span data-ttu-id="b8d6a-143">Spécifie le nombre maximal de sessions à distance qui sont dans un état opérationnel.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-143">Specifies the maximum number of remote sessions that are in an operational state.</span></span> <span data-ttu-id="b8d6a-144">Ce quota est appliqué aux sessions connectées à tous les nœuds distants (ordinateurs cibles).</span><span class="sxs-lookup"><span data-stu-id="b8d6a-144">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="b8d6a-145">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-145">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-146">-MaxDisconnectedSessions</span><span class="sxs-lookup"><span data-stu-id="b8d6a-146">-MaxDisconnectedSessions</span></span>

<span data-ttu-id="b8d6a-147">Spécifie le nombre maximal de sessions à distance qui sont dans un état déconnecté.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-147">Specifies the maximum number of remote sessions that are in a disconnected state.</span></span> <span data-ttu-id="b8d6a-148">Ce quota est appliqué aux sessions connectées à tous les nœuds distants (ordinateurs cibles).</span><span class="sxs-lookup"><span data-stu-id="b8d6a-148">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="b8d6a-149">La valeur par défaut est 1000.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-149">The default value is 1000.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-150">-MaxPersistenceStoreSizeGB</span><span class="sxs-lookup"><span data-stu-id="b8d6a-150">-MaxPersistenceStoreSizeGB</span></span>

<span data-ttu-id="b8d6a-151">Spécifie la taille maximale, en gigaoctets, du magasin de persistance alloué aux workflows exécutés dans la session.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-151">Specifies the maximum size, in gigabytes, of the persistence store allocated to workflows that run in the session.</span></span> <span data-ttu-id="b8d6a-152">Quand la taille est dépassée, le magasin de persistance est développé pour enregistrer toutes les données persistantes, mais un avertissement s'affiche et un message est écrit dans le journal des événements du workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-152">When the size is exceeded, the persistence store is expanded to save all persisted data, but a warning is displayed and a message is written to the workflow event log.</span></span> <span data-ttu-id="b8d6a-153">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-153">The default value is 10.</span></span>

<span data-ttu-id="b8d6a-154">Le magasin de persistance contient des données pour toutes les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-154">The persistence store contains data for all workflow jobs.</span></span> <span data-ttu-id="b8d6a-155">La possibilité de stocker des données permet la reprise des tâches sans perte d'état.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-155">The ability to store data allows the jobs to resume without losing state.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-156">-MaxRunningWorkflows</span><span class="sxs-lookup"><span data-stu-id="b8d6a-156">-MaxRunningWorkflows</span></span>

<span data-ttu-id="b8d6a-157">Spécifie le nombre maximal de workflows qui peuvent s'exécuter simultanément dans la session.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-157">Specifies that maximum number of workflows that can run in the session concurrently.</span></span>
<span data-ttu-id="b8d6a-158">La valeur par défaut est 30.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-158">The default value is 30.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-159">-MaxSessionsPerRemoteNode</span><span class="sxs-lookup"><span data-stu-id="b8d6a-159">-MaxSessionsPerRemoteNode</span></span>

<span data-ttu-id="b8d6a-160">Spécifie le nombre maximal de sessions qui peuvent être connectées à chaque nœud distant (ordinateur cible).</span><span class="sxs-lookup"><span data-stu-id="b8d6a-160">Specifies the maximum number of sessions that can be connected to each remote node (target computer).</span></span> <span data-ttu-id="b8d6a-161">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-161">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-162">-MaxSessionsPerWorkflow</span><span class="sxs-lookup"><span data-stu-id="b8d6a-162">-MaxSessionsPerWorkflow</span></span>

<span data-ttu-id="b8d6a-163">Spécifie le nombre maximal de sessions qui peuvent être créées pour prendre en charge chaque workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-163">Specifies the maximum number of session that can be created to support each workflow.</span></span> <span data-ttu-id="b8d6a-164">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-164">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-165">-OutOfProcessActivity</span><span class="sxs-lookup"><span data-stu-id="b8d6a-165">-OutOfProcessActivity</span></span>

<span data-ttu-id="b8d6a-166">Détermine les activités autorisées (spécifiées par le paramètre **AllowedActivities** ) qui sont exécutées hors processus.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-166">Determines which allowed activities (specified by the **AllowedActivities** parameter) run out-of-process.</span></span> <span data-ttu-id="b8d6a-167">La valeur par défaut est **InlineScript** .</span><span class="sxs-lookup"><span data-stu-id="b8d6a-167">The default value is **InlineScript** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-168">-PersistencePath</span><span class="sxs-lookup"><span data-stu-id="b8d6a-168">-PersistencePath</span></span>

<span data-ttu-id="b8d6a-169">Spécifie l'emplacement sur le disque où sont stockés l'état et les données de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-169">Specifies the location on disk where workflow state and data are stored.</span></span> <span data-ttu-id="b8d6a-170">Le stockage de l'état et des données de workflow permet la suspension et la reprise des workflows, et une récupération suite à des interruptions et des défaillances du réseau.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-170">Storing the workflow state and data allows workflows to be suspended and resumed, and to recover from interruptions and network failures.</span></span>

<span data-ttu-id="b8d6a-171">La valeur par défaut est `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-171">The default value is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-172">-PersistWithEncryption</span><span class="sxs-lookup"><span data-stu-id="b8d6a-172">-PersistWithEncryption</span></span>

<span data-ttu-id="b8d6a-173">Indique que le flux de travail chiffre les données dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-173">Indicates that the workflow encrypts the data in the persistence store.</span></span> <span data-ttu-id="b8d6a-174">Envisagez d'utiliser cette fonctionnalité lors du stockage de données de persistance dans un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-174">Consider using this feature when storing persistence data in a network share.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-175">-RemoteNodeSessionIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b8d6a-175">-RemoteNodeSessionIdleTimeoutSec</span></span>

<span data-ttu-id="b8d6a-176">Spécifie la durée pendant laquelle une session qui est connectée à un nœud distant (ordinateur cible) est maintenue si elle est inactive.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-176">Specifies how long a session that is connected to a remote node (target computer) is maintained if it is idle.</span></span>

<span data-ttu-id="b8d6a-177">Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-177">Enter a value in seconds.</span></span> <span data-ttu-id="b8d6a-178">La valeur par défaut est 60.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-178">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-179">-SessionThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b8d6a-179">-SessionThrottleLimit</span></span>

<span data-ttu-id="b8d6a-180">Spécifie le nombre d'opérations créées pour prendre en charge tous les workflows démarrés dans la session.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-180">Specifies how many operations are created to support all workflows started in the session.</span></span> <span data-ttu-id="b8d6a-181">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-181">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-182">-WorkflowShutdownTimeoutMSec</span><span class="sxs-lookup"><span data-stu-id="b8d6a-182">-WorkflowShutdownTimeoutMSec</span></span>

<span data-ttu-id="b8d6a-183">Spécifie la durée pendant laquelle la session est maintenue une fois que tous les workflows dans la session sont suspendus de force.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-183">Specifies how long the session is maintained after all workflows in the session are forcibly suspended.</span></span> <span data-ttu-id="b8d6a-184">Quand le délai arrive à expiration, Windows PowerShell ferme la session, même si tous les workflows ne sont pas encore suspendus.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-184">When the timeout expires, Windows PowerShell closes the session, even if all workflows are not yet suspended.</span></span>

<span data-ttu-id="b8d6a-185">Entrez une valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-185">Enter a value in milliseconds.</span></span>
<span data-ttu-id="b8d6a-186">La valeur par défaut est 500.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-186">The default value is 500.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d6a-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8d6a-187">CommonParameters</span></span>

<span data-ttu-id="b8d6a-188">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8d6a-189">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b8d6a-189">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b8d6a-190">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b8d6a-190">INPUTS</span></span>

### <span data-ttu-id="b8d6a-191">Aucun</span><span class="sxs-lookup"><span data-stu-id="b8d6a-191">None</span></span>

<span data-ttu-id="b8d6a-192">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b8d6a-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b8d6a-193">OUTPUTS</span></span>

### <span data-ttu-id="b8d6a-194">Microsoft. PowerShell. Commands. PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="b8d6a-194">Microsoft.PowerShell.Commands.PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="b8d6a-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b8d6a-195">NOTES</span></span>

<span data-ttu-id="b8d6a-196">Quand la valeur maximale définie par une option est dépassée, la commande pour créer une autre instance dans la session échoue, sauf indication dans la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-196">When the maximum value set by an option is exceeded, the command to create another instance in the session fails, unless noted in the parameter description.</span></span> <span data-ttu-id="b8d6a-197">Par exemple, si la valeur de **MaxConnectedSessions** est 100,</span><span class="sxs-lookup"><span data-stu-id="b8d6a-197">For example, if the value of **MaxConnectedSessions** is 100.</span></span> <span data-ttu-id="b8d6a-198">la commande pour créer la 101è session sur un nœud distant (ordinateur cible) échoue.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-198">The command to create the 101st session to a remote node (target computer) fails.</span></span>

<span data-ttu-id="b8d6a-199">Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-199">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="b8d6a-200">En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-200">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="b8d6a-201">En particulier, les propriétés des configurations de sessions qui comprennent un objet **PSWorkflowExecutionOptions** varient en fonction des valeurs d'option de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-201">In particular, the properties of session configurations that include a **PSWorkflowExecutionOptions** object vary based on the workflow option values.</span></span> <span data-ttu-id="b8d6a-202">Par exemple, si la configuration de session inclut un objet **PSWorkflowExecutionOptions** qui définit une valeur autre que par défaut pour la propriété **SessionThrottleLimit** , la configuration de session a une propriété **SessionThrottleLimit** .</span><span class="sxs-lookup"><span data-stu-id="b8d6a-202">For example, if the session configuration includes a **PSWorkflowExecutionOptions** object that sets a non-default value for the **SessionThrottleLimit** property, the session configuration has a **SessionThrottleLimit** property.</span></span> <span data-ttu-id="b8d6a-203">Sinon, elle ne l'a pas.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-203">Otherwise, it does not.</span></span>

## <span data-ttu-id="b8d6a-204">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b8d6a-204">RELATED LINKS</span></span>

[<span data-ttu-id="b8d6a-205">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="b8d6a-205">New-PSWorkflowSession</span></span>](New-PSWorkflowSession.md)

[<span data-ttu-id="b8d6a-206">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="b8d6a-206">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="b8d6a-207">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8d6a-207">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)

---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387904"
---
# <span data-ttu-id="88c22-103">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-103">Set-ScheduledJob</span></span>

## <span data-ttu-id="88c22-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="88c22-104">SYNOPSIS</span></span>
<span data-ttu-id="88c22-105">Modifie les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="88c22-105">Changes scheduled jobs.</span></span>

## <span data-ttu-id="88c22-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="88c22-106">SYNTAX</span></span>

### <span data-ttu-id="88c22-107">ScriptBlock (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="88c22-107">ScriptBlock (Default)</span></span>

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="88c22-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="88c22-108">FilePath</span></span>

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="88c22-109">Exécution</span><span class="sxs-lookup"><span data-stu-id="88c22-109">Execution</span></span>

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## <span data-ttu-id="88c22-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="88c22-110">DESCRIPTION</span></span>
<span data-ttu-id="88c22-111">L'applet de commande **Set-ScheduledJob** modifie les propriétés des tâches planifiées, telles que les commandes exécutées par les tâches ou les informations d'identification requises pour exécuter la tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-111">The **Set-ScheduledJob** cmdlet changes the properties of scheduled jobs, such as the commands that the jobs run or the credentials required to run the job.</span></span>
<span data-ttu-id="88c22-112">Vous pouvez également l'utiliser pour effacer l'historique d'exécution de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-112">You can also use it to clear the execution history of the scheduled job.</span></span>

<span data-ttu-id="88c22-113">Pour utiliser cette applet de commande, commencez par utiliser l’applet de commande Get-ScheduledJob pour accéder à la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-113">To use this cmdlet, begin by using the Get-ScheduledJob cmdlet to get the scheduled job.</span></span>
<span data-ttu-id="88c22-114">Ensuite, dirigez la tâche planifiée vers **Set-ScheduledJob** ou enregistrez la tâche dans une variable et utilisez le paramètre *InputObject* pour identifier la tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-114">Then, pipe the scheduled job to **Set-ScheduledJob** or save the job in a variable and use the *InputObject* parameter to identify the job.</span></span>
<span data-ttu-id="88c22-115">Utilisez les paramètres restants de **Set-ScheduledJob** pour modifier les propriétés de la tâche ou effacer l'historique d'exécution.</span><span class="sxs-lookup"><span data-stu-id="88c22-115">Use the remaining parameters of **Set-ScheduledJob** to change the job properties or clear the execution history.</span></span>

<span data-ttu-id="88c22-116">Bien que vous puissiez utiliser **Set-ScheduledJob** pour modifier les déclencheurs et les options d’une tâche planifiée, les applets de commande Add-JobTrigger, Set-JobTrigger et Set-ScheduledJobOption fournissent des méthodes beaucoup plus faciles pour accomplir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="88c22-116">Although you can use **Set-ScheduledJob** to change the triggers and options of a scheduled job, the Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJobOption cmdlets provide much easier ways to accomplish those tasks.</span></span>
<span data-ttu-id="88c22-117">Pour créer une nouvelle tâche planifiée, utilisez l’applet de commande Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="88c22-117">To create a new scheduled job, use the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="88c22-118">Le paramètre *Trigger* de **Set-ScheduledJob** ajoute un ou plusieurs déclencheurs de tâche qui démarrent le travail.</span><span class="sxs-lookup"><span data-stu-id="88c22-118">The *Trigger* parameter of **Set-ScheduledJob** adds one or more job triggers that start the job.</span></span>
<span data-ttu-id="88c22-119">Le paramètre de *déclencheur* étant facultatif, vous pouvez ajouter des déclencheurs quand vous créez la tâche planifiée, ajouter des déclencheurs de tâche ultérieurement, ajouter le paramètre *RunNow* pour démarrer la tâche immédiatement, utiliser l’applet de commande Start-Job pour démarrer la tâche immédiatement à tout moment, ou enregistrer la tâche planifiée non déclenchée comme modèle pour d’autres travaux.</span><span class="sxs-lookup"><span data-stu-id="88c22-119">The *Trigger* parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the *RunNow* parameter to start the job immediately, use the Start-Job cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="88c22-120">**Set-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88c22-120">**Set-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="88c22-121">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="88c22-121">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="88c22-122">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="88c22-122">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="88c22-123">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="88c22-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="88c22-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="88c22-124">EXAMPLES</span></span>

### <span data-ttu-id="88c22-125">Exemple 1 : modifier le script exécuté par un travail</span><span class="sxs-lookup"><span data-stu-id="88c22-125">Example 1: Change the script that a job runs</span></span>

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

<span data-ttu-id="88c22-126">Cet exemple montre comment modifier le script qui est exécuté dans une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-126">This example shows how to change the script that is run in a scheduled job.</span></span>

<span data-ttu-id="88c22-127">La première commande utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée Inventory.</span><span class="sxs-lookup"><span data-stu-id="88c22-127">The first command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job.</span></span>
<span data-ttu-id="88c22-128">La sortie indique que la tâche exécute le script Get-Inventory.ps1.</span><span class="sxs-lookup"><span data-stu-id="88c22-128">The output shows that the job runs the Get-Inventory.ps1 script.</span></span>

<span data-ttu-id="88c22-129">Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du script.</span><span class="sxs-lookup"><span data-stu-id="88c22-129">This command is not required; it is included only to show the effect of the script change.</span></span>

### <span data-ttu-id="88c22-130">Exemple 2 : supprimer l’historique d’exécution d’une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="88c22-130">Example 2: Delete the execution history of a scheduled job</span></span>

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="88c22-131">Cette commande supprime l'historique d'exécution actuel et les résultats enregistrés pour la tâche planifiée BackupArchive.</span><span class="sxs-lookup"><span data-stu-id="88c22-131">This command deletes the current execution history and saved job results for the BackupArchive scheduled job.</span></span>

<span data-ttu-id="88c22-132">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée BackupArchive.</span><span class="sxs-lookup"><span data-stu-id="88c22-132">The command uses the Get-ScheduledJob cmdlet to get the BackupArchive scheduled job.</span></span>
<span data-ttu-id="88c22-133">Un opérateur pipeline (|) envoie la tâche à l'applet de commande **Set-ScheduledJob** pour la modifier.</span><span class="sxs-lookup"><span data-stu-id="88c22-133">A pipeline operator (|) sends the job to the **Set-ScheduledJob** cmdlet to change it.</span></span>
<span data-ttu-id="88c22-134">L’applet de commande **Set-ScheduledJob** utilise le paramètre *ClearExecutionHistory* pour supprimer l’historique d’exécution et les résultats enregistrés.</span><span class="sxs-lookup"><span data-stu-id="88c22-134">The **Set-ScheduledJob** cmdlet uses the *ClearExecutionHistory* parameter to delete the execution history and saved results.</span></span>

<span data-ttu-id="88c22-135">Pour plus d'informations sur l'historique d'exécution et les résultats enregistrés des tâches planifiées, consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="88c22-135">For more information about the execution history and saved job results of scheduled jobs, see about_Scheduled_Jobs.</span></span>

### <span data-ttu-id="88c22-136">Exemple 3 : modification des tâches planifiées sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="88c22-136">Example 3: Change scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

<span data-ttu-id="88c22-137">Cette commande modifie le script d'initialisation dans toutes les tâches planifiées sur les ordinateurs Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="88c22-137">This command changes the initialization script in all scheduled jobs on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="88c22-138">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur les ordinateurs SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="88c22-138">The command uses the Invoke-Command cmdlet to run a command on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="88c22-139">La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="88c22-139">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="88c22-140">Les tâches planifiées sont dirigées vers l’applet de commande **Set-ScheduledJob** , qui modifie le script d’initialisation en SetForRun.ps1.</span><span class="sxs-lookup"><span data-stu-id="88c22-140">The scheduled jobs are piped to the **Set-ScheduledJob** cmdlet, which changes the initialization script to SetForRun.ps1.</span></span>

## <span data-ttu-id="88c22-141">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="88c22-141">PARAMETERS</span></span>

### <span data-ttu-id="88c22-142">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="88c22-142">-ArgumentList</span></span>
<span data-ttu-id="88c22-143">Spécifie des valeurs pour les paramètres du script spécifié par le paramètre *FilePath* ou pour la commande spécifiée par le paramètre *ScriptBlock*.</span><span class="sxs-lookup"><span data-stu-id="88c22-143">Specifies values for the parameters of the script that is specified by the *FilePath* parameter or for the command that is specified by the *ScriptBlock* parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-144">-Authentification</span><span class="sxs-lookup"><span data-stu-id="88c22-144">-Authentication</span></span>
<span data-ttu-id="88c22-145">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="88c22-145">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="88c22-146">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="88c22-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="88c22-147">Default</span><span class="sxs-lookup"><span data-stu-id="88c22-147">Default</span></span>
- <span data-ttu-id="88c22-148">De base</span><span class="sxs-lookup"><span data-stu-id="88c22-148">Basic</span></span>
- <span data-ttu-id="88c22-149">CredSSP</span><span class="sxs-lookup"><span data-stu-id="88c22-149">Credssp</span></span>
- <span data-ttu-id="88c22-150">Digest</span><span class="sxs-lookup"><span data-stu-id="88c22-150">Digest</span></span>
- <span data-ttu-id="88c22-151">Kerberos</span><span class="sxs-lookup"><span data-stu-id="88c22-151">Kerberos</span></span>
- <span data-ttu-id="88c22-152">Negotiate</span><span class="sxs-lookup"><span data-stu-id="88c22-152">Negotiate</span></span>
- <span data-ttu-id="88c22-153">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="88c22-153">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="88c22-154">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="88c22-154">The default value is Default.</span></span> <span data-ttu-id="88c22-155">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) dans le kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88c22-155">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) in the PowerShell SDK.</span></span>

<span data-ttu-id="88c22-156">ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="88c22-156">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="88c22-157">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="88c22-157">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="88c22-158">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="88c22-158">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-159">-ClearExecutionHistory</span><span class="sxs-lookup"><span data-stu-id="88c22-159">-ClearExecutionHistory</span></span>
<span data-ttu-id="88c22-160">Supprime l'historique d'exécution actuel et les résultats enregistrés de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-160">Deletes the current execution history and the saved results of the scheduled job.</span></span>

<span data-ttu-id="88c22-161">L'historique d'exécution des tâches et les résultats de ces dernières sont enregistrés avec la tâche planifiée dans le répertoire $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs sur l'ordinateur sur lequel la tâche est créée.</span><span class="sxs-lookup"><span data-stu-id="88c22-161">The job execution history and job results are saved with the scheduled job in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the computer on which the job is created.</span></span>
<span data-ttu-id="88c22-162">Pour afficher l’historique d’exécution, utilisez l’applet de commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="88c22-162">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="88c22-163">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="88c22-163">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="88c22-164">Ce paramètre n'affecte pas les événements écrits par le Planificateur de tâches dans les journaux des événements Windows et n'empêche pas Windows PowerShell d'enregistrer les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-164">This parameter does not affect the events that Task Scheduler writes to the Windows event logs and it does not stop Windows PowerShell from saving job results.</span></span>
<span data-ttu-id="88c22-165">Pour gérer le nombre de résultats de la tâche qui sont enregistrés, utilisez le paramètre *MaxResultCount*.</span><span class="sxs-lookup"><span data-stu-id="88c22-165">To manage the number of job results that are saved, use the *MaxResultCount* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="88c22-166">-Credential</span></span>
<span data-ttu-id="88c22-167">Spécifie un compte d'utilisateur qui a l'autorisation d'exécuter la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-167">Specifies a user account that has permission to run the scheduled job.</span></span>
<span data-ttu-id="88c22-168">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="88c22-168">The default is the current user.</span></span>

<span data-ttu-id="88c22-169">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui de l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="88c22-169">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the Get-Credential cmdlet.</span></span>
<span data-ttu-id="88c22-170">Si vous entrez uniquement un nom d'utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="88c22-170">If you enter only a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-171">-FilePath</span><span class="sxs-lookup"><span data-stu-id="88c22-171">-FilePath</span></span>
<span data-ttu-id="88c22-172">Spécifie un script exécuté par la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-172">Specifies a script that the scheduled job runs.</span></span>
<span data-ttu-id="88c22-173">Entrez le chemin d'accès à un fichier .ps1 sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="88c22-173">Enter the path to a .ps1 file on the local computer.</span></span>
<span data-ttu-id="88c22-174">Pour spécifier les valeurs par défaut des paramètres de script, utilisez le paramètre *ArgumentList*.</span><span class="sxs-lookup"><span data-stu-id="88c22-174">To specify default values for the script parameters, use the *ArgumentList* parameter.</span></span>
<span data-ttu-id="88c22-175">Chaque tâche planifiée doit avoir une valeur *ScriptBlock* ou *FilePath*.</span><span class="sxs-lookup"><span data-stu-id="88c22-175">Every scheduled job must have either a *ScriptBlock* or *FilePath* value.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-176">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="88c22-176">-InitializationScript</span></span>
<span data-ttu-id="88c22-177">Spécifie le chemin d'accès complet à un script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="88c22-177">Specifies the fully qualified path to a Windows PowerShell script (.ps1).</span></span>
<span data-ttu-id="88c22-178">Le script d'initialisation s'exécute dans la session créée pour la tâche en arrière-plan avant les commandes spécifiées par le paramètre *ScriptBlock* ou le script spécifié par le paramètre *FilePath*.</span><span class="sxs-lookup"><span data-stu-id="88c22-178">The initialization script runs in the session that is created for the background job before the commands that are specified by the *ScriptBlock* parameter or the script that is specified by the *FilePath* parameter.</span></span>
<span data-ttu-id="88c22-179">Vous pouvez utiliser le script d'initialisation pour configurer la session, par exemple, pour ajouter des fichiers, des fonctions ou des alias, pour créer des répertoires ou pour vérifier des conditions préalables.</span><span class="sxs-lookup"><span data-stu-id="88c22-179">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="88c22-180">Pour spécifier un script qui exécute les commandes de tâche principales, utilisez le paramètre *FilePath*.</span><span class="sxs-lookup"><span data-stu-id="88c22-180">To specify a script that runs the primary job commands, use the *FilePath* parameter.</span></span>

<span data-ttu-id="88c22-181">Si le script d’initialisation génère une erreur, y compris une erreur sans fin d’exécution, l’instance actuelle de la tâche planifiée ne s’exécute pas et son état est failed.</span><span class="sxs-lookup"><span data-stu-id="88c22-181">If the initialization script generates an error, including a non-terminating error, the current instance of the scheduled job does not run and its status is Failed.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-182">-InputObject</span><span class="sxs-lookup"><span data-stu-id="88c22-182">-InputObject</span></span>
<span data-ttu-id="88c22-183">Spécifie la tâche planifiée à modifier.</span><span class="sxs-lookup"><span data-stu-id="88c22-183">Specifies the scheduled job to be changed.</span></span>
<span data-ttu-id="88c22-184">Entrez une variable qui contient des objets **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="88c22-184">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="88c22-185">Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="88c22-185">You can also pipe a **ScheduledJobDefinition** object to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="88c22-186">Si vous spécifiez plusieurs tâches planifiées, **Set-ScheduledJob** apporte les mêmes modifications à toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="88c22-186">If you specify multiple scheduled jobs, **Set-ScheduledJob** makes the same changes to all jobs.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-187">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="88c22-187">-MaxResultCount</span></span>
<span data-ttu-id="88c22-188">Spécifie le nombre d'entrées de résultat de tâche qui sont conservées pour la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-188">Specifies how many job result entries are maintained for the scheduled job.</span></span>
<span data-ttu-id="88c22-189">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="88c22-189">The default value is 32.</span></span>

<span data-ttu-id="88c22-190">Windows PowerShell enregistre l'historique d'exécution et les résultats de chaque instance déclenchée de la tâche planifiée sur le disque.</span><span class="sxs-lookup"><span data-stu-id="88c22-190">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span>
<span data-ttu-id="88c22-191">La valeur de ce paramètre détermine le nombre de résultats d'instance de tâche qui sont enregistrés pour cette tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-191">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span>
<span data-ttu-id="88c22-192">Quand le nombre de résultats d'instance de tâche dépasse cette valeur, Windows PowerShell supprime les résultats de l'instance de tâche la plus ancienne pour libérer de l'espace pour les résultats de la dernière instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-192">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="88c22-193">L’historique d’exécution du travail et les résultats du travail sont enregistrés dans les \\ \<JobName\> répertoires $Home \appdata\local\microsoft\windows\powershell\scheduledjobs \Output. \\ \<Timestamp\> de l’ordinateur sur lequel le travail est créé.</span><span class="sxs-lookup"><span data-stu-id="88c22-193">The job execution history and job results are saved in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\\\<JobName\>\Output\\\<Timestamp\> directories on the computer on which the job is created.</span></span>
<span data-ttu-id="88c22-194">Pour afficher l’historique d’exécution, utilisez l’applet de commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="88c22-194">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="88c22-195">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="88c22-195">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="88c22-196">Le paramètre *MaxResultCount* définit la valeur de la propriété ExecutionHistoryLength de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-196">The *MaxResultCount* parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="88c22-197">Pour supprimer l'historique d'exécution actuel et les résultats des tâches, utilisez le paramètre *ClearExecutionHistory*.</span><span class="sxs-lookup"><span data-stu-id="88c22-197">To delete the current execution history and job results, use the *ClearExecutionHistory* parameter.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-198">-Name</span><span class="sxs-lookup"><span data-stu-id="88c22-198">-Name</span></span>
<span data-ttu-id="88c22-199">Spécifie un nouveau nom pour la tâche planifiée et les instances de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-199">Specifies a new name for the scheduled job and instances of the scheduled job.</span></span>
<span data-ttu-id="88c22-200">Le nom doit être unique sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="88c22-200">The name must be unique on the local computer.</span></span>

<span data-ttu-id="88c22-201">Pour identifier la tâche planifiée à modifier, utilisez le paramètre *InputObject* ou dirigez une tâche planifiée à partir de Get-ScheduledJob vers **Set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="88c22-201">To identify the scheduled job to be changed, use the *InputObject* parameter or pipe a scheduled job from Get-ScheduledJob to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="88c22-202">Ce paramètre ne modifie pas les noms des instances de tâche sur le disque.</span><span class="sxs-lookup"><span data-stu-id="88c22-202">This parameter does not change the names of job instances on disk.</span></span>
<span data-ttu-id="88c22-203">Il affecte uniquement les instances de tâche qui sont démarrées à l'issue de cette commande.</span><span class="sxs-lookup"><span data-stu-id="88c22-203">It affects only job instances that are started after this command completes.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-204">-PassThru</span><span class="sxs-lookup"><span data-stu-id="88c22-204">-PassThru</span></span>
<span data-ttu-id="88c22-205">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="88c22-205">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="88c22-206">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="88c22-206">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-207">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="88c22-207">-RunAs32</span></span>
<span data-ttu-id="88c22-208">Exécute la tâche planifiée dans un processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="88c22-208">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-209">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="88c22-209">-RunEvery</span></span>

<span data-ttu-id="88c22-210">Utilisé pour spécifier la fréquence d’exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="88c22-210">Used to specify how often to run the job.</span></span> <span data-ttu-id="88c22-211">Par exemple, utilisez cette option pour exécuter un travail toutes les 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="88c22-211">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-212">-RunNow</span><span class="sxs-lookup"><span data-stu-id="88c22-212">-RunNow</span></span>
<span data-ttu-id="88c22-213">Démarre une tâche immédiatement, dès que l’applet de commande **Set-ScheduledJob** est exécutée.</span><span class="sxs-lookup"><span data-stu-id="88c22-213">Starts a job immediately, as soon as the **Set-ScheduledJob** cmdlet is run.</span></span>
<span data-ttu-id="88c22-214">Ce paramètre évite d'avoir à déclencher le Planificateur de tâches pour exécuter un script Windows PowerShell immédiatement après l'inscription et n'oblige pas les utilisateurs à créer un déclencheur qui spécifie une date et une heure de début.</span><span class="sxs-lookup"><span data-stu-id="88c22-214">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and does not require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-215">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="88c22-215">-ScheduledJobOption</span></span>
<span data-ttu-id="88c22-216">Définit les options de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-216">Sets options for the scheduled job.</span></span>
<span data-ttu-id="88c22-217">Entrez un objet **ScheduledJobOptions** , tel que celui que vous créez à l’aide de l’applet de commande New-ScheduledJobOption, ou une valeur de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="88c22-217">Enter a **ScheduledJobOptions** object, such as one that you create by using the New-ScheduledJobOption cmdlet, or a hash table value.</span></span>

<span data-ttu-id="88c22-218">Vous pouvez définir les options d’une tâche planifiée lorsque vous inscrivez la tâche planifiée ou utilisez les applets de commande Set-ScheduledJobOption ou **Set-ScheduledJob** pour définir ou modifier les options.</span><span class="sxs-lookup"><span data-stu-id="88c22-218">You can set options for a scheduled job when you register the scheduled job or use the Set-ScheduledJobOption or **Set-ScheduledJob** cmdlets to set or change options.</span></span>

<span data-ttu-id="88c22-219">La plupart des options et leurs valeurs par défaut déterminent si et quand une tâche planifiée s'exécute.</span><span class="sxs-lookup"><span data-stu-id="88c22-219">Many of the options and their default values determine whether and when a scheduled job runs.</span></span>
<span data-ttu-id="88c22-220">Veillez à consulter ces options avant de planifier une tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-220">Be sure to review these options before scheduling a job.</span></span>
<span data-ttu-id="88c22-221">Pour obtenir une description des options de tâche planifiée, y compris les valeurs par défaut, consultez New-ScheduledJobOption.</span><span class="sxs-lookup"><span data-stu-id="88c22-221">For a description of the scheduled job options, including the default values, see New-ScheduledJobOption.</span></span>

<span data-ttu-id="88c22-222">Pour envoyer une table de hachage, utilisez les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="88c22-222">To submit a hash table, use the following keys.</span></span>
<span data-ttu-id="88c22-223">Dans la table de hachage suivante, les clés sont affichées avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="88c22-223">In the following hash table, the keys are shown with their default values.</span></span>

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-224">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="88c22-224">-ScriptBlock</span></span>
<span data-ttu-id="88c22-225">Spécifie les commandes exécutées par la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-225">Specifies the commands that the scheduled job runs.</span></span>
<span data-ttu-id="88c22-226">Placez les commandes entre accolades ( { } ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="88c22-226">Enclose the commands in braces ( { } ) to create a script block.</span></span>
<span data-ttu-id="88c22-227">Pour spécifier les valeurs par défaut des paramètres de commande, utilisez le paramètre *ArgumentList*.</span><span class="sxs-lookup"><span data-stu-id="88c22-227">To specify default values for command parameters, use the *ArgumentList* parameter.</span></span>

<span data-ttu-id="88c22-228">Chaque commande Register-ScheduledJob doit utiliser les paramètres *ScriptBlock* ou *FilePath*.</span><span class="sxs-lookup"><span data-stu-id="88c22-228">Every Register-ScheduledJob command must use either the *ScriptBlock* or *FilePath* parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-229">-Déclencheur</span><span class="sxs-lookup"><span data-stu-id="88c22-229">-Trigger</span></span>
<span data-ttu-id="88c22-230">Spécifie les déclencheurs de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-230">Specifies the triggers for the scheduled job.</span></span>
<span data-ttu-id="88c22-231">Entrez un ou plusieurs objets **ScheduledJobTrigger** , tels que les objets retournées par l’applet de commande New-JobTrigger, ou une table de hachage des clés et des valeurs de déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-231">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the New-JobTrigger cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="88c22-232">Un déclencheur de tâche démarre automatiquement une tâche planifiée sur une planification ponctuelle ou périodique, ou quand un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="88c22-232">A job trigger starts a scheduled job automatically on a one-time or recurring scheduled or when an event occurs.</span></span>

<span data-ttu-id="88c22-233">Les déclencheurs de tâche sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="88c22-233">Job triggers are optional.</span></span>
<span data-ttu-id="88c22-234">Vous pouvez ajouter un déclencheur quand vous créez la tâche planifiée, utiliser les applets de commande Add-JobTrigger ou **Set-ScheduledJob** pour ajouter des déclencheurs ultérieurement, ou utiliser l’applet de commande Start-Job pour démarrer immédiatement la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-234">You can add a trigger when you create the scheduled job, use the Add-JobTrigger or **Set-ScheduledJob** cmdlets to add triggers later, or use the Start-Job cmdlet to start the scheduled job immediately.</span></span>
<span data-ttu-id="88c22-235">Vous pouvez également créer et gérer une tâche planifiée qui n'a aucun déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="88c22-235">You can also create and maintain a scheduled job that has no job triggers.</span></span>

<span data-ttu-id="88c22-236">Pour envoyer une table de hachage, utilisez les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="88c22-236">To submit a hash table, use the following keys.</span></span>

<span data-ttu-id="88c22-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (ou toute chaîne d’heure valide); `DaysOfWeek="Monday", "Wednesday"` (ou toute combinaison de noms de jours); `Interval=2` (ou n’importe quel intervalle de fréquence valide); `RandomDelay="30minutes"` (ou toute chaîne TimeSpan valide); `User="Domain1\User01"` (ou tout utilisateur valide ; utilisé uniquement avec la valeur de fréquence AtLogon)</span><span class="sxs-lookup"><span data-stu-id="88c22-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01"` (or any valid user; used only with the AtLogon frequency value)</span></span>

<span data-ttu-id="88c22-238">}</span><span class="sxs-lookup"><span data-stu-id="88c22-238">}</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88c22-239">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88c22-239">CommonParameters</span></span>
<span data-ttu-id="88c22-240">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88c22-240">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88c22-241">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="88c22-241">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88c22-242">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="88c22-242">INPUTS</span></span>

### <span data-ttu-id="88c22-243">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="88c22-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="88c22-244">Vous pouvez diriger les tâches planifiées vers **Set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="88c22-244">You can pipe scheduled jobs to **Set-ScheduledJob**.</span></span>

## <span data-ttu-id="88c22-245">SORTIES</span><span class="sxs-lookup"><span data-stu-id="88c22-245">OUTPUTS</span></span>

### <span data-ttu-id="88c22-246">Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="88c22-246">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="88c22-247">Si vous utilisez le paramètre *Passthru* , **Set-ScheduledJob** retourne la tâche planifiée modifiée.</span><span class="sxs-lookup"><span data-stu-id="88c22-247">If you use the *Passthru* parameter, **Set-ScheduledJob** returns the scheduled job that was changed.</span></span>
<span data-ttu-id="88c22-248">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="88c22-248">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="88c22-249">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="88c22-249">NOTES</span></span>

## <span data-ttu-id="88c22-250">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="88c22-250">RELATED LINKS</span></span>

[<span data-ttu-id="88c22-251">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-251">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="88c22-252">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-252">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="88c22-253">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-253">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="88c22-254">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-254">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="88c22-255">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-255">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="88c22-256">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-256">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="88c22-257">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-257">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="88c22-258">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="88c22-258">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="88c22-259">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-259">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="88c22-260">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="88c22-260">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="88c22-261">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-261">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="88c22-262">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-262">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="88c22-263">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="88c22-263">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="88c22-264">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-264">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="88c22-265">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="88c22-265">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="88c22-266">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="88c22-266">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)

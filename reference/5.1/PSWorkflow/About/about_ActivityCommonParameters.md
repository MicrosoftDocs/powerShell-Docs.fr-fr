---
description: Décrit les paramètres que Windows PowerShell workflow ajoute aux activités.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207245"
---
# <a name="about-activitycommonparameters"></a><span data-ttu-id="63426-104">À propos de ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="63426-104">About ActivityCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="63426-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="63426-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="63426-106">Décrit les paramètres que Windows PowerShell workflow ajoute aux activités.</span><span class="sxs-lookup"><span data-stu-id="63426-106">Describes the parameters that Windows PowerShell Workflow adds to activities.</span></span>

## <a name="long-description"></a><span data-ttu-id="63426-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="63426-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="63426-108">Le workflow Windows PowerShell ajoute les paramètres communs d’activité aux activités dérivées de la classe de base PSActivity.</span><span class="sxs-lookup"><span data-stu-id="63426-108">Windows PowerShell Workflow adds the activity common parameters to activities that are derived from the PSActivity base class.</span></span> <span data-ttu-id="63426-109">Cette catégorie comprend l’activité InlineScript et les applets de commande Windows PowerShell qui sont implémentées en tant qu’activités, telles que Get-Process et WinEvent.</span><span class="sxs-lookup"><span data-stu-id="63426-109">This category includes the InlineScript activity and Windows PowerShell cmdlets that are implemented as activities, such as Get-Process and Get-WinEvent.</span></span>

<span data-ttu-id="63426-110">Les paramètres communs d’activité ne sont pas valides sur les activités Suspend-Workflow et Checkpoint-Workflow et ne sont pas ajoutés aux applets de commande ou aux expressions que Windows PowerShell Workflow exécute automatiquement dans un bloc de script InlineScript ou une activité similaire.</span><span class="sxs-lookup"><span data-stu-id="63426-110">The activity common parameters are not valid on the Suspend-Workflow and Checkpoint-Workflow activities and they are not added to cmdlets or expressions that Windows PowerShell Workflow automatically runs in an InlineScript script block or similar activity.</span></span> <span data-ttu-id="63426-111">Les paramètres communs d'activités sont disponibles sur l'activité InlineScript, mais pas sur les commandes figurant dans le bloc de script InlineScript.</span><span class="sxs-lookup"><span data-stu-id="63426-111">The activity common parameters are available on the InlineScript activity, but not on commands in the InlineScript script block.</span></span>

<span data-ttu-id="63426-112">Plusieurs des paramètres communs d’activité sont également des paramètres communs de flux de travail ou des paramètres communs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-112">Several of the activity common parameters are also workflow common parameters or Windows PowerShell common parameters.</span></span> <span data-ttu-id="63426-113">Les autres paramètres communs d’activité sont spécifiques aux activités.</span><span class="sxs-lookup"><span data-stu-id="63426-113">Other activity common parameters are unique to activities.</span></span>

<span data-ttu-id="63426-114">Pour plus d’informations sur les paramètres communs de workflow, consultez about_WorkflowCommonParameters.</span><span class="sxs-lookup"><span data-stu-id="63426-114">For information about the workflow common parameters, see about_WorkflowCommonParameters.</span></span> <span data-ttu-id="63426-115">Pour plus d’informations sur les paramètres communs de Windows PowerShell, consultez about_CommonParameters.</span><span class="sxs-lookup"><span data-stu-id="63426-115">For information about the Windows PowerShell common parameters, see about_CommonParameters.</span></span>

### <a name="list-of-activity-common-parameters"></a><span data-ttu-id="63426-116">LISTE DES PARAMÈTRES COMMUNS D’ACTIVITÉ</span><span class="sxs-lookup"><span data-stu-id="63426-116">LIST OF ACTIVITY COMMON PARAMETERS</span></span>

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a><span data-ttu-id="63426-117">DESCRIPTIONS DES PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="63426-117">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="63426-118">Cette section décrit les paramètres communs d’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-118">This section describes the activity common parameters.</span></span>

#### <a name="appendoutput-boolean"></a><span data-ttu-id="63426-119">AppendOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-119">AppendOutput \<Boolean\></span></span>

<span data-ttu-id="63426-120">La valeur `$True` ajoute la sortie de l’activité à la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="63426-120">A value of `$True` adds the output of the activity to the value of the variable.</span></span>
<span data-ttu-id="63426-121">La valeur n' `$False` a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="63426-121">A value of `$False` has no effect.</span></span> <span data-ttu-id="63426-122">Par défaut, l’attribution d’une valeur à une variable remplace la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="63426-122">By default, assigning a value to a variable replaces the variable value.</span></span>

<span data-ttu-id="63426-123">Par exemple, les commandes suivantes ajoutent un objet processus à l’objet de service dans la `$x` variable.</span><span class="sxs-lookup"><span data-stu-id="63426-123">For example, the following commands add a process object to the service object in the `$x` variable.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

<span data-ttu-id="63426-124">Ce paramètre est conçu pour les workflows basés sur XAML.</span><span class="sxs-lookup"><span data-stu-id="63426-124">This parameter is designed for XAML-based workflows.</span></span> <span data-ttu-id="63426-125">Dans les workflows de script, vous pouvez également utiliser l’opérateur d’assignation + = pour ajouter une sortie à la valeur d’une variable, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="63426-125">In script workflows, you can also use the += assignment operator to add output to the value of a variable, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a><span data-ttu-id="63426-126">Debug \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="63426-126">Debug \<SwitchParameter\></span></span>

<span data-ttu-id="63426-127">Affiche des détails au niveau du programmeur sur l’opération effectuée par la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-127">Displays programmer-level detail about the operation performed by the command.</span></span>
<span data-ttu-id="63426-128">Le paramètre de débogage remplace la valeur de la variable $DebugPreference pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="63426-128">The Debug parameter overrides the value of the $DebugPreference variable for the current command.</span></span> <span data-ttu-id="63426-129">Ce paramètre fonctionne uniquement lorsque la commande génère des messages de débogage.</span><span class="sxs-lookup"><span data-stu-id="63426-129">This parameter works only when the command generates debugging messages.</span></span> <span data-ttu-id="63426-130">Ce paramètre est également un paramètre commun Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-130">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="displayname-string"></a><span data-ttu-id="63426-131">NomComplet \<String\></span><span class="sxs-lookup"><span data-stu-id="63426-131">DisplayName \<String\></span></span>

<span data-ttu-id="63426-132">Spécifie le nom convivial de l’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-132">Specifies a friendly name for the activity.</span></span> <span data-ttu-id="63426-133">La valeur DisplayName apparaît dans la barre de progression pendant l’exécution du workflow et dans la valeur de la propriété Progress de la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-133">The DisplayName value appears in the progress bar while the workflow runs and in the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="63426-134">Lorsque le paramètre PSProgressMessage est également inclus dans la commande, le contenu de la barre de progression s’affiche dans \<DisplayName\> : \<PSProgressMessage\> format.</span><span class="sxs-lookup"><span data-stu-id="63426-134">When the PSProgressMessage parameter is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

#### <a name="erroraction-actionpreference"></a><span data-ttu-id="63426-135">ErrorAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="63426-135">ErrorAction \<ActionPreference\></span></span>

<span data-ttu-id="63426-136">Détermine la façon dont l’activité répond à une erreur sans fin d’achèvement à partir de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-136">Determines how the activity responds to a non-terminating error from the command.</span></span> <span data-ttu-id="63426-137">Elle n’a aucun effet sur les erreurs d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="63426-137">It has no effect on termination errors.</span></span> <span data-ttu-id="63426-138">Ce paramètre fonctionne uniquement lorsque la commande génère une erreur sans fin d’achèvement, telle que celles de l’applet de commande Write-Error.</span><span class="sxs-lookup"><span data-stu-id="63426-138">This parameter works only when the command generates a non-terminating error, such as those from the Write-Error cmdlet.</span></span> <span data-ttu-id="63426-139">Le paramètre ErrorAction remplace la valeur de la variable $ErrorActionPreference pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="63426-139">The ErrorAction parameter overrides the value of the $ErrorActionPreference variable for the current command.</span></span> <span data-ttu-id="63426-140">Ce paramètre est également un paramètre commun Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-140">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="63426-141">Valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="63426-141">Valid values:</span></span>

- <span data-ttu-id="63426-142">Pouvoir.</span><span class="sxs-lookup"><span data-stu-id="63426-142">Continue.</span></span> <span data-ttu-id="63426-143">Affiche le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-143">Displays the error message and continues executing the command.</span></span> <span data-ttu-id="63426-144">« Continue » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63426-144">"Continue" is the default value.</span></span>

- <span data-ttu-id="63426-145">à ignorer.</span><span class="sxs-lookup"><span data-stu-id="63426-145">Ignore.</span></span> <span data-ttu-id="63426-146">Supprime le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-146">Suppresses the error message and continues executing the command.</span></span>
  <span data-ttu-id="63426-147">Contrairement à SilentlyContinue, ignore n’ajoute pas le message d’erreur à la variable automatique $Error.</span><span class="sxs-lookup"><span data-stu-id="63426-147">Unlike SilentlyContinue, Ignore does not add the error message to the $Error automatic variable.</span></span> <span data-ttu-id="63426-148">La valeur ignorer est introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="63426-148">The Ignore value is introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="63426-149">Inquire.</span><span class="sxs-lookup"><span data-stu-id="63426-149">Inquire.</span></span> <span data-ttu-id="63426-150">Affiche le message d’erreur et vous invite à confirmer avant de poursuivre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="63426-150">Displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="63426-151">Cette valeur est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="63426-151">This value is rarely used.</span></span>

- <span data-ttu-id="63426-152">Interrompre :</span><span class="sxs-lookup"><span data-stu-id="63426-152">Suspend.</span></span> <span data-ttu-id="63426-153">Suspend automatiquement une tâche de workflow pour permettre une investigation plus poussée.</span><span class="sxs-lookup"><span data-stu-id="63426-153">Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="63426-154">Après l’examen, le flux de travail peut être repris.</span><span class="sxs-lookup"><span data-stu-id="63426-154">After investigation, the workflow can be resumed.</span></span>

- <span data-ttu-id="63426-155">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="63426-155">SilentlyContinue.</span></span> <span data-ttu-id="63426-156">Supprime le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-156">Suppresses the error message and continues executing the command.</span></span>

- <span data-ttu-id="63426-157">Arrêter.</span><span class="sxs-lookup"><span data-stu-id="63426-157">Stop.</span></span> <span data-ttu-id="63426-158">Affiche le message d’erreur et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-158">Displays the error message and stops executing the command.</span></span>

#### <a name="input-object"></a><span data-ttu-id="63426-159">Entrée \<Object[]\></span><span class="sxs-lookup"><span data-stu-id="63426-159">Input \<Object[]\></span></span>

<span data-ttu-id="63426-160">Soumet une collection d’objets à une activité.</span><span class="sxs-lookup"><span data-stu-id="63426-160">Submits a collection of objects to an activity.</span></span> <span data-ttu-id="63426-161">Il s’agit d’une alternative à la canalisation des objets vers l’activité un à un.</span><span class="sxs-lookup"><span data-stu-id="63426-161">This is an alternative to piping objects to the activity one at a time.</span></span>

#### <a name="mergeerrortooutput-boolean"></a><span data-ttu-id="63426-162">MergeErrorToOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-162">MergeErrorToOutput \<Boolean\></span></span>

<span data-ttu-id="63426-163">`$True`La valeur ajoute des erreurs au flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="63426-163">A value of `$True` adds errors to the output stream.</span></span> <span data-ttu-id="63426-164">La valeur n' `$False` a pas d’effet.</span><span class="sxs-lookup"><span data-stu-id="63426-164">A value of `$False` has not effect.</span></span> <span data-ttu-id="63426-165">Utilisez ce paramètre avec les `ForEach -Parallel` Mots clés Parallel et pour collecter les erreurs et la sortie de plusieurs commandes parallèles dans une collection unique.</span><span class="sxs-lookup"><span data-stu-id="63426-165">Use this parameter with the Parallel and `ForEach -Parallel` keywords to collect errors and output from multiple parallel commands in a single collection.</span></span>

#### <a name="psactionretrycount-int32"></a><span data-ttu-id="63426-166">PSActionRetryCount \<Int32\></span><span class="sxs-lookup"><span data-stu-id="63426-166">PSActionRetryCount \<Int32\></span></span>

<span data-ttu-id="63426-167">Essaie à plusieurs reprises d’exécuter l’activité en cas d’échec de la première tentative.</span><span class="sxs-lookup"><span data-stu-id="63426-167">Tries repeatedly to run the activity if the first attempt fails.</span></span> <span data-ttu-id="63426-168">La valeur par défaut 0 n’effectue pas de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="63426-168">The default value, 0, does not retry.</span></span>

#### <a name="psactionretryintervalsec-int32"></a><span data-ttu-id="63426-169">PSActionRetryIntervalSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="63426-169">PSActionRetryIntervalSec \<Int32\></span></span>

<span data-ttu-id="63426-170">Détermine l’intervalle entre les actions de nouvelle tentative (en secondes).</span><span class="sxs-lookup"><span data-stu-id="63426-170">Determines the interval between action retries in seconds.</span></span> <span data-ttu-id="63426-171">La valeur par défaut 0 retente l’action immédiatement.</span><span class="sxs-lookup"><span data-stu-id="63426-171">The default value, 0, retries the action immediately.</span></span> <span data-ttu-id="63426-172">Ce paramètre n’est valide que si le paramètre PSActionRetryCount est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-172">This parameter is valid only when the PSActionRetryCount parameter is also used in the command.</span></span>

#### <a name="psactionrunningtimeoutsec-int32"></a><span data-ttu-id="63426-173">PSActionRunningTimeoutSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="63426-173">PSActionRunningTimeoutSec \<Int32\></span></span>

<span data-ttu-id="63426-174">Détermine la durée pendant laquelle l’activité peut s’exécuter sur chaque ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-174">Determines how long the activity can run on each target computer.</span></span> <span data-ttu-id="63426-175">Si l’activité ne se termine pas avant l’expiration du délai d’attente, le workflow Windows PowerShell génère une erreur de fin et arrête le traitement du workflow sur l’ordinateur cible concerné.</span><span class="sxs-lookup"><span data-stu-id="63426-175">If the activity does not complete before the timeout expires, Windows PowerShell Workflow generates a terminating error and stops processing the workflow on the affected target computer.</span></span>

#### <a name="psallowredirection-boolean"></a><span data-ttu-id="63426-176">PSAllowRedirection \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-176">PSAllowRedirection \<Boolean\></span></span>

<span data-ttu-id="63426-177">La valeur $True permet la redirection de la connexion aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-177">A value of $True allows redirection of the connection to the target computers.</span></span>
<span data-ttu-id="63426-178">La valeur $False n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="63426-178">A value of $False has no effect.</span></span> <span data-ttu-id="63426-179">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-179">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-180">Quand vous utilisez le paramètre PSConnectionURI, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="63426-180">When you use the PSConnectionURI parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="63426-181">Par défaut, Windows PowerShell ne redirige pas les connexions, mais vous pouvez utiliser le paramètre PSAllowRedirection avec la valeur $True pour autoriser la redirection de la connexion à l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-181">By default, Windows PowerShell does not redirect connections, but you can use the PSAllowRedirection parameter with a value of $True to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="63426-182">Vous pouvez également limiter le nombre de redirections de la connexion en définissant la propriété MaximumConnectionRedirectionCount de la `$PSSessionOption` variable de préférence ou la propriété MaximumConnectionRedirectionCount de la valeur du paramètre SSessionOption des applets de commande qui créent une session.</span><span class="sxs-lookup"><span data-stu-id="63426-182">You can also limit the number of times that the connection is redirected by setting the MaximumConnectionRedirectionCount property of the `$PSSessionOption` preference variable, or the MaximumConnectionRedirectionCount property of the value of the SSessionOption parameter of cmdlets that create a session.</span></span> <span data-ttu-id="63426-183">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="63426-183">The default value is 5.</span></span>

#### <a name="psapplicationname-string"></a><span data-ttu-id="63426-184">PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="63426-184">PSApplicationName \<String\></span></span>

<span data-ttu-id="63426-185">Spécifie le segment de nom d’application de l’URI de connexion utilisé pour se connecter aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-185">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="63426-186">Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre ConnectionURI dans la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-186">Use this parameter to specify the application name when you are not using the ConnectionURI parameter in the command.</span></span> <span data-ttu-id="63426-187">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-187">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-188">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-188">The default value is the value of the `$PSSessionApplicationName` preference variable on the target computer.</span></span> <span data-ttu-id="63426-189">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="63426-189">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="63426-190">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="63426-190">This value is appropriate for most uses.</span></span> <span data-ttu-id="63426-191">Pour plus d’informations, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="63426-191">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="63426-192">Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="63426-192">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="63426-193">La valeur de ce paramètre doit correspondre à la valeur de la propriété URLPrefix d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="63426-193">The value of this parameter should match the value of the URLPrefix property of a listener on the remote computer.</span></span>

#### <a name="psauthentication-authenticationmechanism"></a><span data-ttu-id="63426-194">PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="63426-194">PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="63426-195">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lors de la connexion aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-195">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span> <span data-ttu-id="63426-196">Les valeurs valides sont Default, Basic, Credssp, Digest, Kerberos, Negotiate et NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="63426-196">Valid values are Default, Basic, Credssp, Digest, Kerberos, Negotiate, and NegotiateWithImplicitCredential.</span></span> <span data-ttu-id="63426-197">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="63426-197">The default value is Default.</span></span> <span data-ttu-id="63426-198">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-198">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-199">Pour plus d'informations sur les valeurs de ce paramètre, consultez la description de l'énumération **System.Management.Automation.Runspaces.AuthenticationMechanism** sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="63426-199">For information about the values of this parameter, see the description of the **System.Management.Automation.Runspaces.AuthenticationMechanism** enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="63426-200">L'authentification CredSSP (Credential Security Service Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="63426-200">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="63426-201">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="63426-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="63426-202">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="63426-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="pscertificatethumbprint-string"></a><span data-ttu-id="63426-203">PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="63426-203">PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="63426-204">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="63426-204">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="63426-205">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="63426-205">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="63426-206">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-206">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-207">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="63426-207">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="63426-208">Ils peuvent uniquement être mappés aux comptes d'utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="63426-208">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="63426-209">Pour obtenir un certificat, utilisez les applets de commande [obtenir-Item](xref:Microsoft.PowerShell.Management.Get-Item) ou [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) dans le lecteur Cert : de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-209">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="pscomputername-string"></a><span data-ttu-id="63426-210">PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="63426-210">PSComputerName \<String[]\></span></span>

<span data-ttu-id="63426-211">Spécifie les ordinateurs cibles sur lesquels l’activité s’exécute.</span><span class="sxs-lookup"><span data-stu-id="63426-211">Specifies the target computers on which the activity run.</span></span> <span data-ttu-id="63426-212">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="63426-212">The default is the local computer.</span></span> <span data-ttu-id="63426-213">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-213">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-214">Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="63426-214">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="63426-215">Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, « localhost » ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="63426-215">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="63426-216">Pour inclure l’ordinateur local dans la valeur du paramètre PSComputerName, ouvrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="63426-216">To include the local computer in the value of the PSComputerName parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="63426-217">Si ce paramètre est omis de la commande, ou si la valeur est $null ou une chaîne vide, la cible de workflow est l’ordinateur local et la communication à distance Windows PowerShell n’est pas utilisée pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-217">If this parameter is omitted from the command, or it value is $null or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="63426-218">Pour utiliser une adresse IP dans la valeur du paramètre ComputerName, la commande doit inclure le paramètre PSCredential.</span><span class="sxs-lookup"><span data-stu-id="63426-218">To use an IP address in the value of the ComputerName parameter, the command must include the PSCredential parameter.</span></span> <span data-ttu-id="63426-219">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="63426-219">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="63426-220">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="63426-220">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="psconfigurationname-string"></a><span data-ttu-id="63426-221">PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="63426-221">PSConfigurationName \<String\></span></span>

<span data-ttu-id="63426-222">Spécifie les configurations de session utilisées pour créer des sessions sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-222">Specifies the session configurations that are used to create sessions on the target computers.</span></span> <span data-ttu-id="63426-223">Entrez le nom d’une configuration de session sur les ordinateurs cibles (et non sur l’ordinateur qui exécute le Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-223">Enter the name of a session configuration on the target computers (not on the computer that is running the workflow.</span></span> <span data-ttu-id="63426-224">La valeur par défaut est Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-224">The default is Microsoft.PowerShell.</span></span> <span data-ttu-id="63426-225">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-225">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretrycount-uint"></a><span data-ttu-id="63426-226">PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="63426-226">PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="63426-227">Spécifie le nombre maximal de tentatives de connexion à chaque ordinateur cible en cas d’échec de la première tentative de connexion.</span><span class="sxs-lookup"><span data-stu-id="63426-227">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="63426-228">Entrez un nombre compris entre 1 et 4 294 967 295 (UInt. MaxValue).</span><span class="sxs-lookup"><span data-stu-id="63426-228">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="63426-229">La valeur par défaut, zéro (0), ne représente aucune nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="63426-229">The default value, zero (0), represents no retry attempts.</span></span>
<span data-ttu-id="63426-230">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-230">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretryintervalsec-uint"></a><span data-ttu-id="63426-231">PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="63426-231">PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="63426-232">Spécifie le délai entre les nouvelles tentatives de connexion en secondes.</span><span class="sxs-lookup"><span data-stu-id="63426-232">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="63426-233">La valeur par défaut est zéro (0).</span><span class="sxs-lookup"><span data-stu-id="63426-233">The default value is zero (0).</span></span> <span data-ttu-id="63426-234">Ce paramètre est valide uniquement lorsque la valeur de PSConnectionRetryCount est au moins égale à 1.</span><span class="sxs-lookup"><span data-stu-id="63426-234">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span> <span data-ttu-id="63426-235">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-235">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionuri-systemuri"></a><span data-ttu-id="63426-236">PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="63426-236">PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="63426-237">Spécifie un Uniform Resource Identifier (URI) qui définit le point de terminaison de connexion pour l’activité sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-237">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the activity on the target computer.</span></span> <span data-ttu-id="63426-238">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="63426-238">The URI must be fully qualified.</span></span> <span data-ttu-id="63426-239">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-239">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-240">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="63426-240">The format of this string is as follows:</span></span>

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

<span data-ttu-id="63426-241">La valeur par défaut est `http://localhost:5985/WSMAN`.</span><span class="sxs-lookup"><span data-stu-id="63426-241">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="63426-242">Si vous ne spécifiez pas de PSConnectionURI, vous pouvez utiliser les paramètres PSUseSSL, PSComputerName, PSPort et PSApplicationName pour spécifier les valeurs PSConnectionURI.</span><span class="sxs-lookup"><span data-stu-id="63426-242">If you do not specify a PSConnectionURI, you can use the PSUseSSL, PSComputerName, PSPort, and PSApplicationName parameters to specify the PSConnectionURI values.</span></span>

<span data-ttu-id="63426-243">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63426-243">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="63426-244">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="63426-244">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="63426-245">Pour utiliser les ports par défaut pour la communication à distance Windows PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63426-245">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="pscredential-pscredential"></a><span data-ttu-id="63426-246">PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="63426-246">PSCredential \<PSCredential\></span></span>

<span data-ttu-id="63426-247">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter l’activité sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-247">Specifies a user account that has permission to run the activity on the target computer.</span></span> <span data-ttu-id="63426-248">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="63426-248">The default is the current user.</span></span> <span data-ttu-id="63426-249">Ce paramètre n’est valide que si le paramètre PSComputerName est inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-249">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span> <span data-ttu-id="63426-250">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-250">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-251">Tapez un nom d’utilisateur, tel que « User01 » ou « Domaine01\utilisateur01 », ou entrez une variable qui contient un objet PSCredential, tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="63426-251">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a PSCredential object, such as one that the Get-Credential cmdlet returns.</span></span> <span data-ttu-id="63426-252">Si vous entrez uniquement un nom d'utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="63426-252">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="psdebug-psdatacollectiondebugrecord"></a><span data-ttu-id="63426-253">PSDebug \<PSDataCollection[DebugRecord]\></span><span class="sxs-lookup"><span data-stu-id="63426-253">PSDebug \<PSDataCollection[DebugRecord]\></span></span>

<span data-ttu-id="63426-254">Ajoute des messages de débogage de l’activité à la collection d’enregistrements de débogage spécifiée, au lieu d’écrire les messages de débogage dans la console ou à la valeur de la propriété de débogage de la tâche de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-254">Adds debug messages from the activity to the specified debug record collection, instead of writing the debug messages to the console or to the value of the Debug property of the workflow job.</span></span> <span data-ttu-id="63426-255">Vous pouvez ajouter des messages de débogage de plusieurs activités au même objet de collection d’enregistrements de débogage.</span><span class="sxs-lookup"><span data-stu-id="63426-255">You can add debug messages from multiple activities to the same debug record collection object.</span></span>

<span data-ttu-id="63426-256">Pour utiliser ce paramètre commun d’activité, utilisez l’applet de commande New-Object pour créer un objet PSDataCollection avec un type DebugRecord et enregistrer l’objet dans une variable.</span><span class="sxs-lookup"><span data-stu-id="63426-256">To use this activity common parameter, use the New-Object cmdlet to create a PSDataCollection object with a type of DebugRecord and save the object in a variable.</span></span> <span data-ttu-id="63426-257">Ensuite, utilisez la variable comme valeur du paramètre PSDebug d’une ou plusieurs activités, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="63426-257">Then, use the variable as the value of the PSDebug parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a><span data-ttu-id="63426-258">PSDisableSerialization \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-258">PSDisableSerialization \<Boolean\></span></span>

<span data-ttu-id="63426-259">Indique à l’activité de retourner les objets « dynamiques » (non sérialisés) au workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-259">Directs the activity to return "live" (not serialized) objects to the workflow.</span></span>
<span data-ttu-id="63426-260">Les objets ainsi générés ont des méthodes, ainsi que des propriétés, mais ils ne peuvent pas être enregistrés lorsqu’un point de contrôle est activé.</span><span class="sxs-lookup"><span data-stu-id="63426-260">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>

#### <a name="psdisableserializationpreference-boolean"></a><span data-ttu-id="63426-261">PSDisableSerializationPreference \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-261">PSDisableSerializationPreference \<Boolean\></span></span>

<span data-ttu-id="63426-262">Applique l’équivalent du paramètre PSDisableSerialization à l’ensemble du workflow, pas seulement à l’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-262">Applies the equivalent of the PSDisableSerialization parameter to the entire workflow, not just the activity.</span></span> <span data-ttu-id="63426-263">L’ajout de ce paramètre n’est généralement pas recommandé, car un workflow qui ne sérialise pas ses objets ne peut pas être repris ou rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="63426-263">Adding this parameter is generally not recommended, because a workflow that doesn't serialize its objects cannot be resumed or persisted.</span></span>

<span data-ttu-id="63426-264">Valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="63426-264">Valid values:</span></span>

- <span data-ttu-id="63426-265">Valeurs En cas d’omission, et que vous n’avez pas ajouté le paramètre PSDisableSerialization à une activité, les objets sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="63426-265">(Default) If omitted, and you have also not added the PSDisableSerialization parameter to an activity, objects are serialized.</span></span>

- <span data-ttu-id="63426-266">`$True`.</span><span class="sxs-lookup"><span data-stu-id="63426-266">`$True`.</span></span> <span data-ttu-id="63426-267">Indique à toutes les activités au sein d’un workflow de retourner les objets « dynamiques » (non sérialisés).</span><span class="sxs-lookup"><span data-stu-id="63426-267">Directs all activities within a workflow to return "live" (not serialized) objects.</span></span> <span data-ttu-id="63426-268">Les objets ainsi générés ont des méthodes, ainsi que des propriétés, mais ils ne peuvent pas être enregistrés lorsqu’un point de contrôle est activé.</span><span class="sxs-lookup"><span data-stu-id="63426-268">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>
- <span data-ttu-id="63426-269">`$False`.</span><span class="sxs-lookup"><span data-stu-id="63426-269">`$False`.</span></span> <span data-ttu-id="63426-270">Les objets de workflow sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="63426-270">Workflow objects are serialized.</span></span>

#### <a name="pserror-psdatacollectionerrorrecord"></a><span data-ttu-id="63426-271">PSError \<PSDataCollection[ErrorRecord]\></span><span class="sxs-lookup"><span data-stu-id="63426-271">PSError \<PSDataCollection[ErrorRecord]\></span></span>

<span data-ttu-id="63426-272">Ajoute des messages d’erreur de l’activité à la collection d’enregistrements d’erreurs spécifiée, au lieu d’écrire les messages d’erreur dans la console ou à la valeur de la propriété Error de la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-272">Adds error messages from the activity to the specified error record collection, instead of writing the error messages to the console or to the value of the Error property of the workflow job.</span></span> <span data-ttu-id="63426-273">Vous pouvez ajouter des messages d’erreur de plusieurs activités au même objet de collection d’enregistrements d’erreur.</span><span class="sxs-lookup"><span data-stu-id="63426-273">You can add error messages from multiple activities to the same error record collection object.</span></span>

<span data-ttu-id="63426-274">Pour utiliser ce paramètre commun d’activité, utilisez l' `New-Object` applet de commande pour créer un objet PSDataCollection avec un type ErrorRecord et enregistrer l’objet dans une variable.</span><span class="sxs-lookup"><span data-stu-id="63426-274">To use this activity common parameter, use the `New-Object` cmdlet to create a PSDataCollection object with a type of ErrorRecord and save the object in a variable.</span></span> <span data-ttu-id="63426-275">Ensuite, utilisez la variable comme valeur du paramètre PSError d’une ou plusieurs activités, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="63426-275">Then, use the variable as the value of the PSError parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a><span data-ttu-id="63426-276">PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-276">PSPersist \<Boolean\></span></span>

<span data-ttu-id="63426-277">Prend un point de contrôle après l’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-277">Takes a checkpoint after the activity.</span></span> <span data-ttu-id="63426-278">Ce point de contrôle s’ajoute à tous les points de contrôle spécifiés dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-278">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span> <span data-ttu-id="63426-279">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-279">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-280">Un « point de contrôle » ou un « point de persistance » est un instantané de l’état du flux de travail et des données capturées pendant l’exécution du workflow et il est enregistré dans un magasin de persistance sur le disque.</span><span class="sxs-lookup"><span data-stu-id="63426-280">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk.</span></span> <span data-ttu-id="63426-281">Le workflow Windows PowerShell utilise les données enregistrées pour reprendre un workflow suspendu ou interrompu à partir du dernier point de persistance, plutôt que de redémarrer le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-281">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="63426-282">Valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="63426-282">Valid values:</span></span>

- <span data-ttu-id="63426-283">Valeurs Si vous omettez ce paramètre, aucun point de contrôle n’est ajouté.</span><span class="sxs-lookup"><span data-stu-id="63426-283">(Default) If you omit this parameter, no checkpoints are added.</span></span> <span data-ttu-id="63426-284">Les points de contrôle sont pris en fonction des paramètres du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-284">Checkpoints are taken based on the settings for the workflow.</span></span>

- <span data-ttu-id="63426-285">`$True`.</span><span class="sxs-lookup"><span data-stu-id="63426-285">`$True`.</span></span> <span data-ttu-id="63426-286">Applique un point de contrôle une fois l’activité terminée.</span><span class="sxs-lookup"><span data-stu-id="63426-286">Takes a checkpoint after the activity completes.</span></span>
  <span data-ttu-id="63426-287">Ce point de contrôle s’ajoute à tous les points de contrôle spécifiés dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-287">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="63426-288">`$False`.</span><span class="sxs-lookup"><span data-stu-id="63426-288">`$False`.</span></span> <span data-ttu-id="63426-289">Aucun point de contrôle n’est ajouté.</span><span class="sxs-lookup"><span data-stu-id="63426-289">No checkpoints are added.</span></span> <span data-ttu-id="63426-290">Les points de contrôle sont pris uniquement lorsqu’ils sont spécifiés dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-290">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="psport-int32"></a><span data-ttu-id="63426-291">PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="63426-291">PSPort \<Int32\></span></span>

<span data-ttu-id="63426-292">Spécifie le port réseau sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-292">Specifies the network port on the target computers.</span></span> <span data-ttu-id="63426-293">Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPS).</span><span class="sxs-lookup"><span data-stu-id="63426-293">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span> <span data-ttu-id="63426-294">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-294">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-295">N’utilisez pas le paramètre PSPort, sauf si vous devez le faire.</span><span class="sxs-lookup"><span data-stu-id="63426-295">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="63426-296">Le port défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="63426-296">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="63426-297">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="63426-297">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="63426-298">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="63426-298">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="psprogress-psdatacollectionprogressrecord"></a><span data-ttu-id="63426-299">PSProgress \<PSDataCollection[ProgressRecord]\></span><span class="sxs-lookup"><span data-stu-id="63426-299">PSProgress \<PSDataCollection[ProgressRecord]\></span></span>

<span data-ttu-id="63426-300">Ajoute des messages de progression de l’activité à la collection d’enregistrements de progression spécifiée au lieu d’écrire les messages de progression dans la console ou à la valeur de la propriété Progress de la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-300">Adds progress messages from the activity to the specified progress record collection, instead of writing the progress messages to the console or to the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="63426-301">Vous pouvez ajouter des messages de progression de plusieurs activités au même objet de collection d’enregistrements de progression.</span><span class="sxs-lookup"><span data-stu-id="63426-301">You can add progress messages from multiple activities to the same progress record collection object.</span></span>

#### <a name="psprogressmessage-string"></a><span data-ttu-id="63426-302">PSProgressMessage \<String\></span><span class="sxs-lookup"><span data-stu-id="63426-302">PSProgressMessage \<String\></span></span>

<span data-ttu-id="63426-303">Spécifie la description conviviale de l’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-303">Specifies a friendly description of the activity.</span></span> <span data-ttu-id="63426-304">La valeur PSProgressMessage apparaît dans la barre de progression pendant l’exécution du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="63426-304">The PSProgressMessage value appears in the progress bar while the workflow runs.</span></span> <span data-ttu-id="63426-305">Lorsque DisplayName est également inclus dans la commande, le contenu de la barre de progression s’affiche dans \<DisplayName\> : \<PSProgressMessage\> format.</span><span class="sxs-lookup"><span data-stu-id="63426-305">When the DisplayName is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

<span data-ttu-id="63426-306">Ce paramètre est particulièrement utile pour identifier des activités dans un bloc de script ForEach-Parallel.</span><span class="sxs-lookup"><span data-stu-id="63426-306">This parameter is particularly useful for identifying activities in a ForEach -Parallel script block.</span></span> <span data-ttu-id="63426-307">Sans ce message, les activités de toutes les branches parallèles sont identifiées par le même nom.</span><span class="sxs-lookup"><span data-stu-id="63426-307">Without this message, activities in all parallel branches are identified by the same name.</span></span>

#### <a name="psremotingbehavior-remotingbehavior"></a><span data-ttu-id="63426-308">PSRemotingBehavior \<RemotingBehavior\></span><span class="sxs-lookup"><span data-stu-id="63426-308">PSRemotingBehavior \<RemotingBehavior\></span></span>

<span data-ttu-id="63426-309">Spécifie la gestion de la communication à distance lorsque l’activité est exécutée sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-309">Specifies how remoting is managed when the activity is run on target computers.</span></span>
<span data-ttu-id="63426-310">PowerShell est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63426-310">PowerShell is the default.</span></span>

<span data-ttu-id="63426-311">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="63426-311">Valid values are:</span></span>

- <span data-ttu-id="63426-312">Aucun : l’activité n’est pas exécutée sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="63426-312">None: The activity is not run on remote computers.</span></span>

- <span data-ttu-id="63426-313">PowerShell : la communication à distance Windows PowerShell est utilisée pour exécuter l’activité sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-313">PowerShell: Windows PowerShell remoting is used to run the activity on target computers.</span></span>

- <span data-ttu-id="63426-314">Personnalisé : l’activité prend en charge son propre type de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="63426-314">Custom: The activity supports its own type of remoting.</span></span> <span data-ttu-id="63426-315">Cette valeur est valide lorsque l’applet de commande qui est implémentée en tant qu’activité définit la valeur de l’attribut RemotingCapability sur SupportedByCommand et que la commande comprend le paramètre ComputerName.</span><span class="sxs-lookup"><span data-stu-id="63426-315">This value is valid when the cmdlet that is being implemented as an activity sets the value of the RemotingCapability attribute to SupportedByCommand and the command includes the ComputerName parameter.</span></span>

#### <a name="psrequiredmodules-string"></a><span data-ttu-id="63426-316">PSRequiredModules \<String[]\></span><span class="sxs-lookup"><span data-stu-id="63426-316">PSRequiredModules \<String[]\></span></span>

<span data-ttu-id="63426-317">Importe les modules spécifiés avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-317">Imports the specified modules before running the command.</span></span> <span data-ttu-id="63426-318">Entrez les noms des modules.</span><span class="sxs-lookup"><span data-stu-id="63426-318">Enter the module names.</span></span> <span data-ttu-id="63426-319">Les modules doivent être installés sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-319">The modules must be installed on the target computer.</span></span>

<span data-ttu-id="63426-320">Les modules installés dans un chemin d’accès spécifié dans la variable d’environnement PSModulePath sont automatiquement importés lors de la première utilisation d’une commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="63426-320">Modules that are installed in a path specified in the PSModulePath environment variable are automatically imported on first use of any command in the module.</span></span>
<span data-ttu-id="63426-321">Utilisez ce paramètre pour importer des modules qui ne se trouvent pas dans un emplacement PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="63426-321">Use this parameter to import modules that are not in a PSModulePath location.</span></span>

<span data-ttu-id="63426-322">Étant donné que chaque activité d’un workflow s’exécute dans sa propre session, une commande Import-Module importe un module uniquement dans la session dans laquelle il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="63426-322">Because each activity in a workflow runs in its own session, an Import-Module command imports a module only into the session in which it runs.</span></span> <span data-ttu-id="63426-323">Elle n’importe pas le module dans des sessions dans lesquelles d’autres activités sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="63426-323">It does not import the module into sessions in which other activities run.</span></span>

#### <a name="pssessionoption-pssessionoption"></a><span data-ttu-id="63426-324">PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="63426-324">PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="63426-325">Définit des options avancées pour les sessions sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-325">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="63426-326">Entrez un objet PSSessionOption, tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="63426-326">Enter a PSSessionOption object, such as one that you create by using the New-PSSessionOption cmdlet.</span></span> <span data-ttu-id="63426-327">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-327">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-328">Les valeurs par défaut pour les options de session sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="63426-328">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="63426-329">Dans le cas contraire, la session utilise les valeurs spécifiées dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="63426-329">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="63426-330">Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez la rubrique d’aide de l’applet de commande New-PSSessionOption [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="63426-330">For a description of the session options, including the default values, see the help topic for the New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="63426-331">Pour plus d’informations sur la variable de préférence $PSSessionOption, consultez [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="63426-331">For more information about the $PSSessionOption preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="psusessl-boolean"></a><span data-ttu-id="63426-332">PSUseSSL \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-332">PSUseSSL \<Boolean\></span></span>

<span data-ttu-id="63426-333">La valeur $True utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="63426-333">A value of $True uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="63426-334">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="63426-334">By default, SSL is not used.</span></span> <span data-ttu-id="63426-335">La valeur $False n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="63426-335">A value of $False has no effect.</span></span> <span data-ttu-id="63426-336">Ce paramètre commun d’activité est également un paramètre commun de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-336">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="63426-337">WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="63426-337">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="63426-338">UseSSL est une protection supplémentaire qui envoie les données via HTTPS au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="63426-338">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="63426-339">Si vous utilisez ce paramètre, mais que SSL n'est pas disponible sur le port utilisé pour la commande, celle-ci échoue.</span><span class="sxs-lookup"><span data-stu-id="63426-339">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

#### <a name="psverbose-psdatacollectionverboserecord"></a><span data-ttu-id="63426-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span><span class="sxs-lookup"><span data-stu-id="63426-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span></span>

<span data-ttu-id="63426-341">Ajoute des messages détaillés de l’activité à la collection d’enregistrements détaillés spécifiée, au lieu d’écrire les messages détaillés dans la console ou à la valeur de la propriété verbose de la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-341">Adds verbose messages from the activity to the specified verbose record collection, instead of writing the verbose messages to the console or to the value of the Verbose property of the workflow job.</span></span> <span data-ttu-id="63426-342">Vous pouvez ajouter des messages en clair de plusieurs activités au même objet de collection d’enregistrements en clair.</span><span class="sxs-lookup"><span data-stu-id="63426-342">You can add verbose messages from multiple activities to the same verbose record collection object.</span></span>

#### <a name="pswarning-psdatacollectionwarningrecord"></a><span data-ttu-id="63426-343">PSWarning \<PSDataCollection[WarningRecord]\></span><span class="sxs-lookup"><span data-stu-id="63426-343">PSWarning \<PSDataCollection[WarningRecord]\></span></span>

<span data-ttu-id="63426-344">Ajoute des messages d’avertissement de l’activité à la collection d’enregistrements d’avertissements spécifiée au lieu d’écrire les messages d’avertissement dans la console ou à la valeur de la propriété Warning de la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-344">Adds warning messages from the activity to the specified warning record collection, instead of writing the warning messages to the console or to the value of the Warning property of the workflow job.</span></span> <span data-ttu-id="63426-345">Vous pouvez ajouter des messages d’avertissement de plusieurs activités au même objet de collection d’enregistrements d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="63426-345">You can add warning messages from multiple activities to the same warning record collection object.</span></span>

#### <a name="result"></a><span data-ttu-id="63426-346">Résultats</span><span class="sxs-lookup"><span data-stu-id="63426-346">Result</span></span>

<span data-ttu-id="63426-347">Ce paramètre n’est valide que dans les workflows XAML.</span><span class="sxs-lookup"><span data-stu-id="63426-347">This parameter is valid only in XAML workflows.</span></span>

#### <a name="usedefaultinput-boolean"></a><span data-ttu-id="63426-348">UseDefaultInput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="63426-348">UseDefaultInput \<Boolean\></span></span>

<span data-ttu-id="63426-349">Accepte toutes les entrées de workflow en tant qu’entrée dans l’activité par valeur.</span><span class="sxs-lookup"><span data-stu-id="63426-349">Accepts all workflow input as input to the activity by value.</span></span>

<span data-ttu-id="63426-350">Par exemple, l’activité Get-Process de l’exemple de workflow suivant utilise le paramètre commun d’activité UseDefaultInput pour obtenir une entrée qui est transmise au workflow.</span><span class="sxs-lookup"><span data-stu-id="63426-350">For example, the Get-Process activity in the following sample workflow uses the UseDefaultInput activity common parameter to get input that is passed to the workflow.</span></span> <span data-ttu-id="63426-351">Lorsque vous exécutez le workflow avec l’entrée, cette dernière est utilisée par l’activité.</span><span class="sxs-lookup"><span data-stu-id="63426-351">When you run the workflow with input, that input is used by the activity.</span></span>

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a><span data-ttu-id="63426-352">Verbose \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="63426-352">Verbose \<SwitchParameter\></span></span>

<span data-ttu-id="63426-353">Affiche des informations détaillées sur l’opération effectuée par la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-353">Displays detailed information about the operation performed by the command.</span></span>
<span data-ttu-id="63426-354">Ces informations sont semblables aux informations contenues dans une trace ou dans un journal des transactions.</span><span class="sxs-lookup"><span data-stu-id="63426-354">This information resembles the information in a trace or in a transaction log.</span></span>
<span data-ttu-id="63426-355">Le paramètre Verbose remplace la valeur de la variable $VerbosePreference pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="63426-355">The Verbose parameter overrides the value of the $VerbosePreference variable for the current command.</span></span> <span data-ttu-id="63426-356">Ce paramètre fonctionne uniquement lorsque la commande génère un message détaillé.</span><span class="sxs-lookup"><span data-stu-id="63426-356">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="63426-357">Ce paramètre est également un paramètre commun Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-357">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="warningaction-actionpreference"></a><span data-ttu-id="63426-358">WarningAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="63426-358">WarningAction \<ActionPreference\></span></span>

<span data-ttu-id="63426-359">Détermine la façon dont l’activité répond à un avertissement.</span><span class="sxs-lookup"><span data-stu-id="63426-359">Determines how the activity responds to a warning.</span></span> <span data-ttu-id="63426-360">« Continue » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63426-360">"Continue" is the default value.</span></span> <span data-ttu-id="63426-361">Le paramètre WarningAction remplace la valeur de la variable $WarningPreference pour la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="63426-361">The WarningAction parameter overrides the value of the $WarningPreference variable for the current command.</span></span> <span data-ttu-id="63426-362">Ce paramètre fonctionne uniquement lorsque la commande génère un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="63426-362">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="63426-363">Ce paramètre est également un paramètre commun Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63426-363">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="63426-364">Valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="63426-364">Valid Values:</span></span>

- <span data-ttu-id="63426-365">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="63426-365">SilentlyContinue.</span></span> <span data-ttu-id="63426-366">Supprime le message d’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-366">Suppresses the warning message and continues executing the command.</span></span>

- <span data-ttu-id="63426-367">Pouvoir.</span><span class="sxs-lookup"><span data-stu-id="63426-367">Continue.</span></span> <span data-ttu-id="63426-368">Affiche le message d’avertissement et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-368">Displays the warning message and continues executing the command.</span></span>
  <span data-ttu-id="63426-369">« Continue » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63426-369">"Continue" is the default value.</span></span>

- <span data-ttu-id="63426-370">Inquire.</span><span class="sxs-lookup"><span data-stu-id="63426-370">Inquire.</span></span> <span data-ttu-id="63426-371">Affiche le message d’avertissement et vous invite à confirmer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="63426-371">Displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="63426-372">Cette valeur est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="63426-372">This value is rarely used.</span></span>

- <span data-ttu-id="63426-373">Arrêter.</span><span class="sxs-lookup"><span data-stu-id="63426-373">Stop.</span></span> <span data-ttu-id="63426-374">Affiche le message d’avertissement et arrête l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="63426-374">Displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="63426-375">Le paramètre WarningAction ne remplace pas la valeur de la variable de préférence $WarningAction lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="63426-375">The WarningAction parameter does not override the value of the $WarningAction preference variable when the parameter is used in a command to run a script or function.</span></span>

### <a name="examples"></a><span data-ttu-id="63426-376">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="63426-376">EXAMPLES</span></span>

<span data-ttu-id="63426-377">Les paramètres communs d’activité sont extrêmement utiles.</span><span class="sxs-lookup"><span data-stu-id="63426-377">The activity common parameters are extremely useful.</span></span> <span data-ttu-id="63426-378">Par exemple, vous pouvez utiliser le paramètre PSComputerName pour exécuter des activités spécifiques sur un sous-ensemble d’ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="63426-378">For example, you can use the PSComputerName parameter to run particular activities on only a subset of the target computers.</span></span>

<span data-ttu-id="63426-379">Vous pouvez également utiliser les paramètres PSConnectionRetryCount et PSConnectionRetryIntervalSec pour ajuster les valeurs de nouvelle tentative pour des activités particulières.</span><span class="sxs-lookup"><span data-stu-id="63426-379">Or, you might use the PSConnectionRetryCount and PSConnectionRetryIntervalSec parameters to adjust the retry values for particular activities.</span></span>

<span data-ttu-id="63426-380">L’exemple suivant montre comment utiliser les paramètres communs d’activité PSComputerName pour exécuter une activité de Get-EventLog uniquement sur des ordinateurs informatiques d’un domaine particulier.</span><span class="sxs-lookup"><span data-stu-id="63426-380">The following example shows how to use the PSComputerName activity common parameters to run a Get-EventLog activity only on computers it a particular domain.</span></span>

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a><span data-ttu-id="63426-381">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="63426-381">SEE ALSO</span></span>

<span data-ttu-id="63426-382">[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="63426-382">[about_Workflows](about_workflows.md)
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span></span>

---
description: Fournit une brève introduction à la fonctionnalité PowerShell Workflow.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207210"
---
# <a name="about-workflows"></a><span data-ttu-id="968bc-104">À propos des workflows</span><span class="sxs-lookup"><span data-stu-id="968bc-104">About Workflows</span></span>

## <a name="short-description"></a><span data-ttu-id="968bc-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="968bc-105">Short description</span></span>

<span data-ttu-id="968bc-106">Fournit une brève introduction à la fonctionnalité PowerShell Workflow.</span><span class="sxs-lookup"><span data-stu-id="968bc-106">Provides a brief introduction to the PowerShell Workflow feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="968bc-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="968bc-107">Long description</span></span>

<span data-ttu-id="968bc-108">PowerShell Workflow offre les avantages de l' [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) à PowerShell et vous permet d’écrire et d’exécuter des workflows.</span><span class="sxs-lookup"><span data-stu-id="968bc-108">PowerShell Workflow brings the benefits of the [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) to PowerShell and enables you to write and run workflows.</span></span>

<span data-ttu-id="968bc-109">PowerShell workflow a été introduit dans PowerShell 3,0 et le module est disponible jusqu’à PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="968bc-109">PowerShell Workflow was introduced in PowerShell 3.0 and the module is available up to PowerShell 5.1.</span></span> <span data-ttu-id="968bc-110">Pour plus d’informations sur PowerShell workflow, consultez le [Guide des flux de travail](/previous-versions/powershell/scripting/components/workflows-guide) et l' [écriture d’un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span><span class="sxs-lookup"><span data-stu-id="968bc-110">For more information about PowerShell Workflow, see the [Workflows Guide](/previous-versions/powershell/scripting/components/workflows-guide) and [Writing a Windows PowerShell Workflow](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span></span>

## <a name="about-workflows"></a><span data-ttu-id="968bc-111">À propos des workflows</span><span class="sxs-lookup"><span data-stu-id="968bc-111">About workflows</span></span>

<span data-ttu-id="968bc-112">Les flux de travail sont des commandes qui se composent d’une séquence ordonnée d’activités associées.</span><span class="sxs-lookup"><span data-stu-id="968bc-112">Workflows are commands that consist of an ordered sequence of related activities.</span></span> <span data-ttu-id="968bc-113">En règle générale, elles s’exécutent pendant une période prolongée, en recueillant des données à partir de centaines d’ordinateurs et en les modifiant, souvent dans des environnements hétérogènes.</span><span class="sxs-lookup"><span data-stu-id="968bc-113">Typically, they run for an extended period of time, gathering data from and making changes to hundreds of computers, often in heterogeneous environments.</span></span>

<span data-ttu-id="968bc-114">Les workflows peuvent être écrits en XAML, le langage utilisé dans Windows Workflow Foundation ou dans le langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="968bc-114">Workflows can be written in XAML, the language used in Windows Workflow Foundation, or in the PowerShell language.</span></span> <span data-ttu-id="968bc-115">Les flux de travail sont généralement empaquetés dans des modules et incluent des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="968bc-115">Workflows are typically packaged in modules and include help topics.</span></span> <span data-ttu-id="968bc-116">Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span><span class="sxs-lookup"><span data-stu-id="968bc-116">For more information, see [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span></span>

<span data-ttu-id="968bc-117">Les flux de travail sont essentiels dans un environnement informatique, car ils peuvent survivre aux redémarrages et à la récupération automatique à partir des défaillances courantes.</span><span class="sxs-lookup"><span data-stu-id="968bc-117">Workflows are critical in an IT environment because they can survive reboots and recover automatically from common failures.</span></span> <span data-ttu-id="968bc-118">Vous pouvez vous déconnecter et vous reconnecter des sessions et des ordinateurs qui exécutent des workflows sans interrompre le traitement des flux de travail, et interrompre et reprendre des flux de travail en toute transparence sans perte de données.</span><span class="sxs-lookup"><span data-stu-id="968bc-118">You can disconnect and reconnect from sessions and computers running workflows without interrupting workflow processing, and suspend and resume workflows transparently without data loss.</span></span> <span data-ttu-id="968bc-119">Chaque activité d’un workflow peut être journalisée et auditée à des fins de référence.</span><span class="sxs-lookup"><span data-stu-id="968bc-119">Each activity in a workflow can be logged and audited for reference.</span></span>
<span data-ttu-id="968bc-120">Les workflows peuvent être exécutés en tant que travaux et peuvent être planifiés à l’aide de la fonctionnalité tâches planifiées de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="968bc-120">Workflows can run as jobs and can be scheduled by using the Scheduled Jobs feature of PowerShell.</span></span>

<span data-ttu-id="968bc-121">L’État et les données d’un workflow sont enregistrés ou conservés au début et à la fin du workflow et aux points que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="968bc-121">The state and data in a workflow is saved or persisted at the beginning and end of the workflow and at points that you specify.</span></span> <span data-ttu-id="968bc-122">Les points de persistance de workflow fonctionnent comme des instantanés de base de données ou des points de contrôle de programme pour protéger le flux de travail contre les effets des interruptions et des échecs.</span><span class="sxs-lookup"><span data-stu-id="968bc-122">Workflow persistence points work like database snapshots or program checkpoints to protect the workflow from the effects of interruptions and failures.</span></span> <span data-ttu-id="968bc-123">Si le flux de travail ne parvient pas à effectuer une récupération suite à une défaillance, vous pouvez utiliser les données persistantes et reprendre à partir du dernier point de persistance, au lieu de réexécuter un flux de travail complet depuis le début.</span><span class="sxs-lookup"><span data-stu-id="968bc-123">If the workflow is unable to recover from a failure, you can use the persisted data and resume from the last persistence point, instead of rerunning an extensive workflow from the beginning.</span></span>

## <a name="workflow-requirements-and-configuration"></a><span data-ttu-id="968bc-124">Configuration requise et configuration du flux de travail</span><span class="sxs-lookup"><span data-stu-id="968bc-124">Workflow requirements and configuration</span></span>

<span data-ttu-id="968bc-125">Une configuration de workflow PowerShell se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="968bc-125">A PowerShell Workflow configuration consists of the following elements:</span></span>

- <span data-ttu-id="968bc-126">Ordinateur client qui exécute le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-126">A client computer, which runs the workflow.</span></span>
- <span data-ttu-id="968bc-127">Session de workflow, **PSSession** , sur l’ordinateur client ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="968bc-127">A workflow session, **PSSession** , on the client computer or on a remote computer.</span></span>
- <span data-ttu-id="968bc-128">Nœuds gérés, ordinateurs cibles affectés par les activités de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-128">Managed nodes, the target computers that are affected by the workflow activities.</span></span>

<span data-ttu-id="968bc-129">La session de workflow n’est pas obligatoire, mais elle est recommandée.</span><span class="sxs-lookup"><span data-stu-id="968bc-129">The workflow session isn't required, but is recommended.</span></span> <span data-ttu-id="968bc-130">**Sessions PSSession** peut tirer parti des fonctionnalités robustes de récupération et de sessions déconnectées de PowerShell pour récupérer les sessions de workflow déconnectées.</span><span class="sxs-lookup"><span data-stu-id="968bc-130">**PSSessions** can take advantage of the robust recovery and Disconnected Sessions features of PowerShell to recover disconnected workflow sessions.</span></span> <span data-ttu-id="968bc-131">Pour plus d’informations, consultez [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span><span class="sxs-lookup"><span data-stu-id="968bc-131">For more information, see [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span></span>

<span data-ttu-id="968bc-132">Étant donné que l’ordinateur client et l’ordinateur sur lequel la session de workflow s’exécute peuvent être des nœuds gérés, vous pouvez exécuter un workflow sur un ordinateur unique qui assume tous les rôles.</span><span class="sxs-lookup"><span data-stu-id="968bc-132">Because the client computer and the computer on which the workflow session runs can be managed nodes, you can run a workflow on a single computer that fulfills all roles.</span></span>

<span data-ttu-id="968bc-133">L’ordinateur client et l’ordinateur sur lequel la session de workflow s’exécute doivent exécuter PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="968bc-133">The client computer and the computer on which the workflow session runs must be running PowerShell 3.0.</span></span> <span data-ttu-id="968bc-134">Tous les systèmes éligibles sont pris en charge, y compris les options d’installation minimale des systèmes d’exploitation Windows Server.</span><span class="sxs-lookup"><span data-stu-id="968bc-134">All eligible systems are supported, including the Server Core installation options of Windows Server operating systems.</span></span>

<span data-ttu-id="968bc-135">Pour exécuter des workflows qui incluent des applets de commande, les nœuds gérés doivent avoir Windows PowerShell 2,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="968bc-135">To run workflows that include cmdlets, the managed nodes must have Windows PowerShell 2.0 or later.</span></span> <span data-ttu-id="968bc-136">Les nœuds gérés ne requièrent pas PowerShell, sauf si le flux de travail comprend des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="968bc-136">Managed nodes don't require PowerShell unless the workflow includes cmdlets.</span></span> <span data-ttu-id="968bc-137">Vous pouvez exécuter des workflows qui incluent des commandes Windows Management Instrumentation (WMI) et Common Information Model (CIM) sur des ordinateurs qui n’ont pas PowerShell.</span><span class="sxs-lookup"><span data-stu-id="968bc-137">You can run workflows that include Windows Management Instrumentation (WMI) and Common Information Model (CIM) commands on computers that don't have PowerShell.</span></span>

## <a name="how-to-get-workflows"></a><span data-ttu-id="968bc-138">Comment accéder aux flux de travail</span><span class="sxs-lookup"><span data-stu-id="968bc-138">How to get workflows</span></span>

<span data-ttu-id="968bc-139">Les flux de travail sont généralement empaquetés dans des modules.</span><span class="sxs-lookup"><span data-stu-id="968bc-139">Workflows are typically packaged in modules.</span></span> <span data-ttu-id="968bc-140">Pour importer le module qui comprend un flux de travail, utilisez une commande quelconque dans le module ou utilisez l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="968bc-140">To import the module that includes a workflow, use any command in the module or use the `Import-Module` cmdlet.</span></span>
<span data-ttu-id="968bc-141">Les modules sont automatiquement importés lors de la première utilisation d’une commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="968bc-141">Modules are imported automatically on first use of any command in the module.</span></span>

<span data-ttu-id="968bc-142">Pour rechercher les workflows dans les modules installés sur votre ordinateur, utilisez le `Get-Command` paramètre **CommandType** de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="968bc-142">To find the workflows in modules installed on your computer, use the `Get-Command` cmdlet's **CommandType** parameter.</span></span>

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a><span data-ttu-id="968bc-143">Comment exécuter des workflows</span><span class="sxs-lookup"><span data-stu-id="968bc-143">How to run workflows</span></span>

<span data-ttu-id="968bc-144">Pour exécuter un workflow, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="968bc-144">To run a workflow, use the following procedure.</span></span>

1. <span data-ttu-id="968bc-145">Si le nœud géré est l’ordinateur local, cette étape n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="968bc-145">When the managed node is the local computer, this step isn't required.</span></span>
   <span data-ttu-id="968bc-146">Dans le cas contraire, sur l’ordinateur client, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="968bc-146">Otherwise, on the client computer, start PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. <span data-ttu-id="968bc-147">Activez la communication à distance PowerShell sur l’ordinateur qui exécute la session de workflow et sur les nœuds gérés affectés par les workflows qui incluent des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="968bc-147">Enable PowerShell remoting on the computer that runs the workflow session and on managed nodes affected by workflows that include cmdlets.</span></span>

   <span data-ttu-id="968bc-148">Vous ne devez effectuer cette étape qu’une seule fois sur chaque ordinateur participant.</span><span class="sxs-lookup"><span data-stu-id="968bc-148">You only need to do this step once on each participating computer.</span></span>

   <span data-ttu-id="968bc-149">Cette étape est requise uniquement lors de l’exécution de flux de travail qui incluent des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="968bc-149">This step is required only when running workflows that include cmdlets.</span></span> <span data-ttu-id="968bc-150">Vous n’avez pas besoin d’activer la communication à distance sur l’ordinateur client, sauf si la session workflows s’exécute sur l’ordinateur client ou sur des nœuds gérés qui exécutent PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="968bc-150">You don't need to enable remoting on the client computer, unless the workflows session runs on the client computer, or on any managed nodes that are running PowerShell 3.0.</span></span>

   <span data-ttu-id="968bc-151">Pour activer la communication à distance, utilisez l’applet de commande `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="968bc-151">To enable remoting, use the `Enable-PSRemoting` cmdlet.</span></span>

   ```powershell
   Enable-PSRemoting -Force
   ```

   <span data-ttu-id="968bc-152">Vous pouvez activer la communication à distance à l’aide du paramètre **activer l’exécution du Script** stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="968bc-152">You can enable remoting by using the **Turn on Script Execution** Group Policy setting.</span></span> <span data-ttu-id="968bc-153">Pour plus d’informations, consultez [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) et [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="968bc-153">For more information, see [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) and [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

1. <span data-ttu-id="968bc-154">Utilisez les `New-PSWorkflowSession` `New-PSSession` applets de commande ou pour créer la session de Workflow.</span><span class="sxs-lookup"><span data-stu-id="968bc-154">Use the `New-PSWorkflowSession` or `New-PSSession` cmdlets to create the workflow session.</span></span>

   <span data-ttu-id="968bc-155">L' `New-PSWorkflowSession` applet de commande démarre une session qui utilise la configuration de session **Microsoft. PowerShell. Workflow** intégrée sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="968bc-155">The `New-PSWorkflowSession` cmdlet starts a session that uses the built-in **Microsoft.PowerShell.Workflow** session configuration on the destination computer.</span></span> <span data-ttu-id="968bc-156">Cette configuration de session comprend des scripts, des fichiers de type et de mise en forme, ainsi que des options conçues pour les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-156">This session configuration includes scripts, type and formatting files, and options that are designed for workflows.</span></span>

   <span data-ttu-id="968bc-157">Ou utilisez l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="968bc-157">Or, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="968bc-158">Utilisez le paramètre **ConfigurationName** pour spécifier la configuration de session **Microsoft. PowerShell. Workflow** .</span><span class="sxs-lookup"><span data-stu-id="968bc-158">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span> <span data-ttu-id="968bc-159">Cette commande est identique à l’utilisation de l’applet de commande `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="968bc-159">This command is the same as using the `New-PSWorkflowSession` cmdlet.</span></span>

   <span data-ttu-id="968bc-160">Une alternative consiste à utiliser l' `New-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="968bc-160">An alternative is to use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="968bc-161">Utilisez le paramètre **ConfigurationName** pour spécifier la configuration de session **Microsoft. PowerShell. Workflow** .</span><span class="sxs-lookup"><span data-stu-id="968bc-161">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

   <span data-ttu-id="968bc-162">Sur l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="968bc-162">On the local computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   <span data-ttu-id="968bc-163">Sur un ordinateur distant :</span><span class="sxs-lookup"><span data-stu-id="968bc-163">On a remote computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   <span data-ttu-id="968bc-164">Si vous êtes administrateur sur l’ordinateur de la session de workflow, vous pouvez utiliser l' `New-PSWorkflowExecutionOption` applet de commande pour créer des paramètres d’option personnalisés pour la configuration de session de Workflow.</span><span class="sxs-lookup"><span data-stu-id="968bc-164">If you are an Administrator on the workflow session computer, you can use the `New-PSWorkflowExecutionOption` cmdlet to create custom option settings for the workflow session configuration.</span></span> <span data-ttu-id="968bc-165">Utilisez l' `Set-PSSessionConfiguration` applet de commande pour modifier la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="968bc-165">And, use the `Set-PSSessionConfiguration` cmdlet to change the session configuration.</span></span>

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. <span data-ttu-id="968bc-166">Exécutez le workflow dans la session de Workflow.</span><span class="sxs-lookup"><span data-stu-id="968bc-166">Run the workflow in the workflow session.</span></span> <span data-ttu-id="968bc-167">Pour spécifier les noms des nœuds gérés, les ordinateurs cibles, utilisez le paramètre commun de workflow **PSComputerName** .</span><span class="sxs-lookup"><span data-stu-id="968bc-167">To specify the names of the managed nodes, target computers, use the **PSComputerName** workflow common parameter.</span></span>

   <span data-ttu-id="968bc-168">Les exemples suivants exécutent le workflow nommé **test-Workflow** .</span><span class="sxs-lookup"><span data-stu-id="968bc-168">The following examples run the workflow named **Test-Workflow** .</span></span>

   <span data-ttu-id="968bc-169">Où le nœud géré est l’ordinateur qui héberge la session de workflow :</span><span class="sxs-lookup"><span data-stu-id="968bc-169">Where the managed node is the computer that hosts the workflow session:</span></span>

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   <span data-ttu-id="968bc-170">Où les nœuds gérés sont des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="968bc-170">Where the managed nodes are remote computers.</span></span>

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   <span data-ttu-id="968bc-171">L’exemple suivant exécute **test-Workflow** sur des centaines d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="968bc-171">The following example runs the **Test-Workflow** on hundreds of computers.</span></span> <span data-ttu-id="968bc-172">L' `Get-Content` applet de commande obtient les noms d’ordinateur à partir d’un fichier texte et les enregistre dans la `$Servers` variable sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="968bc-172">The `Get-Content` cmdlet gets the computer names from a text file and saves them in the `$Servers` variable on the local computer.</span></span>

   <span data-ttu-id="968bc-173">`Invoke-Command` utilise le `$Using` modificateur de portée pour définir la `$Servers` variable dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="968bc-173">`Invoke-Command` uses the `$Using` scope modifier to define the `$Servers` variable in the local session.</span></span> <span data-ttu-id="968bc-174">Pour plus d’informations sur le `$Using` modificateur d’étendue, consultez [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="968bc-174">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a><span data-ttu-id="968bc-175">Utilisation des paramètres communs de workflow</span><span class="sxs-lookup"><span data-stu-id="968bc-175">Using workflow common parameters</span></span>

<span data-ttu-id="968bc-176">Les paramètres communs de workflow sont un ensemble de paramètres que PowerShell ajoute automatiquement à tous les flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-176">The workflow common parameters are a set of parameters that PowerShell adds automatically to all workflows.</span></span> <span data-ttu-id="968bc-177">PowerShell ajoute les paramètres communs de l’applet de commande à tous les flux de travail, même si le workflow n’utilise pas l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="968bc-177">PowerShell adds the cmdlet common parameters to all workflows, even if the workflow doesn't use the **CmdletBinding** attribute.</span></span>

<span data-ttu-id="968bc-178">Par exemple, le workflow suivant ne définit aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="968bc-178">For example, the following workflow defines no parameters.</span></span> <span data-ttu-id="968bc-179">Toutefois, lorsque vous exécutez le workflow, il a à la fois les types **paramètres_courants** et **WorkflowCommonParameters** .</span><span class="sxs-lookup"><span data-stu-id="968bc-179">However, when you run the workflow, it has both the **CommonParameters** and **WorkflowCommonParameters** .</span></span>

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

<span data-ttu-id="968bc-180">Les paramètres communs de workflow incluent plusieurs paramètres qui sont essentiels à l’exécution de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-180">The workflow common parameters include several parameters that are essential to running workflows.</span></span> <span data-ttu-id="968bc-181">Par exemple, le paramètre commun **PSComputerName** spécifie les nœuds gérés affectés par le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="968bc-181">For example, the **PSComputerName** common parameter specifies the managed nodes that the workflow affects.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

<span data-ttu-id="968bc-182">Le paramètre commun de workflow **PSPersist** détermine le moment où les données de workflow sont conservées.</span><span class="sxs-lookup"><span data-stu-id="968bc-182">The **PSPersist** workflow common parameter determines when workflow data is persisted.</span></span> <span data-ttu-id="968bc-183">Elle vous permet d’ajouter un point de persistance entre les activités aux flux de travail qui ne définissent pas de points de persistance.</span><span class="sxs-lookup"><span data-stu-id="968bc-183">It enables you to add persistence point between activities to workflows that don't define persistence points.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

<span data-ttu-id="968bc-184">D’autres paramètres communs de workflow vous permettent de spécifier les caractéristiques de la connexion à distance aux nœuds gérés.</span><span class="sxs-lookup"><span data-stu-id="968bc-184">Other workflow common parameters let you specify the characteristics of the remote connection to the managed nodes.</span></span> <span data-ttu-id="968bc-185">Leurs noms et leurs fonctionnalités sont similaires aux paramètres des applets de commande de communication à distance, y compris `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="968bc-185">Their names and functionality are similar to the parameters of remoting cmdlets, including `Invoke-Command`.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

<span data-ttu-id="968bc-186">Veillez à distinguer les paramètres de communication à distance qui définissent la connexion pour la session de workflow des paramètres communs de flux de travail du **préfixe PS** qui définissent la connexion aux nœuds gérés.</span><span class="sxs-lookup"><span data-stu-id="968bc-186">Take care to distinguish the remoting parameters that define the connection for the workflow session from the **PS-prefixed** workflow common parameters that define the connection to the managed nodes.</span></span>

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

<span data-ttu-id="968bc-187">Certains paramètres communs de workflow sont propres aux workflows, tels que le paramètre **PSParameterCollection** qui vous permet de spécifier des valeurs de paramètres communes de workflow différentes pour différents nœuds distants.</span><span class="sxs-lookup"><span data-stu-id="968bc-187">Some workflow common parameters are unique to workflows, such as the **PSParameterCollection** parameter that lets you specify different workflow common parameter values for different remote nodes.</span></span> <span data-ttu-id="968bc-188">Pour obtenir une liste et une description des paramètres communs de workflow, consultez [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="968bc-188">For a list and description of the workflow common parameters, see [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="968bc-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="968bc-189">See also</span></span>

[<span data-ttu-id="968bc-190">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="968bc-190">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[<span data-ttu-id="968bc-191">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="968bc-191">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

<span data-ttu-id="968bc-192">Applets de commande [PSWorkflow](xref:PSWorkflow)</span><span class="sxs-lookup"><span data-stu-id="968bc-192">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="968bc-193">Guide des workflows</span><span class="sxs-lookup"><span data-stu-id="968bc-193">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="968bc-194">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="968bc-194">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)

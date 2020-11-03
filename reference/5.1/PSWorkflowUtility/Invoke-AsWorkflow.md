---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202965"
---
# <span data-ttu-id="54be9-103">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="54be9-103">Invoke-AsWorkflow</span></span>

## <span data-ttu-id="54be9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="54be9-104">SYNOPSIS</span></span>
<span data-ttu-id="54be9-105">Exécute une commande ou une expression comme un workflow Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54be9-105">Runs a command or expression as a Windows PowerShell Workflow.</span></span>

## <span data-ttu-id="54be9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54be9-106">SYNTAX</span></span>

### <span data-ttu-id="54be9-107">Command (par défaut)</span><span class="sxs-lookup"><span data-stu-id="54be9-107">Command (Default)</span></span>

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### <span data-ttu-id="54be9-108">Expression</span><span class="sxs-lookup"><span data-stu-id="54be9-108">Expression</span></span>

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## <span data-ttu-id="54be9-109">Description</span><span class="sxs-lookup"><span data-stu-id="54be9-109">DESCRIPTION</span></span>

<span data-ttu-id="54be9-110">Le `Invoke-AsWorkflow` flux de travail exécute une commande ou une expression comme un script inline dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="54be9-110">The `Invoke-AsWorkflow` workflow runs any command or expression as an inline script in a workflow.</span></span>
<span data-ttu-id="54be9-111">Ces workflows utilisent la sémantique de workflow standard, ont tous les paramètres communs de workflow et tous les avantages de workflow, notamment la possibilité d'arrêter, de reprendre et de récupérer.</span><span class="sxs-lookup"><span data-stu-id="54be9-111">These workflows use the standard workflow semantics, have all workflow common parameters, and have all benefits of workflows, including the ability to stop, resume, and recover.</span></span>

<span data-ttu-id="54be9-112">Les workflows sont conçus pour les commandes de longue durée collectant des données essentielles, mais peuvent être utilisés pour exécuter toute commande.</span><span class="sxs-lookup"><span data-stu-id="54be9-112">Workflows are designed for long-running commands that collect critical data, but can be used to run any command.</span></span>
<span data-ttu-id="54be9-113">Pour plus d’informations, consultez [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="54be9-113">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

<span data-ttu-id="54be9-114">Vous pouvez également ajouter des paramètres communs de workflow à cette commande.</span><span class="sxs-lookup"><span data-stu-id="54be9-114">You can also add workflow common parameters to this command.</span></span>
<span data-ttu-id="54be9-115">Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="54be9-115">For more information about workflow common parameters, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="54be9-116">Ce workflow est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="54be9-116">This workflow is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="54be9-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="54be9-117">EXAMPLES</span></span>

### <span data-ttu-id="54be9-118">Exemple 1 : exécuter une applet de commande en tant que Workflow</span><span class="sxs-lookup"><span data-stu-id="54be9-118">Example 1: Run a cmdlet as a workflow</span></span>

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

<span data-ttu-id="54be9-119">Cette commande exécute l' `Get-ExecutionPolicy` applet de commande en tant que flux de travail sur des centaines d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="54be9-119">This command runs the `Get-ExecutionPolicy` cmdlet as a workflow on hundreds of computers.</span></span>

<span data-ttu-id="54be9-120">La commande utilise le paramètre **CommandName** pour spécifier l'applet de commande exécutée dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="54be9-120">The command uses the **CommandName** parameter to specify the cmdlet that runs in the workflow.</span></span>
<span data-ttu-id="54be9-121">Elle utilise le paramètre commun de workflow **PSComputerName** pour spécifier les ordinateurs sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="54be9-121">It uses the **PSComputerName** workflow common parameter to specify the computers on which the command runs.</span></span>
<span data-ttu-id="54be9-122">La valeur du paramètre **PSComputerName** est une `Get-Content` commande qui obtient une liste de noms d’ordinateurs à partir du fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="54be9-122">The value of the **PSComputerName** parameter is a `Get-Content` command that gets a list of computer names from the Servers.txt file.</span></span>
<span data-ttu-id="54be9-123">La valeur du paramètre est placée entre parenthèses pour indiquer à Windows PowerShell d’exécuter la `Get-Command` commande avant d’utiliser la valeur.</span><span class="sxs-lookup"><span data-stu-id="54be9-123">The parameter value is enclosed in parentheses to direct Windows PowerShell to run the `Get-Command` command before using the value.</span></span>

<span data-ttu-id="54be9-124">Comme avec toutes les commandes à distance, si la commande s'exécute sur l'ordinateur local (si la valeur du paramètre PSComputerName inclut l'ordinateur local), vous devez démarrer Windows PowerShell avec l'option « Exécuter en tant qu'administrateur ».</span><span class="sxs-lookup"><span data-stu-id="54be9-124">As with all remote commands, if the command runs on the local computer, (if the value of the PSComputerName parameter includes the local computer), you must start Windows PowerShell with the "Run as administrator" option.</span></span>

### <span data-ttu-id="54be9-125">Exemple 2 : exécuter une applet de commande avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="54be9-125">Example 2: Run a cmdlet with parameters</span></span>

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

<span data-ttu-id="54be9-126">La première commande utilise l' `Import-Csv` applet de commande pour créer un objet à partir du contenu du fichier Servers.csv.</span><span class="sxs-lookup"><span data-stu-id="54be9-126">The first command uses the `Import-Csv` cmdlet to create an object from the content in the Servers.csv file.</span></span> <span data-ttu-id="54be9-127">La commande utilise le `Header` paramètre pour créer une `ServerName` propriété pour la colonne qui contient les noms des ordinateurs cibles, également appelés « nœuds distants ».</span><span class="sxs-lookup"><span data-stu-id="54be9-127">The command uses the `Header` parameter to create a `ServerName` property for the column that contains the names of the target computers, also known as "remote nodes."</span></span> <span data-ttu-id="54be9-128">La commande enregistre le résultat dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="54be9-128">The command saves the result in the `$s` variable.</span></span>

<span data-ttu-id="54be9-129">La deuxième commande utilise le `Invoke-AsWorkflow` flux de travail pour exécuter une `Get-ExecutionPolicy` commande sur les ordinateurs du fichier Servers.csv.</span><span class="sxs-lookup"><span data-stu-id="54be9-129">The second command uses the `Invoke-AsWorkflow` workflow to run a `Get-ExecutionPolicy` command on the computers in the Servers.csv file.</span></span> <span data-ttu-id="54be9-130">La commande utilise le paramètre **CommandName** de `Invoke-AsWorkflow`  pour spécifier la commande à exécuter dans le Workflow.</span><span class="sxs-lookup"><span data-stu-id="54be9-130">The command uses the **CommandName** parameter of `Invoke-AsWorkflow`  to specify the command to run in the workflow.</span></span> <span data-ttu-id="54be9-131">Elle utilise le `Parameter` paramètre de `Invoke-AsWorkflow` pour spécifier le `Scope` paramètre de l' `Get-ExecutionPolicy` applet de commande avec la valeur **Process** . La commande utilise également le `PSConnectionRetryCount` paramètre commun de flux de travail pour limiter la commande à cinq tentatives sur chaque ordinateur et le `PSComputerName` paramètre commun de flux de travail pour spécifier les noms des nœuds distants (ordinateurs cibles).</span><span class="sxs-lookup"><span data-stu-id="54be9-131">It uses the `Parameter` parameter of `Invoke-AsWorkflow` to specify the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** .The command also uses the `PSConnectionRetryCount` workflow common parameter to limit the command to five attempts on each computer and the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span> <span data-ttu-id="54be9-132">La valeur du `PSComputerName` paramètre est une expression qui obtient la `ServerName` propriété de chaque objet dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="54be9-132">The value of the `PSComputerName` parameter is an expression that gets the `ServerName` property of every object in the `$s` variable.</span></span>

<span data-ttu-id="54be9-133">Ces commandes exécutent une `Get-ExecutionPolicy` commande en tant que flux de travail sur des centaines d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="54be9-133">These commands run a `Get-ExecutionPolicy` command as a workflow on hundreds of computers.</span></span>
<span data-ttu-id="54be9-134">La commande utilise le `Scope` paramètre de l' `Get-ExecutionPolicy` applet de commande avec la valeur **Process** pour obtenir la stratégie d’exécution dans la session active.</span><span class="sxs-lookup"><span data-stu-id="54be9-134">The command uses the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** to get the execution policy in the current session.</span></span>

### <span data-ttu-id="54be9-135">Exemple 3 : exécuter une expression en tant que flux de travail</span><span class="sxs-lookup"><span data-stu-id="54be9-135">Example 3: Run an expression as a workflow</span></span>

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

<span data-ttu-id="54be9-136">Cette commande utilise le `Invoke-AsWorkflow` flux de travail pour exécuter une commande ipconfig en tant que tâche de workflow sur les ordinateurs figurant dans le fichier DomainControllers.txt.</span><span class="sxs-lookup"><span data-stu-id="54be9-136">This command uses the `Invoke-AsWorkflow` workflow to run an Ipconfig command as a workflow job on the computers listed in the DomainControllers.txt file.</span></span>

<span data-ttu-id="54be9-137">La commande utilise le `Expression` paramètre pour spécifier l’expression à exécuter.</span><span class="sxs-lookup"><span data-stu-id="54be9-137">The command uses the `Expression` parameter to specify the expression to run.</span></span>
<span data-ttu-id="54be9-138">Elle utilise le `PSComputerName` paramètre commun de flux de travail pour spécifier les noms des nœuds distants (ordinateurs cibles).</span><span class="sxs-lookup"><span data-stu-id="54be9-138">It uses the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span>

<span data-ttu-id="54be9-139">La commande utilise également les `AsJob` paramètres communs de flux de travail et `JobName` pour exécuter le workflow en tant que tâche en arrière-plan sur chaque ordinateur avec le nom de travail « ipconfig ».</span><span class="sxs-lookup"><span data-stu-id="54be9-139">The command also uses the `AsJob` and `JobName` workflow common parameters to run the workflow as a background job on each computer with the "Ipconfig" job name.</span></span>

<span data-ttu-id="54be9-140">La commande retourne un `ContainerParentJob` objet ( `System.Management.Automation.ContainerParentJob` ) qui contient les tâches de workflow sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="54be9-140">The command returns a `ContainerParentJob` object (`System.Management.Automation.ContainerParentJob`) that contains the workflow jobs on each computer.</span></span>

## <span data-ttu-id="54be9-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54be9-141">PARAMETERS</span></span>

### <span data-ttu-id="54be9-142">-CommandName</span><span class="sxs-lookup"><span data-stu-id="54be9-142">-CommandName</span></span>

<span data-ttu-id="54be9-143">Exécute l'applet de commande ou la fonction avancée spécifiée comme un workflow.</span><span class="sxs-lookup"><span data-stu-id="54be9-143">Runs the specified cmdlet or advanced function as a workflow.</span></span>
<span data-ttu-id="54be9-144">Entrez le nom de l’applet de commande ou de la fonction, tel que `Update-Help` , `Set-ExecutionPolicy` ou `Set-NetFirewallRule` .</span><span class="sxs-lookup"><span data-stu-id="54be9-144">Enter the cmdlet or function name, such as `Update-Help`, `Set-ExecutionPolicy`, or `Set-NetFirewallRule`.</span></span>

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54be9-145">-Expression</span><span class="sxs-lookup"><span data-stu-id="54be9-145">-Expression</span></span>

<span data-ttu-id="54be9-146">Spécifie l’expression que cette applet de commande exécute en tant que flux de travail.</span><span class="sxs-lookup"><span data-stu-id="54be9-146">Specifies the  expression that this cmdlet runs as a workflow.</span></span>
<span data-ttu-id="54be9-147">Entrez l’expression sous la forme d’une chaîne, telle que `"ipconfig /all"` .</span><span class="sxs-lookup"><span data-stu-id="54be9-147">Enter the expression as a string, such as `"ipconfig /all"`.</span></span>
<span data-ttu-id="54be9-148">Si l'expression comprend des espaces ou des caractères spéciaux, placez l'expression entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="54be9-148">If the expression includes spaces or special characters, enclose the expression in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54be9-149">Paramètres </span><span class="sxs-lookup"><span data-stu-id="54be9-149">-Parameter</span></span>

<span data-ttu-id="54be9-150">Spécifie les paramètres et les valeurs de paramètre de la commande spécifiée dans le `CommandName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="54be9-150">Specifies the parameters and parameter values of the command that is specified in the `CommandName` parameter.</span></span>
<span data-ttu-id="54be9-151">Entrez une table de hachage dans laquelle chaque clé est un nom de paramètre et sa valeur est la valeur du paramètre, par exemple `@{ExecutionPolicy="AllSigned"}` .</span><span class="sxs-lookup"><span data-stu-id="54be9-151">Enter a hash table in which each key is a parameter name and its value is the parameter value, such as `@{ExecutionPolicy="AllSigned"}`.</span></span>

<span data-ttu-id="54be9-152">Pour plus d’informations sur les tables de hachage, consultez [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="54be9-152">For information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54be9-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="54be9-153">-InputObject</span></span>

<span data-ttu-id="54be9-154">Utilisé pour autoriser l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="54be9-154">Used to allows pipeline input.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="54be9-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54be9-155">CommonParameters</span></span>

<span data-ttu-id="54be9-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54be9-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54be9-157">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="54be9-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

### <span data-ttu-id="54be9-158">WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="54be9-158">WorkflowCommonParameters</span></span>

<span data-ttu-id="54be9-159">Cette applet de commande prend également en charge les paramètres communs spécifiques au flux de travail.</span><span class="sxs-lookup"><span data-stu-id="54be9-159">This cmdlet also supports workflow specific common parameters.</span></span>
<span data-ttu-id="54be9-160">Pour plus d’informations, consultez [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="54be9-160">For information, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span></span>

## <span data-ttu-id="54be9-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="54be9-161">INPUTS</span></span>

### <span data-ttu-id="54be9-162">System.Object</span><span class="sxs-lookup"><span data-stu-id="54be9-162">System.Object</span></span>

<span data-ttu-id="54be9-163">Vous pouvez diriger n’importe quel objet vers le `InputObject` paramètre.</span><span class="sxs-lookup"><span data-stu-id="54be9-163">You can pipe any object to the `InputObject` parameter.</span></span>

## <span data-ttu-id="54be9-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="54be9-164">OUTPUTS</span></span>

### <span data-ttu-id="54be9-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="54be9-165">None</span></span>

<span data-ttu-id="54be9-166">Cette commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="54be9-166">This command does not generate any output.</span></span>
<span data-ttu-id="54be9-167">Toutefois, elle exécute le workflow, ce qui peut générer une sortie.</span><span class="sxs-lookup"><span data-stu-id="54be9-167">However, it runs the workflow, which might generate output.</span></span>

## <span data-ttu-id="54be9-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="54be9-168">NOTES</span></span>

## <span data-ttu-id="54be9-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="54be9-169">RELATED LINKS</span></span>

[<span data-ttu-id="54be9-170">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="54be9-170">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="54be9-171">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="54be9-171">New-PSWorkflowSession</span></span>](../PSWorkflow/New-PSWorkflowSession.md)

[<span data-ttu-id="54be9-172">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="54be9-172">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="54be9-173">about_Workflow_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="54be9-173">about_Workflow_Common_Parameters</span></span>](../PSWorkflow/About/about_WorkflowCommonParameters.md)

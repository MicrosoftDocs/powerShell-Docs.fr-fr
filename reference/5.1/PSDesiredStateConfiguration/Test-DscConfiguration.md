---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203074"
---
# <span data-ttu-id="059d7-103">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="059d7-103">Test-DscConfiguration</span></span>

## <span data-ttu-id="059d7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="059d7-104">SYNOPSIS</span></span>
<span data-ttu-id="059d7-105">Teste si la configuration réelle sur les nœuds correspond à la configuration souhaitée.</span><span class="sxs-lookup"><span data-stu-id="059d7-105">Tests whether the actual configuration on the nodes matches the desired configuration.</span></span>

## <span data-ttu-id="059d7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="059d7-106">SYNTAX</span></span>

### <span data-ttu-id="059d7-107">ComputerNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="059d7-107">ComputerNameSet (Default)</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### <span data-ttu-id="059d7-108">ComputerNameAndPathSet</span><span class="sxs-lookup"><span data-stu-id="059d7-108">ComputerNameAndPathSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="059d7-109">ComputerNameAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="059d7-109">ComputerNameAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="059d7-110">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="059d7-110">CimSessionAndPathSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="059d7-111">CimSessionAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="059d7-111">CimSessionAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="059d7-112">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="059d7-112">CimSessionSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## <span data-ttu-id="059d7-113">Description</span><span class="sxs-lookup"><span data-stu-id="059d7-113">DESCRIPTION</span></span>
<span data-ttu-id="059d7-114">L'applet de commande **Test-DscConfiguration** teste si la configuration réelle sur les nœuds correspond à la configuration souhaitée.</span><span class="sxs-lookup"><span data-stu-id="059d7-114">The **Test-DscConfiguration** cmdlet tests whether the actual configuration on the nodes matches the desired configuration.</span></span>
<span data-ttu-id="059d7-115">Spécifiez les ordinateurs pour lesquels vous souhaitez tester les configurations à l’aide de noms d’ordinateur ou de sessions Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="059d7-115">Specify which computers for which you want to test configurations by using computer names or Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="059d7-116">Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande teste la configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="059d7-116">If you do not specify a target computer, the cmdlet tests configuration of the local computer.</span></span>

<span data-ttu-id="059d7-117">Si les configurations souhaitées et réelles correspondent, l’applet de commande retourne la valeur de chaîne « true ».</span><span class="sxs-lookup"><span data-stu-id="059d7-117">If the desired and actual configurations match, the cmdlet returns a string value of 'True'.</span></span>
<span data-ttu-id="059d7-118">Sinon, elle retourne une valeur de chaîne de « false ».</span><span class="sxs-lookup"><span data-stu-id="059d7-118">Otherwise, it returns a string value of 'False'.</span></span>

## <span data-ttu-id="059d7-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="059d7-119">EXAMPLES</span></span>

### <span data-ttu-id="059d7-120">Exemple 1 : configuration de test pour l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="059d7-120">Example 1: Test configuration for the local computer</span></span>

```
PS C:\> Test-DscConfiguration
```

<span data-ttu-id="059d7-121">Cette commande teste la configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="059d7-121">This command tests configuration for the local computer.</span></span>

### <span data-ttu-id="059d7-122">Exemple 2 : configuration de test pour un ordinateur spécifié</span><span class="sxs-lookup"><span data-stu-id="059d7-122">Example 2: Test configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

<span data-ttu-id="059d7-123">Cet exemple teste la configuration d'un ordinateur spécifié par une session CIM.</span><span class="sxs-lookup"><span data-stu-id="059d7-123">This example test configuration from a computer specified by a CIM session.</span></span>
<span data-ttu-id="059d7-124">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="059d7-124">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="059d7-125">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="059d7-125">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="059d7-126">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.</span><span class="sxs-lookup"><span data-stu-id="059d7-126">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="059d7-127">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="059d7-127">The command prompts you for a password.</span></span>
<span data-ttu-id="059d7-128">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="059d7-128">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="059d7-129">La deuxième commande teste la configuration des ordinateurs identifiés par les objets **CimSession** stockés dans la variable $Session (dans ce cas, l'ordinateur nommé Server01).</span><span class="sxs-lookup"><span data-stu-id="059d7-129">The second command tests configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

### <span data-ttu-id="059d7-130">Exemple 3 : configurations de test avec des résultats détaillés</span><span class="sxs-lookup"><span data-stu-id="059d7-130">Example 3: Test configurations with detailed results</span></span>

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

<span data-ttu-id="059d7-131">Cette commande teste les configurations pour un ensemble d’ordinateurs spécifiés par le paramètre *ComputerName* et retourne des informations détaillées qui incluent l’état global, les ressources qui sont dans l’état souhaité, les ressources qui ne sont pas dans l’état souhaité et le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="059d7-131">This command tests configurations for a set of computers specified by the *ComputerName* parameter and returns detailed information that includes the overall state, resources that are in the desired state, resources that are not in the desired state and computer name.</span></span>

### <span data-ttu-id="059d7-132">Exemple 4 : configurations de test spécifiées dans un dossier</span><span class="sxs-lookup"><span data-stu-id="059d7-132">Example 4: Test configurations specified in a folder</span></span>

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

<span data-ttu-id="059d7-133">Cette commande teste les configurations définies dans un dossier spécifié par le paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="059d7-133">This command tests configurations that are defined in a folder specified by the *Path* parameter.</span></span>
<span data-ttu-id="059d7-134">Les configurations sont testées sur un ensemble d’ordinateurs, chacun identifié par le nom de fichier du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="059d7-134">The configurations are tested against a set of computers, each identified by the file name of the configuration file.</span></span>

### <span data-ttu-id="059d7-135">Exemple 5 : configurations de test spécifiées dans un fichier</span><span class="sxs-lookup"><span data-stu-id="059d7-135">Example 5: Test configurations specified in a file</span></span>

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

<span data-ttu-id="059d7-136">Cette commande teste une configuration définie dans un fichier par rapport à un ensemble d’ordinateurs spécifié par le paramètre *ComputerName* .</span><span class="sxs-lookup"><span data-stu-id="059d7-136">This command tests a configuration defined in a file against a set of computers specified by the *ComputerName* parameter.</span></span>

## <span data-ttu-id="059d7-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="059d7-137">PARAMETERS</span></span>

### <span data-ttu-id="059d7-138">-AsJob</span><span class="sxs-lookup"><span data-stu-id="059d7-138">-AsJob</span></span>
<span data-ttu-id="059d7-139">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="059d7-139">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="059d7-140">Si vous spécifiez le paramètre *AsJob* , la commande retourne un objet qui représente le travail, puis affiche l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="059d7-140">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="059d7-141">Vous pouvez continuer à travailler dans la session jusqu’à ce que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="059d7-141">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="059d7-142">La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="059d7-142">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="059d7-143">Pour gérer la tâche, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="059d7-143">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="059d7-144">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="059d7-144">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="059d7-145">Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="059d7-145">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="059d7-146">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="059d7-146">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="059d7-147">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="059d7-147">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="059d7-148">-CimSession</span><span class="sxs-lookup"><span data-stu-id="059d7-148">-CimSession</span></span>
<span data-ttu-id="059d7-149">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="059d7-149">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="059d7-150">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="059d7-150">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="059d7-151">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="059d7-151">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="059d7-152">-ComputerName</span></span>
<span data-ttu-id="059d7-153">Spécifie un tableau de noms d’ordinateurs sur lequel cette applet de commande teste la configuration.</span><span class="sxs-lookup"><span data-stu-id="059d7-153">Specifies an array of computer names on which this cmdlet tests the configuration.</span></span>
<span data-ttu-id="059d7-154">L’applet de commande teste le document de configuration à l’emplacement spécifié par le paramètre *path* à ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="059d7-154">The cmdlet tests the configuration document in the location specified by the *Path* parameter to these computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="059d7-155">-Credential</span></span>
<span data-ttu-id="059d7-156">Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="059d7-156">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="059d7-157">Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="059d7-157">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="059d7-158">Pour plus d'informations, voir `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="059d7-158">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-159">-Detailed</span><span class="sxs-lookup"><span data-stu-id="059d7-159">-Detailed</span></span>
<span data-ttu-id="059d7-160">Indique que cette applet de commande retourne un résultat détaillé de la comparaison du document de configuration avec l’état souhaité des nœuds.</span><span class="sxs-lookup"><span data-stu-id="059d7-160">Indicates that this cmdlet returns a detailed result of comparing the configuration document with the desired state of the nodes.</span></span>
<span data-ttu-id="059d7-161">Le résultat comprend des informations telles que l’état global, les ressources qui sont dans l’état souhaité, les ressources qui ne sont pas dans l’état souhaité et le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="059d7-161">The result includes information such as overall state, resources that are in the desired state, resources that are not in desired state, and computer name.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-162">-Path</span><span class="sxs-lookup"><span data-stu-id="059d7-162">-Path</span></span>
<span data-ttu-id="059d7-163">Spécifie le chemin d’accès d’un dossier qui contient des fichiers de document de configuration.</span><span class="sxs-lookup"><span data-stu-id="059d7-163">Specifies the path of a folder that contains configuration document files.</span></span>
<span data-ttu-id="059d7-164">L’applet de commande teste la configuration par rapport à l’état souhaité des ordinateurs spécifiés par le paramètre *ComputerName* ou *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="059d7-164">The cmdlet tests the configuration against the desired state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-165">-ReferenceConfiguration</span><span class="sxs-lookup"><span data-stu-id="059d7-165">-ReferenceConfiguration</span></span>
<span data-ttu-id="059d7-166">Spécifie le chemin d’accès du fichier du document de configuration.</span><span class="sxs-lookup"><span data-stu-id="059d7-166">Specifies the path of the configuration document file.</span></span>
<span data-ttu-id="059d7-167">Cette applet de commande teste la configuration par rapport à l’état réel des ordinateurs spécifiés par le paramètre *ComputerName* ou *CimSession* .</span><span class="sxs-lookup"><span data-stu-id="059d7-167">This cmdlet tests the configuration against the actual state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-168">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="059d7-168">-ThrottleLimit</span></span>
<span data-ttu-id="059d7-169">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="059d7-169">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="059d7-170">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="059d7-170">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="059d7-171">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="059d7-171">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="059d7-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="059d7-172">CommonParameters</span></span>
<span data-ttu-id="059d7-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="059d7-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="059d7-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="059d7-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="059d7-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="059d7-175">INPUTS</span></span>

## <span data-ttu-id="059d7-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="059d7-176">OUTPUTS</span></span>

## <span data-ttu-id="059d7-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="059d7-177">NOTES</span></span>

## <span data-ttu-id="059d7-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="059d7-178">RELATED LINKS</span></span>

[<span data-ttu-id="059d7-179">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="059d7-179">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="059d7-180">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="059d7-180">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="059d7-181">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="059d7-181">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="059d7-182">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="059d7-182">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="059d7-183">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="059d7-183">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

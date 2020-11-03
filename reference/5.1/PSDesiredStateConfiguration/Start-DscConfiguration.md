---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203930"
---
# <span data-ttu-id="6ad84-103">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-103">Start-DscConfiguration</span></span>

## <span data-ttu-id="6ad84-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6ad84-104">SYNOPSIS</span></span>
<span data-ttu-id="6ad84-105">Applique la configuration à des nœuds.</span><span class="sxs-lookup"><span data-stu-id="6ad84-105">Applies configuration to nodes.</span></span>

## <span data-ttu-id="6ad84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ad84-106">SYNTAX</span></span>

### <span data-ttu-id="6ad84-107">ComputerNameAndPathSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6ad84-107">ComputerNameAndPathSet (Default)</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="6ad84-108">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="6ad84-108">CimSessionAndPathSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ad84-109">ComputerNameAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="6ad84-109">ComputerNameAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ad84-110">CimSessionAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="6ad84-110">CimSessionAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6ad84-111">Description</span><span class="sxs-lookup"><span data-stu-id="6ad84-111">DESCRIPTION</span></span>
<span data-ttu-id="6ad84-112">L'applet de commande **Start-DscConfiguration** applique la configuration à des nœuds.</span><span class="sxs-lookup"><span data-stu-id="6ad84-112">The **Start-DscConfiguration** cmdlet applies configuration to nodes.</span></span>
<span data-ttu-id="6ad84-113">Lorsqu’elle est utilisée avec le paramètre *UseExisting* , la configuration existante sur l’ordinateur cible est appliquée.</span><span class="sxs-lookup"><span data-stu-id="6ad84-113">When used with the *UseExisting* parameter, the existing configuration on the target computer is applied.</span></span>
<span data-ttu-id="6ad84-114">Spécifiez les ordinateurs auxquels vous souhaitez appliquer la configuration en spécifiant des noms d’ordinateur ou à l’aide de sessions Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="6ad84-114">Specify which computers that you want to apply configuration to by specifying computer names or by using Common Information Model (CIM) sessions.</span></span>

<span data-ttu-id="6ad84-115">Par défaut, cette applet de commande crée une tâche et retourne un objet **Job** .</span><span class="sxs-lookup"><span data-stu-id="6ad84-115">By default, this cmdlet creates a job and returns a **Job** object.</span></span>
<span data-ttu-id="6ad84-116">Pour plus d’informations sur les tâches en arrière-plan, tapez `Get-Help about_Jobs` .</span><span class="sxs-lookup"><span data-stu-id="6ad84-116">For more information about background jobs, type `Get-Help about_Jobs`.</span></span>
<span data-ttu-id="6ad84-117">Pour utiliser cette applet de commande de manière interactive, spécifiez le paramètre *Wait* .</span><span class="sxs-lookup"><span data-stu-id="6ad84-117">To use this cmdlet interactively, specify the *Wait* parameter.</span></span>

<span data-ttu-id="6ad84-118">Spécifiez le paramètre *Verbose* pour afficher en détail de ce que fait l'applet de commande lorsqu'elle applique des paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-118">Specify the *Verbose* parameter to see details of what the cmdlet does when it applies configuration settings.</span></span>

## <span data-ttu-id="6ad84-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6ad84-119">EXAMPLES</span></span>

### <span data-ttu-id="6ad84-120">Exemple 1 : appliquer les paramètres de configuration</span><span class="sxs-lookup"><span data-stu-id="6ad84-120">Example 1: Apply configuration settings</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="6ad84-121">Cette commande applique les paramètres de configuration de C:\DSC\Configurations\ à chaque ordinateur possédant des paramètres dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="6ad84-121">This command applies the configuration settings from C:\DSC\Configurations\ to the every computer that has settings in that folder.</span></span>
<span data-ttu-id="6ad84-122">La commande retourne des objets **Job** pour chaque nœud cible visé par le déploiement.</span><span class="sxs-lookup"><span data-stu-id="6ad84-122">The command returns **Job** objects for each target node deployed to.</span></span>

### <span data-ttu-id="6ad84-123">Exemple 2 : appliquer des paramètres de configuration et attendre la fin de la configuration</span><span class="sxs-lookup"><span data-stu-id="6ad84-123">Example 2: Apply configuration settings and wait for configuration to complete</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

<span data-ttu-id="6ad84-124">Cette commande applique la configuration de C:\DSC\Configurations\ à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6ad84-124">This command applies the configuration from C:\DSC\Configurations\ to the local computer.</span></span>
<span data-ttu-id="6ad84-125">La commande retourne des objets **Job** pour chaque nœud cible visé par le déploiement (dans ce cas, uniquement l'ordinateur local).</span><span class="sxs-lookup"><span data-stu-id="6ad84-125">The command returns **Job** objects for each target node deployed to, in this case, just the local computer.</span></span>
<span data-ttu-id="6ad84-126">Cet exemple spécifie le paramètre *Verbose* .</span><span class="sxs-lookup"><span data-stu-id="6ad84-126">This example specifies the *Verbose* parameter.</span></span>
<span data-ttu-id="6ad84-127">Par conséquent, la commande envoie des messages à la console à mesure qu’elle se poursuit.</span><span class="sxs-lookup"><span data-stu-id="6ad84-127">Therefore, the command sends messages to the console as it proceeds.</span></span>
<span data-ttu-id="6ad84-128">La commande comprend le paramètre *Wait* .</span><span class="sxs-lookup"><span data-stu-id="6ad84-128">The command includes the *Wait* parameter.</span></span>
<span data-ttu-id="6ad84-129">Par conséquent, vous ne pouvez pas utiliser la console tant que la commande n’a pas terminé toutes les tâches de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-129">Therefore, you cannot use the console until the command finishes all configuration tasks.</span></span>

### <span data-ttu-id="6ad84-130">Exemple 3 : appliquer des paramètres de configuration à l’aide d’une session CIM</span><span class="sxs-lookup"><span data-stu-id="6ad84-130">Example 3: Apply configuration settings by using a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="6ad84-131">Cet exemple applique les paramètres de configuration à un ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="6ad84-131">This example applies configuration settings to a specified computer.</span></span>
<span data-ttu-id="6ad84-132">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6ad84-132">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="6ad84-133">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6ad84-133">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="6ad84-134">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.</span><span class="sxs-lookup"><span data-stu-id="6ad84-134">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="6ad84-135">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6ad84-135">The command prompts you for a password.</span></span>
<span data-ttu-id="6ad84-136">Pour plus d'informations, voir `Get-Help NewCimSession`.</span><span class="sxs-lookup"><span data-stu-id="6ad84-136">For more information, type `Get-Help NewCimSession`.</span></span>

<span data-ttu-id="6ad84-137">La deuxième commande applique les paramètres de configuration de C:\DSC\Configurations\ aux ordinateurs identifiés par les objets **CimSession** stockés dans la variable $session.</span><span class="sxs-lookup"><span data-stu-id="6ad84-137">The second command applies the configuration settings from C:\DSC\Configurations\ to the computers identified by the **CimSession** objects stored in the $Session variable.</span></span>
<span data-ttu-id="6ad84-138">Dans cet exemple, la variable $Session contient une session CIM uniquement pour l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="6ad84-138">In this example, the $Session variable contains a CIM session only for the computer named Server01.</span></span>
<span data-ttu-id="6ad84-139">La commande applique la configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-139">The command applies the configuration.</span></span>
<span data-ttu-id="6ad84-140">La commande crée des objets **Job** pour chaque ordinateur configuré.</span><span class="sxs-lookup"><span data-stu-id="6ad84-140">The command creates **Job** objects for each configured computer.</span></span>

## <span data-ttu-id="6ad84-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ad84-141">PARAMETERS</span></span>

### <span data-ttu-id="6ad84-142">-CimSession</span><span class="sxs-lookup"><span data-stu-id="6ad84-142">-CimSession</span></span>
<span data-ttu-id="6ad84-143">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="6ad84-143">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="6ad84-144">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="6ad84-144">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="6ad84-145">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6ad84-145">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6ad84-146">-ComputerName</span></span>
<span data-ttu-id="6ad84-147">Spécifie un tableau de noms d'ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="6ad84-147">Specifies an array of computer names.</span></span>
<span data-ttu-id="6ad84-148">Ce paramètre limite les ordinateurs qui ont des documents de configuration dans le paramètre *path* à ceux spécifiés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6ad84-148">This parameter restricts the computers that have configuration documents in the *Path* parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="6ad84-149">-Credential</span></span>
<span data-ttu-id="6ad84-150">Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="6ad84-150">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="6ad84-151">Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="6ad84-151">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="6ad84-152">Pour plus d'informations, voir `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="6ad84-152">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-153">-Force</span><span class="sxs-lookup"><span data-stu-id="6ad84-153">-Force</span></span>
<span data-ttu-id="6ad84-154">Arrête l’opération de configuration en cours d’exécution sur l’ordinateur cible et commence la nouvelle opération de Start-Configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-154">Stops the configuration operation currently running on the target computer and begins the new Start-Configuration operation.</span></span>
<span data-ttu-id="6ad84-155">Si la propriété **RefreshMode** de l’Configuration Manager local est définie sur **pull** , la spécification de ce paramètre le remplace par **Push** .</span><span class="sxs-lookup"><span data-stu-id="6ad84-155">If the **RefreshMode** property of the Local Configuration Manager is set to **Pull** , specifying this parameter changes it to **Push** .</span></span>

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

### <span data-ttu-id="6ad84-156">-JobName</span><span class="sxs-lookup"><span data-stu-id="6ad84-156">-JobName</span></span>
<span data-ttu-id="6ad84-157">Spécifie le nom convivial d'une tâche.</span><span class="sxs-lookup"><span data-stu-id="6ad84-157">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="6ad84-158">Si vous spécifiez ce paramètre, l'applet de commande s'exécute en tant que tâche et retourne un objet **Job** .</span><span class="sxs-lookup"><span data-stu-id="6ad84-158">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="6ad84-159">Par défaut, Windows PowerShell attribue le nom JobN, où N est un entier.</span><span class="sxs-lookup"><span data-stu-id="6ad84-159">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="6ad84-160">Si vous spécifiez le paramètre *Wait* , ne spécifiez pas ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6ad84-160">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-161">-Path</span><span class="sxs-lookup"><span data-stu-id="6ad84-161">-Path</span></span>
<span data-ttu-id="6ad84-162">Spécifie le chemin d'accès d'un dossier qui contient les fichiers de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-162">Specifies a file path of a folder that contains configuration settings files.</span></span>
<span data-ttu-id="6ad84-163">Cette applet de commande publie et applique ces paramètres de configuration aux ordinateurs qui ont des fichiers de paramètres dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="6ad84-163">This cmdlet publishes and applies these configuration settings to computers that have settings files in the specified path.</span></span>
<span data-ttu-id="6ad84-164">Chaque nœud cible doit avoir un fichier de paramètres au format suivant : NetBIOS Name. mof.</span><span class="sxs-lookup"><span data-stu-id="6ad84-164">Each target node must have a settings file of the following format: NetBIOS Name.mof.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-165">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6ad84-165">-ThrottleLimit</span></span>
<span data-ttu-id="6ad84-166">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6ad84-166">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="6ad84-167">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6ad84-167">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="6ad84-168">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6ad84-168">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="6ad84-169">-UseExisting</span><span class="sxs-lookup"><span data-stu-id="6ad84-169">-UseExisting</span></span>
<span data-ttu-id="6ad84-170">Indique que cette applet de commande applique la configuration existante.</span><span class="sxs-lookup"><span data-stu-id="6ad84-170">Indicates that this cmdlet applies the existing configuration.</span></span>
<span data-ttu-id="6ad84-171">La configuration peut exister sur l’ordinateur cible en cas d’adoption à l’aide de **Start-DscConfiguration** ou de la publication à l’aide de l’applet de commande Publish-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-171">The configuration can exist on the target computer by enactment using **Start-DscConfiguration** or by publication using the Publish-DscConfiguration cmdlet.</span></span>

<span data-ttu-id="6ad84-172">Avant de spécifier ce paramètre pour cette applet de commande, passez en revue les informations [contenues dans Nouveautés de Windows PowerShell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span><span class="sxs-lookup"><span data-stu-id="6ad84-172">Before you specify this parameter for this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-173">-Wait</span><span class="sxs-lookup"><span data-stu-id="6ad84-173">-Wait</span></span>
<span data-ttu-id="6ad84-174">Indique que l’applet de commande bloque la console jusqu’à ce qu’elle termine toutes les tâches de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ad84-174">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="6ad84-175">Si vous spécifiez ce paramètre, ne spécifiez pas le paramètre *JobName* .</span><span class="sxs-lookup"><span data-stu-id="6ad84-175">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="6ad84-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6ad84-176">-Confirm</span></span>
<span data-ttu-id="6ad84-177">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6ad84-177">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6ad84-178">-WhatIf</span></span>
<span data-ttu-id="6ad84-179">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6ad84-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6ad84-180">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6ad84-180">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ad84-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ad84-181">CommonParameters</span></span>
<span data-ttu-id="6ad84-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ad84-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ad84-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6ad84-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ad84-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6ad84-184">INPUTS</span></span>

## <span data-ttu-id="6ad84-185">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6ad84-185">OUTPUTS</span></span>

## <span data-ttu-id="6ad84-186">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6ad84-186">NOTES</span></span>

## <span data-ttu-id="6ad84-187">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6ad84-187">RELATED LINKS</span></span>

[<span data-ttu-id="6ad84-188">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ad84-188">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="6ad84-189">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-189">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="6ad84-190">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6ad84-190">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="6ad84-191">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-191">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="6ad84-192">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-192">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="6ad84-193">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-193">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="6ad84-194">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ad84-194">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

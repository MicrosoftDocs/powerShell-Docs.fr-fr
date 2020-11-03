---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203073"
---
# <span data-ttu-id="d07e4-103">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-103">Update-DscConfiguration</span></span>

## <span data-ttu-id="d07e4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d07e4-104">SYNOPSIS</span></span>
<span data-ttu-id="d07e4-105">Recherche une configuration mise à jour dans le serveur collecteur et l’applique.</span><span class="sxs-lookup"><span data-stu-id="d07e4-105">Checks the pull server for an updated configuration and applies it.</span></span>

## <span data-ttu-id="d07e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d07e4-106">SYNTAX</span></span>

### <span data-ttu-id="d07e4-107">ComputerNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d07e4-107">ComputerNameSet (Default)</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d07e4-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="d07e4-108">CimSessionSet</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d07e4-109">Description</span><span class="sxs-lookup"><span data-stu-id="d07e4-109">DESCRIPTION</span></span>
<span data-ttu-id="d07e4-110">L' `Update-DscConfiguration` applet de commande se connecte à un serveur collecteur, télécharge la configuration si elle diffère de la valeur actuelle sur le nœud, puis applique la configuration à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d07e4-110">The `Update-DscConfiguration` cmdlet connects to a pull server, downloads the configuration if it differs from what is current on the node, and then applies the configuration to the computer.</span></span>

<span data-ttu-id="d07e4-111">Cette applet de commande est disponible uniquement dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8,1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) à partir de la bibliothèque de support Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d07e4-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="d07e4-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d07e4-112">EXAMPLES</span></span>

### <span data-ttu-id="d07e4-113">Exemple 1 : mettre à jour une configuration</span><span class="sxs-lookup"><span data-stu-id="d07e4-113">Example 1: Update a configuration</span></span>

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

<span data-ttu-id="d07e4-114">Après avoir exécuté cette commande, le serveur se connecte au service d’extraction inscrit, télécharge la dernière configuration attribuée, puis l’applique.</span><span class="sxs-lookup"><span data-stu-id="d07e4-114">After running this command, the server will connect to the registered pull service, download the latest assigned configuration, and then apply it.</span></span>
<span data-ttu-id="d07e4-115">Les paramètres-Wait et-verbose sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="d07e4-115">The -Wait and -Verbose parameters are optional.</span></span>
<span data-ttu-id="d07e4-116">Lorsque vous travaillez de manière interactive, ces paramètres regroupés activent les commentaires en temps réel sur la progression et la réussite ou l’échec lors de l’application de la configuration.</span><span class="sxs-lookup"><span data-stu-id="d07e4-116">When working interactively, these parameters combined enable real-time feedback about progress and success or failure when applying the configuration.</span></span>

### <span data-ttu-id="d07e4-117">Exemple 2 : mettre à jour une configuration en se connectant via une session CIM</span><span class="sxs-lookup"><span data-stu-id="d07e4-117">Example 2: Update a configuration by connecting over a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

<span data-ttu-id="d07e4-118">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.</span><span class="sxs-lookup"><span data-stu-id="d07e4-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="d07e4-119">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d07e4-119">The command prompts you for a password.</span></span>
<span data-ttu-id="d07e4-120">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="d07e4-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="d07e4-121">La deuxième commande met à jour l’ordinateur spécifié dans le **CimSession** stocké dans $session.</span><span class="sxs-lookup"><span data-stu-id="d07e4-121">The second command updates the computer specified in the **CimSession** stored in $Session.</span></span>
<span data-ttu-id="d07e4-122">La commande spécifie le paramètre *Wait* .</span><span class="sxs-lookup"><span data-stu-id="d07e4-122">The command specifies the *Wait* parameter.</span></span>
<span data-ttu-id="d07e4-123">La console n’accepte pas de commandes supplémentaires tant que la commande en cours n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="d07e4-123">The console does not accept additional commands until the current command finishes.</span></span>

## <span data-ttu-id="d07e4-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d07e4-124">PARAMETERS</span></span>

### <span data-ttu-id="d07e4-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d07e4-125">-CimSession</span></span>
<span data-ttu-id="d07e4-126">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d07e4-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="d07e4-127">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="d07e4-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="d07e4-128">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d07e4-128">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d07e4-129">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d07e4-129">-ComputerName</span></span>
<span data-ttu-id="d07e4-130">Spécifie un tableau de noms d'ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d07e4-130">Specifies an array of computer names.</span></span>
<span data-ttu-id="d07e4-131">L’applet de commande applique les paramètres de configuration aux ordinateurs que ce paramètre spécifie.</span><span class="sxs-lookup"><span data-stu-id="d07e4-131">The cmdlet applies the configuration settings to the computers that this parameter specifies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d07e4-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="d07e4-132">-Credential</span></span>
<span data-ttu-id="d07e4-133">Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="d07e4-133">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="d07e4-134">Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="d07e4-134">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="d07e4-135">Pour plus d'informations, voir `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="d07e4-135">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d07e4-136">-JobName</span><span class="sxs-lookup"><span data-stu-id="d07e4-136">-JobName</span></span>
<span data-ttu-id="d07e4-137">Spécifie le nom convivial d'une tâche.</span><span class="sxs-lookup"><span data-stu-id="d07e4-137">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="d07e4-138">Si vous spécifiez ce paramètre, l'applet de commande s'exécute en tant que tâche et retourne un objet **Job** .</span><span class="sxs-lookup"><span data-stu-id="d07e4-138">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="d07e4-139">Par défaut, Windows PowerShell attribue le nom JobN, où N est un entier.</span><span class="sxs-lookup"><span data-stu-id="d07e4-139">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="d07e4-140">Si vous spécifiez le paramètre *Wait* , ne spécifiez pas ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d07e4-140">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

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

### <span data-ttu-id="d07e4-141">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d07e4-141">-ThrottleLimit</span></span>
<span data-ttu-id="d07e4-142">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d07e4-142">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="d07e4-143">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d07e4-143">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="d07e4-144">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d07e4-144">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="d07e4-145">-Wait</span><span class="sxs-lookup"><span data-stu-id="d07e4-145">-Wait</span></span>
<span data-ttu-id="d07e4-146">Indique que l’applet de commande bloque la console jusqu’à ce qu’elle termine toutes les tâches de configuration.</span><span class="sxs-lookup"><span data-stu-id="d07e4-146">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="d07e4-147">Si vous spécifiez ce paramètre, ne spécifiez pas le paramètre *JobName* .</span><span class="sxs-lookup"><span data-stu-id="d07e4-147">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="d07e4-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d07e4-148">-Confirm</span></span>
<span data-ttu-id="d07e4-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d07e4-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d07e4-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d07e4-150">-WhatIf</span></span>
<span data-ttu-id="d07e4-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d07e4-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d07e4-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d07e4-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d07e4-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d07e4-153">CommonParameters</span></span>
<span data-ttu-id="d07e4-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d07e4-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d07e4-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d07e4-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d07e4-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d07e4-156">INPUTS</span></span>

## <span data-ttu-id="d07e4-157">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d07e4-157">OUTPUTS</span></span>

## <span data-ttu-id="d07e4-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d07e4-158">NOTES</span></span>

## <span data-ttu-id="d07e4-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d07e4-159">RELATED LINKS</span></span>

[<span data-ttu-id="d07e4-160">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d07e4-160">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d07e4-161">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-161">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="d07e4-162">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d07e4-162">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="d07e4-163">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-163">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="d07e4-164">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-164">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="d07e4-165">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-165">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="d07e4-166">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d07e4-166">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

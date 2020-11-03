---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203086"
---
# <span data-ttu-id="2c25e-103">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-103">Stop-DscConfiguration</span></span>

## <span data-ttu-id="2c25e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2c25e-104">SYNOPSIS</span></span>
<span data-ttu-id="2c25e-105">Arrête une tâche de configuration en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c25e-105">Stops a configuration job that is running.</span></span>

## <span data-ttu-id="2c25e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c25e-106">SYNTAX</span></span>

### <span data-ttu-id="2c25e-107">Tous</span><span class="sxs-lookup"><span data-stu-id="2c25e-107">All</span></span>

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2c25e-108">Description</span><span class="sxs-lookup"><span data-stu-id="2c25e-108">DESCRIPTION</span></span>

<span data-ttu-id="2c25e-109">L' `Stop-DscConfiguration` applet de commande arrête une tâche de configuration en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c25e-109">The `Stop-DscConfiguration` cmdlet stops a configuration job that is running.</span></span> <span data-ttu-id="2c25e-110">Spécifiez les ordinateurs auxquels cette applet de commande s’applique en utilisant des sessions Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="2c25e-110">Specify which computers this cmdlet applies to by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="2c25e-111">Si aucune tâche de configuration n’est en cours d’exécution, cette cmdlet renvoie un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="2c25e-111">If there's no configuration job running, this cmdlet returns a warning message.</span></span>

<span data-ttu-id="2c25e-112">`Stop-DscConfiguration` est uniquement disponible dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8,1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) à partir de la bibliothèque de support Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c25e-112">`Stop-DscConfiguration` is only available as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span> <span data-ttu-id="2c25e-113">Avant d’utiliser cette applet de commande, passez en revue les informations [contenues dans Nouveautés de Windows PowerShell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span><span class="sxs-lookup"><span data-stu-id="2c25e-113">Before you use this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span></span>

## <span data-ttu-id="2c25e-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2c25e-114">EXAMPLES</span></span>

### <span data-ttu-id="2c25e-115">Exemple 1 : arrêter une tâche de configuration</span><span class="sxs-lookup"><span data-stu-id="2c25e-115">Example 1: Stop a configuration job</span></span>

<span data-ttu-id="2c25e-116">Dans cet exemple, une session CIM est créée à l’aide de l’applet de commande `New-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="2c25e-116">In this example, a CIM session is created using the `New-CimSession` cmdlet.</span></span> <span data-ttu-id="2c25e-117">L’objet **CimSession** est utilisé pour arrêter un travail de configuration en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c25e-117">The **CimSession** object is used to stop a running configuration job.</span></span>

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

<span data-ttu-id="2c25e-118">`New-CimSession` utilise le paramètre **ComputerName** pour spécifier l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="2c25e-118">`New-CimSession` uses the **ComputerName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="2c25e-119">Le paramètre Credential spécifie le compte **d'** utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2c25e-119">The **Credential** parameter specifies the user account.</span></span> <span data-ttu-id="2c25e-120">L’objet **CimSession** est stocké dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="2c25e-120">The **CimSession** object is stored in the `$Session` variable.</span></span> <span data-ttu-id="2c25e-121">Lorsque la commande est exécutée, vous êtes invité à entrer le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2c25e-121">When the command is run, you're prompted for the user account's password.</span></span>

<span data-ttu-id="2c25e-122">`Stop-DscConfiguration` utilise le paramètre **CimSession** et l’objet stocké dans `$Session` pour arrêter la tâche de configuration.</span><span class="sxs-lookup"><span data-stu-id="2c25e-122">`Stop-DscConfiguration` uses the **CimSession** parameter and the object stored in `$Session` to stop the configuration job.</span></span>

## <span data-ttu-id="2c25e-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2c25e-123">PARAMETERS</span></span>

### <span data-ttu-id="2c25e-124">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2c25e-124">-AsJob</span></span>

<span data-ttu-id="2c25e-125">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2c25e-125">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="2c25e-126">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2c25e-126">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="2c25e-127">Pour utiliser le paramètre **AsJob** , les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="2c25e-127">To use the **AsJob** parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="2c25e-128">Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="2c25e-128">On Windows Vista and later versions of the Windows operating system, you must open PowerShell with the **Run as administrator** option.</span></span> <span data-ttu-id="2c25e-129">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c25e-129">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c25e-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2c25e-130">-CimSession</span></span>

<span data-ttu-id="2c25e-131">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2c25e-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="2c25e-132">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie de `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="2c25e-132">Enter a computer name or a session object, such as the output from `New-CimSession` or `Get-CimSession`.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c25e-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2c25e-133">-Confirm</span></span>

<span data-ttu-id="2c25e-134">`Stop-DscConfiguration` ne prend pas en charge le paramètre **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="2c25e-134">`Stop-DscConfiguration` doesn't support the **Confirm** parameter.</span></span> <span data-ttu-id="2c25e-135">Si le paramètre **Confirm** est utilisé, une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2c25e-135">If the **Confirm** parameter is used, an error is displayed.</span></span>

<span data-ttu-id="2c25e-136">Pour les applets de commande PowerShell qui prennent en charge la vérification, l’utilisation du paramètre vous invite à **confirmer** l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="2c25e-136">For PowerShell cmdlets that support **Confirm** , using the parameter prompts you for verification before a command is run.</span></span>

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

### <span data-ttu-id="2c25e-137">-Force</span><span class="sxs-lookup"><span data-stu-id="2c25e-137">-Force</span></span>

<span data-ttu-id="2c25e-138">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2c25e-138">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c25e-139">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2c25e-139">-ThrottleLimit</span></span>

<span data-ttu-id="2c25e-140">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2c25e-140">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

<span data-ttu-id="2c25e-141">Si ce paramètre est omis ou si la valeur `0` est entrée, PowerShell calcule une limite de limitation optimale en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2c25e-141">If this parameter is omitted or a value of `0` is entered, PowerShell calculates an optimum throttle limit based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="2c25e-142">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2c25e-142">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2c25e-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2c25e-143">-WhatIf</span></span>

<span data-ttu-id="2c25e-144">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2c25e-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2c25e-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2c25e-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2c25e-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2c25e-146">CommonParameters</span></span>

<span data-ttu-id="2c25e-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2c25e-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2c25e-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2c25e-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2c25e-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2c25e-149">INPUTS</span></span>

### <span data-ttu-id="2c25e-150">Aucun</span><span class="sxs-lookup"><span data-stu-id="2c25e-150">None</span></span>

## <span data-ttu-id="2c25e-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2c25e-151">OUTPUTS</span></span>

### <span data-ttu-id="2c25e-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="2c25e-152">None</span></span>

## <span data-ttu-id="2c25e-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2c25e-153">NOTES</span></span>

## <span data-ttu-id="2c25e-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2c25e-154">RELATED LINKS</span></span>

[<span data-ttu-id="2c25e-155">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="2c25e-155">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="2c25e-156">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-156">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="2c25e-157">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2c25e-157">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2c25e-158">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="2c25e-158">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="2c25e-159">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-159">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2c25e-160">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-160">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2c25e-161">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-161">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="2c25e-162">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c25e-162">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

[<span data-ttu-id="2c25e-163">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c25e-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

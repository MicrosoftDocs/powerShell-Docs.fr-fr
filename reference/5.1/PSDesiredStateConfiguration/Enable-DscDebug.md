---
external help file: Enable-DscDebug.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/enable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-DscDebug
ms.openlocfilehash: 136481c5a1945c3d5cbd1ca7fc8ce5f580c39b0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203966"
---
# <span data-ttu-id="d1397-103">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d1397-103">Enable-DscDebug</span></span>

## <span data-ttu-id="d1397-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d1397-104">SYNOPSIS</span></span>
<span data-ttu-id="d1397-105">Démarre le débogage de toutes les ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="d1397-105">Starts debugging of all DSC resources.</span></span>

## <span data-ttu-id="d1397-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d1397-106">SYNTAX</span></span>

```
Enable-DscDebug [-BreakAll] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="d1397-107">Description</span><span class="sxs-lookup"><span data-stu-id="d1397-107">DESCRIPTION</span></span>
<span data-ttu-id="d1397-108">L’applet de commande **Enable-DscDebug** active le débogage des ressources DSC (Desired State Configuration) Windows PowerShell par le moteur DSC, également appelé Configuration Manager local (LCM).</span><span class="sxs-lookup"><span data-stu-id="d1397-108">The **Enable-DscDebug** cmdlet enables Windows PowerShell Desired State Configuration (DSC) resource debugging by the DSC engine, which is also known as the Local Configuration Manager (LCM).</span></span>
<span data-ttu-id="d1397-109">Par défaut, toutes les instances de ressource s’arrêtent dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="d1397-109">By default, all resource instances break into the debugger.</span></span>

## <span data-ttu-id="d1397-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d1397-110">EXAMPLES</span></span>

### <span data-ttu-id="d1397-111">Exemple 1 : démarrer le débogage</span><span class="sxs-lookup"><span data-stu-id="d1397-111">Example 1: Start debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll
```

<span data-ttu-id="d1397-112">Cette commande indique au moteur DSC ou au LCM de démarrer le débogage des ressources.</span><span class="sxs-lookup"><span data-stu-id="d1397-112">This command indicates to the DSC engine or LCM to start resource debugging.</span></span>
<span data-ttu-id="d1397-113">Lors de la prochaine exécution de la configuration, le processus entre dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="d1397-113">The next time the configuration is run, the process enters the debugger.</span></span>

### <span data-ttu-id="d1397-114">Exemple 2 : démarrer le débogage à distance</span><span class="sxs-lookup"><span data-stu-id="d1397-114">Example 2: Start remote debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll -CimSession DeploymentServer
```

<span data-ttu-id="d1397-115">Cette commande indique au moteur DSC de l’ordinateur distant de démarrer le débogage des ressources.</span><span class="sxs-lookup"><span data-stu-id="d1397-115">This command indicates to the DSC engine of the remote computer to start resource debugging.</span></span>

## <span data-ttu-id="d1397-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d1397-116">PARAMETERS</span></span>

### <span data-ttu-id="d1397-117">-AsJob</span><span class="sxs-lookup"><span data-stu-id="d1397-117">-AsJob</span></span>
<span data-ttu-id="d1397-118">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d1397-118">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="d1397-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="d1397-119">-BreakAll</span></span>
<span data-ttu-id="d1397-120">Indique que toutes les ressources entrent dans le débogueur lors de l’exécution d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="d1397-120">Indicates that all resources enter the debugger when a configuration runs.</span></span>

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

### <span data-ttu-id="d1397-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d1397-121">-CimSession</span></span>
<span data-ttu-id="d1397-122">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d1397-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="d1397-123">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="d1397-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="d1397-124">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d1397-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="d1397-125">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d1397-125">-ThrottleLimit</span></span>
<span data-ttu-id="d1397-126">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1397-126">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="d1397-127">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d1397-127">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="d1397-128">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d1397-128">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="d1397-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d1397-129">-Confirm</span></span>
<span data-ttu-id="d1397-130">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1397-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d1397-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d1397-131">-WhatIf</span></span>
<span data-ttu-id="d1397-132">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1397-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d1397-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d1397-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d1397-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1397-134">CommonParameters</span></span>
<span data-ttu-id="d1397-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1397-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1397-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d1397-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1397-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d1397-137">INPUTS</span></span>

## <span data-ttu-id="d1397-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d1397-138">OUTPUTS</span></span>

## <span data-ttu-id="d1397-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d1397-139">NOTES</span></span>

## <span data-ttu-id="d1397-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d1397-140">RELATED LINKS</span></span>

[<span data-ttu-id="d1397-141">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1397-141">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d1397-142">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d1397-142">Disable-DscDebug</span></span>](Disable-DscDebug.md)

[<span data-ttu-id="d1397-143">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1397-143">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="d1397-144">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d1397-144">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="d1397-145">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1397-145">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="d1397-146">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1397-146">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="d1397-147">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1397-147">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

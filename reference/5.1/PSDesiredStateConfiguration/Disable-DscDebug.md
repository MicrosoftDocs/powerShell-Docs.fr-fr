---
external help file: Disable-DscDebug.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/disable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-DscDebug
ms.openlocfilehash: fdaba8358772f559a33117c796a923d774b009cb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203962"
---
# <span data-ttu-id="2c684-103">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="2c684-103">Disable-DscDebug</span></span>

## <span data-ttu-id="2c684-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2c684-104">SYNOPSIS</span></span>
<span data-ttu-id="2c684-105">Arrête le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="2c684-105">Stops debugging of DSC resources.</span></span>

## <span data-ttu-id="2c684-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c684-106">SYNTAX</span></span>

```
Disable-DscDebug [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2c684-107">Description</span><span class="sxs-lookup"><span data-stu-id="2c684-107">DESCRIPTION</span></span>
<span data-ttu-id="2c684-108">L’applet **de commande Disable-DscDebug** demande que le moteur de configuration d’état souhaité (DSC) Windows PowerShell arrête le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="2c684-108">The **Disable-DscDebug** cmdlet requests that the Windows PowerShell Desired State Configuration (DSC) engine stop debugging of DSC resources.</span></span>
<span data-ttu-id="2c684-109">Cette applet de commande n’a aucun effet si le moteur DSC n’est pas actuellement en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="2c684-109">This cmdlet has no effect if the DSC engine is not currently in debugging mode.</span></span>

## <span data-ttu-id="2c684-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2c684-110">EXAMPLES</span></span>

### <span data-ttu-id="2c684-111">Exemple 1 : arrêter le débogage des ressources</span><span class="sxs-lookup"><span data-stu-id="2c684-111">Example 1: Stop resource debugging</span></span>

```
PS C:\> Disable-DscDebug
```

<span data-ttu-id="2c684-112">Cette commande indique au moteur DSC sur le Configuration Manager local (LCM) d’arrêter le débogage des ressources.</span><span class="sxs-lookup"><span data-stu-id="2c684-112">This command indicates to the DSC engine on the Local Configuration Manager (LCM) to stop resource debugging.</span></span>

### <span data-ttu-id="2c684-113">Exemple 2 : vérifier l’état du moteur et arrêter le débogage</span><span class="sxs-lookup"><span data-stu-id="2c684-113">Example 2: Check the engine state and stop debugging</span></span>

```
PS C:\> if((Get-DscLocalConfigurationManager).DebugMode -like '*Break*'){Disable-DscDebug}
```

<span data-ttu-id="2c684-114">Cette commande vérifie l’état du moteur DSC et arrête le débogage des ressources uniquement s’il est déjà en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="2c684-114">This command checks the DSC engine state, and stops resource debugging only if it is already in debugging mode</span></span>

## <span data-ttu-id="2c684-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2c684-115">PARAMETERS</span></span>

### <span data-ttu-id="2c684-116">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2c684-116">-AsJob</span></span>
<span data-ttu-id="2c684-117">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2c684-117">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2c684-118">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2c684-118">-CimSession</span></span>
<span data-ttu-id="2c684-119">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2c684-119">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2c684-120">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="2c684-120">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2c684-121">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2c684-121">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="2c684-122">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2c684-122">-ThrottleLimit</span></span>
<span data-ttu-id="2c684-123">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2c684-123">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2c684-124">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2c684-124">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2c684-125">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2c684-125">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2c684-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2c684-126">-Confirm</span></span>
<span data-ttu-id="2c684-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2c684-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2c684-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2c684-128">-WhatIf</span></span>
<span data-ttu-id="2c684-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2c684-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2c684-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2c684-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2c684-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2c684-131">CommonParameters</span></span>
<span data-ttu-id="2c684-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2c684-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2c684-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2c684-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2c684-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2c684-134">INPUTS</span></span>

## <span data-ttu-id="2c684-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2c684-135">OUTPUTS</span></span>

## <span data-ttu-id="2c684-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2c684-136">NOTES</span></span>

## <span data-ttu-id="2c684-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2c684-137">RELATED LINKS</span></span>

[<span data-ttu-id="2c684-138">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c684-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2c684-139">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="2c684-139">Enable-DscDebug</span></span>](Enable-DscDebug.md)

[<span data-ttu-id="2c684-140">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2c684-140">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2c684-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2c684-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="2c684-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c684-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2c684-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c684-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2c684-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c684-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

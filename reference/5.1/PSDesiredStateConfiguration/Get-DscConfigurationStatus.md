---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203969"
---
# <span data-ttu-id="2ce69-103">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2ce69-103">Get-DscConfigurationStatus</span></span>

## <span data-ttu-id="2ce69-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2ce69-104">SYNOPSIS</span></span>
<span data-ttu-id="2ce69-105">Récupère des données sur les exécutions de configuration terminées.</span><span class="sxs-lookup"><span data-stu-id="2ce69-105">Retrieves data about completed configuration runs.</span></span>

## <span data-ttu-id="2ce69-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ce69-106">SYNTAX</span></span>

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="2ce69-107">Description</span><span class="sxs-lookup"><span data-stu-id="2ce69-107">DESCRIPTION</span></span>
<span data-ttu-id="2ce69-108">L’applet de commande **obtenir-DscConfigurationStatus** récupère des informations détaillées sur les exécutions de la configuration terminée sur le système.</span><span class="sxs-lookup"><span data-stu-id="2ce69-108">The **Get-DscConfigurationStatus** cmdlet retrieves detailed information about completed configuration runs on the system.</span></span>
<span data-ttu-id="2ce69-109">Par défaut, elle retourne les informations relatives à la dernière exécution de la configuration.</span><span class="sxs-lookup"><span data-stu-id="2ce69-109">By default, it returns the information about the last configuration run.</span></span>
<span data-ttu-id="2ce69-110">Cette applet de commande est utile pour rechercher des informations historiques sur les exécutions de configuration, telles que le moment où les configurations ont été exécutées, l’état des exécutions, le nombre de ressources dans les configurations et les ressources qui ont réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="2ce69-110">This cmdlet is useful for finding historical information about configuration runs, such as when the configurations were run, the status of the runs, the number of resources in the configurations, and which resources succeeded or failed.</span></span>

## <span data-ttu-id="2ce69-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2ce69-111">EXAMPLES</span></span>

### <span data-ttu-id="2ce69-112">Exemple 1 : récupérer des informations sur la dernière exécution de la configuration</span><span class="sxs-lookup"><span data-stu-id="2ce69-112">Example 1: Get information on the last configuration run</span></span>

```
PS C:\> Get-DscConfigurationStatus
```

<span data-ttu-id="2ce69-113">Cette commande obtient des informations sur la dernière exécution de la configuration.</span><span class="sxs-lookup"><span data-stu-id="2ce69-113">This command gets information on the last configuration run.</span></span>

### <span data-ttu-id="2ce69-114">Exemple 2 : récupérer des informations sur toutes les configurations</span><span class="sxs-lookup"><span data-stu-id="2ce69-114">Example 2: Get information on all configurations</span></span>

```
PS C:\> Get-DscConfigurationStatus -All
```

<span data-ttu-id="2ce69-115">Cette commande obtient des informations sur toutes les configurations qui ont été exécutées sur le système, y compris la vérification de cohérence de la configuration d’état souhaité (DSC) Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce69-115">This command gets information about all the configurations that were run on the system, including the Windows PowerShell Desired State Configuration (DSC) consistency check.</span></span>

### <span data-ttu-id="2ce69-116">Exemple 3 : obtenir des informations sur la configuration exécutée sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="2ce69-116">Example 3: Get information on the configuration run on a remote computer</span></span>

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

<span data-ttu-id="2ce69-117">Cette commande obtient les détails de l’exécution de la configuration de l’ordinateur distant nommé SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="2ce69-117">This command gets the configuration run details of the remote computer named Server01.</span></span>
<span data-ttu-id="2ce69-118">Le transport WSMan est utilisé pour se connecter à l’ordinateur distant et nécessite que l’utilisateur qui se connecte soit un administrateur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2ce69-118">This uses the WSMan transport to connect to the remote computer and requires that the connecting user be an administrator on the remote computer.</span></span>

## <span data-ttu-id="2ce69-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2ce69-119">PARAMETERS</span></span>

### <span data-ttu-id="2ce69-120">-All</span><span class="sxs-lookup"><span data-stu-id="2ce69-120">-All</span></span>
<span data-ttu-id="2ce69-121">Indique que cette applet de commande récupère des informations sur toutes les exécutions de configuration sur l’ordinateur, y compris l’application de configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="2ce69-121">Indicates that this cmdlet retrieves information about all the configuration runs on the computer, including the configuration application and the consistency check.</span></span>

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

### <span data-ttu-id="2ce69-122">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2ce69-122">-AsJob</span></span>
<span data-ttu-id="2ce69-123">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2ce69-123">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2ce69-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2ce69-124">-CimSession</span></span>
<span data-ttu-id="2ce69-125">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2ce69-125">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2ce69-126">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="2ce69-126">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2ce69-127">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2ce69-127">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="2ce69-128">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2ce69-128">-ThrottleLimit</span></span>
<span data-ttu-id="2ce69-129">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2ce69-129">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2ce69-130">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ce69-130">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2ce69-131">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ce69-131">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2ce69-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ce69-132">CommonParameters</span></span>
<span data-ttu-id="2ce69-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2ce69-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ce69-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2ce69-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ce69-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2ce69-135">INPUTS</span></span>

## <span data-ttu-id="2ce69-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2ce69-136">OUTPUTS</span></span>

## <span data-ttu-id="2ce69-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2ce69-137">NOTES</span></span>

## <span data-ttu-id="2ce69-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2ce69-138">RELATED LINKS</span></span>

[<span data-ttu-id="2ce69-139">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ce69-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2ce69-140">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ce69-140">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="2ce69-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2ce69-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="2ce69-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ce69-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2ce69-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ce69-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2ce69-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ce69-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

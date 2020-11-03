---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203965"
---
# <span data-ttu-id="2cdcb-103">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cdcb-103">Get-DscConfiguration</span></span>

## <span data-ttu-id="2cdcb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2cdcb-104">SYNOPSIS</span></span>
<span data-ttu-id="2cdcb-105">Obtient la configuration actuelle des nœuds.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-105">Gets the current configuration of the nodes.</span></span>

## <span data-ttu-id="2cdcb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2cdcb-106">SYNTAX</span></span>

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="2cdcb-107">Description</span><span class="sxs-lookup"><span data-stu-id="2cdcb-107">DESCRIPTION</span></span>
<span data-ttu-id="2cdcb-108">L’applet de commande **obtenir-DscConfiguration** obtient la configuration actuelle des nœuds, si la configuration existe.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-108">The **Get-DscConfiguration** cmdlet gets the current configuration of the nodes, if the configuration exists.</span></span>
<span data-ttu-id="2cdcb-109">Spécifiez les ordinateurs à l'aide de sessions CIM (Common Information Model).</span><span class="sxs-lookup"><span data-stu-id="2cdcb-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="2cdcb-110">Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande obtient la configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-110">If you do not specify a target computer, the cmdlet gets the configuration from the local computer.</span></span>

## <span data-ttu-id="2cdcb-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2cdcb-111">EXAMPLES</span></span>

### <span data-ttu-id="2cdcb-112">Exemple 1 : obtenir la configuration de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2cdcb-112">Example 1: Get the configuration for the local computer</span></span>

```
PS C:\> Get-DscConfiguration
```

<span data-ttu-id="2cdcb-113">Cette commande obtient l’état actuel de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-113">This command gets the current state for the local computer.</span></span>

### <span data-ttu-id="2cdcb-114">Exemple 2 : obtenir la configuration d’un ordinateur spécifié</span><span class="sxs-lookup"><span data-stu-id="2cdcb-114">Example 2: Get the configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

<span data-ttu-id="2cdcb-115">Cet exemple obtient l’état actuel à partir d’un ordinateur spécifié par une session CIM.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-115">This example gets the current state from a computer specified by a CIM session.</span></span>
<span data-ttu-id="2cdcb-116">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-116">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="2cdcb-117">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-117">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="2cdcb-118">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable **$Session** .</span><span class="sxs-lookup"><span data-stu-id="2cdcb-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the **$Session** variable.</span></span>
<span data-ttu-id="2cdcb-119">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-119">The command prompts you for a password.</span></span>
<span data-ttu-id="2cdcb-120">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="2cdcb-121">La deuxième commande obtient la configuration actuelle des ordinateurs identifiés par les objets **CimSession** stockés dans la variable **$Session** (dans ce cas, l'ordinateur nommé Server01).</span><span class="sxs-lookup"><span data-stu-id="2cdcb-121">The second command gets the current configuration for the computers identified by the **CimSession** objects stored in the **$Session** variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="2cdcb-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2cdcb-122">PARAMETERS</span></span>

### <span data-ttu-id="2cdcb-123">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2cdcb-123">-AsJob</span></span>
<span data-ttu-id="2cdcb-124">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-124">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2cdcb-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2cdcb-125">-CimSession</span></span>
<span data-ttu-id="2cdcb-126">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2cdcb-127">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="2cdcb-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2cdcb-128">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="2cdcb-129">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2cdcb-129">-ThrottleLimit</span></span>
<span data-ttu-id="2cdcb-130">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-130">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2cdcb-131">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-131">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2cdcb-132">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-132">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2cdcb-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2cdcb-133">CommonParameters</span></span>
<span data-ttu-id="2cdcb-134">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2cdcb-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2cdcb-135">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2cdcb-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2cdcb-136">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2cdcb-136">INPUTS</span></span>

## <span data-ttu-id="2cdcb-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2cdcb-137">OUTPUTS</span></span>

## <span data-ttu-id="2cdcb-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2cdcb-138">NOTES</span></span>

## <span data-ttu-id="2cdcb-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2cdcb-139">RELATED LINKS</span></span>

[<span data-ttu-id="2cdcb-140">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2cdcb-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2cdcb-141">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2cdcb-141">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2cdcb-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cdcb-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2cdcb-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cdcb-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2cdcb-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cdcb-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

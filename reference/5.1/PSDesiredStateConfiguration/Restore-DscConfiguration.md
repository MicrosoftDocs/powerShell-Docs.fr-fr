---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203934"
---
# <span data-ttu-id="2dc25-103">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2dc25-103">Restore-DscConfiguration</span></span>

## <span data-ttu-id="2dc25-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2dc25-104">SYNOPSIS</span></span>
<span data-ttu-id="2dc25-105">Réapplique la configuration précédente pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="2dc25-105">Reapplies the previous configuration for the node.</span></span>

## <span data-ttu-id="2dc25-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2dc25-106">SYNTAX</span></span>

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2dc25-107">Description</span><span class="sxs-lookup"><span data-stu-id="2dc25-107">DESCRIPTION</span></span>
<span data-ttu-id="2dc25-108">L’applet de commande **Restore-DscConfiguration** réapplique la configuration précédente pour le nœud, si une configuration précédente existe.</span><span class="sxs-lookup"><span data-stu-id="2dc25-108">The **Restore-DscConfiguration** cmdlet reapplies the previous configuration for the node, if a previous configuration exists.</span></span>
<span data-ttu-id="2dc25-109">Spécifiez les ordinateurs à l'aide de sessions CIM (Common Information Model).</span><span class="sxs-lookup"><span data-stu-id="2dc25-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="2dc25-110">Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande restaure la configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2dc25-110">If you do not specify a target computer, the cmdlet restores the configuration of the local computer.</span></span>
<span data-ttu-id="2dc25-111">S’il n’existe pas de configuration précédente pour un nœud particulier, cette applet de commande retourne un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2dc25-111">If there is no previous configuration for a particular node, this cmdlet returns an error message.</span></span>

<span data-ttu-id="2dc25-112">Cette applet de commande ne prend pas en charge le paramètre **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="2dc25-112">This cmdlet does not support the **Confirm** parameter.</span></span>

## <span data-ttu-id="2dc25-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2dc25-113">EXAMPLES</span></span>

### <span data-ttu-id="2dc25-114">Exemple 1 : restaurer la configuration de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2dc25-114">Example 1: Restore the configuration for the local computer</span></span>

```
PS C:\> Restore-DscConfiguration
```

<span data-ttu-id="2dc25-115">Cette commande restaure la configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2dc25-115">This command restores the configuration for the local computer.</span></span>

### <span data-ttu-id="2dc25-116">Exemple 2 : restaurer la configuration d’un ordinateur spécifié</span><span class="sxs-lookup"><span data-stu-id="2dc25-116">Example 2: Restore configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

<span data-ttu-id="2dc25-117">Cet exemple restaure la configuration d'un ordinateur spécifié par une session CIM.</span><span class="sxs-lookup"><span data-stu-id="2dc25-117">This example restores configuration on a computer specified by a CIM session.</span></span>
<span data-ttu-id="2dc25-118">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2dc25-118">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="2dc25-119">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2dc25-119">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="2dc25-120">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.</span><span class="sxs-lookup"><span data-stu-id="2dc25-120">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="2dc25-121">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2dc25-121">The command prompts you for a password.</span></span>
<span data-ttu-id="2dc25-122">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="2dc25-122">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="2dc25-123">La deuxième commande restaure la configuration des ordinateurs identifiés par les objets **CimSession** stockés dans la variable $Session (dans ce cas, l'ordinateur nommé Server01).</span><span class="sxs-lookup"><span data-stu-id="2dc25-123">The second command restores the configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="2dc25-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dc25-124">PARAMETERS</span></span>

### <span data-ttu-id="2dc25-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2dc25-125">-AsJob</span></span>
<span data-ttu-id="2dc25-126">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2dc25-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2dc25-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2dc25-127">-CimSession</span></span>
<span data-ttu-id="2dc25-128">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2dc25-128">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2dc25-129">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande **New-CimSession** ou **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="2dc25-129">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

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

### <span data-ttu-id="2dc25-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2dc25-130">-ThrottleLimit</span></span>
<span data-ttu-id="2dc25-131">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2dc25-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="2dc25-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2dc25-132">-Confirm</span></span>
<span data-ttu-id="2dc25-133">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2dc25-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2dc25-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2dc25-134">-WhatIf</span></span>
<span data-ttu-id="2dc25-135">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2dc25-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2dc25-136">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2dc25-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2dc25-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dc25-137">CommonParameters</span></span>
<span data-ttu-id="2dc25-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2dc25-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2dc25-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2dc25-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2dc25-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2dc25-140">INPUTS</span></span>

## <span data-ttu-id="2dc25-141">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2dc25-141">OUTPUTS</span></span>

## <span data-ttu-id="2dc25-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2dc25-142">NOTES</span></span>

## <span data-ttu-id="2dc25-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2dc25-143">RELATED LINKS</span></span>

[<span data-ttu-id="2dc25-144">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dc25-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2dc25-145">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2dc25-145">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="2dc25-146">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2dc25-146">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2dc25-147">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2dc25-147">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2dc25-148">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2dc25-148">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

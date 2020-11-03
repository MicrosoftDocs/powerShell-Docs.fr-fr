---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203937"
---
# <span data-ttu-id="47e19-103">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="47e19-103">Remove-DscConfigurationDocument</span></span>

## <span data-ttu-id="47e19-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="47e19-104">SYNOPSIS</span></span>
<span data-ttu-id="47e19-105">Supprime un document de configuration du magasin de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="47e19-105">Removes a configuration document from the DSC configuration store.</span></span>

## <span data-ttu-id="47e19-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="47e19-106">SYNTAX</span></span>

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="47e19-107">Description</span><span class="sxs-lookup"><span data-stu-id="47e19-107">DESCRIPTION</span></span>
<span data-ttu-id="47e19-108">L' `Remove-DscConfigurationDocument` applet de commande supprime un document de configuration (fichier. MOF) du magasin de configuration de la configuration d’état souhaité (DSC) Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47e19-108">The `Remove-DscConfigurationDocument` cmdlet removes a configuration document (.mof file) from the Windows PowerShell Desired State Configuration (DSC) configuration store.</span></span>
<span data-ttu-id="47e19-109">Pendant la configuration, l’applet de commande `Start-DscConfiguration` copie un fichier. mof dans un dossier sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="47e19-109">During configuration, the `Start-DscConfiguration` cmdlet copies a .mof file to a folder on the target computer.</span></span>
<span data-ttu-id="47e19-110">Cette applet de commande supprime ce document de configuration et effectue un nettoyage supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="47e19-110">This cmdlet removes that configuration document and does additional cleanup.</span></span>

<span data-ttu-id="47e19-111">Cette applet de commande est disponible uniquement dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8,1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) à partir de la bibliothèque de support Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47e19-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="47e19-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="47e19-112">EXAMPLES</span></span>

### <span data-ttu-id="47e19-113">Exemple 1 : supprimer le document de configuration actuel</span><span class="sxs-lookup"><span data-stu-id="47e19-113">Example 1: Remove the current configuration document</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

<span data-ttu-id="47e19-114">La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.</span><span class="sxs-lookup"><span data-stu-id="47e19-114">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="47e19-115">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="47e19-115">The command prompts you for a password.</span></span>
<span data-ttu-id="47e19-116">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="47e19-116">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="47e19-117">La deuxième commande supprime le document de configuration actuel pour l’ordinateur spécifié dans le **CimSession** stocké dans $session.</span><span class="sxs-lookup"><span data-stu-id="47e19-117">The second command removes the current configuration document for the computer specified in the **CimSession** stored in $Session.</span></span>

## <span data-ttu-id="47e19-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="47e19-118">PARAMETERS</span></span>

### <span data-ttu-id="47e19-119">-AsJob</span><span class="sxs-lookup"><span data-stu-id="47e19-119">-AsJob</span></span>
<span data-ttu-id="47e19-120">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="47e19-120">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="47e19-121">Si vous spécifiez le paramètre *AsJob* , la commande retourne un objet qui représente le travail, puis affiche l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="47e19-121">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="47e19-122">Vous pouvez continuer à travailler dans la session jusqu’à ce que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="47e19-122">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="47e19-123">La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="47e19-123">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="47e19-124">Pour gérer la tâche, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="47e19-124">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="47e19-125">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="47e19-125">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="47e19-126">Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="47e19-126">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="47e19-127">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47e19-127">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="47e19-128">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="47e19-128">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="47e19-129">-CimSession</span><span class="sxs-lookup"><span data-stu-id="47e19-129">-CimSession</span></span>
<span data-ttu-id="47e19-130">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="47e19-130">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="47e19-131">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande **New-CimSession** ou **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="47e19-131">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

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

### <span data-ttu-id="47e19-132">-Force</span><span class="sxs-lookup"><span data-stu-id="47e19-132">-Force</span></span>
<span data-ttu-id="47e19-133">Indique que cette applet de commande arrête le travail de configuration en cours d’exécution avant de supprimer le document de configuration.</span><span class="sxs-lookup"><span data-stu-id="47e19-133">Indicates that this cmdlet stops the running configuration job before it removes the configuration document.</span></span>
<span data-ttu-id="47e19-134">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="47e19-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="47e19-135">-Étape</span><span class="sxs-lookup"><span data-stu-id="47e19-135">-Stage</span></span>
<span data-ttu-id="47e19-136">Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="47e19-136">Specifies which configuration document to remove.</span></span>
<span data-ttu-id="47e19-137">Vous pouvez spécifier plusieurs documents.</span><span class="sxs-lookup"><span data-stu-id="47e19-137">You can specify multiple documents.</span></span>
<span data-ttu-id="47e19-138">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="47e19-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="47e19-139">Version actuelle.</span><span class="sxs-lookup"><span data-stu-id="47e19-139">Current.</span></span>
<span data-ttu-id="47e19-140">Supprimez le document de configuration qui décrit l’état actuel du système.</span><span class="sxs-lookup"><span data-stu-id="47e19-140">Remove the configuration document that describes the current state of the system.</span></span>
- <span data-ttu-id="47e19-141">En attente.</span><span class="sxs-lookup"><span data-stu-id="47e19-141">Pending.</span></span>
<span data-ttu-id="47e19-142">Supprimez le document de configuration qui décrit l’état d’attente du système.</span><span class="sxs-lookup"><span data-stu-id="47e19-142">Remove the configuration document that describes the pending state of the system.</span></span>
- <span data-ttu-id="47e19-143">Précédent.</span><span class="sxs-lookup"><span data-stu-id="47e19-143">Previous.</span></span>
<span data-ttu-id="47e19-144">Supprimez le document de configuration qui décrit l’état précédent du système.</span><span class="sxs-lookup"><span data-stu-id="47e19-144">Remove the configuration document that describes the previous state of the system.</span></span>

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="47e19-145">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="47e19-145">-ThrottleLimit</span></span>
<span data-ttu-id="47e19-146">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47e19-146">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="47e19-147">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="47e19-147">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="47e19-148">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="47e19-148">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="47e19-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="47e19-149">-Confirm</span></span>
<span data-ttu-id="47e19-150">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47e19-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="47e19-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="47e19-151">-WhatIf</span></span>
<span data-ttu-id="47e19-152">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47e19-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="47e19-153">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="47e19-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="47e19-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="47e19-154">CommonParameters</span></span>
<span data-ttu-id="47e19-155">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="47e19-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="47e19-156">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="47e19-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="47e19-157">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="47e19-157">INPUTS</span></span>

### <span data-ttu-id="47e19-158">Aucun</span><span class="sxs-lookup"><span data-stu-id="47e19-158">None</span></span>

## <span data-ttu-id="47e19-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="47e19-159">OUTPUTS</span></span>

### <span data-ttu-id="47e19-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="47e19-160">None</span></span>

## <span data-ttu-id="47e19-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="47e19-161">NOTES</span></span>

## <span data-ttu-id="47e19-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="47e19-162">RELATED LINKS</span></span>

[<span data-ttu-id="47e19-163">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47e19-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="47e19-164">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="47e19-164">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="47e19-165">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="47e19-165">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203938"
---
# <span data-ttu-id="db74b-103">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="db74b-103">Publish-DscConfiguration</span></span>

## <span data-ttu-id="db74b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="db74b-104">SYNOPSIS</span></span>
<span data-ttu-id="db74b-105">Publie une configuration DSC sur un ensemble d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="db74b-105">Publishes a DSC configuration to a set of computers.</span></span>

## <span data-ttu-id="db74b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db74b-106">SYNTAX</span></span>

### <span data-ttu-id="db74b-107">ComputerNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="db74b-107">ComputerNameSet (Default)</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="db74b-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="db74b-108">CimSessionSet</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="db74b-109">Description</span><span class="sxs-lookup"><span data-stu-id="db74b-109">DESCRIPTION</span></span>
<span data-ttu-id="db74b-110">L’applet de commande **Publish-DscConfiguration** publie un document de configuration DSC (Desired State Configuration) Windows PowerShell sur un ensemble d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="db74b-110">The **Publish-DscConfiguration** cmdlet publishes a Windows PowerShell Desired State Configuration (DSC) configuration document on set of computers.</span></span>
<span data-ttu-id="db74b-111">Cette applet de commande n’applique pas la configuration.</span><span class="sxs-lookup"><span data-stu-id="db74b-111">This cmdlet does not apply the configuration.</span></span>
<span data-ttu-id="db74b-112">Les configurations sont appliquées par l’applet de commande Start-DscConfiguration lorsqu’elle est utilisée avec le paramètre *UseExisting* ou lorsque le moteur DSC exécute son cycle de cohérence.</span><span class="sxs-lookup"><span data-stu-id="db74b-112">Configurations are applied by either the Start-DscConfiguration cmdlet when it is used with the *UseExisting* parameter or when the DSC engine runs its consistency cycle.</span></span>
<span data-ttu-id="db74b-113">Le moteur DSC est également connu sous le nom de Configuration Manager local (LCM).</span><span class="sxs-lookup"><span data-stu-id="db74b-113">The DSC engine is also known as the Local Configuration Manager (LCM).</span></span>

<span data-ttu-id="db74b-114">Cette applet de commande est particulièrement utile lorsque des fragments de plusieurs documents de configuration sont remis.</span><span class="sxs-lookup"><span data-stu-id="db74b-114">This cmdlet is especially useful when fragments of multiple configuration documents are delivered.</span></span>
<span data-ttu-id="db74b-115">Lorsque plusieurs fragments de documents de configuration sont remis, ils remplacent les fragments de document de configuration antérieurs.</span><span class="sxs-lookup"><span data-stu-id="db74b-115">When multiple configuration documents fragments are delivered, they overwrite the older configuration document fragments.</span></span>

## <span data-ttu-id="db74b-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="db74b-116">EXAMPLES</span></span>

### <span data-ttu-id="db74b-117">Exemple 1 : publier une configuration sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="db74b-117">Example 1: Publish a configuration to a remote computer</span></span>

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

<span data-ttu-id="db74b-118">Cette commande publie une configuration sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="db74b-118">This command publishes a configuration to a remote computer.</span></span>
<span data-ttu-id="db74b-119">L’utilisateur qui exécute l’applet de commande doit être administrateur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="db74b-119">The user who runs the cmdlet should be administrator on the remote computer.</span></span>

## <span data-ttu-id="db74b-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db74b-120">PARAMETERS</span></span>

### <span data-ttu-id="db74b-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="db74b-121">-CimSession</span></span>
<span data-ttu-id="db74b-122">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="db74b-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="db74b-123">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="db74b-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="db74b-124">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db74b-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="db74b-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="db74b-125">-ComputerName</span></span>
<span data-ttu-id="db74b-126">Spécifie un ou plusieurs ordinateurs sur lesquels cette applet de commande publie la configuration.</span><span class="sxs-lookup"><span data-stu-id="db74b-126">Specifies one or more computers on which this cmdlet publishes the configuration.</span></span>

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

### <span data-ttu-id="db74b-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="db74b-127">-Credential</span></span>
<span data-ttu-id="db74b-128">Spécifie les informations d’identification utilisées pour accéder à l’appareil cible.</span><span class="sxs-lookup"><span data-stu-id="db74b-128">Specifies credentials that are used to access the target device.</span></span>

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

### <span data-ttu-id="db74b-129">-Force</span><span class="sxs-lookup"><span data-stu-id="db74b-129">-Force</span></span>
<span data-ttu-id="db74b-130">Force l’applet de commande à se terminer.</span><span class="sxs-lookup"><span data-stu-id="db74b-130">Forces the cmdlet to finish.</span></span>
<span data-ttu-id="db74b-131">Si le mode d’actualisation local Configuration Manager est défini sur PULL, l’utilisation de ce paramètre le remplace par PUSH et active la publication de la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="db74b-131">If the Local Configuration Manager refresh mode is set to PULL, usage of this parameter changes it to PUSH and enables publication of the DSC configuration.</span></span>
<span data-ttu-id="db74b-132">En outre, si une configuration DSC en attente existe, l’utilisation de ce paramètre remplace la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="db74b-132">Also, if a pending DSC configuration exists, usage of this parameter overwrites that pending configuration.</span></span>

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

### <span data-ttu-id="db74b-133">-Path</span><span class="sxs-lookup"><span data-stu-id="db74b-133">-Path</span></span>
<span data-ttu-id="db74b-134">Spécifie un chemin d’accès qui contient les configurations à publier sur les ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="db74b-134">Specifies a path that contains configurations to publish to target computers.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db74b-135">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="db74b-135">-ThrottleLimit</span></span>
<span data-ttu-id="db74b-136">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db74b-136">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="db74b-137">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="db74b-137">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="db74b-138">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="db74b-138">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="db74b-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="db74b-139">-Confirm</span></span>
<span data-ttu-id="db74b-140">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db74b-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="db74b-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="db74b-141">-WhatIf</span></span>
<span data-ttu-id="db74b-142">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db74b-142">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="db74b-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="db74b-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="db74b-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db74b-144">CommonParameters</span></span>
<span data-ttu-id="db74b-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db74b-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db74b-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="db74b-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db74b-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="db74b-147">INPUTS</span></span>

## <span data-ttu-id="db74b-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="db74b-148">OUTPUTS</span></span>

## <span data-ttu-id="db74b-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="db74b-149">NOTES</span></span>

## <span data-ttu-id="db74b-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="db74b-150">RELATED LINKS</span></span>

[<span data-ttu-id="db74b-151">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="db74b-151">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="db74b-152">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="db74b-152">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="db74b-153">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="db74b-153">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="db74b-154">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="db74b-154">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="db74b-155">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="db74b-155">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="db74b-156">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="db74b-156">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "93205294"
---
# <span data-ttu-id="4a766-103">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4a766-103">Set-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="4a766-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4a766-104">SYNOPSIS</span></span>

<span data-ttu-id="4a766-105">Applique les paramètres du Configuration Manager local (LCM) aux nœuds.</span><span class="sxs-lookup"><span data-stu-id="4a766-105">Applies Local Configuration Manager (LCM) settings to nodes.</span></span>

## <span data-ttu-id="4a766-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a766-106">SYNTAX</span></span>

### <span data-ttu-id="4a766-107">ComputerNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4a766-107">ComputerNameSet (Default)</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4a766-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="4a766-108">CimSessionSet</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4a766-109">Description</span><span class="sxs-lookup"><span data-stu-id="4a766-109">DESCRIPTION</span></span>

<span data-ttu-id="4a766-110">L' `Set-DscLocalConfigurationManager` applet de commande applique les paramètres du gestionnaire de configuration local aux nœuds.</span><span class="sxs-lookup"><span data-stu-id="4a766-110">The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings, or meta-configuration, to nodes.</span></span> <span data-ttu-id="4a766-111">Spécifiez les ordinateurs en indiquant leurs noms ou en utilisant des sessions CIM (Common Information Model).</span><span class="sxs-lookup"><span data-stu-id="4a766-111">Specify computers by specifying computer names or by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="4a766-112">Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande applique les paramètres à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4a766-112">If you do not specify a target computer, the cmdlet applies settings to the local computer.</span></span>

## <span data-ttu-id="4a766-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4a766-113">EXAMPLES</span></span>

### <span data-ttu-id="4a766-114">Exemple 1 : appliquer les paramètres du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="4a766-114">Example 1: Apply LCM settings</span></span>

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="4a766-115">Cette commande applique les paramètres du gestionnaire de configuration local à des `C:\DSC\Configurations\` nœuds ciblés.</span><span class="sxs-lookup"><span data-stu-id="4a766-115">This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes.</span></span> <span data-ttu-id="4a766-116">Une fois les paramètres reçus, le gestionnaire de configuration local les traite.</span><span class="sxs-lookup"><span data-stu-id="4a766-116">After receiving the settings, LCM processes them.</span></span>

> [!WARNING]
> <span data-ttu-id="4a766-117">S’il existe plusieurs méta-MOF pour le même ordinateur stocké dans le dossier spécifié, seul le premier méta MOF sera appliqué.</span><span class="sxs-lookup"><span data-stu-id="4a766-117">If there are multiple meta mofs for the same computer stored in the specified folder, only the first meta mof will be applied.</span></span>

### <span data-ttu-id="4a766-118">Exemple 2 : appliquer les paramètres du gestionnaire de configuration local à l’aide d’une session CIM</span><span class="sxs-lookup"><span data-stu-id="4a766-118">Example 2: Apply LCM settings by using a CIM session</span></span>

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="4a766-119">Cet exemple applique les paramètres du gestionnaire de configuration local à un ordinateur et applique les paramètres.</span><span class="sxs-lookup"><span data-stu-id="4a766-119">This example applies LCM settings to a computer and applies the settings.</span></span> <span data-ttu-id="4a766-120">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a766-120">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span> <span data-ttu-id="4a766-121">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4a766-121">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="4a766-122">La première commande crée une session CIM à l’aide de l’applet de commande `New-CimSession` , puis stocke l’objet **CimSession** dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="4a766-122">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the `$Session` variable.</span></span> <span data-ttu-id="4a766-123">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4a766-123">The command prompts you for a password.</span></span> <span data-ttu-id="4a766-124">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="4a766-124">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="4a766-125">La deuxième commande applique les paramètres LCM du nœud ciblé de `C:\DSC\Configurations\` à l’ordinateur identifié par les objets **CimSession** stockés dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="4a766-125">The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the computer identified by the **CimSession** objects stored in the `$Session` variable.</span></span> <span data-ttu-id="4a766-126">Dans cet exemple, la `$Session` variable contient une session CIM uniquement pour l’ordinateur nommé SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="4a766-126">In this example, the `$Session` variable contains a CIM session only for the computer named Server01.</span></span> <span data-ttu-id="4a766-127">La commande applique les paramètres.</span><span class="sxs-lookup"><span data-stu-id="4a766-127">The command applies the settings.</span></span> <span data-ttu-id="4a766-128">Une fois les paramètres reçus, le gestionnaire de configuration local les traite.</span><span class="sxs-lookup"><span data-stu-id="4a766-128">After receiving the settings, LCM processes them.</span></span>

## <span data-ttu-id="4a766-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a766-129">PARAMETERS</span></span>

### <span data-ttu-id="4a766-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="4a766-130">-CimSession</span></span>

<span data-ttu-id="4a766-131">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="4a766-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="4a766-132">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) ou [CimSession](/powershell/module/CimCmdlets/Get-CimSession) .</span><span class="sxs-lookup"><span data-stu-id="4a766-132">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span></span>
<span data-ttu-id="4a766-133">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4a766-133">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="4a766-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4a766-134">-ComputerName</span></span>

<span data-ttu-id="4a766-135">Spécifie un tableau de noms d'ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="4a766-135">Specifies an array of computer names.</span></span> <span data-ttu-id="4a766-136">Ce paramètre limite les ordinateurs qui ont des documents de méta-configuration dans le paramètre **path** à ceux spécifiés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="4a766-136">This parameter restricts the computers that have meta-configuration documents in the **Path** parameter to those specified in the array.</span></span>

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

### <span data-ttu-id="4a766-137">-Credential</span><span class="sxs-lookup"><span data-stu-id="4a766-137">-Credential</span></span>

<span data-ttu-id="4a766-138">Spécifie un nom d'utilisateur et un mot de passe, sous la forme d'un objet **PSCredential** , pour l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="4a766-138">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span> <span data-ttu-id="4a766-139">Pour obtenir un objet **PSCredential** , utilisez l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="4a766-139">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span> <span data-ttu-id="4a766-140">Pour plus d'informations, voir `Get-Help Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="4a766-140">For more information, type `Get-Help Get-Credential`.</span></span>

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

### <span data-ttu-id="4a766-141">-Force</span><span class="sxs-lookup"><span data-stu-id="4a766-141">-Force</span></span>

<span data-ttu-id="4a766-142">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4a766-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4a766-143">-Path</span><span class="sxs-lookup"><span data-stu-id="4a766-143">-Path</span></span>

<span data-ttu-id="4a766-144">Spécifie le chemin d'accès d'un dossier qui contient les fichiers de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="4a766-144">Specifies a file path of a folder that contains configuration settings files.</span></span> <span data-ttu-id="4a766-145">L’applet de commande publie et applique ces paramètres LCM aux ordinateurs qui ont des fichiers de paramètres dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a766-145">The cmdlet publishes and applies these LCM settings to computers that have settings files in the specified path.</span></span> <span data-ttu-id="4a766-146">Chaque nœud cible doit avoir un fichier de paramètres au format suivant : `NetBIOS Name.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="4a766-146">Each target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.</span></span>

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

### <span data-ttu-id="4a766-147">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4a766-147">-ThrottleLimit</span></span>

<span data-ttu-id="4a766-148">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a766-148">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span> <span data-ttu-id="4a766-149">Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4a766-149">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="4a766-150">Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4a766-150">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="4a766-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4a766-151">-Confirm</span></span>

<span data-ttu-id="4a766-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a766-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4a766-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4a766-153">-WhatIf</span></span>

<span data-ttu-id="4a766-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a766-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4a766-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a766-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4a766-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a766-156">CommonParameters</span></span>

<span data-ttu-id="4a766-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4a766-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a766-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4a766-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a766-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4a766-159">INPUTS</span></span>

## <span data-ttu-id="4a766-160">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4a766-160">OUTPUTS</span></span>

## <span data-ttu-id="4a766-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4a766-161">NOTES</span></span>

## <span data-ttu-id="4a766-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4a766-162">RELATED LINKS</span></span>

[<span data-ttu-id="4a766-163">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a766-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="4a766-164">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4a766-164">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

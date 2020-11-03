---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 0bf221e28586d4cb3530583255b763ff0d6282df
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202590"
---
# <span data-ttu-id="2a2bd-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-103">Update-Script</span></span>

## <span data-ttu-id="2a2bd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2a2bd-104">SYNOPSIS</span></span>
<span data-ttu-id="2a2bd-105">Met à jour un script.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-105">Updates a script.</span></span>

## <span data-ttu-id="2a2bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a2bd-106">SYNTAX</span></span>

### <span data-ttu-id="2a2bd-107">Tous</span><span class="sxs-lookup"><span data-stu-id="2a2bd-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a2bd-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a2bd-108">DESCRIPTION</span></span>

<span data-ttu-id="2a2bd-109">L' `Update-Script` applet de commande met à jour un script qui est installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="2a2bd-110">Le script mis à jour est téléchargé à partir du même référentiel que la version installée.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="2a2bd-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2a2bd-111">EXAMPLES</span></span>

### <span data-ttu-id="2a2bd-112">Exemple 1 : mettre à jour le script spécifié</span><span class="sxs-lookup"><span data-stu-id="2a2bd-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="2a2bd-113">Cet exemple met à jour un script installé et affiche la version mise à jour.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="2a2bd-114">`Update-Script` utilise le paramètre **Name** pour spécifier le script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="2a2bd-115">Le paramètre **RequiredVersion** spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="2a2bd-116">`Get-InstalledScript` affiche la version mise à jour du script.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="2a2bd-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a2bd-117">PARAMETERS</span></span>

### <span data-ttu-id="2a2bd-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2a2bd-118">-AcceptLicense</span></span>

<span data-ttu-id="2a2bd-119">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="2a2bd-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="2a2bd-120">-AllowPrerelease</span></span>

<span data-ttu-id="2a2bd-121">Vous permet de mettre à jour un script avec le script le plus récent marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="2a2bd-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a2bd-122">-Confirm</span></span>

<span data-ttu-id="2a2bd-123">Vous invite à confirmer l’exécution `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="2a2bd-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="2a2bd-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="2a2bd-124">-Credential</span></span>

<span data-ttu-id="2a2bd-125">Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un script.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-125">Specifies a user account that has permission to update a script.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-126">-Force</span><span class="sxs-lookup"><span data-stu-id="2a2bd-126">-Force</span></span>

<span data-ttu-id="2a2bd-127">Force l' `Update-Script` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2a2bd-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2a2bd-128">-MaximumVersion</span></span>

<span data-ttu-id="2a2bd-129">Spécifie la version maximale ou la plus récente du script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="2a2bd-130">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-131">-Name</span><span class="sxs-lookup"><span data-stu-id="2a2bd-131">-Name</span></span>

<span data-ttu-id="2a2bd-132">Spécifie un nom de script ou un tableau de noms de script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-132">Specifies one script name or an array of script names to update.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2a2bd-133">-PassThru</span></span>

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

### <span data-ttu-id="2a2bd-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="2a2bd-134">-Proxy</span></span>

<span data-ttu-id="2a2bd-135">Spécifie un serveur proxy pour la demande plutôt que de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2a2bd-136">-ProxyCredential</span></span>

<span data-ttu-id="2a2bd-137">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="2a2bd-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2a2bd-138">-RequiredVersion</span></span>

<span data-ttu-id="2a2bd-139">Spécifie le numéro de version exact du script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="2a2bd-140">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a2bd-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a2bd-141">-WhatIf</span></span>

<span data-ttu-id="2a2bd-142">Montre ce qui se passe si `Update-Script` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="2a2bd-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2a2bd-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a2bd-144">CommonParameters</span></span>

<span data-ttu-id="2a2bd-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a2bd-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a2bd-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2a2bd-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a2bd-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2a2bd-147">INPUTS</span></span>

### <span data-ttu-id="2a2bd-148">System.String[]</span><span class="sxs-lookup"><span data-stu-id="2a2bd-148">System.String[]</span></span>

### <span data-ttu-id="2a2bd-149">System.String</span><span class="sxs-lookup"><span data-stu-id="2a2bd-149">System.String</span></span>

### <span data-ttu-id="2a2bd-150">System.Uri</span><span class="sxs-lookup"><span data-stu-id="2a2bd-150">System.Uri</span></span>

### <span data-ttu-id="2a2bd-151">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="2a2bd-151">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="2a2bd-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2a2bd-152">OUTPUTS</span></span>

### <span data-ttu-id="2a2bd-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="2a2bd-153">System.Object</span></span>

## <span data-ttu-id="2a2bd-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2a2bd-154">NOTES</span></span>

## <span data-ttu-id="2a2bd-155">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2a2bd-155">RELATED LINKS</span></span>

[<span data-ttu-id="2a2bd-156">Find-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-156">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="2a2bd-157">Install-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-157">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="2a2bd-158">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-158">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="2a2bd-159">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-159">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="2a2bd-160">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="2a2bd-160">Uninstall-Script</span></span>](Uninstall-Script.md)


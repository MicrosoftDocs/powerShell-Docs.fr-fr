---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 7f0da0403b21b6b4980844f13c23b2659500dd7c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891436"
---
# <span data-ttu-id="0fa2f-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-103">Update-Script</span></span>

## <span data-ttu-id="0fa2f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0fa2f-104">SYNOPSIS</span></span>
<span data-ttu-id="0fa2f-105">Met à jour un script.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-105">Updates a script.</span></span>

## <span data-ttu-id="0fa2f-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0fa2f-106">SYNTAX</span></span>

### <span data-ttu-id="0fa2f-107">Tous</span><span class="sxs-lookup"><span data-stu-id="0fa2f-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0fa2f-108">Description</span><span class="sxs-lookup"><span data-stu-id="0fa2f-108">DESCRIPTION</span></span>

<span data-ttu-id="0fa2f-109">L' `Update-Script` applet de commande met à jour un script qui est installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="0fa2f-110">Le script mis à jour est téléchargé à partir du même référentiel que la version installée.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="0fa2f-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0fa2f-111">EXAMPLES</span></span>

### <span data-ttu-id="0fa2f-112">Exemple 1 : mettre à jour le script spécifié</span><span class="sxs-lookup"><span data-stu-id="0fa2f-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="0fa2f-113">Cet exemple met à jour un script installé et affiche la version mise à jour.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="0fa2f-114">`Update-Script` utilise le paramètre **Name** pour spécifier le script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="0fa2f-115">Le paramètre **RequiredVersion** spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="0fa2f-116">`Get-InstalledScript` affiche la version mise à jour du script.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="0fa2f-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0fa2f-117">PARAMETERS</span></span>

### <span data-ttu-id="0fa2f-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="0fa2f-118">-AcceptLicense</span></span>

<span data-ttu-id="0fa2f-119">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="0fa2f-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0fa2f-120">-AllowPrerelease</span></span>

<span data-ttu-id="0fa2f-121">Vous permet de mettre à jour un script avec le script le plus récent marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="0fa2f-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0fa2f-122">-Confirm</span></span>

<span data-ttu-id="0fa2f-123">Vous invite à confirmer l’exécution `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="0fa2f-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="0fa2f-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="0fa2f-124">-Credential</span></span>

<span data-ttu-id="0fa2f-125">Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un script.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-125">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="0fa2f-126">-Force</span><span class="sxs-lookup"><span data-stu-id="0fa2f-126">-Force</span></span>

<span data-ttu-id="0fa2f-127">Force l' `Update-Script` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0fa2f-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0fa2f-128">-MaximumVersion</span></span>

<span data-ttu-id="0fa2f-129">Spécifie la version maximale ou la plus récente du script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="0fa2f-130">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0fa2f-131">-Name</span><span class="sxs-lookup"><span data-stu-id="0fa2f-131">-Name</span></span>

<span data-ttu-id="0fa2f-132">Spécifie un nom de script ou un tableau de noms de script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-132">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="0fa2f-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0fa2f-133">-PassThru</span></span>

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

### <span data-ttu-id="0fa2f-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="0fa2f-134">-Proxy</span></span>

<span data-ttu-id="0fa2f-135">Spécifie un serveur proxy pour la demande plutôt que de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="0fa2f-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0fa2f-136">-ProxyCredential</span></span>

<span data-ttu-id="0fa2f-137">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="0fa2f-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="0fa2f-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0fa2f-138">-RequiredVersion</span></span>

<span data-ttu-id="0fa2f-139">Spécifie le numéro de version exact du script à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="0fa2f-140">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0fa2f-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0fa2f-141">-WhatIf</span></span>

<span data-ttu-id="0fa2f-142">Montre ce qui se passe si `Update-Script` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="0fa2f-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0fa2f-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0fa2f-144">CommonParameters</span></span>

<span data-ttu-id="0fa2f-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0fa2f-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0fa2f-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0fa2f-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0fa2f-147">INPUTS</span></span>

### <span data-ttu-id="0fa2f-148">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0fa2f-148">System.String[]</span></span>

### <span data-ttu-id="0fa2f-149">System.String</span><span class="sxs-lookup"><span data-stu-id="0fa2f-149">System.String</span></span>

### <span data-ttu-id="0fa2f-150">System.Uri</span><span class="sxs-lookup"><span data-stu-id="0fa2f-150">System.Uri</span></span>

### <span data-ttu-id="0fa2f-151">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="0fa2f-151">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="0fa2f-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0fa2f-152">OUTPUTS</span></span>

### <span data-ttu-id="0fa2f-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="0fa2f-153">System.Object</span></span>

## <span data-ttu-id="0fa2f-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0fa2f-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fa2f-155">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="0fa2f-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0fa2f-156">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0fa2f-157">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="0fa2f-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0fa2f-158">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fa2f-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0fa2f-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0fa2f-159">RELATED LINKS</span></span>

[<span data-ttu-id="0fa2f-160">Find-Script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-160">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="0fa2f-161">Install-Script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-161">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0fa2f-162">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-162">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0fa2f-163">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-163">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0fa2f-164">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="0fa2f-164">Uninstall-Script</span></span>](Uninstall-Script.md)

---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 539131ad5a22671984079988ce589b5b7a2fd15b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202601"
---
# <span data-ttu-id="e0f1c-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-103">Save-Script</span></span>

## <span data-ttu-id="e0f1c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e0f1c-104">SYNOPSIS</span></span>
<span data-ttu-id="e0f1c-105">Enregistre un script.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-105">Saves a script.</span></span>

## <span data-ttu-id="e0f1c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0f1c-106">SYNTAX</span></span>

### <span data-ttu-id="e0f1c-107">NameAndPathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e0f1c-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0f1c-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="e0f1c-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0f1c-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="e0f1c-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0f1c-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="e0f1c-110">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e0f1c-111">Description</span><span class="sxs-lookup"><span data-stu-id="e0f1c-111">DESCRIPTION</span></span>

<span data-ttu-id="e0f1c-112">L' `Save-Script` applet de commande enregistre le script spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-112">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="e0f1c-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e0f1c-113">EXAMPLES</span></span>

### <span data-ttu-id="e0f1c-114">Exemple 1 : enregistrer un script et valider les métadonnées du script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-114">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="e0f1c-115">Dans cet exemple, un script d’un référentiel est enregistré sur l’ordinateur local et les métadonnées du script sont validées.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-115">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="e0f1c-116">`Save-Script` utilise le paramètre **Name** pour spécifier le nom du script.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-116">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="e0f1c-117">Le paramètre de **dépôt** spécifie où trouver le script.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-117">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="e0f1c-118">Le script est enregistré à l’emplacement spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-118">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="e0f1c-119">`Test-ScriptFileInfo` Spécifie le **chemin d’accès** et valide les métadonnées du script.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-119">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="e0f1c-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0f1c-120">PARAMETERS</span></span>

### <span data-ttu-id="e0f1c-121">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="e0f1c-121">-AcceptLicense</span></span>

<span data-ttu-id="e0f1c-122">Accepter automatiquement le contrat de licence si le script l’exige.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-122">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="e0f1c-123">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e0f1c-123">-AllowPrerelease</span></span>

<span data-ttu-id="e0f1c-124">Vous permet d’enregistrer un script marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-124">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e0f1c-125">-Confirm</span></span>

<span data-ttu-id="e0f1c-126">Vous invite à confirmer l’exécution `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-126">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="e0f1c-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="e0f1c-127">-Credential</span></span>

<span data-ttu-id="e0f1c-128">Spécifie un compte d’utilisateur qui a l’autorisation d’enregistrer un script.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-128">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="e0f1c-129">-Force</span><span class="sxs-lookup"><span data-stu-id="e0f1c-129">-Force</span></span>

<span data-ttu-id="e0f1c-130">Force l' `Save-Script` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-130">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e0f1c-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e0f1c-131">-InputObject</span></span>

<span data-ttu-id="e0f1c-132">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-132">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="e0f1c-133">Par exemple, `Find-Script` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-133">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e0f1c-134">-LiteralPath</span></span>

<span data-ttu-id="e0f1c-135">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="e0f1c-136">La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-136">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="e0f1c-137">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e0f1c-138">Si le chemin d’accès comprend des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-138">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="e0f1c-139">PowerShell n’interprète pas les caractères placés entre guillemets simples comme séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-139">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-140">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e0f1c-140">-MaximumVersion</span></span>

<span data-ttu-id="e0f1c-141">Spécifie la version maximale ou la version la plus récente du script à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-141">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="e0f1c-142">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-142">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-143">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e0f1c-143">-MinimumVersion</span></span>

<span data-ttu-id="e0f1c-144">Spécifie la version minimale d’un script à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-144">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="e0f1c-145">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-145">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-146">-Name</span><span class="sxs-lookup"><span data-stu-id="e0f1c-146">-Name</span></span>

<span data-ttu-id="e0f1c-147">Spécifie un tableau de noms de script à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-147">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-148">-Path</span><span class="sxs-lookup"><span data-stu-id="e0f1c-148">-Path</span></span>

<span data-ttu-id="e0f1c-149">Spécifie l’emplacement sur l’ordinateur local où stocker un module enregistré.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-149">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="e0f1c-150">Accepte les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-150">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e0f1c-151">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e0f1c-151">-Proxy</span></span>

<span data-ttu-id="e0f1c-152">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-152">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="e0f1c-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e0f1c-153">-ProxyCredential</span></span>

<span data-ttu-id="e0f1c-154">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-154">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e0f1c-155">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="e0f1c-155">-Repository</span></span>

<span data-ttu-id="e0f1c-156">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="e0f1c-156">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="e0f1c-157">Utilisez `Get-PSRepository` pour afficher les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-157">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-158">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e0f1c-158">-RequiredVersion</span></span>

<span data-ttu-id="e0f1c-159">Spécifie le numéro de version exact du script à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-159">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0f1c-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e0f1c-160">-WhatIf</span></span>

<span data-ttu-id="e0f1c-161">Montre ce qui se passe si `Save-Script` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-161">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="e0f1c-162">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-162">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e0f1c-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0f1c-163">CommonParameters</span></span>

<span data-ttu-id="e0f1c-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0f1c-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0f1c-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e0f1c-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0f1c-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e0f1c-166">INPUTS</span></span>

### <span data-ttu-id="e0f1c-167">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e0f1c-167">System.String[]</span></span>

### <span data-ttu-id="e0f1c-168">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="e0f1c-168">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="e0f1c-169">System.String</span><span class="sxs-lookup"><span data-stu-id="e0f1c-169">System.String</span></span>

### <span data-ttu-id="e0f1c-170">System.Uri</span><span class="sxs-lookup"><span data-stu-id="e0f1c-170">System.Uri</span></span>

### <span data-ttu-id="e0f1c-171">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e0f1c-171">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="e0f1c-172">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e0f1c-172">OUTPUTS</span></span>

### <span data-ttu-id="e0f1c-173">System.Object</span><span class="sxs-lookup"><span data-stu-id="e0f1c-173">System.Object</span></span>

## <span data-ttu-id="e0f1c-174">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e0f1c-174">NOTES</span></span>

## <span data-ttu-id="e0f1c-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e0f1c-175">RELATED LINKS</span></span>

[<span data-ttu-id="e0f1c-176">Find-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-176">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="e0f1c-177">Install-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-177">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="e0f1c-178">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-178">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="e0f1c-179">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="e0f1c-179">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="e0f1c-180">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-180">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="e0f1c-181">Update-Script</span><span class="sxs-lookup"><span data-stu-id="e0f1c-181">Update-Script</span></span>](Update-Script.md)


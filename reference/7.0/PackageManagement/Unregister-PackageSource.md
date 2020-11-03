---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 06a4649d0d2f0912807219f25e60d85ba22564b0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201357"
---
# <span data-ttu-id="526b8-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="526b8-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="526b8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="526b8-104">SYNOPSIS</span></span>
<span data-ttu-id="526b8-105">Supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="526b8-105">Removes a registered package source.</span></span>

## <span data-ttu-id="526b8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="526b8-106">SYNTAX</span></span>

### <span data-ttu-id="526b8-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="526b8-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="526b8-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="526b8-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="526b8-109">NuGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="526b8-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="526b8-110">NuGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="526b8-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="526b8-111">PowerShellGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="526b8-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="526b8-112">PowerShellGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="526b8-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="526b8-113">Description</span><span class="sxs-lookup"><span data-stu-id="526b8-113">DESCRIPTION</span></span>

<span data-ttu-id="526b8-114">L' `Unregister-PackageSource` applet de commande supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="526b8-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="526b8-115">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="526b8-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="526b8-116">Pour rechercher des sources de package, utilisez l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="526b8-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="526b8-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="526b8-117">EXAMPLES</span></span>

### <span data-ttu-id="526b8-118">Exemple 1 : annuler l’inscription d’une source de package pour le fournisseur NuGet</span><span class="sxs-lookup"><span data-stu-id="526b8-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="526b8-119">L' `Unregister-PackageSource` applet de commande annule l’inscription d’une source de package à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="526b8-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="526b8-120">L' **emplacement** et les paramètres du **fournisseur** peuvent être utilisés pour spécifier plus précisément la source à supprimer.</span><span class="sxs-lookup"><span data-stu-id="526b8-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="526b8-121">L' `Unregister-PackageSource` applet de commande utilise le paramètre **source** pour spécifier la source à supprimer.</span><span class="sxs-lookup"><span data-stu-id="526b8-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="526b8-122">Exemple 2 : utiliser un objet PackageSource pour annuler l’inscription d’un package</span><span class="sxs-lookup"><span data-stu-id="526b8-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="526b8-123">Cet exemple utilise `Get-PackageSource` et `Unregister-PackageSource` pour annuler l’inscription d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="526b8-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="526b8-124">L’objet **PackageSource** est stocké dans une variable.</span><span class="sxs-lookup"><span data-stu-id="526b8-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="526b8-125">La `$pkgsource` variable stocke les **PackageSource** créés par l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="526b8-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="526b8-126">`Unregister-PackageSource` utilise `$pkgsource` en tant qu’entrée pour le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="526b8-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="526b8-127">L’applet de commande `Unregister-PackageSource` peut également spécifier une valeur pour le paramètre **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="526b8-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="526b8-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="526b8-128">PARAMETERS</span></span>

### <span data-ttu-id="526b8-129">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="526b8-129">-ConfigFile</span></span>

<span data-ttu-id="526b8-130">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="526b8-130">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="526b8-131">-Credential</span></span>

<span data-ttu-id="526b8-132">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="526b8-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="526b8-133">Tapez un nom d’utilisateur, tel que **User01** , **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="526b8-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="526b8-134">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="526b8-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="526b8-135">Lorsque le paramètre Credential n’est pas spécifié, le compte **d'** utilisateur actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="526b8-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-136">-Force</span><span class="sxs-lookup"><span data-stu-id="526b8-136">-Force</span></span>

<span data-ttu-id="526b8-137">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="526b8-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="526b8-138">Remplace les restrictions qui empêchent `Unregister-PackageSource` la réussie, à l’exception de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="526b8-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="526b8-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="526b8-139">-ForceBootstrap</span></span>

<span data-ttu-id="526b8-140">Indique que `Unregister-PackageSource` force **PackageManagement** à désinstaller automatiquement le fournisseur de package pour la source de package spécifiée.</span><span class="sxs-lookup"><span data-stu-id="526b8-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="526b8-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="526b8-141">-InputObject</span></span>

<span data-ttu-id="526b8-142">Accepte l’entrée de pipeline qui spécifie l’objet **PackageSource** de l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="526b8-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="526b8-143">**InputObject** accepte l’objet **PackageSource** comme une `Get-PackageSource` valeur ou une variable qui contient l’objet.</span><span class="sxs-lookup"><span data-stu-id="526b8-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-144">-Location</span><span class="sxs-lookup"><span data-stu-id="526b8-144">-Location</span></span>

<span data-ttu-id="526b8-145">Spécifie l’emplacement vers lequel pointe une source de package.</span><span class="sxs-lookup"><span data-stu-id="526b8-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="526b8-146">La valeur de ce paramètre peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="526b8-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="526b8-147">-PackageManagementProvider</span></span>

<span data-ttu-id="526b8-148">Spécifie le fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="526b8-148">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="526b8-149">-ProviderName</span></span>

<span data-ttu-id="526b8-150">Spécifie le nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="526b8-150">Specifies the provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="526b8-151">-PublishLocation</span></span>

<span data-ttu-id="526b8-152">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="526b8-152">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-153">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="526b8-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="526b8-154">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="526b8-154">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="526b8-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="526b8-156">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="526b8-156">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="526b8-157">-SkipValidate</span></span>

<span data-ttu-id="526b8-158">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="526b8-158">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-159">-Source</span><span class="sxs-lookup"><span data-stu-id="526b8-159">-Source</span></span>

<span data-ttu-id="526b8-160">Spécifie le nom convivial de la source du package.</span><span class="sxs-lookup"><span data-stu-id="526b8-160">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="526b8-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="526b8-161">-Confirm</span></span>

<span data-ttu-id="526b8-162">Vous invite à confirmer avant l' `Unregister-PackageSource` exécution de.</span><span class="sxs-lookup"><span data-stu-id="526b8-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="526b8-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="526b8-163">-WhatIf</span></span>

<span data-ttu-id="526b8-164">Montre ce qui se passe si l' `Unregister-PackageSource` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="526b8-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="526b8-165">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="526b8-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="526b8-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="526b8-166">CommonParameters</span></span>

<span data-ttu-id="526b8-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="526b8-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="526b8-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="526b8-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="526b8-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="526b8-169">INPUTS</span></span>

### <span data-ttu-id="526b8-170">`Unregister-PackageSource` accepte les objets **PackageSource** du pipeline en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="526b8-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="526b8-171">SORTIES</span><span class="sxs-lookup"><span data-stu-id="526b8-171">OUTPUTS</span></span>

### <span data-ttu-id="526b8-172">`Unregister-PackageSource` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="526b8-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="526b8-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="526b8-173">NOTES</span></span>

<span data-ttu-id="526b8-174">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="526b8-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="526b8-175">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="526b8-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="526b8-176">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="526b8-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="526b8-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="526b8-177">RELATED LINKS</span></span>

[<span data-ttu-id="526b8-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="526b8-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="526b8-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="526b8-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="526b8-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="526b8-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="526b8-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="526b8-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="526b8-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="526b8-182">Set-PackageSource</span></span>](Set-PackageSource.md)

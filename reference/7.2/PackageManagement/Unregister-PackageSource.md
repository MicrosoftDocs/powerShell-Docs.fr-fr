---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603886"
---
# <span data-ttu-id="e3980-102">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e3980-102">Unregister-PackageSource</span></span>

## <span data-ttu-id="e3980-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e3980-103">SYNOPSIS</span></span>
<span data-ttu-id="e3980-104">Supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="e3980-104">Removes a registered package source.</span></span>

## <span data-ttu-id="e3980-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e3980-105">SYNTAX</span></span>

### <span data-ttu-id="e3980-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="e3980-106">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="e3980-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="e3980-107">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e3980-108">NuGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="e3980-108">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="e3980-109">NuGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="e3980-109">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="e3980-110">PowerShellGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="e3980-110">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="e3980-111">PowerShellGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="e3980-111">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="e3980-112">Description</span><span class="sxs-lookup"><span data-stu-id="e3980-112">DESCRIPTION</span></span>

<span data-ttu-id="e3980-113">L' `Unregister-PackageSource` applet de commande supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="e3980-113">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="e3980-114">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="e3980-114">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="e3980-115">Pour rechercher des sources de package, utilisez l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="e3980-115">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="e3980-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e3980-116">EXAMPLES</span></span>

### <span data-ttu-id="e3980-117">Exemple 1 : annuler l’inscription d’une source de package pour le fournisseur NuGet</span><span class="sxs-lookup"><span data-stu-id="e3980-117">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="e3980-118">L' `Unregister-PackageSource` applet de commande annule l’inscription d’une source de package à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e3980-118">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="e3980-119">L' **emplacement** et les paramètres du **fournisseur** peuvent être utilisés pour spécifier plus précisément la source à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e3980-119">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="e3980-120">L' `Unregister-PackageSource` applet de commande utilise le paramètre **source** pour spécifier la source à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e3980-120">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="e3980-121">Exemple 2 : utiliser un objet PackageSource pour annuler l’inscription d’un package</span><span class="sxs-lookup"><span data-stu-id="e3980-121">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="e3980-122">Cet exemple utilise `Get-PackageSource` et `Unregister-PackageSource` pour annuler l’inscription d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="e3980-122">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="e3980-123">L’objet **PackageSource** est stocké dans une variable.</span><span class="sxs-lookup"><span data-stu-id="e3980-123">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="e3980-124">La `$pkgsource` variable stocke les **PackageSource** créés par l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="e3980-124">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="e3980-125">`Unregister-PackageSource` utilise `$pkgsource` en tant qu’entrée pour le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="e3980-125">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="e3980-126">L’applet de commande `Unregister-PackageSource` peut également spécifier une valeur pour le paramètre **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="e3980-126">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="e3980-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3980-127">PARAMETERS</span></span>

### <span data-ttu-id="e3980-128">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="e3980-128">-ConfigFile</span></span>

<span data-ttu-id="e3980-129">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e3980-129">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="e3980-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="e3980-130">-Credential</span></span>

<span data-ttu-id="e3980-131">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="e3980-131">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="e3980-132">Tapez un nom d’utilisateur, tel que **User01**, **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** , généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e3980-132">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e3980-133">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e3980-133">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="e3980-134">Lorsque le paramètre Credential n’est pas spécifié, le compte **d'** utilisateur actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e3980-134">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="e3980-135">-Force</span><span class="sxs-lookup"><span data-stu-id="e3980-135">-Force</span></span>

<span data-ttu-id="e3980-136">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e3980-136">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="e3980-137">Remplace les restrictions qui empêchent `Unregister-PackageSource` la réussie, à l’exception de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e3980-137">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="e3980-138">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e3980-138">-ForceBootstrap</span></span>

<span data-ttu-id="e3980-139">Indique que `Unregister-PackageSource` force **PackageManagement** à désinstaller automatiquement le fournisseur de package pour la source de package spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e3980-139">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="e3980-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e3980-140">-InputObject</span></span>

<span data-ttu-id="e3980-141">Accepte l’entrée de pipeline qui spécifie l’objet **PackageSource** de l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="e3980-141">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="e3980-142">**InputObject** accepte l’objet **PackageSource** comme une `Get-PackageSource` valeur ou une variable qui contient l’objet.</span><span class="sxs-lookup"><span data-stu-id="e3980-142">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="e3980-143">-Location</span><span class="sxs-lookup"><span data-stu-id="e3980-143">-Location</span></span>

<span data-ttu-id="e3980-144">Spécifie l’emplacement vers lequel pointe une source de package.</span><span class="sxs-lookup"><span data-stu-id="e3980-144">Specifies the location to which a package source points.</span></span> <span data-ttu-id="e3980-145">La valeur de ce paramètre peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="e3980-145">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="e3980-146">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e3980-146">-PackageManagementProvider</span></span>

<span data-ttu-id="e3980-147">Spécifie le fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="e3980-147">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="e3980-148">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="e3980-148">-ProviderName</span></span>

<span data-ttu-id="e3980-149">Spécifie le nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e3980-149">Specifies the provider name.</span></span>

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

### <span data-ttu-id="e3980-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="e3980-150">-PublishLocation</span></span>

<span data-ttu-id="e3980-151">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="e3980-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="e3980-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="e3980-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="e3980-153">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="e3980-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="e3980-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="e3980-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="e3980-155">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="e3980-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="e3980-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="e3980-156">-SkipValidate</span></span>

<span data-ttu-id="e3980-157">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="e3980-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="e3980-158">-Source</span><span class="sxs-lookup"><span data-stu-id="e3980-158">-Source</span></span>

<span data-ttu-id="e3980-159">Spécifie le nom convivial de la source du package.</span><span class="sxs-lookup"><span data-stu-id="e3980-159">Specifies the friendly name of the package source.</span></span>

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

### <span data-ttu-id="e3980-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e3980-160">-Confirm</span></span>

<span data-ttu-id="e3980-161">Vous invite à confirmer avant l' `Unregister-PackageSource` exécution de.</span><span class="sxs-lookup"><span data-stu-id="e3980-161">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="e3980-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e3980-162">-WhatIf</span></span>

<span data-ttu-id="e3980-163">Montre ce qui se passe si l' `Unregister-PackageSource` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="e3980-163">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="e3980-164">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e3980-164">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e3980-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3980-165">CommonParameters</span></span>

<span data-ttu-id="e3980-166">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3980-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3980-167">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e3980-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3980-168">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e3980-168">INPUTS</span></span>

### <span data-ttu-id="e3980-169">`Unregister-PackageSource` accepte les objets **PackageSource** du pipeline en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="e3980-169">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="e3980-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e3980-170">OUTPUTS</span></span>

### <span data-ttu-id="e3980-171">`Unregister-PackageSource` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e3980-171">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="e3980-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e3980-172">NOTES</span></span>

<span data-ttu-id="e3980-173">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e3980-173">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="e3980-174">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="e3980-174">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="e3980-175">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e3980-175">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="e3980-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e3980-176">RELATED LINKS</span></span>

[<span data-ttu-id="e3980-177">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e3980-177">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="e3980-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="e3980-178">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="e3980-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e3980-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="e3980-180">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e3980-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="e3980-181">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e3980-181">Set-PackageSource</span></span>](Set-PackageSource.md)


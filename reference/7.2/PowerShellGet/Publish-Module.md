---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 2edc05ff660cfcca232af878c593c29de68eb122
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595930"
---
# <span data-ttu-id="5371e-102">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="5371e-102">Publish-Module</span></span>

## <span data-ttu-id="5371e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5371e-103">SYNOPSIS</span></span>
<span data-ttu-id="5371e-104">Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="5371e-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="5371e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5371e-105">SYNTAX</span></span>

### <span data-ttu-id="5371e-106">ModuleNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5371e-106">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5371e-107">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="5371e-107">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5371e-108">Description</span><span class="sxs-lookup"><span data-stu-id="5371e-108">DESCRIPTION</span></span>

<span data-ttu-id="5371e-109">L' `Publish-Module` applet de commande publie un module dans une galerie en ligne NuGet à l’aide d’une clé API, stockée en tant que partie du profil d’un utilisateur dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="5371e-109">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="5371e-110">Vous pouvez indiquer le module à publier par son nom ou par le chemin d’accès au dossier le contenant.</span><span class="sxs-lookup"><span data-stu-id="5371e-110">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="5371e-111">Lorsque vous spécifiez un module par son nom, `Publish-Module` publie le premier module qui serait trouvé en exécutant `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="5371e-111">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="5371e-112">Si vous spécifiez une version minimale d’un module à publier, `Publish-Module` publie le premier module avec une version qui est supérieure ou égale à la version minimale que vous avez spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5371e-112">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="5371e-113">La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="5371e-113">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="5371e-114">Les métadonnées requises incluent le nom du module, la version, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="5371e-114">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="5371e-115">Bien que la plupart des métadonnées proviennent du manifeste de module, certaines métadonnées doivent être spécifiées dans des `Publish-Module` paramètres tels que **tag**, **ReleaseNote**, **iconUri**, **ProjectUri** et **LicenseUri**, car ces paramètres correspondent aux champs d’une galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="5371e-115">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**, because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="5371e-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5371e-116">EXAMPLES</span></span>

### <span data-ttu-id="5371e-117">Exemple 1 : publier un module</span><span class="sxs-lookup"><span data-stu-id="5371e-117">Example 1: Publish a module</span></span>

<span data-ttu-id="5371e-118">Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la galerie en ligne du propriétaire du module.</span><span class="sxs-lookup"><span data-stu-id="5371e-118">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="5371e-119">Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="5371e-119">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="5371e-120">Exemple 2 : publier un module avec les métadonnées de la Galerie</span><span class="sxs-lookup"><span data-stu-id="5371e-120">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="5371e-121">Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la Galerie du propriétaire du module.</span><span class="sxs-lookup"><span data-stu-id="5371e-121">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="5371e-122">Les métadonnées supplémentaires fournies sont affichées sur la page Web du module dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="5371e-122">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="5371e-123">Le propriétaire ajoute deux balises de recherche pour le module, en les associant à Active Directory ; une brève note de publication est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="5371e-123">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="5371e-124">Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="5371e-124">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="5371e-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5371e-125">PARAMETERS</span></span>

### <span data-ttu-id="5371e-126">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5371e-126">-AllowPrerelease</span></span>

<span data-ttu-id="5371e-127">Autorise la publication des modules marqués comme préversion.</span><span class="sxs-lookup"><span data-stu-id="5371e-127">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5371e-128">-Confirm</span></span>

<span data-ttu-id="5371e-129">Vous invite à confirmer l’exécution de l' `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="5371e-129">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="5371e-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="5371e-130">-Credential</span></span>

<span data-ttu-id="5371e-131">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour publier un module pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5371e-131">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="5371e-132">-Exclude</span><span class="sxs-lookup"><span data-stu-id="5371e-132">-Exclude</span></span>

<span data-ttu-id="5371e-133">Définit les fichiers à exclure du module publié.</span><span class="sxs-lookup"><span data-stu-id="5371e-133">Defines files to exclude from the published module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-134">-Force</span><span class="sxs-lookup"><span data-stu-id="5371e-134">-Force</span></span>

<span data-ttu-id="5371e-135">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5371e-135">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-136">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="5371e-136">-FormatVersion</span></span>

<span data-ttu-id="5371e-137">Accepte uniquement les valeurs valides spécifiées par l’attribut **ValidateSet** .</span><span class="sxs-lookup"><span data-stu-id="5371e-137">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="5371e-138">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) et [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span><span class="sxs-lookup"><span data-stu-id="5371e-138">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="5371e-139">-IconUri</span></span>

<span data-ttu-id="5371e-140">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="5371e-140">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="5371e-141">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="5371e-141">The specified icon is displayed on the gallery webpage for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="5371e-142">-LicenseUri</span></span>

<span data-ttu-id="5371e-143">Spécifie l’URL des termes du contrat de licence pour le module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="5371e-143">Specifies the URL of licensing terms for the module you want to publish.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-144">-Name</span><span class="sxs-lookup"><span data-stu-id="5371e-144">-Name</span></span>

<span data-ttu-id="5371e-145">Spécifie le nom du module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="5371e-145">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="5371e-146">`Publish-Module` recherche le nom de module spécifié dans `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="5371e-146">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-147">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="5371e-147">-NuGetApiKey</span></span>

<span data-ttu-id="5371e-148">Spécifie la clé API que vous souhaitez utiliser pour publier un module dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="5371e-148">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="5371e-149">La clé API fait partie de votre profil dans la galerie en ligne, et se trouve sur la page de votre compte d’utilisateur dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="5371e-149">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="5371e-150">La clé API est une fonctionnalité spécifique de NuGet.</span><span class="sxs-lookup"><span data-stu-id="5371e-150">The API key is NuGet-specific functionality.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-151">-Path</span><span class="sxs-lookup"><span data-stu-id="5371e-151">-Path</span></span>

<span data-ttu-id="5371e-152">Spécifie le chemin d’accès au module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="5371e-152">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="5371e-153">Ce paramètre accepte le chemin d’accès au dossier qui contient le module.</span><span class="sxs-lookup"><span data-stu-id="5371e-153">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-154">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="5371e-154">-ProjectUri</span></span>

<span data-ttu-id="5371e-155">Spécifie l’URL d’une page Web relative à ce projet.</span><span class="sxs-lookup"><span data-stu-id="5371e-155">Specifies the URL of a webpage about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-156">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="5371e-156">-ReleaseNotes</span></span>

<span data-ttu-id="5371e-157">Spécifie une chaîne contenant des notes de publication ou des commentaires que vous souhaitez mettre à la disposition des utilisateurs de cette version du module.</span><span class="sxs-lookup"><span data-stu-id="5371e-157">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-158">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="5371e-158">-Repository</span></span>

<span data-ttu-id="5371e-159">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="5371e-159">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="5371e-160">Le référentiel doit avoir un **PublishLocation**, qui est un URI NuGet valide.</span><span class="sxs-lookup"><span data-stu-id="5371e-160">The repository must have a **PublishLocation**, which is a valid NuGet URI.</span></span>
<span data-ttu-id="5371e-161">Le **PublishLocation** peut être défini en exécutant `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="5371e-161">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5371e-162">-RequiredVersion</span></span>

<span data-ttu-id="5371e-163">Spécifie la version exacte d’un module unique à publier.</span><span class="sxs-lookup"><span data-stu-id="5371e-163">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-164">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="5371e-164">-SkipAutomaticTags</span></span>

<span data-ttu-id="5371e-165">Supprime les commandes et les ressources d’être incluses en tant que balises.</span><span class="sxs-lookup"><span data-stu-id="5371e-165">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="5371e-166">Ignore l’ajout automatique de balises à un module.</span><span class="sxs-lookup"><span data-stu-id="5371e-166">Skips automatically adding tags to a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="5371e-167">-Tags</span></span>

<span data-ttu-id="5371e-168">Ajoute une ou plusieurs balises au module que vous publiez.</span><span class="sxs-lookup"><span data-stu-id="5371e-168">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="5371e-169">Exemples de balises : DesiredStateConfiguration, DSC, DSCResourceKit ou PSModule.</span><span class="sxs-lookup"><span data-stu-id="5371e-169">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="5371e-170">Séparez plusieurs balises par des virgules.</span><span class="sxs-lookup"><span data-stu-id="5371e-170">Separate multiple tags with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5371e-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5371e-171">-WhatIf</span></span>

<span data-ttu-id="5371e-172">Montre ce qui se passerait si le `Publish-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="5371e-172">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="5371e-173">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5371e-173">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5371e-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5371e-174">CommonParameters</span></span>

<span data-ttu-id="5371e-175">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5371e-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5371e-176">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5371e-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5371e-177">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5371e-177">INPUTS</span></span>

### <span data-ttu-id="5371e-178">System.String</span><span class="sxs-lookup"><span data-stu-id="5371e-178">System.String</span></span>

### <span data-ttu-id="5371e-179">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="5371e-179">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="5371e-180">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5371e-180">OUTPUTS</span></span>

### <span data-ttu-id="5371e-181">System.Object</span><span class="sxs-lookup"><span data-stu-id="5371e-181">System.Object</span></span>

## <span data-ttu-id="5371e-182">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5371e-182">NOTES</span></span>

<span data-ttu-id="5371e-183">`Publish-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="5371e-183">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5371e-184">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="5371e-184">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5371e-185">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="5371e-185">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5371e-186">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="5371e-186">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5371e-187">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5371e-187">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="5371e-188">La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="5371e-188">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="5371e-189">Les métadonnées requises incluent le nom du module, la version, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="5371e-189">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="5371e-190">La plupart des métadonnées proviennent du manifeste de module, mais certaines métadonnées peuvent être spécifiées dans des `Publish-Module` paramètres, tels que **tag**, **ReleaseNote**, **iconUri**, **ProjectUri** et **LicenseUri**.</span><span class="sxs-lookup"><span data-stu-id="5371e-190">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**.</span></span> <span data-ttu-id="5371e-191">Pour plus d’informations, consultez [valeurs de manifeste du package qui ont un impact sur l’interface utilisateur PowerShell Gallery](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span><span class="sxs-lookup"><span data-stu-id="5371e-191">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="5371e-192">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5371e-192">RELATED LINKS</span></span>

[<span data-ttu-id="5371e-193">Find-Module</span><span class="sxs-lookup"><span data-stu-id="5371e-193">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="5371e-194">Install-Module</span><span class="sxs-lookup"><span data-stu-id="5371e-194">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="5371e-195">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5371e-195">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="5371e-196">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5371e-196">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="5371e-197">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="5371e-197">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="5371e-198">Update-Module</span><span class="sxs-lookup"><span data-stu-id="5371e-198">Update-Module</span></span>](Update-Module.md)

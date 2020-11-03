---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 50f873e6691ead7c220b6250458f4fdf8a90af22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203905"
---
# <span data-ttu-id="600c8-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="600c8-103">Publish-Module</span></span>

## <span data-ttu-id="600c8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="600c8-104">SYNOPSIS</span></span>
<span data-ttu-id="600c8-105">Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="600c8-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="600c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="600c8-106">SYNTAX</span></span>

### <span data-ttu-id="600c8-107">ModuleNameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="600c8-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="600c8-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="600c8-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="600c8-109">Description</span><span class="sxs-lookup"><span data-stu-id="600c8-109">DESCRIPTION</span></span>

<span data-ttu-id="600c8-110">L' `Publish-Module` applet de commande publie un module dans une galerie en ligne NuGet à l’aide d’une clé API, stockée en tant que partie du profil d’un utilisateur dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="600c8-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="600c8-111">Vous pouvez indiquer le module à publier par son nom ou par le chemin d’accès au dossier le contenant.</span><span class="sxs-lookup"><span data-stu-id="600c8-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="600c8-112">Lorsque vous spécifiez un module par son nom, `Publish-Module` publie le premier module qui serait trouvé en exécutant `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="600c8-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="600c8-113">Si vous spécifiez une version minimale d’un module à publier, `Publish-Module` publie le premier module avec une version qui est supérieure ou égale à la version minimale que vous avez spécifiée.</span><span class="sxs-lookup"><span data-stu-id="600c8-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="600c8-114">La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="600c8-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="600c8-115">Les métadonnées requises incluent le nom du module, la version, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="600c8-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="600c8-116">Bien que la plupart des métadonnées proviennent du manifeste de module, certaines métadonnées doivent être spécifiées dans des `Publish-Module` paramètres tels que **tag** , **ReleaseNote** , **iconUri** , **ProjectUri** et **LicenseUri** , car ces paramètres correspondent aux champs d’une galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="600c8-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** , because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="600c8-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="600c8-117">EXAMPLES</span></span>

### <span data-ttu-id="600c8-118">Exemple 1 : publier un module</span><span class="sxs-lookup"><span data-stu-id="600c8-118">Example 1: Publish a module</span></span>

<span data-ttu-id="600c8-119">Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la galerie en ligne du propriétaire du module.</span><span class="sxs-lookup"><span data-stu-id="600c8-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="600c8-120">Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="600c8-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="600c8-121">Exemple 2 : publier un module avec les métadonnées de la Galerie</span><span class="sxs-lookup"><span data-stu-id="600c8-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="600c8-122">Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la Galerie du propriétaire du module.</span><span class="sxs-lookup"><span data-stu-id="600c8-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="600c8-123">Les métadonnées supplémentaires fournies sont affichées sur la page Web du module dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="600c8-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="600c8-124">Le propriétaire ajoute deux balises de recherche pour le module, en les associant à Active Directory ; une brève note de publication est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="600c8-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="600c8-125">Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="600c8-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="600c8-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="600c8-126">PARAMETERS</span></span>

### <span data-ttu-id="600c8-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="600c8-127">-AllowPrerelease</span></span>

<span data-ttu-id="600c8-128">Autorise la publication des modules marqués comme préversion.</span><span class="sxs-lookup"><span data-stu-id="600c8-128">Allows modules marked as prerelease to be published.</span></span>

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

### <span data-ttu-id="600c8-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="600c8-129">-Confirm</span></span>

<span data-ttu-id="600c8-130">Vous invite à confirmer l’exécution de l' `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="600c8-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="600c8-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="600c8-131">-Credential</span></span>

<span data-ttu-id="600c8-132">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour publier un module pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="600c8-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="600c8-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="600c8-133">-Exclude</span></span>

<span data-ttu-id="600c8-134">Définit les fichiers à exclure du module publié.</span><span class="sxs-lookup"><span data-stu-id="600c8-134">Defines files to exclude from the published module.</span></span> <span data-ttu-id="600c8-135">La prise en charge des paramètres **Exclude** est ajoutée à **PowershellGet** version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="600c8-135">**Exclude** parameter support is add in **PowershellGet** version 2.0.0.</span></span>

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

### <span data-ttu-id="600c8-136">-Force</span><span class="sxs-lookup"><span data-stu-id="600c8-136">-Force</span></span>

<span data-ttu-id="600c8-137">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="600c8-137">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="600c8-138">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="600c8-138">-FormatVersion</span></span>

<span data-ttu-id="600c8-139">Accepte uniquement les valeurs valides spécifiées par l’attribut **ValidateSet** .</span><span class="sxs-lookup"><span data-stu-id="600c8-139">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="600c8-140">Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) et [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span><span class="sxs-lookup"><span data-stu-id="600c8-140">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

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

### <span data-ttu-id="600c8-141">-IconUri</span><span class="sxs-lookup"><span data-stu-id="600c8-141">-IconUri</span></span>

<span data-ttu-id="600c8-142">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="600c8-142">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="600c8-143">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="600c8-143">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="600c8-144">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="600c8-144">-LicenseUri</span></span>

<span data-ttu-id="600c8-145">Spécifie l’URL des termes du contrat de licence pour le module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="600c8-145">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="600c8-146">-Name</span><span class="sxs-lookup"><span data-stu-id="600c8-146">-Name</span></span>

<span data-ttu-id="600c8-147">Spécifie le nom du module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="600c8-147">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="600c8-148">`Publish-Module` recherche le nom de module spécifié dans `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="600c8-148">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

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

### <span data-ttu-id="600c8-149">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="600c8-149">-NuGetApiKey</span></span>

<span data-ttu-id="600c8-150">Spécifie la clé API que vous souhaitez utiliser pour publier un module dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="600c8-150">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="600c8-151">La clé API fait partie de votre profil dans la galerie en ligne, et se trouve sur la page de votre compte d’utilisateur dans la Galerie.</span><span class="sxs-lookup"><span data-stu-id="600c8-151">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="600c8-152">La clé API est une fonctionnalité spécifique de NuGet.</span><span class="sxs-lookup"><span data-stu-id="600c8-152">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="600c8-153">-Path</span><span class="sxs-lookup"><span data-stu-id="600c8-153">-Path</span></span>

<span data-ttu-id="600c8-154">Spécifie le chemin d’accès au module que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="600c8-154">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="600c8-155">Ce paramètre accepte le chemin d’accès au dossier qui contient le module.</span><span class="sxs-lookup"><span data-stu-id="600c8-155">This parameter accepts the path to the folder that contains the module.</span></span>

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

### <span data-ttu-id="600c8-156">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="600c8-156">-ProjectUri</span></span>

<span data-ttu-id="600c8-157">Spécifie l’URL d’une page Web relative à ce projet.</span><span class="sxs-lookup"><span data-stu-id="600c8-157">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="600c8-158">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="600c8-158">-ReleaseNotes</span></span>

<span data-ttu-id="600c8-159">Spécifie une chaîne contenant des notes de publication ou des commentaires que vous souhaitez mettre à la disposition des utilisateurs de cette version du module.</span><span class="sxs-lookup"><span data-stu-id="600c8-159">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

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

### <span data-ttu-id="600c8-160">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="600c8-160">-Repository</span></span>

<span data-ttu-id="600c8-161">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="600c8-161">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="600c8-162">Le référentiel doit avoir un **PublishLocation** , qui est un URI NuGet valide.</span><span class="sxs-lookup"><span data-stu-id="600c8-162">The repository must have a **PublishLocation** , which is a valid NuGet URI.</span></span>
<span data-ttu-id="600c8-163">Le **PublishLocation** peut être défini en exécutant `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="600c8-163">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="600c8-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="600c8-164">-RequiredVersion</span></span>

<span data-ttu-id="600c8-165">Spécifie la version exacte d’un module unique à publier.</span><span class="sxs-lookup"><span data-stu-id="600c8-165">Specifies the exact version of a single module to publish.</span></span>

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

### <span data-ttu-id="600c8-166">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="600c8-166">-SkipAutomaticTags</span></span>

<span data-ttu-id="600c8-167">Supprime les commandes et les ressources d’être incluses en tant que balises.</span><span class="sxs-lookup"><span data-stu-id="600c8-167">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="600c8-168">Ignore l’ajout automatique de balises à un module.</span><span class="sxs-lookup"><span data-stu-id="600c8-168">Skips automatically adding tags to a module.</span></span> <span data-ttu-id="600c8-169">La prise en charge des paramètres **SkipAutomaticTags** est ajoutée à **PowerShellGet** version 2.0.0</span><span class="sxs-lookup"><span data-stu-id="600c8-169">**SkipAutomaticTags** parameter support is added in **PowerShellGet** version 2.0.0</span></span>

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

### <span data-ttu-id="600c8-170">-Tags</span><span class="sxs-lookup"><span data-stu-id="600c8-170">-Tags</span></span>

<span data-ttu-id="600c8-171">Ajoute une ou plusieurs balises au module que vous publiez.</span><span class="sxs-lookup"><span data-stu-id="600c8-171">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="600c8-172">Exemples de balises : DesiredStateConfiguration, DSC, DSCResourceKit ou PSModule.</span><span class="sxs-lookup"><span data-stu-id="600c8-172">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="600c8-173">Séparez plusieurs balises par des virgules.</span><span class="sxs-lookup"><span data-stu-id="600c8-173">Separate multiple tags with commas.</span></span>

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

### <span data-ttu-id="600c8-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="600c8-174">-WhatIf</span></span>

<span data-ttu-id="600c8-175">Montre ce qui se passerait si le `Publish-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="600c8-175">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="600c8-176">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="600c8-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="600c8-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="600c8-177">CommonParameters</span></span>

<span data-ttu-id="600c8-178">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="600c8-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="600c8-179">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="600c8-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="600c8-180">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="600c8-180">INPUTS</span></span>

### <span data-ttu-id="600c8-181">System.String</span><span class="sxs-lookup"><span data-stu-id="600c8-181">System.String</span></span>

### <span data-ttu-id="600c8-182">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="600c8-182">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="600c8-183">SORTIES</span><span class="sxs-lookup"><span data-stu-id="600c8-183">OUTPUTS</span></span>

### <span data-ttu-id="600c8-184">System.Object</span><span class="sxs-lookup"><span data-stu-id="600c8-184">System.Object</span></span>

## <span data-ttu-id="600c8-185">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="600c8-185">NOTES</span></span>

<span data-ttu-id="600c8-186">`Publish-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="600c8-186">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="600c8-187">La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="600c8-187">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="600c8-188">Les métadonnées requises incluent le nom du module, la version, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="600c8-188">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="600c8-189">La plupart des métadonnées proviennent du manifeste de module, mais certaines métadonnées peuvent être spécifiées dans des `Publish-Module` paramètres, tels que **tag** , **ReleaseNote** , **iconUri** , **ProjectUri** et **LicenseUri** .</span><span class="sxs-lookup"><span data-stu-id="600c8-189">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** .</span></span> <span data-ttu-id="600c8-190">Pour plus d’informations, consultez [valeurs de manifeste du package qui ont un impact sur l’interface utilisateur PowerShell Gallery](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span><span class="sxs-lookup"><span data-stu-id="600c8-190">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="600c8-191">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="600c8-191">RELATED LINKS</span></span>

[<span data-ttu-id="600c8-192">Find-Module</span><span class="sxs-lookup"><span data-stu-id="600c8-192">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="600c8-193">Install-Module</span><span class="sxs-lookup"><span data-stu-id="600c8-193">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="600c8-194">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="600c8-194">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="600c8-195">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="600c8-195">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="600c8-196">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="600c8-196">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="600c8-197">Update-Module</span><span class="sxs-lookup"><span data-stu-id="600c8-197">Update-Module</span></span>](Update-Module.md)

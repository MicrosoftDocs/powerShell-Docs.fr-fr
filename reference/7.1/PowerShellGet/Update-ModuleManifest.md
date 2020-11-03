---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 2977992a04e5a94f5124ec85abd980dc3d4f129f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204950"
---
# <span data-ttu-id="eec26-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="eec26-103">Update-ModuleManifest</span></span>

## <span data-ttu-id="eec26-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="eec26-104">SYNOPSIS</span></span>
<span data-ttu-id="eec26-105">Met à jour un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="eec26-105">Updates a module manifest file.</span></span>

## <span data-ttu-id="eec26-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eec26-106">SYNTAX</span></span>

### <span data-ttu-id="eec26-107">Tous</span><span class="sxs-lookup"><span data-stu-id="eec26-107">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="eec26-108">Description</span><span class="sxs-lookup"><span data-stu-id="eec26-108">DESCRIPTION</span></span>

<span data-ttu-id="eec26-109">L' `Update-ModuleManifest` applet de commande met à jour un fichier manifeste de module ( `.psd1` ).</span><span class="sxs-lookup"><span data-stu-id="eec26-109">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="eec26-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="eec26-110">EXAMPLES</span></span>

### <span data-ttu-id="eec26-111">Exemple 1 : mettre à jour un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="eec26-111">Example 1: Update a module manifest</span></span>

<span data-ttu-id="eec26-112">Cet exemple met à jour un fichier manifeste de module existant.</span><span class="sxs-lookup"><span data-stu-id="eec26-112">This example updates an existing module manifest file.</span></span> <span data-ttu-id="eec26-113">La projection est utilisée pour passer des valeurs de paramètre à `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="eec26-113">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="eec26-114">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="eec26-114">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="eec26-115">`$Parms` est un se terminant par qui stocke les valeurs de paramètre pour **path** , **Author** , **CompanyName** et **Copyright** .</span><span class="sxs-lookup"><span data-stu-id="eec26-115">`$Parms` is a splat that stores the parameter values for **Path** , **Author** , **CompanyName** , and **Copyright** .</span></span> <span data-ttu-id="eec26-116">`Update-ModuleManifest` Obtient les valeurs de paramètre à partir de `@Parms` et met à jour le manifeste de module, **TestManifest.psd1** .</span><span class="sxs-lookup"><span data-stu-id="eec26-116">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1** .</span></span>

## <span data-ttu-id="eec26-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eec26-117">PARAMETERS</span></span>

### <span data-ttu-id="eec26-118">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="eec26-118">-AliasesToExport</span></span>

<span data-ttu-id="eec26-119">Spécifie les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-119">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="eec26-120">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-120">Wildcards are permitted.</span></span>

<span data-ttu-id="eec26-121">Utilisez ce paramètre pour limiter les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-121">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="eec26-122">**AliasesToExport** peut supprimer des alias de la liste des alias exportés, mais il ne peut pas ajouter d’alias à la liste.</span><span class="sxs-lookup"><span data-stu-id="eec26-122">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eec26-123">-Auteur</span><span class="sxs-lookup"><span data-stu-id="eec26-123">-Author</span></span>

<span data-ttu-id="eec26-124">Spécifie l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-124">Specifies the module author.</span></span>

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

### <span data-ttu-id="eec26-125">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="eec26-125">-ClrVersion</span></span>

<span data-ttu-id="eec26-126">Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="eec26-126">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-127">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="eec26-127">-CmdletsToExport</span></span>

<span data-ttu-id="eec26-128">Spécifie les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-128">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="eec26-129">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-129">Wildcards are permitted.</span></span>

<span data-ttu-id="eec26-130">Utilisez ce paramètre pour limiter les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-130">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="eec26-131">**CmdletsToExport** peut supprimer des applets de commande de la liste des applets de commande exportées, mais il ne peut pas ajouter d’applets de commande à la liste.</span><span class="sxs-lookup"><span data-stu-id="eec26-131">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eec26-132">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="eec26-132">-CompanyName</span></span>

<span data-ttu-id="eec26-133">Spécifie la société ou le fournisseur qui a créé le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-133">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="eec26-134">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="eec26-134">-CompatiblePSEditions</span></span>

<span data-ttu-id="eec26-135">Spécifie le **des éditions PS** compatible du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-135">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="eec26-136">Pour plus d’informations sur **PSEdition** , consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="eec26-136">For information about **PSEdition** , see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eec26-137">-Confirm</span></span>

<span data-ttu-id="eec26-138">Vous invite à confirmer l’exécution `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="eec26-138">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="eec26-139">-Copyright</span><span class="sxs-lookup"><span data-stu-id="eec26-139">-Copyright</span></span>

<span data-ttu-id="eec26-140">Spécifie une déclaration de copyright pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-140">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="eec26-141">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="eec26-141">-DefaultCommandPrefix</span></span>

<span data-ttu-id="eec26-142">Spécifie le préfixe de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="eec26-142">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="eec26-143">Description</span><span class="sxs-lookup"><span data-stu-id="eec26-143">-Description</span></span>

<span data-ttu-id="eec26-144">Spécifie une description du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-144">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="eec26-145">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="eec26-145">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="eec26-146">Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="eec26-146">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-147">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="eec26-147">-DscResourcesToExport</span></span>

<span data-ttu-id="eec26-148">Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-148">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="eec26-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="eec26-150">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="eec26-150">-ExternalModuleDependencies</span></span>

<span data-ttu-id="eec26-151">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="eec26-151">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="eec26-152">-FileList</span><span class="sxs-lookup"><span data-stu-id="eec26-152">-FileList</span></span>

<span data-ttu-id="eec26-153">Spécifie tous les éléments qui sont inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-153">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="eec26-154">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="eec26-154">-FormatsToProcess</span></span>

<span data-ttu-id="eec26-155">Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-155">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="eec26-156">Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="eec26-156">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="eec26-157">Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="eec26-157">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="eec26-158">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="eec26-158">-FunctionsToExport</span></span>

<span data-ttu-id="eec26-159">Spécifie les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-159">Specifies the functions that the module exports.</span></span> <span data-ttu-id="eec26-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-160">Wildcards are permitted.</span></span>

<span data-ttu-id="eec26-161">Utilisez ce paramètre pour limiter les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-161">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="eec26-162">**FunctionsToExport** peut supprimer des fonctions de la liste des alias exportés, mais il ne peut pas ajouter de fonctions à la liste.</span><span class="sxs-lookup"><span data-stu-id="eec26-162">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eec26-163">-Guid</span><span class="sxs-lookup"><span data-stu-id="eec26-163">-Guid</span></span>

<span data-ttu-id="eec26-164">Spécifie un identificateur unique pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-164">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="eec26-165">Le GUID peut servir à distinguer les modules portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="eec26-165">The GUID can be used to distinguish among modules with the same name.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-166">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="eec26-166">-HelpInfoUri</span></span>

<span data-ttu-id="eec26-167">Spécifie l’adresse Internet du fichier **XML HelpInfo** du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-167">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="eec26-168">Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https** .</span><span class="sxs-lookup"><span data-stu-id="eec26-168">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https** .</span></span>

<span data-ttu-id="eec26-169">Le fichier **XML HelpInfo** prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="eec26-169">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="eec26-170">Elle contient des informations sur l’emplacement des fichiers d’aide téléchargeables du module et les numéros de version des fichiers d’aide les plus récents pour chaque paramètre régional pris en charge.</span><span class="sxs-lookup"><span data-stu-id="eec26-170">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="eec26-171">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="eec26-171">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="eec26-172">Pour plus d’informations sur le fichier **XML HelpInfo** , consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="eec26-172">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="eec26-173">-IconUri</span><span class="sxs-lookup"><span data-stu-id="eec26-173">-IconUri</span></span>

<span data-ttu-id="eec26-174">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-174">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="eec26-175">L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-175">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="eec26-176">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="eec26-176">-LicenseUri</span></span>

<span data-ttu-id="eec26-177">Spécifie l’URL des termes du contrat de licence pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-177">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="eec26-178">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="eec26-178">-ModuleList</span></span>

<span data-ttu-id="eec26-179">Spécifie un tableau de modules inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-179">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="eec26-180">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="eec26-180">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="eec26-181">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="eec26-181">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="eec26-182">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec26-182">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="eec26-183">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="eec26-183">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="eec26-184">Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.</span><span class="sxs-lookup"><span data-stu-id="eec26-184">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-185">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="eec26-185">-ModuleVersion</span></span>

<span data-ttu-id="eec26-186">Spécifie la version du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-186">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-187">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="eec26-187">-NestedModules</span></span>

<span data-ttu-id="eec26-188">Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-188">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="eec26-189">Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="eec26-189">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="eec26-190">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="eec26-190">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="eec26-191">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="eec26-191">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="eec26-192">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec26-192">You can combine strings and hash tables in the parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-193">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="eec26-193">-PackageManagementProviders</span></span>

<span data-ttu-id="eec26-194">Spécifie un tableau de fournisseurs de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="eec26-194">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="eec26-195">-PassThru</span><span class="sxs-lookup"><span data-stu-id="eec26-195">-PassThru</span></span>

<span data-ttu-id="eec26-196">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="eec26-196">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="eec26-197">Par défaut, `Update-ModuleManifest` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="eec26-197">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="eec26-198">-Path</span><span class="sxs-lookup"><span data-stu-id="eec26-198">-Path</span></span>

<span data-ttu-id="eec26-199">Spécifie le chemin d’accès et le nom de fichier du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="eec26-199">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="eec26-200">Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="eec26-200">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="eec26-201">Si vous spécifiez le chemin d’accès à un fichier existant, `Update-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="eec26-201">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="eec26-202">Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension.</span><span class="sxs-lookup"><span data-stu-id="eec26-202">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="eec26-203">Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="eec26-203">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="eec26-204">Pour utiliser une variable, incluez le paramètre **Path** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="eec26-204">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-205">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="eec26-205">-PowerShellHostName</span></span>

<span data-ttu-id="eec26-206">Spécifie le nom du programme hôte PowerShell requis par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-206">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="eec26-207">Entrez le nom du programme hôte, tel que hôte ISE PowerShell ou ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="eec26-207">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="eec26-208">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-208">Wildcards aren't permitted.</span></span>

<span data-ttu-id="eec26-209">Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="eec26-209">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="eec26-210">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="eec26-210">-PowerShellHostVersion</span></span>

<span data-ttu-id="eec26-211">Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-211">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="eec26-212">Entrez un numéro de version, par exemple 1.1.</span><span class="sxs-lookup"><span data-stu-id="eec26-212">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-213">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="eec26-213">-PowerShellVersion</span></span>

<span data-ttu-id="eec26-214">Spécifie la version minimale de PowerShell qui fonctionnera avec ce module.</span><span class="sxs-lookup"><span data-stu-id="eec26-214">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="eec26-215">Par exemple, vous pouvez spécifier 3,0, 4,0 ou 5,0 comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec26-215">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-216">-Version préliminaire</span><span class="sxs-lookup"><span data-stu-id="eec26-216">-Prerelease</span></span>

<span data-ttu-id="eec26-217">Indique que le module est en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="eec26-217">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="eec26-218">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="eec26-218">-PrivateData</span></span>

<span data-ttu-id="eec26-219">Spécifie les données qui sont passées au module lors de son importation.</span><span class="sxs-lookup"><span data-stu-id="eec26-219">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-220">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="eec26-220">-ProcessorArchitecture</span></span>

<span data-ttu-id="eec26-221">Spécifie l'architecture de processeur dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="eec26-221">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="eec26-222">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="eec26-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eec26-223">Amd64</span><span class="sxs-lookup"><span data-stu-id="eec26-223">Amd64</span></span>
- <span data-ttu-id="eec26-224">Arm</span><span class="sxs-lookup"><span data-stu-id="eec26-224">Arm</span></span>
- <span data-ttu-id="eec26-225">IA64</span><span class="sxs-lookup"><span data-stu-id="eec26-225">IA64</span></span>
- <span data-ttu-id="eec26-226">MSIL</span><span class="sxs-lookup"><span data-stu-id="eec26-226">MSIL</span></span>
- <span data-ttu-id="eec26-227">Aucun (inconnu ou non spécifié)</span><span class="sxs-lookup"><span data-stu-id="eec26-227">None (unknown or unspecified)</span></span>
- <span data-ttu-id="eec26-228">X86</span><span class="sxs-lookup"><span data-stu-id="eec26-228">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-229">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="eec26-229">-ProjectUri</span></span>

<span data-ttu-id="eec26-230">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="eec26-230">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="eec26-231">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="eec26-231">-ReleaseNotes</span></span>

<span data-ttu-id="eec26-232">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez voir disponibles pour cette version du script.</span><span class="sxs-lookup"><span data-stu-id="eec26-232">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="eec26-233">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="eec26-233">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="eec26-234">Spécifie qu’une acceptation de licence est requise pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-234">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="eec26-235">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="eec26-235">-RequiredAssemblies</span></span>

<span data-ttu-id="eec26-236">Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="eec26-236">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="eec26-237">Entrez les noms de fichiers d'assembly.</span><span class="sxs-lookup"><span data-stu-id="eec26-237">Enter the assembly file names.</span></span>
<span data-ttu-id="eec26-238">PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="eec26-238">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="eec26-239">Utilisez ce paramètre pour spécifier tous les assemblys requis par le module, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess** , même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="eec26-239">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="eec26-240">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="eec26-240">-RequiredModules</span></span>

<span data-ttu-id="eec26-241">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="eec26-241">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="eec26-242">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="eec26-242">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="eec26-243">Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="eec26-243">If the required modules aren't available, the `Import-Module` command fails.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec26-244">-RootModule</span><span class="sxs-lookup"><span data-stu-id="eec26-244">-RootModule</span></span>

<span data-ttu-id="eec26-245">Spécifie le fichier principal ou racine du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-245">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="eec26-246">Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="eec26-246">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="eec26-247">Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="eec26-247">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="eec26-248">Si un module a un fichier manifeste et qu’aucun fichier racine n’a été spécifié dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-248">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="eec26-249">Et, le module devient un module de manifeste (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="eec26-249">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="eec26-250">Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="eec26-250">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="eec26-251">Dans le cas contraire, leurs membres ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="eec26-251">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="eec26-252">Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess** .</span><span class="sxs-lookup"><span data-stu-id="eec26-252">In PowerShell 2.0, this key was called **ModuleToProcess** .</span></span>

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

### <span data-ttu-id="eec26-253">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="eec26-253">-ScriptsToProcess</span></span>

<span data-ttu-id="eec26-254">Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-254">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="eec26-255">Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.</span><span class="sxs-lookup"><span data-stu-id="eec26-255">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="eec26-256">Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="eec26-256">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="eec26-257">-Tags</span><span class="sxs-lookup"><span data-stu-id="eec26-257">-Tags</span></span>

<span data-ttu-id="eec26-258">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="eec26-258">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="eec26-259">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="eec26-259">-TypesToProcess</span></span>

<span data-ttu-id="eec26-260">Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="eec26-260">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="eec26-261">Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="eec26-261">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="eec26-262">Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="eec26-262">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="eec26-263">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="eec26-263">-VariablesToExport</span></span>

<span data-ttu-id="eec26-264">Spécifie les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-264">Specifies the variables that the module exports.</span></span> <span data-ttu-id="eec26-265">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eec26-265">Wildcards are permitted.</span></span>

<span data-ttu-id="eec26-266">Utilisez ce paramètre pour limiter les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="eec26-266">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="eec26-267">**VariablesToExport** peut supprimer des variables de la liste des variables exportées, mais il ne peut pas ajouter de variables à la liste.</span><span class="sxs-lookup"><span data-stu-id="eec26-267">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eec26-268">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eec26-268">-WhatIf</span></span>

<span data-ttu-id="eec26-269">Montre ce qui se passe si `Update-ModuleManifest` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="eec26-269">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="eec26-270">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="eec26-270">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="eec26-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eec26-271">CommonParameters</span></span>

<span data-ttu-id="eec26-272">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eec26-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eec26-273">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eec26-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eec26-274">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="eec26-274">INPUTS</span></span>

### <span data-ttu-id="eec26-275">System.String</span><span class="sxs-lookup"><span data-stu-id="eec26-275">System.String</span></span>

## <span data-ttu-id="eec26-276">SORTIES</span><span class="sxs-lookup"><span data-stu-id="eec26-276">OUTPUTS</span></span>

### <span data-ttu-id="eec26-277">System.Object</span><span class="sxs-lookup"><span data-stu-id="eec26-277">System.Object</span></span>

## <span data-ttu-id="eec26-278">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="eec26-278">NOTES</span></span>

## <span data-ttu-id="eec26-279">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="eec26-279">RELATED LINKS</span></span>

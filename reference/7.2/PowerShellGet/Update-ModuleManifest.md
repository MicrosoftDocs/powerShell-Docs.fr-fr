---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 4f00450257178cac72d03303358150fd9f5cd26b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597746"
---
# <span data-ttu-id="09d6d-102">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="09d6d-102">Update-ModuleManifest</span></span>

## <span data-ttu-id="09d6d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="09d6d-103">SYNOPSIS</span></span>
<span data-ttu-id="09d6d-104">Met à jour un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-104">Updates a module manifest file.</span></span>

## <span data-ttu-id="09d6d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="09d6d-105">SYNTAX</span></span>

### <span data-ttu-id="09d6d-106">Tous</span><span class="sxs-lookup"><span data-stu-id="09d6d-106">All</span></span>

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

## <span data-ttu-id="09d6d-107">Description</span><span class="sxs-lookup"><span data-stu-id="09d6d-107">DESCRIPTION</span></span>

<span data-ttu-id="09d6d-108">L' `Update-ModuleManifest` applet de commande met à jour un fichier manifeste de module ( `.psd1` ).</span><span class="sxs-lookup"><span data-stu-id="09d6d-108">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="09d6d-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="09d6d-109">EXAMPLES</span></span>

### <span data-ttu-id="09d6d-110">Exemple 1 : mettre à jour un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="09d6d-110">Example 1: Update a module manifest</span></span>

<span data-ttu-id="09d6d-111">Cet exemple met à jour un fichier manifeste de module existant.</span><span class="sxs-lookup"><span data-stu-id="09d6d-111">This example updates an existing module manifest file.</span></span> <span data-ttu-id="09d6d-112">La projection est utilisée pour passer des valeurs de paramètre à `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="09d6d-112">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="09d6d-113">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="09d6d-113">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="09d6d-114">`$Parms` est un se terminant par qui stocke les valeurs de paramètre pour **path**, **Author**, **CompanyName** et **Copyright**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-114">`$Parms` is a splat that stores the parameter values for **Path**, **Author**, **CompanyName**, and **Copyright**.</span></span> <span data-ttu-id="09d6d-115">`Update-ModuleManifest` Obtient les valeurs de paramètre à partir de `@Parms` et met à jour le manifeste de module, **TestManifest.psd1**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-115">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="09d6d-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09d6d-116">PARAMETERS</span></span>

### <span data-ttu-id="09d6d-117">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="09d6d-117">-AliasesToExport</span></span>

<span data-ttu-id="09d6d-118">Spécifie les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-118">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="09d6d-119">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-119">Wildcards are permitted.</span></span>

<span data-ttu-id="09d6d-120">Utilisez ce paramètre pour limiter les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-120">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="09d6d-121">**AliasesToExport** peut supprimer des alias de la liste des alias exportés, mais il ne peut pas ajouter d’alias à la liste.</span><span class="sxs-lookup"><span data-stu-id="09d6d-121">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

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

### <span data-ttu-id="09d6d-122">-Auteur</span><span class="sxs-lookup"><span data-stu-id="09d6d-122">-Author</span></span>

<span data-ttu-id="09d6d-123">Spécifie l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-123">Specifies the module author.</span></span>

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

### <span data-ttu-id="09d6d-124">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="09d6d-124">-ClrVersion</span></span>

<span data-ttu-id="09d6d-125">Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="09d6d-125">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="09d6d-126">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="09d6d-126">-CmdletsToExport</span></span>

<span data-ttu-id="09d6d-127">Spécifie les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-127">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="09d6d-128">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-128">Wildcards are permitted.</span></span>

<span data-ttu-id="09d6d-129">Utilisez ce paramètre pour limiter les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-129">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="09d6d-130">**CmdletsToExport** peut supprimer des applets de commande de la liste des applets de commande exportées, mais il ne peut pas ajouter d’applets de commande à la liste.</span><span class="sxs-lookup"><span data-stu-id="09d6d-130">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

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

### <span data-ttu-id="09d6d-131">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="09d6d-131">-CompanyName</span></span>

<span data-ttu-id="09d6d-132">Spécifie la société ou le fournisseur qui a créé le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-132">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="09d6d-133">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="09d6d-133">-CompatiblePSEditions</span></span>

<span data-ttu-id="09d6d-134">Spécifie le **des éditions PS** compatible du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-134">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="09d6d-135">Pour plus d’informations sur **PSEdition**, consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="09d6d-135">For information about **PSEdition**, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="09d6d-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="09d6d-136">-Confirm</span></span>

<span data-ttu-id="09d6d-137">Vous invite à confirmer l’exécution `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="09d6d-137">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="09d6d-138">-Copyright</span><span class="sxs-lookup"><span data-stu-id="09d6d-138">-Copyright</span></span>

<span data-ttu-id="09d6d-139">Spécifie une déclaration de copyright pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-139">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="09d6d-140">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="09d6d-140">-DefaultCommandPrefix</span></span>

<span data-ttu-id="09d6d-141">Spécifie le préfixe de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="09d6d-141">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="09d6d-142">Description</span><span class="sxs-lookup"><span data-stu-id="09d6d-142">-Description</span></span>

<span data-ttu-id="09d6d-143">Spécifie une description du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-143">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="09d6d-144">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="09d6d-144">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="09d6d-145">Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="09d6d-145">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="09d6d-146">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="09d6d-146">-DscResourcesToExport</span></span>

<span data-ttu-id="09d6d-147">Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-147">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="09d6d-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="09d6d-149">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="09d6d-149">-ExternalModuleDependencies</span></span>

<span data-ttu-id="09d6d-150">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="09d6d-150">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="09d6d-151">-FileList</span><span class="sxs-lookup"><span data-stu-id="09d6d-151">-FileList</span></span>

<span data-ttu-id="09d6d-152">Spécifie tous les éléments qui sont inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-152">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="09d6d-153">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="09d6d-153">-FormatsToProcess</span></span>

<span data-ttu-id="09d6d-154">Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-154">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="09d6d-155">Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-155">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="09d6d-156">Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="09d6d-156">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="09d6d-157">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="09d6d-157">-FunctionsToExport</span></span>

<span data-ttu-id="09d6d-158">Spécifie les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-158">Specifies the functions that the module exports.</span></span> <span data-ttu-id="09d6d-159">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-159">Wildcards are permitted.</span></span>

<span data-ttu-id="09d6d-160">Utilisez ce paramètre pour limiter les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-160">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="09d6d-161">**FunctionsToExport** peut supprimer des fonctions de la liste des alias exportés, mais il ne peut pas ajouter de fonctions à la liste.</span><span class="sxs-lookup"><span data-stu-id="09d6d-161">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

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

### <span data-ttu-id="09d6d-162">-Guid</span><span class="sxs-lookup"><span data-stu-id="09d6d-162">-Guid</span></span>

<span data-ttu-id="09d6d-163">Spécifie un identificateur unique pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-163">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="09d6d-164">Le GUID peut servir à distinguer les modules portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="09d6d-164">The GUID can be used to distinguish among modules with the same name.</span></span>

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

### <span data-ttu-id="09d6d-165">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="09d6d-165">-HelpInfoUri</span></span>

<span data-ttu-id="09d6d-166">Spécifie l’adresse Internet du fichier **XML HelpInfo** du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-166">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="09d6d-167">Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-167">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="09d6d-168">Le fichier **XML HelpInfo** prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="09d6d-168">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="09d6d-169">Elle contient des informations sur l’emplacement des fichiers d’aide téléchargeables du module et les numéros de version des fichiers d’aide les plus récents pour chaque paramètre régional pris en charge.</span><span class="sxs-lookup"><span data-stu-id="09d6d-169">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="09d6d-170">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="09d6d-170">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="09d6d-171">Pour plus d’informations sur le fichier **XML HelpInfo** , consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="09d6d-171">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="09d6d-172">-IconUri</span><span class="sxs-lookup"><span data-stu-id="09d6d-172">-IconUri</span></span>

<span data-ttu-id="09d6d-173">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-173">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="09d6d-174">L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-174">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="09d6d-175">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="09d6d-175">-LicenseUri</span></span>

<span data-ttu-id="09d6d-176">Spécifie l’URL des termes du contrat de licence pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-176">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="09d6d-177">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="09d6d-177">-ModuleList</span></span>

<span data-ttu-id="09d6d-178">Spécifie un tableau de modules inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-178">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="09d6d-179">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-179">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="09d6d-180">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="09d6d-180">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="09d6d-181">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="09d6d-181">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="09d6d-182">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-182">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="09d6d-183">Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.</span><span class="sxs-lookup"><span data-stu-id="09d6d-183">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="09d6d-184">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="09d6d-184">-ModuleVersion</span></span>

<span data-ttu-id="09d6d-185">Spécifie la version du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-185">Specifies the version of the module.</span></span>

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

### <span data-ttu-id="09d6d-186">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="09d6d-186">-NestedModules</span></span>

<span data-ttu-id="09d6d-187">Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-187">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="09d6d-188">Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="09d6d-188">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="09d6d-189">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-189">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="09d6d-190">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="09d6d-190">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="09d6d-191">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="09d6d-191">You can combine strings and hash tables in the parameter value.</span></span>

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

### <span data-ttu-id="09d6d-192">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="09d6d-192">-PackageManagementProviders</span></span>

<span data-ttu-id="09d6d-193">Spécifie un tableau de fournisseurs de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="09d6d-193">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="09d6d-194">-PassThru</span><span class="sxs-lookup"><span data-stu-id="09d6d-194">-PassThru</span></span>

<span data-ttu-id="09d6d-195">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="09d6d-195">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="09d6d-196">Par défaut, `Update-ModuleManifest` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="09d6d-196">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="09d6d-197">-Path</span><span class="sxs-lookup"><span data-stu-id="09d6d-197">-Path</span></span>

<span data-ttu-id="09d6d-198">Spécifie le chemin d’accès et le nom de fichier du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-198">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="09d6d-199">Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="09d6d-199">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="09d6d-200">Si vous spécifiez le chemin d’accès à un fichier existant, `Update-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="09d6d-200">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="09d6d-201">Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension.</span><span class="sxs-lookup"><span data-stu-id="09d6d-201">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="09d6d-202">Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="09d6d-202">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="09d6d-203">Pour utiliser une variable, incluez le paramètre **Path** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="09d6d-203">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="09d6d-204">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="09d6d-204">-PowerShellHostName</span></span>

<span data-ttu-id="09d6d-205">Spécifie le nom du programme hôte PowerShell requis par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-205">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="09d6d-206">Entrez le nom du programme hôte, tel que hôte ISE PowerShell ou ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="09d6d-206">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="09d6d-207">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-207">Wildcards aren't permitted.</span></span>

<span data-ttu-id="09d6d-208">Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="09d6d-208">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="09d6d-209">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="09d6d-209">-PowerShellHostVersion</span></span>

<span data-ttu-id="09d6d-210">Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-210">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="09d6d-211">Entrez un numéro de version, par exemple 1.1.</span><span class="sxs-lookup"><span data-stu-id="09d6d-211">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="09d6d-212">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="09d6d-212">-PowerShellVersion</span></span>

<span data-ttu-id="09d6d-213">Spécifie la version minimale de PowerShell qui fonctionnera avec ce module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-213">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="09d6d-214">Par exemple, vous pouvez spécifier 3,0, 4,0 ou 5,0 comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="09d6d-214">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

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

### <span data-ttu-id="09d6d-215">-Version préliminaire</span><span class="sxs-lookup"><span data-stu-id="09d6d-215">-Prerelease</span></span>

<span data-ttu-id="09d6d-216">Indique que le module est en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="09d6d-216">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="09d6d-217">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="09d6d-217">-PrivateData</span></span>

<span data-ttu-id="09d6d-218">Spécifie les données qui sont passées au module lors de son importation.</span><span class="sxs-lookup"><span data-stu-id="09d6d-218">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="09d6d-219">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="09d6d-219">-ProcessorArchitecture</span></span>

<span data-ttu-id="09d6d-220">Spécifie l'architecture de processeur dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="09d6d-220">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="09d6d-221">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="09d6d-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="09d6d-222">Amd64</span><span class="sxs-lookup"><span data-stu-id="09d6d-222">Amd64</span></span>
- <span data-ttu-id="09d6d-223">Arm</span><span class="sxs-lookup"><span data-stu-id="09d6d-223">Arm</span></span>
- <span data-ttu-id="09d6d-224">IA64</span><span class="sxs-lookup"><span data-stu-id="09d6d-224">IA64</span></span>
- <span data-ttu-id="09d6d-225">MSIL</span><span class="sxs-lookup"><span data-stu-id="09d6d-225">MSIL</span></span>
- <span data-ttu-id="09d6d-226">Aucun (inconnu ou non spécifié)</span><span class="sxs-lookup"><span data-stu-id="09d6d-226">None (unknown or unspecified)</span></span>
- <span data-ttu-id="09d6d-227">X86</span><span class="sxs-lookup"><span data-stu-id="09d6d-227">X86</span></span>

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

### <span data-ttu-id="09d6d-228">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="09d6d-228">-ProjectUri</span></span>

<span data-ttu-id="09d6d-229">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="09d6d-229">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="09d6d-230">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="09d6d-230">-ReleaseNotes</span></span>

<span data-ttu-id="09d6d-231">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez voir disponibles pour cette version du script.</span><span class="sxs-lookup"><span data-stu-id="09d6d-231">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="09d6d-232">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="09d6d-232">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="09d6d-233">Spécifie qu’une acceptation de licence est requise pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-233">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="09d6d-234">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="09d6d-234">-RequiredAssemblies</span></span>

<span data-ttu-id="09d6d-235">Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="09d6d-235">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="09d6d-236">Entrez les noms de fichiers d'assembly.</span><span class="sxs-lookup"><span data-stu-id="09d6d-236">Enter the assembly file names.</span></span>
<span data-ttu-id="09d6d-237">PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="09d6d-237">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="09d6d-238">Utilisez ce paramètre pour spécifier tous les assemblys requis par le module, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess** , même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="09d6d-238">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="09d6d-239">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="09d6d-239">-RequiredModules</span></span>

<span data-ttu-id="09d6d-240">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="09d6d-240">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="09d6d-241">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="09d6d-241">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="09d6d-242">Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="09d6d-242">If the required modules aren't available, the `Import-Module` command fails.</span></span>

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

### <span data-ttu-id="09d6d-243">-RootModule</span><span class="sxs-lookup"><span data-stu-id="09d6d-243">-RootModule</span></span>

<span data-ttu-id="09d6d-244">Spécifie le fichier principal ou racine du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-244">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="09d6d-245">Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="09d6d-245">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="09d6d-246">Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="09d6d-246">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="09d6d-247">Si un module a un fichier manifeste et qu’aucun fichier racine n’a été spécifié dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-247">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="09d6d-248">Et, le module devient un module de manifeste (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="09d6d-248">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="09d6d-249">Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="09d6d-249">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="09d6d-250">Dans le cas contraire, leurs membres ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-250">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="09d6d-251">Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-251">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="09d6d-252">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="09d6d-252">-ScriptsToProcess</span></span>

<span data-ttu-id="09d6d-253">Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-253">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="09d6d-254">Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.</span><span class="sxs-lookup"><span data-stu-id="09d6d-254">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="09d6d-255">Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules**.</span><span class="sxs-lookup"><span data-stu-id="09d6d-255">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="09d6d-256">-Tags</span><span class="sxs-lookup"><span data-stu-id="09d6d-256">-Tags</span></span>

<span data-ttu-id="09d6d-257">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="09d6d-257">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="09d6d-258">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="09d6d-258">-TypesToProcess</span></span>

<span data-ttu-id="09d6d-259">Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-259">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="09d6d-260">Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-260">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="09d6d-261">Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="09d6d-261">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="09d6d-262">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="09d6d-262">-VariablesToExport</span></span>

<span data-ttu-id="09d6d-263">Spécifie les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-263">Specifies the variables that the module exports.</span></span> <span data-ttu-id="09d6d-264">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09d6d-264">Wildcards are permitted.</span></span>

<span data-ttu-id="09d6d-265">Utilisez ce paramètre pour limiter les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="09d6d-265">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="09d6d-266">**VariablesToExport** peut supprimer des variables de la liste des variables exportées, mais il ne peut pas ajouter de variables à la liste.</span><span class="sxs-lookup"><span data-stu-id="09d6d-266">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

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

### <span data-ttu-id="09d6d-267">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="09d6d-267">-WhatIf</span></span>

<span data-ttu-id="09d6d-268">Montre ce qui se passe si `Update-ModuleManifest` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="09d6d-268">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="09d6d-269">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="09d6d-269">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="09d6d-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09d6d-270">CommonParameters</span></span>

<span data-ttu-id="09d6d-271">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09d6d-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09d6d-272">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="09d6d-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09d6d-273">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="09d6d-273">INPUTS</span></span>

### <span data-ttu-id="09d6d-274">System.String</span><span class="sxs-lookup"><span data-stu-id="09d6d-274">System.String</span></span>

## <span data-ttu-id="09d6d-275">SORTIES</span><span class="sxs-lookup"><span data-stu-id="09d6d-275">OUTPUTS</span></span>

### <span data-ttu-id="09d6d-276">System.Object</span><span class="sxs-lookup"><span data-stu-id="09d6d-276">System.Object</span></span>

## <span data-ttu-id="09d6d-277">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="09d6d-277">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09d6d-278">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="09d6d-278">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="09d6d-279">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="09d6d-279">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="09d6d-280">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="09d6d-280">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="09d6d-281">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09d6d-281">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="09d6d-282">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="09d6d-282">RELATED LINKS</span></span>

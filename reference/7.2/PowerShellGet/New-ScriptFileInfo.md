---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: d3e3c0ec257bd9c405accaf3051abd1ae4501f0f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599007"
---
# <span data-ttu-id="192c9-102">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="192c9-102">New-ScriptFileInfo</span></span>

## <span data-ttu-id="192c9-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="192c9-103">SYNOPSIS</span></span>
<span data-ttu-id="192c9-104">Crée un fichier de script avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="192c9-104">Creates a script file with metadata.</span></span>

## <span data-ttu-id="192c9-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="192c9-105">SYNTAX</span></span>

### <span data-ttu-id="192c9-106">Tous</span><span class="sxs-lookup"><span data-stu-id="192c9-106">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="192c9-107">Description</span><span class="sxs-lookup"><span data-stu-id="192c9-107">DESCRIPTION</span></span>

<span data-ttu-id="192c9-108">L' `New-ScriptFileInfo` applet de commande crée un fichier de script PowerShell, y compris les métadonnées relatives au script.</span><span class="sxs-lookup"><span data-stu-id="192c9-108">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="192c9-109">Les exemples utilisent la projection pour passer des paramètres à l' `New-ScriptFileInfo` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="192c9-109">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="192c9-110">Pour plus d’informations, consultez [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="192c9-110">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="192c9-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="192c9-111">EXAMPLES</span></span>

### <span data-ttu-id="192c9-112">Exemple 1 : créer un fichier de script et spécifier sa version, son auteur et sa description</span><span class="sxs-lookup"><span data-stu-id="192c9-112">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="192c9-113">Dans cet exemple, un fichier de script est créé et son contenu est affiché dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="192c9-113">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="192c9-114">L' `New-ScriptFileInfo` applet de commande utilise la projection pour configurer plusieurs paramètres pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-114">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="192c9-115">**Path** définit l’emplacement et le nom du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-115">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="192c9-116">**Version** spécifie le numéro de version du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-116">**Version** specifies the script's version number.</span></span> <span data-ttu-id="192c9-117">**Auteur** est l’adresse de messagerie de la personne qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-117">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="192c9-118">**Description** explique l’objectif du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-118">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="192c9-119">Une fois le script créé, `Get-Content` utilise le paramètre **path** pour localiser le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-119">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="192c9-120">Le contenu du script s’affiche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="192c9-120">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="192c9-121">Exemple 2 : tester un fichier de script</span><span class="sxs-lookup"><span data-stu-id="192c9-121">Example 2: Test a script file</span></span>

<span data-ttu-id="192c9-122">Dans cet exemple, les métadonnées du script créé dans l' **exemple 1** sont testées.</span><span class="sxs-lookup"><span data-stu-id="192c9-122">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="192c9-123">L' `Test-ScriptFileInfo` applet de commande utilise le paramètre **path** pour spécifier l’emplacement du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="192c9-123">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="192c9-124">Exemple 3 : créer un fichier de script avec toutes les propriétés de métadonnées</span><span class="sxs-lookup"><span data-stu-id="192c9-124">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="192c9-125">Cet exemple utilise la projection pour créer un fichier de script nommé `New-ScriptFile.ps1` qui comprend toutes ses propriétés de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="192c9-125">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="192c9-126">Le paramètre **Verbose** spécifie que la sortie détaillée est affichée lors de la création du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-126">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="192c9-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="192c9-127">PARAMETERS</span></span>

### <span data-ttu-id="192c9-128">-Auteur</span><span class="sxs-lookup"><span data-stu-id="192c9-128">-Author</span></span>

<span data-ttu-id="192c9-129">Spécifie l’auteur du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-129">Specifies the script author.</span></span>

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

### <span data-ttu-id="192c9-130">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="192c9-130">-CompanyName</span></span>

<span data-ttu-id="192c9-131">Spécifie la société ou le fournisseur qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-131">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="192c9-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="192c9-132">-Confirm</span></span>

<span data-ttu-id="192c9-133">Vous invite à confirmer l’exécution de l' `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="192c9-133">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="192c9-134">-Copyright</span><span class="sxs-lookup"><span data-stu-id="192c9-134">-Copyright</span></span>

<span data-ttu-id="192c9-135">Spécifie une déclaration de copyright pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-135">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="192c9-136">Description</span><span class="sxs-lookup"><span data-stu-id="192c9-136">-Description</span></span>

<span data-ttu-id="192c9-137">Spécifie une description pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-137">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="192c9-138">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="192c9-138">-ExternalModuleDependencies</span></span>

<span data-ttu-id="192c9-139">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="192c9-139">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="192c9-140">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="192c9-140">-ExternalScriptDependencies</span></span>

<span data-ttu-id="192c9-141">Spécifie un tableau de dépendances de script externe.</span><span class="sxs-lookup"><span data-stu-id="192c9-141">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="192c9-142">-Force</span><span class="sxs-lookup"><span data-stu-id="192c9-142">-Force</span></span>

<span data-ttu-id="192c9-143">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="192c9-143">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="192c9-144">-Guid</span><span class="sxs-lookup"><span data-stu-id="192c9-144">-Guid</span></span>

<span data-ttu-id="192c9-145">Spécifie un ID unique pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-145">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="192c9-146">-IconUri</span><span class="sxs-lookup"><span data-stu-id="192c9-146">-IconUri</span></span>

<span data-ttu-id="192c9-147">Spécifie l’URL d’une icône pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-147">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="192c9-148">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le script.</span><span class="sxs-lookup"><span data-stu-id="192c9-148">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="192c9-149">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="192c9-149">-LicenseUri</span></span>

<span data-ttu-id="192c9-150">Spécifie l’URL des termes du contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="192c9-150">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="192c9-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="192c9-151">-PassThru</span></span>

<span data-ttu-id="192c9-152">Retourne un objet qui représente l’élément avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="192c9-152">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="192c9-153">Par défaut, `New-ScriptFileInfo` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="192c9-153">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="192c9-154">-Path</span><span class="sxs-lookup"><span data-stu-id="192c9-154">-Path</span></span>

<span data-ttu-id="192c9-155">Spécifie l’emplacement où le fichier de script est enregistré.</span><span class="sxs-lookup"><span data-stu-id="192c9-155">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="192c9-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="192c9-156">-PrivateData</span></span>

<span data-ttu-id="192c9-157">Spécifie les données privées du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-157">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="192c9-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="192c9-158">-ProjectUri</span></span>

<span data-ttu-id="192c9-159">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="192c9-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="192c9-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="192c9-160">-ReleaseNotes</span></span>

<span data-ttu-id="192c9-161">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez que les utilisateurs de cette version du script puissent utiliser.</span><span class="sxs-lookup"><span data-stu-id="192c9-161">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="192c9-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="192c9-162">-RequiredModules</span></span>

<span data-ttu-id="192c9-163">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="192c9-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="192c9-164">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="192c9-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="192c9-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="192c9-165">-RequiredScripts</span></span>

<span data-ttu-id="192c9-166">Spécifie un tableau de scripts requis.</span><span class="sxs-lookup"><span data-stu-id="192c9-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="192c9-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="192c9-167">-Tags</span></span>

<span data-ttu-id="192c9-168">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="192c9-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="192c9-169">-Version</span><span class="sxs-lookup"><span data-stu-id="192c9-169">-Version</span></span>

<span data-ttu-id="192c9-170">Spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="192c9-170">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="192c9-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="192c9-171">-WhatIf</span></span>

<span data-ttu-id="192c9-172">Montre ce qui se passe si `New-ScriptFileInfo` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="192c9-172">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="192c9-173">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="192c9-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="192c9-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="192c9-174">CommonParameters</span></span>

<span data-ttu-id="192c9-175">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="192c9-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="192c9-176">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="192c9-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="192c9-177">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="192c9-177">INPUTS</span></span>

### <span data-ttu-id="192c9-178">System.String</span><span class="sxs-lookup"><span data-stu-id="192c9-178">System.String</span></span>

## <span data-ttu-id="192c9-179">SORTIES</span><span class="sxs-lookup"><span data-stu-id="192c9-179">OUTPUTS</span></span>

### <span data-ttu-id="192c9-180">System.Object</span><span class="sxs-lookup"><span data-stu-id="192c9-180">System.Object</span></span>

## <span data-ttu-id="192c9-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="192c9-181">NOTES</span></span>

## <span data-ttu-id="192c9-182">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="192c9-182">RELATED LINKS</span></span>

[<span data-ttu-id="192c9-183">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="192c9-183">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="192c9-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="192c9-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="192c9-185">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="192c9-185">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)


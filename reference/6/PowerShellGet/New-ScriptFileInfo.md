---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: 649110ddb4147587dbff31d7b8410b706decca89
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204254"
---
# <span data-ttu-id="9e398-103">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="9e398-103">New-ScriptFileInfo</span></span>

## <span data-ttu-id="9e398-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9e398-104">SYNOPSIS</span></span>
<span data-ttu-id="9e398-105">Crée un fichier de script avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9e398-105">Creates a script file with metadata.</span></span>

## <span data-ttu-id="9e398-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e398-106">SYNTAX</span></span>

### <span data-ttu-id="9e398-107">Tous</span><span class="sxs-lookup"><span data-stu-id="9e398-107">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9e398-108">Description</span><span class="sxs-lookup"><span data-stu-id="9e398-108">DESCRIPTION</span></span>

<span data-ttu-id="9e398-109">L' `New-ScriptFileInfo` applet de commande crée un fichier de script PowerShell, y compris les métadonnées relatives au script.</span><span class="sxs-lookup"><span data-stu-id="9e398-109">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="9e398-110">Les exemples utilisent la projection pour passer des paramètres à l' `New-ScriptFileInfo` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9e398-110">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="9e398-111">Pour plus d’informations, consultez [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="9e398-111">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="9e398-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9e398-112">EXAMPLES</span></span>

### <span data-ttu-id="9e398-113">Exemple 1 : créer un fichier de script et spécifier sa version, son auteur et sa description</span><span class="sxs-lookup"><span data-stu-id="9e398-113">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="9e398-114">Dans cet exemple, un fichier de script est créé et son contenu est affiché dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e398-114">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

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

<span data-ttu-id="9e398-115">L' `New-ScriptFileInfo` applet de commande utilise la projection pour configurer plusieurs paramètres pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-115">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="9e398-116">**Path** définit l’emplacement et le nom du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-116">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="9e398-117">**Version** spécifie le numéro de version du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-117">**Version** specifies the script's version number.</span></span> <span data-ttu-id="9e398-118">**Auteur** est l’adresse de messagerie de la personne qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-118">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="9e398-119">**Description** explique l’objectif du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-119">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="9e398-120">Une fois le script créé, `Get-Content` utilise le paramètre **path** pour localiser le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-120">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="9e398-121">Le contenu du script s’affiche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e398-121">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="9e398-122">Exemple 2 : tester un fichier de script</span><span class="sxs-lookup"><span data-stu-id="9e398-122">Example 2: Test a script file</span></span>

<span data-ttu-id="9e398-123">Dans cet exemple, les métadonnées du script créé dans l' **exemple 1** sont testées.</span><span class="sxs-lookup"><span data-stu-id="9e398-123">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="9e398-124">L' `Test-ScriptFileInfo` applet de commande utilise le paramètre **path** pour spécifier l’emplacement du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="9e398-124">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="9e398-125">Exemple 3 : créer un fichier de script avec toutes les propriétés de métadonnées</span><span class="sxs-lookup"><span data-stu-id="9e398-125">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="9e398-126">Cet exemple utilise la projection pour créer un fichier de script nommé `New-ScriptFile.ps1` qui comprend toutes ses propriétés de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9e398-126">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="9e398-127">Le paramètre **Verbose** spécifie que la sortie détaillée est affichée lors de la création du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-127">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

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

## <span data-ttu-id="9e398-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e398-128">PARAMETERS</span></span>

### <span data-ttu-id="9e398-129">-Auteur</span><span class="sxs-lookup"><span data-stu-id="9e398-129">-Author</span></span>

<span data-ttu-id="9e398-130">Spécifie l’auteur du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-130">Specifies the script author.</span></span>

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

### <span data-ttu-id="9e398-131">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="9e398-131">-CompanyName</span></span>

<span data-ttu-id="9e398-132">Spécifie la société ou le fournisseur qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-132">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="9e398-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9e398-133">-Confirm</span></span>

<span data-ttu-id="9e398-134">Vous invite à confirmer l’exécution de l' `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="9e398-134">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="9e398-135">-Copyright</span><span class="sxs-lookup"><span data-stu-id="9e398-135">-Copyright</span></span>

<span data-ttu-id="9e398-136">Spécifie une déclaration de copyright pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-136">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="9e398-137">Description</span><span class="sxs-lookup"><span data-stu-id="9e398-137">-Description</span></span>

<span data-ttu-id="9e398-138">Spécifie une description pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-138">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="9e398-139">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="9e398-139">-ExternalModuleDependencies</span></span>

<span data-ttu-id="9e398-140">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="9e398-140">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="9e398-141">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="9e398-141">-ExternalScriptDependencies</span></span>

<span data-ttu-id="9e398-142">Spécifie un tableau de dépendances de script externe.</span><span class="sxs-lookup"><span data-stu-id="9e398-142">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="9e398-143">-Force</span><span class="sxs-lookup"><span data-stu-id="9e398-143">-Force</span></span>

<span data-ttu-id="9e398-144">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e398-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9e398-145">-Guid</span><span class="sxs-lookup"><span data-stu-id="9e398-145">-Guid</span></span>

<span data-ttu-id="9e398-146">Spécifie un ID unique pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-146">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="9e398-147">-IconUri</span><span class="sxs-lookup"><span data-stu-id="9e398-147">-IconUri</span></span>

<span data-ttu-id="9e398-148">Spécifie l’URL d’une icône pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-148">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="9e398-149">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le script.</span><span class="sxs-lookup"><span data-stu-id="9e398-149">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="9e398-150">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="9e398-150">-LicenseUri</span></span>

<span data-ttu-id="9e398-151">Spécifie l’URL des termes du contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="9e398-151">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="9e398-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9e398-152">-PassThru</span></span>

<span data-ttu-id="9e398-153">Retourne un objet qui représente l’élément avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="9e398-153">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="9e398-154">Par défaut, `New-ScriptFileInfo` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="9e398-154">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="9e398-155">-Path</span><span class="sxs-lookup"><span data-stu-id="9e398-155">-Path</span></span>

<span data-ttu-id="9e398-156">Spécifie l’emplacement où le fichier de script est enregistré.</span><span class="sxs-lookup"><span data-stu-id="9e398-156">Specifies the location where the script file is saved.</span></span>

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

### <span data-ttu-id="9e398-157">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="9e398-157">-PrivateData</span></span>

<span data-ttu-id="9e398-158">Spécifie les données privées du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-158">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="9e398-159">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="9e398-159">-ProjectUri</span></span>

<span data-ttu-id="9e398-160">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="9e398-160">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="9e398-161">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="9e398-161">-ReleaseNotes</span></span>

<span data-ttu-id="9e398-162">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez que les utilisateurs de cette version du script puissent utiliser.</span><span class="sxs-lookup"><span data-stu-id="9e398-162">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="9e398-163">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="9e398-163">-RequiredModules</span></span>

<span data-ttu-id="9e398-164">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="9e398-164">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="9e398-165">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="9e398-165">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="9e398-166">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="9e398-166">-RequiredScripts</span></span>

<span data-ttu-id="9e398-167">Spécifie un tableau de scripts requis.</span><span class="sxs-lookup"><span data-stu-id="9e398-167">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="9e398-168">-Tags</span><span class="sxs-lookup"><span data-stu-id="9e398-168">-Tags</span></span>

<span data-ttu-id="9e398-169">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="9e398-169">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="9e398-170">-Version</span><span class="sxs-lookup"><span data-stu-id="9e398-170">-Version</span></span>

<span data-ttu-id="9e398-171">Spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="9e398-171">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="9e398-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9e398-172">-WhatIf</span></span>

<span data-ttu-id="9e398-173">Montre ce qui se passe si `New-ScriptFileInfo` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="9e398-173">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="9e398-174">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9e398-174">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9e398-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e398-175">CommonParameters</span></span>

<span data-ttu-id="9e398-176">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e398-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e398-177">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9e398-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e398-178">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9e398-178">INPUTS</span></span>

### <span data-ttu-id="9e398-179">System.String</span><span class="sxs-lookup"><span data-stu-id="9e398-179">System.String</span></span>

## <span data-ttu-id="9e398-180">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9e398-180">OUTPUTS</span></span>

### <span data-ttu-id="9e398-181">System.Object</span><span class="sxs-lookup"><span data-stu-id="9e398-181">System.Object</span></span>

## <span data-ttu-id="9e398-182">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9e398-182">NOTES</span></span>

## <span data-ttu-id="9e398-183">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9e398-183">RELATED LINKS</span></span>

[<span data-ttu-id="9e398-184">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="9e398-184">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="9e398-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="9e398-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="9e398-186">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="9e398-186">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

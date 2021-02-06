---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: de138a27ed9425057406dc6120a8354b72a3b8a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603906"
---
# <span data-ttu-id="07b7c-102">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="07b7c-102">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="07b7c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="07b7c-103">SYNOPSIS</span></span>
<span data-ttu-id="07b7c-104">Met à jour les informations d’un script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-104">Updates information for a script.</span></span>

## <span data-ttu-id="07b7c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="07b7c-105">SYNTAX</span></span>

### <span data-ttu-id="07b7c-106">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="07b7c-106">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="07b7c-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="07b7c-107">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="07b7c-108">Description</span><span class="sxs-lookup"><span data-stu-id="07b7c-108">DESCRIPTION</span></span>

<span data-ttu-id="07b7c-109">L' `Update-ScriptFileInfo` applet de commande met à jour les valeurs de propriété d’un script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-109">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="07b7c-110">Par exemple, les valeurs pour version, auteur ou description.</span><span class="sxs-lookup"><span data-stu-id="07b7c-110">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="07b7c-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="07b7c-111">EXAMPLES</span></span>

### <span data-ttu-id="07b7c-112">Exemple 1 : mettre à jour la version d’un fichier de script</span><span class="sxs-lookup"><span data-stu-id="07b7c-112">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="07b7c-113">Dans cet exemple, un fichier de script existant est mis à jour avec de nouvelles valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="07b7c-113">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="07b7c-114">La projection est utilisée pour passer des paramètres à l' `Update-ScriptFileInfo` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07b7c-114">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="07b7c-115">Pour plus d’informations, consultez [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="07b7c-115">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

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
This is the updated description

#>
Param()
```

<span data-ttu-id="07b7c-116">`$Parms` stocke les valeurs de paramètre pour **path**, **version**, **Author**, **CompanyName** et **Description**.</span><span class="sxs-lookup"><span data-stu-id="07b7c-116">`$Parms` stores the parameter values for **Path**, **Version**, **Author**, **CompanyName**, and **Description**.</span></span> <span data-ttu-id="07b7c-117">`Update-ScriptFileInfo` Obtient les valeurs de paramètre à partir de `@Parms` et met à jour le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-117">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="07b7c-118">Le paramètre **PassThru** affiche le contenu du script dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07b7c-118">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="07b7c-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07b7c-119">PARAMETERS</span></span>

### <span data-ttu-id="07b7c-120">-Auteur</span><span class="sxs-lookup"><span data-stu-id="07b7c-120">-Author</span></span>

<span data-ttu-id="07b7c-121">Spécifie l’auteur du script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-121">Specifies the script author.</span></span>

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

### <span data-ttu-id="07b7c-122">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="07b7c-122">-CompanyName</span></span>

<span data-ttu-id="07b7c-123">Spécifie la société ou le fournisseur qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-123">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="07b7c-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="07b7c-124">-Confirm</span></span>

<span data-ttu-id="07b7c-125">Vous invite à confirmer l’exécution `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="07b7c-125">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="07b7c-126">-Copyright</span><span class="sxs-lookup"><span data-stu-id="07b7c-126">-Copyright</span></span>

<span data-ttu-id="07b7c-127">Spécifie une déclaration de copyright pour le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-127">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="07b7c-128">Description</span><span class="sxs-lookup"><span data-stu-id="07b7c-128">-Description</span></span>

<span data-ttu-id="07b7c-129">Spécifie une description pour le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-129">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="07b7c-130">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="07b7c-130">-ExternalModuleDependencies</span></span>

<span data-ttu-id="07b7c-131">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="07b7c-131">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="07b7c-132">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="07b7c-132">-ExternalScriptDependencies</span></span>

<span data-ttu-id="07b7c-133">Spécifie un tableau de dépendances de script externe.</span><span class="sxs-lookup"><span data-stu-id="07b7c-133">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="07b7c-134">-Force</span><span class="sxs-lookup"><span data-stu-id="07b7c-134">-Force</span></span>

<span data-ttu-id="07b7c-135">Force l' `Update-ScriptFileInfo` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07b7c-135">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="07b7c-136">-Guid</span><span class="sxs-lookup"><span data-stu-id="07b7c-136">-Guid</span></span>

<span data-ttu-id="07b7c-137">Spécifie un ID unique pour un script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-137">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="07b7c-138">-IconUri</span><span class="sxs-lookup"><span data-stu-id="07b7c-138">-IconUri</span></span>

<span data-ttu-id="07b7c-139">Spécifie l’URL d’une icône pour le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-139">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="07b7c-140">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-140">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="07b7c-141">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="07b7c-141">-LicenseUri</span></span>

<span data-ttu-id="07b7c-142">Spécifie l’URL des termes du contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="07b7c-142">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="07b7c-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="07b7c-143">-LiteralPath</span></span>

<span data-ttu-id="07b7c-144">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="07b7c-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="07b7c-145">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est entrée.</span><span class="sxs-lookup"><span data-stu-id="07b7c-145">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="07b7c-146">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="07b7c-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="07b7c-147">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="07b7c-147">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="07b7c-148">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="07b7c-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="07b7c-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="07b7c-149">-PassThru</span></span>

<span data-ttu-id="07b7c-150">Retourne un objet qui représente l’élément avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="07b7c-150">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="07b7c-151">Par défaut, `Update-ScriptFileInfo` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="07b7c-151">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="07b7c-152">-Path</span><span class="sxs-lookup"><span data-stu-id="07b7c-152">-Path</span></span>

<span data-ttu-id="07b7c-153">Spécifie l’emplacement du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-153">Specifies the script file's location.</span></span> <span data-ttu-id="07b7c-154">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="07b7c-154">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="07b7c-155">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="07b7c-155">-PrivateData</span></span>

<span data-ttu-id="07b7c-156">Spécifie les données privées du script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-156">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="07b7c-157">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="07b7c-157">-ProjectUri</span></span>

<span data-ttu-id="07b7c-158">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="07b7c-158">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="07b7c-159">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="07b7c-159">-ReleaseNotes</span></span>

<span data-ttu-id="07b7c-160">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez voir disponibles pour cette version du script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-160">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="07b7c-161">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="07b7c-161">-RequiredModules</span></span>

<span data-ttu-id="07b7c-162">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="07b7c-162">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="07b7c-163">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="07b7c-163">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="07b7c-164">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="07b7c-164">-RequiredScripts</span></span>

<span data-ttu-id="07b7c-165">Spécifie un tableau de scripts requis.</span><span class="sxs-lookup"><span data-stu-id="07b7c-165">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="07b7c-166">-Tags</span><span class="sxs-lookup"><span data-stu-id="07b7c-166">-Tags</span></span>

<span data-ttu-id="07b7c-167">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="07b7c-167">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="07b7c-168">-Version</span><span class="sxs-lookup"><span data-stu-id="07b7c-168">-Version</span></span>

<span data-ttu-id="07b7c-169">Spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-169">Specifies the script's version.</span></span>

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

### <span data-ttu-id="07b7c-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="07b7c-170">-WhatIf</span></span>

<span data-ttu-id="07b7c-171">Montre ce qui se passe si `Update-ScriptFileInfo` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="07b7c-171">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="07b7c-172">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="07b7c-172">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="07b7c-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07b7c-173">CommonParameters</span></span>

<span data-ttu-id="07b7c-174">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07b7c-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07b7c-175">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07b7c-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07b7c-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="07b7c-176">INPUTS</span></span>

### <span data-ttu-id="07b7c-177">System.String</span><span class="sxs-lookup"><span data-stu-id="07b7c-177">System.String</span></span>

## <span data-ttu-id="07b7c-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="07b7c-178">OUTPUTS</span></span>

### <span data-ttu-id="07b7c-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="07b7c-179">System.Object</span></span>

## <span data-ttu-id="07b7c-180">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="07b7c-180">NOTES</span></span>

<span data-ttu-id="07b7c-181">Utilisez l' `Test-ScriptFileInfo` applet de commande pour valider les métadonnées d’un script.</span><span class="sxs-lookup"><span data-stu-id="07b7c-181">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="07b7c-182">Les scripts doivent inclure des valeurs pour la version, le GUID, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="07b7c-182">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="07b7c-183">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="07b7c-183">RELATED LINKS</span></span>

[<span data-ttu-id="07b7c-184">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="07b7c-184">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="07b7c-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="07b7c-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)


---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: 1fa19b82d0467bdd363af70919efe9a51febbdcb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201954"
---
# <span data-ttu-id="1efe2-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="1efe2-103">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="1efe2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1efe2-104">SYNOPSIS</span></span>
<span data-ttu-id="1efe2-105">Met à jour les informations d’un script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-105">Updates information for a script.</span></span>

## <span data-ttu-id="1efe2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1efe2-106">SYNTAX</span></span>

### <span data-ttu-id="1efe2-107">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1efe2-107">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1efe2-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="1efe2-108">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1efe2-109">Description</span><span class="sxs-lookup"><span data-stu-id="1efe2-109">DESCRIPTION</span></span>

<span data-ttu-id="1efe2-110">L' `Update-ScriptFileInfo` applet de commande met à jour les valeurs de propriété d’un script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-110">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="1efe2-111">Par exemple, les valeurs pour version, auteur ou description.</span><span class="sxs-lookup"><span data-stu-id="1efe2-111">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="1efe2-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1efe2-112">EXAMPLES</span></span>

### <span data-ttu-id="1efe2-113">Exemple 1 : mettre à jour la version d’un fichier de script</span><span class="sxs-lookup"><span data-stu-id="1efe2-113">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="1efe2-114">Dans cet exemple, un fichier de script existant est mis à jour avec de nouvelles valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="1efe2-114">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="1efe2-115">La projection est utilisée pour passer des paramètres à l' `Update-ScriptFileInfo` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1efe2-115">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="1efe2-116">Pour plus d’informations, consultez [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span><span class="sxs-lookup"><span data-stu-id="1efe2-116">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

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

<span data-ttu-id="1efe2-117">`$Parms` stocke les valeurs de paramètre pour **path** , **version** , **Author** , **CompanyName** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="1efe2-117">`$Parms` stores the parameter values for **Path** , **Version** , **Author** , **CompanyName** , and **Description** .</span></span> <span data-ttu-id="1efe2-118">`Update-ScriptFileInfo` Obtient les valeurs de paramètre à partir de `@Parms` et met à jour le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-118">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="1efe2-119">Le paramètre **PassThru** affiche le contenu du script dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1efe2-119">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="1efe2-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1efe2-120">PARAMETERS</span></span>

### <span data-ttu-id="1efe2-121">-Auteur</span><span class="sxs-lookup"><span data-stu-id="1efe2-121">-Author</span></span>

<span data-ttu-id="1efe2-122">Spécifie l’auteur du script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-122">Specifies the script author.</span></span>

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

### <span data-ttu-id="1efe2-123">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="1efe2-123">-CompanyName</span></span>

<span data-ttu-id="1efe2-124">Spécifie la société ou le fournisseur qui a créé le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-124">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="1efe2-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1efe2-125">-Confirm</span></span>

<span data-ttu-id="1efe2-126">Vous invite à confirmer l’exécution `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="1efe2-126">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="1efe2-127">-Copyright</span><span class="sxs-lookup"><span data-stu-id="1efe2-127">-Copyright</span></span>

<span data-ttu-id="1efe2-128">Spécifie une déclaration de copyright pour le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-128">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="1efe2-129">Description</span><span class="sxs-lookup"><span data-stu-id="1efe2-129">-Description</span></span>

<span data-ttu-id="1efe2-130">Spécifie une description pour le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-130">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="1efe2-131">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="1efe2-131">-ExternalModuleDependencies</span></span>

<span data-ttu-id="1efe2-132">Spécifie un tableau de dépendances de modules externes.</span><span class="sxs-lookup"><span data-stu-id="1efe2-132">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="1efe2-133">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="1efe2-133">-ExternalScriptDependencies</span></span>

<span data-ttu-id="1efe2-134">Spécifie un tableau de dépendances de script externe.</span><span class="sxs-lookup"><span data-stu-id="1efe2-134">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="1efe2-135">-Force</span><span class="sxs-lookup"><span data-stu-id="1efe2-135">-Force</span></span>

<span data-ttu-id="1efe2-136">Force l' `Update-ScriptFileInfo` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1efe2-136">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1efe2-137">-Guid</span><span class="sxs-lookup"><span data-stu-id="1efe2-137">-Guid</span></span>

<span data-ttu-id="1efe2-138">Spécifie un ID unique pour un script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-138">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="1efe2-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="1efe2-139">-IconUri</span></span>

<span data-ttu-id="1efe2-140">Spécifie l’URL d’une icône pour le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-140">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="1efe2-141">L’icône spécifiée s’affiche sur la page Web de la Galerie pour le script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-141">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="1efe2-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="1efe2-142">-LicenseUri</span></span>

<span data-ttu-id="1efe2-143">Spécifie l’URL des termes du contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="1efe2-143">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="1efe2-144">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1efe2-144">-LiteralPath</span></span>

<span data-ttu-id="1efe2-145">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="1efe2-145">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1efe2-146">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est entrée.</span><span class="sxs-lookup"><span data-stu-id="1efe2-146">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="1efe2-147">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1efe2-147">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1efe2-148">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="1efe2-148">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="1efe2-149">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="1efe2-149">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="1efe2-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1efe2-150">-PassThru</span></span>

<span data-ttu-id="1efe2-151">Retourne un objet qui représente l’élément avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="1efe2-151">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="1efe2-152">Par défaut, `Update-ScriptFileInfo` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="1efe2-152">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="1efe2-153">-Path</span><span class="sxs-lookup"><span data-stu-id="1efe2-153">-Path</span></span>

<span data-ttu-id="1efe2-154">Spécifie l’emplacement du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-154">Specifies the script file's location.</span></span> <span data-ttu-id="1efe2-155">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1efe2-155">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1efe2-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="1efe2-156">-PrivateData</span></span>

<span data-ttu-id="1efe2-157">Spécifie les données privées du script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-157">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="1efe2-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="1efe2-158">-ProjectUri</span></span>

<span data-ttu-id="1efe2-159">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="1efe2-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="1efe2-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="1efe2-160">-ReleaseNotes</span></span>

<span data-ttu-id="1efe2-161">Spécifie un tableau de chaînes qui contient des notes de publication ou des commentaires que vous souhaitez voir disponibles pour cette version du script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-161">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="1efe2-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="1efe2-162">-RequiredModules</span></span>

<span data-ttu-id="1efe2-163">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="1efe2-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="1efe2-164">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="1efe2-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="1efe2-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="1efe2-165">-RequiredScripts</span></span>

<span data-ttu-id="1efe2-166">Spécifie un tableau de scripts requis.</span><span class="sxs-lookup"><span data-stu-id="1efe2-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="1efe2-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="1efe2-167">-Tags</span></span>

<span data-ttu-id="1efe2-168">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="1efe2-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="1efe2-169">-Version</span><span class="sxs-lookup"><span data-stu-id="1efe2-169">-Version</span></span>

<span data-ttu-id="1efe2-170">Spécifie la version du script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-170">Specifies the script's version.</span></span>

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

### <span data-ttu-id="1efe2-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1efe2-171">-WhatIf</span></span>

<span data-ttu-id="1efe2-172">Montre ce qui se passe si `Update-ScriptFileInfo` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1efe2-172">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="1efe2-173">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1efe2-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1efe2-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1efe2-174">CommonParameters</span></span>

<span data-ttu-id="1efe2-175">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1efe2-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1efe2-176">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1efe2-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1efe2-177">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1efe2-177">INPUTS</span></span>

### <span data-ttu-id="1efe2-178">System.String</span><span class="sxs-lookup"><span data-stu-id="1efe2-178">System.String</span></span>

## <span data-ttu-id="1efe2-179">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1efe2-179">OUTPUTS</span></span>

### <span data-ttu-id="1efe2-180">System.Object</span><span class="sxs-lookup"><span data-stu-id="1efe2-180">System.Object</span></span>

## <span data-ttu-id="1efe2-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1efe2-181">NOTES</span></span>

<span data-ttu-id="1efe2-182">Utilisez l' `Test-ScriptFileInfo` applet de commande pour valider les métadonnées d’un script.</span><span class="sxs-lookup"><span data-stu-id="1efe2-182">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="1efe2-183">Les scripts doivent inclure des valeurs pour la version, le GUID, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="1efe2-183">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="1efe2-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1efe2-184">RELATED LINKS</span></span>

[<span data-ttu-id="1efe2-185">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="1efe2-185">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="1efe2-186">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="1efe2-186">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

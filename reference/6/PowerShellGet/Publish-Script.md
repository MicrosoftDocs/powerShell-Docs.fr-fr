---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 95dadef6a1cbc4e730fed21fd8bda629f4c04563
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204253"
---
# <span data-ttu-id="ffc30-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-103">Publish-Script</span></span>

## <span data-ttu-id="ffc30-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ffc30-104">SYNOPSIS</span></span>
<span data-ttu-id="ffc30-105">Publie un script.</span><span class="sxs-lookup"><span data-stu-id="ffc30-105">Publishes a script.</span></span>

## <span data-ttu-id="ffc30-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ffc30-106">SYNTAX</span></span>

### <span data-ttu-id="ffc30-107">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ffc30-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ffc30-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ffc30-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ffc30-109">Description</span><span class="sxs-lookup"><span data-stu-id="ffc30-109">DESCRIPTION</span></span>

<span data-ttu-id="ffc30-110">L' `Publish-Script` applet de commande publie le script spécifié dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="ffc30-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="ffc30-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ffc30-111">EXAMPLES</span></span>

### <span data-ttu-id="ffc30-112">Exemple 1 : créer un fichier de script, y ajouter du contenu et le publier</span><span class="sxs-lookup"><span data-stu-id="ffc30-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="ffc30-113">L' `New-ScriptFileInfo` applet de commande crée un fichier de script nommé `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ffc30-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="ffc30-114">`Get-Content` affiche le contenu de `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ffc30-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="ffc30-115">L' `Add-Content` applet de commande ajoute une fonction et un flux de travail à `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ffc30-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

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
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="ffc30-116">L’applet de commande est `Test-ScriptFileInfo` validée `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ffc30-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="ffc30-117">L' `Publish-Script` applet de commande publie le script dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="ffc30-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="ffc30-118">Enfin,</span><span class="sxs-lookup"><span data-stu-id="ffc30-118">Finally.</span></span> <span data-ttu-id="ffc30-119">`Find-Script` est utilisé pour rechercher `Demo-Script.ps1` dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="ffc30-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="ffc30-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ffc30-120">PARAMETERS</span></span>

### <span data-ttu-id="ffc30-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="ffc30-121">-Credential</span></span>

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

### <span data-ttu-id="ffc30-122">-Force</span><span class="sxs-lookup"><span data-stu-id="ffc30-122">-Force</span></span>

<span data-ttu-id="ffc30-123">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ffc30-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ffc30-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ffc30-124">-LiteralPath</span></span>

<span data-ttu-id="ffc30-125">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="ffc30-125">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ffc30-126">Contrairement au paramètre **path** , la valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="ffc30-126">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="ffc30-127">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ffc30-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ffc30-128">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="ffc30-128">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="ffc30-129">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="ffc30-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffc30-130">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="ffc30-130">-NuGetApiKey</span></span>

<span data-ttu-id="ffc30-131">Spécifie la clé API que vous souhaitez utiliser pour publier un script dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="ffc30-131">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="ffc30-132">La clé API fait partie de votre profil dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="ffc30-132">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="ffc30-133">Pour plus d’informations, consultez [gestion des clés API](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span><span class="sxs-lookup"><span data-stu-id="ffc30-133">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="ffc30-134">-Path</span><span class="sxs-lookup"><span data-stu-id="ffc30-134">-Path</span></span>

<span data-ttu-id="ffc30-135">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="ffc30-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ffc30-136">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ffc30-136">Wildcards are permitted.</span></span> <span data-ttu-id="ffc30-137">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ffc30-137">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ffc30-138">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="ffc30-138">-Repository</span></span>

<span data-ttu-id="ffc30-139">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="ffc30-139">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="ffc30-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ffc30-140">-Confirm</span></span>

<span data-ttu-id="ffc30-141">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ffc30-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ffc30-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ffc30-142">-WhatIf</span></span>

<span data-ttu-id="ffc30-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ffc30-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ffc30-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ffc30-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ffc30-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ffc30-145">CommonParameters</span></span>

<span data-ttu-id="ffc30-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ffc30-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ffc30-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ffc30-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ffc30-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ffc30-148">INPUTS</span></span>

### <span data-ttu-id="ffc30-149">System.String</span><span class="sxs-lookup"><span data-stu-id="ffc30-149">System.String</span></span>

### <span data-ttu-id="ffc30-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ffc30-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="ffc30-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ffc30-151">OUTPUTS</span></span>

### <span data-ttu-id="ffc30-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="ffc30-152">System.Object</span></span>

## <span data-ttu-id="ffc30-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ffc30-153">NOTES</span></span>

## <span data-ttu-id="ffc30-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ffc30-154">RELATED LINKS</span></span>

[<span data-ttu-id="ffc30-155">Find-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="ffc30-156">Install-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="ffc30-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="ffc30-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="ffc30-159">Update-Script</span><span class="sxs-lookup"><span data-stu-id="ffc30-159">Update-Script</span></span>](Update-Script.md)

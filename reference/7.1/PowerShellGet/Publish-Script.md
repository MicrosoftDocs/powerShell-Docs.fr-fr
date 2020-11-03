---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 1c333494525ed697ad04f6b500cabfb5964ec9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205061"
---
# <span data-ttu-id="cfebe-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-103">Publish-Script</span></span>

## <span data-ttu-id="cfebe-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cfebe-104">SYNOPSIS</span></span>
<span data-ttu-id="cfebe-105">Publie un script.</span><span class="sxs-lookup"><span data-stu-id="cfebe-105">Publishes a script.</span></span>

## <span data-ttu-id="cfebe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cfebe-106">SYNTAX</span></span>

### <span data-ttu-id="cfebe-107">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="cfebe-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cfebe-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="cfebe-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cfebe-109">Description</span><span class="sxs-lookup"><span data-stu-id="cfebe-109">DESCRIPTION</span></span>

<span data-ttu-id="cfebe-110">L' `Publish-Script` applet de commande publie le script spécifié dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="cfebe-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="cfebe-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cfebe-111">EXAMPLES</span></span>

### <span data-ttu-id="cfebe-112">Exemple 1 : créer un fichier de script, y ajouter du contenu et le publier</span><span class="sxs-lookup"><span data-stu-id="cfebe-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="cfebe-113">L' `New-ScriptFileInfo` applet de commande crée un fichier de script nommé `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cfebe-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="cfebe-114">`Get-Content` affiche le contenu de `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cfebe-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="cfebe-115">L' `Add-Content` applet de commande ajoute une fonction et un flux de travail à `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cfebe-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

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

<span data-ttu-id="cfebe-116">L’applet de commande est `Test-ScriptFileInfo` validée `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cfebe-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="cfebe-117">L' `Publish-Script` applet de commande publie le script dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="cfebe-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="cfebe-118">Enfin,</span><span class="sxs-lookup"><span data-stu-id="cfebe-118">Finally.</span></span> <span data-ttu-id="cfebe-119">`Find-Script` est utilisé pour rechercher `Demo-Script.ps1` dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="cfebe-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="cfebe-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cfebe-120">PARAMETERS</span></span>

### <span data-ttu-id="cfebe-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cfebe-121">-Confirm</span></span>

<span data-ttu-id="cfebe-122">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cfebe-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cfebe-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="cfebe-123">-Credential</span></span>

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

### <span data-ttu-id="cfebe-124">-Force</span><span class="sxs-lookup"><span data-stu-id="cfebe-124">-Force</span></span>

<span data-ttu-id="cfebe-125">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cfebe-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cfebe-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cfebe-126">-LiteralPath</span></span>

<span data-ttu-id="cfebe-127">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="cfebe-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="cfebe-128">Contrairement au paramètre **path** , la valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="cfebe-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="cfebe-129">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="cfebe-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="cfebe-130">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="cfebe-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="cfebe-131">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="cfebe-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="cfebe-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="cfebe-132">-NuGetApiKey</span></span>

<span data-ttu-id="cfebe-133">Spécifie la clé API que vous souhaitez utiliser pour publier un script dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="cfebe-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="cfebe-134">La clé API fait partie de votre profil dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="cfebe-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="cfebe-135">Pour plus d’informations, consultez [gestion des clés API](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span><span class="sxs-lookup"><span data-stu-id="cfebe-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="cfebe-136">-Path</span><span class="sxs-lookup"><span data-stu-id="cfebe-136">-Path</span></span>

<span data-ttu-id="cfebe-137">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="cfebe-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="cfebe-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cfebe-138">Wildcards are permitted.</span></span> <span data-ttu-id="cfebe-139">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="cfebe-139">The default location is the current directory.</span></span>

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

### <span data-ttu-id="cfebe-140">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="cfebe-140">-Repository</span></span>

<span data-ttu-id="cfebe-141">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="cfebe-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="cfebe-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cfebe-142">-WhatIf</span></span>

<span data-ttu-id="cfebe-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cfebe-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cfebe-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="cfebe-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cfebe-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cfebe-145">CommonParameters</span></span>

<span data-ttu-id="cfebe-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cfebe-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cfebe-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cfebe-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cfebe-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cfebe-148">INPUTS</span></span>

### <span data-ttu-id="cfebe-149">System.String</span><span class="sxs-lookup"><span data-stu-id="cfebe-149">System.String</span></span>

### <span data-ttu-id="cfebe-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="cfebe-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="cfebe-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cfebe-151">OUTPUTS</span></span>

### <span data-ttu-id="cfebe-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="cfebe-152">System.Object</span></span>

## <span data-ttu-id="cfebe-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cfebe-153">NOTES</span></span>

## <span data-ttu-id="cfebe-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cfebe-154">RELATED LINKS</span></span>

[<span data-ttu-id="cfebe-155">Find-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="cfebe-156">Install-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="cfebe-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="cfebe-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="cfebe-159">Update-Script</span><span class="sxs-lookup"><span data-stu-id="cfebe-159">Update-Script</span></span>](Update-Script.md)


---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 26fc71546c03fbb49bf8824f6779e6b6371daa0e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891139"
---
# <span data-ttu-id="f6beb-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-103">Publish-Script</span></span>

## <span data-ttu-id="f6beb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f6beb-104">SYNOPSIS</span></span>
<span data-ttu-id="f6beb-105">Publie un script.</span><span class="sxs-lookup"><span data-stu-id="f6beb-105">Publishes a script.</span></span>

## <span data-ttu-id="f6beb-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f6beb-106">SYNTAX</span></span>

### <span data-ttu-id="f6beb-107">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f6beb-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f6beb-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="f6beb-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f6beb-109">Description</span><span class="sxs-lookup"><span data-stu-id="f6beb-109">DESCRIPTION</span></span>

<span data-ttu-id="f6beb-110">L' `Publish-Script` applet de commande publie le script spécifié dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="f6beb-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="f6beb-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f6beb-111">EXAMPLES</span></span>

### <span data-ttu-id="f6beb-112">Exemple 1 : créer un fichier de script, y ajouter du contenu et le publier</span><span class="sxs-lookup"><span data-stu-id="f6beb-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="f6beb-113">L' `New-ScriptFileInfo` applet de commande crée un fichier de script nommé `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f6beb-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="f6beb-114">`Get-Content` affiche le contenu de `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f6beb-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="f6beb-115">L' `Add-Content` applet de commande ajoute une fonction et un flux de travail à `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f6beb-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

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

<span data-ttu-id="f6beb-116">L’applet de commande est `Test-ScriptFileInfo` validée `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f6beb-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="f6beb-117">L' `Publish-Script` applet de commande publie le script dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="f6beb-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="f6beb-118">Enfin,</span><span class="sxs-lookup"><span data-stu-id="f6beb-118">Finally.</span></span> <span data-ttu-id="f6beb-119">`Find-Script` est utilisé pour rechercher `Demo-Script.ps1` dans le référentiel **LocalRepo1** .</span><span class="sxs-lookup"><span data-stu-id="f6beb-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="f6beb-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6beb-120">PARAMETERS</span></span>

### <span data-ttu-id="f6beb-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f6beb-121">-Confirm</span></span>

<span data-ttu-id="f6beb-122">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f6beb-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f6beb-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="f6beb-123">-Credential</span></span>

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

### <span data-ttu-id="f6beb-124">-Force</span><span class="sxs-lookup"><span data-stu-id="f6beb-124">-Force</span></span>

<span data-ttu-id="f6beb-125">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f6beb-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f6beb-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f6beb-126">-LiteralPath</span></span>

<span data-ttu-id="f6beb-127">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="f6beb-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f6beb-128">Contrairement au paramètre **path** , la valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f6beb-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="f6beb-129">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="f6beb-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f6beb-130">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="f6beb-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="f6beb-131">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="f6beb-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="f6beb-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="f6beb-132">-NuGetApiKey</span></span>

<span data-ttu-id="f6beb-133">Spécifie la clé API que vous souhaitez utiliser pour publier un script dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="f6beb-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="f6beb-134">La clé API fait partie de votre profil dans la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="f6beb-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="f6beb-135">Pour plus d’informations, consultez [gestion des clés API](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span><span class="sxs-lookup"><span data-stu-id="f6beb-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="f6beb-136">-Path</span><span class="sxs-lookup"><span data-stu-id="f6beb-136">-Path</span></span>

<span data-ttu-id="f6beb-137">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="f6beb-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f6beb-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f6beb-138">Wildcards are permitted.</span></span> <span data-ttu-id="f6beb-139">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f6beb-139">The default location is the current directory.</span></span>

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

### <span data-ttu-id="f6beb-140">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="f6beb-140">-Repository</span></span>

<span data-ttu-id="f6beb-141">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="f6beb-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="f6beb-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f6beb-142">-WhatIf</span></span>

<span data-ttu-id="f6beb-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f6beb-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f6beb-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="f6beb-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f6beb-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6beb-145">CommonParameters</span></span>

<span data-ttu-id="f6beb-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f6beb-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6beb-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f6beb-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6beb-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f6beb-148">INPUTS</span></span>

### <span data-ttu-id="f6beb-149">System.String</span><span class="sxs-lookup"><span data-stu-id="f6beb-149">System.String</span></span>

### <span data-ttu-id="f6beb-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="f6beb-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="f6beb-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f6beb-151">OUTPUTS</span></span>

### <span data-ttu-id="f6beb-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="f6beb-152">System.Object</span></span>

## <span data-ttu-id="f6beb-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f6beb-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6beb-154">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="f6beb-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="f6beb-155">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f6beb-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="f6beb-156">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="f6beb-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="f6beb-157">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6beb-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="f6beb-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f6beb-158">RELATED LINKS</span></span>

[<span data-ttu-id="f6beb-159">Find-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="f6beb-160">Install-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="f6beb-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="f6beb-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="f6beb-163">Update-Script</span><span class="sxs-lookup"><span data-stu-id="f6beb-163">Update-Script</span></span>](Update-Script.md)

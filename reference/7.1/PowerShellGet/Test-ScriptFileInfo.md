---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: 4b02b853da5f42eb76d63ec38f77852df838bbe0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202602"
---
# <span data-ttu-id="a6d09-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a6d09-103">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="a6d09-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a6d09-104">SYNOPSIS</span></span>
<span data-ttu-id="a6d09-105">Valide un bloc de commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="a6d09-105">Validates a comment block for a script.</span></span>

## <span data-ttu-id="a6d09-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6d09-106">SYNTAX</span></span>

### <span data-ttu-id="a6d09-107">PathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a6d09-107">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="a6d09-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="a6d09-108">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="a6d09-109">Description</span><span class="sxs-lookup"><span data-stu-id="a6d09-109">DESCRIPTION</span></span>

<span data-ttu-id="a6d09-110">L’applet de commande **test-ScriptFileInfo** valide le bloc de commentaires au début d’un script qui sera publié avec l’applet de commande Publish-Script.</span><span class="sxs-lookup"><span data-stu-id="a6d09-110">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="a6d09-111">Si le bloc de commentaires contient une erreur, cette applet de commande retourne des informations sur l’emplacement de l’erreur ou sur la manière de la corriger.</span><span class="sxs-lookup"><span data-stu-id="a6d09-111">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="a6d09-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a6d09-112">EXAMPLES</span></span>

### <span data-ttu-id="a6d09-113">Exemple 1 : tester un fichier de script</span><span class="sxs-lookup"><span data-stu-id="a6d09-113">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="a6d09-114">Cette commande teste le New-ScriptFile.ps1 fichier de script et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="a6d09-114">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="a6d09-115">Le fichier de script contient des métadonnées valides.</span><span class="sxs-lookup"><span data-stu-id="a6d09-115">The script file includes valid metadata.</span></span>

### <span data-ttu-id="a6d09-116">Exemple 2 : tester un fichier de script qui a des valeurs pour toutes les propriétés de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a6d09-116">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="a6d09-117">Cette commande teste le fichier de script Test-Runbook.ps1 et utilise l’opérateur de pipeline pour transmettre les résultats à l’applet de commande Format-List pour mettre en forme les résultats.</span><span class="sxs-lookup"><span data-stu-id="a6d09-117">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="a6d09-118">Exemple 3 : tester un fichier de script qui n’a pas de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a6d09-118">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="a6d09-119">Cette commande teste le fichier de script Hello-World.ps1, à laquelle aucune métadonnée n’est associée.</span><span class="sxs-lookup"><span data-stu-id="a6d09-119">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="a6d09-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6d09-120">PARAMETERS</span></span>

### <span data-ttu-id="a6d09-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a6d09-121">-LiteralPath</span></span>

<span data-ttu-id="a6d09-122">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a6d09-122">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="a6d09-123">Contrairement au paramètre *path* , la valeur du paramètre *LiteralPath* est utilisée exactement telle qu’elle est entrée.</span><span class="sxs-lookup"><span data-stu-id="a6d09-123">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="a6d09-124">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a6d09-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="a6d09-125">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a6d09-125">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="a6d09-126">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a6d09-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a6d09-127">-Path</span><span class="sxs-lookup"><span data-stu-id="a6d09-127">-Path</span></span>

<span data-ttu-id="a6d09-128">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a6d09-128">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="a6d09-129">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a6d09-129">Wildcards are permitted.</span></span>
<span data-ttu-id="a6d09-130">L’emplacement par défaut est le répertoire actif (.).</span><span class="sxs-lookup"><span data-stu-id="a6d09-130">The default location is the current directory (.).</span></span>

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

### <span data-ttu-id="a6d09-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6d09-131">CommonParameters</span></span>

<span data-ttu-id="a6d09-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a6d09-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6d09-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a6d09-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6d09-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a6d09-134">INPUTS</span></span>

### <span data-ttu-id="a6d09-135">System.String</span><span class="sxs-lookup"><span data-stu-id="a6d09-135">System.String</span></span>

## <span data-ttu-id="a6d09-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a6d09-136">OUTPUTS</span></span>

### <span data-ttu-id="a6d09-137">System.Object</span><span class="sxs-lookup"><span data-stu-id="a6d09-137">System.Object</span></span>

## <span data-ttu-id="a6d09-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a6d09-138">NOTES</span></span>

## <span data-ttu-id="a6d09-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a6d09-139">RELATED LINKS</span></span>

[<span data-ttu-id="a6d09-140">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a6d09-140">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="a6d09-141">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="a6d09-141">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="a6d09-142">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="a6d09-142">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)


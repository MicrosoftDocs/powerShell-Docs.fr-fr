---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 8c96b4cd56073a9185ca4b0f0f13b866b839931d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201409"
---
# <span data-ttu-id="9dc05-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="9dc05-103">Get-InstalledModule</span></span>

## <span data-ttu-id="9dc05-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9dc05-104">SYNOPSIS</span></span>
<span data-ttu-id="9dc05-105">Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="9dc05-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="9dc05-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9dc05-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="9dc05-107">Description</span><span class="sxs-lookup"><span data-stu-id="9dc05-107">DESCRIPTION</span></span>

<span data-ttu-id="9dc05-108">L' `Get-InstalledModule` applet de commande obtient les modules PowerShell qui sont installés sur un ordinateur à l’aide de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="9dc05-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="9dc05-109">Pour afficher tous les modules installés sur le système, utilisez la `Get-Module -ListAvailable` commande.</span><span class="sxs-lookup"><span data-stu-id="9dc05-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="9dc05-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9dc05-110">EXAMPLES</span></span>

### <span data-ttu-id="9dc05-111">Exemple 1 : récupération de tous les modules installés</span><span class="sxs-lookup"><span data-stu-id="9dc05-111">Example 1: Get all installed modules</span></span>

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="9dc05-112">Cette commande obtient tous les modules installés.</span><span class="sxs-lookup"><span data-stu-id="9dc05-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="9dc05-113">Exemple 2 : obtenir des versions spécifiques d’un module</span><span class="sxs-lookup"><span data-stu-id="9dc05-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="9dc05-114">Cette commande obtient les versions du module AzureRM. Automation de la version 1,0 à la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="9dc05-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="9dc05-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9dc05-115">PARAMETERS</span></span>

### <span data-ttu-id="9dc05-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9dc05-116">-AllowPrerelease</span></span>

<span data-ttu-id="9dc05-117">Comprend dans les modules de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="9dc05-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="9dc05-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="9dc05-118">-AllVersions</span></span>

<span data-ttu-id="9dc05-119">Indique que vous souhaitez obtenir toutes les versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="9dc05-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="9dc05-120">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="9dc05-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="9dc05-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9dc05-121">-MaximumVersion</span></span>

<span data-ttu-id="9dc05-122">Spécifie la version maximale ou la plus récente d’un module à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9dc05-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="9dc05-123">Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="9dc05-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9dc05-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9dc05-124">-MinimumVersion</span></span>

<span data-ttu-id="9dc05-125">Spécifie la version minimale d’un module unique à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9dc05-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="9dc05-126">Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="9dc05-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9dc05-127">-Name</span><span class="sxs-lookup"><span data-stu-id="9dc05-127">-Name</span></span>

<span data-ttu-id="9dc05-128">Spécifie un tableau de noms de modules à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9dc05-128">Specifies an array of names of modules to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9dc05-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9dc05-129">-RequiredVersion</span></span>

<span data-ttu-id="9dc05-130">Spécifie la version exacte d’un module à obtenir.</span><span class="sxs-lookup"><span data-stu-id="9dc05-130">Specifies the exact version of a module to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9dc05-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9dc05-131">CommonParameters</span></span>

<span data-ttu-id="9dc05-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9dc05-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9dc05-133">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="9dc05-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9dc05-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9dc05-134">INPUTS</span></span>

### <span data-ttu-id="9dc05-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9dc05-135">System.String[]</span></span>

### <span data-ttu-id="9dc05-136">System.String</span><span class="sxs-lookup"><span data-stu-id="9dc05-136">System.String</span></span>

## <span data-ttu-id="9dc05-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9dc05-137">OUTPUTS</span></span>

### <span data-ttu-id="9dc05-138">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="9dc05-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="9dc05-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9dc05-139">NOTES</span></span>

## <span data-ttu-id="9dc05-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9dc05-140">RELATED LINKS</span></span>

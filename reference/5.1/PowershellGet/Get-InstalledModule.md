---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: e894e2f71e0a76badd05b86b42903d49aab4af0b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202889"
---
# <span data-ttu-id="0219b-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="0219b-103">Get-InstalledModule</span></span>

## <span data-ttu-id="0219b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0219b-104">SYNOPSIS</span></span>
<span data-ttu-id="0219b-105">Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="0219b-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="0219b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0219b-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="0219b-107">Description</span><span class="sxs-lookup"><span data-stu-id="0219b-107">DESCRIPTION</span></span>

<span data-ttu-id="0219b-108">L' `Get-InstalledModule` applet de commande obtient les modules PowerShell qui sont installés sur un ordinateur à l’aide de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="0219b-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="0219b-109">Pour afficher tous les modules installés sur le système, utilisez la `Get-Module -ListAvailable` commande.</span><span class="sxs-lookup"><span data-stu-id="0219b-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="0219b-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0219b-110">EXAMPLES</span></span>

### <span data-ttu-id="0219b-111">Exemple 1 : récupération de tous les modules installés</span><span class="sxs-lookup"><span data-stu-id="0219b-111">Example 1: Get all installed modules</span></span>

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

<span data-ttu-id="0219b-112">Cette commande obtient tous les modules installés.</span><span class="sxs-lookup"><span data-stu-id="0219b-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="0219b-113">Exemple 2 : obtenir des versions spécifiques d’un module</span><span class="sxs-lookup"><span data-stu-id="0219b-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="0219b-114">Cette commande obtient les versions du module AzureRM. Automation de la version 1,0 à la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="0219b-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="0219b-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0219b-115">PARAMETERS</span></span>

### <span data-ttu-id="0219b-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0219b-116">-AllowPrerelease</span></span>

<span data-ttu-id="0219b-117">Comprend dans les modules de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="0219b-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="0219b-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="0219b-118">-AllVersions</span></span>

<span data-ttu-id="0219b-119">Indique que vous souhaitez obtenir toutes les versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="0219b-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="0219b-120">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="0219b-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="0219b-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0219b-121">-MaximumVersion</span></span>

<span data-ttu-id="0219b-122">Spécifie la version maximale ou la plus récente d’un module à obtenir.</span><span class="sxs-lookup"><span data-stu-id="0219b-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="0219b-123">Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0219b-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0219b-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0219b-124">-MinimumVersion</span></span>

<span data-ttu-id="0219b-125">Spécifie la version minimale d’un module unique à obtenir.</span><span class="sxs-lookup"><span data-stu-id="0219b-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="0219b-126">Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0219b-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0219b-127">-Name</span><span class="sxs-lookup"><span data-stu-id="0219b-127">-Name</span></span>

<span data-ttu-id="0219b-128">Spécifie un tableau de noms de modules à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0219b-128">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="0219b-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0219b-129">-RequiredVersion</span></span>

<span data-ttu-id="0219b-130">Spécifie la version exacte d’un module à obtenir.</span><span class="sxs-lookup"><span data-stu-id="0219b-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="0219b-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0219b-131">CommonParameters</span></span>

<span data-ttu-id="0219b-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0219b-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0219b-133">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0219b-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0219b-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0219b-134">INPUTS</span></span>

## <span data-ttu-id="0219b-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0219b-135">OUTPUTS</span></span>

### <span data-ttu-id="0219b-136">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0219b-136">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="0219b-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0219b-137">NOTES</span></span>

## <span data-ttu-id="0219b-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0219b-138">RELATED LINKS</span></span>

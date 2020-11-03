---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: b3414b9f34787cc5285475d9de784fd779bd1431
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202721"
---
# <span data-ttu-id="86226-103">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="86226-103">Get-PackageProvider</span></span>

## <span data-ttu-id="86226-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="86226-104">SYNOPSIS</span></span>
<span data-ttu-id="86226-105">Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="86226-105">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="86226-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="86226-106">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="86226-107">Description</span><span class="sxs-lookup"><span data-stu-id="86226-107">DESCRIPTION</span></span>

<span data-ttu-id="86226-108">L’applet de commande **PackageProvider** renvoie une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="86226-108">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="86226-109">PSModule, NuGet et Chocolated sont des exemples de ces fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="86226-109">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="86226-110">Vous pouvez filtrer les résultats en fonction de l’ensemble ou d’une partie d’un ou plusieurs noms de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="86226-110">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="86226-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="86226-111">EXAMPLES</span></span>

### <span data-ttu-id="86226-112">Exemple 1 : récupération de tous les fournisseurs de packages actuellement chargés</span><span class="sxs-lookup"><span data-stu-id="86226-112">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="86226-113">Cette commande obtient la liste de tous les fournisseurs de packages qui sont actuellement chargés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86226-113">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="86226-114">Exemple 2 : récupération de tous les fournisseurs de packages disponibles</span><span class="sxs-lookup"><span data-stu-id="86226-114">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="86226-115">Cette commande obtient une liste de tous les fournisseurs de packages qui sont disponibles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86226-115">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="86226-116">Exemple 3 : obtenir dynamiquement un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="86226-116">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="86226-117">Cette commande installe automatiquement le fournisseur de Chocolate si le fournisseur de chocolat n’est pas installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86226-117">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="86226-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86226-118">PARAMETERS</span></span>

### <span data-ttu-id="86226-119">-Force</span><span class="sxs-lookup"><span data-stu-id="86226-119">-Force</span></span>

<span data-ttu-id="86226-120">Indique que cette applet de commande force toutes les autres actions avec cette applet de commande qui peuvent être forcées.</span><span class="sxs-lookup"><span data-stu-id="86226-120">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="86226-121">Dans la méthode **PackageProvider** , cela signifie que le paramètre *force* agit de la même manière que le paramètre *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="86226-121">In **Get-PackageProvider** , this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="86226-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="86226-122">-ForceBootstrap</span></span>

<span data-ttu-id="86226-123">Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="86226-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="86226-124">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="86226-124">-ListAvailable</span></span>

<span data-ttu-id="86226-125">Obtient tous les fournisseurs installés.</span><span class="sxs-lookup"><span data-stu-id="86226-125">Gets all installed providers.</span></span>
<span data-ttu-id="86226-126">La fonction **PackageProvider** obtient le fournisseur dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** , ainsi que dans les dossiers d’assembly du fournisseur de package :</span><span class="sxs-lookup"><span data-stu-id="86226-126">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="86226-127">**$env :P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env : Localappdata\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="86226-127">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="86226-128">Sans ce paramètre, la **PackageProvider** obtient uniquement les fournisseurs chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="86226-128">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="86226-129">-Name</span><span class="sxs-lookup"><span data-stu-id="86226-129">-Name</span></span>

<span data-ttu-id="86226-130">Spécifie un ou plusieurs noms de fournisseurs ou des noms de fournisseurs partiels.</span><span class="sxs-lookup"><span data-stu-id="86226-130">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="86226-131">Séparez les noms de fournisseurs multiples par des virgules.</span><span class="sxs-lookup"><span data-stu-id="86226-131">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="86226-132">Les valeurs valides pour ce paramètre incluent les noms des fournisseurs que vous avez installés avec des packages. PackageManagement est fourni avec un ensemble de fournisseurs par défaut, y compris les fournisseurs **PSModule** et **MSI** .</span><span class="sxs-lookup"><span data-stu-id="86226-132">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86226-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86226-133">CommonParameters</span></span>

<span data-ttu-id="86226-134">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86226-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86226-135">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="86226-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86226-136">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="86226-136">INPUTS</span></span>

## <span data-ttu-id="86226-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="86226-137">OUTPUTS</span></span>

### <span data-ttu-id="86226-138">PackageProvider []</span><span class="sxs-lookup"><span data-stu-id="86226-138">PackageProvider[]</span></span>

## <span data-ttu-id="86226-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="86226-139">NOTES</span></span>

## <span data-ttu-id="86226-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="86226-140">RELATED LINKS</span></span>

[<span data-ttu-id="86226-141">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="86226-141">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="86226-142">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="86226-142">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="86226-143">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="86226-143">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="86226-144">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="86226-144">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)


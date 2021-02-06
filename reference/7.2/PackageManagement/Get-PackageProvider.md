---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595717"
---
# <span data-ttu-id="f32ab-102">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f32ab-102">Get-PackageProvider</span></span>

## <span data-ttu-id="f32ab-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f32ab-103">SYNOPSIS</span></span>
<span data-ttu-id="f32ab-104">Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="f32ab-104">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="f32ab-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f32ab-105">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="f32ab-106">Description</span><span class="sxs-lookup"><span data-stu-id="f32ab-106">DESCRIPTION</span></span>

<span data-ttu-id="f32ab-107">L’applet de commande **PackageProvider** renvoie une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="f32ab-107">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="f32ab-108">PSModule, NuGet et Chocolated sont des exemples de ces fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="f32ab-108">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="f32ab-109">Vous pouvez filtrer les résultats en fonction de l’ensemble ou d’une partie d’un ou plusieurs noms de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="f32ab-109">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="f32ab-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f32ab-110">EXAMPLES</span></span>

### <span data-ttu-id="f32ab-111">Exemple 1 : récupération de tous les fournisseurs de packages actuellement chargés</span><span class="sxs-lookup"><span data-stu-id="f32ab-111">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="f32ab-112">Cette commande obtient la liste de tous les fournisseurs de packages qui sont actuellement chargés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f32ab-112">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="f32ab-113">Exemple 2 : récupération de tous les fournisseurs de packages disponibles</span><span class="sxs-lookup"><span data-stu-id="f32ab-113">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="f32ab-114">Cette commande obtient une liste de tous les fournisseurs de packages qui sont disponibles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f32ab-114">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="f32ab-115">Exemple 3 : obtenir dynamiquement un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="f32ab-115">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="f32ab-116">Cette commande installe automatiquement le fournisseur de Chocolate si le fournisseur de chocolat n’est pas installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f32ab-116">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="f32ab-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f32ab-117">PARAMETERS</span></span>

### <span data-ttu-id="f32ab-118">-Force</span><span class="sxs-lookup"><span data-stu-id="f32ab-118">-Force</span></span>

<span data-ttu-id="f32ab-119">Indique que cette applet de commande force toutes les autres actions avec cette applet de commande qui peuvent être forcées.</span><span class="sxs-lookup"><span data-stu-id="f32ab-119">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="f32ab-120">Dans la méthode **PackageProvider**, cela signifie que le paramètre *force* agit de la même manière que le paramètre *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="f32ab-120">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="f32ab-121">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="f32ab-121">-ForceBootstrap</span></span>

<span data-ttu-id="f32ab-122">Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="f32ab-122">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="f32ab-123">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="f32ab-123">-ListAvailable</span></span>

<span data-ttu-id="f32ab-124">Obtient tous les fournisseurs installés.</span><span class="sxs-lookup"><span data-stu-id="f32ab-124">Gets all installed providers.</span></span>
<span data-ttu-id="f32ab-125">La fonction **PackageProvider** obtient le fournisseur dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** , ainsi que dans les dossiers d’assembly du fournisseur de package :</span><span class="sxs-lookup"><span data-stu-id="f32ab-125">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="f32ab-126">**$env :P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env : Localappdata\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="f32ab-126">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="f32ab-127">Sans ce paramètre, la **PackageProvider** obtient uniquement les fournisseurs chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f32ab-127">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="f32ab-128">-Name</span><span class="sxs-lookup"><span data-stu-id="f32ab-128">-Name</span></span>

<span data-ttu-id="f32ab-129">Spécifie un ou plusieurs noms de fournisseurs ou des noms de fournisseurs partiels.</span><span class="sxs-lookup"><span data-stu-id="f32ab-129">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="f32ab-130">Séparez les noms de fournisseurs multiples par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f32ab-130">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="f32ab-131">Les valeurs valides pour ce paramètre incluent les noms des fournisseurs que vous avez installés avec des packages. PackageManagement est fourni avec un ensemble de fournisseurs par défaut, y compris les fournisseurs **PSModule** et **MSI** .</span><span class="sxs-lookup"><span data-stu-id="f32ab-131">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

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

### <span data-ttu-id="f32ab-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f32ab-132">CommonParameters</span></span>

<span data-ttu-id="f32ab-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f32ab-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f32ab-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f32ab-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f32ab-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f32ab-135">INPUTS</span></span>

## <span data-ttu-id="f32ab-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f32ab-136">OUTPUTS</span></span>

### <span data-ttu-id="f32ab-137">PackageProvider []</span><span class="sxs-lookup"><span data-stu-id="f32ab-137">PackageProvider[]</span></span>

## <span data-ttu-id="f32ab-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f32ab-138">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f32ab-139">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="f32ab-139">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="f32ab-140">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f32ab-140">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="f32ab-141">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="f32ab-141">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="f32ab-142">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f32ab-142">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="f32ab-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f32ab-143">RELATED LINKS</span></span>

[<span data-ttu-id="f32ab-144">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f32ab-144">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="f32ab-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f32ab-145">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="f32ab-146">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f32ab-146">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="f32ab-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f32ab-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

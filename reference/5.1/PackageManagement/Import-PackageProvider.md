---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 1ff00ea134c442e2bdb926d12ebbfa02098d6104
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202929"
---
# <span data-ttu-id="824ee-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="824ee-103">Import-PackageProvider</span></span>

## <span data-ttu-id="824ee-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="824ee-104">SYNOPSIS</span></span>
<span data-ttu-id="824ee-105">Ajoute Package Management fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="824ee-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="824ee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="824ee-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="824ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="824ee-107">DESCRIPTION</span></span>

<span data-ttu-id="824ee-108">L' `Import-PackageProvider` applet de commande ajoute un ou plusieurs fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="824ee-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="824ee-109">Le fournisseur que vous importez doit être installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="824ee-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="824ee-110">Pour obtenir la liste des fournisseurs disponibles, exécutez `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="824ee-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="824ee-111">Notez qu’un nom de fournisseur de package peut être différent de son nom de module.</span><span class="sxs-lookup"><span data-stu-id="824ee-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="824ee-112">Pour des raisons de sécurité, **PackageManagement** requiert que les fournisseurs C# contiennent un `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="824ee-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="824ee-113">Pour plus d’informations sur la façon de générer un fournisseur avec `provider.manifest` injecté, consultez les `.csproj` fichiers projet sur [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="824ee-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="824ee-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="824ee-114">EXAMPLES</span></span>

### <span data-ttu-id="824ee-115">Exemple 1 : importer un fournisseur de package à partir de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="824ee-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="824ee-116">Cette commande importe le fournisseur NuGet une fois qu’il a été installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="824ee-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="824ee-117">Exemple 2 : importer une version spécifique d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="824ee-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="824ee-118">Cette commande recherche, installe et importe une version spécifique du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="824ee-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="824ee-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="824ee-119">PARAMETERS</span></span>

### <span data-ttu-id="824ee-120">-Force</span><span class="sxs-lookup"><span data-stu-id="824ee-120">-Force</span></span>

<span data-ttu-id="824ee-121">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="824ee-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="824ee-122">Réimporte un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="824ee-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="824ee-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="824ee-123">-ForceBootstrap</span></span>

<span data-ttu-id="824ee-124">Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="824ee-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="824ee-125">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="824ee-125">-MaximumVersion</span></span>

<span data-ttu-id="824ee-126">Spécifie la version maximale autorisée du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="824ee-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="824ee-127">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="824ee-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="824ee-128">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="824ee-128">-MinimumVersion</span></span>

<span data-ttu-id="824ee-129">Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="824ee-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="824ee-130">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du package qui satisfait également à toute version maximale spécifiée à l’aide du paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="824ee-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="824ee-131">-Name</span><span class="sxs-lookup"><span data-stu-id="824ee-131">-Name</span></span>

<span data-ttu-id="824ee-132">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="824ee-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="824ee-133">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="824ee-133">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="824ee-134">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="824ee-134">-RequiredVersion</span></span>

<span data-ttu-id="824ee-135">Spécifie la version exacte du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="824ee-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="824ee-136">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur qui satisfait également à toute version maximale spécifiée à l’aide du paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="824ee-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="824ee-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="824ee-137">CommonParameters</span></span>

<span data-ttu-id="824ee-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="824ee-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="824ee-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="824ee-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="824ee-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="824ee-140">INPUTS</span></span>

### <span data-ttu-id="824ee-141">Microsoft. PackageManagement. implementation. PackageProvider</span><span class="sxs-lookup"><span data-stu-id="824ee-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="824ee-142">Vous pouvez diriger un objet **PackageProvider** retourné par `Get-PackageProvider` dans `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="824ee-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="824ee-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="824ee-143">OUTPUTS</span></span>

## <span data-ttu-id="824ee-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="824ee-144">NOTES</span></span>

## <span data-ttu-id="824ee-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="824ee-145">RELATED LINKS</span></span>

[<span data-ttu-id="824ee-146">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="824ee-146">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="824ee-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="824ee-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="824ee-148">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="824ee-148">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="824ee-149">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="824ee-149">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="824ee-150">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="824ee-150">Get-PackageProvider</span></span>](Get-PackageProvider.md)

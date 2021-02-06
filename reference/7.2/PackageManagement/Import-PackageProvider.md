---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597956"
---
# <span data-ttu-id="d899d-102">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d899d-102">Import-PackageProvider</span></span>

## <span data-ttu-id="d899d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d899d-103">SYNOPSIS</span></span>
<span data-ttu-id="d899d-104">Ajoute Package Management fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="d899d-104">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="d899d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d899d-105">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="d899d-106">Description</span><span class="sxs-lookup"><span data-stu-id="d899d-106">DESCRIPTION</span></span>

<span data-ttu-id="d899d-107">L' `Import-PackageProvider` applet de commande ajoute un ou plusieurs fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="d899d-107">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="d899d-108">Le fournisseur que vous importez doit être installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d899d-108">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="d899d-109">Pour obtenir la liste des fournisseurs disponibles, exécutez `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="d899d-109">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="d899d-110">Notez qu’un nom de fournisseur de package peut être différent de son nom de module.</span><span class="sxs-lookup"><span data-stu-id="d899d-110">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="d899d-111">Pour des raisons de sécurité, **PackageManagement** requiert que les fournisseurs C# contiennent un `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="d899d-111">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="d899d-112">Pour plus d’informations sur la façon de générer un fournisseur avec `provider.manifest` injecté, consultez les `.csproj` fichiers projet sur [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="d899d-112">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="d899d-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d899d-113">EXAMPLES</span></span>

### <span data-ttu-id="d899d-114">Exemple 1 : importer un fournisseur de package à partir de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="d899d-114">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="d899d-115">Cette commande importe le fournisseur NuGet une fois qu’il a été installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d899d-115">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="d899d-116">Exemple 2 : importer une version spécifique d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="d899d-116">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="d899d-117">Cette commande recherche, installe et importe une version spécifique du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="d899d-117">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="d899d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d899d-118">PARAMETERS</span></span>

### <span data-ttu-id="d899d-119">-Force</span><span class="sxs-lookup"><span data-stu-id="d899d-119">-Force</span></span>

<span data-ttu-id="d899d-120">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d899d-120">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="d899d-121">Réimporte un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="d899d-121">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="d899d-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d899d-122">-ForceBootstrap</span></span>

<span data-ttu-id="d899d-123">Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="d899d-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="d899d-124">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d899d-124">-MaximumVersion</span></span>

<span data-ttu-id="d899d-125">Spécifie la version maximale autorisée du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="d899d-125">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="d899d-126">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d899d-126">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="d899d-127">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d899d-127">-MinimumVersion</span></span>

<span data-ttu-id="d899d-128">Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="d899d-128">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="d899d-129">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du package qui satisfait également à toute version maximale spécifiée à l’aide du paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="d899d-129">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="d899d-130">-Name</span><span class="sxs-lookup"><span data-stu-id="d899d-130">-Name</span></span>

<span data-ttu-id="d899d-131">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="d899d-131">Specifies one or more package provider names.</span></span> <span data-ttu-id="d899d-132">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="d899d-132">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="d899d-133">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d899d-133">-RequiredVersion</span></span>

<span data-ttu-id="d899d-134">Spécifie la version exacte du fournisseur de packages que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="d899d-134">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="d899d-135">Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur qui satisfait également à toute version maximale spécifiée à l’aide du paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="d899d-135">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="d899d-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d899d-136">CommonParameters</span></span>

<span data-ttu-id="d899d-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d899d-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d899d-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d899d-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d899d-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d899d-139">INPUTS</span></span>

### <span data-ttu-id="d899d-140">Microsoft. PackageManagement. implementation. PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d899d-140">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="d899d-141">Vous pouvez diriger un objet **PackageProvider** retourné par `Get-PackageProvider` dans `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="d899d-141">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="d899d-142">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d899d-142">OUTPUTS</span></span>

## <span data-ttu-id="d899d-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d899d-143">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d899d-144">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="d899d-144">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d899d-145">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d899d-145">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d899d-146">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="d899d-146">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d899d-147">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d899d-147">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d899d-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d899d-148">RELATED LINKS</span></span>

[<span data-ttu-id="d899d-149">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d899d-149">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d899d-150">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d899d-150">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="d899d-151">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d899d-151">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d899d-152">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d899d-152">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d899d-153">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d899d-153">Get-PackageProvider</span></span>](Get-PackageProvider.md)

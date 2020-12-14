---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: 1a31fa29d9baa17f5bc1c2f48b9179c2ce071310
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890179"
---
# <span data-ttu-id="54b03-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="54b03-103">Find-PackageProvider</span></span>

## <span data-ttu-id="54b03-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="54b03-104">SYNOPSIS</span></span>
<span data-ttu-id="54b03-105">Retourne une liste de Package Management fournisseurs de packages disponibles pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="54b03-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="54b03-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="54b03-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="54b03-107">Description</span><span class="sxs-lookup"><span data-stu-id="54b03-107">DESCRIPTION</span></span>

<span data-ttu-id="54b03-108">L’applet de commande **Find-PackageProvider** recherche les fournisseurs PackageManagement correspondants qui sont disponibles dans les sources de package inscrites auprès de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="54b03-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="54b03-109">Il s’agit de fournisseurs de packages disponibles pour l’installation avec l’applet de commande Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="54b03-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="54b03-110">Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery avec les balises **PackageManagement** et **Provider** .</span><span class="sxs-lookup"><span data-stu-id="54b03-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="54b03-111">**Find-PackageProvider** recherche également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets Blob Azure Package Management.</span><span class="sxs-lookup"><span data-stu-id="54b03-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="54b03-112">Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.</span><span class="sxs-lookup"><span data-stu-id="54b03-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="54b03-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="54b03-113">EXAMPLES</span></span>

### <span data-ttu-id="54b03-114">Exemple 1 : Rechercher tous les fournisseurs de packages disponibles</span><span class="sxs-lookup"><span data-stu-id="54b03-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="54b03-115">Cette commande obtient une liste de tous les fournisseurs de packages qui sont disponibles dans les référentiels pris en charge par Package Management.</span><span class="sxs-lookup"><span data-stu-id="54b03-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="54b03-116">Par défaut, ces fournisseurs de packages sont disponibles sur le PowerShell Gallery et à l’aide de l’application d’amorçage Package Management.</span><span class="sxs-lookup"><span data-stu-id="54b03-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="54b03-117">Exemple 2 : Rechercher toutes les versions d’un fournisseur</span><span class="sxs-lookup"><span data-stu-id="54b03-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="54b03-118">Cette commande recherche toutes les versions du fournisseur de package nommé NuGet.</span><span class="sxs-lookup"><span data-stu-id="54b03-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="54b03-119">Exemple 3 : Rechercher un fournisseur à partir d’une source spécifiée</span><span class="sxs-lookup"><span data-stu-id="54b03-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="54b03-120">Cette commande recherche un fournisseur de package disponible à l’aide d’une source de package spécifiée.</span><span class="sxs-lookup"><span data-stu-id="54b03-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="54b03-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54b03-121">PARAMETERS</span></span>

### <span data-ttu-id="54b03-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="54b03-122">-AllVersions</span></span>

<span data-ttu-id="54b03-123">Indique que cette applet de commande retourne toutes les versions disponibles du fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="54b03-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="54b03-124">Par défaut, **Find-PackageProvider** retourne uniquement la version disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="54b03-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="54b03-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="54b03-125">-Credential</span></span>

<span data-ttu-id="54b03-126">Spécifie un compte d’utilisateur qui a l’autorisation de rechercher des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="54b03-126">Specifies a user account that has permission to search for package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54b03-127">-Force</span><span class="sxs-lookup"><span data-stu-id="54b03-127">-Force</span></span>

<span data-ttu-id="54b03-128">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54b03-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="54b03-129">Actuellement, cette valeur est équivalente au paramètre *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="54b03-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="54b03-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="54b03-130">-ForceBootstrap</span></span>

<span data-ttu-id="54b03-131">Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="54b03-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="54b03-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="54b03-132">-IncludeDependencies</span></span>

<span data-ttu-id="54b03-133">Indique que cette applet de commande comprend des dépendances.</span><span class="sxs-lookup"><span data-stu-id="54b03-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="54b03-134">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="54b03-134">-MaximumVersion</span></span>

<span data-ttu-id="54b03-135">Spécifie la version maximale autorisée du fournisseur de packages que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="54b03-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="54b03-136">Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version la plus élevée disponible du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="54b03-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="54b03-137">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="54b03-137">-MinimumVersion</span></span>

<span data-ttu-id="54b03-138">Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="54b03-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="54b03-139">Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version disponible la plus élevée du package qui satisfait également à la version maximale spécifiée spécifiée par le paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="54b03-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="54b03-140">-Name</span><span class="sxs-lookup"><span data-stu-id="54b03-140">-Name</span></span>

<span data-ttu-id="54b03-141">Spécifie un ou plusieurs noms de module du fournisseur de package, ou des noms de fournisseurs avec des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="54b03-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="54b03-142">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="54b03-142">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="54b03-143">-Proxy</span><span class="sxs-lookup"><span data-stu-id="54b03-143">-Proxy</span></span>

<span data-ttu-id="54b03-144">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="54b03-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54b03-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="54b03-145">-ProxyCredential</span></span>

<span data-ttu-id="54b03-146">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="54b03-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="54b03-147">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="54b03-147">-RequiredVersion</span></span>

<span data-ttu-id="54b03-148">Spécifie la version exacte du fournisseur de packages que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="54b03-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="54b03-149">Si vous n’ajoutez pas ce paramètre, **Find-PackageProvider** recherche la version disponible la plus élevée du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="54b03-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="54b03-150">-Source</span><span class="sxs-lookup"><span data-stu-id="54b03-150">-Source</span></span>

<span data-ttu-id="54b03-151">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="54b03-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="54b03-152">Vous pouvez obtenir la liste des sources de packages disponibles à l’aide de l’applet de commande Get-PackageSource.</span><span class="sxs-lookup"><span data-stu-id="54b03-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54b03-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54b03-153">CommonParameters</span></span>

<span data-ttu-id="54b03-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54b03-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54b03-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="54b03-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="54b03-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="54b03-156">INPUTS</span></span>

## <span data-ttu-id="54b03-157">SORTIES</span><span class="sxs-lookup"><span data-stu-id="54b03-157">OUTPUTS</span></span>

### <span data-ttu-id="54b03-158">Microsoft. PackageManagement. Packaging. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="54b03-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="54b03-159">Cette applet de commande retourne un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="54b03-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="54b03-160">Un objet **SoftwareIdentity** peut être transmis à **install-PackageProvider** pour installer les résultats de **Find-PackageProvider**.</span><span class="sxs-lookup"><span data-stu-id="54b03-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider**.</span></span>

## <span data-ttu-id="54b03-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="54b03-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54b03-162">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="54b03-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="54b03-163">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="54b03-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="54b03-164">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="54b03-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="54b03-165">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54b03-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="54b03-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="54b03-166">RELATED LINKS</span></span>

[<span data-ttu-id="54b03-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="54b03-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="54b03-168">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="54b03-168">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="54b03-169">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="54b03-169">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="54b03-170">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="54b03-170">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="54b03-171">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="54b03-171">Install-PackageProvider</span></span>](Install-PackageProvider.md)

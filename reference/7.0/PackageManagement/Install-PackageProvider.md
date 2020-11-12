---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: bd149e554528101e20cdc51ca728e679ed2cf28d
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524618"
---
# <span data-ttu-id="a7c38-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a7c38-103">Install-PackageProvider</span></span>

## <span data-ttu-id="a7c38-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a7c38-104">SYNOPSIS</span></span>
<span data-ttu-id="a7c38-105">Installe un ou plusieurs fournisseurs de packages Package Management.</span><span class="sxs-lookup"><span data-stu-id="a7c38-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="a7c38-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a7c38-106">SYNTAX</span></span>

### <span data-ttu-id="a7c38-107">PackageBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a7c38-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a7c38-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="a7c38-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a7c38-109">Description</span><span class="sxs-lookup"><span data-stu-id="a7c38-109">DESCRIPTION</span></span>

<span data-ttu-id="a7c38-110">L' `Install-PackageProvider` applet de commande installe les fournisseurs de Package Management correspondants qui sont disponibles dans les sources de package inscrites auprès de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="a7c38-110">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="a7c38-111">Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery Windows avec la balise **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a7c38-111">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="a7c38-112">Le fournisseur de Package Management **PowerShellGet** est utilisé pour rechercher des fournisseurs dans ces dépôts.</span><span class="sxs-lookup"><span data-stu-id="a7c38-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="a7c38-113">Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles à l’aide de l’application d’amorçage Package Management.</span><span class="sxs-lookup"><span data-stu-id="a7c38-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="a7c38-114">Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets BLOB Azure Package Management.</span><span class="sxs-lookup"><span data-stu-id="a7c38-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="a7c38-115">Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.</span><span class="sxs-lookup"><span data-stu-id="a7c38-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="a7c38-116">Pour pouvoir s’exécuter la première fois, PackageManagement requiert une connexion Internet pour télécharger le fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-116">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="a7c38-117">Toutefois, si votre ordinateur ne dispose pas d’une connexion Internet et que vous devez utiliser le fournisseur NuGet ou PowerShellGet, vous pouvez les télécharger sur un autre ordinateur et les copier sur votre ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a7c38-117">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="a7c38-118">Utilisez les étapes suivantes pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="a7c38-118">Use the following steps to do this:</span></span>

1. <span data-ttu-id="a7c38-119">Exécutez `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` pour installer le fournisseur à partir d’un ordinateur disposant d’une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="a7c38-120">Après l’installation, vous trouverez le fournisseur installé dans `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .</span><span class="sxs-lookup"><span data-stu-id="a7c38-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="a7c38-121">Placez le `<ProviderName>` dossier, qui est dans ce cas le dossier NuGet, à l’emplacement correspondant sur votre ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a7c38-121">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="a7c38-122">Si votre ordinateur cible est un serveur nano, vous devez exécuter `Install-PackageProvider` à partir de nano Server pour télécharger les fichiers binaires NuGet appropriés.</span><span class="sxs-lookup"><span data-stu-id="a7c38-122">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="a7c38-123">Redémarrez PowerShell pour charger automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a7c38-123">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="a7c38-124">Vous pouvez également exécuter `Get-PackageProvider -ListAvailable` pour répertorier tous les fournisseurs de packages disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a7c38-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="a7c38-125">Utilisez ensuite `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` pour importer le fournisseur dans la session Windows PowerShell actuelle.</span><span class="sxs-lookup"><span data-stu-id="a7c38-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="a7c38-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a7c38-126">EXAMPLES</span></span>

### <span data-ttu-id="a7c38-127">Exemple 1 : installer un fournisseur de package à partir de la PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="a7c38-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="a7c38-128">Cette commande installe le fournisseur de packages GistProvider à partir de l’PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a7c38-128">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="a7c38-129">Exemple 2 : installer une version spécifiée d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="a7c38-129">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="a7c38-130">Cet exemple installe une version spécifiée du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-130">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="a7c38-131">La première commande recherche toutes les versions du fournisseur de package nommé NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-131">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="a7c38-132">La deuxième commande installe une version spécifiée du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-132">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="a7c38-133">Exemple 3 : Rechercher un fournisseur et l’installer</span><span class="sxs-lookup"><span data-stu-id="a7c38-133">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="a7c38-134">Cet exemple utilise `Find-PackageProvider` et le pipeline pour rechercher le fournisseur du Registre et l’installer.</span><span class="sxs-lookup"><span data-stu-id="a7c38-134">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="a7c38-135">Exemple 4 : installer un fournisseur dans le dossier du module de l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="a7c38-135">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="a7c38-136">Cette commande installe un fournisseur de package pour `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` que seul l’utilisateur actuel puisse l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a7c38-136">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="a7c38-137">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="a7c38-137">PARAMETERS</span></span>

### <span data-ttu-id="a7c38-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a7c38-138">-AllVersions</span></span>

<span data-ttu-id="a7c38-139">Indique que cette applet de commande installe toutes les versions disponibles du fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a7c38-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="a7c38-140">Par défaut, `Install-PackageProvider` retourne uniquement la version la plus récente disponible.</span><span class="sxs-lookup"><span data-stu-id="a7c38-140">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="a7c38-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="a7c38-141">-Credential</span></span>

<span data-ttu-id="a7c38-142">Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="a7c38-142">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-143">-Force</span><span class="sxs-lookup"><span data-stu-id="a7c38-143">-Force</span></span>

<span data-ttu-id="a7c38-144">Indique que cette applet de commande force toutes les actions avec cette applet de commande qui peuvent être forcées.</span><span class="sxs-lookup"><span data-stu-id="a7c38-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="a7c38-145">Actuellement, cela signifie que le paramètre **force** agit de la même façon que le paramètre **ForceBootstrap** .</span><span class="sxs-lookup"><span data-stu-id="a7c38-145">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="a7c38-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a7c38-146">-ForceBootstrap</span></span>

<span data-ttu-id="a7c38-147">Indique que cette applet de commande installe automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a7c38-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="a7c38-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a7c38-148">-InputObject</span></span>

<span data-ttu-id="a7c38-149">Spécifie un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="a7c38-149">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="a7c38-150">Utilisez l' `Find-PackageProvider` applet de commande pour obtenir un objet **SoftwareIdentity** dans lequel canaliser `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="a7c38-150">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a7c38-151">-MaximumVersion</span></span>

<span data-ttu-id="a7c38-152">Spécifie la version maximale autorisée du fournisseur de package que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a7c38-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a7c38-153">Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus récente du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a7c38-153">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a7c38-154">-MinimumVersion</span></span>

<span data-ttu-id="a7c38-155">Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a7c38-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a7c38-156">Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus élevée du package qui répond également aux exigences spécifiées par le paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="a7c38-156">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-157">-Name</span><span class="sxs-lookup"><span data-stu-id="a7c38-157">-Name</span></span>

<span data-ttu-id="a7c38-158">Spécifie un ou plusieurs noms de module du fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a7c38-158">Specifies one or more package provider module names.</span></span> <span data-ttu-id="a7c38-159">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a7c38-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="a7c38-160">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a7c38-160">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a7c38-161">-Proxy</span></span>

<span data-ttu-id="a7c38-162">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="a7c38-162">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="a7c38-163">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a7c38-163">-ProxyCredential</span></span>

<span data-ttu-id="a7c38-164">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="a7c38-164">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a7c38-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a7c38-165">-RequiredVersion</span></span>

<span data-ttu-id="a7c38-166">Spécifie la version exacte du fournisseur de packages que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a7c38-166">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a7c38-167">Si vous n’ajoutez pas ce paramètre, `Install-PackageProvider` installe la version disponible la plus récente du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="a7c38-167">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-168">-Étendue</span><span class="sxs-lookup"><span data-stu-id="a7c38-168">-Scope</span></span>

<span data-ttu-id="a7c38-169">Spécifie l’étendue d’installation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a7c38-169">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="a7c38-170">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="a7c38-170">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a7c38-171">**ALLUSERS** -installe les fournisseurs à un emplacement accessible à tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a7c38-171">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="a7c38-172">Par défaut, il s’agit de **$env :P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="a7c38-172">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="a7c38-173">**CurrentUser** -installe les fournisseurs à un emplacement où ils sont uniquement accessibles à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a7c38-173">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="a7c38-174">Par défaut, il s’agit de **$env : LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="a7c38-174">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-175">-Source</span><span class="sxs-lookup"><span data-stu-id="a7c38-175">-Source</span></span>

<span data-ttu-id="a7c38-176">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="a7c38-176">Specifies one or more package sources.</span></span> <span data-ttu-id="a7c38-177">Utilisez l' `Get-PackageSource` applet de commande pour obtenir la liste des sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="a7c38-177">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a7c38-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a7c38-178">-Confirm</span></span>

<span data-ttu-id="a7c38-179">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7c38-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a7c38-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a7c38-180">-WhatIf</span></span>

<span data-ttu-id="a7c38-181">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7c38-181">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a7c38-182">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a7c38-182">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a7c38-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7c38-183">CommonParameters</span></span>

<span data-ttu-id="a7c38-184">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7c38-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7c38-185">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a7c38-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7c38-186">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a7c38-186">INPUTS</span></span>

### <span data-ttu-id="a7c38-187">Microsoft. PackageManagement. Packaging. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="a7c38-187">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="a7c38-188">Vous pouvez diriger un objet **SoftwareIdentity** vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7c38-188">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="a7c38-189">Utilisez `Find-PackageProvider` pour obtenir un objet **SoftwareIdentity** qui peut être dirigé vers `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="a7c38-189">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="a7c38-190">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a7c38-190">OUTPUTS</span></span>

## <span data-ttu-id="a7c38-191">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a7c38-191">NOTES</span></span>

## <span data-ttu-id="a7c38-192">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a7c38-192">RELATED LINKS</span></span>

[<span data-ttu-id="a7c38-193">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a7c38-193">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="a7c38-194">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a7c38-194">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="a7c38-195">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a7c38-195">Import-PackageProvider</span></span>](Import-PackageProvider.md)

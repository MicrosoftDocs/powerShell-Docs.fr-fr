---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ed69b50019b3393eeeda42a250d65d4dfb809a51
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204178"
---
# <span data-ttu-id="a4e4e-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a4e4e-103">Install-PackageProvider</span></span>

## <span data-ttu-id="a4e4e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a4e4e-104">SYNOPSIS</span></span>
<span data-ttu-id="a4e4e-105">Installe un ou plusieurs fournisseurs de packages Package Management.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="a4e4e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a4e4e-106">SYNTAX</span></span>

### <span data-ttu-id="a4e4e-107">PackageBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a4e4e-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a4e4e-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="a4e4e-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a4e4e-109">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4e-109">DESCRIPTION</span></span>

<span data-ttu-id="a4e4e-110">L’applet de commande **install-PackageProvider** installe les fournisseurs de Package Management correspondants qui sont disponibles dans les sources de package inscrites auprès de **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-110">The **Install-PackageProvider** cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet** .</span></span>
<span data-ttu-id="a4e4e-111">Par défaut, cela comprend les modules disponibles dans le PowerShell Gallery avec la balise **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-111">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** tag.</span></span>
<span data-ttu-id="a4e4e-112">Le fournisseur de Package Management **PowerShellGet** est utilisé pour rechercher des fournisseurs dans ces dépôts.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="a4e4e-113">Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles à l’aide de l’application d’amorçage Package Management.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="a4e4e-114">Cette applet de commande installe également les fournisseurs de Package Management correspondants qui sont disponibles dans le magasin d’objets BLOB Azure Package Management.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="a4e4e-115">Utilisez le fournisseur du programme d’amorçage pour les Rechercher et les installer.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="a4e4e-116">Pour pouvoir s’exécuter la première fois, PackageManagement requiert une connexion Internet pour télécharger le fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-116">In order to execute the first time, PackageManagement requires an internet connection to download the Nuget package provider.</span></span>
<span data-ttu-id="a4e4e-117">Toutefois, si votre ordinateur ne dispose pas d’une connexion Internet et que vous devez utiliser le fournisseur NuGet ou PowerShellGet, vous pouvez les télécharger sur un autre ordinateur et les copier sur votre ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-117">However, if your computer does not have an internet connection and you need to use the Nuget or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span>
<span data-ttu-id="a4e4e-118">Utilisez les étapes suivantes pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="a4e4e-118">Use the following steps to do this:</span></span>

1.
<span data-ttu-id="a4e4e-119">Exécutez `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` pour installer le fournisseur à partir d’un ordinateur disposant d’une connexion Internet.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>

2.
<span data-ttu-id="a4e4e-120">Après l’installation, vous trouverez le fournisseur installé dans `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>`.</span></span>

3.
<span data-ttu-id="a4e4e-121">Placez le \<ProviderName\> dossier, qui est dans ce cas le dossier NuGet, à l’emplacement correspondant sur votre ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-121">Place the \<ProviderName\> folder, which in this case is the Nuget folder, in the corresponding location on your target computer.</span></span>
<span data-ttu-id="a4e4e-122">Si votre ordinateur cible est un serveur nano, vous devez exécuter **install-PackageProvider** à partir de nano Server pour télécharger les fichiers binaires NuGet appropriés.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-122">If your target computer is a Nano server, you need to run **Install-PackageProvider** from Nano Server to download the correct Nuget binaries.</span></span>

4.
<span data-ttu-id="a4e4e-123">Redémarrez PowerShell pour charger automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-123">Restart PowerShell to auto-load the package provider.</span></span>
<span data-ttu-id="a4e4e-124">Vous pouvez également exécuter `Get-PackageProvider -ListAvailable` pour répertorier tous les fournisseurs de packages disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
<span data-ttu-id="a4e4e-125">Utilisez ensuite `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` pour importer le fournisseur dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current PowerShell session.</span></span>

## <span data-ttu-id="a4e4e-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a4e4e-126">EXAMPLES</span></span>

### <span data-ttu-id="a4e4e-127">Exemple 1 : installer un fournisseur de package à partir de la PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="a4e4e-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

<span data-ttu-id="a4e4e-128">Cette commande installe le Gistprovider à partir de la PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-128">This command installs the Gistprovider from the PowerShell Gallery.</span></span>

### <span data-ttu-id="a4e4e-129">Exemple 2 : installer une version spécifiée d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="a4e4e-129">Example 2: Install a specified version of a package provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

<span data-ttu-id="a4e4e-130">Cet exemple installe une version spécifiée du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-130">This example installs a specified version of the Nuget package provider.</span></span>

<span data-ttu-id="a4e4e-131">La première commande recherche toutes les versions du fournisseur de package nommé NuGet.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-131">The first command finds all versions of the package provider named Nuget.</span></span>
<span data-ttu-id="a4e4e-132">La deuxième commande installe une version spécifiée du fournisseur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-132">The second command installs a specified version of the Nuget package provider.</span></span>

### <span data-ttu-id="a4e4e-133">Exemple 3 : Rechercher un fournisseur et l’installer</span><span class="sxs-lookup"><span data-stu-id="a4e4e-133">Example 3: Find a provider and install it</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

<span data-ttu-id="a4e4e-134">Cette commande utilise **Find-PackageProvider** et le pipeline pour rechercher le fournisseur de l’aide et l’installer.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-134">This command uses **Find-PackageProvider** and the pipeline to search for the Gist provider and install it.</span></span>

### <span data-ttu-id="a4e4e-135">Exemple 4 : installer un fournisseur dans le dossier du module de l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="a4e4e-135">Example 4: Install a provider to the current user's module folder</span></span>

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

<span data-ttu-id="a4e4e-136">Cette commande installe un fournisseur de package pour $env : Localappdata\packagemanagement\providerassemblies. afin que seul l’utilisateur actuel puisse l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-136">This command installs a package provider to $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies so that only the current user can use it.</span></span>

## <span data-ttu-id="a4e4e-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a4e4e-137">PARAMETERS</span></span>

### <span data-ttu-id="a4e4e-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a4e4e-138">-AllVersions</span></span>

<span data-ttu-id="a4e4e-139">Indique que cette applet de commande installe toutes les versions disponibles du fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span>
<span data-ttu-id="a4e4e-140">Par défaut, **install-PackageProvider** retourne uniquement la version la plus récente disponible.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-140">By default, **Install-PackageProvider** only returns the highest available version.</span></span>

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

### <span data-ttu-id="a4e4e-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="a4e4e-141">-Credential</span></span>

<span data-ttu-id="a4e4e-142">Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-142">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="a4e4e-143">-Force</span><span class="sxs-lookup"><span data-stu-id="a4e4e-143">-Force</span></span>

<span data-ttu-id="a4e4e-144">Indique que cette applet de commande force toutes les actions avec cette applet de commande qui peuvent être forcées.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="a4e4e-145">Actuellement, cela signifie que le paramètre *force* agit de la même façon que le paramètre *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-145">Currently, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="a4e4e-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a4e4e-146">-ForceBootstrap</span></span>

<span data-ttu-id="a4e4e-147">Indique que cette applet de commande installe automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="a4e4e-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a4e4e-148">-InputObject</span></span>

<span data-ttu-id="a4e4e-149">Spécifie un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-149">Specifies a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="a4e4e-150">Utilisez l’applet de commande **Find-PackageProvider** pour obtenir un objet **SoftwareIdentity** pour canaliser dans **install-PackageProvider** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-150">Use the **Find-PackageProvider** cmdlet to obtain a **SoftwareIdentity** object to pipe into **Install-PackageProvider** .</span></span>

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

### <span data-ttu-id="a4e4e-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a4e4e-151">-MaximumVersion</span></span>

<span data-ttu-id="a4e4e-152">Spécifie la version maximale autorisée du fournisseur de package que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="a4e4e-153">Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus récente du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-153">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="a4e4e-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a4e4e-154">-MinimumVersion</span></span>

<span data-ttu-id="a4e4e-155">Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="a4e4e-156">Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus élevée du package qui répond également aux exigences spécifiées par le paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-156">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="a4e4e-157">-Name</span><span class="sxs-lookup"><span data-stu-id="a4e4e-157">-Name</span></span>

<span data-ttu-id="a4e4e-158">Spécifie un ou plusieurs noms de module du fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-158">Specifies one or more package provider module names.</span></span>
<span data-ttu-id="a4e4e-159">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="a4e4e-160">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-160">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="a4e4e-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a4e4e-161">-Proxy</span></span>

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

### <span data-ttu-id="a4e4e-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a4e4e-162">-ProxyCredential</span></span>

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

### <span data-ttu-id="a4e4e-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a4e4e-163">-RequiredVersion</span></span>

<span data-ttu-id="a4e4e-164">Spécifie la version exacte du fournisseur de packages que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-164">Specifies the exact allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="a4e4e-165">Si vous n’ajoutez pas ce paramètre, **install-PackageProvider** installe la version disponible la plus récente du fournisseur qui satisfait également à toute version maximale spécifiée par le paramètre *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-165">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="a4e4e-166">-Étendue</span><span class="sxs-lookup"><span data-stu-id="a4e4e-166">-Scope</span></span>

<span data-ttu-id="a4e4e-167">Spécifie l’étendue d’installation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-167">Specifies the installation scope of the provider.</span></span>
<span data-ttu-id="a4e4e-168">Les valeurs acceptables pour ce paramètre sont les suivantes : **ALLUSERS** et **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-168">The acceptable values for this parameter are: **AllUsers** and **CurrentUser** .</span></span>

<span data-ttu-id="a4e4e-169">L’étendue **ALLUSERS** installe les fournisseurs à un emplacement accessible à tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-169">The **AllUsers** scope installs providers in a location that is accessible to all users of the computer.</span></span>
<span data-ttu-id="a4e4e-170">Par défaut, il s’agit de **$env :P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="a4e4e-170">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

<span data-ttu-id="a4e4e-171">L’étendue **CurrentUser** installe les fournisseurs à un emplacement où ils sont accessibles uniquement à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-171">The **CurrentUser** scope installs providers in a location where they are only accessible to the current user.</span></span>
<span data-ttu-id="a4e4e-172">Par défaut, il s’agit de **$env : LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="a4e4e-172">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="a4e4e-173">-Source</span><span class="sxs-lookup"><span data-stu-id="a4e4e-173">-Source</span></span>

<span data-ttu-id="a4e4e-174">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-174">Specifies one or more package sources.</span></span>
<span data-ttu-id="a4e4e-175">Utilisez l’applet de commande Get-PackageSource pour obtenir la liste des sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-175">Use the Get-PackageSource cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="a4e4e-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a4e4e-176">-Confirm</span></span>

<span data-ttu-id="a4e4e-177">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a4e4e-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a4e4e-178">-WhatIf</span></span>

<span data-ttu-id="a4e4e-179">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a4e4e-180">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a4e4e-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a4e4e-181">CommonParameters</span></span>

<span data-ttu-id="a4e4e-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a4e4e-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a4e4e-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a4e4e-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a4e4e-184">INPUTS</span></span>

### <span data-ttu-id="a4e4e-185">Microsoft. PackageManagement. Packaging. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="a4e4e-185">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="a4e4e-186">Vous pouvez diriger un objet **SoftwareIdentity** vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a4e4e-186">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span>
<span data-ttu-id="a4e4e-187">Utilisez Find-PackageProvider pour obtenir un objet **SoftwareIdentity** qui peut être dirigé vers **install-PackageProvider** .</span><span class="sxs-lookup"><span data-stu-id="a4e4e-187">Use Find-PackageProvider to get a **SoftwareIdentity** object that can be piped into **Install-PackageProvider** .</span></span>

## <span data-ttu-id="a4e4e-188">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a4e4e-188">OUTPUTS</span></span>

## <span data-ttu-id="a4e4e-189">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a4e4e-189">NOTES</span></span>

## <span data-ttu-id="a4e4e-190">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a4e4e-190">RELATED LINKS</span></span>

[<span data-ttu-id="a4e4e-191">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a4e4e-191">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="a4e4e-192">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a4e4e-192">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="a4e4e-193">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a4e4e-193">Import-PackageProvider</span></span>](Import-PackageProvider.md)


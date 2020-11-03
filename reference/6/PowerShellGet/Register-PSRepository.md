---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: c42d13707e850990a8dcacfdaacec2b382c224a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204250"
---
# <span data-ttu-id="f0819-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f0819-103">Register-PSRepository</span></span>

## <span data-ttu-id="f0819-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f0819-104">SYNOPSIS</span></span>
<span data-ttu-id="f0819-105">Inscrit un référentiel PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0819-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="f0819-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0819-106">SYNTAX</span></span>

### <span data-ttu-id="f0819-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0819-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="f0819-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0819-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="f0819-109">Description</span><span class="sxs-lookup"><span data-stu-id="f0819-109">DESCRIPTION</span></span>

<span data-ttu-id="f0819-110">L' `Register-PSRepository` applet de commande inscrit le référentiel par défaut pour les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0819-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="f0819-111">Une fois qu’un référentiel est inscrit, vous pouvez le référencer à partir des `Find-Module` applets de commande, `Install-Module` et `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="f0819-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="f0819-112">Le référentiel inscrit devient le référentiel par défaut dans `Find-Module` et `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="f0819-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="f0819-113">Les référentiels enregistrés sont spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0819-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="f0819-114">Ils ne sont pas enregistrés dans un contexte à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="f0819-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="f0819-115">Chaque référentiel inscrit est associé à un fournisseur de packages OneGet, qui est spécifié avec le paramètre **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="f0819-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="f0819-116">Chaque fournisseur OneGet est conçu pour interagir avec un type spécifique de référentiel.</span><span class="sxs-lookup"><span data-stu-id="f0819-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="f0819-117">Par exemple, le fournisseur NuGet est conçu pour interagir avec les référentiels NuGet.</span><span class="sxs-lookup"><span data-stu-id="f0819-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="f0819-118">Si aucun fournisseur OneGet n’est spécifié lors de l’inscription, PowerShellGet tente de trouver un fournisseur OneGet pouvant gérer l’emplacement source spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0819-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="f0819-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f0819-119">EXAMPLES</span></span>

### <span data-ttu-id="f0819-120">Exemple 1 : inscrire un dépôt</span><span class="sxs-lookup"><span data-stu-id="f0819-120">Example 1: Register a repository</span></span>

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

<span data-ttu-id="f0819-121">La première commande s’inscrit `https://www.myget.org/F/powershellgetdemo/` en tant que référentiel pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="f0819-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="f0819-122">Une fois myNuGetSource inscrit, vous pouvez le référencer explicitement lors de la recherche, de l’installation et de la publication des modules.</span><span class="sxs-lookup"><span data-stu-id="f0819-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="f0819-123">Étant donné que le paramètre **PackageManagementProvider** n’est pas spécifié, le référentiel n’est pas associé explicitement à un fournisseur de packages OneGet, de sorte que PowerShellGet interroge les fournisseurs de packages disponibles et les associe au fournisseur NuGet.</span><span class="sxs-lookup"><span data-stu-id="f0819-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="f0819-124">La deuxième commande récupère les dépôts inscrits et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="f0819-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="f0819-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0819-125">PARAMETERS</span></span>

### <span data-ttu-id="f0819-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="f0819-126">-Credential</span></span>

<span data-ttu-id="f0819-127">Spécifie les informations d’identification d’un compte disposant des droits nécessaires pour inscrire un dépôt.</span><span class="sxs-lookup"><span data-stu-id="f0819-127">Specifies credentials of an account that has rights to register a repository.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-128">-Par défaut</span><span class="sxs-lookup"><span data-stu-id="f0819-128">-Default</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f0819-129">-InstallationPolicy</span></span>

<span data-ttu-id="f0819-130">Spécifie la stratégie d’installation.</span><span class="sxs-lookup"><span data-stu-id="f0819-130">Specifies the installation policy.</span></span> <span data-ttu-id="f0819-131">Les valeurs valides sont : approuvé, non approuvé.</span><span class="sxs-lookup"><span data-stu-id="f0819-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="f0819-132">La valeur par défaut n’est pas fiable.</span><span class="sxs-lookup"><span data-stu-id="f0819-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="f0819-133">La stratégie d’installation d’un référentiel spécifie le comportement PowerShell lors de l’installation à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="f0819-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="f0819-134">Lorsque vous installez des modules à partir d’un référentiel non approuvé, l’utilisateur est invité à confirmer l’installation.</span><span class="sxs-lookup"><span data-stu-id="f0819-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="f0819-135">Vous pouvez définir **InstallationPolicy** avec l’applet de commande `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="f0819-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-136">-Name</span><span class="sxs-lookup"><span data-stu-id="f0819-136">-Name</span></span>

<span data-ttu-id="f0819-137">Spécifie le nom du dépôt à inscrire.</span><span class="sxs-lookup"><span data-stu-id="f0819-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="f0819-138">Vous pouvez utiliser ce nom pour spécifier le référentiel dans les applets de commande telles que `Find-Module` et `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="f0819-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="f0819-139">-PackageManagementProvider</span></span>

<span data-ttu-id="f0819-140">Spécifie un fournisseur de packages OneGet.</span><span class="sxs-lookup"><span data-stu-id="f0819-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="f0819-141">Si vous ne spécifiez pas de valeur pour ce paramètre, PowerShellGet interroge les fournisseurs de packages disponibles et associe ce dépôt au premier fournisseur de package qui indique qu’il peut gérer le référentiel.</span><span class="sxs-lookup"><span data-stu-id="f0819-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f0819-142">-Proxy</span></span>

<span data-ttu-id="f0819-143">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="f0819-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f0819-144">-ProxyCredential</span></span>

<span data-ttu-id="f0819-145">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="f0819-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="f0819-146">-PublishLocation</span></span>

<span data-ttu-id="f0819-147">Spécifie l’URI de l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="f0819-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="f0819-148">Par exemple, pour les référentiels NuGet, l’emplacement de publication est semblable à `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="f0819-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="f0819-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="f0819-150">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="f0819-150">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="f0819-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="f0819-152">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="f0819-152">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-153">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="f0819-153">-SourceLocation</span></span>

<span data-ttu-id="f0819-154">Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="f0819-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="f0819-155">Un URI peut être un flux de serveur NuGet (situation la plus courante), HTTP, HTTPs, FTP ou un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="f0819-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="f0819-156">Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="f0819-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0819-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0819-157">CommonParameters</span></span>

<span data-ttu-id="f0819-158">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0819-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0819-159">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0819-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0819-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f0819-160">INPUTS</span></span>

### <span data-ttu-id="f0819-161">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="f0819-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="f0819-162">System.Uri</span><span class="sxs-lookup"><span data-stu-id="f0819-162">System.Uri</span></span>

## <span data-ttu-id="f0819-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f0819-163">OUTPUTS</span></span>

### <span data-ttu-id="f0819-164">System.Object</span><span class="sxs-lookup"><span data-stu-id="f0819-164">System.Object</span></span>

## <span data-ttu-id="f0819-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f0819-165">NOTES</span></span>

## <span data-ttu-id="f0819-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f0819-166">RELATED LINKS</span></span>

[<span data-ttu-id="f0819-167">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f0819-167">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="f0819-168">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f0819-168">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="f0819-169">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f0819-169">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

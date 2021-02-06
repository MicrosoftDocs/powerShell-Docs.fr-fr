---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 179e672a099cfb92275795a0dc6129581a0e0299
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603889"
---
# <span data-ttu-id="bd469-102">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="bd469-102">Register-PSRepository</span></span>

## <span data-ttu-id="bd469-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bd469-103">SYNOPSIS</span></span>
<span data-ttu-id="bd469-104">Inscrit un référentiel PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd469-104">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="bd469-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bd469-105">SYNTAX</span></span>

### <span data-ttu-id="bd469-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bd469-106">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="bd469-107">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="bd469-107">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="bd469-108">Description</span><span class="sxs-lookup"><span data-stu-id="bd469-108">DESCRIPTION</span></span>

<span data-ttu-id="bd469-109">L' `Register-PSRepository` applet de commande inscrit le référentiel par défaut pour les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd469-109">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="bd469-110">Une fois qu’un référentiel est inscrit, vous pouvez le référencer à partir des `Find-Module` applets de commande, `Install-Module` et `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="bd469-110">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="bd469-111">Le référentiel inscrit devient le référentiel par défaut dans `Find-Module` et `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="bd469-111">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="bd469-112">Les référentiels enregistrés sont spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bd469-112">Registered repositories are user-specific.</span></span> <span data-ttu-id="bd469-113">Ils ne sont pas enregistrés dans un contexte à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="bd469-113">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="bd469-114">Chaque référentiel inscrit est associé à un fournisseur de packages OneGet, qui est spécifié avec le paramètre **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="bd469-114">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="bd469-115">Chaque fournisseur OneGet est conçu pour interagir avec un type spécifique de référentiel.</span><span class="sxs-lookup"><span data-stu-id="bd469-115">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="bd469-116">Par exemple, le fournisseur NuGet est conçu pour interagir avec les référentiels NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd469-116">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="bd469-117">Si aucun fournisseur OneGet n’est spécifié lors de l’inscription, PowerShellGet tente de trouver un fournisseur OneGet pouvant gérer l’emplacement source spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd469-117">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="bd469-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bd469-118">EXAMPLES</span></span>

### <span data-ttu-id="bd469-119">Exemple 1 : inscrire un dépôt</span><span class="sxs-lookup"><span data-stu-id="bd469-119">Example 1: Register a repository</span></span>

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

<span data-ttu-id="bd469-120">La première commande s’inscrit `https://www.myget.org/F/powershellgetdemo/` en tant que référentiel pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bd469-120">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="bd469-121">Une fois myNuGetSource inscrit, vous pouvez le référencer explicitement lors de la recherche, de l’installation et de la publication des modules.</span><span class="sxs-lookup"><span data-stu-id="bd469-121">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="bd469-122">Étant donné que le paramètre **PackageManagementProvider** n’est pas spécifié, le référentiel n’est pas associé explicitement à un fournisseur de packages OneGet, de sorte que PowerShellGet interroge les fournisseurs de packages disponibles et les associe au fournisseur NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd469-122">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="bd469-123">La deuxième commande récupère les dépôts inscrits et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="bd469-123">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="bd469-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd469-124">PARAMETERS</span></span>

### <span data-ttu-id="bd469-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="bd469-125">-Credential</span></span>

<span data-ttu-id="bd469-126">Spécifie les informations d’identification d’un compte disposant des droits nécessaires pour inscrire un dépôt.</span><span class="sxs-lookup"><span data-stu-id="bd469-126">Specifies credentials of an account that has rights to register a repository.</span></span>

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

### <span data-ttu-id="bd469-127">-Par défaut</span><span class="sxs-lookup"><span data-stu-id="bd469-127">-Default</span></span>

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

### <span data-ttu-id="bd469-128">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="bd469-128">-InstallationPolicy</span></span>

<span data-ttu-id="bd469-129">Spécifie la stratégie d’installation.</span><span class="sxs-lookup"><span data-stu-id="bd469-129">Specifies the installation policy.</span></span> <span data-ttu-id="bd469-130">Les valeurs valides sont : approuvé, non approuvé.</span><span class="sxs-lookup"><span data-stu-id="bd469-130">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="bd469-131">La valeur par défaut n’est pas fiable.</span><span class="sxs-lookup"><span data-stu-id="bd469-131">The default value is UnTrusted.</span></span>

<span data-ttu-id="bd469-132">La stratégie d’installation d’un référentiel spécifie le comportement PowerShell lors de l’installation à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="bd469-132">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="bd469-133">Lorsque vous installez des modules à partir d’un référentiel non approuvé, l’utilisateur est invité à confirmer l’installation.</span><span class="sxs-lookup"><span data-stu-id="bd469-133">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="bd469-134">Vous pouvez définir **InstallationPolicy** avec l’applet de commande `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="bd469-134">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

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

### <span data-ttu-id="bd469-135">-Name</span><span class="sxs-lookup"><span data-stu-id="bd469-135">-Name</span></span>

<span data-ttu-id="bd469-136">Spécifie le nom du dépôt à inscrire.</span><span class="sxs-lookup"><span data-stu-id="bd469-136">Specifies the name of the repository to register.</span></span> <span data-ttu-id="bd469-137">Vous pouvez utiliser ce nom pour spécifier le référentiel dans les applets de commande telles que `Find-Module` et `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="bd469-137">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

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

### <span data-ttu-id="bd469-138">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="bd469-138">-PackageManagementProvider</span></span>

<span data-ttu-id="bd469-139">Spécifie un fournisseur de packages OneGet.</span><span class="sxs-lookup"><span data-stu-id="bd469-139">Specifies a OneGet package provider.</span></span> <span data-ttu-id="bd469-140">Si vous ne spécifiez pas de valeur pour ce paramètre, PowerShellGet interroge les fournisseurs de packages disponibles et associe ce dépôt au premier fournisseur de package qui indique qu’il peut gérer le référentiel.</span><span class="sxs-lookup"><span data-stu-id="bd469-140">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

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

### <span data-ttu-id="bd469-141">-Proxy</span><span class="sxs-lookup"><span data-stu-id="bd469-141">-Proxy</span></span>

<span data-ttu-id="bd469-142">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="bd469-142">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="bd469-143">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="bd469-143">-ProxyCredential</span></span>

<span data-ttu-id="bd469-144">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="bd469-144">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="bd469-145">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="bd469-145">-PublishLocation</span></span>

<span data-ttu-id="bd469-146">Spécifie l’URI de l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="bd469-146">Specifies the URI of the publish location.</span></span> <span data-ttu-id="bd469-147">Par exemple, pour les référentiels NuGet, l’emplacement de publication est semblable à `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="bd469-147">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="bd469-148">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="bd469-148">-ScriptPublishLocation</span></span>

<span data-ttu-id="bd469-149">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="bd469-149">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="bd469-150">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="bd469-150">-ScriptSourceLocation</span></span>

<span data-ttu-id="bd469-151">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="bd469-151">Specifies the script source location.</span></span>

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

### <span data-ttu-id="bd469-152">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="bd469-152">-SourceLocation</span></span>

<span data-ttu-id="bd469-153">Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="bd469-153">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="bd469-154">Un URI peut être un flux de serveur NuGet (situation la plus courante), HTTP, HTTPs, FTP ou un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="bd469-154">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="bd469-155">Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="bd469-155">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="bd469-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd469-156">CommonParameters</span></span>

<span data-ttu-id="bd469-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd469-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd469-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bd469-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd469-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bd469-159">INPUTS</span></span>

### <span data-ttu-id="bd469-160">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="bd469-160">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="bd469-161">System.Uri</span><span class="sxs-lookup"><span data-stu-id="bd469-161">System.Uri</span></span>

## <span data-ttu-id="bd469-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bd469-162">OUTPUTS</span></span>

### <span data-ttu-id="bd469-163">System.Object</span><span class="sxs-lookup"><span data-stu-id="bd469-163">System.Object</span></span>

## <span data-ttu-id="bd469-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bd469-164">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd469-165">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="bd469-165">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="bd469-166">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="bd469-166">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="bd469-167">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="bd469-167">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="bd469-168">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd469-168">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="bd469-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bd469-169">RELATED LINKS</span></span>

[<span data-ttu-id="bd469-170">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="bd469-170">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="bd469-171">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="bd469-171">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="bd469-172">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="bd469-172">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

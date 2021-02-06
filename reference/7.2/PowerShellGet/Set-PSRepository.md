---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: d6f3901ba389ff910dcc808d2e4296032617052c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603468"
---
# <span data-ttu-id="8289f-102">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8289f-102">Set-PSRepository</span></span>

## <span data-ttu-id="8289f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8289f-103">SYNOPSIS</span></span>
<span data-ttu-id="8289f-104">Définit des valeurs pour un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="8289f-104">Sets values for a registered repository.</span></span>

## <span data-ttu-id="8289f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8289f-105">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="8289f-106">Description</span><span class="sxs-lookup"><span data-stu-id="8289f-106">DESCRIPTION</span></span>

<span data-ttu-id="8289f-107">L' `Set-PSRepository` applet de commande définit des valeurs pour un référentiel de module inscrit.</span><span class="sxs-lookup"><span data-stu-id="8289f-107">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="8289f-108">Les paramètres sont persistants pour l’utilisateur actuel et s’appliquent à toutes les versions de PowerShell installées pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8289f-108">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="8289f-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8289f-109">EXAMPLES</span></span>

### <span data-ttu-id="8289f-110">Exemple 1 : définir la stratégie d’installation d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="8289f-110">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="8289f-111">Cette commande définit la stratégie d’installation pour le référentiel **myInternalSource** sur **approuvé**, de sorte que vous n’êtes pas invité à installer les modules à partir de cette source.</span><span class="sxs-lookup"><span data-stu-id="8289f-111">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="8289f-112">Exemple 2 : définir les emplacements source et de publication d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="8289f-112">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="8289f-113">Cette commande définit l’emplacement source et l’emplacement de publication de **myInternalSource** sur les URI spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8289f-113">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="8289f-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8289f-114">PARAMETERS</span></span>

### <span data-ttu-id="8289f-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="8289f-115">-Credential</span></span>

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

### <span data-ttu-id="8289f-116">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="8289f-116">-InstallationPolicy</span></span>

<span data-ttu-id="8289f-117">Spécifie la stratégie d’installation.</span><span class="sxs-lookup"><span data-stu-id="8289f-117">Specifies the installation policy.</span></span> <span data-ttu-id="8289f-118">Les valeurs valides sont : **approuvé**, **non** approuvé.</span><span class="sxs-lookup"><span data-stu-id="8289f-118">Valid values are: **Trusted**, **Untrusted**.</span></span>

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

### <span data-ttu-id="8289f-119">-Name</span><span class="sxs-lookup"><span data-stu-id="8289f-119">-Name</span></span>

<span data-ttu-id="8289f-120">Spécifie le nom du dépôt.</span><span class="sxs-lookup"><span data-stu-id="8289f-120">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8289f-121">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="8289f-121">-PackageManagementProvider</span></span>

<span data-ttu-id="8289f-122">Spécifie le fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="8289f-122">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="8289f-123">-Proxy</span><span class="sxs-lookup"><span data-stu-id="8289f-123">-Proxy</span></span>

<span data-ttu-id="8289f-124">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="8289f-124">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="8289f-125">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8289f-125">-ProxyCredential</span></span>

<span data-ttu-id="8289f-126">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="8289f-126">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="8289f-127">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="8289f-127">-PublishLocation</span></span>

<span data-ttu-id="8289f-128">Spécifie l’URI de l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="8289f-128">Specifies the URI of the publish location.</span></span> <span data-ttu-id="8289f-129">Par exemple, pour les référentiels NuGet, l’emplacement de publication est semblable à `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="8289f-129">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="8289f-130">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="8289f-130">-ScriptPublishLocation</span></span>

<span data-ttu-id="8289f-131">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="8289f-131">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="8289f-132">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="8289f-132">-ScriptSourceLocation</span></span>

<span data-ttu-id="8289f-133">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="8289f-133">Specifies the script source location.</span></span>

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

### <span data-ttu-id="8289f-134">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="8289f-134">-SourceLocation</span></span>

<span data-ttu-id="8289f-135">Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="8289f-135">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="8289f-136">Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="8289f-136">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8289f-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8289f-137">CommonParameters</span></span>

<span data-ttu-id="8289f-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8289f-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8289f-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8289f-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8289f-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8289f-140">INPUTS</span></span>

### <span data-ttu-id="8289f-141">System.String</span><span class="sxs-lookup"><span data-stu-id="8289f-141">System.String</span></span>

### <span data-ttu-id="8289f-142">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="8289f-142">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="8289f-143">System.Uri</span><span class="sxs-lookup"><span data-stu-id="8289f-143">System.Uri</span></span>

## <span data-ttu-id="8289f-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8289f-144">OUTPUTS</span></span>

### <span data-ttu-id="8289f-145">System.Object</span><span class="sxs-lookup"><span data-stu-id="8289f-145">System.Object</span></span>

## <span data-ttu-id="8289f-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8289f-146">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8289f-147">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="8289f-147">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8289f-148">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8289f-148">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8289f-149">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="8289f-149">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8289f-150">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8289f-150">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8289f-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8289f-151">RELATED LINKS</span></span>

[<span data-ttu-id="8289f-152">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8289f-152">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="8289f-153">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8289f-153">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="8289f-154">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8289f-154">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

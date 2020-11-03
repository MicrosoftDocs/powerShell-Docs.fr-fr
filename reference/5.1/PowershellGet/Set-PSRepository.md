---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 0734bda0a3462e39f799570c853cffa3e267c5db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203894"
---
# <span data-ttu-id="d32c9-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d32c9-103">Set-PSRepository</span></span>

## <span data-ttu-id="d32c9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d32c9-104">SYNOPSIS</span></span>
<span data-ttu-id="d32c9-105">Définit des valeurs pour un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="d32c9-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="d32c9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d32c9-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="d32c9-107">Description</span><span class="sxs-lookup"><span data-stu-id="d32c9-107">DESCRIPTION</span></span>

<span data-ttu-id="d32c9-108">L' `Set-PSRepository` applet de commande définit des valeurs pour un référentiel de module inscrit.</span><span class="sxs-lookup"><span data-stu-id="d32c9-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="d32c9-109">Les paramètres sont persistants pour l’utilisateur actuel et s’appliquent à toutes les versions de PowerShell installées pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d32c9-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="d32c9-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d32c9-110">EXAMPLES</span></span>

### <span data-ttu-id="d32c9-111">Exemple 1 : définir la stratégie d’installation d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="d32c9-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="d32c9-112">Cette commande définit la stratégie d’installation pour le référentiel **myInternalSource** sur **approuvé** , de sorte que vous n’êtes pas invité à installer les modules à partir de cette source.</span><span class="sxs-lookup"><span data-stu-id="d32c9-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted** , so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="d32c9-113">Exemple 2 : définir les emplacements source et de publication d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="d32c9-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="d32c9-114">Cette commande définit l’emplacement source et l’emplacement de publication de **myInternalSource** sur les URI spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d32c9-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="d32c9-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d32c9-115">PARAMETERS</span></span>

### <span data-ttu-id="d32c9-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="d32c9-116">-Credential</span></span>

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

### <span data-ttu-id="d32c9-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="d32c9-117">-InstallationPolicy</span></span>

<span data-ttu-id="d32c9-118">Spécifie la stratégie d’installation.</span><span class="sxs-lookup"><span data-stu-id="d32c9-118">Specifies the installation policy.</span></span> <span data-ttu-id="d32c9-119">Les valeurs valides sont : **approuvé** , **non** approuvé.</span><span class="sxs-lookup"><span data-stu-id="d32c9-119">Valid values are: **Trusted** , **Untrusted** .</span></span>

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

### <span data-ttu-id="d32c9-120">-Name</span><span class="sxs-lookup"><span data-stu-id="d32c9-120">-Name</span></span>

<span data-ttu-id="d32c9-121">Spécifie le nom du dépôt.</span><span class="sxs-lookup"><span data-stu-id="d32c9-121">Specifies the name of the repository.</span></span>

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

### <span data-ttu-id="d32c9-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d32c9-122">-PackageManagementProvider</span></span>

<span data-ttu-id="d32c9-123">Spécifie le fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="d32c9-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="d32c9-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d32c9-124">-Proxy</span></span>

<span data-ttu-id="d32c9-125">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="d32c9-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="d32c9-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d32c9-126">-ProxyCredential</span></span>

<span data-ttu-id="d32c9-127">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="d32c9-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d32c9-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d32c9-128">-PublishLocation</span></span>

<span data-ttu-id="d32c9-129">Spécifie l’URI de l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="d32c9-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="d32c9-130">Par exemple, pour les référentiels NuGet, l’emplacement de publication est semblable à `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="d32c9-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="d32c9-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d32c9-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="d32c9-132">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="d32c9-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="d32c9-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d32c9-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="d32c9-134">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="d32c9-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="d32c9-135">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="d32c9-135">-SourceLocation</span></span>

<span data-ttu-id="d32c9-136">Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="d32c9-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="d32c9-137">Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="d32c9-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="d32c9-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d32c9-138">CommonParameters</span></span>

<span data-ttu-id="d32c9-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d32c9-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d32c9-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d32c9-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d32c9-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d32c9-141">INPUTS</span></span>

### <span data-ttu-id="d32c9-142">System.String</span><span class="sxs-lookup"><span data-stu-id="d32c9-142">System.String</span></span>

### <span data-ttu-id="d32c9-143">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="d32c9-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="d32c9-144">System.Uri</span><span class="sxs-lookup"><span data-stu-id="d32c9-144">System.Uri</span></span>

## <span data-ttu-id="d32c9-145">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d32c9-145">OUTPUTS</span></span>

### <span data-ttu-id="d32c9-146">System.Object</span><span class="sxs-lookup"><span data-stu-id="d32c9-146">System.Object</span></span>

## <span data-ttu-id="d32c9-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d32c9-147">NOTES</span></span>

## <span data-ttu-id="d32c9-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d32c9-148">RELATED LINKS</span></span>

[<span data-ttu-id="d32c9-149">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d32c9-149">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="d32c9-150">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d32c9-150">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="d32c9-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d32c9-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

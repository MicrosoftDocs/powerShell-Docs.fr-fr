---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 6b6cf6b4056dd5907f6a43cd9cf6d491bc7512b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202557"
---
# <span data-ttu-id="b5d3c-103">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5d3c-103">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="b5d3c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b5d3c-104">SYNOPSIS</span></span>
<span data-ttu-id="b5d3c-105">Désactive l’authentification CredSSP sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-105">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="b5d3c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5d3c-106">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="b5d3c-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5d3c-107">DESCRIPTION</span></span>
<span data-ttu-id="b5d3c-108">L’applet de commande **Disable-WSManCredSSP** désactive l’authentification CredSSP (Credential Security Support Provider) sur un client ou sur un ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-108">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="b5d3c-109">Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="b5d3c-110">Utilisez cette applet de commande pour désactiver CredSSP sur le client en spécifiant le client dans le paramètre *role* .</span><span class="sxs-lookup"><span data-stu-id="b5d3c-110">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="b5d3c-111">Cette applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5d3c-111">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="b5d3c-112">Désactive CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-112">Disables CredSSP on the client.</span></span> <span data-ttu-id="b5d3c-113">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Client\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-113">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="b5d3c-114">Supprime tout paramètre WSMan/\* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-114">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="b5d3c-115">Utilisez cette applet de commande pour désactiver CredSSP sur le serveur en spécifiant le serveur dans le *rôle* .</span><span class="sxs-lookup"><span data-stu-id="b5d3c-115">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role* .</span></span>
<span data-ttu-id="b5d3c-116">Cette applet de commande effectue l’action suivante :</span><span class="sxs-lookup"><span data-stu-id="b5d3c-116">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="b5d3c-117">Désactive CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-117">Disables CredSSP on the server.</span></span> <span data-ttu-id="b5d3c-118">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-118">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="b5d3c-119">ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-119">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="b5d3c-120">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-120">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="b5d3c-121">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="b5d3c-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b5d3c-122">EXAMPLES</span></span>

### <span data-ttu-id="b5d3c-123">Exemple 1 : désactiver CredSSP sur un client</span><span class="sxs-lookup"><span data-stu-id="b5d3c-123">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="b5d3c-124">Cette commande désactive CredSSP sur le client, ce qui empêche la délégation aux serveurs.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-124">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="b5d3c-125">Exemple 2 : désactiver CredSSP sur un serveur</span><span class="sxs-lookup"><span data-stu-id="b5d3c-125">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="b5d3c-126">Cette commande désactive CredSSP sur le serveur, ce qui empêche la délégation des clients.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-126">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="b5d3c-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5d3c-127">PARAMETERS</span></span>

### <span data-ttu-id="b5d3c-128">-Rôle</span><span class="sxs-lookup"><span data-stu-id="b5d3c-128">-Role</span></span>
<span data-ttu-id="b5d3c-129">Spécifie s’il faut désactiver CredSSP en tant que client ou serveur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-129">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="b5d3c-130">Les valeurs acceptables pour ce paramètre sont : client et serveur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-130">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="b5d3c-131">Si vous spécifiez client, cette applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5d3c-131">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="b5d3c-132">Désactive CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-132">Disables CredSSP on the client.</span></span> <span data-ttu-id="b5d3c-133">Cette applet de commande définit WS-Management affecter la valeur false à **\<localhost|computername\> \Client\Auth\CredSSP** .</span><span class="sxs-lookup"><span data-stu-id="b5d3c-133">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="b5d3c-134">Supprime tout paramètre WSMan/\* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-134">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="b5d3c-135">Si vous spécifiez Server, cette applet de commande effectue l’action suivante :</span><span class="sxs-lookup"><span data-stu-id="b5d3c-135">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="b5d3c-136">Désactive CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-136">Disables CredSSP on the server.</span></span> <span data-ttu-id="b5d3c-137">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-137">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5d3c-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5d3c-138">CommonParameters</span></span>
<span data-ttu-id="b5d3c-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5d3c-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b5d3c-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5d3c-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b5d3c-141">INPUTS</span></span>

### <span data-ttu-id="b5d3c-142">Aucun</span><span class="sxs-lookup"><span data-stu-id="b5d3c-142">None</span></span>
<span data-ttu-id="b5d3c-143">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-143">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="b5d3c-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b5d3c-144">OUTPUTS</span></span>

### <span data-ttu-id="b5d3c-145">Aucun</span><span class="sxs-lookup"><span data-stu-id="b5d3c-145">None</span></span>
<span data-ttu-id="b5d3c-146">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-146">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b5d3c-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b5d3c-147">NOTES</span></span>

* <span data-ttu-id="b5d3c-148">Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-148">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="b5d3c-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b5d3c-149">RELATED LINKS</span></span>

[<span data-ttu-id="b5d3c-150">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5d3c-150">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b5d3c-151">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5d3c-151">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b5d3c-152">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5d3c-152">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b5d3c-153">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5d3c-153">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b5d3c-154">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5d3c-154">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b5d3c-155">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b5d3c-155">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b5d3c-156">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5d3c-156">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b5d3c-157">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b5d3c-157">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b5d3c-158">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5d3c-158">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="b5d3c-159">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5d3c-159">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="b5d3c-160">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b5d3c-160">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="b5d3c-161">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5d3c-161">Test-WSMan</span></span>](Test-WSMan.md)

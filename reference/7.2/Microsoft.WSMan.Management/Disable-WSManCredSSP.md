---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3260c88d57e98c0072af8621600a02901c561acb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599168"
---
# <span data-ttu-id="d4ca7-102">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d4ca7-102">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="d4ca7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d4ca7-103">SYNOPSIS</span></span>
<span data-ttu-id="d4ca7-104">Désactive l’authentification CredSSP sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-104">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="d4ca7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d4ca7-105">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="d4ca7-106">Description</span><span class="sxs-lookup"><span data-stu-id="d4ca7-106">DESCRIPTION</span></span>
<span data-ttu-id="d4ca7-107">L’applet de commande **Disable-WSManCredSSP** désactive l’authentification CredSSP (Credential Security Support Provider) sur un client ou sur un ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-107">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="d4ca7-108">Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-108">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="d4ca7-109">Utilisez cette applet de commande pour désactiver CredSSP sur le client en spécifiant le client dans le paramètre *role* .</span><span class="sxs-lookup"><span data-stu-id="d4ca7-109">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="d4ca7-110">Cette applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d4ca7-110">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="d4ca7-111">Désactive CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-111">Disables CredSSP on the client.</span></span> <span data-ttu-id="d4ca7-112">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Client\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-112">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="d4ca7-113">Supprime tout paramètre WSMan/\* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-113">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="d4ca7-114">Utilisez cette applet de commande pour désactiver CredSSP sur le serveur en spécifiant le serveur dans le *rôle*.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-114">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="d4ca7-115">Cette applet de commande effectue l’action suivante :</span><span class="sxs-lookup"><span data-stu-id="d4ca7-115">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="d4ca7-116">Désactive CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-116">Disables CredSSP on the server.</span></span> <span data-ttu-id="d4ca7-117">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-117">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="d4ca7-118">ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="d4ca7-119">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="d4ca7-120">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="d4ca7-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d4ca7-121">EXAMPLES</span></span>

### <span data-ttu-id="d4ca7-122">Exemple 1 : désactiver CredSSP sur un client</span><span class="sxs-lookup"><span data-stu-id="d4ca7-122">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="d4ca7-123">Cette commande désactive CredSSP sur le client, ce qui empêche la délégation aux serveurs.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-123">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="d4ca7-124">Exemple 2 : désactiver CredSSP sur un serveur</span><span class="sxs-lookup"><span data-stu-id="d4ca7-124">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="d4ca7-125">Cette commande désactive CredSSP sur le serveur, ce qui empêche la délégation des clients.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-125">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="d4ca7-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d4ca7-126">PARAMETERS</span></span>

### <span data-ttu-id="d4ca7-127">-Rôle</span><span class="sxs-lookup"><span data-stu-id="d4ca7-127">-Role</span></span>
<span data-ttu-id="d4ca7-128">Spécifie s’il faut désactiver CredSSP en tant que client ou serveur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-128">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="d4ca7-129">Les valeurs acceptables pour ce paramètre sont : client et serveur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-129">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="d4ca7-130">Si vous spécifiez client, cette applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d4ca7-130">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="d4ca7-131">Désactive CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-131">Disables CredSSP on the client.</span></span> <span data-ttu-id="d4ca7-132">Cette applet de commande définit WS-Management affecter la valeur false à **\<localhost|computername\> \Client\Auth\CredSSP** .</span><span class="sxs-lookup"><span data-stu-id="d4ca7-132">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="d4ca7-133">Supprime tout paramètre WSMan/\* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-133">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="d4ca7-134">Si vous spécifiez Server, cette applet de commande effectue l’action suivante :</span><span class="sxs-lookup"><span data-stu-id="d4ca7-134">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="d4ca7-135">Désactive CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-135">Disables CredSSP on the server.</span></span> <span data-ttu-id="d4ca7-136">Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-136">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="d4ca7-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4ca7-137">CommonParameters</span></span>
<span data-ttu-id="d4ca7-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4ca7-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d4ca7-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4ca7-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d4ca7-140">INPUTS</span></span>

### <span data-ttu-id="d4ca7-141">None</span><span class="sxs-lookup"><span data-stu-id="d4ca7-141">None</span></span>
<span data-ttu-id="d4ca7-142">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-142">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="d4ca7-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d4ca7-143">OUTPUTS</span></span>

### <span data-ttu-id="d4ca7-144">None</span><span class="sxs-lookup"><span data-stu-id="d4ca7-144">None</span></span>
<span data-ttu-id="d4ca7-145">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d4ca7-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d4ca7-146">NOTES</span></span>

* <span data-ttu-id="d4ca7-147">Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="d4ca7-147">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="d4ca7-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d4ca7-148">RELATED LINKS</span></span>

[<span data-ttu-id="d4ca7-149">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="d4ca7-149">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="d4ca7-150">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="d4ca7-150">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="d4ca7-151">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d4ca7-151">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="d4ca7-152">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="d4ca7-152">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="d4ca7-153">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d4ca7-153">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="d4ca7-154">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="d4ca7-154">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="d4ca7-155">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d4ca7-155">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="d4ca7-156">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="d4ca7-156">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="d4ca7-157">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d4ca7-157">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="d4ca7-158">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="d4ca7-158">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="d4ca7-159">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="d4ca7-159">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="d4ca7-160">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="d4ca7-160">Test-WSMan</span></span>](Test-WSMan.md)


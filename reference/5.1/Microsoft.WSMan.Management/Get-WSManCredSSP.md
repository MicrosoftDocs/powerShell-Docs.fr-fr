---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: ce2046a9df5d4d02d718d6408c7a196a753c9914
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208705"
---
# <span data-ttu-id="2e936-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e936-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="2e936-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2e936-104">SYNOPSIS</span></span>
<span data-ttu-id="2e936-105">Obtient la configuration liée au fournisseur CredSSP (Credential Security Support Provider) pour le client.</span><span class="sxs-lookup"><span data-stu-id="2e936-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="2e936-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e936-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="2e936-107">Description</span><span class="sxs-lookup"><span data-stu-id="2e936-107">DESCRIPTION</span></span>
<span data-ttu-id="2e936-108">L’applet de commande **obtenir-WSManCredSSP** obtient la configuration liée au fournisseur de prise en charge de la sécurité des informations d’identification du client et du serveur.</span><span class="sxs-lookup"><span data-stu-id="2e936-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="2e936-109">La sortie indique si l'authentification CredSSP (Credential Security Support Provider) est activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="2e936-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="2e936-110">Cette applet de commande affiche également les informations de configuration pour la stratégie **AllowFreshCredentials** de CredSSP.</span><span class="sxs-lookup"><span data-stu-id="2e936-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="2e936-111">Lorsque vous utilisez l’authentification CredSSP, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="2e936-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="2e936-112">Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance.</span><span class="sxs-lookup"><span data-stu-id="2e936-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="2e936-113">Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.</span><span class="sxs-lookup"><span data-stu-id="2e936-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="2e936-114">L'applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e936-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="2e936-115">Obtient le paramètre CredSSP WS-Management sur le client ( **\<localhost|computername\> \Client\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="2e936-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="2e936-116">Obtient le paramètre de stratégie CredSSP Windows **AllowFreshCredentials** .</span><span class="sxs-lookup"><span data-stu-id="2e936-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials** .</span></span>
- <span data-ttu-id="2e936-117">Obtient le paramètre CredSSP WS-Management sur le serveur ( **\<localhost|computername\> \Service\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="2e936-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="2e936-118">ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e936-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="2e936-119">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="2e936-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="2e936-120">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="2e936-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="2e936-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2e936-121">EXAMPLES</span></span>

### <span data-ttu-id="2e936-122">Exemple 1 : afficher la configuration CredSSP</span><span class="sxs-lookup"><span data-stu-id="2e936-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="2e936-123">Cette commande affiche les informations de configuration CredSSP pour le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="2e936-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="2e936-124">La sortie indique si cet ordinateur est configuré ou non pour CredSSP.</span><span class="sxs-lookup"><span data-stu-id="2e936-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="2e936-125">Si l'ordinateur est configuré pour CredSSP, la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2e936-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="2e936-126">Si l'ordinateur n'est pas configuré pour CredSSP, la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2e936-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="2e936-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e936-127">PARAMETERS</span></span>

### <span data-ttu-id="2e936-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e936-128">CommonParameters</span></span>
<span data-ttu-id="2e936-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e936-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e936-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2e936-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e936-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2e936-131">INPUTS</span></span>

### <span data-ttu-id="2e936-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="2e936-132">None</span></span>
<span data-ttu-id="2e936-133">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="2e936-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="2e936-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2e936-134">OUTPUTS</span></span>

### <span data-ttu-id="2e936-135">Aucun</span><span class="sxs-lookup"><span data-stu-id="2e936-135">None</span></span>
<span data-ttu-id="2e936-136">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="2e936-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2e936-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2e936-137">NOTES</span></span>

* <span data-ttu-id="2e936-138">Pour désactiver l'authentification CredSSP, utilisez l'applet de commande Disable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="2e936-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="2e936-139">Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="2e936-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="2e936-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2e936-140">RELATED LINKS</span></span>

[<span data-ttu-id="2e936-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e936-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="2e936-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e936-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="2e936-143">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e936-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="2e936-144">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2e936-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="2e936-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e936-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="2e936-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="2e936-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="2e936-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e936-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="2e936-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="2e936-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="2e936-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e936-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="2e936-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2e936-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="2e936-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="2e936-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="2e936-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="2e936-152">Test-WSMan</span></span>](Test-WSMan.md)
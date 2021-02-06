---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598754"
---
# <span data-ttu-id="82707-102">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82707-102">Get-WSManCredSSP</span></span>

## <span data-ttu-id="82707-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="82707-103">SYNOPSIS</span></span>
<span data-ttu-id="82707-104">Obtient la configuration liée au fournisseur CredSSP (Credential Security Support Provider) pour le client.</span><span class="sxs-lookup"><span data-stu-id="82707-104">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="82707-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="82707-105">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="82707-106">Description</span><span class="sxs-lookup"><span data-stu-id="82707-106">DESCRIPTION</span></span>
<span data-ttu-id="82707-107">L’applet de commande **obtenir-WSManCredSSP** obtient la configuration liée au fournisseur de prise en charge de la sécurité des informations d’identification du client et du serveur.</span><span class="sxs-lookup"><span data-stu-id="82707-107">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="82707-108">La sortie indique si l'authentification CredSSP (Credential Security Support Provider) est activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="82707-108">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="82707-109">Cette applet de commande affiche également les informations de configuration pour la stratégie **AllowFreshCredentials** de CredSSP.</span><span class="sxs-lookup"><span data-stu-id="82707-109">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="82707-110">Lorsque vous utilisez l’authentification CredSSP, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="82707-110">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="82707-111">Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance.</span><span class="sxs-lookup"><span data-stu-id="82707-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="82707-112">Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.</span><span class="sxs-lookup"><span data-stu-id="82707-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="82707-113">L'applet de commande effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="82707-113">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="82707-114">Obtient le paramètre CredSSP WS-Management sur le client (**\<localhost|computername\> \Client\Auth\CredSSP**).</span><span class="sxs-lookup"><span data-stu-id="82707-114">Gets the WS-Management CredSSP setting on the client (**\<localhost|computername\>\Client\Auth\CredSSP**).</span></span>
- <span data-ttu-id="82707-115">Obtient le paramètre de stratégie CredSSP Windows **AllowFreshCredentials**.</span><span class="sxs-lookup"><span data-stu-id="82707-115">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="82707-116">Obtient le paramètre CredSSP WS-Management sur le serveur (**\<localhost|computername\> \Service\Auth\CredSSP**).</span><span class="sxs-lookup"><span data-stu-id="82707-116">Gets the WS-Management CredSSP setting on the server (**\<localhost|computername\>\Service\Auth\CredSSP**).</span></span>

<span data-ttu-id="82707-117">ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="82707-117">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="82707-118">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="82707-118">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="82707-119">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="82707-119">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="82707-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="82707-120">EXAMPLES</span></span>

### <span data-ttu-id="82707-121">Exemple 1 : afficher la configuration CredSSP</span><span class="sxs-lookup"><span data-stu-id="82707-121">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="82707-122">Cette commande affiche les informations de configuration CredSSP pour le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="82707-122">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="82707-123">La sortie indique si cet ordinateur est configuré ou non pour CredSSP.</span><span class="sxs-lookup"><span data-stu-id="82707-123">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="82707-124">Si l'ordinateur est configuré pour CredSSP, la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="82707-124">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="82707-125">Si l'ordinateur n'est pas configuré pour CredSSP, la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="82707-125">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="82707-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82707-126">PARAMETERS</span></span>

### <span data-ttu-id="82707-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82707-127">CommonParameters</span></span>
<span data-ttu-id="82707-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82707-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82707-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82707-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82707-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="82707-130">INPUTS</span></span>

### <span data-ttu-id="82707-131">None</span><span class="sxs-lookup"><span data-stu-id="82707-131">None</span></span>
<span data-ttu-id="82707-132">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="82707-132">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="82707-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="82707-133">OUTPUTS</span></span>

### <span data-ttu-id="82707-134">None</span><span class="sxs-lookup"><span data-stu-id="82707-134">None</span></span>
<span data-ttu-id="82707-135">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="82707-135">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="82707-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="82707-136">NOTES</span></span>

* <span data-ttu-id="82707-137">Pour désactiver l'authentification CredSSP, utilisez l'applet de commande Disable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="82707-137">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="82707-138">Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="82707-138">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="82707-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="82707-139">RELATED LINKS</span></span>

[<span data-ttu-id="82707-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="82707-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="82707-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82707-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="82707-142">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="82707-142">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="82707-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82707-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="82707-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82707-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="82707-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="82707-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="82707-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82707-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="82707-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="82707-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="82707-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82707-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="82707-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82707-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="82707-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="82707-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="82707-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="82707-151">Test-WSMan</span></span>](Test-WSMan.md)


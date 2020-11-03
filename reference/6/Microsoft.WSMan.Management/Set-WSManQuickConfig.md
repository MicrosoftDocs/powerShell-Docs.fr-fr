---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e8bc5bc248eafe479f366397aa947845e94e190c
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206202"
---
# <span data-ttu-id="19b90-103">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="19b90-103">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="19b90-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="19b90-104">SYNOPSIS</span></span>
<span data-ttu-id="19b90-105">Configure l'ordinateur local pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="19b90-105">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="19b90-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="19b90-106">SYNTAX</span></span>

### <span data-ttu-id="19b90-107">Tous</span><span class="sxs-lookup"><span data-stu-id="19b90-107">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="19b90-108">Description</span><span class="sxs-lookup"><span data-stu-id="19b90-108">DESCRIPTION</span></span>

<span data-ttu-id="19b90-109">L' `Set-WSManQuickConfig` applet de commande configure l’ordinateur pour recevoir des commandes à distance PowerShell qui sont envoyées à l’aide de la technologie Web Services for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="19b90-109">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="19b90-110">`Set-WSManQuickConfig` effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="19b90-110">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="19b90-111">Vérifie si le service WinRM est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="19b90-111">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="19b90-112">Si le service WinRM n’est pas en cours d’exécution, le service est démarré.</span><span class="sxs-lookup"><span data-stu-id="19b90-112">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="19b90-113">Définit le type de démarrage du service WinRM sur Automatique.</span><span class="sxs-lookup"><span data-stu-id="19b90-113">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="19b90-114">Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="19b90-114">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="19b90-115">Le transport par défaut est **http** .</span><span class="sxs-lookup"><span data-stu-id="19b90-115">The default transport is **HTTP** .</span></span>
- <span data-ttu-id="19b90-116">Active une exception de pare-feu pour le trafic WinRM.</span><span class="sxs-lookup"><span data-stu-id="19b90-116">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="19b90-117">Pour exécuter `Set-WSManQuickConfig` , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="19b90-117">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="19b90-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="19b90-118">EXAMPLES</span></span>

### <span data-ttu-id="19b90-119">Exemple 1 : activer la gestion à distance de l’ordinateur local via HTTP</span><span class="sxs-lookup"><span data-stu-id="19b90-119">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="19b90-120">Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="19b90-120">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="19b90-121">Par défaut, cette commande crée un écouteur WS-Management sur **http** .</span><span class="sxs-lookup"><span data-stu-id="19b90-121">By default, this command creates a WS-Management listener on **HTTP** .</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="19b90-122">Exemple 2 : activer la gestion à distance de l’ordinateur local via HTTPs</span><span class="sxs-lookup"><span data-stu-id="19b90-122">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="19b90-123">Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="19b90-123">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="19b90-124">Le paramètre **UseSSL** spécifie que le **protocole HTTPS** est utilisé pour communiquer avec l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="19b90-124">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="19b90-125">**Https** nécessite une configuration manuelle.</span><span class="sxs-lookup"><span data-stu-id="19b90-125">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="19b90-126">Pour plus d’informations, consultez la description du paramètre **UseSSL** .</span><span class="sxs-lookup"><span data-stu-id="19b90-126">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="19b90-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="19b90-127">PARAMETERS</span></span>

### <span data-ttu-id="19b90-128">-Force</span><span class="sxs-lookup"><span data-stu-id="19b90-128">-Force</span></span>

<span data-ttu-id="19b90-129">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="19b90-129">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="19b90-130">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="19b90-130">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="19b90-131">Configure les versions du client Windows pour la communication à distance lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="19b90-131">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="19b90-132">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="19b90-132">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="19b90-133">Ce paramètre n’a aucun effet sur les versions serveur de Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="19b90-133">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="19b90-134">Si la règle de pare-feu de sous-réseau local est désactivée sur la version serveur de Windows, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="19b90-134">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="19b90-135">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="19b90-135">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="19b90-136">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="19b90-136">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="19b90-137">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="19b90-137">-UseSSL</span></span>

<span data-ttu-id="19b90-138">Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="19b90-138">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="19b90-139">Par défaut, SSL n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="19b90-139">By default, SSL isn't used.</span></span>

<span data-ttu-id="19b90-140">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="19b90-140">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="19b90-141">Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="19b90-141">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="19b90-142">Si vous utilisez ce paramètre et que le protocole SSL n’est pas disponible sur le port utilisé pour la connexion, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="19b90-142">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="19b90-143">**Https** requiert la configuration manuelle de WinRM et des règles de pare-feu.</span><span class="sxs-lookup"><span data-stu-id="19b90-143">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="19b90-144">Pour plus d’informations, consultez [Comment : configurer WINRM pour HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span><span class="sxs-lookup"><span data-stu-id="19b90-144">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="19b90-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="19b90-145">CommonParameters</span></span>

<span data-ttu-id="19b90-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="19b90-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="19b90-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="19b90-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="19b90-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="19b90-148">INPUTS</span></span>

### <span data-ttu-id="19b90-149">Aucun</span><span class="sxs-lookup"><span data-stu-id="19b90-149">None</span></span>

<span data-ttu-id="19b90-150">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="19b90-150">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="19b90-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="19b90-151">OUTPUTS</span></span>

### <span data-ttu-id="19b90-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="19b90-152">None</span></span>

<span data-ttu-id="19b90-153">Cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="19b90-153">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="19b90-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="19b90-154">NOTES</span></span>

## <span data-ttu-id="19b90-155">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="19b90-155">RELATED LINKS</span></span>

[<span data-ttu-id="19b90-156">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="19b90-156">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="19b90-157">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="19b90-157">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="19b90-158">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="19b90-158">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="19b90-159">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="19b90-159">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="19b90-160">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="19b90-160">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="19b90-161">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="19b90-161">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="19b90-162">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="19b90-162">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="19b90-163">Procédure : configurer WINRM pour HTTPs</span><span class="sxs-lookup"><span data-stu-id="19b90-163">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="19b90-164">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="19b90-164">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="19b90-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="19b90-165">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="19b90-166">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="19b90-166">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="19b90-167">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="19b90-167">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="19b90-168">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="19b90-168">Test-WSMan</span></span>](Test-WSMan.md)

---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e5d50af0551a183b8e9e1995fbd722c331a48486
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596098"
---
# <span data-ttu-id="4ce86-102">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="4ce86-102">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="4ce86-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4ce86-103">SYNOPSIS</span></span>
<span data-ttu-id="4ce86-104">Configure l'ordinateur local pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="4ce86-104">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="4ce86-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4ce86-105">SYNTAX</span></span>

### <span data-ttu-id="4ce86-106">Tous</span><span class="sxs-lookup"><span data-stu-id="4ce86-106">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="4ce86-107">Description</span><span class="sxs-lookup"><span data-stu-id="4ce86-107">DESCRIPTION</span></span>

<span data-ttu-id="4ce86-108">L' `Set-WSManQuickConfig` applet de commande configure l’ordinateur pour recevoir des commandes à distance PowerShell qui sont envoyées à l’aide de la technologie Web Services for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="4ce86-108">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="4ce86-109">`Set-WSManQuickConfig` effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ce86-109">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="4ce86-110">Vérifie si le service WinRM est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4ce86-110">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="4ce86-111">Si le service WinRM n’est pas en cours d’exécution, le service est démarré.</span><span class="sxs-lookup"><span data-stu-id="4ce86-111">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="4ce86-112">Définit le type de démarrage du service WinRM sur Automatique.</span><span class="sxs-lookup"><span data-stu-id="4ce86-112">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="4ce86-113">Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="4ce86-113">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="4ce86-114">Le transport par défaut est **http**.</span><span class="sxs-lookup"><span data-stu-id="4ce86-114">The default transport is **HTTP**.</span></span>
- <span data-ttu-id="4ce86-115">Active une exception de pare-feu pour le trafic WinRM.</span><span class="sxs-lookup"><span data-stu-id="4ce86-115">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="4ce86-116">Pour exécuter `Set-WSManQuickConfig` , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="4ce86-116">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="4ce86-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4ce86-117">EXAMPLES</span></span>

### <span data-ttu-id="4ce86-118">Exemple 1 : activer la gestion à distance de l’ordinateur local via HTTP</span><span class="sxs-lookup"><span data-stu-id="4ce86-118">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="4ce86-119">Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4ce86-119">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="4ce86-120">Par défaut, cette commande crée un écouteur WS-Management sur **http**.</span><span class="sxs-lookup"><span data-stu-id="4ce86-120">By default, this command creates a WS-Management listener on **HTTP**.</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="4ce86-121">Exemple 2 : activer la gestion à distance de l’ordinateur local via HTTPs</span><span class="sxs-lookup"><span data-stu-id="4ce86-121">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="4ce86-122">Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4ce86-122">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="4ce86-123">Le paramètre **UseSSL** spécifie que le **protocole HTTPS** est utilisé pour communiquer avec l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4ce86-123">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="4ce86-124">**Https** nécessite une configuration manuelle.</span><span class="sxs-lookup"><span data-stu-id="4ce86-124">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="4ce86-125">Pour plus d’informations, consultez la description du paramètre **UseSSL** .</span><span class="sxs-lookup"><span data-stu-id="4ce86-125">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="4ce86-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4ce86-126">PARAMETERS</span></span>

### <span data-ttu-id="4ce86-127">-Force</span><span class="sxs-lookup"><span data-stu-id="4ce86-127">-Force</span></span>

<span data-ttu-id="4ce86-128">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ce86-128">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4ce86-129">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="4ce86-129">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="4ce86-130">Configure les versions du client Windows pour la communication à distance lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="4ce86-130">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="4ce86-131">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="4ce86-131">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="4ce86-132">Ce paramètre n’a aucun effet sur les versions serveur de Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="4ce86-132">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="4ce86-133">Si la règle de pare-feu de sous-réseau local est désactivée sur la version serveur de Windows, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4ce86-133">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="4ce86-134">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="4ce86-134">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="4ce86-135">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4ce86-135">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="4ce86-136">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="4ce86-136">-UseSSL</span></span>

<span data-ttu-id="4ce86-137">Spécifie que le protocole SSL (Secure Sockets Layer) (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="4ce86-137">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="4ce86-138">Par défaut, SSL n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="4ce86-138">By default, SSL isn't used.</span></span>

<span data-ttu-id="4ce86-139">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="4ce86-139">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="4ce86-140">Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="4ce86-140">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="4ce86-141">Si vous utilisez ce paramètre et que le protocole SSL n’est pas disponible sur le port utilisé pour la connexion, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="4ce86-141">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="4ce86-142">**Https** requiert la configuration manuelle de WinRM et des règles de pare-feu.</span><span class="sxs-lookup"><span data-stu-id="4ce86-142">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="4ce86-143">Pour plus d’informations, consultez [Comment : configurer WINRM pour HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span><span class="sxs-lookup"><span data-stu-id="4ce86-143">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

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

### <span data-ttu-id="4ce86-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ce86-144">CommonParameters</span></span>

<span data-ttu-id="4ce86-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ce86-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ce86-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ce86-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ce86-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4ce86-147">INPUTS</span></span>

### <span data-ttu-id="4ce86-148">None</span><span class="sxs-lookup"><span data-stu-id="4ce86-148">None</span></span>

<span data-ttu-id="4ce86-149">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="4ce86-149">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="4ce86-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4ce86-150">OUTPUTS</span></span>

### <span data-ttu-id="4ce86-151">None</span><span class="sxs-lookup"><span data-stu-id="4ce86-151">None</span></span>

<span data-ttu-id="4ce86-152">Cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="4ce86-152">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="4ce86-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4ce86-153">NOTES</span></span>

## <span data-ttu-id="4ce86-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4ce86-154">RELATED LINKS</span></span>

[<span data-ttu-id="4ce86-155">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="4ce86-155">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="4ce86-156">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4ce86-156">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="4ce86-157">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="4ce86-157">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="4ce86-158">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="4ce86-158">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="4ce86-159">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4ce86-159">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="4ce86-160">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="4ce86-160">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="4ce86-161">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4ce86-161">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="4ce86-162">Procédure : configurer WINRM pour HTTPs</span><span class="sxs-lookup"><span data-stu-id="4ce86-162">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="4ce86-163">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="4ce86-163">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="4ce86-164">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4ce86-164">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="4ce86-165">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4ce86-165">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="4ce86-166">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="4ce86-166">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="4ce86-167">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="4ce86-167">Test-WSMan</span></span>](Test-WSMan.md)


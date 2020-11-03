---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205306"
---
# <span data-ttu-id="0aa42-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="0aa42-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="0aa42-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0aa42-104">SYNOPSIS</span></span>
<span data-ttu-id="0aa42-105">Configure l'ordinateur pour recevoir des commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="0aa42-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="0aa42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0aa42-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0aa42-107">Description</span><span class="sxs-lookup"><span data-stu-id="0aa42-107">DESCRIPTION</span></span>

<span data-ttu-id="0aa42-108">L' `Enable-PSRemoting` applet de commande configure l’ordinateur pour qu’il reçoive les commandes PowerShell à distance qui sont envoyées à l’aide de la technologie WS-Management.</span><span class="sxs-lookup"><span data-stu-id="0aa42-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span>

<span data-ttu-id="0aa42-109">La communication à distance PowerShell est activée par défaut sur Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="0aa42-109">PowerShell remoting is enabled by default on Windows Server 2012.</span></span> <span data-ttu-id="0aa42-110">Vous pouvez utiliser `Enable-PSRemoting` pour activer la communication à distance PowerShell sur d’autres versions de Windows prises en charge et pour réactiver la communication à distance sur Windows Server 2012 si elle est désactivée.</span><span class="sxs-lookup"><span data-stu-id="0aa42-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting on Windows Server 2012 if it becomes disabled.</span></span>

<span data-ttu-id="0aa42-111">Vous ne devez exécuter cette commande qu’une seule fois sur chaque ordinateur qui recevra des commandes.</span><span class="sxs-lookup"><span data-stu-id="0aa42-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="0aa42-112">Vous n’avez pas besoin de l’exécuter sur les ordinateurs qui envoient uniquement des commandes.</span><span class="sxs-lookup"><span data-stu-id="0aa42-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="0aa42-113">Étant donné que la configuration démarre les écouteurs, il est prudent de l’exécuter uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0aa42-113">Because the configuration starts listeners, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="0aa42-114">À compter de PowerShell 3,0, l' `Enable-PSRemoting` applet de commande peut activer la communication à distance PowerShell sur les versions client de Windows lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="0aa42-114">Beginning in PowerShell 3.0, the `Enable-PSRemoting` cmdlet can enable PowerShell remoting on client versions of Windows when the computer is on a public network.</span></span> <span data-ttu-id="0aa42-115">Pour plus d'informations, consultez la description du paramètre **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="0aa42-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="0aa42-116">L' `Enable-PSRemoting` applet de commande effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0aa42-116">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="0aa42-117">Exécute l’applet de commande [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) , qui effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0aa42-117">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="0aa42-118">Démarre le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="0aa42-118">Starts the WinRM service.</span></span>
  - <span data-ttu-id="0aa42-119">Définit le type de démarrage du service WinRM sur automatique.</span><span class="sxs-lookup"><span data-stu-id="0aa42-119">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="0aa42-120">Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="0aa42-120">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="0aa42-121">Active une exception de pare-feu pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="0aa42-121">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="0aa42-122">Inscrit les configurations de session **Microsoft. PowerShell** et **Microsoft. PowerShell. Workflow** , si elles ne sont pas déjà inscrites.</span><span class="sxs-lookup"><span data-stu-id="0aa42-122">Registers the **Microsoft.PowerShell** and **Microsoft.PowerShell.Workflow** session configurations, if it they are not already registered.</span></span>
  - <span data-ttu-id="0aa42-123">Inscrit la configuration de session **Microsoft. powershell32** sur les ordinateurs 64 bits, si elle n’est pas déjà inscrite.</span><span class="sxs-lookup"><span data-stu-id="0aa42-123">Registers the **Microsoft.PowerShell32** session configuration on 64-bit computers, if it is not already registered.</span></span>
  - <span data-ttu-id="0aa42-124">Active toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="0aa42-124">Enables all session configurations.</span></span>
  - <span data-ttu-id="0aa42-125">Modifie le descripteur de sécurité de toutes les configurations de session pour autoriser l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="0aa42-125">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="0aa42-126">Redémarre le service WinRM pour que les modifications précédentes soient effectives.</span><span class="sxs-lookup"><span data-stu-id="0aa42-126">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="0aa42-127">Pour exécuter cette applet de commande sur la plateforme Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="0aa42-127">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="0aa42-128">Cela ne s’applique pas aux versions Linux ou MacOS de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0aa42-128">This does not apply to Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="0aa42-129">Sur les systèmes qui ont à la fois PowerShell 3,0 et PowerShell 2,0, n’utilisez pas PowerShell 2,0 pour exécuter les `Enable-PSRemoting` applets de commande et `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="0aa42-129">On systems that have both PowerShell 3.0 and PowerShell 2.0, do not use PowerShell 2.0 to run the `Enable-PSRemoting` and `Disable-PSRemoting` cmdlets.</span></span> <span data-ttu-id="0aa42-130">Les commandes peuvent sembler réussir, mais la communication à distance n'est pas configurée correctement.</span><span class="sxs-lookup"><span data-stu-id="0aa42-130">The commands might appear to succeed, but the remoting is not configured correctly.</span></span> <span data-ttu-id="0aa42-131">Les commandes distantes et les tentatives ultérieures d’activation et de désactivation de la communication à distance sont susceptibles d’échouer.</span><span class="sxs-lookup"><span data-stu-id="0aa42-131">Remote commands and later attempts to enable and disable remoting, are likely to fail.</span></span>

## <span data-ttu-id="0aa42-132">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0aa42-132">EXAMPLES</span></span>

### <span data-ttu-id="0aa42-133">Exemple 1 : configurer un ordinateur pour recevoir des commandes à distance</span><span class="sxs-lookup"><span data-stu-id="0aa42-133">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="0aa42-134">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="0aa42-134">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

### <span data-ttu-id="0aa42-135">Exemple 2 : configurer un ordinateur pour qu’il reçoive des commandes distantes sans invite de confirmation</span><span class="sxs-lookup"><span data-stu-id="0aa42-135">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="0aa42-136">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="0aa42-136">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="0aa42-137">Le paramètre **force** supprime les invites utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0aa42-137">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

### <span data-ttu-id="0aa42-138">Exemple 3 : autoriser l’accès à distance sur les clients</span><span class="sxs-lookup"><span data-stu-id="0aa42-138">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="0aa42-139">Cet exemple montre comment autoriser l’accès à distance à partir de réseaux publics sur des versions clientes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="0aa42-139">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="0aa42-140">Le nom de la règle de pare-feu peut être différent pour les différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="0aa42-140">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="0aa42-141">Utilisez `Get-NetFirewallRule` pour afficher une liste de règles.</span><span class="sxs-lookup"><span data-stu-id="0aa42-141">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="0aa42-142">Avant d’activer la règle de pare-feu, affichez les paramètres de sécurité de la règle pour vérifier que la configuration est adaptée à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0aa42-142">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="0aa42-143">Par défaut, `Enable-PSRemoting` crée des règles de réseau qui autorisent l’accès à distance à partir de réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="0aa42-143">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="0aa42-144">La commande utilise le paramètre **SkipNetworkProfileCheck** pour autoriser l'accès à distance à partir de réseaux publics dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="0aa42-144">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="0aa42-145">La commande spécifie le paramètre **force** pour supprimer les messages de confirmation.</span><span class="sxs-lookup"><span data-stu-id="0aa42-145">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="0aa42-146">Le paramètre **SkipNetworkProfileCheck** n’affecte pas les versions serveur du système d’exploitation Windows, qui autorisent l’accès à distance à partir de réseaux publics dans le même sous-réseau local par défaut.</span><span class="sxs-lookup"><span data-stu-id="0aa42-146">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="0aa42-147">L' `Set-NetFirewallRule` applet de commande du module **netsecurity** ajoute une règle de pare-feu qui autorise l’accès à distance à partir de n’importe quel emplacement distant à partir de réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="0aa42-147">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="0aa42-148">Cela comprend les emplacements situés dans des sous-réseaux différents.</span><span class="sxs-lookup"><span data-stu-id="0aa42-148">This includes locations in different subnets.</span></span>

> [!NOTE]
> <span data-ttu-id="0aa42-149">Le nom de la règle de pare-feu peut être différent selon la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="0aa42-149">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="0aa42-150">Utilisez l' `Get-NetFirewallRule` applet de commande pour répertorier les noms des règles sur votre système.</span><span class="sxs-lookup"><span data-stu-id="0aa42-150">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="0aa42-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0aa42-151">PARAMETERS</span></span>

### <span data-ttu-id="0aa42-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0aa42-152">-Confirm</span></span>

<span data-ttu-id="0aa42-153">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0aa42-153">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aa42-154">-Force</span><span class="sxs-lookup"><span data-stu-id="0aa42-154">-Force</span></span>

<span data-ttu-id="0aa42-155">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0aa42-155">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aa42-156">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="0aa42-156">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="0aa42-157">Indique que cette applet de commande active la communication à distance sur les versions clientes du système d’exploitation Windows lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="0aa42-157">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="0aa42-158">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="0aa42-158">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="0aa42-159">Ce paramètre n’affecte pas les versions serveur du système d’exploitation Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="0aa42-159">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="0aa42-160">Si la règle de pare-feu de sous-réseau local est désactivée sur une version de serveur, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="0aa42-160">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="0aa42-161">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="0aa42-161">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="0aa42-162">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0aa42-162">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aa42-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0aa42-163">-WhatIf</span></span>

<span data-ttu-id="0aa42-164">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0aa42-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0aa42-165">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="0aa42-165">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0aa42-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0aa42-166">CommonParameters</span></span>

<span data-ttu-id="0aa42-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0aa42-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0aa42-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0aa42-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0aa42-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0aa42-169">INPUTS</span></span>

### <span data-ttu-id="0aa42-170">Aucun</span><span class="sxs-lookup"><span data-stu-id="0aa42-170">None</span></span>

<span data-ttu-id="0aa42-171">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0aa42-171">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0aa42-172">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0aa42-172">OUTPUTS</span></span>

### <span data-ttu-id="0aa42-173">System.String</span><span class="sxs-lookup"><span data-stu-id="0aa42-173">System.String</span></span>

<span data-ttu-id="0aa42-174">Cette applet de commande retourne des chaînes qui décrivent ses résultats.</span><span class="sxs-lookup"><span data-stu-id="0aa42-174">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="0aa42-175">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0aa42-175">NOTES</span></span>

<span data-ttu-id="0aa42-176">Dans PowerShell 3,0, `Enable-PSRemoting` crée les exceptions de pare-feu suivantes pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="0aa42-176">In PowerShell 3.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="0aa42-177">Sur les versions serveur du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance, et crée une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="0aa42-177">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="0aa42-178">Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` PowerShell 3,0 crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance illimité.</span><span class="sxs-lookup"><span data-stu-id="0aa42-178">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 3.0 creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="0aa42-179">Pour créer une règle de pare-feu pour les réseaux publics qui autorise l'accès à distance à partir du même sous-réseau local, utilisez le paramètre **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="0aa42-179">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="0aa42-180">Sur les versions client ou serveur du système d’exploitation Windows, pour créer une règle de pare-feu pour les réseaux publics qui supprime la restriction de sous-réseau local et autorise l’accès à distance, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity pour exécuter la commande suivante : `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="0aa42-180">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="0aa42-181">Dans PowerShell 2,0, `Enable-PSRemoting` crée les exceptions de pare-feu suivantes pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="0aa42-181">In PowerShell 2.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="0aa42-182">Sur les versions serveur du système d’exploitation Windows, il crée des règles de pare-feu pour tous les réseaux qui autorisent l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="0aa42-182">On server versions of the Windows operating system, it creates firewall rules for all networks that allow remote access.</span></span>

<span data-ttu-id="0aa42-183">Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` PowerShell 2,0 crée une exception de pare-feu uniquement pour les emplacements de réseau privé et de domaine.</span><span class="sxs-lookup"><span data-stu-id="0aa42-183">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 2.0 creates a firewall exception only for domain and private network locations.</span></span> <span data-ttu-id="0aa42-184">Pour réduire les risques de sécurité, `Enable-PSRemoting` ne crée pas de règle de pare-feu pour les réseaux publics sur les versions client de Windows.</span><span class="sxs-lookup"><span data-stu-id="0aa42-184">To minimize security risks, `Enable-PSRemoting` does not create a firewall rule for public networks on client versions of Windows.</span></span> <span data-ttu-id="0aa42-185">Lorsque l’emplacement réseau actuel est public, `Enable-PSRemoting` retourne le message suivant : impossible de vérifier l’état du pare-feu.</span><span class="sxs-lookup"><span data-stu-id="0aa42-185">When the current network location is public, `Enable-PSRemoting` returns the following message: Unable to check the status of the firewall.</span></span>

<span data-ttu-id="0aa42-186">À compter de PowerShell 3,0, `Enable-PSRemoting` Active toutes les configurations de session en définissant la valeur de la propriété **Enabled** de toutes les configurations de session sur `$True` .</span><span class="sxs-lookup"><span data-stu-id="0aa42-186">Starting in PowerShell 3.0, `Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="0aa42-187">Dans PowerShell 2,0, `Enable-PSRemoting` supprime le paramètre **Deny_All** du descripteur de sécurité des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="0aa42-187">In PowerShell 2.0, `Enable-PSRemoting` removes the **Deny_All** setting from the security descriptor of session configurations.</span></span> <span data-ttu-id="0aa42-188">Dans PowerShell 3,0, `Enable-PSRemoting` supprime les paramètres **Deny_All** et **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="0aa42-188">In PowerShell 3.0, `Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="0aa42-189">Cela permet l’accès à distance aux configurations de session qui ont été réservées pour une utilisation locale.</span><span class="sxs-lookup"><span data-stu-id="0aa42-189">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="0aa42-190">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0aa42-190">RELATED LINKS</span></span>

[<span data-ttu-id="0aa42-191">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0aa42-191">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="0aa42-192">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0aa42-192">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="0aa42-193">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0aa42-193">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="0aa42-194">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0aa42-194">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="0aa42-195">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0aa42-195">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="0aa42-196">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="0aa42-196">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="0aa42-197">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="0aa42-197">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="0aa42-198">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0aa42-198">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="0aa42-199">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="0aa42-199">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 5b69a1ec6945f910815d5469fad77213b517d7b6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342295"
---
# <span data-ttu-id="707a6-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="707a6-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="707a6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="707a6-104">SYNOPSIS</span></span>
<span data-ttu-id="707a6-105">Configure l'ordinateur pour recevoir des commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="707a6-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="707a6-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="707a6-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="707a6-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="707a6-107">DESCRIPTION</span></span>

<span data-ttu-id="707a6-108">L' `Enable-PSRemoting` applet de commande configure l’ordinateur pour qu’il reçoive les commandes PowerShell à distance qui sont envoyées à l’aide de la technologie WS-Management.</span><span class="sxs-lookup"><span data-stu-id="707a6-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="707a6-109">La communication à distance PowerShell basée sur WS-Management n’est actuellement prise en charge que sur la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="707a6-109">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="707a6-110">La communication à distance PowerShell est activée par défaut sur les plateformes Windows Server.</span><span class="sxs-lookup"><span data-stu-id="707a6-110">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="707a6-111">Vous pouvez utiliser `Enable-PSRemoting` pour activer la communication à distance PowerShell sur d’autres versions de Windows prises en charge et pour réactiver la communication à distance si elle est désactivée.</span><span class="sxs-lookup"><span data-stu-id="707a6-111">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="707a6-112">Vous ne devez exécuter cette commande qu’une seule fois sur chaque ordinateur qui recevra des commandes.</span><span class="sxs-lookup"><span data-stu-id="707a6-112">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="707a6-113">Vous n’avez pas besoin de l’exécuter sur les ordinateurs qui envoient uniquement des commandes.</span><span class="sxs-lookup"><span data-stu-id="707a6-113">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="707a6-114">Étant donné que la configuration démarre les écouteurs pour accepter les connexions à distance, il est prudent de l’exécuter uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="707a6-114">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="707a6-115">L’activation de la communication à distance PowerShell sur les versions client de Windows lorsque l’ordinateur se trouve sur un réseau public est normalement interdite, mais vous pouvez ignorer cette restriction à l’aide du paramètre **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="707a6-115">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="707a6-116">Pour plus d'informations, consultez la description du paramètre **SkipNetworkProfileCheck**.</span><span class="sxs-lookup"><span data-stu-id="707a6-116">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="707a6-117">Plusieurs installations PowerShell peuvent coexister côte à côte sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="707a6-117">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="707a6-118">L’exécution `Enable-PSRemoting` configure un point de terminaison de communication à distance pour la version d’installation spécifique dans laquelle vous exécutez l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="707a6-118">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="707a6-119">Par conséquent, si vous exécutez `Enable-PSRemoting` en exécutant powershell 6,2, un point de terminaison de communication à distance sera configuré pour exécuter powershell 6,2.</span><span class="sxs-lookup"><span data-stu-id="707a6-119">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="707a6-120">Si vous exécutez `Enable-PSRemoting` en exécutant PowerShell 7-Preview, un point de terminaison de communication à distance sera configuré pour exécuter PowerShell 7-preview.</span><span class="sxs-lookup"><span data-stu-id="707a6-120">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="707a6-121">`Enable-PSRemoting` crée deux configurations de point de terminaison de communication à distance si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="707a6-121">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="707a6-122">Si les configurations de point de terminaison existent déjà, elles sont simplement vérifiées pour être activées.</span><span class="sxs-lookup"><span data-stu-id="707a6-122">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="707a6-123">Les configurations créées sont identiques, mais ont des noms différents.</span><span class="sxs-lookup"><span data-stu-id="707a6-123">The created configurations are identical but have different names.</span></span> <span data-ttu-id="707a6-124">Un nom simple correspondant à la version PowerShell qui héberge la session est utilisé.</span><span class="sxs-lookup"><span data-stu-id="707a6-124">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="707a6-125">L’autre nom de configuration contient des informations plus détaillées sur la version de PowerShell qui héberge la session.</span><span class="sxs-lookup"><span data-stu-id="707a6-125">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="707a6-126">Par exemple, lors `Enable-PSRemoting` de l’exécution dans powershell 6,2, vous obtiendrez deux points de terminaison configurés nommés **PowerShell. 6** , **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="707a6-126">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6** , **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="707a6-127">Cela vous permet de créer une connexion à la dernière version de l’hôte PowerShell 6 en utilisant le nom simple **PowerShell. 6**.</span><span class="sxs-lookup"><span data-stu-id="707a6-127">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="707a6-128">Vous pouvez ou vous connecter à une version spécifique de l’hôte PowerShell en utilisant le nom plus long **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="707a6-128">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="707a6-129">Pour utiliser les points de terminaison de communication à distance récemment activés, vous devez les spécifier par leur nom avec le paramètre **ConfigurationName** lors de la création d’une connexion à distance à l’aide des `Invoke-Command` applets de commande, `New-PSSession` , `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="707a6-129">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="707a6-130">Pour plus d’informations, consultez l’exemple 4.</span><span class="sxs-lookup"><span data-stu-id="707a6-130">For more information, see Example 4.</span></span>

<span data-ttu-id="707a6-131">L' `Enable-PSRemoting` applet de commande effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="707a6-131">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="707a6-132">Exécute l’applet de commande [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) , qui effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="707a6-132">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="707a6-133">Démarre le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="707a6-133">Starts the WinRM service.</span></span>
  - <span data-ttu-id="707a6-134">Définit le type de démarrage du service WinRM sur automatique.</span><span class="sxs-lookup"><span data-stu-id="707a6-134">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="707a6-135">Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="707a6-135">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="707a6-136">Active une exception de pare-feu pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="707a6-136">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="707a6-137">Crée les configurations de point de terminaison de session de nom simple et long, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="707a6-137">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="707a6-138">Active toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="707a6-138">Enables all session configurations.</span></span>
  - <span data-ttu-id="707a6-139">Modifie le descripteur de sécurité de toutes les configurations de session pour autoriser l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="707a6-139">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="707a6-140">Redémarre le service WinRM pour que les modifications précédentes soient effectives.</span><span class="sxs-lookup"><span data-stu-id="707a6-140">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="707a6-141">Pour exécuter cette applet de commande sur la plateforme Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="707a6-141">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="707a6-142">Cette applet de commande n’est pas disponible dans les versions Linux ou MacOS de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="707a6-142">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="707a6-143">Cette applet de commande n’affecte pas les configurations de point de terminaison distant créées par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="707a6-143">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="707a6-144">Il affecte uniquement les points de terminaison créés avec PowerShell version 6 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="707a6-144">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="707a6-145">Pour activer et désactiver les points de terminaison de communication à distance PowerShell qui sont hébergés par Windows PowerShell, exécutez l' `Enable-PSRemoting` applet de commande à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="707a6-145">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="707a6-146">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="707a6-146">EXAMPLES</span></span>

### <span data-ttu-id="707a6-147">Exemple 1 : configurer un ordinateur pour recevoir des commandes à distance</span><span class="sxs-lookup"><span data-stu-id="707a6-147">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="707a6-148">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="707a6-148">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="707a6-149">Exemple 2 : configurer un ordinateur pour qu’il reçoive des commandes distantes sans invite de confirmation</span><span class="sxs-lookup"><span data-stu-id="707a6-149">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="707a6-150">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="707a6-150">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="707a6-151">Le paramètre **force** supprime les invites utilisateur.</span><span class="sxs-lookup"><span data-stu-id="707a6-151">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="707a6-152">Exemple 3 : autoriser l’accès à distance sur les clients</span><span class="sxs-lookup"><span data-stu-id="707a6-152">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="707a6-153">Cet exemple montre comment autoriser l’accès à distance à partir de réseaux publics sur des versions clientes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="707a6-153">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="707a6-154">Le nom de la règle de pare-feu peut être différent pour les différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="707a6-154">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="707a6-155">Utilisez `Get-NetFirewallRule` pour afficher une liste de règles.</span><span class="sxs-lookup"><span data-stu-id="707a6-155">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="707a6-156">Avant d’activer la règle de pare-feu, affichez les paramètres de sécurité de la règle pour vérifier que la configuration est adaptée à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="707a6-156">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="707a6-157">Par défaut, `Enable-PSRemoting` crée des règles de réseau qui autorisent l’accès à distance à partir de réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="707a6-157">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="707a6-158">La commande utilise le paramètre **SkipNetworkProfileCheck** pour autoriser l'accès à distance à partir de réseaux publics dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="707a6-158">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="707a6-159">La commande spécifie le paramètre **force** pour supprimer les messages de confirmation.</span><span class="sxs-lookup"><span data-stu-id="707a6-159">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="707a6-160">Le paramètre **SkipNetworkProfileCheck** n’affecte pas les versions serveur du système d’exploitation Windows, qui autorisent l’accès à distance à partir de réseaux publics dans le même sous-réseau local par défaut.</span><span class="sxs-lookup"><span data-stu-id="707a6-160">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="707a6-161">L' `Set-NetFirewallRule` applet de commande du module **netsecurity** ajoute une règle de pare-feu qui autorise l’accès à distance à partir de n’importe quel emplacement distant à partir de réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="707a6-161">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="707a6-162">Cela comprend les emplacements situés dans des sous-réseaux différents.</span><span class="sxs-lookup"><span data-stu-id="707a6-162">This includes locations in different subnets.</span></span>

### <span data-ttu-id="707a6-163">Exemple 4 : créer une session à distance sur la configuration de point de terminaison récemment activée</span><span class="sxs-lookup"><span data-stu-id="707a6-163">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="707a6-164">Cet exemple montre comment activer la communication à distance PowerShell sur un ordinateur, rechercher les noms de points de terminaison configurés et créer une session à distance sur l’un des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="707a6-164">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="707a6-165">La première commande active la communication à distance PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="707a6-165">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="707a6-166">La deuxième commande répertorie les configurations de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="707a6-166">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="707a6-167">La troisième commande crée une session PowerShell distante sur le même ordinateur, en spécifiant le point de terminaison **PowerShell. 6** par son nom.</span><span class="sxs-lookup"><span data-stu-id="707a6-167">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="707a6-168">La session à distance sera hébergée avec la dernière version de PowerShell 6 (6.2.2).</span><span class="sxs-lookup"><span data-stu-id="707a6-168">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="707a6-169">La dernière commande accède à la `$PSVersionTable` variable dans la session à distance pour afficher la version de PowerShell qui héberge la session.</span><span class="sxs-lookup"><span data-stu-id="707a6-169">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="707a6-170">Le nom de la règle de pare-feu peut être différent selon la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="707a6-170">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="707a6-171">Utilisez l' `Get-NetFirewallRule` applet de commande pour répertorier les noms des règles sur votre système.</span><span class="sxs-lookup"><span data-stu-id="707a6-171">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="707a6-172">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="707a6-172">PARAMETERS</span></span>

### <span data-ttu-id="707a6-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="707a6-173">-Confirm</span></span>

<span data-ttu-id="707a6-174">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="707a6-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="707a6-175">-Force</span><span class="sxs-lookup"><span data-stu-id="707a6-175">-Force</span></span>

<span data-ttu-id="707a6-176">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="707a6-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="707a6-177">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="707a6-177">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="707a6-178">Indique que cette applet de commande active la communication à distance sur les versions clientes du système d’exploitation Windows lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="707a6-178">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="707a6-179">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="707a6-179">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="707a6-180">Ce paramètre n’affecte pas les versions serveur du système d’exploitation Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="707a6-180">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="707a6-181">Si la règle de pare-feu de sous-réseau local est désactivée sur une version de serveur, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="707a6-181">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="707a6-182">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="707a6-182">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="707a6-183">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="707a6-183">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="707a6-184">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="707a6-184">-WhatIf</span></span>

<span data-ttu-id="707a6-185">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="707a6-185">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="707a6-186">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="707a6-186">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="707a6-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="707a6-187">CommonParameters</span></span>

<span data-ttu-id="707a6-188">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="707a6-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="707a6-189">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="707a6-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="707a6-190">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="707a6-190">INPUTS</span></span>

### <span data-ttu-id="707a6-191">Aucun</span><span class="sxs-lookup"><span data-stu-id="707a6-191">None</span></span>

<span data-ttu-id="707a6-192">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="707a6-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="707a6-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="707a6-193">OUTPUTS</span></span>

### <span data-ttu-id="707a6-194">System.String</span><span class="sxs-lookup"><span data-stu-id="707a6-194">System.String</span></span>

<span data-ttu-id="707a6-195">Cette applet de commande retourne des chaînes qui décrivent ses résultats.</span><span class="sxs-lookup"><span data-stu-id="707a6-195">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="707a6-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="707a6-196">NOTES</span></span>

<span data-ttu-id="707a6-197">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="707a6-197">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="707a6-198">Sur les versions serveur du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance, et crée une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="707a6-198">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="707a6-199">Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance illimité.</span><span class="sxs-lookup"><span data-stu-id="707a6-199">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="707a6-200">Pour créer une règle de pare-feu pour les réseaux publics qui autorise l'accès à distance à partir du même sous-réseau local, utilisez le paramètre **SkipNetworkProfileCheck**.</span><span class="sxs-lookup"><span data-stu-id="707a6-200">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="707a6-201">Sur les versions client ou serveur du système d’exploitation Windows, pour créer une règle de pare-feu pour les réseaux publics qui supprime la restriction de sous-réseau local et autorise l’accès à distance, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity pour exécuter la commande suivante : `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="707a6-201">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="707a6-202">`Enable-PSRemoting` Active toutes les configurations de session en définissant la valeur de la propriété **Enabled** de toutes les configurations de session sur `$True` .</span><span class="sxs-lookup"><span data-stu-id="707a6-202">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="707a6-203">`Enable-PSRemoting` supprime les paramètres **Deny_All** et **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="707a6-203">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="707a6-204">Cela permet l’accès à distance aux configurations de session qui ont été réservées pour une utilisation locale.</span><span class="sxs-lookup"><span data-stu-id="707a6-204">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="707a6-205">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="707a6-205">RELATED LINKS</span></span>

[<span data-ttu-id="707a6-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="707a6-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="707a6-207">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="707a6-207">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="707a6-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="707a6-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="707a6-209">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="707a6-209">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="707a6-210">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="707a6-210">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="707a6-211">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="707a6-211">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="707a6-212">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="707a6-212">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="707a6-213">about_Remote</span><span class="sxs-lookup"><span data-stu-id="707a6-213">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="707a6-214">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="707a6-214">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

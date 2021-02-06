---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: a3d9506a0fd2adbb9cc093fb24f99e922dc8a938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597552"
---
# <span data-ttu-id="aad0e-102">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="aad0e-102">Enable-PSRemoting</span></span>

## <span data-ttu-id="aad0e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="aad0e-103">SYNOPSIS</span></span>
<span data-ttu-id="aad0e-104">Configure l'ordinateur pour recevoir des commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="aad0e-104">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="aad0e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="aad0e-105">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aad0e-106">Description</span><span class="sxs-lookup"><span data-stu-id="aad0e-106">DESCRIPTION</span></span>

<span data-ttu-id="aad0e-107">L' `Enable-PSRemoting` applet de commande configure l’ordinateur pour qu’il reçoive les commandes PowerShell à distance qui sont envoyées à l’aide de la technologie WS-Management.</span><span class="sxs-lookup"><span data-stu-id="aad0e-107">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="aad0e-108">La communication à distance PowerShell basée sur WS-Management n’est actuellement prise en charge que sur la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="aad0e-108">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="aad0e-109">La communication à distance PowerShell est activée par défaut sur les plateformes Windows Server.</span><span class="sxs-lookup"><span data-stu-id="aad0e-109">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="aad0e-110">Vous pouvez utiliser `Enable-PSRemoting` pour activer la communication à distance PowerShell sur d’autres versions de Windows prises en charge et pour réactiver la communication à distance si elle est désactivée.</span><span class="sxs-lookup"><span data-stu-id="aad0e-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="aad0e-111">Vous ne devez exécuter cette commande qu’une seule fois sur chaque ordinateur qui recevra des commandes.</span><span class="sxs-lookup"><span data-stu-id="aad0e-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="aad0e-112">Vous n’avez pas besoin de l’exécuter sur les ordinateurs qui envoient uniquement des commandes.</span><span class="sxs-lookup"><span data-stu-id="aad0e-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="aad0e-113">Étant donné que la configuration démarre les écouteurs pour accepter les connexions à distance, il est prudent de l’exécuter uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="aad0e-113">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="aad0e-114">L’activation de la communication à distance PowerShell sur les versions client de Windows lorsque l’ordinateur se trouve sur un réseau public est normalement interdite, mais vous pouvez ignorer cette restriction à l’aide du paramètre **SkipNetworkProfileCheck** .</span><span class="sxs-lookup"><span data-stu-id="aad0e-114">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="aad0e-115">Pour plus d'informations, consultez la description du paramètre **SkipNetworkProfileCheck**.</span><span class="sxs-lookup"><span data-stu-id="aad0e-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="aad0e-116">Plusieurs installations PowerShell peuvent coexister côte à côte sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aad0e-116">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="aad0e-117">L’exécution `Enable-PSRemoting` configure un point de terminaison de communication à distance pour la version d’installation spécifique dans laquelle vous exécutez l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aad0e-117">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="aad0e-118">Par conséquent, si vous exécutez `Enable-PSRemoting` en exécutant powershell 6,2, un point de terminaison de communication à distance sera configuré pour exécuter powershell 6,2.</span><span class="sxs-lookup"><span data-stu-id="aad0e-118">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="aad0e-119">Si vous exécutez `Enable-PSRemoting` en exécutant PowerShell 7-Preview, un point de terminaison de communication à distance sera configuré pour exécuter PowerShell 7-preview.</span><span class="sxs-lookup"><span data-stu-id="aad0e-119">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="aad0e-120">`Enable-PSRemoting` crée deux configurations de point de terminaison de communication à distance si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="aad0e-120">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="aad0e-121">Si les configurations de point de terminaison existent déjà, elles sont simplement vérifiées pour être activées.</span><span class="sxs-lookup"><span data-stu-id="aad0e-121">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="aad0e-122">Les configurations créées sont identiques, mais ont des noms différents.</span><span class="sxs-lookup"><span data-stu-id="aad0e-122">The created configurations are identical but have different names.</span></span> <span data-ttu-id="aad0e-123">Un nom simple correspondant à la version PowerShell qui héberge la session est utilisé.</span><span class="sxs-lookup"><span data-stu-id="aad0e-123">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="aad0e-124">L’autre nom de configuration contient des informations plus détaillées sur la version de PowerShell qui héberge la session.</span><span class="sxs-lookup"><span data-stu-id="aad0e-124">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="aad0e-125">Par exemple, lors `Enable-PSRemoting` de l’exécution dans powershell 6,2, vous obtiendrez deux points de terminaison configurés nommés **PowerShell. 6**, **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="aad0e-125">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6**, **PowerShell.6.2.2**.</span></span>
<span data-ttu-id="aad0e-126">Cela vous permet de créer une connexion à la dernière version de l’hôte PowerShell 6 en utilisant le nom simple **PowerShell. 6**.</span><span class="sxs-lookup"><span data-stu-id="aad0e-126">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6**.</span></span> <span data-ttu-id="aad0e-127">Vous pouvez ou vous connecter à une version spécifique de l’hôte PowerShell en utilisant le nom plus long **PowerShell. 6.2.2**.</span><span class="sxs-lookup"><span data-stu-id="aad0e-127">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2**.</span></span>

<span data-ttu-id="aad0e-128">Pour utiliser les points de terminaison de communication à distance récemment activés, vous devez les spécifier par leur nom avec le paramètre **ConfigurationName** lors de la création d’une connexion à distance à l’aide des `Invoke-Command` applets de commande, `New-PSSession` , `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="aad0e-128">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="aad0e-129">Pour plus d’informations, consultez l’exemple 4.</span><span class="sxs-lookup"><span data-stu-id="aad0e-129">For more information, see Example 4.</span></span>

<span data-ttu-id="aad0e-130">L' `Enable-PSRemoting` applet de commande effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aad0e-130">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="aad0e-131">Exécute l’applet de commande [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) , qui effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="aad0e-131">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="aad0e-132">Démarre le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="aad0e-132">Starts the WinRM service.</span></span>
  - <span data-ttu-id="aad0e-133">Définit le type de démarrage du service WinRM sur automatique.</span><span class="sxs-lookup"><span data-stu-id="aad0e-133">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="aad0e-134">Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="aad0e-134">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="aad0e-135">Active une exception de pare-feu pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="aad0e-135">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="aad0e-136">Crée les configurations de point de terminaison de session de nom simple et long, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="aad0e-136">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="aad0e-137">Active toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="aad0e-137">Enables all session configurations.</span></span>
  - <span data-ttu-id="aad0e-138">Modifie le descripteur de sécurité de toutes les configurations de session pour autoriser l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="aad0e-138">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="aad0e-139">Redémarre le service WinRM pour que les modifications précédentes soient effectives.</span><span class="sxs-lookup"><span data-stu-id="aad0e-139">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="aad0e-140">Pour exécuter cette applet de commande sur la plateforme Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="aad0e-140">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="aad0e-141">Cette applet de commande n’est pas disponible dans les versions Linux ou MacOS de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad0e-141">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="aad0e-142">Cette applet de commande n’affecte pas les configurations de point de terminaison distant créées par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad0e-142">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="aad0e-143">Il affecte uniquement les points de terminaison créés avec PowerShell version 6 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="aad0e-143">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="aad0e-144">Pour activer et désactiver les points de terminaison de communication à distance PowerShell qui sont hébergés par Windows PowerShell, exécutez l' `Enable-PSRemoting` applet de commande à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad0e-144">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="aad0e-145">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="aad0e-145">EXAMPLES</span></span>

### <span data-ttu-id="aad0e-146">Exemple 1 : configurer un ordinateur pour recevoir des commandes à distance</span><span class="sxs-lookup"><span data-stu-id="aad0e-146">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="aad0e-147">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="aad0e-147">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="aad0e-148">Exemple 2 : configurer un ordinateur pour qu’il reçoive des commandes distantes sans invite de confirmation</span><span class="sxs-lookup"><span data-stu-id="aad0e-148">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="aad0e-149">Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.</span><span class="sxs-lookup"><span data-stu-id="aad0e-149">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="aad0e-150">Le paramètre **force** supprime les invites utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aad0e-150">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="aad0e-151">Exemple 3 : autoriser l’accès à distance sur les clients</span><span class="sxs-lookup"><span data-stu-id="aad0e-151">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="aad0e-152">Cet exemple montre comment autoriser l’accès à distance à partir de réseaux publics sur des versions clientes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="aad0e-152">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="aad0e-153">Le nom de la règle de pare-feu peut être différent pour les différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="aad0e-153">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="aad0e-154">Utilisez `Get-NetFirewallRule` pour afficher une liste de règles.</span><span class="sxs-lookup"><span data-stu-id="aad0e-154">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="aad0e-155">Avant d’activer la règle de pare-feu, affichez les paramètres de sécurité de la règle pour vérifier que la configuration est adaptée à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="aad0e-155">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="aad0e-156">Par défaut, `Enable-PSRemoting` crée des règles de réseau qui autorisent l’accès à distance à partir de réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="aad0e-156">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="aad0e-157">La commande utilise le paramètre **SkipNetworkProfileCheck** pour autoriser l'accès à distance à partir de réseaux publics dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="aad0e-157">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="aad0e-158">La commande spécifie le paramètre **force** pour supprimer les messages de confirmation.</span><span class="sxs-lookup"><span data-stu-id="aad0e-158">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="aad0e-159">Le paramètre **SkipNetworkProfileCheck** n’affecte pas les versions serveur du système d’exploitation Windows, qui autorisent l’accès à distance à partir de réseaux publics dans le même sous-réseau local par défaut.</span><span class="sxs-lookup"><span data-stu-id="aad0e-159">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="aad0e-160">L' `Set-NetFirewallRule` applet de commande du module **netsecurity** ajoute une règle de pare-feu qui autorise l’accès à distance à partir de n’importe quel emplacement distant à partir de réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="aad0e-160">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="aad0e-161">Cela comprend les emplacements situés dans des sous-réseaux différents.</span><span class="sxs-lookup"><span data-stu-id="aad0e-161">This includes locations in different subnets.</span></span>

### <span data-ttu-id="aad0e-162">Exemple 4 : créer une session à distance sur la configuration de point de terminaison récemment activée</span><span class="sxs-lookup"><span data-stu-id="aad0e-162">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="aad0e-163">Cet exemple montre comment activer la communication à distance PowerShell sur un ordinateur, rechercher les noms de points de terminaison configurés et créer une session à distance sur l’un des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="aad0e-163">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="aad0e-164">La première commande active la communication à distance PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aad0e-164">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="aad0e-165">La deuxième commande répertorie les configurations de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="aad0e-165">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="aad0e-166">La troisième commande crée une session PowerShell distante sur le même ordinateur, en spécifiant le point de terminaison **PowerShell. 6** par son nom.</span><span class="sxs-lookup"><span data-stu-id="aad0e-166">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="aad0e-167">La session à distance sera hébergée avec la dernière version de PowerShell 6 (6.2.2).</span><span class="sxs-lookup"><span data-stu-id="aad0e-167">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="aad0e-168">La dernière commande accède à la `$PSVersionTable` variable dans la session à distance pour afficher la version de PowerShell qui héberge la session.</span><span class="sxs-lookup"><span data-stu-id="aad0e-168">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

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
> <span data-ttu-id="aad0e-169">Le nom de la règle de pare-feu peut être différent selon la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="aad0e-169">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="aad0e-170">Utilisez l' `Get-NetFirewallRule` applet de commande pour répertorier les noms des règles sur votre système.</span><span class="sxs-lookup"><span data-stu-id="aad0e-170">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="aad0e-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aad0e-171">PARAMETERS</span></span>

### <span data-ttu-id="aad0e-172">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aad0e-172">-Confirm</span></span>

<span data-ttu-id="aad0e-173">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aad0e-173">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aad0e-174">-Force</span><span class="sxs-lookup"><span data-stu-id="aad0e-174">-Force</span></span>

<span data-ttu-id="aad0e-175">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aad0e-175">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="aad0e-176">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="aad0e-176">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="aad0e-177">Indique que cette applet de commande active la communication à distance sur les versions clientes du système d’exploitation Windows lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="aad0e-177">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="aad0e-178">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="aad0e-178">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="aad0e-179">Ce paramètre n’affecte pas les versions serveur du système d’exploitation Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="aad0e-179">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="aad0e-180">Si la règle de pare-feu de sous-réseau local est désactivée sur une version de serveur, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="aad0e-180">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="aad0e-181">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="aad0e-181">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="aad0e-182">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aad0e-182">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aad0e-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aad0e-183">-WhatIf</span></span>

<span data-ttu-id="aad0e-184">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aad0e-184">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aad0e-185">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="aad0e-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aad0e-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aad0e-186">CommonParameters</span></span>

<span data-ttu-id="aad0e-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aad0e-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aad0e-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aad0e-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aad0e-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="aad0e-189">INPUTS</span></span>

### <span data-ttu-id="aad0e-190">None</span><span class="sxs-lookup"><span data-stu-id="aad0e-190">None</span></span>

<span data-ttu-id="aad0e-191">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aad0e-191">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="aad0e-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="aad0e-192">OUTPUTS</span></span>

### <span data-ttu-id="aad0e-193">System.String</span><span class="sxs-lookup"><span data-stu-id="aad0e-193">System.String</span></span>

<span data-ttu-id="aad0e-194">Cette applet de commande retourne des chaînes qui décrivent ses résultats.</span><span class="sxs-lookup"><span data-stu-id="aad0e-194">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="aad0e-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="aad0e-195">NOTES</span></span>

<span data-ttu-id="aad0e-196">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="aad0e-196">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="aad0e-197">Sur les versions serveur du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance, et crée une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="aad0e-197">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="aad0e-198">Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance illimité.</span><span class="sxs-lookup"><span data-stu-id="aad0e-198">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="aad0e-199">Pour créer une règle de pare-feu pour les réseaux publics qui autorise l'accès à distance à partir du même sous-réseau local, utilisez le paramètre **SkipNetworkProfileCheck**.</span><span class="sxs-lookup"><span data-stu-id="aad0e-199">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="aad0e-200">Sur les versions client ou serveur du système d’exploitation Windows, pour créer une règle de pare-feu pour les réseaux publics qui supprime la restriction de sous-réseau local et autorise l’accès à distance, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity pour exécuter la commande suivante : `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="aad0e-200">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="aad0e-201">`Enable-PSRemoting` Active toutes les configurations de session en définissant la valeur de la propriété **Enabled** de toutes les configurations de session sur `$True` .</span><span class="sxs-lookup"><span data-stu-id="aad0e-201">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="aad0e-202">`Enable-PSRemoting` supprime les paramètres **Deny_All** et **Network_Deny_All** .</span><span class="sxs-lookup"><span data-stu-id="aad0e-202">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="aad0e-203">Cela permet l’accès à distance aux configurations de session qui ont été réservées pour une utilisation locale.</span><span class="sxs-lookup"><span data-stu-id="aad0e-203">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="aad0e-204">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="aad0e-204">RELATED LINKS</span></span>

[<span data-ttu-id="aad0e-205">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aad0e-205">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="aad0e-206">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aad0e-206">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="aad0e-207">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aad0e-207">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="aad0e-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aad0e-208">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="aad0e-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aad0e-209">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="aad0e-210">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="aad0e-210">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="aad0e-211">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="aad0e-211">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="aad0e-212">about_Remote</span><span class="sxs-lookup"><span data-stu-id="aad0e-212">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="aad0e-213">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="aad0e-213">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

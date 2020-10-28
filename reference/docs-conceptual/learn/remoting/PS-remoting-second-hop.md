---
ms.date: 05/14/2020
keywords: powershell,applet de commande
title: Effectuer le deuxième saut dans la communication à distance PowerShell
description: Cet article explique les différentes méthodes de configuration de l’authentification de second saut pour l’accès distant à PowerShell, y compris les implications et les recommandations relatives à la sécurité.
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501369"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="59953-104">Effectuer le deuxième saut dans la communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="59953-104">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="59953-105">Le « problème du deuxième saut » fait référence à une situation de ce type :</span><span class="sxs-lookup"><span data-stu-id="59953-105">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="59953-106">Vous êtes connecté à _ServerA_ .</span><span class="sxs-lookup"><span data-stu-id="59953-106">You are logged in to _ServerA_ .</span></span>
2. <span data-ttu-id="59953-107">À partir de _ServerA_ , vous démarrez une session PowerShell à distance pour vous connecter à _ServerB_ .</span><span class="sxs-lookup"><span data-stu-id="59953-107">From _ServerA_ , you start a remote PowerShell session to connect to _ServerB_ .</span></span>
3. <span data-ttu-id="59953-108">Une commande exécutée sur _ServerB_ via votre session de communication à distance PowerShell tente d’accéder à une ressource sur _ServerC_ .</span><span class="sxs-lookup"><span data-stu-id="59953-108">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_ .</span></span>
4. <span data-ttu-id="59953-109">L’accès à la ressource sur _ServerC_ est refusé, car les informations d’identification utilisées pour créer la session de communication à distance PowerShell ne sont pas transmises de _ServerB_ à _ServerC_ .</span><span class="sxs-lookup"><span data-stu-id="59953-109">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_ .</span></span>

<span data-ttu-id="59953-110">Il existe plusieurs moyens de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="59953-110">There are several ways to address this problem.</span></span> <span data-ttu-id="59953-111">Le tableau suivant répertorie les méthodes par ordre de préférence.</span><span class="sxs-lookup"><span data-stu-id="59953-111">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="59953-112">Configuration</span><span class="sxs-lookup"><span data-stu-id="59953-112">Configuration</span></span>                       |                                  <span data-ttu-id="59953-113">Remarque</span><span class="sxs-lookup"><span data-stu-id="59953-113">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="59953-114">CredSSP</span><span class="sxs-lookup"><span data-stu-id="59953-114">CredSSP</span></span>                                                  | <span data-ttu-id="59953-115">Équilibre la facilité d’utilisation et la sécurité</span><span class="sxs-lookup"><span data-stu-id="59953-115">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="59953-116">Délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="59953-116">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="59953-117">Sécurité accrue avec une configuration plus simple</span><span class="sxs-lookup"><span data-stu-id="59953-117">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="59953-118">Délégation Kerberos contrainte</span><span class="sxs-lookup"><span data-stu-id="59953-118">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="59953-119">Sécurité élevée, mais nécessite un administrateur de domaine</span><span class="sxs-lookup"><span data-stu-id="59953-119">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="59953-120">Délégation Kerberos (sans contraintes)</span><span class="sxs-lookup"><span data-stu-id="59953-120">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="59953-121">Non recommandé</span><span class="sxs-lookup"><span data-stu-id="59953-121">Not recommended</span></span>                                                        |
| <span data-ttu-id="59953-122">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="59953-122">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="59953-123">Peut fournir la meilleure sécurité, mais nécessite une configuration plus détaillée</span><span class="sxs-lookup"><span data-stu-id="59953-123">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="59953-124">PSSessionConfiguration avec la commande RunAs</span><span class="sxs-lookup"><span data-stu-id="59953-124">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="59953-125">Plus simple à configurer mais nécessite une gestion des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="59953-125">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="59953-126">Transmettre des informations d’identification à l’intérieur d’un bloc de script `Invoke-Command`</span><span class="sxs-lookup"><span data-stu-id="59953-126">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="59953-127">La méthode la plus simple à utiliser, mais vous devez fournir des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="59953-127">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="59953-128">CredSSP</span><span class="sxs-lookup"><span data-stu-id="59953-128">CredSSP</span></span>

<span data-ttu-id="59953-129">Vous pouvez utiliser le [protocole CredSSP (Credential Security Support Provider)][credssp] pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="59953-129">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="59953-130">Le protocole CredSSP mettant en cache les informations d’identification sur le serveur distant ( _ServerB_ ), son utilisation vous expose à des risques de vol de ces informations.</span><span class="sxs-lookup"><span data-stu-id="59953-130">CredSSP caches credentials on the remote server ( _ServerB_ ), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="59953-131">Si l’ordinateur distant est compromis, la personne malveillante a accès aux informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59953-131">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="59953-132">CredSSP est désactivé par défaut sur les ordinateurs clients et serveurs.</span><span class="sxs-lookup"><span data-stu-id="59953-132">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="59953-133">Vous devez activer CredSSP uniquement dans les environnements les plus approuvés,</span><span class="sxs-lookup"><span data-stu-id="59953-133">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="59953-134">Par exemple un administrateur de domaine qui se connecte à un contrôleur de domaine, car le contrôleur de domaine est hautement approuvé.</span><span class="sxs-lookup"><span data-stu-id="59953-134">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="59953-135">Pour plus d’informations sur les questions de sécurité lors de l’utilisation de CredSSP pour la communication à distance PowerShell, voir [Accidental Sabotage: Beware of CredSSP][beware].</span><span class="sxs-lookup"><span data-stu-id="59953-135">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="59953-136">Pour plus d’informations sur les risques de vol des informations d’identification, voir [Atténuation des attaques PtH (Pass-The-Hash) et autres risques de vol des informations d’identification][pth].</span><span class="sxs-lookup"><span data-stu-id="59953-136">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="59953-137">Pour accéder à un exemple montrant comment activer et utiliser CredSSP pour la communication à distance PowerShell, consultez [Activer la fonctionnalité « deuxième saut » de PowerShell avec CredSSP][credssp-psblog].</span><span class="sxs-lookup"><span data-stu-id="59953-137">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="59953-138">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-138">**Pros**</span></span>

- <span data-ttu-id="59953-139">Fonctionne pour tous les serveurs avec Windows Server 2008 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="59953-139">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="59953-140">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-140">**Cons**</span></span>

- <span data-ttu-id="59953-141">Présente des failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="59953-141">Has security vulnerabilities.</span></span>
- <span data-ttu-id="59953-142">Requiert la configuration des rôles client et serveur.</span><span class="sxs-lookup"><span data-stu-id="59953-142">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="59953-143">Ne fonctionne pas avec le groupe Utilisateurs protégés.</span><span class="sxs-lookup"><span data-stu-id="59953-143">Does not work with the Protected Users group.</span></span> <span data-ttu-id="59953-144">Pour plus d’informations, consultez [Groupe de sécurité Utilisateurs protégés][protected-users].</span><span class="sxs-lookup"><span data-stu-id="59953-144">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="59953-145">Délégation Kerberos contrainte</span><span class="sxs-lookup"><span data-stu-id="59953-145">Kerberos constrained delegation</span></span>

<span data-ttu-id="59953-146">Vous pouvez utiliser la délégation contrainte héritée (non basée sur les ressources) pour effectuer le deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="59953-146">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="59953-147">Configurez la délégation contrainte Kerberos avec l’option « Utiliser tout protocole d’authentification » pour permettre la transition du protocole.</span><span class="sxs-lookup"><span data-stu-id="59953-147">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="59953-148">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-148">**Pros**</span></span>

- <span data-ttu-id="59953-149">Ne requiert pas de programmation particulière.</span><span class="sxs-lookup"><span data-stu-id="59953-149">Requires no special coding</span></span>
- <span data-ttu-id="59953-150">Informations d’identification non stockées.</span><span class="sxs-lookup"><span data-stu-id="59953-150">Credentials are not stored.</span></span>

<span data-ttu-id="59953-151">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-151">**Cons**</span></span>

- <span data-ttu-id="59953-152">Ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="59953-152">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="59953-153">Nécessite un accès Administrateur de domaine pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="59953-153">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="59953-154">Doit être configuré sur l’objet Active Directory du serveur distant ( _ServerB_ ).</span><span class="sxs-lookup"><span data-stu-id="59953-154">Must be configured on the Active Directory object of the remote server ( _ServerB_ ).</span></span>
- <span data-ttu-id="59953-155">Limité à un serveur.</span><span class="sxs-lookup"><span data-stu-id="59953-155">Limited to one domain.</span></span> <span data-ttu-id="59953-156">Ne peut pas traverser des domaines ou des forêts.</span><span class="sxs-lookup"><span data-stu-id="59953-156">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="59953-157">Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="59953-157">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="59953-158">_ServerB_ peut acquérir un ticket Kerberos pour _ServerC_ au nom de l’utilisateur sans intervention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59953-158">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="59953-159">Les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués.</span><span class="sxs-lookup"><span data-stu-id="59953-159">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="59953-160">Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés][blog] et [Paramètres et outils d’authentification Kerberos][ktools].</span><span class="sxs-lookup"><span data-stu-id="59953-160">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="59953-161">Délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="59953-161">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="59953-162">La délégation Kerberos contrainte basée sur les ressources (introduite dans Windows Server 2012) permet de configurer la délégation des informations d’identification sur l’objet serveur où résident les ressources.</span><span class="sxs-lookup"><span data-stu-id="59953-162">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="59953-163">Dans le scénario du deuxième saut décrit ci-dessus, vous configurez _ServerC_ pour spécifier l’emplacement où il accepte les informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="59953-163">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="59953-164">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-164">**Pros**</span></span>

- <span data-ttu-id="59953-165">Informations d’identification non stockées.</span><span class="sxs-lookup"><span data-stu-id="59953-165">Credentials are not stored.</span></span>
- <span data-ttu-id="59953-166">Configuration effectuée à l’aide des cmdlets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59953-166">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="59953-167">Pas de programmation particulière requise.</span><span class="sxs-lookup"><span data-stu-id="59953-167">No special coding required.</span></span>
- <span data-ttu-id="59953-168">Ne nécessite pas un accès Administrateur de domaine pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="59953-168">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="59953-169">Fonctionne à travers des domaines et des forêts.</span><span class="sxs-lookup"><span data-stu-id="59953-169">Works across domains and forests.</span></span>

<span data-ttu-id="59953-170">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-170">**Cons**</span></span>

- <span data-ttu-id="59953-171">Requiert Windows Server 2012 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="59953-171">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="59953-172">Ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="59953-172">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="59953-173">Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="59953-173">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="59953-174">Les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués.</span><span class="sxs-lookup"><span data-stu-id="59953-174">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="59953-175">Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés][blog] et [Paramètres et outils d’authentification Kerberos][ktools].</span><span class="sxs-lookup"><span data-stu-id="59953-175">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="59953-176">Exemple</span><span class="sxs-lookup"><span data-stu-id="59953-176">Example</span></span>

<span data-ttu-id="59953-177">Examinons un exemple PowerShell qui configure la délégation contrainte basée sur les ressources sur _ServerC_ de façon à autoriser les informations d’identification déléguées à partir d’un _ServerB_ .</span><span class="sxs-lookup"><span data-stu-id="59953-177">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_ .</span></span> <span data-ttu-id="59953-178">Cet exemple suppose que tous les serveurs exécutent Windows Server 2012 ou une version ultérieure, et qu’il existe au moins un contrôleur de domaine Windows Server 2012 sur chacun des domaines auquel appartient chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="59953-178">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="59953-179">Pour pouvoir configurer la délégation contrainte, vous devez ajouter la fonctionnalité `RSAT-AD-PowerShell` afin d’installer le module Active Directory PowerShell, puis importer ce module dans votre session :</span><span class="sxs-lookup"><span data-stu-id="59953-179">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="59953-180">Plusieurs applets de commande disponibles ont désormais un paramètre  **PrincipalsAllowedToDelegateToAccount** :</span><span class="sxs-lookup"><span data-stu-id="59953-180">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="59953-181">Le paramètre **PrincipalsAllowedToDelegateToAccount** définit l’attribut d’objet Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity** contenant une liste de contrôle d’accès (ACL) qui spécifie quels comptes ont l’autorisation de déléguer les informations d’identification au compte associé (dans notre exemple, il s’agira du compte d’ordinateur de _ServerA_ ).</span><span class="sxs-lookup"><span data-stu-id="59953-181">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity** , which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_ ).</span></span>

<span data-ttu-id="59953-182">Nous allons maintenant définir les variables que nous utiliserons pour représenter les serveurs :</span><span class="sxs-lookup"><span data-stu-id="59953-182">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="59953-183">WinRM (et par conséquent la communication à distance PowerShell) s’exécute en tant que compte d’ordinateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="59953-183">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="59953-184">Vous pouvez le constater en examinant la propriété **StartName** du service `winrm` :</span><span class="sxs-lookup"><span data-stu-id="59953-184">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="59953-185">Pour que _ServerC_ autorise la délégation à partir d’une session de communication à distance PowerShell sur _ServerB_ , nous devons définir le paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ sur l’objet d’ordinateur de _ServerB_ :</span><span class="sxs-lookup"><span data-stu-id="59953-185">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_ , we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_ :</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="59953-186">Le [Centre de distribution de clés (KDC)](/windows/win32/secauthn/key-distribution-center) Kerberos met en cache les tentatives d’accès refusées (cache négatif) pendant 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="59953-186">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="59953-187">Si _ServerB_ a précédemment essayé d’accéder à _ServerC_ , vous devez effacer le cache sur _ServerB_ en appelant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="59953-187">If _ServerB_ has previously attempted to access _ServerC_ , you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="59953-188">Vous pouvez également redémarrer l’ordinateur, ou attendre au moins 15 minutes pour effacer le cache.</span><span class="sxs-lookup"><span data-stu-id="59953-188">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="59953-189">Après avoir vidé le cache, vous pouvez exécuter le code de _ServerA_ à _ServerC_ via _ServerB_ :</span><span class="sxs-lookup"><span data-stu-id="59953-189">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_ :</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="59953-190">Dans cet exemple, la variable `$using` est utilisée pour rendre la variable `$ServerC` visible pour _ServerB_ .</span><span class="sxs-lookup"><span data-stu-id="59953-190">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_ .</span></span>
<span data-ttu-id="59953-191">Pour plus d’informations sur la variable `$using`, consultez [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span><span class="sxs-lookup"><span data-stu-id="59953-191">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="59953-192">Pour permettre à plusieurs serveurs de déléguer les informations d’identification à _ServerC_ , donnez comme valeur un tableau au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_  :</span><span class="sxs-lookup"><span data-stu-id="59953-192">To allow multiple servers to delegate credentials to _ServerC_ , set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="59953-193">Si vous souhaitez effectuer le deuxième saut entre domaines, ajoutez le nom de domaine complet (FQDN) du contrôleur du domaine auquel _ServerB_ appartient :</span><span class="sxs-lookup"><span data-stu-id="59953-193">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="59953-194">Pour supprimer la possibilité de déléguer les informations d’identification à ServerC, donnez comme valeur `$null` au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_  :</span><span class="sxs-lookup"><span data-stu-id="59953-194">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="59953-195">Informations sur la délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="59953-195">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="59953-196">[Nouveautés de l’authentification Kerberos][whats-new]</span><span class="sxs-lookup"><span data-stu-id="59953-196">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="59953-197">[Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 1][kcd2012-1]</span><span class="sxs-lookup"><span data-stu-id="59953-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="59953-198">[Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 2][kcd2012-2]</span><span class="sxs-lookup"><span data-stu-id="59953-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="59953-199">[Comprendre la délégation Kerberos contrainte pour les déploiements de proxy d’applications Azure Active Directory avec l’authentification Windows intégrée][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="59953-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="59953-200">[[MS-ADA2] : Attributs de schéma Active Directory M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="59953-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="59953-201">[[MS-SFU] : Extensions du protocole Kerberos : protocole de service pour l’utilisateur et de délégation contrainte 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="59953-201">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="59953-202">[Administration à distance sans la délégation contrainte à l’aide de PrincipalsAllowedToDelegateToAccount][remote-admin]</span><span class="sxs-lookup"><span data-stu-id="59953-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="59953-203">Délégation Kerberos (sans contraintes)</span><span class="sxs-lookup"><span data-stu-id="59953-203">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="59953-204">Vous pouvez également utiliser la délégation sans contraintes Kerberos pour effectuer le deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="59953-204">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="59953-205">Comme dans tous les scénarios Kerberos, les informations d’identification ne sont pas stockées.</span><span class="sxs-lookup"><span data-stu-id="59953-205">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="59953-206">Cette méthode ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="59953-206">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="59953-207">Cette méthode ne fournit aucun contrôle sur l’utilisation des informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="59953-207">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="59953-208">Elle est moins sécurisée que la méthode CredSSP.</span><span class="sxs-lookup"><span data-stu-id="59953-208">It is less secure than CredSSP.</span></span> <span data-ttu-id="59953-209">Cette méthode ne doit être utilisée que pour les scénarios de test.</span><span class="sxs-lookup"><span data-stu-id="59953-209">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="59953-210">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="59953-210">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="59953-211">JEA vous permet de restreindre les commandes qu’un administrateur peut exécuter au cours d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59953-211">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="59953-212">Il peut être utilisé pour résoudre le problème du deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="59953-212">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="59953-213">Pour plus d’informations sur JEA, consultez [Juste assez d’administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="59953-213">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="59953-214">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-214">**Pros**</span></span>

- <span data-ttu-id="59953-215">Aucune maintenance des mots de passe lorsque vous utilisez un compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="59953-215">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="59953-216">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-216">**Cons**</span></span>

- <span data-ttu-id="59953-217">Nécessite WMF 5.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="59953-217">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="59953-218">Requiert la configuration de chaque serveur intermédiaire ( _ServerB_ ).</span><span class="sxs-lookup"><span data-stu-id="59953-218">Requires configuration on every intermediate server ( _ServerB_ ).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="59953-219">PSSessionConfiguration avec la commande RunAs</span><span class="sxs-lookup"><span data-stu-id="59953-219">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="59953-220">Vous pouvez créer une configuration de session sur _ServerB_ et définir son paramètre **RunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="59953-220">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="59953-221">Pour plus d’informations sur l’utilisation de **PSSessionConfiguration** et de **RunAs** afin de résoudre le problème du deuxième saut, consultez [Autre solution de communication à distance PowerShell sur plusieurs sauts][pssessionconfig].</span><span class="sxs-lookup"><span data-stu-id="59953-221">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="59953-222">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-222">**Pros**</span></span>

- <span data-ttu-id="59953-223">Fonctionne avec n’importe quel serveur avec WMF 3.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="59953-223">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="59953-224">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-224">**Cons**</span></span>

- <span data-ttu-id="59953-225">Nécessite la configuration de **PSSessionConfiguration** et de **RunAs** sur chaque serveur intermédiaire ( _ServerB_ ).</span><span class="sxs-lookup"><span data-stu-id="59953-225">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server ( _ServerB_ ).</span></span>
- <span data-ttu-id="59953-226">Nécessite la maintenance des mots de passe lorsqu’un compte de domaine **RunAs** est utilisé</span><span class="sxs-lookup"><span data-stu-id="59953-226">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="59953-227">Transmettre des informations d’identification à l’intérieur d’un bloc de script Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="59953-227">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="59953-228">Vous pouvez transmettre des informations d’identification à l’intérieur du paramètre **ScriptBlock** d’un appel à l’applet de commande [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="59953-228">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="59953-229">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="59953-229">**Pros**</span></span>

- <span data-ttu-id="59953-230">Ne nécessite pas de configuration particulière du serveur.</span><span class="sxs-lookup"><span data-stu-id="59953-230">Does not require special server configuration.</span></span>
- <span data-ttu-id="59953-231">Fonctionne sur n’importe quel serveur exécutant WMF 2.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="59953-231">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="59953-232">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="59953-232">**Cons**</span></span>

- <span data-ttu-id="59953-233">Nécessite une technique de programmation délicate.</span><span class="sxs-lookup"><span data-stu-id="59953-233">Requires an awkward code technique.</span></span>
- <span data-ttu-id="59953-234">Si vous exécutez WMF 2.0, requiert une syntaxe différente pour transmettre des arguments à une session à distance.</span><span class="sxs-lookup"><span data-stu-id="59953-234">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="59953-235">Exemple</span><span class="sxs-lookup"><span data-stu-id="59953-235">Example</span></span>

<span data-ttu-id="59953-236">L’exemple suivant montre comment transmettre des informations d’identification dans un bloc de script **Invoke-Command**  :</span><span class="sxs-lookup"><span data-stu-id="59953-236">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="59953-237">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59953-237">See also</span></span>

[<span data-ttu-id="59953-238">Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="59953-238">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group

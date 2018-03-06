---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Effectuer le deuxième saut dans la communication à distance PowerShell"
ms.openlocfilehash: 726b4d1b7a41e9e344347543ecde26da6547bcf3
ms.sourcegitcommit: fff6c0522508eeb408cb055ba4c9337a2759b392
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="03cac-103">Effectuer le deuxième saut dans la communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="03cac-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="03cac-104">Le « problème du deuxième saut » fait référence à une situation de ce type :</span><span class="sxs-lookup"><span data-stu-id="03cac-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="03cac-105">Vous êtes connecté à _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="03cac-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="03cac-106">À partir de _ServerA_, vous démarrez une session PowerShell à distance pour vous connecter à _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="03cac-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="03cac-107">Une commande exécutée sur _ServerB_ via votre session de communication à distance PowerShell tente d’accéder à une ressource sur _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="03cac-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="03cac-108">L’accès à la ressource sur _ServerC_ est refusé, car les informations d’identification utilisées pour créer la session de communication à distance PowerShell ne sont pas transmises de _ServerB_ à _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="03cac-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="03cac-109">Il existe plusieurs moyens de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="03cac-109">There are several ways to address this problem.</span></span> <span data-ttu-id="03cac-110">Dans cette rubrique, nous allons étudier quelques-unes des solutions les plus courantes pour le problème du deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="03cac-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="03cac-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="03cac-111">CredSSP</span></span>

<span data-ttu-id="03cac-112">Vous pouvez utiliser le [protocole CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="03cac-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="03cac-113">Le protocole CredSSP mettant en cache les informations d’identification sur le serveur distant (_ServerB_), son utilisation vous expose à des risques de vol de ces informations.</span><span class="sxs-lookup"><span data-stu-id="03cac-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="03cac-114">Si l’ordinateur distant est compromis, la personne malveillante a accès aux informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="03cac-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="03cac-115">CredSSP est désactivé par défaut sur les ordinateurs clients et serveurs.</span><span class="sxs-lookup"><span data-stu-id="03cac-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="03cac-116">Vous devez activer CredSSP uniquement dans les environnements les plus approuvés,</span><span class="sxs-lookup"><span data-stu-id="03cac-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="03cac-117">Par exemple un administrateur de domaine qui se connecte à un contrôleur de domaine, car le contrôleur de domaine est hautement approuvé.</span><span class="sxs-lookup"><span data-stu-id="03cac-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="03cac-118">Pour plus d’informations sur les questions de sécurité lors de l’utilisation de CredSSP pour la communication à distance PowerShell, voir [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="03cac-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="03cac-119">Pour plus d’informations sur les risques de vol des informations d’identification, voir [Atténuation des attaques PtH (Pass-The-Hash) et autres risques de vol des informations d’identification](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="03cac-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="03cac-120">Pour accéder à un exemple montrant comment activer et utiliser CredSSP pour la communication à distance PowerShell, consultez [Utiliser CredSSP pour résoudre le problème du deuxième saut](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="03cac-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-121">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-121">Pros</span></span>

- <span data-ttu-id="03cac-122">Fonctionne pour tous les serveurs avec Windows Server 2008 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03cac-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-123">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-123">Cons</span></span>

- <span data-ttu-id="03cac-124">Présente des failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="03cac-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="03cac-125">Requiert la configuration des rôles client et serveur.</span><span class="sxs-lookup"><span data-stu-id="03cac-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="03cac-126">Délégation Kerberos (sans contraintes)</span><span class="sxs-lookup"><span data-stu-id="03cac-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="03cac-127">Vous pouvez également utiliser la délégation sans contraintes Kerberos pour effectuer le deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="03cac-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="03cac-128">Toutefois, cette méthode ne fournit aucun contrôle sur l’utilisation des informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="03cac-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="03cac-129">**Remarque :** les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués.</span><span class="sxs-lookup"><span data-stu-id="03cac-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="03cac-130">Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="03cac-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-131">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-131">Pros</span></span>

- <span data-ttu-id="03cac-132">Ne requiert pas de programmation particulière.</span><span class="sxs-lookup"><span data-stu-id="03cac-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-133">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-133">Cons</span></span>

- <span data-ttu-id="03cac-134">Ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="03cac-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="03cac-135">Ne fournit aucun contrôle sur l’utilisation des informations d’identification, ce qui crée une faille de sécurité.</span><span class="sxs-lookup"><span data-stu-id="03cac-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="03cac-136">Délégation Kerberos contrainte</span><span class="sxs-lookup"><span data-stu-id="03cac-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="03cac-137">Vous pouvez utiliser la délégation contrainte héritée (non basée sur les ressources) pour effectuer le deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="03cac-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> 

><span data-ttu-id="03cac-138">**Remarque :** les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués.</span><span class="sxs-lookup"><span data-stu-id="03cac-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="03cac-139">Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="03cac-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-140">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-140">Pros</span></span>

- <span data-ttu-id="03cac-141">Ne requiert pas de programmation particulière.</span><span class="sxs-lookup"><span data-stu-id="03cac-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-142">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-142">Cons</span></span>

- <span data-ttu-id="03cac-143">Ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="03cac-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="03cac-144">Doit être configuré sur l’objet Active Directory du serveur distant (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="03cac-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="03cac-145">Limité à un serveur.</span><span class="sxs-lookup"><span data-stu-id="03cac-145">Limited to one domain.</span></span> <span data-ttu-id="03cac-146">Ne peut pas traverser des domaines ou des forêts.</span><span class="sxs-lookup"><span data-stu-id="03cac-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="03cac-147">Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="03cac-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="03cac-148">Délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="03cac-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="03cac-149">La délégation Kerberos contrainte basée sur les ressources (introduite dans Windows Server 2012) permet de configurer la délégation des informations d’identification sur l’objet serveur où résident les ressources.</span><span class="sxs-lookup"><span data-stu-id="03cac-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="03cac-150">Dans le scénario du deuxième saut décrit ci-dessus, vous configurez _ServerC_ pour spécifier l’emplacement où il acceptera les informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="03cac-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="03cac-151">**Remarque :** les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués.</span><span class="sxs-lookup"><span data-stu-id="03cac-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="03cac-152">Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="03cac-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-153">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-153">Pros</span></span>

- <span data-ttu-id="03cac-154">Informations d’identification non stockées.</span><span class="sxs-lookup"><span data-stu-id="03cac-154">Credentials are not stored.</span></span>
- <span data-ttu-id="03cac-155">Relativement facile à configurer à l’aide des applets de commande PowerShell, sans programmation particulière.</span><span class="sxs-lookup"><span data-stu-id="03cac-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="03cac-156">Aucun domaine spécial n’est requis.</span><span class="sxs-lookup"><span data-stu-id="03cac-156">No special domain access is required.</span></span>
- <span data-ttu-id="03cac-157">Fonctionne à travers des domaines et des forêts.</span><span class="sxs-lookup"><span data-stu-id="03cac-157">Works across domains and forests.</span></span>
- <span data-ttu-id="03cac-158">Code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03cac-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-159">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-159">Cons</span></span>

- <span data-ttu-id="03cac-160">Requiert Windows Server 2012 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03cac-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="03cac-161">Ne prend pas en charge le deuxième saut pour WinRM.</span><span class="sxs-lookup"><span data-stu-id="03cac-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="03cac-162">Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="03cac-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span> 

### <a name="example"></a><span data-ttu-id="03cac-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="03cac-163">Example</span></span>

<span data-ttu-id="03cac-164">Examinons un exemple PowerShell qui configure la délégation contrainte basée sur les ressources sur _ServerC_ de façon à autoriser les informations d’identification déléguées à partir d’un _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="03cac-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="03cac-165">Cet exemple suppose que tous les serveurs exécutent Windows Server 2012 ou une version ultérieure, et qu’il existe au moins un contrôleur de domaine Windows Server 2012 sur chacun des domaines auquel appartient chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="03cac-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="03cac-166">Pour pouvoir configurer la délégation contrainte, vous devez ajouter la fonctionnalité `RSAT-AD-PowerShell` afin d’installer le module Active Directory PowerShell, puis importer ce module dans votre session :</span><span class="sxs-lookup"><span data-stu-id="03cac-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="03cac-167">Plusieurs applets de commande disponibles ont désormais un paramètre **PrincipalsAllowedToDelegateToAccount** :</span><span class="sxs-lookup"><span data-stu-id="03cac-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName     
----------- ----                 ----------     
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="03cac-168">Le paramètre **PrincipalsAllowedToDelegateToAccount** définit l’attribut d’objet Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity** contenant une liste de contrôle d’accès (ACL) qui spécifie quels comptes ont l’autorisation de déléguer les informations d’identification au compte associé (dans notre exemple, il s’agira du compte d’ordinateur de _Server_).</span><span class="sxs-lookup"><span data-stu-id="03cac-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="03cac-169">Nous allons maintenant définir les variables que nous utiliserons pour représenter les serveurs :</span><span class="sxs-lookup"><span data-stu-id="03cac-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

<span data-ttu-id="03cac-170">WinRM (et par conséquent la communication à distance PowerShell) s’exécute en tant que compte d’ordinateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="03cac-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="03cac-171">Vous pouvez le constater en examinant la propriété **StartName** du service `winrm` :</span><span class="sxs-lookup"><span data-stu-id="03cac-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="03cac-172">Pour que _ServerC_ autorise la délégation à partir d’une session de communication à distance PowerShell sur _ServerB_, nous allons accorder l’accès en donnant comme valeur au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ l’objet d’ordinateur de _ServerB_ :</span><span class="sxs-lookup"><span data-stu-id="03cac-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="03cac-173">Le [Centre de distribution de clés (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) Kerberos met en cache les tentatives d’accès refusées (cache négatif) pendant 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="03cac-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="03cac-174">Si _ServerB_ a précédemment essayé d’accéder à _ServerC_, vous devez effacer le cache sur _ServerB_ en appelant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="03cac-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

<span data-ttu-id="03cac-175">Vous pouvez également redémarrer l’ordinateur, ou attendre au moins 15 minutes pour effacer le cache.</span><span class="sxs-lookup"><span data-stu-id="03cac-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="03cac-176">Après avoir vidé le cache, vous pouvez exécuter le code de _ServerA_ à _ServerC_ via _ServerB_ :</span><span class="sxs-lookup"><span data-stu-id="03cac-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="03cac-177">Dans cet exemple, la variable `$using` est utilisée pour rendre la variable `$ServerC` visible pour _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="03cac-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="03cac-178">Pour plus d’informations sur la variable `$using`, consultez [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="03cac-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span></span>

<span data-ttu-id="03cac-179">Pour permettre à plusieurs serveurs de déléguer les informations d’identification à _ServerC_, donnez comme valeur un tableau au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ :</span><span class="sxs-lookup"><span data-stu-id="03cac-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="03cac-180">Si vous souhaitez effectuer le deuxième saut entre domaines, ajoutez le nom de domaine complet (FQDN) du contrôleur du domaine auquel _ServerB_ appartient :</span><span class="sxs-lookup"><span data-stu-id="03cac-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="03cac-181">Pour supprimer la possibilité de déléguer les informations d’identification à ServerC, donnez comme valeur `$null` au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ :</span><span class="sxs-lookup"><span data-stu-id="03cac-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="03cac-182">Informations sur la délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="03cac-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="03cac-183">Nouveautés de l’authentification Kerberos</span><span class="sxs-lookup"><span data-stu-id="03cac-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="03cac-184">Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 1</span><span class="sxs-lookup"><span data-stu-id="03cac-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="03cac-185">Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 2</span><span class="sxs-lookup"><span data-stu-id="03cac-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="03cac-186">Comprendre la délégation Kerberos contrainte pour les déploiements de proxy d’applications Azure Active Directory avec l’authentification Windows intégrée</span><span class="sxs-lookup"><span data-stu-id="03cac-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](http://aka.ms/kcdpaper)
- <span data-ttu-id="03cac-187">[[MS-ADA2] : Attributs de schéma Active Directory M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="03cac-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span></span>
- <span data-ttu-id="03cac-188">[[MS-SFU] : extensions du protocole Kerberos : protocole de service pour l’utilisateur et de délégation contrainte 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="03cac-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="03cac-189">Délégation Kerberos contrainte basée sur les ressources</span><span class="sxs-lookup"><span data-stu-id="03cac-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="03cac-190">Administration à distance sans la délégation contrainte à l’aide de PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="03cac-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="03cac-191">PSSessionConfiguration avec la commande RunAs</span><span class="sxs-lookup"><span data-stu-id="03cac-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="03cac-192">Vous pouvez créer une configuration de session sur _ServerB_ et définir son paramètre **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="03cac-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="03cac-193">Pour plus d’informations sur l’utilisation de PSSessionConfiguration et de RunAs afin de résoudre le problème du deuxième saut, consultez [Autre solution de communication à distance PowerShell sur plusieurs sauts](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="03cac-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-194">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-194">Pros</span></span>

- <span data-ttu-id="03cac-195">Fonctionne avec n’importe quel serveur avec WMF 3.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03cac-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-196">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-196">Cons</span></span>

- <span data-ttu-id="03cac-197">Nécessite la configuration de **PSSessionConfiguration** et de **RunAs** sur chaque serveur intermédiaire (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="03cac-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="03cac-198">Nécessite la maintenance des mots de passe lorsqu’un compte de domaine **RunAs** est utilisé</span><span class="sxs-lookup"><span data-stu-id="03cac-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="03cac-199">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="03cac-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="03cac-200">JEA vous permet de restreindre les commandes qu’un administrateur peut exécuter au cours d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03cac-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="03cac-201">Il peut être utilisé pour résoudre le problème du deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="03cac-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="03cac-202">Pour plus d’informations sur JEA, consultez [Juste assez d’administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="03cac-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-203">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-203">Pros</span></span>

- <span data-ttu-id="03cac-204">Aucune maintenance des mots de passe lorsque vous utilisez un compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="03cac-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-205">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-205">Cons</span></span>

- <span data-ttu-id="03cac-206">Nécessite WMF 5.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03cac-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="03cac-207">Requiert la configuration de chaque serveur intermédiaire (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="03cac-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="03cac-208">Transmettre des informations d’identification à l’intérieur d’un bloc de script Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="03cac-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="03cac-209">Vous pouvez transmettre des informations d’identification à l’intérieur du paramètre **ScriptBlock** d’un appel à l’applet de commande [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="03cac-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="03cac-210">Avantages</span><span class="sxs-lookup"><span data-stu-id="03cac-210">Pros</span></span>

- <span data-ttu-id="03cac-211">Ne nécessite pas de configuration particulière du serveur.</span><span class="sxs-lookup"><span data-stu-id="03cac-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="03cac-212">Fonctionne sur n’importe quel serveur exécutant WMF 2.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="03cac-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="03cac-213">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="03cac-213">Cons</span></span>

- <span data-ttu-id="03cac-214">Nécessite une technique de programmation délicate.</span><span class="sxs-lookup"><span data-stu-id="03cac-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="03cac-215">Si vous exécutez WMF 2.0, requiert une syntaxe différente pour transmettre des arguments à une session à distance.</span><span class="sxs-lookup"><span data-stu-id="03cac-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="03cac-216">Exemple</span><span class="sxs-lookup"><span data-stu-id="03cac-216">Example</span></span>

<span data-ttu-id="03cac-217">L’exemple suivant montre comment transmettre des informations d’identification dans un bloc de script **Invoke-Command** :</span><span class="sxs-lookup"><span data-stu-id="03cac-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a><span data-ttu-id="03cac-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03cac-218">See also</span></span>

[<span data-ttu-id="03cac-219">Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="03cac-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)








 

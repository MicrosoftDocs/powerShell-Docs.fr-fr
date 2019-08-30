---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Considérations de sécurité JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017770"
---
# <a name="jea-security-considerations"></a><span data-ttu-id="b3a5c-103">Considérations de sécurité JEA</span><span class="sxs-lookup"><span data-stu-id="b3a5c-103">JEA Security Considerations</span></span>

<span data-ttu-id="b3a5c-104">JEA vous aide à améliorer votre sécurité en réduisant le nombre d’administrateurs permanents sur vos machines.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-104">JEA helps you improve your security posture by reducing the number of permanent administrators on your machines.</span></span> <span data-ttu-id="b3a5c-105">JEA utilise une configuration de session PowerShell pour créer un point d’entrée pour les utilisateurs afin de gérer le système.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-105">JEA uses a PowerShell session configuration to create a new entry point for users to manage the system.</span></span> <span data-ttu-id="b3a5c-106">Les utilisateurs ayant besoin d’un accès à la machine avec des privilèges élevés mais pas illimités pour effectuer des tâches d’administration peuvent recevoir l’accès au point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-106">Users who need elevated, but not unlimited, access to the machine to do administrative tasks can be granted access to the JEA endpoint.</span></span> <span data-ttu-id="b3a5c-107">Comme JEA les autorise à exécuter des commandes d’administration sans disposer d’un accès d’administration complet, vous pouvez supprimer ces utilisateurs de groupes de sécurité disposant de privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-107">Since JEA allows these users to run admin commands without having full admin access, you can then remove those users from highly privileged security groups.</span></span>

## <a name="run-as-account"></a><span data-ttu-id="b3a5c-108">Compte d’identification</span><span class="sxs-lookup"><span data-stu-id="b3a5c-108">Run-As account</span></span>

<span data-ttu-id="b3a5c-109">Chaque point de terminaison JEA a un compte **d’identification** désigné.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-109">Each JEA endpoint has a designated **run-as** account.</span></span> <span data-ttu-id="b3a5c-110">Il s’agit du compte sous lequel les actions de l’utilisateur connecté sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-110">This is the account under which the connecting user's actions are executed.</span></span> <span data-ttu-id="b3a5c-111">Ce compte est configurable dans le [fichier de configuration de session](session-configurations.md), et le compte que vous choisissez a une incidence considérable sur la sécurité de votre point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-111">This account is configurable in the [session configuration file](session-configurations.md), and the account you choose has a significant bearing on the security of your endpoint.</span></span>

<span data-ttu-id="b3a5c-112">Les **comptes virtuels** sont la méthode recommandée pour la configuration du compte **d’identification**.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-112">**Virtual accounts** are the recommended way of configuring the **run-as** account.</span></span> <span data-ttu-id="b3a5c-113">Les comptes virtuels sont des comptes locaux à usage unique temporaires, qui sont créés pour l’utilisateur qui se connecte à utiliser pendant la durée de sa session JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-113">Virtual accounts are one-time, temporary local accounts that are created for the connecting user to use during the duration of their JEA session.</span></span> <span data-ttu-id="b3a5c-114">Dès que la session est terminée, le compte virtuel est détruit et ne peut plus être utilisé.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-114">As soon as their session is terminated, the virtual account is destroyed and can't be used anymore.</span></span> <span data-ttu-id="b3a5c-115">L’utilisateur connecté ne connaît pas les informations d’identification pour le compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-115">The connecting user doesn't know the credentials for the virtual account.</span></span> <span data-ttu-id="b3a5c-116">Le compte virtuel ne peut pas être utilisé pour accéder au système par d’autres moyens, comme Bureau à distance ou un point de terminaison PowerShell sans contrainte.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-116">The virtual account can't be used to access the system via other means like Remote Desktop or an unconstrained PowerShell endpoint.</span></span>

<span data-ttu-id="b3a5c-117">Par défaut, les comptes virtuels appartiennent au groupe **Administrateurs** local sur la machine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-117">By default, virtual accounts belong to the local **Administrators** group on the machine.</span></span> <span data-ttu-id="b3a5c-118">Ainsi, ils disposent des droits complets pour gérer n’importe quel élément sur le système, mais pas de droits pour gérer les ressources sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-118">This gives them full rights to manage anything on the system, but no rights to manage resources on the network.</span></span>
<span data-ttu-id="b3a5c-119">Lors de l’authentification auprès d’autres machines, le contexte de l’utilisateur est celui du compte d’ordinateur local, et non pas celui du compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-119">When authenticating with other machines, the user context is that of the local computer account, not the virtual account.</span></span>

<span data-ttu-id="b3a5c-120">Les contrôleurs de domaine constituent un cas particulier dans la mesure où il n’y a pas de groupe **Administrateurs** local.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-120">Domain controllers are a special case since there isn't a local **Administrators** group.</span></span> <span data-ttu-id="b3a5c-121">Au lieu de cela, les comptes virtuels appartiennent à **Administrateurs du domaine** et peuvent gérer les services d’annuaire sur le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-121">Instead, virtual accounts belong to **Domain Admins** and can manage the directory services on the domain controller.</span></span> <span data-ttu-id="b3a5c-122">L’identité du domaine reste limitée à une utilisation sur le contrôleur de domaine où la session JEA a été instanciée.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-122">The domain identity is still restricted for use on the domain controller where the JEA session was instantiated.</span></span> <span data-ttu-id="b3a5c-123">Les accès réseau paraissent à la place provenir de l’objet ordinateur du contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-123">Any network access appears to come from the domain controller computer object instead.</span></span>

<span data-ttu-id="b3a5c-124">Dans les deux cas, vous pouvez définir explicitement les groupes de sécurité auxquels le compte virtuel appartient.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-124">In both cases, you may explicitly define which security groups the virtual account belongs to.</span></span> <span data-ttu-id="b3a5c-125">Il s’agit d’une bonne pratique quand la tâche peut être effectuée sans privilèges d’administrateur local ou de domaine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-125">This is a good practice when the task can be done without local or domain admin privileges.</span></span> <span data-ttu-id="b3a5c-126">Si vous disposez déjà d’un groupe de sécurité défini pour vos administrateurs, accordez l’appartenance au compte virtuel à ce groupe.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-126">If you already have a security group defined for your admins, grant the virtual account membership to that group.</span></span> <span data-ttu-id="b3a5c-127">L’appartenance des comptes virtuels à des groupes est limitée à des groupes de sécurité locaux sur la station de travail et les serveurs membres.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-127">Virtual account group membership is limited to local security groups on workstation and member servers.</span></span> <span data-ttu-id="b3a5c-128">Sur les contrôleurs de domaine, les comptes virtuels doivent être membres des groupes de sécurité du domaine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-128">On domain controllers, virtual accounts must be members of domain security groups.</span></span>
<span data-ttu-id="b3a5c-129">Une fois que le compte virtuel a été ajouté à un ou plusieurs groupes de sécurité, il n’appartient plus aux groupes par défaut (Administrateurs locaux ou du domaine).</span><span class="sxs-lookup"><span data-stu-id="b3a5c-129">Once the virtual account has been added to one or more security groups, it no longer belongs to the default groups (local or domain admins).</span></span>

<span data-ttu-id="b3a5c-130">Le tableau suivant récapitule les options de configuration possibles et les autorisations qui en résultent pour les comptes virtuels :</span><span class="sxs-lookup"><span data-stu-id="b3a5c-130">The following table summarizes the possible configuration options and resulting permissions for virtual accounts:</span></span>

|        <span data-ttu-id="b3a5c-131">Type d’ordinateur</span><span class="sxs-lookup"><span data-stu-id="b3a5c-131">Computer type</span></span>         | <span data-ttu-id="b3a5c-132">Configuration du groupe du compte virtuel</span><span class="sxs-lookup"><span data-stu-id="b3a5c-132">Virtual account group configuration</span></span> |                   <span data-ttu-id="b3a5c-133">Contexte de l’utilisateur local</span><span class="sxs-lookup"><span data-stu-id="b3a5c-133">Local user context</span></span>                    | <span data-ttu-id="b3a5c-134">Contexte de l’utilisateur réseau</span><span class="sxs-lookup"><span data-stu-id="b3a5c-134">Network user context</span></span> |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| <span data-ttu-id="b3a5c-135">Contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="b3a5c-135">Domain controller</span></span>            | <span data-ttu-id="b3a5c-136">Par défaut</span><span class="sxs-lookup"><span data-stu-id="b3a5c-136">Default</span></span>                             | <span data-ttu-id="b3a5c-137">Utilisateur de domaine, membre de « *DOMAIN*\Domain Admins »</span><span class="sxs-lookup"><span data-stu-id="b3a5c-137">Domain user, member of '*DOMAIN*\Domain Admins'</span></span>         | <span data-ttu-id="b3a5c-138">Compte d'ordinateur</span><span class="sxs-lookup"><span data-stu-id="b3a5c-138">Computer account</span></span>     |
| <span data-ttu-id="b3a5c-139">Contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="b3a5c-139">Domain controller</span></span>            | <span data-ttu-id="b3a5c-140">Groupes de domaine A et B</span><span class="sxs-lookup"><span data-stu-id="b3a5c-140">Domain groups A and B</span></span>               | <span data-ttu-id="b3a5c-141">Utilisateur de domaine, membre de « *DOMAIN*\A », « *DOMAIN*\B »</span><span class="sxs-lookup"><span data-stu-id="b3a5c-141">Domain user, member of '*DOMAIN*\A', '*DOMAIN*\B'</span></span>       | <span data-ttu-id="b3a5c-142">Compte d'ordinateur</span><span class="sxs-lookup"><span data-stu-id="b3a5c-142">Computer account</span></span>     |
| <span data-ttu-id="b3a5c-143">Serveur membre ou station de travail</span><span class="sxs-lookup"><span data-stu-id="b3a5c-143">Member server or workstation</span></span> | <span data-ttu-id="b3a5c-144">Par défaut</span><span class="sxs-lookup"><span data-stu-id="b3a5c-144">Default</span></span>                             | <span data-ttu-id="b3a5c-145">Utilisateur local, membre de « *BUILTIN*\Administrators »</span><span class="sxs-lookup"><span data-stu-id="b3a5c-145">Local user, member of '*BUILTIN*\Administrators'</span></span>        | <span data-ttu-id="b3a5c-146">Compte d'ordinateur</span><span class="sxs-lookup"><span data-stu-id="b3a5c-146">Computer account</span></span>     |
| <span data-ttu-id="b3a5c-147">Serveur membre ou station de travail</span><span class="sxs-lookup"><span data-stu-id="b3a5c-147">Member server or workstation</span></span> | <span data-ttu-id="b3a5c-148">Groupes locaux C et D</span><span class="sxs-lookup"><span data-stu-id="b3a5c-148">Local groups C and D</span></span>                | <span data-ttu-id="b3a5c-149">Utilisateur local, le membre de« *COMPUTER*\C » et « *COMPUTER*\D »</span><span class="sxs-lookup"><span data-stu-id="b3a5c-149">Local user, member of '*COMPUTER*\C' and '*COMPUTER*\D'</span></span> | <span data-ttu-id="b3a5c-150">Compte d'ordinateur</span><span class="sxs-lookup"><span data-stu-id="b3a5c-150">Computer account</span></span>     |

<span data-ttu-id="b3a5c-151">Quand vous examinez les événements d’audit de sécurité et les journaux des événements d’applications, vous voyez que chaque session d’utilisateur JEA a un compte virtuel unique.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-151">When you look at security audit events and application event logs, you see that each JEA user session has a unique virtual account.</span></span> <span data-ttu-id="b3a5c-152">Ce compte unique vous permet de retracer les actions de l’utilisateur dans un point de terminaison JEA jusqu’à l’utilisateur d’origine qui a exécuté la commande.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-152">This unique account helps you track user actions in a JEA endpoint back to the original user who ran the command.</span></span> <span data-ttu-id="b3a5c-153">Les noms de compte virtuel sont au format `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>`. Par exemple, si l’utilisateur **Alice** dans le domaine **Contoso** redémarre un service dans un point de terminaison JEA, le nom d’utilisateur associé à des événements du Gestionnaire de contrôle des services est `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-153">Virtual account names follow the format `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` For example, if user **Alice** in domain **Contoso** restarts a service in a JEA endpoint, the username associated with any service control manager events would be `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.</span></span>

<span data-ttu-id="b3a5c-154">Les **comptes de service gérés de groupe (GMSA)** sont pratiques quand un serveur membre doit avoir accès à des ressources réseau dans la session JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-154">**Group-managed service accounts (gMSAs)** are useful when a member server needs to have access to network resources in the JEA session.</span></span> <span data-ttu-id="b3a5c-155">Par exemple, quand un point de terminaison JEA est utilisé pour contrôler l’accès à un service d’API REST hébergé sur une autre machine.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-155">For example, when a JEA endpoint is used to control access to a REST API service hosted on a different machine.</span></span> <span data-ttu-id="b3a5c-156">Il est facile d’écrire des fonctions pour appeler les API REST, mais vous avez besoin d’une identité réseau pour vous authentifier auprès de l’API.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-156">It's easy to write functions to invoke the REST APIs, but you need a network identity to authenticate with the API.</span></span> <span data-ttu-id="b3a5c-157">Un compte de service géré de groupe rend possible le second tronçon tout en conservant le contrôle avec lequel les ordinateurs peuvent utiliser le compte.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-157">Using a group-managed service account makes the second hop possible while maintaining control over which computers can use the account.</span></span> <span data-ttu-id="b3a5c-158">Les autorisations effectives du gMSA sont définies par les groupes de sécurité (locaux ou de domaine) auquel appartient le compte gMSA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-158">The effective permissions of the gMSA are defined by the security groups (local or domain) to which the gMSA account belongs.</span></span>

<span data-ttu-id="b3a5c-159">Quand un point de terminaison JEA est configuré pour utiliser un compte GMSA, les actions de tous les utilisateurs JEA paraissent provenir du même compte GMSA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-159">When a JEA endpoint is configured to use a gMSA, the actions of all JEA users appear to come from the same gMSA.</span></span> <span data-ttu-id="b3a5c-160">La seule manière de retracer des actions jusqu’à un utilisateur spécifique est d’identifier le jeu de commandes exécuté dans une transcription de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-160">The only way to trace actions back to a specific user is to identify the set of commands run in a PowerShell session transcript.</span></span>

<span data-ttu-id="b3a5c-161">Des **informations d’identification directes** sont utilisées quand vous ne spécifiez pas de compte**d’identification**.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-161">**Pass-thru credentials** are used when you don't specify a **run-as** account.</span></span> <span data-ttu-id="b3a5c-162">PowerShell utilise les informations d’identification de l’utilisateur connecté pour exécuter des commandes sur le serveur distant.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-162">PowerShell uses the connecting user's credential to run commands on the remote server.</span></span> <span data-ttu-id="b3a5c-163">Ceci vous oblige à accorder à l’utilisateur connecté un accès direct à des groupes d’administration privilégiés.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-163">This requires you to grant the connecting user direct access to privileged management groups.</span></span> <span data-ttu-id="b3a5c-164">Cette configuration n’est **pas** recommandée pour JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-164">This configuration is **not** recommended for JEA.</span></span> <span data-ttu-id="b3a5c-165">Si l’utilisateur connecté a déjà des privilèges d’administrateur, il peut éviter JEA et gérer le système par d’autres moyens sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-165">If the connecting user already has admin privileges, they can avoid JEA and manage the system via other, unconstrained means.</span></span> <span data-ttu-id="b3a5c-166">Pour plus d’informations, consultez la section ci-dessous sur la façon dont [JEA ne protège pas contre les administrateurs](#jea-doesnt-protect-against-admins).</span><span class="sxs-lookup"><span data-stu-id="b3a5c-166">For more information, see the section below on how [JEA doesn't protect against admins](#jea-doesnt-protect-against-admins).</span></span>

<span data-ttu-id="b3a5c-167">Les **comptes d’identification standard** vous permettent de spécifier un compte d’utilisateur sous lequel l’ensemble de la session PowerShell s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-167">**Standard run-as accounts** allow you to specify any user account under which the entire PowerShell session runs.</span></span> <span data-ttu-id="b3a5c-168">Les configurations de session utilisant des comptes **d’identification** (avec le paramètre `-RunAsCredential`) n’ont pas connaissance de JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-168">Session configurations using fixed **run-as** accounts (with the `-RunAsCredential` parameter) aren't JEA-aware.</span></span> <span data-ttu-id="b3a5c-169">Les définitions de rôles ne fonctionnent plus comme attendu.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-169">Role definitions no longer function as expected.</span></span> <span data-ttu-id="b3a5c-170">Chaque utilisateur autorisé à accéder au point de terminaison reçoit le même rôle.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-170">Every user authorized to access the endpoint is assigned the same role.</span></span>

<span data-ttu-id="b3a5c-171">Vous ne devez pas utiliser **RunAsCredential** sur un point de terminaison JEA, car il est difficile de retracer les actions jusqu’à des utilisateurs spécifiques et en raison de l’absence de prise en charge du mappage des utilisateurs aux rôles.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-171">You shouldn't use a **RunAsCredential** on a JEA endpoint because it's difficult to trace actions back to specific users and lacks support for mapping users to roles.</span></span>

## <a name="winrm-endpoint-acl"></a><span data-ttu-id="b3a5c-172">Liste de contrôle d’accès de point de terminaison WinRM</span><span class="sxs-lookup"><span data-stu-id="b3a5c-172">WinRM Endpoint ACL</span></span>

<span data-ttu-id="b3a5c-173">Comme avec les points de terminaison de communication à distance PowerShell standard, chaque point de terminaison JEA a une liste de contrôle d’accès (ACL) distincte qui contrôle les utilisateurs pouvant s’authentifier auprès du point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-173">As with regular PowerShell remoting endpoints, each JEA endpoint has a separate access control list (ACL) that controls who can authenticate with the JEA endpoint.</span></span> <span data-ttu-id="b3a5c-174">S’il est mal configuré, les utilisateurs approuvés pourraient ne pas être en mesure d’accéder au point de terminaison JEA et des utilisateurs non approuvés pourraient par contre y accéder.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-174">If improperly configured, trusted users may not be able to access the JEA endpoint and untrusted users may have access.</span></span> <span data-ttu-id="b3a5c-175">La liste de contrôle d’accès WinRM n’affecte pas la mise en correspondance des utilisateurs aux rôles JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-175">The WinRM ACL doesn't affect the mapping of users to JEA roles.</span></span> <span data-ttu-id="b3a5c-176">La mise en correspondance est contrôlée par le champ **RoleDefinitions** dans le fichier de configuration de session utilisé pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-176">Mapping is controlled by the **RoleDefinitions** field in the session configuration file used to register the endpoint.</span></span>

<span data-ttu-id="b3a5c-177">Par défaut, quand un point de terminaison JEA a plusieurs capacités de rôle, la liste de contrôle d’accès WinRM est configurée pour autoriser l’accès à tous les utilisateurs mappés.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-177">By default, when a JEA endpoint has multiple role capabilities, the WinRM ACL is configured to allow access to all mapped users.</span></span> <span data-ttu-id="b3a5c-178">Par exemple, une session JEA configurée à l’aide des commandes suivantes accorde un accès complet à `CONTOSO\JEA_Lev1` et à `CONTOSO\JEA_Lev2`.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-178">For example, a JEA session configured using the following commands grants full access to `CONTOSO\JEA_Lev1` and `CONTOSO\JEA_Lev2`.</span></span>

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

<span data-ttu-id="b3a5c-179">Vous pouvez auditer les autorisations des utilisateurs avec l’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="b3a5c-179">You can audit user permissions with the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

<span data-ttu-id="b3a5c-180">Pour modifier les utilisateurs disposant d’un accès, exécutez `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` pour une invite interactive ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` pour mettre à jour les autorisations.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-180">To change which users have access, run either `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` for an interactive prompt or `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` to update the permissions.</span></span> <span data-ttu-id="b3a5c-181">Les utilisateurs doivent au moins disposer de droits *Invoke* pour accéder au point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-181">Users need at least *Invoke* rights to access the JEA endpoint.</span></span>

<span data-ttu-id="b3a5c-182">Il est possible de créer un point de terminaison JEA qui n’associe pas un rôle défini à chaque utilisateur qui a accès.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-182">It's possible to create a JEA endpoint that doesn't map a defined role to every user that has access.</span></span> <span data-ttu-id="b3a5c-183">Ces utilisateurs peuvent démarrer une session JEA, mais ont accès seulement aux applets de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-183">These users can start a JEA session, but only have access to the default cmdlets.</span></span> <span data-ttu-id="b3a5c-184">Vous pouvez auditer les autorisations utilisateur dans un point de terminaison JEA en exécutant `Get-PSSessionCapability`.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-184">You can audit user permissions in a JEA endpoint by running `Get-PSSessionCapability`.</span></span> <span data-ttu-id="b3a5c-185">Pour plus d’informations, consultez [Audit et création de rapports sur JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="b3a5c-185">For more information, see [Auditing and Reporting on JEA](audit-and-report.md).</span></span>

## <a name="least-privilege-roles"></a><span data-ttu-id="b3a5c-186">Rôles avec des privilèges minimum</span><span class="sxs-lookup"><span data-stu-id="b3a5c-186">Least privilege roles</span></span>

<span data-ttu-id="b3a5c-187">Quand vous concevez des rôles JEA, il est important de se rappeler que le compte virtuel et le compte de service géré de groupe exécuté en arrière-plan peut avoir un accès sans limitations à la machine locale.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-187">When designing JEA roles, it's important to remember that the virtual and group-managed service accounts running behind the scenes can have unrestricted access to the local machine.</span></span> <span data-ttu-id="b3a5c-188">Les capacités de rôle JEA vous aident à limiter les commandes et les applications qui peuvent être exécutées dans ce contexte privilégié.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-188">JEA role capabilities help limit the commands and applications that can be run in that privileged context.</span></span>
<span data-ttu-id="b3a5c-189">Les rôles incorrectement conçus peuvent autoriser des commandes dangereuses qui peuvent permettre à un utilisateur de sortir des limites JEA ou d’accéder à des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-189">Improperly designed roles can allow dangerous commands that may permit a user to break out of the JEA boundaries or obtain access to sensitive information.</span></span>

<span data-ttu-id="b3a5c-190">Par exemple, examinez l’entrée de fonctionnalités de rôle suivante :</span><span class="sxs-lookup"><span data-stu-id="b3a5c-190">For example, consider the following role capability entry:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

<span data-ttu-id="b3a5c-191">Cette capacité de rôle permet aux utilisateurs d’exécuter toutes les applets de commande PowerShell avec le nom **Process** à partir du module **Microsoft.PowerShell.Management**.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-191">This role capability allows users to run any PowerShell cmdlet with the noun **Process** from the **Microsoft.PowerShell.Management** module.</span></span> <span data-ttu-id="b3a5c-192">Les utilisateurs peuvent avoir besoin d’accéder à des applets de commande comme `Get-Process` pour voir quelles applications s’exécutent sur le système, et `Stop-Process` pour mettre fin aux applications qui ne répondent pas.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-192">Users may need to access cmdlets like `Get-Process` to see what applications are running on the system and `Stop-Process` to kill applications that aren't responding.</span></span> <span data-ttu-id="b3a5c-193">Toutefois, cette entrée autorise également `Start-Process`, qui peut être utilisé pour lancer un programme arbitraire avec des autorisations d’administrateur complètes.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-193">However, this entry also allows `Start-Process`, which can be used to start up an arbitrary program with full administrator permissions.</span></span> <span data-ttu-id="b3a5c-194">Le programme n’a pas besoin d’être installé localement sur le système.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-194">The program doesn't need to be installed locally on the system.</span></span> <span data-ttu-id="b3a5c-195">Un utilisateur connecté peut démarrer un programme à partir d’un partage de fichiers, qui donne à l’utilisateur des privilèges d’administrateur local, exécute des programmes malveillants, etc.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-195">A connected user could start a program from a file share that gives the user local admin privileges, runs malware, and more.</span></span>

<span data-ttu-id="b3a5c-196">Une version plus sécurisée de cette même fonctionnalité de rôle ressemblerait à la version suivante :</span><span class="sxs-lookup"><span data-stu-id="b3a5c-196">A more secure version of this same role capability would look like:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

<span data-ttu-id="b3a5c-197">Évitez d’utiliser des caractères génériques dans les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-197">Avoid using wildcards in role capabilities.</span></span> <span data-ttu-id="b3a5c-198">Veillez à [auditer les autorisations effectives des utilisateurs ](audit-and-report.md#check-effective-rights-for-a-specific-user) de façon régulière pour comprendre les commandes accessibles aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-198">Be sure to regularly [audit effective user permissions](audit-and-report.md#check-effective-rights-for-a-specific-user) to understand which commands are accessible to the user.</span></span>

## <a name="jea-doesnt-protect-against-admins"></a><span data-ttu-id="b3a5c-199">JEA ne protège pas contre les administrateurs</span><span class="sxs-lookup"><span data-stu-id="b3a5c-199">JEA doesn't protect against admins</span></span>

<span data-ttu-id="b3a5c-200">Un des principes fondamentaux de JEA est de permettre à des utilisateurs non administrateurs d’effectuer certaines tâches d’administration.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-200">One of the core principles of JEA is that it allows non-admins to do some admin tasks.</span></span> <span data-ttu-id="b3a5c-201">JEA ne protège pas contre les utilisateurs qui ont déjà des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-201">JEA doesn't protect against users who already have administrator privileges.</span></span> <span data-ttu-id="b3a5c-202">Les utilisateurs qui appartiennent au groupe **Admins du domaine**, au groupe **Administrateurs** local ou à d’autres groupes disposant de privilèges élevés peuvent contourner les protections de JEA par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-202">Users who belong **Domain Admins**, local **Administrators**, or other highly privileged groups can circumvent JEA's protections via another means.</span></span> <span data-ttu-id="b3a5c-203">Par exemple, ils pourraient se connecter avec RDP, utiliser des consoles MMC distantes ou se connecter à des points de terminaison PowerShell sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-203">For example, they could sign in with RDP, use remote MMC consoles, or connect to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="b3a5c-204">De même, les administrateurs locaux sur un système peuvent modifier les configurations de JEA pour autoriser d’autres utilisateurs ou modifier une capacité de rôle de façon à agrandir l’étendue de ce qu’un utilisateur peut faire dans sa session JEA.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-204">Also, local admins on a system can modify JEA configurations to allow additional users or change a role capability to extend the scope of what a user can do in their JEA session.</span></span> <span data-ttu-id="b3a5c-205">Il est important d’évaluer les autorisations étendues de vos utilisateurs JEA pour voir s’ils peuvent obtenir un accès privilégié au système d’une autre manière.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-205">It's important to evaluate your JEA users' extended permissions to see if there are other ways to gain privileged access to the system.</span></span>

<span data-ttu-id="b3a5c-206">Une pratique courante consiste à utiliser JEA pour une maintenance régulière quotidienne, et à avoir une solution de gestion des accès privilégiés juste-à-temps qui permet aux utilisateurs de devenir temporairement des administrateurs locaux en cas d’urgence.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-206">A common practice is to use JEA for regular day-to-day maintenance and have a just-in-time, privileged access management solution that allows users to temporarily become local admins in emergency situations.</span></span> <span data-ttu-id="b3a5c-207">Ainsi, les utilisateurs ne sont pas des administrateurs de manière permanente sur le système, mais ils peuvent obtenir ces droits si et seulement si un workflow documente leur utilisation de ces autorisations.</span><span class="sxs-lookup"><span data-stu-id="b3a5c-207">This helps ensure users aren't permanent admins on the system, but can get those rights if, and only when, they complete a workflow that documents their use of those permissions.</span></span>
---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Configuration de session JEA
description: Les configurations de session définissent qui peut utiliser le point de terminaison JEA et à quels rôles il a accès.
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501556"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="ea992-104">Configuration de session JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-104">JEA Session Configurations</span></span>

<span data-ttu-id="ea992-105">Un point de terminaison JEA est inscrit sur un système en créant et en inscrivant un fichier de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea992-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="ea992-106">Les configurations de session définissent qui peut utiliser le point de terminaison JEA et à quels rôles il a accès.</span><span class="sxs-lookup"><span data-stu-id="ea992-106">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="ea992-107">Elles définissent également les paramètres globaux qui s’appliquent à tous les utilisateurs de la session JEA.</span><span class="sxs-lookup"><span data-stu-id="ea992-107">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="ea992-108">Créer un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="ea992-108">Create a session configuration file</span></span>

<span data-ttu-id="ea992-109">Pour inscrire un point de terminaison JEA, vous devez spécifier la façon dont ce point de terminaison est configuré.</span><span class="sxs-lookup"><span data-stu-id="ea992-109">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="ea992-110">Il y a de nombreuses options à considérer.</span><span class="sxs-lookup"><span data-stu-id="ea992-110">There are many options to consider.</span></span> <span data-ttu-id="ea992-111">Les options les plus importantes sont :</span><span class="sxs-lookup"><span data-stu-id="ea992-111">The most important options are:</span></span>

- <span data-ttu-id="ea992-112">Qui a accès au point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-112">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="ea992-113">Quels rôles leur sont affectés</span><span class="sxs-lookup"><span data-stu-id="ea992-113">Which roles they be assigned</span></span>
- <span data-ttu-id="ea992-114">Quelle identité JEA utilise en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="ea992-114">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="ea992-115">Le nom du point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-115">The name of the JEA endpoint</span></span>

<span data-ttu-id="ea992-116">Ces options sont définies dans un fichier de données PowerShell avec une extension `.pssc`, désignée sous le nom de « fichier de configuration de session PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="ea992-116">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="ea992-117">Vous pouvez modifier le fichier de configuration de session avec n’importe quel éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="ea992-117">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="ea992-118">Exécutez la commande suivante pour créer un modèle de fichier de configuration vide.</span><span class="sxs-lookup"><span data-stu-id="ea992-118">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="ea992-119">Seules les options de configuration les plus courantes sont incluses dans le modèle de fichier par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea992-119">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="ea992-120">Utilisez le commutateur `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.</span><span class="sxs-lookup"><span data-stu-id="ea992-120">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="ea992-121">Le champ `-SessionType RestrictedRemoteServer` indique que la configuration de session est utilisée par JEA pour la gestion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ea992-121">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="ea992-122">Les sessions de ce type fonctionnent en **mode NoLanguage** et ont accès seulement aux commandes (et à leur alias) par défaut suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea992-122">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="ea992-123">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="ea992-123">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="ea992-124">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="ea992-124">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="ea992-125">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="ea992-125">Get-Command (gcm)</span></span>
- <span data-ttu-id="ea992-126">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ea992-126">Get-FormatData</span></span>
- <span data-ttu-id="ea992-127">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ea992-127">Get-Help</span></span>
- <span data-ttu-id="ea992-128">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="ea992-128">Measure-Object (measure)</span></span>
- <span data-ttu-id="ea992-129">Out-Default</span><span class="sxs-lookup"><span data-stu-id="ea992-129">Out-Default</span></span>
- <span data-ttu-id="ea992-130">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="ea992-130">Select-Object (select)</span></span>

<span data-ttu-id="ea992-131">Aucun fournisseur PowerShell ni aucun programme externe (exécutables, scripts, etc.) ne sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="ea992-131">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="ea992-132">Pour plus d’informations sur les modes de langage, consultez [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="ea992-132">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="ea992-133">Choisir l’identité JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-133">Choose the JEA identity</span></span>

<span data-ttu-id="ea992-134">En coulisses, JEA a besoin d’une identité (compte) pour exécuter les commandes d’un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ea992-134">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="ea992-135">Vous définissez quelle identité JEA utilise dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="ea992-135">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="ea992-136">Compte virtuel local</span><span class="sxs-lookup"><span data-stu-id="ea992-136">Local Virtual Account</span></span>

<span data-ttu-id="ea992-137">Les comptes virtuels locaux sont pratiques quand tous les rôles définis pour le point de terminaison JEA sont utilisés pour gérer la machine locale et qu’un compte d’administrateur local est suffisant pour exécuter les commandes avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea992-137">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="ea992-138">Les comptes virtuels sont des comptes temporaires propres à un utilisateur spécifique, qui ne durent que le temps de sa session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea992-138">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="ea992-139">Sur une station de travail ou un serveur membre, les comptes virtuels appartiennent au groupe **Administrateurs** de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ea992-139">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="ea992-140">Sur un contrôleur de domaine Active Directory, les comptes virtuels appartiennent au groupe **Administrateurs du domaine**.</span><span class="sxs-lookup"><span data-stu-id="ea992-140">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="ea992-141">Si les rôles définis par la configuration de session ne nécessitent pas de privilèges d’administration complets, vous pouvez spécifier les groupes de sécurité auxquels appartiendra le compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="ea992-141">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="ea992-142">Sur une station de travail ou un serveur membre, les groupes de sécurité spécifiés doivent être des groupes locaux, et non les groupes d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="ea992-142">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="ea992-143">Quand un ou plusieurs groupes de sécurité sont spécifiés, le compte virtuel n’est pas affecté au groupe Administrateurs local ou du domaine.</span><span class="sxs-lookup"><span data-stu-id="ea992-143">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="ea992-144">Le droit « Se connecter en tant que service » est accordé temporairement aux comptes virtuels dans la stratégie de sécurité du serveur local.</span><span class="sxs-lookup"><span data-stu-id="ea992-144">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="ea992-145">Si l’un des VirtualAccountGroups spécifiés dans la stratégie a déjà reçu ce droit, le compte virtuel en question ne sera plus ajouté et supprimé de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ea992-145">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="ea992-146">Cela peut être utile dans les scénarios tels que ceux où les révisions de la stratégie de sécurité de contrôleur de domaine sont étroitement auditées.</span><span class="sxs-lookup"><span data-stu-id="ea992-146">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="ea992-147">Cette fonctionnalité est disponible uniquement dans Windows Server 2016 avec le correctif cumulatif de novembre 2018 ou plus récent, et Windows Server 2019 avec le correctif cumulatif de janvier 2019 ou plus récent.</span><span class="sxs-lookup"><span data-stu-id="ea992-147">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="ea992-148">Compte de service géré de groupe</span><span class="sxs-lookup"><span data-stu-id="ea992-148">Group-managed service account</span></span>

<span data-ttu-id="ea992-149">Un compte de service géré de groupe (GMSA, Group-Managed Service Account) est l’identité appropriée à utiliser quand les utilisateurs JEA doivent accéder à des ressources réseau, comme des partages de fichiers et des services web.</span><span class="sxs-lookup"><span data-stu-id="ea992-149">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="ea992-150">Les comptes GMSA vous donnent une identité de domaine qui est utilisée pour s’authentifier auprès de ressources sur n’importe quelle machine du domaine.</span><span class="sxs-lookup"><span data-stu-id="ea992-150">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="ea992-151">Les droits fournis par un compte GMSA sont déterminés par les ressources auxquelles vous accédez.</span><span class="sxs-lookup"><span data-stu-id="ea992-151">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="ea992-152">Vous ne disposez pas de droits d’administrateur sur des machines ou des services, sauf si l’administrateur de la machine ou du service a accordé explicitement ces droits au compte GMSA.</span><span class="sxs-lookup"><span data-stu-id="ea992-152">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="ea992-153">Les comptes GMSA doivent être utilisés seulement quand c’est nécessaire :</span><span class="sxs-lookup"><span data-stu-id="ea992-153">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="ea992-154">Il est difficile de retracer les actions jusqu’à un utilisateur s’il utilise un compte GMSA.</span><span class="sxs-lookup"><span data-stu-id="ea992-154">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="ea992-155">Tous les utilisateurs partagent la même identité d’identification.</span><span class="sxs-lookup"><span data-stu-id="ea992-155">Every user shares the same run-as identity.</span></span> <span data-ttu-id="ea992-156">Vous devez examiner les journaux et les transcriptions de sessions PowerShell pour mettre en corrélation les utilisateurs individuels et leurs actions.</span><span class="sxs-lookup"><span data-stu-id="ea992-156">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="ea992-157">Le compte GMSA peut avoir accès à de nombreuses ressources réseau auxquelles l’utilisateur connecté n’a pas besoin d’accéder.</span><span class="sxs-lookup"><span data-stu-id="ea992-157">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="ea992-158">Essayez toujours de limiter les autorisations effectives dans une session JEA en suivant le principe des privilèges minimum.</span><span class="sxs-lookup"><span data-stu-id="ea992-158">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="ea992-159">Les comptes GMSA sont disponibles seulement sur les machines jointes à un domaine avec PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ea992-159">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ea992-160">Pour plus d’informations sur la sécurisation d’une session JEA, consultez l’article [Considérations sur la sécurité](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-160">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="ea992-161">Transcription de sessions</span><span class="sxs-lookup"><span data-stu-id="ea992-161">Session transcripts</span></span>

<span data-ttu-id="ea992-162">Il est recommandé de configurer un point de terminaison JEA de manière à enregistrer automatiquement les transcriptions des sessions des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ea992-162">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="ea992-163">Les transcriptions de sessions PowerShell contiennent des informations sur l’utilisateur connecté, l’identité « Exécuter en tant que » affectée et les commandes exécutées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea992-163">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="ea992-164">Elles peuvent être utiles à une équipe d’audit qui a besoin de comprendre qui a apporté une modification spécifique à un système.</span><span class="sxs-lookup"><span data-stu-id="ea992-164">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="ea992-165">Pour configurer la transcription automatique dans le fichier de configuration de session, fournissez le chemin d’accès du dossier dans lequel les transcriptions devront être stockées.</span><span class="sxs-lookup"><span data-stu-id="ea992-165">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="ea992-166">Les transcriptions sont écrites dans le dossier par le compte **Système local**, qui nécessite un accès en lecture et en écriture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="ea992-166">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="ea992-167">Les utilisateurs standard ne doivent pas avoir accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="ea992-167">Standard users should have no access to the folder.</span></span> <span data-ttu-id="ea992-168">Limitez le nombre d’administrateurs de sécurité qui ont un accès permettant d’auditer les transcriptions.</span><span class="sxs-lookup"><span data-stu-id="ea992-168">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="ea992-169">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="ea992-169">User drive</span></span>

<span data-ttu-id="ea992-170">Si vos utilisateurs connectés ont besoin de copier des fichiers vers ou depuis le point de terminaison JEA, vous pouvez activer le lecteur utilisateur dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="ea992-170">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="ea992-171">Le lecteur utilisateur est un **PSDrive** mappé à un dossier unique pour chaque utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="ea992-171">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="ea992-172">Ce dossier permet aux utilisateurs de copier des fichiers vers ou depuis le système, sans qu’ils puissent accéder à la totalité du système de fichiers ou exposer le fournisseur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ea992-172">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="ea992-173">Le contenu du lecteur utilisateur est persistant d’une session à l’autre de façon à gérer les situations dans lesquelles la connectivité réseau risque d’être interrompue.</span><span class="sxs-lookup"><span data-stu-id="ea992-173">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="ea992-174">Par défaut, le lecteur utilisateur vous permet de stocker 50 Mo de données maximum par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea992-174">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="ea992-175">Vous pouvez limiter la quantité de données qu’un utilisateur peut consommer avec le champ *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="ea992-175">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="ea992-176">Si vous ne voulez pas que les données du lecteur utilisateur soient persistantes, vous pouvez configurer une tâche planifiée sur le système qui nettoie automatiquement le dossier toutes les nuits.</span><span class="sxs-lookup"><span data-stu-id="ea992-176">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="ea992-177">Le lecteur utilisateur est disponible seulement dans PowerShell 5.1 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ea992-177">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ea992-178">Pour plus d’informations sur PSDrives, consultez [Gestion des disques PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="ea992-178">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="ea992-179">Définitions de rôles</span><span class="sxs-lookup"><span data-stu-id="ea992-179">Role definitions</span></span>

<span data-ttu-id="ea992-180">Les définitions de rôles d’un fichier de configuration de session définissent le mappage des **utilisateurs** aux **rôles**.</span><span class="sxs-lookup"><span data-stu-id="ea992-180">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="ea992-181">Chaque utilisateur ou groupe de ce champ reçoit l’autorisation d’accès au point de terminaison JEA lors de son inscription.</span><span class="sxs-lookup"><span data-stu-id="ea992-181">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="ea992-182">Chaque utilisateur ou groupe ne peut être inclus qu’une seule fois en tant que clé de la table de hachage, mais plusieurs rôles peuvent lui être affectés.</span><span class="sxs-lookup"><span data-stu-id="ea992-182">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="ea992-183">Le nom de la capacité du rôle doit être le même que celui du fichier des capacités des rôles, sans l’extension `.psrc`.</span><span class="sxs-lookup"><span data-stu-id="ea992-183">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="ea992-184">Si un utilisateur appartient à plusieurs groupes dans la définition des rôles, il a accès aux rôles de chacun de ces groupes.</span><span class="sxs-lookup"><span data-stu-id="ea992-184">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="ea992-185">Quand deux rôles accordent l’accès aux mêmes applets de commande, l’ensemble de paramètres le plus permissif est accordé à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea992-185">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="ea992-186">Quand vous spécifiez des utilisateurs ou des groupes locaux dans le champ des définitions de rôle, veillez à utiliser le nom de l’ordinateur, et non pas **localhost** ou des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="ea992-186">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="ea992-187">Pour vérifier le nom de l’ordinateur, inspectez la variable `$env:COMPUTERNAME`.</span><span class="sxs-lookup"><span data-stu-id="ea992-187">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="ea992-188">Ordre de recherche des capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="ea992-188">Role capability search order</span></span>

<span data-ttu-id="ea992-189">Comme le montre l’exemple ci-dessus, les capacités de rôle sont référencées par le nom de base du fichier des capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="ea992-189">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="ea992-190">Le nom de base d’un fichier est le nom de fichier sans l’extension.</span><span class="sxs-lookup"><span data-stu-id="ea992-190">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="ea992-191">Si plusieurs capacités de rôle sont disponibles sur le système avec le même nom, PowerShell utilise son ordre de recherche implicite pour sélectionner le fichier effectif de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="ea992-191">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="ea992-192">JEA ne donne **pas** accès à tous les fichiers de capacités de rôle portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ea992-192">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="ea992-193">JEA utilise la variable d’environnement `$env:PSModulePath` pour déterminer les chemins d’accès à analyser pour rechercher les fichiers de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="ea992-193">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="ea992-194">Dans chacun de ces chemins, JEA recherche les modules PowerShell valides contenant un sous-dossier « RoleCapabilities ».</span><span class="sxs-lookup"><span data-stu-id="ea992-194">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="ea992-195">Tout comme pour l’importation de modules, JEA préfère les capacités de rôle qui sont livrées avec Windows aux capacités de rôle personnalisées portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ea992-195">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="ea992-196">Pour tous les autres conflits de noms, la priorité est déterminée par l’ordre dans lequel Windows énumère les fichiers dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="ea992-196">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="ea992-197">Il n’est pas garanti que l’ordre soit alphabétique.</span><span class="sxs-lookup"><span data-stu-id="ea992-197">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="ea992-198">Le premier fichier de capacités de rôle trouvé qui correspond au nom spécifié est utilisé pour l’utilisateur qui se connecte.</span><span class="sxs-lookup"><span data-stu-id="ea992-198">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="ea992-199">Comme la recherche des capacités de rôle n’est pas déterministe, il est **fortement recommandé** d’utiliser des noms de fichier uniques pour les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="ea992-199">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="ea992-200">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="ea992-200">Conditional access rules</span></span>

<span data-ttu-id="ea992-201">Tous les utilisateurs et groupes inclus dans le champ **RoleDefinitions** reçoivent automatiquement l’accès aux points de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="ea992-201">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="ea992-202">Les règles d’accès conditionnel vous permettent d’affiner cet accès et d’exiger que les utilisateurs appartiennent à d’autres groupes de sécurité qui n’affectent pas les rôles qui leur sont attribués.</span><span class="sxs-lookup"><span data-stu-id="ea992-202">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="ea992-203">C’est utile quand vous voulez intégrer une solution de gestion des accès privilégiés en « juste à temps », l’authentification par carte à puce ou une autre solution d’authentification multifacteur avec JEA.</span><span class="sxs-lookup"><span data-stu-id="ea992-203">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="ea992-204">Les règles d’accès conditionnel sont définies dans le champ RequiredGroups d’un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="ea992-204">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="ea992-205">Vous pouvez y spécifier une table de hachage (éventuellement imbriquée) qui utilise des clés « And » et « Or » pour créer vos règles.</span><span class="sxs-lookup"><span data-stu-id="ea992-205">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="ea992-206">Voici quelques exemples d’utilisation de ce champ :</span><span class="sxs-lookup"><span data-stu-id="ea992-206">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="ea992-207">Les règles d’accès conditionnel sont disponibles seulement dans PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ea992-207">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="ea992-208">Autres propriétés</span><span class="sxs-lookup"><span data-stu-id="ea992-208">Other properties</span></span>

<span data-ttu-id="ea992-209">Les fichiers de configuration de session peuvent également faire les mêmes choses qu’un fichier de capacités de rôle, sauf donner accès aux utilisateurs connectés à des commandes différentes.</span><span class="sxs-lookup"><span data-stu-id="ea992-209">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="ea992-210">Si vous souhaitez autoriser tous les utilisateurs à accéder à des applets de commande, fonctions ou fournisseurs spécifiques, vous pouvez le faire directement dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="ea992-210">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="ea992-211">Pour obtenir la liste complète des propriétés prises en charge dans le fichier de configuration de session, exécutez `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="ea992-211">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="ea992-212">Tester un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="ea992-212">Testing a session configuration file</span></span>

<span data-ttu-id="ea992-213">Vous pouvez tester une configuration de session avec l’applet de commande [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="ea992-213">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="ea992-214">Il est recommandé de tester votre fichier de configuration de session si vous avez modifié manuellement le fichier `.pssc`.</span><span class="sxs-lookup"><span data-stu-id="ea992-214">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="ea992-215">Les tests garantissent que la syntaxe est correcte.</span><span class="sxs-lookup"><span data-stu-id="ea992-215">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="ea992-216">Si un fichier de configuration de session échoue à ce test, il ne peut pas être inscrit sur le système.</span><span class="sxs-lookup"><span data-stu-id="ea992-216">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="ea992-217">Exemple de fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="ea992-217">Sample session configuration file</span></span>

<span data-ttu-id="ea992-218">L’exemple suivant montre comment créer et valider une configuration de session pour JEA.</span><span class="sxs-lookup"><span data-stu-id="ea992-218">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="ea992-219">Les définitions de rôles sont créées et stockées dans la variable `$roles` par souci pratique et de lisibilité.</span><span class="sxs-lookup"><span data-stu-id="ea992-219">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="ea992-220">Il n’y a pas d’obligation à procéder ainsi.</span><span class="sxs-lookup"><span data-stu-id="ea992-220">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="ea992-221">Mettre à jour les fichiers de configuration de session</span><span class="sxs-lookup"><span data-stu-id="ea992-221">Updating session configuration files</span></span>

<span data-ttu-id="ea992-222">Pour changer les propriétés d’une configuration de session JEA, notamment la mise en correspondance des utilisateurs aux rôles, vous devez effectuer une [désinscription](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="ea992-222">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="ea992-223">Ensuite, vous devez [réinscrire](register-jea.md) la configuration de session JEA avec le fichier de configuration de session mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ea992-223">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea992-224">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ea992-224">Next steps</span></span>

- [<span data-ttu-id="ea992-225">Enregistrer une configuration JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-225">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="ea992-226">Créer des rôles JEA</span><span class="sxs-lookup"><span data-stu-id="ea992-226">Author JEA roles</span></span>](role-capabilities.md)

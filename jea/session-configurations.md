---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Configuration de session JEA
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056586"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="c471b-103">Configuration de session JEA</span><span class="sxs-lookup"><span data-stu-id="c471b-103">JEA Session Configurations</span></span>

> <span data-ttu-id="c471b-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c471b-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c471b-105">Un point de terminaison JEA est enregistré sur un système en créant et en enregistrant un fichier de configuration de session PowerShell de manière spécifique.</span><span class="sxs-lookup"><span data-stu-id="c471b-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="c471b-106">Les configurations de session déterminent *qui* peut utiliser le point de terminaison JEA, et à quel(s) rôle(s) ils ont accès.</span><span class="sxs-lookup"><span data-stu-id="c471b-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="c471b-107">Elles définissent également les paramètres globaux qui s’appliquent aux utilisateurs des rôles de la session JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="c471b-108">Cette rubrique décrit comment créer un fichier de configuration de session PowerShell et enregistrer un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="c471b-109">Créer un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="c471b-109">Create a session configuration file</span></span>

<span data-ttu-id="c471b-110">Pour enregistrer un point de terminaison JEA, vous devez spécifier la façon dont ce point de terminaison doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="c471b-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="c471b-111">De nombreuses options sont à prendre en compte ici, voici les plus importantes : qui doit avoir accès au point de terminaison JEA, quels rôles leur seront affectés, quelles identités JEA utilisera en coulisses et quel sera le nom du point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="c471b-112">Elles sont toutes définies dans un fichier de configuration de session PowerShell, qui est un fichier de données PowerShell se terminant par une extension .pssc.</span><span class="sxs-lookup"><span data-stu-id="c471b-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="c471b-113">Pour créer un squelette de fichier de configuration de session pour les points de terminaison JEA, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c471b-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="c471b-114">Seules les options de configuration les plus courantes sont incluses dans le squelette de fichier par défaut.</span><span class="sxs-lookup"><span data-stu-id="c471b-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="c471b-115">Utilisez le commutateur `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.</span><span class="sxs-lookup"><span data-stu-id="c471b-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="c471b-116">Vous pouvez ouvrir le fichier de configuration de session dans l’éditeur de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="c471b-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="c471b-117">Le champ `-SessionType RestrictedRemoteServer` indique que la configuration de session sera utilisée par JEA pour une gestion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="c471b-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="c471b-118">Les sessions configurées de cette façon fonctionnent en [mode NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) et seules les huit commandes par défaut suivantes (et les alias) sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="c471b-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="c471b-119">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="c471b-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="c471b-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="c471b-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="c471b-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="c471b-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="c471b-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="c471b-122">Get-FormatData</span></span>
- <span data-ttu-id="c471b-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="c471b-123">Get-Help</span></span>
- <span data-ttu-id="c471b-124">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="c471b-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="c471b-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="c471b-125">Out-Default</span></span>
- <span data-ttu-id="c471b-126">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="c471b-126">Select-Object (select)</span></span>

<span data-ttu-id="c471b-127">Aucun fournisseur PowerShell n’est disponible, ni aucun programme externe (exécutables, scripts, etc.).</span><span class="sxs-lookup"><span data-stu-id="c471b-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="c471b-128">Il vous faudra configurer d’autres champs pour la session JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="c471b-129">Ils sont décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="c471b-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="c471b-130">Choisir l’identité JEA</span><span class="sxs-lookup"><span data-stu-id="c471b-130">Choose the JEA identity</span></span>

<span data-ttu-id="c471b-131">En coulisses, JEA a besoin d’une identité (compte) pour exécuter les commandes d’un utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="c471b-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="c471b-132">Vous choisissez quelle identité JEA utilisera dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c471b-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="c471b-133">Compte virtuel local</span><span class="sxs-lookup"><span data-stu-id="c471b-133">Local Virtual Account</span></span>

<span data-ttu-id="c471b-134">Si les rôles pris en charge par ce point de terminaison JEA sont tous utilisés pour gérer l’ordinateur local, et qu’un compte Administrateur local est suffisant pour exécuter les commandes, vous devez configurer JEA afin d’utiliser un compte virtuel local.</span><span class="sxs-lookup"><span data-stu-id="c471b-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands successfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="c471b-135">Les comptes virtuels sont des comptes temporaires propres à un utilisateur spécifique, qui ne durent que le temps de sa session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c471b-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="c471b-136">Sur une station de travail ou un serveur membre, les comptes virtuels appartiennent au groupe **Administrateurs** de l’ordinateur local, et ont accès à la plupart des ressources système.</span><span class="sxs-lookup"><span data-stu-id="c471b-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="c471b-137">Sur un contrôleur de domaine Active Directory, les comptes virtuels appartiennent au groupe **Administrateurs du domaine**.</span><span class="sxs-lookup"><span data-stu-id="c471b-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="c471b-138">Si les rôles pris en charge par la configuration de session ne requièrent pas ces privilèges étendus, vous pouvez éventuellement spécifier les groupes de sécurité auxquels appartiendra le compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="c471b-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="c471b-139">Sur une station de travail ou un serveur membre, les groupes de sécurité spécifiés doivent être des groupes locaux, et non les groupes d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="c471b-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="c471b-140">Lorsqu’un ou plusieurs groupes de sécurité sont spécifiés, le compte virtuel n’appartient plus au groupe Administrateurs local ou du domaine.</span><span class="sxs-lookup"><span data-stu-id="c471b-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="c471b-141">Le droit « Se connecter en tant que service » est accordé temporairement aux comptes virtuels dans la stratégie de sécurité du serveur local.</span><span class="sxs-lookup"><span data-stu-id="c471b-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="c471b-142">Si l’un des VirtualAccountGroups spécifiés dans la stratégie a déjà reçu ce droit, le compte virtuel en question ne sera plus ajouté et supprimé de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="c471b-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="c471b-143">Cela peut être utile dans les scénarios tels que ceux où les révisions de la stratégie de sécurité de contrôleur de domaine sont étroitement auditées.</span><span class="sxs-lookup"><span data-stu-id="c471b-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="c471b-144">Cette fonctionnalité est disponible uniquement dans Windows Server 2016 avec le correctif cumulatif de novembre 2018 ou plus récent, et Windows Server 2019 avec le correctif cumulatif de janvier 2019 ou plus récent.</span><span class="sxs-lookup"><span data-stu-id="c471b-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="c471b-145">Compte de service administré de groupe</span><span class="sxs-lookup"><span data-stu-id="c471b-145">Group Managed Service Account</span></span>


<span data-ttu-id="c471b-146">Pour les scénarios exigeant que l’utilisateur JEA accède à des ressources réseau telles que d’autres ordinateurs ou services web, un compte de service géré par un groupe (gMSA) est une identité plus appropriée.</span><span class="sxs-lookup"><span data-stu-id="c471b-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="c471b-147">Les comptes gMSA donnent une identité de domaine utilisable pour s’authentifier auprès des ressources de n’importe quel ordinateur du domaine.</span><span class="sxs-lookup"><span data-stu-id="c471b-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="c471b-148">Les droits que le compte gMSA vous donne sont déterminés par les ressources auxquelles vous accédez.</span><span class="sxs-lookup"><span data-stu-id="c471b-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="c471b-149">Vous ne disposez pas automatiquement de droits d’administrateur sur les ordinateurs ou les services, sauf si l’administrateur du service/de l’ordinateur a accordé explicitement les privilèges Administrateur au compte gMSA.</span><span class="sxs-lookup"><span data-stu-id="c471b-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="c471b-150">Les comptes gMSA ne doivent être utilisés que lorsque l’accès aux ressources réseau est requis, pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="c471b-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="c471b-151">Il est plus difficile de retracer les actions d’un utilisateur avec un compte gMSA, étant donné que tous les utilisateurs partagent la même identité « Exécuter en tant que ».</span><span class="sxs-lookup"><span data-stu-id="c471b-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="c471b-152">Vous devrez consulter les journaux et les transcriptions de sessions PowerShell pour mettre en corrélation les utilisateurs et leurs actions.</span><span class="sxs-lookup"><span data-stu-id="c471b-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="c471b-153">Le compte gMSA peut avoir accès à de nombreuses ressources réseau auxquelles l’utilisateur connecté n’a pas accès.</span><span class="sxs-lookup"><span data-stu-id="c471b-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="c471b-154">Essayez toujours de limiter les autorisations effectives dans une session JEA en suivant le principe des privilèges minimum.</span><span class="sxs-lookup"><span data-stu-id="c471b-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="c471b-155">Les comptes de service gérés par un groupe sont disponibles uniquement dans Windows PowerShell 5.1 et les versions plus récentes, et sur les ordinateurs joints à un domaine.</span><span class="sxs-lookup"><span data-stu-id="c471b-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>

#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="c471b-156">Informations complémentaires sur les utilisateurs « Exécuter en tant que »</span><span class="sxs-lookup"><span data-stu-id="c471b-156">More information about run as users</span></span>

<span data-ttu-id="c471b-157">Vous trouverez plus d’informations sur les identités « Exécuter en tant que » et sur leur rôle dans la sécurité d’une session JEA dans l’article [considérations en matière de sécurité](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="c471b-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="c471b-158">Transcription de sessions</span><span class="sxs-lookup"><span data-stu-id="c471b-158">Session transcripts</span></span>

<span data-ttu-id="c471b-159">Il est recommandé de configurer un fichier de configuration de session JEA de manière à enregistrer automatiquement les transcriptions des sessions des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c471b-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="c471b-160">Les transcriptions de sessions PowerShell contiennent des informations sur l’utilisateur connecté, l’identité « Exécuter en tant que » affectée et les commandes exécutées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c471b-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="c471b-161">Elles peuvent être utiles à une équipe d’audit qui a besoin de comprendre qui a apporté une modification en particulier à un système.</span><span class="sxs-lookup"><span data-stu-id="c471b-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="c471b-162">Pour configurer la transcription automatique dans le fichier de configuration de session, fournissez le chemin d’accès du dossier dans lequel les transcriptions devront être stockées.</span><span class="sxs-lookup"><span data-stu-id="c471b-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="c471b-163">Le dossier spécifié doit être configuré de façon à empêcher les utilisateurs de modifier ou de supprimer les données qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="c471b-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="c471b-164">Les transcriptions sont écrites dans le dossier par le compte système local, qui a besoin d’un accès en lecture et en écriture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="c471b-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="c471b-165">Les utilisateurs standard ne doivent avoir aucun accès au dossier, et un ensemble limité d’administrateurs de sécurité doit y avoir accès pour vérifier les transcriptions.</span><span class="sxs-lookup"><span data-stu-id="c471b-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="c471b-166">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="c471b-166">User drive</span></span>

<span data-ttu-id="c471b-167">Si vos utilisateurs connectés ont besoin de copier des fichiers vers/à partir du point de terminaison JEA afin d’exécuter une commande, vous pouvez activer le lecteur utilisateur dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c471b-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="c471b-168">Le lecteur utilisateur est un [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) mappé à un dossier unique pour chaque utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="c471b-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="c471b-169">Ce dossier leur sert d’espace pour copier des fichiers vers/à partir du système, sans qu’ils puissent accéder à la totalité du système de fichiers ou exposer le fournisseur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c471b-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="c471b-170">Le contenu du lecteur utilisateur est persistant d’une session à l’autre de façon à gérer les situations dans lesquelles la connectivité réseau risque d’être interrompue.</span><span class="sxs-lookup"><span data-stu-id="c471b-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="c471b-171">Par défaut, le lecteur utilisateur vous permet de stocker 50 Mo de données maximum par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c471b-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="c471b-172">Vous pouvez limiter la quantité de données qu’un utilisateur peut consommer avec le champ *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="c471b-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="c471b-173">Si vous ne souhaitez pas que les données du lecteur utilisateur soient persistantes, vous pouvez configurer une tâche planifiée sur le système qui nettoie automatiquement le dossier toutes les nuits.</span><span class="sxs-lookup"><span data-stu-id="c471b-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="c471b-174">Le lecteur utilisateur est disponible uniquement dans Windows PowerShell 5.1 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c471b-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="c471b-175">Définitions de rôles</span><span class="sxs-lookup"><span data-stu-id="c471b-175">Role definitions</span></span>

<span data-ttu-id="c471b-176">Les définitions de rôles d’un fichier de configuration de session définissent le mappage des *utilisateurs* aux *rôles*.</span><span class="sxs-lookup"><span data-stu-id="c471b-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="c471b-177">Chaque utilisateur ou groupe de ce champ reçoit automatiquement l’autorisation d’accès au point de terminaison JEA lors de son enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c471b-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="c471b-178">Chaque utilisateur ou groupe ne peut être inclus qu’une seule fois en tant que clé de la table de hachage, mais plusieurs rôles peuvent lui être affectés.</span><span class="sxs-lookup"><span data-stu-id="c471b-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="c471b-179">Le nom de la capacité de rôle doit être le nom du fichier de capacités de rôle, sans l’extension .psrc.</span><span class="sxs-lookup"><span data-stu-id="c471b-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="c471b-180">Si un utilisateur appartient à plusieurs groupes de la définition des rôles, il a accès aux rôles de chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="c471b-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="c471b-181">Si deux rôles accordent l’accès aux mêmes applets de commande, l’ensemble de paramètres le plus permissif est accordé à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c471b-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="c471b-182">Quand vous spécifiez des utilisateurs ou des groupes locaux dans le champ des définitions de rôle, veillez à utiliser le nom de l’ordinateur (et non *localhost* ou  *.*) avant la barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="c471b-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="c471b-183">Pour vérifier le nom de l’ordinateur, inspectez la variable `$env:computername`.</span><span class="sxs-lookup"><span data-stu-id="c471b-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="c471b-184">Ordre de recherche des capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="c471b-184">Role capability search order</span></span>

<span data-ttu-id="c471b-185">Comme l’indique l’exemple ci-dessus, les capacités de rôle sont référencées par le nom plat (nom du fichier sans l’extension) du fichier de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="c471b-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="c471b-186">Si plusieurs capacités de rôle sont disponibles sur le système avec le même nom plat, PowerShell utilise son ordre de recherche implicite pour sélectionner le fichier effectif de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="c471b-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="c471b-187">Il ne donnera **pas** accès à tous les fichiers de capacités de rôle portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c471b-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="c471b-188">JEA utilise la variable d’environnement `$env:PSModulePath` pour déterminer les chemins d’accès à analyser pour rechercher les fichiers de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="c471b-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="c471b-189">Dans chacun de ces chemins d’accès, JEA recherche les modules PowerShell valides contenant un sous-dossier « RoleCapabilities ».</span><span class="sxs-lookup"><span data-stu-id="c471b-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="c471b-190">Tout comme pour l’importation de modules, JEA préfère les capacités de rôle qui sont livrées avec Windows aux capacités de rôle personnalisées portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c471b-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="c471b-191">Pour tous les autres conflits d’affectation de noms, la priorité est déterminée par l’ordre dans lequel Windows énumère les fichiers dans le répertoire (pas forcément par ordre alphabétique).</span><span class="sxs-lookup"><span data-stu-id="c471b-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="c471b-192">Le premier fichier de capacités de rôle trouvé qui correspond au nom requis sera utilisé pour l’utilisateur qui se connecte.</span><span class="sxs-lookup"><span data-stu-id="c471b-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="c471b-193">Étant donné que l’ordre de recherche des capacités de rôle n’est pas déterministe lorsque deux ou plusieurs capacités de rôle partagent le même nom, il est **fortement recommandé** de vous assurer que les capacités de rôle ont des noms uniques sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c471b-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="c471b-194">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="c471b-194">Conditional access rules</span></span>

<span data-ttu-id="c471b-195">Tous les utilisateurs et groupes inclus dans le champ RoleDefinitions reçoivent automatiquement l’accès aux points de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="c471b-196">Les règles d’accès conditionnel permettent d’affiner cet accès et exigent que les utilisateurs appartiennent à d’autres groupes de sécurité qui n’affectent pas les rôles qui leur sont affectés.</span><span class="sxs-lookup"><span data-stu-id="c471b-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="c471b-197">Cela peut être utile si vous souhaitez intégrer une solution de gestion des accès privilégiés en « juste à temps », l’authentification par carte à puce ou une autre solution d’authentification multifacteur avec JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="c471b-198">Les règles d’accès conditionnel sont définies dans le champ RequiredGroups d’un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c471b-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="c471b-199">Vous pouvez y spécifier une table de hachage (éventuellement imbriquée) qui utilise des clés « And » et « Or » pour créer vos règles.</span><span class="sxs-lookup"><span data-stu-id="c471b-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="c471b-200">Voici quelques exemples montrant comment tirer parti de ce champ :</span><span class="sxs-lookup"><span data-stu-id="c471b-200">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="c471b-201">Les règles d’accès conditionnel sont disponibles uniquement dans Windows PowerShell 5.1 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c471b-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="c471b-202">Autres propriétés</span><span class="sxs-lookup"><span data-stu-id="c471b-202">Other properties</span></span>

<span data-ttu-id="c471b-203">Les fichiers de configuration de session peuvent également faire les mêmes choses qu’un fichier de capacités de rôle, sauf donner accès aux utilisateurs connectés à des commandes différentes.</span><span class="sxs-lookup"><span data-stu-id="c471b-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="c471b-204">Si vous souhaitez autoriser tous les utilisateurs à accéder à des applets de commande, fonctions ou fournisseurs spécifiques, vous pouvez le faire directement dans le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c471b-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="c471b-205">Pour obtenir la liste complète des propriétés prises en charge dans le fichier de configuration de session, exécutez `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="c471b-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="c471b-206">Tester un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="c471b-206">Testing a session configuration file</span></span>

<span data-ttu-id="c471b-207">Vous pouvez tester une configuration de session avec l’applet de commande [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="c471b-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="c471b-208">Il est fortement recommandé de tester votre fichier de configuration de session, si vous avez modifié le fichier pssc manuellement à l’aide d’un éditeur de texte, pour vérifier que la syntaxe est correcte.</span><span class="sxs-lookup"><span data-stu-id="c471b-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="c471b-209">Si le fichier de configuration de session ne passe pas ce test, son enregistrement sur le système ne réussira pas.</span><span class="sxs-lookup"><span data-stu-id="c471b-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="c471b-210">Exemple de fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="c471b-210">Sample session configuration file</span></span>

<span data-ttu-id="c471b-211">Voici un exemple complet montrant comment créer et valider une configuration de session pour JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="c471b-212">Notez que les définitions de rôles sont créées et stockées dans la variable `$roles` par souci de commodité et de lisibilité.</span><span class="sxs-lookup"><span data-stu-id="c471b-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="c471b-213">Il n’y a pas d’obligation à s’y conformer.</span><span class="sxs-lookup"><span data-stu-id="c471b-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="c471b-214">Mettre à jour les fichiers de configuration de session</span><span class="sxs-lookup"><span data-stu-id="c471b-214">Updating session configuration files</span></span>

<span data-ttu-id="c471b-215">Si vous avez besoin de modifier les propriétés d’une configuration de session JEA, y compris le mappage des utilisateurs aux rôles, vous devez [annuler](register-jea.md#unregistering-jea-configurations) et [renouveler l’enregistrement](register-jea.md) de la configuration de session JEA.</span><span class="sxs-lookup"><span data-stu-id="c471b-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="c471b-216">Lorsque vous enregistrez de nouveau la configuration de session JEA, utilisez un fichier de configuration de session PowerShell mis à jour qui inclut les modifications désirées.</span><span class="sxs-lookup"><span data-stu-id="c471b-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c471b-217">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c471b-217">Next steps</span></span>

- [<span data-ttu-id="c471b-218">Enregistrer une configuration JEA</span><span class="sxs-lookup"><span data-stu-id="c471b-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="c471b-219">Créer des rôles JEA</span><span class="sxs-lookup"><span data-stu-id="c471b-219">Author JEA roles</span></span>](role-capabilities.md)

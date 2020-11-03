---
description: Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 3332adb76c76fa644d23060abe2af43bd45a15a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208042"
---
# <a name="about-execution-policies"></a><span data-ttu-id="17a58-104">À propos des stratégies d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="17a58-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="17a58-105">Short Description</span></span>

<span data-ttu-id="17a58-106">Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.</span><span class="sxs-lookup"><span data-stu-id="17a58-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="17a58-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="17a58-107">Long Description</span></span>

<span data-ttu-id="17a58-108">La stratégie d’exécution de PowerShell est une fonctionnalité de sécurité qui contrôle les conditions dans lesquelles PowerShell charge les fichiers de configuration et exécute des scripts.</span><span class="sxs-lookup"><span data-stu-id="17a58-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="17a58-109">Cette fonctionnalité permet d’éviter l’exécution de scripts malveillants.</span><span class="sxs-lookup"><span data-stu-id="17a58-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="17a58-110">Sur un ordinateur Windows, vous pouvez définir une stratégie d’exécution pour l’ordinateur local, pour l’utilisateur actuel ou pour une session particulière.</span><span class="sxs-lookup"><span data-stu-id="17a58-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="17a58-111">Vous pouvez également utiliser un paramètre de stratégie de groupe pour définir des stratégies d’exécution pour les ordinateurs et les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="17a58-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="17a58-112">Les stratégies d’exécution de l’ordinateur local et de l’utilisateur actuel sont stockées dans le registre.</span><span class="sxs-lookup"><span data-stu-id="17a58-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="17a58-113">Vous n’avez pas besoin de définir des stratégies d’exécution dans votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17a58-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="17a58-114">La stratégie d’exécution pour une session particulière est stockée uniquement en mémoire et est perdue lorsque la session est fermée.</span><span class="sxs-lookup"><span data-stu-id="17a58-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="17a58-115">La stratégie d’exécution n’est pas un système de sécurité qui restreint les actions des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="17a58-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="17a58-116">Par exemple, les utilisateurs peuvent facilement contourner une stratégie en tapant le contenu du script sur la ligne de commande lorsqu’ils ne peuvent pas exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="17a58-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="17a58-117">Au lieu de cela, la stratégie d’exécution aide les utilisateurs à définir des règles de base et les empêche de les violer involontairement.</span><span class="sxs-lookup"><span data-stu-id="17a58-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="17a58-118">Stratégies d’exécution de PowerShell</span><span class="sxs-lookup"><span data-stu-id="17a58-118">PowerShell execution policies</span></span>

<span data-ttu-id="17a58-119">Les stratégies d’exécution de PowerShell sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="17a58-119">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="17a58-120">AllSigned</span><span class="sxs-lookup"><span data-stu-id="17a58-120">AllSigned</span></span>

- <span data-ttu-id="17a58-121">Les scripts peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="17a58-121">Scripts can run.</span></span>
- <span data-ttu-id="17a58-122">nécessite que tous les scripts et fichiers de configuration soient signés par un éditeur approuvé, y compris les scripts que vous écrivez sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="17a58-122">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="17a58-123">Vous invite à confirmer l’exécution des scripts des serveurs de publication que vous n’avez pas encore classés comme approuvés ou non approuvés.</span><span class="sxs-lookup"><span data-stu-id="17a58-123">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="17a58-124">Risques liés à l’exécution de scripts signés, mais malveillants.</span><span class="sxs-lookup"><span data-stu-id="17a58-124">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="17a58-125">Contournement</span><span class="sxs-lookup"><span data-stu-id="17a58-125">Bypass</span></span>

- <span data-ttu-id="17a58-126">rien n'est bloqué, et aucun avertissement, ni aucune invite ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="17a58-126">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="17a58-127">Cette stratégie d’exécution est conçue pour les configurations dans lesquelles un script PowerShell est intégré à une application plus volumineuse ou pour les configurations dans lesquelles PowerShell est la base d’un programme qui possède son propre modèle de sécurité.</span><span class="sxs-lookup"><span data-stu-id="17a58-127">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="17a58-128">Default</span><span class="sxs-lookup"><span data-stu-id="17a58-128">Default</span></span>

- <span data-ttu-id="17a58-129">Définit la stratégie d’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="17a58-129">Sets the default execution policy.</span></span>
- <span data-ttu-id="17a58-130">**Limité** pour les clients Windows.</span><span class="sxs-lookup"><span data-stu-id="17a58-130">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="17a58-131">**RemoteSigned** pour les serveurs Windows.</span><span class="sxs-lookup"><span data-stu-id="17a58-131">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="17a58-132">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="17a58-132">RemoteSigned</span></span>

- <span data-ttu-id="17a58-133">Stratégie d’exécution par défaut pour les ordinateurs Windows Server.</span><span class="sxs-lookup"><span data-stu-id="17a58-133">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="17a58-134">Les scripts peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="17a58-134">Scripts can run.</span></span>
- <span data-ttu-id="17a58-135">Requiert une signature numérique d’un éditeur approuvé sur les scripts et les fichiers de configuration téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.</span><span class="sxs-lookup"><span data-stu-id="17a58-135">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="17a58-136">Ne requiert pas de signatures numériques sur les scripts écrits sur l’ordinateur local et non téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="17a58-136">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="17a58-137">Exécute les scripts qui sont téléchargés à partir d’Internet et non signés, si les scripts sont débloqués, par exemple à l’aide de l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="17a58-137">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="17a58-138">Risques liés à l’exécution de scripts non signés provenant de sources autres que l’Internet et scripts signés pouvant être malveillants.</span><span class="sxs-lookup"><span data-stu-id="17a58-138">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="17a58-139">Limitées</span><span class="sxs-lookup"><span data-stu-id="17a58-139">Restricted</span></span>

- <span data-ttu-id="17a58-140">Stratégie d’exécution par défaut pour les ordinateurs clients Windows.</span><span class="sxs-lookup"><span data-stu-id="17a58-140">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="17a58-141">Autorise des commandes individuelles, mais n’autorise pas les scripts.</span><span class="sxs-lookup"><span data-stu-id="17a58-141">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="17a58-142">Empêche l’exécution de tous les fichiers de script, y compris les fichiers de mise en forme et de configuration ( `.ps1xml` ), les fichiers de script de module ( `.psm1` ) et les profils PowerShell ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="17a58-142">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="17a58-143">Indéfini</span><span class="sxs-lookup"><span data-stu-id="17a58-143">Undefined</span></span>

- <span data-ttu-id="17a58-144">Aucune stratégie d’exécution n’est définie dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="17a58-144">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="17a58-145">Si la stratégie d’exécution dans toutes les portées n’est **pas définie** , la stratégie d’exécution effective est **limitée** pour les clients Windows et **RemoteSigned** pour Windows Server.</span><span class="sxs-lookup"><span data-stu-id="17a58-145">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="17a58-146">Non restreint</span><span class="sxs-lookup"><span data-stu-id="17a58-146">Unrestricted</span></span>

- <span data-ttu-id="17a58-147">Les scripts non signés peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="17a58-147">Unsigned scripts can run.</span></span> <span data-ttu-id="17a58-148">L’exécution de scripts malveillants présente un risque.</span><span class="sxs-lookup"><span data-stu-id="17a58-148">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="17a58-149">Avertit l’utilisateur avant d’exécuter des scripts et des fichiers de configuration qui ne proviennent pas de la zone Intranet local.</span><span class="sxs-lookup"><span data-stu-id="17a58-149">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="17a58-150">Sur les systèmes qui ne distinguent pas les chemins d’accès UNC (Universal Naming Convention) des chemins Internet, les scripts identifiés par un chemin d’accès UNC peuvent ne pas être autorisés à s’exécuter avec la stratégie d’exécution **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="17a58-150">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="17a58-151">Étendue de la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-151">Execution policy scope</span></span>

<span data-ttu-id="17a58-152">Vous pouvez définir une stratégie d’exécution qui est effective uniquement dans une étendue particulière.</span><span class="sxs-lookup"><span data-stu-id="17a58-152">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="17a58-153">Les valeurs valides pour **scope** sont **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** et **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="17a58-153">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine** .</span></span> <span data-ttu-id="17a58-154">**LocalMachine** est la valeur par défaut lors de la définition d’une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="17a58-154">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="17a58-155">Les valeurs d' **étendue** sont répertoriées par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="17a58-155">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="17a58-156">La stratégie qui est prioritaire est effective dans la session active, même si une stratégie plus restrictive a été définie à un niveau de priorité inférieur.</span><span class="sxs-lookup"><span data-stu-id="17a58-156">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="17a58-157">Pour plus d’informations, consultez [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span><span class="sxs-lookup"><span data-stu-id="17a58-157">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="17a58-158">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-158">MachinePolicy</span></span>

<span data-ttu-id="17a58-159">Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17a58-159">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="17a58-160">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-160">UserPolicy</span></span>

<span data-ttu-id="17a58-161">Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17a58-161">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="17a58-162">Process</span><span class="sxs-lookup"><span data-stu-id="17a58-162">Process</span></span>

<span data-ttu-id="17a58-163">L’étendue du **processus** affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="17a58-163">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="17a58-164">La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` , plutôt que dans le registre.</span><span class="sxs-lookup"><span data-stu-id="17a58-164">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="17a58-165">Une fois la session PowerShell fermée, la variable et la valeur sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="17a58-165">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="17a58-166">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="17a58-166">CurrentUser</span></span>

<span data-ttu-id="17a58-167">la stratégie d'exécution affecte uniquement l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="17a58-167">The execution policy affects only the current user.</span></span> <span data-ttu-id="17a58-168">Elle est stockée dans la sous-clé de Registre **HKEY_CURRENT_USER** .</span><span class="sxs-lookup"><span data-stu-id="17a58-168">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="17a58-169">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="17a58-169">LocalMachine</span></span>

<span data-ttu-id="17a58-170">La stratégie d’exécution affecte tous les utilisateurs sur l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="17a58-170">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="17a58-171">Elle est stockée dans la sous-clé de Registre **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="17a58-171">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="17a58-172">Gestion de la stratégie d’exécution avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="17a58-172">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="17a58-173">Pour obtenir la stratégie d’exécution effective pour la session PowerShell actuelle, utilisez l’applet de commande `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="17a58-173">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="17a58-174">La commande suivante obtient la stratégie d’exécution effective :</span><span class="sxs-lookup"><span data-stu-id="17a58-174">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="17a58-175">Pour obtenir toutes les stratégies d’exécution qui affectent la session active et les afficher dans l’ordre de priorité :</span><span class="sxs-lookup"><span data-stu-id="17a58-175">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="17a58-176">Le résultat ressemble à l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="17a58-176">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="17a58-177">Dans ce cas, la stratégie d’exécution effective est **RemoteSigned** car la stratégie d’exécution de l’utilisateur actuel est prioritaire sur la stratégie d’exécution définie pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="17a58-177">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="17a58-178">Pour obtenir la stratégie d’exécution définie pour une étendue particulière, utilisez le paramètre **scope** de `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="17a58-178">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="17a58-179">Par exemple, la commande suivante obtient la stratégie d’exécution pour l’étendue **CurrentUser** :</span><span class="sxs-lookup"><span data-stu-id="17a58-179">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="17a58-180">Modifier la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-180">Change the execution policy</span></span>

<span data-ttu-id="17a58-181">Pour modifier la stratégie d’exécution de PowerShell sur votre ordinateur Windows, utilisez l’applet de commande `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="17a58-181">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="17a58-182">La modification prend effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="17a58-182">The change is effective immediately.</span></span> <span data-ttu-id="17a58-183">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17a58-183">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="17a58-184">Si vous définissez la stratégie d’exécution pour les étendues **LocalMachine** ou **CurrentUser** , la modification est enregistrée dans le registre et reste effective jusqu’à ce que vous la modifiiez de nouveau.</span><span class="sxs-lookup"><span data-stu-id="17a58-184">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="17a58-185">Si vous définissez la stratégie d’exécution pour l’étendue du **processus** , celle-ci n’est pas enregistrée dans le registre.</span><span class="sxs-lookup"><span data-stu-id="17a58-185">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="17a58-186">La stratégie d’exécution est conservée jusqu’à la fermeture du processus en cours et de tous les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="17a58-186">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="17a58-187">Dans Windows Vista et les versions ultérieures de Windows, pour exécuter des commandes qui modifient la stratégie d’exécution pour l’ordinateur local, l’étendue **LocalMachine** , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="17a58-187">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="17a58-188">Pour modifier votre stratégie d’exécution :</span><span class="sxs-lookup"><span data-stu-id="17a58-188">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="17a58-189">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="17a58-189">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="17a58-190">Pour définir la stratégie d’exécution dans une étendue particulière :</span><span class="sxs-lookup"><span data-stu-id="17a58-190">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="17a58-191">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="17a58-191">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="17a58-192">Une commande pour modifier une stratégie d’exécution peut être exécutée, mais ne modifie toujours pas la stratégie d’exécution en vigueur.</span><span class="sxs-lookup"><span data-stu-id="17a58-192">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="17a58-193">Par exemple, une commande qui définit la stratégie d’exécution de l’ordinateur local peut être exécutée, mais être remplacée par la stratégie d’exécution de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="17a58-193">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="17a58-194">Supprimer la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-194">Remove the execution policy</span></span>

<span data-ttu-id="17a58-195">Pour supprimer la stratégie d’exécution d’une étendue particulière, définissez la stratégie d’exécution sur **non définie** .</span><span class="sxs-lookup"><span data-stu-id="17a58-195">To remove the execution policy for a particular scope, set the execution policy to **Undefined** .</span></span>

<span data-ttu-id="17a58-196">Par exemple, pour supprimer la stratégie d’exécution pour tous les utilisateurs de l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="17a58-196">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="17a58-197">Pour supprimer la stratégie d’exécution d’une **étendue** :</span><span class="sxs-lookup"><span data-stu-id="17a58-197">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="17a58-198">Si aucune stratégie d’exécution n’est définie dans une étendue, la stratégie d’exécution en vigueur est **Restricted** , ce qui correspond à la valeur par défaut pour les clients Windows.</span><span class="sxs-lookup"><span data-stu-id="17a58-198">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="17a58-199">Définir une stratégie différente pour une session</span><span class="sxs-lookup"><span data-stu-id="17a58-199">Set a different policy for one session</span></span>

<span data-ttu-id="17a58-200">Vous pouvez utiliser le paramètre **ExecutionPolicy** de **powershell.exe** pour définir une stratégie d’exécution pour une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17a58-200">You can use the **ExecutionPolicy** parameter of **powershell.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="17a58-201">La stratégie affecte uniquement la session active et les sessions enfants.</span><span class="sxs-lookup"><span data-stu-id="17a58-201">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="17a58-202">Pour définir la stratégie d’exécution d’une nouvelle session, démarrez PowerShell sur la ligne de commande, par exemple **cmd.exe** ou à partir de PowerShell, puis utilisez le paramètre **ExecutionPolicy** de **powershell.exe** pour définir la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="17a58-202">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **powershell.exe** to set the execution policy.</span></span>

<span data-ttu-id="17a58-203">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="17a58-203">For example:</span></span>

```powershell
powershell.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="17a58-204">La stratégie d’exécution que vous définissez n’est pas stockée dans le registre.</span><span class="sxs-lookup"><span data-stu-id="17a58-204">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="17a58-205">Au lieu de cela, il est stocké dans la `$env:PSExecutionPolicyPreference` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="17a58-205">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="17a58-206">La variable est supprimée lorsque vous fermez la session dans laquelle la stratégie est définie.</span><span class="sxs-lookup"><span data-stu-id="17a58-206">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="17a58-207">Vous ne pouvez pas modifier la stratégie en modifiant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="17a58-207">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="17a58-208">Pendant la session, la stratégie d’exécution définie pour la session est prioritaire sur une stratégie d’exécution qui est définie dans le registre de l’ordinateur local ou de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="17a58-208">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="17a58-209">Toutefois, il n’est pas prioritaire sur la stratégie d’exécution définie à l’aide d’un stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="17a58-209">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="17a58-210">Utiliser stratégie de groupe pour gérer la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-210">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="17a58-211">Vous pouvez utiliser le paramètre **activer l’exécution du Script** stratégie de groupe pour gérer la stratégie d’exécution des ordinateurs de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="17a58-211">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="17a58-212">Le paramètre stratégie de groupe remplace les stratégies d’exécution définies dans PowerShell dans toutes les étendues.</span><span class="sxs-lookup"><span data-stu-id="17a58-212">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="17a58-213">Les paramètres **de stratégie d’exécution de script** sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="17a58-213">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="17a58-214">Si vous désactivez **l’exécution des** scripts, les scripts ne s’exécutent pas.</span><span class="sxs-lookup"><span data-stu-id="17a58-214">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="17a58-215">Cela équivaut à la stratégie d’exécution **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="17a58-215">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="17a58-216">Si vous activez **activer l’exécution des scripts** , vous pouvez sélectionner une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="17a58-216">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="17a58-217">Les paramètres de stratégie de groupe sont équivalents aux paramètres de stratégie d’exécution suivants :</span><span class="sxs-lookup"><span data-stu-id="17a58-217">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="17a58-218">Stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="17a58-218">Group Policy</span></span>                                  | <span data-ttu-id="17a58-219">Stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-219">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="17a58-220">Autoriser tous les scripts</span><span class="sxs-lookup"><span data-stu-id="17a58-220">Allow all scripts</span></span>                             | <span data-ttu-id="17a58-221">Non restreint</span><span class="sxs-lookup"><span data-stu-id="17a58-221">Unrestricted</span></span>     |
  | <span data-ttu-id="17a58-222">Autoriser les scripts locaux et les scripts signés distants</span><span class="sxs-lookup"><span data-stu-id="17a58-222">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="17a58-223">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="17a58-223">RemoteSigned</span></span>     |
  | <span data-ttu-id="17a58-224">Autoriser uniquement les scripts signés</span><span class="sxs-lookup"><span data-stu-id="17a58-224">Allow only signed scripts</span></span>                     | <span data-ttu-id="17a58-225">AllSigned</span><span class="sxs-lookup"><span data-stu-id="17a58-225">AllSigned</span></span>        |

- <span data-ttu-id="17a58-226">Si **l’exécution du script** n’est pas configurée, elle n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="17a58-226">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="17a58-227">La stratégie d’exécution définie dans PowerShell est effective.</span><span class="sxs-lookup"><span data-stu-id="17a58-227">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="17a58-228">Les fichiers PowerShellExecutionPolicy. adm et PowerShellExecutionPolicy. admx ajoutent la stratégie d' **exécution de script activer** aux nœuds Configuration ordinateur et configuration utilisateur dans stratégie de groupe éditeur dans les chemins d’accès suivants.</span><span class="sxs-lookup"><span data-stu-id="17a58-228">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="17a58-229">Pour Windows XP et Windows Server 2003 :</span><span class="sxs-lookup"><span data-stu-id="17a58-229">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="17a58-230">Modèles d’administration\Composants Windows\windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17a58-230">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="17a58-231">Pour Windows Vista et les versions ultérieures de Windows :</span><span class="sxs-lookup"><span data-stu-id="17a58-231">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="17a58-232">Modèles d’administration d’administration Templates\Classic </span><span class="sxs-lookup"><span data-stu-id="17a58-232">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="17a58-233">Windows Windows\windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17a58-233">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="17a58-234">Les stratégies définies dans le nœud Configuration de l’ordinateur sont prioritaires sur les stratégies définies dans le nœud Configuration utilisateur.</span><span class="sxs-lookup"><span data-stu-id="17a58-234">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="17a58-235">Pour plus d’informations, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="17a58-235">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="17a58-236">Priorité de la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="17a58-236">Execution policy precedence</span></span>

<span data-ttu-id="17a58-237">Lors de la détermination de la stratégie d’exécution effective pour une session, PowerShell évalue les stratégies d’exécution dans l’ordre de priorité suivant :</span><span class="sxs-lookup"><span data-stu-id="17a58-237">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="17a58-238">Stratégie de groupe : MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-238">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="17a58-239">Stratégie de groupe : UserPolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-239">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="17a58-240">Stratégie d’exécution : processus (ou `powershell.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="17a58-240">Execution Policy: Process (or `powershell.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="17a58-241">Stratégie d’exécution : CurrentUser</span><span class="sxs-lookup"><span data-stu-id="17a58-241">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="17a58-242">Stratégie d’exécution : LocalMachine</span><span class="sxs-lookup"><span data-stu-id="17a58-242">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="17a58-243">Gérer les scripts signés et non signés</span><span class="sxs-lookup"><span data-stu-id="17a58-243">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="17a58-244">Dans Windows, les programmes comme Internet Explorer et Microsoft Edge ajoutent un flux de données de remplacement aux fichiers téléchargés.</span><span class="sxs-lookup"><span data-stu-id="17a58-244">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="17a58-245">Cela marque le fichier comme « provenant d’Internet ».</span><span class="sxs-lookup"><span data-stu-id="17a58-245">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="17a58-246">Si votre stratégie d’exécution de PowerShell est **RemoteSigned** , PowerShell n’exécutera pas les scripts non signés téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.</span><span class="sxs-lookup"><span data-stu-id="17a58-246">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="17a58-247">Vous pouvez signer le script ou choisir d’exécuter un script non signé sans modifier la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="17a58-247">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="17a58-248">À compter de PowerShell 3,0, vous pouvez utiliser le paramètre **Stream** de l' `Get-Item` applet de commande pour détecter les fichiers qui sont bloqués, car ils ont été téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="17a58-248">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="17a58-249">Utilisez l' `Unblock-File` applet de commande pour débloquer les scripts afin de pouvoir les exécuter dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17a58-249">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="17a58-250">Pour plus d’informations, consultez [about_Signing](about_Signing.md), [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item)et [Unblock-file](xref:Microsoft.PowerShell.Utility.Unblock-File).</span><span class="sxs-lookup"><span data-stu-id="17a58-250">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="17a58-251">D’autres méthodes de téléchargement de fichiers peuvent ne pas marquer les fichiers comme provenant de la zone Internet.</span><span class="sxs-lookup"><span data-stu-id="17a58-251">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="17a58-252">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="17a58-252">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="17a58-253">Stratégie d’exécution sur Windows Server Core et Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="17a58-253">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="17a58-254">Quand PowerShell 5,1 est exécuté sur Windows Server Core ou Windows nano Server sous certaines conditions, les stratégies d’exécution peuvent échouer avec l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="17a58-254">When PowerShell 5.1 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="17a58-255">PowerShell utilise des API dans Windows Desktop Shell ( `explorer.exe` ) pour valider la zone d’un fichier de script.</span><span class="sxs-lookup"><span data-stu-id="17a58-255">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="17a58-256">L’interpréteur de commandes Windows n’est pas disponible sur Windows Server Core et sur Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="17a58-256">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="17a58-257">Vous pouvez également recevoir cette erreur sur n’importe quel système Windows si Windows Desktop Shell n’est pas disponible ou ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="17a58-257">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="17a58-258">Par exemple, lors de l’ouverture de session, un script d’ouverture de session PowerShell peut démarrer l’exécution avant que le bureau Windows soit prêt, provoquant ainsi un échec.</span><span class="sxs-lookup"><span data-stu-id="17a58-258">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="17a58-259">L’utilisation d’une stratégie d’exécution **Bypass** ou **AllSigned** ne nécessite pas de vérification de zone qui évite le problème.</span><span class="sxs-lookup"><span data-stu-id="17a58-259">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="17a58-260">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17a58-260">See Also</span></span>

[<span data-ttu-id="17a58-261">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="17a58-261">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="17a58-262">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="17a58-262">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="17a58-263">about_Signing</span><span class="sxs-lookup"><span data-stu-id="17a58-263">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="17a58-264">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-264">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="17a58-265">Get-Item</span><span class="sxs-lookup"><span data-stu-id="17a58-265">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="17a58-266"> Aide Command-LinePowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="17a58-266">PowerShell.exe Command-Line Help</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="17a58-267">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="17a58-267">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="17a58-268">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="17a58-268">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)

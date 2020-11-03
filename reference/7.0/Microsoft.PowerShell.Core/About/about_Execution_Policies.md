---
description: Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 5a9cb331c0c500f3b8bb944acdaae64788aff834
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208222"
---
# <a name="about-execution-policies"></a><span data-ttu-id="fdbad-104">À propos des stratégies d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="fdbad-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="fdbad-105">Short Description</span></span>
<span data-ttu-id="fdbad-106">Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.</span><span class="sxs-lookup"><span data-stu-id="fdbad-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="fdbad-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="fdbad-107">Long Description</span></span>

<span data-ttu-id="fdbad-108">La stratégie d’exécution de PowerShell est une fonctionnalité de sécurité qui contrôle les conditions dans lesquelles PowerShell charge les fichiers de configuration et exécute des scripts.</span><span class="sxs-lookup"><span data-stu-id="fdbad-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="fdbad-109">Cette fonctionnalité permet d’éviter l’exécution de scripts malveillants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="fdbad-110">Sur un ordinateur Windows, vous pouvez définir une stratégie d’exécution pour l’ordinateur local, pour l’utilisateur actuel ou pour une session particulière.</span><span class="sxs-lookup"><span data-stu-id="fdbad-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="fdbad-111">Vous pouvez également utiliser un paramètre de stratégie de groupe pour définir des stratégies d’exécution pour les ordinateurs et les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fdbad-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="fdbad-112">Les stratégies d’exécution de l’ordinateur local et de l’utilisateur actuel sont stockées dans le registre.</span><span class="sxs-lookup"><span data-stu-id="fdbad-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="fdbad-113">Vous n’avez pas besoin de définir des stratégies d’exécution dans votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdbad-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="fdbad-114">La stratégie d’exécution pour une session particulière est stockée uniquement en mémoire et est perdue lorsque la session est fermée.</span><span class="sxs-lookup"><span data-stu-id="fdbad-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="fdbad-115">La stratégie d’exécution n’est pas un système de sécurité qui restreint les actions des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fdbad-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="fdbad-116">Par exemple, les utilisateurs peuvent facilement contourner une stratégie en tapant le contenu du script sur la ligne de commande lorsqu’ils ne peuvent pas exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="fdbad-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="fdbad-117">Au lieu de cela, la stratégie d’exécution aide les utilisateurs à définir des règles de base et les empêche de les violer involontairement.</span><span class="sxs-lookup"><span data-stu-id="fdbad-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

<span data-ttu-id="fdbad-118">Sur les ordinateurs non-Windows, la stratégie d’exécution par défaut est **illimitée** et ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="fdbad-118">On non-Windows computers, the default execution policy is **Unrestricted** and cannot be changed.</span></span> <span data-ttu-id="fdbad-119">L' `Set-ExecutionPolicy` applet de commande est disponible, mais PowerShell affiche un message de console qui n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fdbad-119">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span> <span data-ttu-id="fdbad-120">Bien que `Get-ExecutionPolicy` retourne une valeur **illimitée** sur les plateformes non-Windows, le comportement correspond vraiment à **Bypass** , car ces plateformes n’implémentent pas les zones de sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-120">While `Get-ExecutionPolicy` returns **Unrestricted** on non-Windows platforms, the behavior really matches **Bypass** because those platforms do not implement the Windows Security Zones.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="fdbad-121">Stratégies d’exécution de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdbad-121">PowerShell execution policies</span></span>

<span data-ttu-id="fdbad-122">L’application de ces stratégies ne se produit que sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-122">Enforcement of these policies only occurs on Windows platforms.</span></span> <span data-ttu-id="fdbad-123">Les stratégies d’exécution de PowerShell sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fdbad-123">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="fdbad-124">AllSigned</span><span class="sxs-lookup"><span data-stu-id="fdbad-124">AllSigned</span></span>

- <span data-ttu-id="fdbad-125">Les scripts peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="fdbad-125">Scripts can run.</span></span>
- <span data-ttu-id="fdbad-126">nécessite que tous les scripts et fichiers de configuration soient signés par un éditeur approuvé, y compris les scripts que vous écrivez sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdbad-126">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="fdbad-127">Vous invite à confirmer l’exécution des scripts des serveurs de publication que vous n’avez pas encore classés comme approuvés ou non approuvés.</span><span class="sxs-lookup"><span data-stu-id="fdbad-127">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="fdbad-128">Risques liés à l’exécution de scripts signés, mais malveillants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-128">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="fdbad-129">Contournement</span><span class="sxs-lookup"><span data-stu-id="fdbad-129">Bypass</span></span>

- <span data-ttu-id="fdbad-130">rien n'est bloqué, et aucun avertissement, ni aucune invite ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="fdbad-130">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="fdbad-131">Cette stratégie d’exécution est conçue pour les configurations dans lesquelles un script PowerShell est intégré à une application plus volumineuse ou pour les configurations dans lesquelles PowerShell est la base d’un programme qui possède son propre modèle de sécurité.</span><span class="sxs-lookup"><span data-stu-id="fdbad-131">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="fdbad-132">Default</span><span class="sxs-lookup"><span data-stu-id="fdbad-132">Default</span></span>

- <span data-ttu-id="fdbad-133">Définit la stratégie d’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="fdbad-133">Sets the default execution policy.</span></span>
- <span data-ttu-id="fdbad-134">**Limité** pour les clients Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-134">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="fdbad-135">**RemoteSigned** pour les serveurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-135">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="fdbad-136">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="fdbad-136">RemoteSigned</span></span>

- <span data-ttu-id="fdbad-137">Stratégie d’exécution par défaut pour les ordinateurs Windows Server.</span><span class="sxs-lookup"><span data-stu-id="fdbad-137">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="fdbad-138">Les scripts peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="fdbad-138">Scripts can run.</span></span>
- <span data-ttu-id="fdbad-139">Requiert une signature numérique d’un éditeur approuvé sur les scripts et les fichiers de configuration téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.</span><span class="sxs-lookup"><span data-stu-id="fdbad-139">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="fdbad-140">Ne requiert pas de signatures numériques sur les scripts écrits sur l’ordinateur local et non téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="fdbad-140">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="fdbad-141">Exécute les scripts qui sont téléchargés à partir d’Internet et non signés, si les scripts sont débloqués, par exemple à l’aide de l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="fdbad-141">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="fdbad-142">Risques liés à l’exécution de scripts non signés provenant de sources autres que l’Internet et scripts signés pouvant être malveillants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-142">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="fdbad-143">Limitées</span><span class="sxs-lookup"><span data-stu-id="fdbad-143">Restricted</span></span>

- <span data-ttu-id="fdbad-144">Stratégie d’exécution par défaut pour les ordinateurs clients Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-144">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="fdbad-145">Autorise des commandes individuelles, mais n’autorise pas les scripts.</span><span class="sxs-lookup"><span data-stu-id="fdbad-145">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="fdbad-146">Empêche l’exécution de tous les fichiers de script, y compris les fichiers de mise en forme et de configuration ( `.ps1xml` ), les fichiers de script de module ( `.psm1` ) et les profils PowerShell ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="fdbad-146">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="fdbad-147">Indéfini</span><span class="sxs-lookup"><span data-stu-id="fdbad-147">Undefined</span></span>

- <span data-ttu-id="fdbad-148">Aucune stratégie d’exécution n’est définie dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="fdbad-148">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="fdbad-149">Si la stratégie d’exécution dans toutes les portées n’est **pas définie** , la stratégie d’exécution effective est **limitée** pour les clients Windows et **RemoteSigned** pour Windows Server.</span><span class="sxs-lookup"><span data-stu-id="fdbad-149">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="fdbad-150">Non restreint</span><span class="sxs-lookup"><span data-stu-id="fdbad-150">Unrestricted</span></span>

- <span data-ttu-id="fdbad-151">La stratégie d’exécution par défaut pour les ordinateurs non-Windows et ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="fdbad-151">The default execution policy for non-Windows computers and cannot be changed.</span></span>
- <span data-ttu-id="fdbad-152">Les scripts non signés peuvent s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="fdbad-152">Unsigned scripts can run.</span></span> <span data-ttu-id="fdbad-153">L’exécution de scripts malveillants présente un risque.</span><span class="sxs-lookup"><span data-stu-id="fdbad-153">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="fdbad-154">Avertit l’utilisateur avant d’exécuter des scripts et des fichiers de configuration qui ne proviennent pas de la zone Intranet local.</span><span class="sxs-lookup"><span data-stu-id="fdbad-154">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="fdbad-155">Sur les systèmes qui ne distinguent pas les chemins d’accès UNC (Universal Naming Convention) des chemins Internet, les scripts identifiés par un chemin d’accès UNC peuvent ne pas être autorisés à s’exécuter avec la stratégie d’exécution **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-155">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="fdbad-156">Étendue de la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-156">Execution policy scope</span></span>

<span data-ttu-id="fdbad-157">Vous pouvez définir une stratégie d’exécution qui est effective uniquement dans une étendue particulière.</span><span class="sxs-lookup"><span data-stu-id="fdbad-157">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="fdbad-158">Les valeurs valides pour **scope** sont **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** et **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-158">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine** .</span></span> <span data-ttu-id="fdbad-159">**LocalMachine** est la valeur par défaut lors de la définition d’une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fdbad-159">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="fdbad-160">Les valeurs d' **étendue** sont répertoriées par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="fdbad-160">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="fdbad-161">La stratégie qui est prioritaire est effective dans la session active, même si une stratégie plus restrictive a été définie à un niveau de priorité inférieur.</span><span class="sxs-lookup"><span data-stu-id="fdbad-161">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="fdbad-162">Pour plus d’informations, consultez [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span><span class="sxs-lookup"><span data-stu-id="fdbad-162">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="fdbad-163">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-163">MachinePolicy</span></span>

<span data-ttu-id="fdbad-164">Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fdbad-164">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="fdbad-165">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-165">UserPolicy</span></span>

<span data-ttu-id="fdbad-166">Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fdbad-166">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="fdbad-167">Process</span><span class="sxs-lookup"><span data-stu-id="fdbad-167">Process</span></span>

<span data-ttu-id="fdbad-168">L’étendue du **processus** affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="fdbad-168">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="fdbad-169">La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` , plutôt que dans le registre.</span><span class="sxs-lookup"><span data-stu-id="fdbad-169">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="fdbad-170">Une fois la session PowerShell fermée, la variable et la valeur sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="fdbad-170">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="fdbad-171">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="fdbad-171">CurrentUser</span></span>

<span data-ttu-id="fdbad-172">la stratégie d'exécution affecte uniquement l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fdbad-172">The execution policy affects only the current user.</span></span> <span data-ttu-id="fdbad-173">Elle est stockée dans la sous-clé de Registre **HKEY_CURRENT_USER** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-173">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="fdbad-174">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="fdbad-174">LocalMachine</span></span>

<span data-ttu-id="fdbad-175">La stratégie d’exécution affecte tous les utilisateurs sur l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fdbad-175">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="fdbad-176">Elle est stockée dans la sous-clé de Registre **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-176">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="fdbad-177">Gestion de la stratégie d’exécution avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdbad-177">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="fdbad-178">Pour obtenir la stratégie d’exécution effective pour la session PowerShell actuelle, utilisez l’applet de commande `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="fdbad-178">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="fdbad-179">La commande suivante obtient la stratégie d’exécution effective :</span><span class="sxs-lookup"><span data-stu-id="fdbad-179">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="fdbad-180">Pour obtenir toutes les stratégies d’exécution qui affectent la session active et les afficher dans l’ordre de priorité :</span><span class="sxs-lookup"><span data-stu-id="fdbad-180">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="fdbad-181">Le résultat ressemble à l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="fdbad-181">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="fdbad-182">Dans ce cas, la stratégie d’exécution effective est **RemoteSigned** car la stratégie d’exécution de l’utilisateur actuel est prioritaire sur la stratégie d’exécution définie pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdbad-182">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="fdbad-183">Pour obtenir la stratégie d’exécution définie pour une étendue particulière, utilisez le paramètre **scope** de `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="fdbad-183">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="fdbad-184">Par exemple, la commande suivante obtient la stratégie d’exécution pour l’étendue **CurrentUser** :</span><span class="sxs-lookup"><span data-stu-id="fdbad-184">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="fdbad-185">Modifier la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-185">Change the execution policy</span></span>

<span data-ttu-id="fdbad-186">Pour modifier la stratégie d’exécution de PowerShell sur votre ordinateur Windows, utilisez l’applet de commande `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="fdbad-186">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="fdbad-187">La modification prend effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="fdbad-187">The change is effective immediately.</span></span> <span data-ttu-id="fdbad-188">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdbad-188">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="fdbad-189">Si vous définissez la stratégie d’exécution pour les étendues **LocalMachine** ou **CurrentUser** , la modification est enregistrée dans le registre et reste effective jusqu’à ce que vous la modifiiez de nouveau.</span><span class="sxs-lookup"><span data-stu-id="fdbad-189">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="fdbad-190">Si vous définissez la stratégie d’exécution pour l’étendue du **processus** , celle-ci n’est pas enregistrée dans le registre.</span><span class="sxs-lookup"><span data-stu-id="fdbad-190">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="fdbad-191">La stratégie d’exécution est conservée jusqu’à la fermeture du processus en cours et de tous les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-191">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="fdbad-192">Dans Windows Vista et les versions ultérieures de Windows, pour exécuter des commandes qui modifient la stratégie d’exécution pour l’ordinateur local, l’étendue **LocalMachine** , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-192">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="fdbad-193">Pour modifier votre stratégie d’exécution :</span><span class="sxs-lookup"><span data-stu-id="fdbad-193">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="fdbad-194">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fdbad-194">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="fdbad-195">Pour définir la stratégie d’exécution dans une étendue particulière :</span><span class="sxs-lookup"><span data-stu-id="fdbad-195">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="fdbad-196">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fdbad-196">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="fdbad-197">Une commande pour modifier une stratégie d’exécution peut être exécutée, mais ne modifie toujours pas la stratégie d’exécution en vigueur.</span><span class="sxs-lookup"><span data-stu-id="fdbad-197">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="fdbad-198">Par exemple, une commande qui définit la stratégie d’exécution de l’ordinateur local peut être exécutée, mais être remplacée par la stratégie d’exécution de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fdbad-198">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="fdbad-199">Supprimer la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-199">Remove the execution policy</span></span>

<span data-ttu-id="fdbad-200">Pour supprimer la stratégie d’exécution d’une étendue particulière, définissez la stratégie d’exécution sur **non définie** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-200">To remove the execution policy for a particular scope, set the execution policy to **Undefined** .</span></span>

<span data-ttu-id="fdbad-201">Par exemple, pour supprimer la stratégie d’exécution pour tous les utilisateurs de l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="fdbad-201">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="fdbad-202">Pour supprimer la stratégie d’exécution d’une **étendue** :</span><span class="sxs-lookup"><span data-stu-id="fdbad-202">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="fdbad-203">Si aucune stratégie d’exécution n’est définie dans une étendue, la stratégie d’exécution en vigueur est **Restricted** , ce qui correspond à la valeur par défaut pour les clients Windows.</span><span class="sxs-lookup"><span data-stu-id="fdbad-203">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="fdbad-204">Définir une stratégie différente pour une session</span><span class="sxs-lookup"><span data-stu-id="fdbad-204">Set a different policy for one session</span></span>

<span data-ttu-id="fdbad-205">Vous pouvez utiliser le paramètre **ExecutionPolicy** de **pwsh.exe** pour définir une stratégie d’exécution pour une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdbad-205">You can use the **ExecutionPolicy** parameter of **pwsh.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="fdbad-206">La stratégie affecte uniquement la session active et les sessions enfants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-206">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="fdbad-207">Pour définir la stratégie d’exécution d’une nouvelle session, démarrez PowerShell sur la ligne de commande, par exemple **cmd.exe** ou à partir de PowerShell, puis utilisez le paramètre **ExecutionPolicy** de **pwsh.exe** pour définir la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fdbad-207">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **pwsh.exe** to set the execution policy.</span></span>

<span data-ttu-id="fdbad-208">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fdbad-208">For example:</span></span>

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="fdbad-209">La stratégie d’exécution que vous définissez n’est pas stockée dans le registre.</span><span class="sxs-lookup"><span data-stu-id="fdbad-209">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="fdbad-210">Au lieu de cela, il est stocké dans la `$env:PSExecutionPolicyPreference` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="fdbad-210">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="fdbad-211">La variable est supprimée lorsque vous fermez la session dans laquelle la stratégie est définie.</span><span class="sxs-lookup"><span data-stu-id="fdbad-211">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="fdbad-212">Vous ne pouvez pas modifier la stratégie en modifiant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="fdbad-212">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="fdbad-213">Pendant la session, la stratégie d’exécution définie pour la session est prioritaire sur une stratégie d’exécution qui est définie dans le registre de l’ordinateur local ou de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fdbad-213">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="fdbad-214">Toutefois, il n’est pas prioritaire sur la stratégie d’exécution définie à l’aide d’un stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="fdbad-214">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="fdbad-215">Utiliser stratégie de groupe pour gérer la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-215">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="fdbad-216">Vous pouvez utiliser le paramètre **activer l’exécution du Script** stratégie de groupe pour gérer la stratégie d’exécution des ordinateurs de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="fdbad-216">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="fdbad-217">Le paramètre stratégie de groupe remplace les stratégies d’exécution définies dans PowerShell dans toutes les étendues.</span><span class="sxs-lookup"><span data-stu-id="fdbad-217">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="fdbad-218">Les paramètres **de stratégie d’exécution de script** sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="fdbad-218">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="fdbad-219">Si vous désactivez **l’exécution des** scripts, les scripts ne s’exécutent pas.</span><span class="sxs-lookup"><span data-stu-id="fdbad-219">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="fdbad-220">Cela équivaut à la stratégie d’exécution **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="fdbad-220">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="fdbad-221">Si vous activez **activer l’exécution des scripts** , vous pouvez sélectionner une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fdbad-221">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="fdbad-222">Les paramètres de stratégie de groupe sont équivalents aux paramètres de stratégie d’exécution suivants :</span><span class="sxs-lookup"><span data-stu-id="fdbad-222">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="fdbad-223">Stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="fdbad-223">Group Policy</span></span>                                  | <span data-ttu-id="fdbad-224">Stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-224">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="fdbad-225">Autoriser tous les scripts</span><span class="sxs-lookup"><span data-stu-id="fdbad-225">Allow all scripts</span></span>                             | <span data-ttu-id="fdbad-226">Non restreint</span><span class="sxs-lookup"><span data-stu-id="fdbad-226">Unrestricted</span></span>     |
  | <span data-ttu-id="fdbad-227">Autoriser les scripts locaux et les scripts signés distants</span><span class="sxs-lookup"><span data-stu-id="fdbad-227">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="fdbad-228">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="fdbad-228">RemoteSigned</span></span>     |
  | <span data-ttu-id="fdbad-229">Autoriser uniquement les scripts signés</span><span class="sxs-lookup"><span data-stu-id="fdbad-229">Allow only signed scripts</span></span>                     | <span data-ttu-id="fdbad-230">AllSigned</span><span class="sxs-lookup"><span data-stu-id="fdbad-230">AllSigned</span></span>        |

- <span data-ttu-id="fdbad-231">Si **l’exécution du script** n’est pas configurée, elle n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="fdbad-231">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="fdbad-232">La stratégie d’exécution définie dans PowerShell est effective.</span><span class="sxs-lookup"><span data-stu-id="fdbad-232">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="fdbad-233">Les fichiers PowerShellExecutionPolicy. adm et PowerShellExecutionPolicy. admx ajoutent la stratégie d' **exécution de script activer** aux nœuds Configuration ordinateur et configuration utilisateur dans stratégie de groupe éditeur dans les chemins d’accès suivants.</span><span class="sxs-lookup"><span data-stu-id="fdbad-233">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="fdbad-234">Pour Windows XP et Windows Server 2003 :</span><span class="sxs-lookup"><span data-stu-id="fdbad-234">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="fdbad-235">Modèles d’administration\Composants Windows\windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdbad-235">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="fdbad-236">Pour Windows Vista et les versions ultérieures de Windows :</span><span class="sxs-lookup"><span data-stu-id="fdbad-236">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="fdbad-237">Modèles d’administration d’administration Templates\Classic </span><span class="sxs-lookup"><span data-stu-id="fdbad-237">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="fdbad-238">Windows Windows\windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdbad-238">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="fdbad-239">Les stratégies définies dans le nœud Configuration de l’ordinateur sont prioritaires sur les stratégies définies dans le nœud Configuration utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fdbad-239">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="fdbad-240">Pour plus d’informations, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="fdbad-240">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="fdbad-241">Priorité de la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="fdbad-241">Execution policy precedence</span></span>

<span data-ttu-id="fdbad-242">Lors de la détermination de la stratégie d’exécution effective pour une session, PowerShell évalue les stratégies d’exécution dans l’ordre de priorité suivant :</span><span class="sxs-lookup"><span data-stu-id="fdbad-242">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="fdbad-243">Stratégie de groupe : MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-243">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="fdbad-244">Stratégie de groupe : UserPolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-244">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="fdbad-245">Stratégie d’exécution : processus (ou `pwsh.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="fdbad-245">Execution Policy: Process (or `pwsh.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="fdbad-246">Stratégie d’exécution : CurrentUser</span><span class="sxs-lookup"><span data-stu-id="fdbad-246">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="fdbad-247">Stratégie d’exécution : LocalMachine</span><span class="sxs-lookup"><span data-stu-id="fdbad-247">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="fdbad-248">Gérer les scripts signés et non signés</span><span class="sxs-lookup"><span data-stu-id="fdbad-248">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="fdbad-249">Dans Windows, les programmes comme Internet Explorer et Microsoft Edge ajoutent un flux de données de remplacement aux fichiers téléchargés.</span><span class="sxs-lookup"><span data-stu-id="fdbad-249">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="fdbad-250">Cela marque le fichier comme « provenant d’Internet ».</span><span class="sxs-lookup"><span data-stu-id="fdbad-250">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="fdbad-251">Si votre stratégie d’exécution de PowerShell est **RemoteSigned** , PowerShell n’exécutera pas les scripts non signés téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.</span><span class="sxs-lookup"><span data-stu-id="fdbad-251">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="fdbad-252">Vous pouvez signer le script ou choisir d’exécuter un script non signé sans modifier la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fdbad-252">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="fdbad-253">À compter de PowerShell 3,0, vous pouvez utiliser le paramètre **Stream** de l' `Get-Item` applet de commande pour détecter les fichiers qui sont bloqués, car ils ont été téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="fdbad-253">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="fdbad-254">Utilisez l' `Unblock-File` applet de commande pour débloquer les scripts afin de pouvoir les exécuter dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdbad-254">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="fdbad-255">Pour plus d’informations, consultez [about_Signing](about_Signing.md), [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item)et [Unblock-file](xref:Microsoft.PowerShell.Utility.Unblock-File).</span><span class="sxs-lookup"><span data-stu-id="fdbad-255">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="fdbad-256">D’autres méthodes de téléchargement de fichiers peuvent ne pas marquer les fichiers comme provenant de la zone Internet.</span><span class="sxs-lookup"><span data-stu-id="fdbad-256">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="fdbad-257">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="fdbad-257">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="fdbad-258">Stratégie d’exécution sur Windows Server Core et Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="fdbad-258">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="fdbad-259">Lorsque PowerShell 6 est exécuté sur Windows Server Core ou Windows nano Server sous certaines conditions, les stratégies d’exécution peuvent échouer avec l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="fdbad-259">When PowerShell 6 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="fdbad-260">PowerShell utilise des API dans Windows Desktop Shell ( `explorer.exe` ) pour valider la zone d’un fichier de script.</span><span class="sxs-lookup"><span data-stu-id="fdbad-260">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="fdbad-261">L’interpréteur de commandes Windows n’est pas disponible sur Windows Server Core et sur Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="fdbad-261">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="fdbad-262">Vous pouvez également recevoir cette erreur sur n’importe quel système Windows si Windows Desktop Shell n’est pas disponible ou ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="fdbad-262">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="fdbad-263">Par exemple, lors de l’ouverture de session, un script d’ouverture de session PowerShell peut démarrer l’exécution avant que le bureau Windows soit prêt, provoquant ainsi un échec.</span><span class="sxs-lookup"><span data-stu-id="fdbad-263">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="fdbad-264">L’utilisation d’une stratégie d’exécution **Bypass** ou **AllSigned** ne nécessite pas de vérification de zone qui évite le problème.</span><span class="sxs-lookup"><span data-stu-id="fdbad-264">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdbad-265">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdbad-265">See Also</span></span>

[<span data-ttu-id="fdbad-266">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="fdbad-266">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="fdbad-267">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="fdbad-267">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="fdbad-268">about_Signing</span><span class="sxs-lookup"><span data-stu-id="fdbad-268">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="fdbad-269">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-269">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="fdbad-270">Get-Item</span><span class="sxs-lookup"><span data-stu-id="fdbad-270">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="fdbad-271">Aide de la console Pwsh</span><span class="sxs-lookup"><span data-stu-id="fdbad-271">Pwsh Console Help</span></span>](about_pwsh.md)

[<span data-ttu-id="fdbad-272">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fdbad-272">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="fdbad-273">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="fdbad-273">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)
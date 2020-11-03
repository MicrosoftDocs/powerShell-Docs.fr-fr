---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 313ff4f2d3fc89263cdf4d0ede860ef8e538a2ea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203389"
---
# <span data-ttu-id="5bd6d-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5bd6d-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="5bd6d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5bd6d-104">SYNOPSIS</span></span>
<span data-ttu-id="5bd6d-105">Définit les stratégies d’exécution de PowerShell pour les ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="5bd6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5bd6d-106">SYNTAX</span></span>

### <span data-ttu-id="5bd6d-107">Tous</span><span class="sxs-lookup"><span data-stu-id="5bd6d-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5bd6d-108">Description</span><span class="sxs-lookup"><span data-stu-id="5bd6d-108">DESCRIPTION</span></span>

<span data-ttu-id="5bd6d-109">L' `Set-ExecutionPolicy` applet de commande modifie les stratégies d’exécution PowerShell pour les ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="5bd6d-110">Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="5bd6d-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="5bd6d-111">Une stratégie d’exécution fait partie de la stratégie de sécurité PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-111">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="5bd6d-112">Les stratégies d’exécution déterminent si vous pouvez charger des fichiers de configuration, tels que votre profil PowerShell, ou exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-112">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="5bd6d-113">Et si les scripts doivent être signés numériquement avant leur exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-113">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="5bd6d-114">L' `Set-ExecutionPolicy` étendue par défaut de l’applet de commande est **LocalMachine** , ce qui affecte tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-114">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="5bd6d-115">Pour modifier la stratégie d’exécution de **LocalMachine** , démarrez PowerShell avec **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-115">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator** .</span></span>

<span data-ttu-id="5bd6d-116">Pour afficher les stratégies d’exécution pour chaque étendue dans l’ordre de priorité, utilisez `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-116">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="5bd6d-117">Pour afficher la stratégie d’exécution effective pour votre session PowerShell `Get-ExecutionPolicy` , utilisez sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-117">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="5bd6d-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5bd6d-118">EXAMPLES</span></span>

### <span data-ttu-id="5bd6d-119">Exemple 1 : définir une stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="5bd6d-119">Example 1: Set an execution policy</span></span>

<span data-ttu-id="5bd6d-120">Cet exemple montre comment définir la stratégie d’exécution pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-120">This example shows how to set the execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="5bd6d-121">L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-121">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="5bd6d-122">Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-122">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span> <span data-ttu-id="5bd6d-123">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-123">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="5bd6d-124">Exemple 2 : définir une stratégie d’exécution qui est en conflit avec un stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="5bd6d-124">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="5bd6d-125">Cette commande tente de définir la stratégie d’exécution de l’étendue **LocalMachine** sur **Restricted** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-125">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted** .</span></span>
<span data-ttu-id="5bd6d-126">**LocalMachine** est plus restrictif, mais n’est pas la stratégie effective, car elle est en conflit avec une stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-126">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="5bd6d-127">La stratégie **restreinte** est écrite dans la ruche du Registre **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-127">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="5bd6d-128">L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-128">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="5bd6d-129">Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-129">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span>
<span data-ttu-id="5bd6d-130">L' `Get-ChildItem` applet de commande utilise le paramètre **path** avec le fournisseur **HKLM** pour spécifier l’emplacement du Registre.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-130">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="5bd6d-131">Exemple 3 : appliquer la stratégie d’exécution d’un ordinateur distant à un ordinateur local</span><span class="sxs-lookup"><span data-stu-id="5bd6d-131">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="5bd6d-132">Cette commande obtient l’objet de stratégie d’exécution à partir d’un ordinateur distant et définit la stratégie sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-132">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="5bd6d-133">`Get-ExecutionPolicy` envoie un objet **Microsoft.PowerShell.ExecutionPolicy** dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-133">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="5bd6d-134">`Set-ExecutionPolicy` accepte l’entrée de pipeline et ne nécessite pas le paramètre **ExecutionPolicy** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-134">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="5bd6d-135">L' `Invoke-Command` applet de commande est exécutée sur l’ordinateur local et envoie le **scriptblock** à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-135">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="5bd6d-136">Le paramètre **ComputerName** spécifie l’ordinateur distant **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-136">The **ComputerName** parameter specifies the remote computer, **Server01** .</span></span> <span data-ttu-id="5bd6d-137">Le paramètre **scriptblock** s’exécute `Get-ExecutionPolicy` sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-137">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="5bd6d-138">L' `Get-ExecutionPolicy` objet est envoyé dans le pipeline au `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-138">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="5bd6d-139">`Set-ExecutionPolicy` applique la stratégie d’exécution à l’étendue par défaut de l’ordinateur local, **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-139">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine** .</span></span>

### <span data-ttu-id="5bd6d-140">Exemple 4 : définir l’étendue d’une stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="5bd6d-140">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="5bd6d-141">Cet exemple montre comment définir une stratégie d’exécution pour une étendue spécifiée, **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-141">This example shows how to set an execution policy for a specified scope, **CurrentUser** .</span></span> <span data-ttu-id="5bd6d-142">L’étendue **CurrentUser** affecte uniquement l’utilisateur qui définit cette étendue.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-142">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="5bd6d-143">`Set-ExecutionPolicy` utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **AllSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-143">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="5bd6d-144">Le paramètre **scope** spécifie le **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-144">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="5bd6d-145">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-145">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="5bd6d-146">La stratégie d’exécution effective pour l’utilisateur devient **AllSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-146">The effective execution policy for the user becomes **AllSigned** .</span></span>

### <span data-ttu-id="5bd6d-147">Exemple 5 : supprimer la stratégie d’exécution de l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="5bd6d-147">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="5bd6d-148">Cet exemple montre comment utiliser la stratégie d’exécution **non définie** pour supprimer une stratégie d’exécution pour une étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-148">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="5bd6d-149">`Set-ExecutionPolicy` utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **non définie** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-149">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="5bd6d-150">Le paramètre **scope** spécifie le **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-150">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="5bd6d-151">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-151">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="5bd6d-152">Exemple 6 : définir la stratégie d’exécution pour la session PowerShell active</span><span class="sxs-lookup"><span data-stu-id="5bd6d-152">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="5bd6d-153">L’étendue du **processus** affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-153">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="5bd6d-154">La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` et est supprimée lors de la fermeture de la session.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-154">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="5bd6d-155">`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **AllSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-155">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="5bd6d-156">Le paramètre **scope** spécifie le **processus** de valeur.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-156">The **Scope** parameter specifies the value **Process** .</span></span> <span data-ttu-id="5bd6d-157">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-157">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="5bd6d-158">Exemple 7 : débloquer un script pour l’exécuter sans modifier la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="5bd6d-158">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="5bd6d-159">Cet exemple montre comment la stratégie d’exécution **RemoteSigned** vous empêche d’exécuter des scripts non signés.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-159">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="5bd6d-160">Une bonne pratique consiste à lire le code du script et à vérifier qu’il est sûr **avant** d’utiliser l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-160">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="5bd6d-161">L' `Unblock-File` applet de commande débloque les scripts pour qu’ils puissent s’exécuter, mais ne modifie pas la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-161">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="5bd6d-162">`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-162">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="5bd6d-163">La stratégie est définie pour l’étendue par défaut, **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-163">The policy is set for the default scope, **LocalMachine** .</span></span>

<span data-ttu-id="5bd6d-164">L' `Get-ExecutionPolicy` applet de commande montre que **RemoteSigned** est la stratégie d’exécution effective pour la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-164">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="5bd6d-165">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-165">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="5bd6d-166">Le script est bloqué par **RemoteSigned** car le script n’est pas signé numériquement.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-166">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="5bd6d-167">Pour cet exemple, le code du script a été révisé et vérifié comme étant sécurisé pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-167">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="5bd6d-168">L' `Unblock-File` applet de commande utilise le paramètre **path** pour débloquer le script.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-168">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="5bd6d-169">Pour vérifier que `Unblock-File` la stratégie d’exécution n’a pas été modifiée, `Get-ExecutionPolicy` affiche la stratégie d’exécution effective, **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-169">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned** .</span></span>

<span data-ttu-id="5bd6d-170">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-170">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="5bd6d-171">Le script commence à s’exécuter, car il a été débloqué par l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-171">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="5bd6d-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5bd6d-172">PARAMETERS</span></span>

### <span data-ttu-id="5bd6d-173">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5bd6d-173">-ExecutionPolicy</span></span>

<span data-ttu-id="5bd6d-174">Spécifie la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-174">Specifies the execution policy.</span></span> <span data-ttu-id="5bd6d-175">S’il n’y a pas de stratégies de groupe et que la stratégie d’exécution de chaque étendue est définie sur non **définie, la** **restriction** devient la stratégie effective pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-175">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="5bd6d-176">Les valeurs de stratégie d’exécution acceptables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bd6d-176">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="5bd6d-177">**AllSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-177">**AllSigned** .</span></span> <span data-ttu-id="5bd6d-178">Requiert que tous les scripts et fichiers de configuration soient signés par un éditeur approuvé, y compris les scripts écrits sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-178">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="5bd6d-179">**Ignorer** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-179">**Bypass** .</span></span> <span data-ttu-id="5bd6d-180">rien n'est bloqué, et aucun avertissement, ni aucune invite ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-180">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="5bd6d-181">**Par défaut** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-181">**Default** .</span></span> <span data-ttu-id="5bd6d-182">Définit la stratégie d’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-182">Sets the default execution policy.</span></span> <span data-ttu-id="5bd6d-183">**Limité** pour les clients Windows ou **RemoteSigned** pour les serveurs Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-183">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="5bd6d-184">**RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-184">**RemoteSigned** .</span></span> <span data-ttu-id="5bd6d-185">Requiert que tous les scripts et fichiers de configuration téléchargés à partir d’Internet soient signés par un éditeur approuvé.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-185">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="5bd6d-186">Stratégie d’exécution par défaut pour les ordinateurs Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-186">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="5bd6d-187">**Limité** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-187">**Restricted** .</span></span> <span data-ttu-id="5bd6d-188">Ne charge pas les fichiers de configuration ou n’exécute pas de scripts.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-188">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="5bd6d-189">La stratégie d’exécution par défaut des ordinateurs clients Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-189">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="5bd6d-190">**Non défini** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-190">**Undefined** .</span></span> <span data-ttu-id="5bd6d-191">Aucune stratégie d’exécution n’est définie pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-191">No execution policy is set for the scope.</span></span> <span data-ttu-id="5bd6d-192">Supprime une stratégie d’exécution affectée d’une étendue qui n’est pas définie par un stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-192">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="5bd6d-193">Si la stratégie d’exécution dans toutes les portées n’est **pas définie** , la stratégie d’exécution effective est **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-193">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** .</span></span>
- <span data-ttu-id="5bd6d-194">Non **restreint** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-194">**Unrestricted** .</span></span> <span data-ttu-id="5bd6d-195">charge tous les fichiers de configuration et exécute tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-195">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="5bd6d-196">Si vous exécutez un script non signé téléchargé à partir d'Internet, vous êtes invité à autoriser son exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-196">If you run an unsigned script that was downloaded from the Internet, you are prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5bd6d-197">-Force</span><span class="sxs-lookup"><span data-stu-id="5bd6d-197">-Force</span></span>

<span data-ttu-id="5bd6d-198">Supprime toutes les invites de confirmation.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-198">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="5bd6d-199">Soyez prudent avec ce paramètre pour éviter des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-199">Use caution with this parameter to avoid unexpected results.</span></span>

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

### <span data-ttu-id="5bd6d-200">-Étendue</span><span class="sxs-lookup"><span data-stu-id="5bd6d-200">-Scope</span></span>

<span data-ttu-id="5bd6d-201">Spécifie l’étendue qui est affectée par une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-201">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="5bd6d-202">La portée par défaut est **LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-202">The default scope is **LocalMachine** .</span></span>

<span data-ttu-id="5bd6d-203">La stratégie d’exécution effective est déterminée par l’ordre de priorité comme suit :</span><span class="sxs-lookup"><span data-stu-id="5bd6d-203">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="5bd6d-204">**MachinePolicy** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-204">**MachinePolicy** .</span></span> <span data-ttu-id="5bd6d-205">Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-205">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="5bd6d-206">**UserPolicy** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-206">**UserPolicy** .</span></span> <span data-ttu-id="5bd6d-207">Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-207">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="5bd6d-208">**Processus** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-208">**Process** .</span></span> <span data-ttu-id="5bd6d-209">Affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-209">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="5bd6d-210">**CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-210">**CurrentUser** .</span></span> <span data-ttu-id="5bd6d-211">Affecte uniquement l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-211">Affects only the current user.</span></span>
- <span data-ttu-id="5bd6d-212">**LocalMachine** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-212">**LocalMachine** .</span></span> <span data-ttu-id="5bd6d-213">Étendue par défaut qui affecte tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-213">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="5bd6d-214">L’étendue du **processus** affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-214">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="5bd6d-215">La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` , plutôt que dans le registre.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-215">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="5bd6d-216">Une fois la session PowerShell fermée, la variable et la valeur sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-216">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="5bd6d-217">Les stratégies d’exécution de l’étendue **CurrentUser** sont écrites dans la ruche du Registre **HKEY_LOCAL_USER** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-217">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER** .</span></span>

<span data-ttu-id="5bd6d-218">Les stratégies d’exécution de l’étendue **LocalMachine** sont écrites dans la ruche du Registre **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-218">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5bd6d-219">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5bd6d-219">-Confirm</span></span>

<span data-ttu-id="5bd6d-220">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-220">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5bd6d-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5bd6d-221">-WhatIf</span></span>

<span data-ttu-id="5bd6d-222">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-222">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5bd6d-223">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-223">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5bd6d-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5bd6d-224">CommonParameters</span></span>

<span data-ttu-id="5bd6d-225">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5bd6d-226">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5bd6d-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5bd6d-227">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5bd6d-227">INPUTS</span></span>

### <span data-ttu-id="5bd6d-228">Microsoft.PowerShell.ExecutionPolicy, System. String</span><span class="sxs-lookup"><span data-stu-id="5bd6d-228">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="5bd6d-229">Vous pouvez diriger un objet de stratégie d’exécution ou une chaîne qui contient le nom d’une stratégie d’exécution vers `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5bd6d-229">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="5bd6d-230">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5bd6d-230">OUTPUTS</span></span>

### <span data-ttu-id="5bd6d-231">Aucun</span><span class="sxs-lookup"><span data-stu-id="5bd6d-231">None</span></span>

<span data-ttu-id="5bd6d-232">`Set-ExecutionPolicy` ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-232">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="5bd6d-233">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5bd6d-233">NOTES</span></span>

<span data-ttu-id="5bd6d-234">`Set-ExecutionPolicy` ne modifie pas les étendues **MachinePolicy** et **UserPolicy** , car elles sont définies par des stratégies de groupe.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-234">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="5bd6d-235">`Set-ExecutionPolicy` ne remplace pas un stratégie de groupe, même si la préférence de l’utilisateur est plus restrictive que la stratégie.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-235">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="5bd6d-236">Si la stratégie de groupe **activer l’exécution du script** est activée pour l’ordinateur ou l’utilisateur, la préférence de l’utilisateur est enregistrée, mais elle n’est pas effective.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-236">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="5bd6d-237">PowerShell affiche un message expliquant le conflit.</span><span class="sxs-lookup"><span data-stu-id="5bd6d-237">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="5bd6d-238">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5bd6d-238">RELATED LINKS</span></span>

[<span data-ttu-id="5bd6d-239">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="5bd6d-239">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="5bd6d-240">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="5bd6d-240">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="5bd6d-241">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5bd6d-241">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="5bd6d-242">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5bd6d-242">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="5bd6d-243">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5bd6d-243">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="5bd6d-244">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5bd6d-244">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="5bd6d-245">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="5bd6d-245">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="5bd6d-246">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5bd6d-246">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="5bd6d-247">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="5bd6d-247">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)

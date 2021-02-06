---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: d6555f1abc824add4613654461106af34045e1a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597140"
---
# <span data-ttu-id="8305d-102">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="8305d-102">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="8305d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8305d-103">SYNOPSIS</span></span>
<span data-ttu-id="8305d-104">Obtient les stratégies d'exécution pour la session active.</span><span class="sxs-lookup"><span data-stu-id="8305d-104">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="8305d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8305d-105">SYNTAX</span></span>

### <span data-ttu-id="8305d-106">Tous</span><span class="sxs-lookup"><span data-stu-id="8305d-106">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="8305d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8305d-107">DESCRIPTION</span></span>

<span data-ttu-id="8305d-108">Pour afficher les stratégies d’exécution pour chaque étendue dans l’ordre de priorité, utilisez `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="8305d-108">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="8305d-109">Pour afficher la stratégie d’exécution effective pour votre session PowerShell `Get-ExecutionPolicy` , utilisez sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="8305d-109">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="8305d-110">La stratégie d’exécution effective est déterminée par les stratégies d’exécution définies par `Set-ExecutionPolicy` et stratégie de groupe paramètres.</span><span class="sxs-lookup"><span data-stu-id="8305d-110">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="8305d-111">Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="8305d-111">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="8305d-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8305d-112">EXAMPLES</span></span>

### <span data-ttu-id="8305d-113">Exemple 1 : récupération de toutes les stratégies d’exécution</span><span class="sxs-lookup"><span data-stu-id="8305d-113">Example 1: Get all execution policies</span></span>

<span data-ttu-id="8305d-114">Cette commande affiche les stratégies d’exécution pour chaque étendue dans l’ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="8305d-114">This command displays the execution policies for each scope in the order of precedence.</span></span>

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

<span data-ttu-id="8305d-115">L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="8305d-115">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="8305d-116">Exemple 2 : définir une stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="8305d-116">Example 2: Set an execution policy</span></span>

<span data-ttu-id="8305d-117">Cet exemple montre comment définir une stratégie d’exécution pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8305d-117">This example shows how to set an execution policy for the local computer.</span></span>

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="8305d-118">L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="8305d-118">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="8305d-119">Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="8305d-119">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="8305d-120">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="8305d-120">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="8305d-121">Exemple 3 : récupération de la stratégie d’exécution en vigueur</span><span class="sxs-lookup"><span data-stu-id="8305d-121">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="8305d-122">Cet exemple montre comment afficher la stratégie d’exécution effective pour une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8305d-122">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

<span data-ttu-id="8305d-123">L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="8305d-123">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="8305d-124">L' `Get-ExecutionPolicy` applet de commande est exécutée sans paramètre pour afficher la stratégie d’exécution effective, **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="8305d-124">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="8305d-125">Exemple 4 : débloquer un script pour l’exécuter sans modifier la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="8305d-125">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="8305d-126">Cet exemple montre comment la stratégie d’exécution **RemoteSigned** vous empêche d’exécuter des scripts non signés.</span><span class="sxs-lookup"><span data-stu-id="8305d-126">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="8305d-127">Une bonne pratique consiste à lire le code du script et à vérifier qu’il est sûr **avant** d’utiliser l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="8305d-127">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="8305d-128">L' `Unblock-File` applet de commande débloque les scripts pour qu’ils puissent s’exécuter, mais ne modifie pas la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8305d-128">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="8305d-129">`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="8305d-129">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="8305d-130">La stratégie est définie pour l’étendue par défaut, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="8305d-130">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="8305d-131">L' `Get-ExecutionPolicy` applet de commande montre que **RemoteSigned** est la stratégie d’exécution effective pour la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8305d-131">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="8305d-132">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="8305d-132">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="8305d-133">Le script est bloqué par **RemoteSigned** car le script n’est pas signé numériquement.</span><span class="sxs-lookup"><span data-stu-id="8305d-133">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="8305d-134">Pour cet exemple, le code du script a été révisé et vérifié comme étant sécurisé pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8305d-134">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="8305d-135">L' `Unblock-File` applet de commande utilise le paramètre **path** pour débloquer le script.</span><span class="sxs-lookup"><span data-stu-id="8305d-135">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="8305d-136">Pour vérifier que `Unblock-File` la stratégie d’exécution n’a pas été modifiée, `Get-ExecutionPolicy` affiche la stratégie d’exécution effective, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="8305d-136">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="8305d-137">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="8305d-137">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="8305d-138">Le script commence à s’exécuter, car il a été débloqué par l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="8305d-138">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="8305d-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8305d-139">PARAMETERS</span></span>

### <span data-ttu-id="8305d-140">-List</span><span class="sxs-lookup"><span data-stu-id="8305d-140">-List</span></span>

<span data-ttu-id="8305d-141">Obtient toutes les valeurs de stratégie d'exécution pour la session dans l'ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="8305d-141">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="8305d-142">Par défaut, `Get-ExecutionPolicy` obtient uniquement la stratégie d’exécution effective.</span><span class="sxs-lookup"><span data-stu-id="8305d-142">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="8305d-143">-Étendue</span><span class="sxs-lookup"><span data-stu-id="8305d-143">-Scope</span></span>

<span data-ttu-id="8305d-144">Spécifie l’étendue qui est affectée par une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8305d-144">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="8305d-145">La stratégie d’exécution effective est déterminée par l’ordre de priorité comme suit :</span><span class="sxs-lookup"><span data-stu-id="8305d-145">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="8305d-146">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="8305d-146">**MachinePolicy**.</span></span> <span data-ttu-id="8305d-147">Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8305d-147">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="8305d-148">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="8305d-148">**UserPolicy**.</span></span> <span data-ttu-id="8305d-149">Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8305d-149">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="8305d-150">**Processus**.</span><span class="sxs-lookup"><span data-stu-id="8305d-150">**Process**.</span></span> <span data-ttu-id="8305d-151">Affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="8305d-151">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="8305d-152">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="8305d-152">**CurrentUser**.</span></span> <span data-ttu-id="8305d-153">Affecte uniquement l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8305d-153">Affects only the current user.</span></span>
- <span data-ttu-id="8305d-154">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="8305d-154">**LocalMachine**.</span></span> <span data-ttu-id="8305d-155">Étendue par défaut qui affecte tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8305d-155">Default scope that affects all users of the computer.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8305d-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8305d-156">CommonParameters</span></span>

<span data-ttu-id="8305d-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8305d-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8305d-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8305d-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8305d-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8305d-159">INPUTS</span></span>

### <span data-ttu-id="8305d-160">None</span><span class="sxs-lookup"><span data-stu-id="8305d-160">None</span></span>

<span data-ttu-id="8305d-161">`Get-ExecutionPolicy` n’accepte pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="8305d-161">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="8305d-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8305d-162">OUTPUTS</span></span>

### <span data-ttu-id="8305d-163">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="8305d-163">Microsoft.PowerShell.ExecutionPolicy</span></span>

<span data-ttu-id="8305d-164">L’applet de commande retourne toujours les plateformes non **restreintes** sur les plateformes Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="8305d-164">The cmdlet always returns **Unrestricted** on Linux and macOS platforms.</span></span>

## <span data-ttu-id="8305d-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8305d-165">NOTES</span></span>

<span data-ttu-id="8305d-166">Une stratégie d’exécution fait partie de la stratégie de sécurité PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8305d-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="8305d-167">Les stratégies d’exécution déterminent si vous pouvez charger des fichiers de configuration, tels que votre profil PowerShell, ou exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="8305d-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="8305d-168">Et si les scripts doivent être signés numériquement avant leur exécution.</span><span class="sxs-lookup"><span data-stu-id="8305d-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="8305d-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8305d-169">RELATED LINKS</span></span>

[<span data-ttu-id="8305d-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="8305d-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="8305d-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="8305d-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="8305d-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8305d-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="8305d-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8305d-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="8305d-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="8305d-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: f798aaef7032db450a13d79589eb7dd0ca762cd6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344828"
---
# <span data-ttu-id="44c4e-103">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="44c4e-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="44c4e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="44c4e-104">SYNOPSIS</span></span>
<span data-ttu-id="44c4e-105">Obtient les stratégies d'exécution pour la session active.</span><span class="sxs-lookup"><span data-stu-id="44c4e-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="44c4e-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="44c4e-106">SYNTAX</span></span>

### <span data-ttu-id="44c4e-107">Tous</span><span class="sxs-lookup"><span data-stu-id="44c4e-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="44c4e-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="44c4e-108">DESCRIPTION</span></span>

<span data-ttu-id="44c4e-109">Pour afficher les stratégies d’exécution pour chaque étendue dans l’ordre de priorité, utilisez `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="44c4e-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="44c4e-110">Pour afficher la stratégie d’exécution effective pour votre session PowerShell `Get-ExecutionPolicy` , utilisez sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="44c4e-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="44c4e-111">La stratégie d’exécution effective est déterminée par les stratégies d’exécution définies par `Set-ExecutionPolicy` et stratégie de groupe paramètres.</span><span class="sxs-lookup"><span data-stu-id="44c4e-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="44c4e-112">Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="44c4e-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="44c4e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="44c4e-113">EXAMPLES</span></span>

### <span data-ttu-id="44c4e-114">Exemple 1 : récupération de toutes les stratégies d’exécution</span><span class="sxs-lookup"><span data-stu-id="44c4e-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="44c4e-115">Cette commande affiche les stratégies d’exécution pour chaque étendue dans l’ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="44c4e-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

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

<span data-ttu-id="44c4e-116">L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="44c4e-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="44c4e-117">Exemple 2 : définir une stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="44c4e-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="44c4e-118">Cet exemple montre comment définir une stratégie d’exécution pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="44c4e-118">This example shows how to set an execution policy for the local computer.</span></span>

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

<span data-ttu-id="44c4e-119">L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="44c4e-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="44c4e-120">Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-120">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="44c4e-121">Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="44c4e-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="44c4e-122">Exemple 3 : récupération de la stratégie d’exécution en vigueur</span><span class="sxs-lookup"><span data-stu-id="44c4e-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="44c4e-123">Cet exemple montre comment afficher la stratégie d’exécution effective pour une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44c4e-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

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

<span data-ttu-id="44c4e-124">L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="44c4e-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="44c4e-125">L' `Get-ExecutionPolicy` applet de commande est exécutée sans paramètre pour afficher la stratégie d’exécution effective, **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="44c4e-126">Exemple 4 : débloquer un script pour l’exécuter sans modifier la stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="44c4e-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="44c4e-127">Cet exemple montre comment la stratégie d’exécution **RemoteSigned** vous empêche d’exécuter des scripts non signés.</span><span class="sxs-lookup"><span data-stu-id="44c4e-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="44c4e-128">Une bonne pratique consiste à lire le code du script et à vérifier qu’il est sûr **avant** d’utiliser l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="44c4e-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="44c4e-129">L' `Unblock-File` applet de commande débloque les scripts pour qu’ils puissent s’exécuter, mais ne modifie pas la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="44c4e-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="44c4e-130">`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** .</span><span class="sxs-lookup"><span data-stu-id="44c4e-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="44c4e-131">La stratégie est définie pour l’étendue par défaut, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-131">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="44c4e-132">L' `Get-ExecutionPolicy` applet de commande montre que **RemoteSigned** est la stratégie d’exécution effective pour la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="44c4e-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="44c4e-133">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="44c4e-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="44c4e-134">Le script est bloqué par **RemoteSigned** car le script n’est pas signé numériquement.</span><span class="sxs-lookup"><span data-stu-id="44c4e-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="44c4e-135">Pour cet exemple, le code du script a été révisé et vérifié comme étant sécurisé pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="44c4e-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="44c4e-136">L' `Unblock-File` applet de commande utilise le paramètre **path** pour débloquer le script.</span><span class="sxs-lookup"><span data-stu-id="44c4e-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="44c4e-137">Pour vérifier que `Unblock-File` la stratégie d’exécution n’a pas été modifiée, `Get-ExecutionPolicy` affiche la stratégie d’exécution effective, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="44c4e-138">Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="44c4e-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="44c4e-139">Le script commence à s’exécuter, car il a été débloqué par l’applet de commande `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="44c4e-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="44c4e-140">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="44c4e-140">PARAMETERS</span></span>

### <span data-ttu-id="44c4e-141">-List</span><span class="sxs-lookup"><span data-stu-id="44c4e-141">-List</span></span>

<span data-ttu-id="44c4e-142">Obtient toutes les valeurs de stratégie d'exécution pour la session dans l'ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="44c4e-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="44c4e-143">Par défaut, `Get-ExecutionPolicy` obtient uniquement la stratégie d’exécution effective.</span><span class="sxs-lookup"><span data-stu-id="44c4e-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="44c4e-144">-Étendue</span><span class="sxs-lookup"><span data-stu-id="44c4e-144">-Scope</span></span>

<span data-ttu-id="44c4e-145">Spécifie l’étendue qui est affectée par une stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="44c4e-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="44c4e-146">La stratégie d’exécution effective est déterminée par l’ordre de priorité comme suit :</span><span class="sxs-lookup"><span data-stu-id="44c4e-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="44c4e-147">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-147">**MachinePolicy**.</span></span> <span data-ttu-id="44c4e-148">Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44c4e-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="44c4e-149">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-149">**UserPolicy**.</span></span> <span data-ttu-id="44c4e-150">Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44c4e-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="44c4e-151">**Processus**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-151">**Process**.</span></span> <span data-ttu-id="44c4e-152">Affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="44c4e-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="44c4e-153">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-153">**CurrentUser**.</span></span> <span data-ttu-id="44c4e-154">Affecte uniquement l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="44c4e-154">Affects only the current user.</span></span>
- <span data-ttu-id="44c4e-155">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="44c4e-155">**LocalMachine**.</span></span> <span data-ttu-id="44c4e-156">Étendue par défaut qui affecte tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44c4e-156">Default scope that affects all users of the computer.</span></span>

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

### <span data-ttu-id="44c4e-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44c4e-157">CommonParameters</span></span>

<span data-ttu-id="44c4e-158">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44c4e-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44c4e-159">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44c4e-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44c4e-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="44c4e-160">INPUTS</span></span>

### <span data-ttu-id="44c4e-161">Aucun</span><span class="sxs-lookup"><span data-stu-id="44c4e-161">None</span></span>

<span data-ttu-id="44c4e-162">`Get-ExecutionPolicy` n’accepte pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="44c4e-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="44c4e-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="44c4e-163">OUTPUTS</span></span>

### <span data-ttu-id="44c4e-164">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="44c4e-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

<span data-ttu-id="44c4e-165">L’applet de commande retourne toujours les plateformes non **restreintes** sur les plateformes Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="44c4e-165">The cmdlet always returns **Unrestricted** on Linux and macOS platforms.</span></span>

## <span data-ttu-id="44c4e-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="44c4e-166">NOTES</span></span>

<span data-ttu-id="44c4e-167">Une stratégie d’exécution fait partie de la stratégie de sécurité PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44c4e-167">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="44c4e-168">Les stratégies d’exécution déterminent si vous pouvez charger des fichiers de configuration, tels que votre profil PowerShell, ou exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="44c4e-168">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="44c4e-169">Et si les scripts doivent être signés numériquement avant leur exécution.</span><span class="sxs-lookup"><span data-stu-id="44c4e-169">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="44c4e-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="44c4e-170">RELATED LINKS</span></span>

[<span data-ttu-id="44c4e-171">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="44c4e-171">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="44c4e-172">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="44c4e-172">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="44c4e-173">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="44c4e-173">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="44c4e-174">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="44c4e-174">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="44c4e-175">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="44c4e-175">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

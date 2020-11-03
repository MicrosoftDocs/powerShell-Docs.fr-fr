---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203566"
---
# <span data-ttu-id="e86c7-103">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-103">Remove-Computer</span></span>

## <span data-ttu-id="e86c7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e86c7-104">SYNOPSIS</span></span>
<span data-ttu-id="e86c7-105">Supprime l’ordinateur local de son domaine.</span><span class="sxs-lookup"><span data-stu-id="e86c7-105">Removes the local computer from its domain.</span></span>

## <span data-ttu-id="e86c7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e86c7-106">SYNTAX</span></span>

### <span data-ttu-id="e86c7-107">Local (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e86c7-107">Local (Default)</span></span>

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e86c7-108">Remote</span><span class="sxs-lookup"><span data-stu-id="e86c7-108">Remote</span></span>

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="e86c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="e86c7-109">DESCRIPTION</span></span>

<span data-ttu-id="e86c7-110">L' `Remove-Computer` applet de commande supprime l’ordinateur local et les ordinateurs distants de leurs domaines actuels.</span><span class="sxs-lookup"><span data-stu-id="e86c7-110">The `Remove-Computer` cmdlet removes the local computer and remote computers from their current domains.</span></span>

<span data-ttu-id="e86c7-111">Lorsque vous supprimez un ordinateur d’un domaine, `Remove-Computer` désactive également le compte de domaine de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e86c7-111">When you remove a computer from a domain, `Remove-Computer` also disables the domain account of the computer.</span></span> <span data-ttu-id="e86c7-112">Vous devez fournir des informations d’identification explicites pour disjoindre l’ordinateur de son domaine, même s’il s’agit des informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e86c7-112">You must provide explicit credentials to unjoin the computer from its domain, even when they are the credentials of the current user.</span></span> <span data-ttu-id="e86c7-113">Vous devez redémarrer l’ordinateur pour que la modification prenne effet.</span><span class="sxs-lookup"><span data-stu-id="e86c7-113">You must restart the computer to make the change effective.</span></span> <span data-ttu-id="e86c7-114">De plus, lorsque vous supprimez un ordinateur d’un domaine, vous devez le déplacer vers un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="e86c7-114">Also, when you remove a computer from a domain, you must move it to a workgroup.</span></span> <span data-ttu-id="e86c7-115">Utilisez le paramètre **WorkgroupName** pour spécifier le groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="e86c7-115">Use the **WorkgroupName** parameter to specify the workgroup.</span></span>

<span data-ttu-id="e86c7-116">Pour déplacer un ordinateur d’un groupe de travail vers un domaine, d’un groupe de travail vers un autre, ou d’un domaine vers un autre, utilisez l’applet de commande `Add-Computer`.</span><span class="sxs-lookup"><span data-stu-id="e86c7-116">To move a computer from a workgroup to a domain, from one workgroup to another, or from one domain to another, use the `Add-Computer` cmdlet.</span></span>

<span data-ttu-id="e86c7-117">Pour obtenir les résultats de la commande, utilisez les paramètres **Verbose** et **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-117">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span> <span data-ttu-id="e86c7-118">Pour supprimer l’invite utilisateur, utilisez le paramètre **Force** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-118">To suppress the user prompt, use the **Force** parameter.</span></span>

<span data-ttu-id="e86c7-119">`Remove-Computer` supprime l’ordinateur local et les ordinateurs distants des domaines.</span><span class="sxs-lookup"><span data-stu-id="e86c7-119">`Remove-Computer` removes the local computer and remote computers from domains.</span></span> <span data-ttu-id="e86c7-120">Elle inclut de nouveaux paramètres d'informations d'identification qui spécifient d'autres informations d'identification pour la connexion à des ordinateurs distants et la disjonction d'un domaine, un nouveau paramètre **Restart** pour le redémarrage des ordinateurs concernés et un paramètre **WorkgroupName** pour la spécification du nom du groupe de travail auquel les ordinateurs sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="e86c7-120">It includes credential parameters that specify alternate credentials for connecting to remote computers, and unjoining from a domain, a **Restart** parameter for restarting the affected computers, and a **WorkgroupName** parameter for specifying the name of the workgroup to which computers are added.</span></span>

## <span data-ttu-id="e86c7-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e86c7-121">EXAMPLES</span></span>

### <span data-ttu-id="e86c7-122">Exemple 1 : supprimer l’ordinateur local de son domaine</span><span class="sxs-lookup"><span data-stu-id="e86c7-122">Example 1: Remove the local computer from its domain</span></span>

<span data-ttu-id="e86c7-123">Cet exemple supprime l’ordinateur local du domaine auquel il est joint.</span><span class="sxs-lookup"><span data-stu-id="e86c7-123">This example removes the local computer from the domain to which it is joined.</span></span>

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

<span data-ttu-id="e86c7-124">Le paramètre **UnjoinDomainCredential** fournit les informations d’identification d’un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="e86c7-124">The **UnjoinDomainCredential** parameter provides the credentials of a domain administrator.</span></span> <span data-ttu-id="e86c7-125">Les paramètres communs **PassThru** et **Verbose** affichent des informations sur la réussite ou l’échec de la commande.</span><span class="sxs-lookup"><span data-stu-id="e86c7-125">The **PassThru** and the **Verbose** common parameters display information about the success or failure of the command.</span></span> <span data-ttu-id="e86c7-126">Le paramètre **restart** redémarre l’ordinateur pour terminer l’opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="e86c7-126">The **Restart** parameter restarts the computer to complete the remove operation.</span></span>

<span data-ttu-id="e86c7-127">Si aucun nom de groupe de travail n’est spécifié, l’ordinateur est déplacé vers le groupe de travail nommé une fois qu’il a été supprimé de son domaine.</span><span class="sxs-lookup"><span data-stu-id="e86c7-127">When no workgroup name is specified, the computer is moved to the workgroup named after it is removed from its domain.</span></span>

### <span data-ttu-id="e86c7-128">Exemple 2 : déplacer plusieurs ordinateurs vers un groupe de travail hérité</span><span class="sxs-lookup"><span data-stu-id="e86c7-128">Example 2: Move several computers to a legacy workgroup</span></span>

<span data-ttu-id="e86c7-129">Cet exemple supprime tous les ordinateurs figurant dans le `OldServers.txt` fichier de leurs domaines et les déplace dans le groupe de travail **hérité** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-129">This example removes all the computers listed in the `OldServers.txt` file from their domains and moves them into the **Legacy** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

<span data-ttu-id="e86c7-130">Le paramètre **LocalCredential** fournit les informations d’identification d’un utilisateur qui a l’autorisation de se connecter à des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="e86c7-130">The **LocalCredential** parameter provides the credentials of a user who has permission to connect to remote computers.</span></span> <span data-ttu-id="e86c7-131">Le paramètre **UnjoinDomainCredential** fournit les informations d’identification d’un utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines.</span><span class="sxs-lookup"><span data-stu-id="e86c7-131">The **UnjoinDomainCredential** parameter provides the credentials of a user who has permission to remove the computers from their domains.</span></span> <span data-ttu-id="e86c7-132">Le paramètre **force** supprime les invites de confirmation pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e86c7-132">The **Force** parameter suppresses the confirmation prompts for each computer.</span></span> <span data-ttu-id="e86c7-133">Le paramètre **restart** redémarre chaque ordinateur après sa suppression de son domaine.</span><span class="sxs-lookup"><span data-stu-id="e86c7-133">The **Restart** parameter restarts each of the computers after it is removed from its domain.</span></span>

### <span data-ttu-id="e86c7-134">Exemple 3 : supprimer des ordinateurs d’un groupe de travail sans confirmation</span><span class="sxs-lookup"><span data-stu-id="e86c7-134">Example 3: Remove computers from a workgroup without confirmation</span></span>

<span data-ttu-id="e86c7-135">Cet exemple supprime l’ordinateur distant, serveur01 et l’ordinateur local de leurs domaines et les ajoute au groupe de travail **local** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-135">This example removes the remote computer, Server01, and the local computer from their domains and adds them to the **Local** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

<span data-ttu-id="e86c7-136">Le paramètre **force** supprime l’invite de confirmation pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e86c7-136">The **Force** parameter suppresses the confirmation prompt for each computer.</span></span> <span data-ttu-id="e86c7-137">Le paramètre **restart** redémarre les ordinateurs pour que la modification prenne effet.</span><span class="sxs-lookup"><span data-stu-id="e86c7-137">The **Restart** parameter restarts the computers to make the change effective.</span></span>

## <span data-ttu-id="e86c7-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e86c7-138">PARAMETERS</span></span>

### <span data-ttu-id="e86c7-139">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e86c7-139">-ComputerName</span></span>

<span data-ttu-id="e86c7-140">Spécifie les ordinateurs à supprimer de leurs domaines.</span><span class="sxs-lookup"><span data-stu-id="e86c7-140">Specifies the computers to be removed from their domains.</span></span> <span data-ttu-id="e86c7-141">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e86c7-141">The default is the local computer.</span></span>

<span data-ttu-id="e86c7-142">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="e86c7-142">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of the remote computers.</span></span> <span data-ttu-id="e86c7-143">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="e86c7-143">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="e86c7-144">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e86c7-144">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="e86c7-145">Vous pouvez utiliser le paramètre **ComputerName** de `Remove-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="e86c7-145">You can use the **ComputerName** parameter of `Remove-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="e86c7-146">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e86c7-146">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e86c7-147">-Force</span><span class="sxs-lookup"><span data-stu-id="e86c7-147">-Force</span></span>

<span data-ttu-id="e86c7-148">Supprime l’invite utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e86c7-148">Suppresses the user prompt.</span></span> <span data-ttu-id="e86c7-149">Par défaut, `Remove-Computer` vous demande confirmation avant de supprimer chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e86c7-149">By default, `Remove-Computer` prompts you for confirmation before removing each computer.</span></span>

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

### <span data-ttu-id="e86c7-150">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="e86c7-150">-LocalCredential</span></span>

<span data-ttu-id="e86c7-151">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs que le paramètre **ComputerName** spécifie.</span><span class="sxs-lookup"><span data-stu-id="e86c7-151">Specifies a user account that has permission to connect to the computers that the **ComputerName** parameter specifies.</span></span> <span data-ttu-id="e86c7-152">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e86c7-152">The default is the current user.</span></span>

<span data-ttu-id="e86c7-153">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e86c7-153">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e86c7-154">Si vous tapez un nom d’utilisateur, l’applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e86c7-154">If you type a user name, the cmdlet prompts you for a password.</span></span> <span data-ttu-id="e86c7-155">Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer l’ordinateur de son domaine actuel, utilisez le paramètre **UnjoinDomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-155">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="e86c7-156">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e86c7-156">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e86c7-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e86c7-157">-PassThru</span></span>

<span data-ttu-id="e86c7-158">Retourne les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="e86c7-158">Returns the results of the command.</span></span> <span data-ttu-id="e86c7-159">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e86c7-159">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e86c7-160">-Restart</span><span class="sxs-lookup"><span data-stu-id="e86c7-160">-Restart</span></span>

<span data-ttu-id="e86c7-161">Indique que cette applet de commande redémarre les ordinateurs qui sont en cours de suppression.</span><span class="sxs-lookup"><span data-stu-id="e86c7-161">Indicates that this cmdlet restarts the computers that are being removed.</span></span> <span data-ttu-id="e86c7-162">Un redémarrage est souvent nécessaire pour que le changement devienne effectif.</span><span class="sxs-lookup"><span data-stu-id="e86c7-162">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="e86c7-163">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e86c7-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e86c7-164">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="e86c7-164">-UnjoinDomainCredential</span></span>

<span data-ttu-id="e86c7-165">Spécifie un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines actuels.</span><span class="sxs-lookup"><span data-stu-id="e86c7-165">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="e86c7-166">Des informations d’identification explicites, fournies par ce paramètre, sont requises pour supprimer les ordinateurs distants d’un domaine, même lorsque la valeur est représentée par les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e86c7-166">Explicit credentials, as provided by this parameter, are required to remove remote computers from a domain, even when the value is the credentials of the current user.</span></span>

<span data-ttu-id="e86c7-167">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e86c7-167">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by `Get-Credential`.</span></span> <span data-ttu-id="e86c7-168">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e86c7-168">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="e86c7-169">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs distants, utilisez le paramètre **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-169">To specify a user account that has permission to connect to the remote computers, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="e86c7-170">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e86c7-170">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e86c7-171">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="e86c7-171">-WorkgroupName</span></span>

<span data-ttu-id="e86c7-172">Spécifie le nom d’un groupe de travail auquel les ordinateurs sont ajoutés lorsqu’ils sont supprimés de leurs domaines.</span><span class="sxs-lookup"><span data-stu-id="e86c7-172">Specifies the name of a workgroup to which the computers are added when they are removed from their domains.</span></span> <span data-ttu-id="e86c7-173">La valeur par défaut est **Workgroup** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-173">The default value is **WORKGROUP** .</span></span> <span data-ttu-id="e86c7-174">Lorsque vous supprimez un ordinateur d’un domaine, vous devez l’ajouter à un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="e86c7-174">When you remove a computer from a domain, you must add it to a workgroup.</span></span>

<span data-ttu-id="e86c7-175">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e86c7-175">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e86c7-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e86c7-176">-Confirm</span></span>

<span data-ttu-id="e86c7-177">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e86c7-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e86c7-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e86c7-178">-WhatIf</span></span>

<span data-ttu-id="e86c7-179">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e86c7-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e86c7-180">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e86c7-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e86c7-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e86c7-181">CommonParameters</span></span>

<span data-ttu-id="e86c7-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e86c7-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e86c7-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e86c7-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e86c7-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e86c7-184">INPUTS</span></span>

### <span data-ttu-id="e86c7-185">System.String</span><span class="sxs-lookup"><span data-stu-id="e86c7-185">System.String</span></span>

<span data-ttu-id="e86c7-186">Vous pouvez diriger les noms d’ordinateurs vers thiscmdlet.</span><span class="sxs-lookup"><span data-stu-id="e86c7-186">You can pipe computer names to thiscmdlet.</span></span>

## <span data-ttu-id="e86c7-187">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e86c7-187">OUTPUTS</span></span>

### <span data-ttu-id="e86c7-188">Microsoft. PowerShell. Commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="e86c7-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="e86c7-189">Quand vous utilisez le paramètre **PassThru** , `Remove-Computer` retourne un objet **ComputerChangeInfo** .</span><span class="sxs-lookup"><span data-stu-id="e86c7-189">When you use the **PassThru** parameter, `Remove-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="e86c7-190">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e86c7-190">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e86c7-191">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e86c7-191">NOTES</span></span>

<span data-ttu-id="e86c7-192">Cette applet de commande ne supprime pas les ordinateurs des groupes de travail.</span><span class="sxs-lookup"><span data-stu-id="e86c7-192">This cmdlet does not remove computers from workgroups.</span></span>

## <span data-ttu-id="e86c7-193">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e86c7-193">RELATED LINKS</span></span>

[<span data-ttu-id="e86c7-194">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-194">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="e86c7-195">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-195">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="e86c7-196">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-196">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="e86c7-197">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-197">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="e86c7-198">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-198">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="e86c7-199">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-199">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="e86c7-200">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="e86c7-200">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="e86c7-201">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="e86c7-201">Test-Connection</span></span>](Test-Connection.md)

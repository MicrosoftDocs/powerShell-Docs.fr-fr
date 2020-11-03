---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203458"
---
# <span data-ttu-id="9623b-103">Test-ComputerSecureChannel</span><span class="sxs-lookup"><span data-stu-id="9623b-103">Test-ComputerSecureChannel</span></span>

## <span data-ttu-id="9623b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9623b-104">SYNOPSIS</span></span>
<span data-ttu-id="9623b-105">Teste et répare le canal sécurisé entre l'ordinateur local et son domaine.</span><span class="sxs-lookup"><span data-stu-id="9623b-105">Tests and repairs the secure channel between the local computer and its domain.</span></span>

## <span data-ttu-id="9623b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9623b-106">SYNTAX</span></span>

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9623b-107">Description</span><span class="sxs-lookup"><span data-stu-id="9623b-107">DESCRIPTION</span></span>
<span data-ttu-id="9623b-108">L’applet de commande **Test-ComputerSecureChannel** vérifie que le canal entre l’ordinateur local et son domaine fonctionne correctement en vérifiant l’état de ses relations d’approbation.</span><span class="sxs-lookup"><span data-stu-id="9623b-108">The **Test-ComputerSecureChannel** cmdlet verifies that the channel between the local computer and its domain is working correctly by checking the status of its trust relationships.</span></span>
<span data-ttu-id="9623b-109">Si une connexion échoue, vous pouvez utiliser le paramètre *Repair* pour essayer de la restaurer.</span><span class="sxs-lookup"><span data-stu-id="9623b-109">If a connection fails, you can use the *Repair* parameter to try to restore it.</span></span>

<span data-ttu-id="9623b-110">**Test-ComputerSecureChannel** retourne $true si le canal fonctionne correctement et $false si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="9623b-110">**Test-ComputerSecureChannel** returns $True if the channel is working correctly and $False if it is not.</span></span>
<span data-ttu-id="9623b-111">Ce résultat vous permet d’utiliser l’applet de commande dans des instructions conditionnelles dans des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="9623b-111">This result lets you use the cmdlet in conditional statements in functions and scripts.</span></span>
<span data-ttu-id="9623b-112">Pour obtenir des résultats de test plus détaillés, utilisez le paramètre *Verbose* .</span><span class="sxs-lookup"><span data-stu-id="9623b-112">To get more detailed test results, use the *Verbose* parameter.</span></span>

<span data-ttu-id="9623b-113">Cette applet de commande fonctionne un peu comme NetDom.exe.</span><span class="sxs-lookup"><span data-stu-id="9623b-113">This cmdlet works much like NetDom.exe.</span></span>
<span data-ttu-id="9623b-114">NetDom et **Test-ComputerSecureChannel** utilisent tous deux le service **Netlogon** pour effectuer les actions.</span><span class="sxs-lookup"><span data-stu-id="9623b-114">Both NetDom and **Test-ComputerSecureChannel** use the **NetLogon** service to perform the actions.</span></span>

## <span data-ttu-id="9623b-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9623b-115">EXAMPLES</span></span>

### <span data-ttu-id="9623b-116">Exemple 1 : tester un canal entre l’ordinateur local et son domaine</span><span class="sxs-lookup"><span data-stu-id="9623b-116">Example 1: Test a channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel
True
```

<span data-ttu-id="9623b-117">Cette commande teste le canal entre l’ordinateur local et le domaine auquel il est joint.</span><span class="sxs-lookup"><span data-stu-id="9623b-117">This command tests the channel between the local computer and the domain to which it is joined.</span></span>

### <span data-ttu-id="9623b-118">Exemple 2 : tester un canal entre l’ordinateur local et un contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="9623b-118">Example 2: Test a channel between the local computer and a domain controller</span></span>

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

<span data-ttu-id="9623b-119">Cette commande spécifie un contrôleur de domaine par défaut pour le test.</span><span class="sxs-lookup"><span data-stu-id="9623b-119">This command specifies a preferred domain controller for the test.</span></span>

### <span data-ttu-id="9623b-120">Exemple 3 : réinitialisation du canal entre l’ordinateur local et son domaine</span><span class="sxs-lookup"><span data-stu-id="9623b-120">Example 3: Reset the channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

<span data-ttu-id="9623b-121">Cette commande réinitialise le canal entre l’ordinateur local et son domaine.</span><span class="sxs-lookup"><span data-stu-id="9623b-121">This command resets the channel between the local computer and its domain.</span></span>

### <span data-ttu-id="9623b-122">Exemple 4 : afficher des informations détaillées sur le test</span><span class="sxs-lookup"><span data-stu-id="9623b-122">Example 4: Display detailed information about the test</span></span>

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

<span data-ttu-id="9623b-123">Cette commande utilise le paramètre commun *Verbose* pour demander des messages détaillés sur l’opération.</span><span class="sxs-lookup"><span data-stu-id="9623b-123">This command uses the *Verbose* common parameter to request detailed messages about the operation.</span></span>
<span data-ttu-id="9623b-124">Pour plus d’informations sur les *Commentaires* , consultez about_CommonParameters.</span><span class="sxs-lookup"><span data-stu-id="9623b-124">For more information about *Verbose* , see about_CommonParameters.</span></span>

### <span data-ttu-id="9623b-125">Exemple 5 : tester une connexion avant d’exécuter un script</span><span class="sxs-lookup"><span data-stu-id="9623b-125">Example 5: Test a connection before you run a script</span></span>

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

<span data-ttu-id="9623b-126">Cet exemple montre comment utiliser **Test-ComputerSecureChannel** pour tester une connexion avant d’exécuter un script qui requiert la connexion.</span><span class="sxs-lookup"><span data-stu-id="9623b-126">This example shows how to use **Test-ComputerSecureChannel** to test a connection before you run a script that requires the connection.</span></span>

<span data-ttu-id="9623b-127">La première commande utilise l’applet de commande Set-Alias pour créer un alias pour le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9623b-127">The first command uses the Set-Alias cmdlet to create an alias for the cmdlet name.</span></span>
<span data-ttu-id="9623b-128">Cela permet d’économiser de l’espace et d’éviter les erreurs de frappe.</span><span class="sxs-lookup"><span data-stu-id="9623b-128">This saves space and prevents typing errors.</span></span>

<span data-ttu-id="9623b-129">L’instruction **If** vérifie la valeur retournée par **Test-ComputerSecureChannel** avant d’exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="9623b-129">The **If** statement checks the value that **Test-ComputerSecureChannel** returns before it runs a script.</span></span>

## <span data-ttu-id="9623b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9623b-130">PARAMETERS</span></span>

### <span data-ttu-id="9623b-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="9623b-131">-Credential</span></span>
<span data-ttu-id="9623b-132">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="9623b-132">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="9623b-133">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="9623b-133">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one that the Get-Credential cmdlet returns.</span></span>
<span data-ttu-id="9623b-134">Par défaut, l'applet de commande utilise les informations d'identification de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9623b-134">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="9623b-135">Le paramètre *Credential* est conçu pour être utilisé dans les commandes qui utilisent le paramètre *Repair* pour réparer le canal entre l’ordinateur et le domaine.</span><span class="sxs-lookup"><span data-stu-id="9623b-135">The *Credential* parameter is designed for use in commands that use the *Repair* parameter to repair the channel between the computer and the domain.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9623b-136">-Repair</span><span class="sxs-lookup"><span data-stu-id="9623b-136">-Repair</span></span>
<span data-ttu-id="9623b-137">Indique que cette applet de commande supprime, puis reconstruit le canal établi par le service Netlogon.</span><span class="sxs-lookup"><span data-stu-id="9623b-137">Indicates that this cmdlet removes and then rebuilds the channel established by the NetLogon service.</span></span>
<span data-ttu-id="9623b-138">Utilisez ce paramètre pour essayer de restaurer une connexion dont le test a échoué.</span><span class="sxs-lookup"><span data-stu-id="9623b-138">Use this parameter to try to restore a connection that has failed the test.</span></span>

<span data-ttu-id="9623b-139">Pour utiliser ce paramètre, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9623b-139">To use this parameter, the current user must be a member of the Administrators group on the local computer.</span></span>

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

### <span data-ttu-id="9623b-140">-Server</span><span class="sxs-lookup"><span data-stu-id="9623b-140">-Server</span></span>
<span data-ttu-id="9623b-141">Spécifie le contrôleur de domaine pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="9623b-141">Specifies the domain controller to run the command.</span></span>
<span data-ttu-id="9623b-142">Si ce paramètre n’est pas spécifié, cette applet de commande sélectionne un contrôleur de domaine par défaut pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="9623b-142">If this parameter is not specified, this cmdlet selects a default domain controller for the operation.</span></span>

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

### <span data-ttu-id="9623b-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9623b-143">-Confirm</span></span>
<span data-ttu-id="9623b-144">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9623b-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9623b-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9623b-145">-WhatIf</span></span>
<span data-ttu-id="9623b-146">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9623b-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9623b-147">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9623b-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9623b-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9623b-148">CommonParameters</span></span>
<span data-ttu-id="9623b-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9623b-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9623b-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9623b-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9623b-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9623b-151">INPUTS</span></span>

### <span data-ttu-id="9623b-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="9623b-152">None</span></span>
<span data-ttu-id="9623b-153">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9623b-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9623b-154">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9623b-154">OUTPUTS</span></span>

### <span data-ttu-id="9623b-155">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="9623b-155">System.Boolean</span></span>
<span data-ttu-id="9623b-156">Cette applet de commande retourne $True si la connexion fonctionne correctement et $False si elle ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="9623b-156">This cmdlet returns $True if the connection is working correctly and $False if it is not.</span></span>

## <span data-ttu-id="9623b-157">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9623b-157">NOTES</span></span>

* <span data-ttu-id="9623b-158">Pour exécuter une commande **Test-ComputerSecureChannel** sur Windows Vista et les versions ultérieures du système d’exploitation Windows, ouvrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="9623b-158">To run a **Test-ComputerSecureChannel** command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="9623b-159">**Test-ComputerSecureChannel** est implémenté à l’aide de la fonction **I_NetLogonControl2** , qui contrôle différents aspects du service Netlogon.</span><span class="sxs-lookup"><span data-stu-id="9623b-159">**Test-ComputerSecureChannel** is implemented by using the **I_NetLogonControl2** function, which controls various aspects of the Netlogon service.</span></span>

## <span data-ttu-id="9623b-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9623b-160">RELATED LINKS</span></span>

[<span data-ttu-id="9623b-161">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="9623b-161">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="9623b-162">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="9623b-162">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="9623b-163">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="9623b-163">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="9623b-164">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="9623b-164">Stop-Computer</span></span>](Stop-Computer.md)

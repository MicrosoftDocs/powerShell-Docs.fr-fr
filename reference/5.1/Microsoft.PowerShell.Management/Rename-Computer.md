---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 4028978b7d2d5353b7250acac3a3454b2f9d8ee1
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343213"
---
# <span data-ttu-id="37ccf-103">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="37ccf-103">Rename-Computer</span></span>

## <span data-ttu-id="37ccf-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="37ccf-104">SYNOPSIS</span></span>
<span data-ttu-id="37ccf-105">Renomme un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37ccf-105">Renames a computer.</span></span>

## <span data-ttu-id="37ccf-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="37ccf-106">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="37ccf-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="37ccf-107">DESCRIPTION</span></span>

<span data-ttu-id="37ccf-108">L' `Rename-Computer` applet de commande renomme l’ordinateur local ou un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="37ccf-108">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="37ccf-109">Elle renomme un ordinateur dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="37ccf-109">It renames one computer in each command.</span></span>

<span data-ttu-id="37ccf-110">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="37ccf-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="37ccf-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="37ccf-111">EXAMPLES</span></span>

### <span data-ttu-id="37ccf-112">Exemple 1 : renommer l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="37ccf-112">Example 1: Rename the local computer</span></span>

<span data-ttu-id="37ccf-113">Cette commande renomme l’ordinateur local en, puis le `Server044` redémarre pour que la modification soit effective.</span><span class="sxs-lookup"><span data-stu-id="37ccf-113">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="37ccf-114">Exemple 2 : renommer un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="37ccf-114">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="37ccf-115">Cette commande renomme l' `Srv01` ordinateur en `Server001` .</span><span class="sxs-lookup"><span data-stu-id="37ccf-115">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="37ccf-116">L’ordinateur n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="37ccf-116">The computer is not restarted.</span></span>

<span data-ttu-id="37ccf-117">Le paramètre **DomainCredential** spécifie les informations d’identification d’un utilisateur qui a l’autorisation de renommer des ordinateurs dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="37ccf-117">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="37ccf-118">Le paramètre **force** supprime l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="37ccf-118">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="37ccf-119">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="37ccf-119">PARAMETERS</span></span>

### <span data-ttu-id="37ccf-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="37ccf-120">-ComputerName</span></span>

<span data-ttu-id="37ccf-121">Renomme l’ordinateur distant spécifié.</span><span class="sxs-lookup"><span data-stu-id="37ccf-121">Renames the specified remote computer.</span></span>
<span data-ttu-id="37ccf-122">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="37ccf-122">The default is the local computer.</span></span>

<span data-ttu-id="37ccf-123">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="37ccf-123">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="37ccf-124">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou `localhost` .</span><span class="sxs-lookup"><span data-stu-id="37ccf-124">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="37ccf-125">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37ccf-125">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="37ccf-126">Vous pouvez utiliser le paramètre **ComputerName** de `Rename-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="37ccf-126">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="37ccf-127">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="37ccf-127">-DomainCredential</span></span>

<span data-ttu-id="37ccf-128">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter au domaine.</span><span class="sxs-lookup"><span data-stu-id="37ccf-128">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="37ccf-129">Des informations d’identification explicites sont requises pour renommer un ordinateur qui est joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="37ccf-129">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="37ccf-130">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="37ccf-130">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="37ccf-131">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="37ccf-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="37ccf-132">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName** , utilisez le paramètre **LocalCredential**.</span><span class="sxs-lookup"><span data-stu-id="37ccf-132">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

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

### <span data-ttu-id="37ccf-133">-Force</span><span class="sxs-lookup"><span data-stu-id="37ccf-133">-Force</span></span>

<span data-ttu-id="37ccf-134">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="37ccf-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="37ccf-135">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="37ccf-135">-LocalCredential</span></span>

<span data-ttu-id="37ccf-136">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="37ccf-136">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="37ccf-137">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="37ccf-137">The default is the current user.</span></span>

<span data-ttu-id="37ccf-138">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="37ccf-138">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="37ccf-139">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="37ccf-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="37ccf-140">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter au domaine, utilisez le paramètre **DomainCredential**.</span><span class="sxs-lookup"><span data-stu-id="37ccf-140">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37ccf-141">-NewName</span><span class="sxs-lookup"><span data-stu-id="37ccf-141">-NewName</span></span>

<span data-ttu-id="37ccf-142">Spécifie un nouveau nom pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37ccf-142">Specifies a new name for the computer.</span></span>
<span data-ttu-id="37ccf-143">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="37ccf-143">This parameter is required.</span></span>

<span data-ttu-id="37ccf-144">Les noms standard peuvent contenir des lettres ( `a-z` ), ( `A-Z` ), des nombres ( `0-9` ) et des traits d’Union ( `-` ), mais pas d’espaces ni de points ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="37ccf-144">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="37ccf-145">Le nom ne peut pas être entièrement composé de chiffres et ne peut pas comporter plus de 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="37ccf-145">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="37ccf-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="37ccf-146">-PassThru</span></span>

<span data-ttu-id="37ccf-147">Retourne les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="37ccf-147">Returns the results of the command.</span></span>
<span data-ttu-id="37ccf-148">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="37ccf-148">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="37ccf-149">-Protocol</span><span class="sxs-lookup"><span data-stu-id="37ccf-149">-Protocol</span></span>

<span data-ttu-id="37ccf-150">Spécifie le protocole à utiliser pour renommer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37ccf-150">Specifies which protocol to use to rename the computer.</span></span>
<span data-ttu-id="37ccf-151">Les valeurs acceptables pour ce paramètre sont les suivantes : WSMan et DCOM.</span><span class="sxs-lookup"><span data-stu-id="37ccf-151">The acceptable values for this parameter are: WSMan and DCOM.</span></span>
<span data-ttu-id="37ccf-152">La valeur par défaut est DCOM.</span><span class="sxs-lookup"><span data-stu-id="37ccf-152">The default value is DCOM.</span></span>

<span data-ttu-id="37ccf-153">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="37ccf-153">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37ccf-154">-Restart</span><span class="sxs-lookup"><span data-stu-id="37ccf-154">-Restart</span></span>

<span data-ttu-id="37ccf-155">Indique que cette applet de commande redémarre l’ordinateur qui a été renommé.</span><span class="sxs-lookup"><span data-stu-id="37ccf-155">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="37ccf-156">Un redémarrage est souvent nécessaire pour que le changement devienne effectif.</span><span class="sxs-lookup"><span data-stu-id="37ccf-156">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="37ccf-157">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="37ccf-157">-WsmanAuthentication</span></span>

<span data-ttu-id="37ccf-158">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="37ccf-158">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="37ccf-159">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="37ccf-159">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="37ccf-160">**De base**</span><span class="sxs-lookup"><span data-stu-id="37ccf-160">**Basic**</span></span>
- <span data-ttu-id="37ccf-161">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="37ccf-161">**CredSSP**</span></span>
- <span data-ttu-id="37ccf-162">**Par défaut**</span><span class="sxs-lookup"><span data-stu-id="37ccf-162">**Default**</span></span>
- <span data-ttu-id="37ccf-163">**Digest**</span><span class="sxs-lookup"><span data-stu-id="37ccf-163">**Digest**</span></span>
- <span data-ttu-id="37ccf-164">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="37ccf-164">**Kerberos**</span></span>
- <span data-ttu-id="37ccf-165">**Prescrit**</span><span class="sxs-lookup"><span data-stu-id="37ccf-165">**Negotiate**</span></span>

<span data-ttu-id="37ccf-166">La valeur par défaut est **Default**.</span><span class="sxs-lookup"><span data-stu-id="37ccf-166">The default value is **Default**.</span></span>

<span data-ttu-id="37ccf-167">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="37ccf-167">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="37ccf-168">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="37ccf-168">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="37ccf-169">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="37ccf-169">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="37ccf-170">Si l’ordinateur distant est compromis, les informations d’identification qui lui sont transmises peuvent être utilisées pour contrôler > la session réseau.</span><span class="sxs-lookup"><span data-stu-id="37ccf-170">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="37ccf-171">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="37ccf-171">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37ccf-172">-Confirm</span><span class="sxs-lookup"><span data-stu-id="37ccf-172">-Confirm</span></span>

<span data-ttu-id="37ccf-173">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="37ccf-173">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="37ccf-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="37ccf-174">-WhatIf</span></span>

<span data-ttu-id="37ccf-175">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="37ccf-175">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="37ccf-176">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="37ccf-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="37ccf-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37ccf-177">CommonParameters</span></span>

<span data-ttu-id="37ccf-178">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="37ccf-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37ccf-179">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="37ccf-179">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="37ccf-180">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="37ccf-180">INPUTS</span></span>

### <span data-ttu-id="37ccf-181">Aucun</span><span class="sxs-lookup"><span data-stu-id="37ccf-181">None</span></span>

<span data-ttu-id="37ccf-182">Cette applet de commande n’a pas de paramètres qui acceptent une entrée par valeur.</span><span class="sxs-lookup"><span data-stu-id="37ccf-182">This cmdlet does not have parameters that take input by value.</span></span> <span data-ttu-id="37ccf-183">Toutefois, vous pouvez diriger les valeurs des propriétés **ComputerName** et **NewName** des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="37ccf-183">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="37ccf-184">SORTIES</span><span class="sxs-lookup"><span data-stu-id="37ccf-184">OUTPUTS</span></span>

### <span data-ttu-id="37ccf-185">Microsoft. PowerShell. Commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="37ccf-185">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="37ccf-186">Cette applet de commande retourne un objet **ComputerChangeInfo** , si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="37ccf-186">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="37ccf-187">Sinon, elle ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="37ccf-187">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="37ccf-188">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="37ccf-188">NOTES</span></span>

## <span data-ttu-id="37ccf-189">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="37ccf-189">RELATED LINKS</span></span>

[<span data-ttu-id="37ccf-190">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="37ccf-190">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="37ccf-191">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="37ccf-191">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="37ccf-192">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="37ccf-192">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="37ccf-193">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="37ccf-193">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="37ccf-194">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="37ccf-194">Stop-Computer</span></span>](Stop-Computer.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 070a428530f4f3eecceb0ae3f520ad565097c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596738"
---
# <span data-ttu-id="5d7d5-102">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="5d7d5-102">Rename-Computer</span></span>

## <span data-ttu-id="5d7d5-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5d7d5-103">SYNOPSIS</span></span>
<span data-ttu-id="5d7d5-104">Renomme un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-104">Renames a computer.</span></span>

## <span data-ttu-id="5d7d5-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5d7d5-105">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5d7d5-106">Description</span><span class="sxs-lookup"><span data-stu-id="5d7d5-106">DESCRIPTION</span></span>

<span data-ttu-id="5d7d5-107">L' `Rename-Computer` applet de commande renomme l’ordinateur local ou un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-107">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="5d7d5-108">Elle renomme un ordinateur dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-108">It renames one computer in each command.</span></span>

<span data-ttu-id="5d7d5-109">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5d7d5-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5d7d5-110">EXAMPLES</span></span>

### <span data-ttu-id="5d7d5-111">Exemple 1 : renommer l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="5d7d5-111">Example 1: Rename the local computer</span></span>

<span data-ttu-id="5d7d5-112">Cette commande renomme l’ordinateur local en, puis le `Server044` redémarre pour que la modification soit effective.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-112">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="5d7d5-113">Exemple 2 : renommer un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="5d7d5-113">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="5d7d5-114">Cette commande renomme l' `Srv01` ordinateur en `Server001` .</span><span class="sxs-lookup"><span data-stu-id="5d7d5-114">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="5d7d5-115">L’ordinateur n’est pas redémarré.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-115">The computer is not restarted.</span></span>

<span data-ttu-id="5d7d5-116">Le paramètre **DomainCredential** spécifie les informations d’identification d’un utilisateur qui a l’autorisation de renommer des ordinateurs dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-116">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="5d7d5-117">Le paramètre **force** supprime l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-117">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="5d7d5-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5d7d5-118">PARAMETERS</span></span>

### <span data-ttu-id="5d7d5-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5d7d5-119">-ComputerName</span></span>

<span data-ttu-id="5d7d5-120">Renomme l’ordinateur distant spécifié.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-120">Renames the specified remote computer.</span></span>
<span data-ttu-id="5d7d5-121">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-121">The default is the local computer.</span></span>

<span data-ttu-id="5d7d5-122">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="5d7d5-123">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou `localhost` .</span><span class="sxs-lookup"><span data-stu-id="5d7d5-123">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="5d7d5-124">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-124">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="5d7d5-125">Vous pouvez utiliser le paramètre **ComputerName** de `Rename-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-125">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="5d7d5-126">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="5d7d5-126">-DomainCredential</span></span>

<span data-ttu-id="5d7d5-127">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter au domaine.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-127">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="5d7d5-128">Des informations d’identification explicites sont requises pour renommer un ordinateur qui est joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-128">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="5d7d5-129">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5d7d5-129">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="5d7d5-130">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-130">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="5d7d5-131">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName**, utilisez le paramètre **LocalCredential**.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-131">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

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

### <span data-ttu-id="5d7d5-132">-Force</span><span class="sxs-lookup"><span data-stu-id="5d7d5-132">-Force</span></span>

<span data-ttu-id="5d7d5-133">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-133">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5d7d5-134">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="5d7d5-134">-LocalCredential</span></span>

<span data-ttu-id="5d7d5-135">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-135">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="5d7d5-136">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-136">The default is the current user.</span></span>

<span data-ttu-id="5d7d5-137">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5d7d5-137">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="5d7d5-138">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="5d7d5-139">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter au domaine, utilisez le paramètre **DomainCredential**.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-139">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

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

### <span data-ttu-id="5d7d5-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="5d7d5-140">-NewName</span></span>

<span data-ttu-id="5d7d5-141">Spécifie un nouveau nom pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-141">Specifies a new name for the computer.</span></span>
<span data-ttu-id="5d7d5-142">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-142">This parameter is required.</span></span>

<span data-ttu-id="5d7d5-143">Les noms standard peuvent contenir des lettres ( `a-z` ), ( `A-Z` ), des nombres ( `0-9` ) et des traits d’Union ( `-` ), mais pas d’espaces ni de points ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="5d7d5-143">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="5d7d5-144">Le nom ne peut pas être entièrement composé de chiffres et ne peut pas comporter plus de 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-144">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

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

### <span data-ttu-id="5d7d5-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5d7d5-145">-PassThru</span></span>

<span data-ttu-id="5d7d5-146">Retourne les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-146">Returns the results of the command.</span></span>
<span data-ttu-id="5d7d5-147">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-147">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5d7d5-148">-Restart</span><span class="sxs-lookup"><span data-stu-id="5d7d5-148">-Restart</span></span>

<span data-ttu-id="5d7d5-149">Indique que cette applet de commande redémarre l’ordinateur qui a été renommé.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-149">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="5d7d5-150">Un redémarrage est souvent nécessaire pour que le changement devienne effectif.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-150">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="5d7d5-151">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="5d7d5-151">-WsmanAuthentication</span></span>

<span data-ttu-id="5d7d5-152">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-152">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="5d7d5-153">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="5d7d5-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5d7d5-154">**De base**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-154">**Basic**</span></span>
- <span data-ttu-id="5d7d5-155">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-155">**CredSSP**</span></span>
- <span data-ttu-id="5d7d5-156">**Par défaut**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-156">**Default**</span></span>
- <span data-ttu-id="5d7d5-157">**Digest**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-157">**Digest**</span></span>
- <span data-ttu-id="5d7d5-158">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-158">**Kerberos**</span></span>
- <span data-ttu-id="5d7d5-159">**Negotiate**</span><span class="sxs-lookup"><span data-stu-id="5d7d5-159">**Negotiate**</span></span>

<span data-ttu-id="5d7d5-160">La valeur par défaut est **Default**.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-160">The default value is **Default**.</span></span>

<span data-ttu-id="5d7d5-161">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="5d7d5-161">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="5d7d5-162">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-162">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="5d7d5-163">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-163">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="5d7d5-164">Si l’ordinateur distant est compromis, les informations d’identification qui lui sont transmises peuvent être utilisées pour contrôler > la session réseau.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-164">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="5d7d5-165">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-165">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5d7d5-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5d7d5-166">-Confirm</span></span>

<span data-ttu-id="5d7d5-167">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5d7d5-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5d7d5-168">-WhatIf</span></span>

<span data-ttu-id="5d7d5-169">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5d7d5-170">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5d7d5-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d7d5-171">CommonParameters</span></span>

<span data-ttu-id="5d7d5-172">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d7d5-173">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5d7d5-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5d7d5-174">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5d7d5-174">INPUTS</span></span>

### <span data-ttu-id="5d7d5-175">None</span><span class="sxs-lookup"><span data-stu-id="5d7d5-175">None</span></span>

<span data-ttu-id="5d7d5-176">Cette applet de commande n’a pas de paramètres qui acceptent une entrée par valeur.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-176">This cmdlet does not have parameters that take input by value.</span></span> <span data-ttu-id="5d7d5-177">Toutefois, vous pouvez diriger les valeurs des propriétés **ComputerName** et **NewName** des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-177">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="5d7d5-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5d7d5-178">OUTPUTS</span></span>

### <span data-ttu-id="5d7d5-179">Microsoft. PowerShell. Commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="5d7d5-179">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="5d7d5-180">Cette applet de commande retourne un objet **ComputerChangeInfo** , si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="5d7d5-180">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="5d7d5-181">Sinon, elle ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-181">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="5d7d5-182">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5d7d5-182">NOTES</span></span>

<span data-ttu-id="5d7d5-183">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="5d7d5-183">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="5d7d5-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5d7d5-184">RELATED LINKS</span></span>

[<span data-ttu-id="5d7d5-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5d7d5-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="5d7d5-186">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="5d7d5-186">Stop-Computer</span></span>](Stop-Computer.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598146"
---
# <span data-ttu-id="ab216-102">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="ab216-102">Stop-Computer</span></span>

## <span data-ttu-id="ab216-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ab216-103">SYNOPSIS</span></span>
<span data-ttu-id="ab216-104">Arrête les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="ab216-104">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="ab216-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ab216-105">SYNTAX</span></span>

### <span data-ttu-id="ab216-106">Tous</span><span class="sxs-lookup"><span data-stu-id="ab216-106">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab216-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab216-107">DESCRIPTION</span></span>

<span data-ttu-id="ab216-108">L' `Stop-Computer` applet de commande arrête l’ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ab216-108">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="ab216-109">Vous pouvez utiliser les paramètres de `Stop-Computer` pour spécifier les niveaux d’authentification et d’autres informations d’identification, et pour forcer l’arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="ab216-109">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="ab216-110">Dans PowerShell 7,1, `Stop-Computer` a été ajouté pour Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="ab216-110">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="ab216-111">Les paramètres n’ont aucun effet sur ces plateformes.</span><span class="sxs-lookup"><span data-stu-id="ab216-111">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="ab216-112">L’applet de commande appelle simplement la commande native `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="ab216-112">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="ab216-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ab216-113">EXAMPLES</span></span>

### <span data-ttu-id="ab216-114">Exemple 1 : arrêter l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="ab216-114">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="ab216-115">Cet exemple arrête l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab216-115">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="ab216-116">Exemple 2 : arrêter deux ordinateurs distants et l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="ab216-116">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="ab216-117">Cet exemple arrête deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab216-117">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="ab216-118">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab216-118">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="ab216-119">Chaque ordinateur est arrêté.</span><span class="sxs-lookup"><span data-stu-id="ab216-119">Each computer is shut down.</span></span>

### <span data-ttu-id="ab216-120">Exemple 3 : arrêter des ordinateurs distants en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="ab216-120">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="ab216-121">Dans cet exemple, `Stop-Computer` s’exécute en tant que tâche en arrière-plan sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ab216-121">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="ab216-122">L’opérateur d’arrière-plan `&` exécute la `Stop-Computer` commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ab216-122">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="ab216-123">Pour plus d’informations, consultez [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="ab216-123">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="ab216-124">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ab216-124">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="ab216-125">L' `&` opérateur d’arrière-plan exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ab216-125">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="ab216-126">Les objets de traitement sont stockés dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-126">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="ab216-127">Les objets de traitement dans la `$j` variable sont envoyés dans le pipeline à `Receive-Job` , qui obtient les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="ab216-127">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="ab216-128">Les objets sont stockés dans la `$results` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-128">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="ab216-129">La `$results` variable affiche les informations sur la tâche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab216-129">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="ab216-130">Exemple 4 : arrêter un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="ab216-130">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="ab216-131">Cet exemple arrête un ordinateur distant à l’aide de l’authentification spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ab216-131">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="ab216-132">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ab216-132">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="ab216-133">Le paramètre **WsmanAuthentication** spécifie d’utiliser Kerberos pour établir une connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="ab216-133">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="ab216-134">Exemple 5 : arrêter des ordinateurs dans un domaine</span><span class="sxs-lookup"><span data-stu-id="ab216-134">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="ab216-135">Dans cet exemple, les commandes forcent l’arrêt immédiat de tous les ordinateurs dans un domaine spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab216-135">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="ab216-136">`Get-Content` utilise le paramètre **path** pour obtenir un fichier dans le répertoire actif avec la liste des ordinateurs du domaine.</span><span class="sxs-lookup"><span data-stu-id="ab216-136">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="ab216-137">Les objets sont stockés dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-137">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="ab216-138">`Get-Credential` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="ab216-138">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="ab216-139">Les informations d’identification sont stockées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-139">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="ab216-140">`Stop-Computer` arrête les ordinateurs spécifiés avec la liste des ordinateurs du paramètre **ComputerName** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-140">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="ab216-141">Le paramètre **force** force un arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="ab216-141">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="ab216-142">Le paramètre **Credential** envoie les informations d’identification enregistrées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="ab216-142">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="ab216-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab216-143">PARAMETERS</span></span>

### <span data-ttu-id="ab216-144">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ab216-144">-ComputerName</span></span>

<span data-ttu-id="ab216-145">Spécifie les ordinateurs à arrêter.</span><span class="sxs-lookup"><span data-stu-id="ab216-145">Specifies the computers to stop.</span></span> <span data-ttu-id="ab216-146">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab216-146">The default is the local computer.</span></span>

<span data-ttu-id="ab216-147">Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ab216-147">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="ab216-148">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur ou localhost.</span><span class="sxs-lookup"><span data-stu-id="ab216-148">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="ab216-149">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab216-149">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="ab216-150">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="ab216-150">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ab216-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab216-151">-Confirm</span></span>

<span data-ttu-id="ab216-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab216-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab216-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="ab216-153">-Credential</span></span>

<span data-ttu-id="ab216-154">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="ab216-154">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="ab216-155">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ab216-155">The default is the current user.</span></span>

<span data-ttu-id="ab216-156">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="ab216-156">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ab216-157">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ab216-157">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="ab216-158">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="ab216-158">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="ab216-159">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="ab216-159">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab216-160">-Force</span><span class="sxs-lookup"><span data-stu-id="ab216-160">-Force</span></span>

<span data-ttu-id="ab216-161">Force l’arrêt immédiat de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ab216-161">Forces an immediate shut down of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab216-162">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="ab216-162">-WsmanAuthentication</span></span>

<span data-ttu-id="ab216-163">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="ab216-163">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="ab216-164">La valeur par défaut est **Default**.</span><span class="sxs-lookup"><span data-stu-id="ab216-164">The default value is **Default**.</span></span>

<span data-ttu-id="ab216-165">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="ab216-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ab216-166">Basic</span><span class="sxs-lookup"><span data-stu-id="ab216-166">Basic</span></span>
- <span data-ttu-id="ab216-167">CredSSP</span><span class="sxs-lookup"><span data-stu-id="ab216-167">CredSSP</span></span>
- <span data-ttu-id="ab216-168">Default</span><span class="sxs-lookup"><span data-stu-id="ab216-168">Default</span></span>
- <span data-ttu-id="ab216-169">Digest</span><span class="sxs-lookup"><span data-stu-id="ab216-169">Digest</span></span>
- <span data-ttu-id="ab216-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="ab216-170">Kerberos</span></span>
- <span data-ttu-id="ab216-171">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="ab216-171">Negotiate.</span></span>

<span data-ttu-id="ab216-172">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="ab216-172">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="ab216-173">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="ab216-173">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="ab216-174">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="ab216-174">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="ab216-175">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="ab216-175">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="ab216-176">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ab216-176">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab216-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab216-177">-WhatIf</span></span>

<span data-ttu-id="ab216-178">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab216-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ab216-179">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ab216-179">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ab216-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab216-180">CommonParameters</span></span>

<span data-ttu-id="ab216-181">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab216-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab216-182">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab216-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab216-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ab216-183">INPUTS</span></span>

### <span data-ttu-id="ab216-184">None</span><span class="sxs-lookup"><span data-stu-id="ab216-184">None</span></span>

<span data-ttu-id="ab216-185">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ab216-185">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ab216-186">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ab216-186">OUTPUTS</span></span>

### <span data-ttu-id="ab216-187">None</span><span class="sxs-lookup"><span data-stu-id="ab216-187">None</span></span>

## <span data-ttu-id="ab216-188">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ab216-188">NOTES</span></span>

<span data-ttu-id="ab216-189">Cette applet de commande utilise la méthode **Win32Shutdown** de la classe WMI **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="ab216-189">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="ab216-190">Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ab216-190">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="ab216-191">Dans PowerShell 7,1, `Stop-Computer` a été ajouté pour Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="ab216-191">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="ab216-192">Pour ces plateformes, l’applet de commande appelle la commande native `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="ab216-192">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="ab216-193">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ab216-193">RELATED LINKS</span></span>

[<span data-ttu-id="ab216-194">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="ab216-194">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="ab216-195">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="ab216-195">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="ab216-196">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="ab216-196">Test-Connection</span></span>](Test-Connection.md)


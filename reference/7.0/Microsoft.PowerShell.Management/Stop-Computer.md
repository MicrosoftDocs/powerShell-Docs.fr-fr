---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 4791f447fbada43830c8e2d41d7f0f2364aecff9
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205489"
---
# <span data-ttu-id="7fdd0-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="7fdd0-103">Stop-Computer</span></span>

## <span data-ttu-id="7fdd0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7fdd0-104">SYNOPSIS</span></span>
<span data-ttu-id="7fdd0-105">Arrête les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="7fdd0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7fdd0-106">SYNTAX</span></span>

### <span data-ttu-id="7fdd0-107">Tous</span><span class="sxs-lookup"><span data-stu-id="7fdd0-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7fdd0-108">Description</span><span class="sxs-lookup"><span data-stu-id="7fdd0-108">DESCRIPTION</span></span>

<span data-ttu-id="7fdd0-109">L' `Stop-Computer` applet de commande arrête l’ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="7fdd0-110">Vous pouvez utiliser les paramètres de `Stop-Computer` pour spécifier les niveaux d’authentification et d’autres informations d’identification, et pour forcer l’arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

## <span data-ttu-id="7fdd0-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7fdd0-111">EXAMPLES</span></span>

### <span data-ttu-id="7fdd0-112">Exemple 1 : arrêter l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="7fdd0-112">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="7fdd0-113">Cet exemple arrête l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-113">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="7fdd0-114">Exemple 2 : arrêter deux ordinateurs distants et l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="7fdd0-114">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="7fdd0-115">Cet exemple arrête deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-115">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="7fdd0-116">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants et l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-116">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="7fdd0-117">Chaque ordinateur est arrêté.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-117">Each computer is shut down.</span></span>

### <span data-ttu-id="7fdd0-118">Exemple 3 : arrêter des ordinateurs distants en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7fdd0-118">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="7fdd0-119">Dans cet exemple, `Stop-Computer` s’exécute en tant que tâche en arrière-plan sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-119">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="7fdd0-120">L’opérateur d’arrière-plan `&` exécute la `Stop-Computer` commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-120">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="7fdd0-121">Pour plus d’informations, consultez [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="7fdd0-121">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="7fdd0-122">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-122">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="7fdd0-123">L' `&` opérateur d’arrière-plan exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-123">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="7fdd0-124">Les objets de traitement sont stockés dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-124">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="7fdd0-125">Les objets de traitement dans la `$j` variable sont envoyés dans le pipeline à `Receive-Job` , qui obtient les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-125">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="7fdd0-126">Les objets sont stockés dans la `$results` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-126">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="7fdd0-127">La `$results` variable affiche les informations sur la tâche dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-127">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="7fdd0-128">Exemple 4 : arrêter un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="7fdd0-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="7fdd0-129">Cet exemple arrête un ordinateur distant à l’aide de l’authentification spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="7fdd0-130">`Stop-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="7fdd0-131">Le paramètre **WsmanAuthentication** spécifie d’utiliser Kerberos pour établir une connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-131">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="7fdd0-132">Exemple 5 : arrêter des ordinateurs dans un domaine</span><span class="sxs-lookup"><span data-stu-id="7fdd0-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="7fdd0-133">Dans cet exemple, les commandes forcent l’arrêt immédiat de tous les ordinateurs dans un domaine spécifié.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="7fdd0-134">`Get-Content` utilise le paramètre **path** pour obtenir un fichier dans le répertoire actif avec la liste des ordinateurs du domaine.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="7fdd0-135">Les objets sont stockés dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="7fdd0-136">`Get-Credential` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="7fdd0-137">Les informations d’identification sont stockées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="7fdd0-138">`Stop-Computer` arrête les ordinateurs spécifiés avec la liste des ordinateurs du paramètre **ComputerName** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="7fdd0-139">Le paramètre **force** force un arrêt immédiat.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="7fdd0-140">Le paramètre **Credential** envoie les informations d’identification enregistrées dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-140">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="7fdd0-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fdd0-141">PARAMETERS</span></span>

### <span data-ttu-id="7fdd0-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7fdd0-142">-ComputerName</span></span>

<span data-ttu-id="7fdd0-143">Spécifie les ordinateurs à arrêter.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-143">Specifies the computers to stop.</span></span> <span data-ttu-id="7fdd0-144">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-144">The default is the local computer.</span></span>

<span data-ttu-id="7fdd0-145">Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-145">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="7fdd0-146">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur ou localhost.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-146">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="7fdd0-147">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-147">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="7fdd0-148">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-148">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="7fdd0-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7fdd0-149">-Confirm</span></span>

<span data-ttu-id="7fdd0-150">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7fdd0-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="7fdd0-151">-Credential</span></span>

<span data-ttu-id="7fdd0-152">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-152">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="7fdd0-153">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-153">The default is the current user.</span></span>

<span data-ttu-id="7fdd0-154">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="7fdd0-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7fdd0-155">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-155">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="7fdd0-156">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="7fdd0-156">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="7fdd0-157">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="7fdd0-157">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="7fdd0-158">-Force</span><span class="sxs-lookup"><span data-stu-id="7fdd0-158">-Force</span></span>

<span data-ttu-id="7fdd0-159">Force l’arrêt immédiat de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-159">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="7fdd0-160">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="7fdd0-160">-WsmanAuthentication</span></span>

<span data-ttu-id="7fdd0-161">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-161">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="7fdd0-162">La valeur par défaut est **Default** .</span><span class="sxs-lookup"><span data-stu-id="7fdd0-162">The default value is **Default** .</span></span>

<span data-ttu-id="7fdd0-163">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7fdd0-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7fdd0-164">Basic</span><span class="sxs-lookup"><span data-stu-id="7fdd0-164">Basic</span></span>
- <span data-ttu-id="7fdd0-165">CredSSP</span><span class="sxs-lookup"><span data-stu-id="7fdd0-165">CredSSP</span></span>
- <span data-ttu-id="7fdd0-166">Default</span><span class="sxs-lookup"><span data-stu-id="7fdd0-166">Default</span></span>
- <span data-ttu-id="7fdd0-167">Digest</span><span class="sxs-lookup"><span data-stu-id="7fdd0-167">Digest</span></span>
- <span data-ttu-id="7fdd0-168">Kerberos</span><span class="sxs-lookup"><span data-stu-id="7fdd0-168">Kerberos</span></span>
- <span data-ttu-id="7fdd0-169">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-169">Negotiate.</span></span>

<span data-ttu-id="7fdd0-170">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="7fdd0-170">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="7fdd0-171">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-171">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="7fdd0-172">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-172">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="7fdd0-173">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-173">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="7fdd0-174">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-174">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7fdd0-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7fdd0-175">-WhatIf</span></span>

<span data-ttu-id="7fdd0-176">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7fdd0-177">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-177">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7fdd0-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fdd0-178">CommonParameters</span></span>

<span data-ttu-id="7fdd0-179">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fdd0-180">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7fdd0-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fdd0-181">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7fdd0-181">INPUTS</span></span>

### <span data-ttu-id="7fdd0-182">Aucun</span><span class="sxs-lookup"><span data-stu-id="7fdd0-182">None</span></span>

<span data-ttu-id="7fdd0-183">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-183">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7fdd0-184">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7fdd0-184">OUTPUTS</span></span>

### <span data-ttu-id="7fdd0-185">Aucun</span><span class="sxs-lookup"><span data-stu-id="7fdd0-185">None</span></span>

## <span data-ttu-id="7fdd0-186">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7fdd0-186">NOTES</span></span>

<span data-ttu-id="7fdd0-187">Cette applet de commande fonctionne uniquement sur Windows et utilise la méthode **Win32Shutdown** de la classe WMI **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="7fdd0-187">This cmdlet only works on Windows and uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="7fdd0-188">Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7fdd0-188">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="7fdd0-189">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7fdd0-189">RELATED LINKS</span></span>

[<span data-ttu-id="7fdd0-190">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="7fdd0-190">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="7fdd0-191">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="7fdd0-191">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="7fdd0-192">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="7fdd0-192">Test-Connection</span></span>](Test-Connection.md)

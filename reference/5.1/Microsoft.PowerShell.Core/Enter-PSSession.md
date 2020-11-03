---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205754"
---
# <span data-ttu-id="21bab-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-103">Enter-PSSession</span></span>

## <span data-ttu-id="21bab-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="21bab-104">SYNOPSIS</span></span>
<span data-ttu-id="21bab-105">Démarre une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="21bab-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21bab-106">SYNTAX</span></span>

### <span data-ttu-id="21bab-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="21bab-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-108">session</span><span class="sxs-lookup"><span data-stu-id="21bab-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-109">Uri</span><span class="sxs-lookup"><span data-stu-id="21bab-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="21bab-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-111">Id</span><span class="sxs-lookup"><span data-stu-id="21bab-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-112">Nom</span><span class="sxs-lookup"><span data-stu-id="21bab-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-113">VMId</span><span class="sxs-lookup"><span data-stu-id="21bab-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="21bab-114">VMName</span><span class="sxs-lookup"><span data-stu-id="21bab-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="21bab-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="21bab-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="21bab-116">Description</span><span class="sxs-lookup"><span data-stu-id="21bab-116">DESCRIPTION</span></span>

<span data-ttu-id="21bab-117">L' `Enter-PSSession` applet de commande démarre une session interactive avec un seul ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span> <span data-ttu-id="21bab-118">Pendant la session, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous tapiez directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="21bab-119">Vous ne pouvez avoir qu'une seule session interactive à la fois.</span><span class="sxs-lookup"><span data-stu-id="21bab-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="21bab-120">En général, vous utilisez le paramètre **ComputerName** pour spécifier le nom de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="21bab-121">Toutefois, vous pouvez également utiliser une session que vous créez à l’aide `New-PSSession` de l’applet de commande pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="21bab-122">Toutefois, vous ne pouvez pas utiliser les `Disconnect-PSSession` applets de commande, ou pour vous déconnecter `Connect-PSSession` ou vous `Receive-PSSession` reconnecter à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="21bab-123">Pour mettre fin à la session interactive et vous déconnecter de l’ordinateur distant, utilisez l’applet de commande `Exit-PSSession` ou tapez `exit` .</span><span class="sxs-lookup"><span data-stu-id="21bab-123">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="21bab-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="21bab-124">EXAMPLES</span></span>

### <span data-ttu-id="21bab-125">Exemple 1 : démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="21bab-125">Example 1: Start an interactive session</span></span>

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

<span data-ttu-id="21bab-126">Cette commande démarre une session interactive sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-126">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="21bab-127">L'invite de commandes change pour vous indiquer que vous exécutez à présent les commandes dans une autre session.</span><span class="sxs-lookup"><span data-stu-id="21bab-127">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="21bab-128">Les commandes que vous entrez s'exécutent dans la nouvelle session. Les résultats sont retournés à la session par défaut sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="21bab-128">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="21bab-129">Exemple 2 : utiliser une session interactive</span><span class="sxs-lookup"><span data-stu-id="21bab-129">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="21bab-130">La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec Serveur01, un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-130">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="21bab-131">Quand la session démarre, l'invite de commandes change pour inclure le nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-131">When the session starts, the command prompt changes to include the computer name.</span></span>
<span data-ttu-id="21bab-132">La deuxième commande récupère le processus Windows PowerShell et redirige la sortie vers le fichier Process.txt.</span><span class="sxs-lookup"><span data-stu-id="21bab-132">The second command gets the Windows PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="21bab-133">La commande est envoyée à l'ordinateur distant, et le fichier est enregistré sur ce dernier.</span><span class="sxs-lookup"><span data-stu-id="21bab-133">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>
<span data-ttu-id="21bab-134">La troisième commande utilise le mot clé **Exit** pour mettre fin à la session interactive et fermer la connexion.</span><span class="sxs-lookup"><span data-stu-id="21bab-134">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="21bab-135">La quatrième commande vérifie que le fichier Process.txt se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-135">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="21bab-136">Une `Get-ChildItem` commande (« dir ») sur l’ordinateur local ne peut pas trouver le fichier.</span><span class="sxs-lookup"><span data-stu-id="21bab-136">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="21bab-137">Cette commande montre comment utiliser une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-137">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="21bab-138">Exemple 3 : utiliser le paramètre de session</span><span class="sxs-lookup"><span data-stu-id="21bab-138">Example 3: Use the Session parameter</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

<span data-ttu-id="21bab-139">Ces commandes utilisent le paramètre **session** de `Enter-PSSession` pour exécuter la session interactive dans une session Windows PowerShell existante ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="21bab-139">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing Windows PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="21bab-140">Exemple 4 : démarrer une session interactive et spécifier les paramètres du port et des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="21bab-140">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

<span data-ttu-id="21bab-141">Cette commande démarre une session interactive sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="21bab-141">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="21bab-142">Elle utilise le paramètre **port** pour spécifier le port et le paramètre **Credential** pour spécifier le compte d’un utilisateur qui a l’autorisation de se connecter à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-142">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="21bab-143">Exemple 5 : arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="21bab-143">Example 5: Stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

<span data-ttu-id="21bab-144">Cet exemple montre comment démarrer et arrêter une session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-144">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="21bab-145">La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="21bab-145">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="21bab-146">La deuxième commande utilise l' `Exit-PSSession` applet de commande pour mettre fin à la session.</span><span class="sxs-lookup"><span data-stu-id="21bab-146">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="21bab-147">Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-147">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="21bab-148">`Exit-PSSession` et **Exit** ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="21bab-148">`Exit-PSSession` and **Exit** have the same effect.</span></span>

## <span data-ttu-id="21bab-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21bab-149">PARAMETERS</span></span>

### <span data-ttu-id="21bab-150">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="21bab-150">-AllowRedirection</span></span>

<span data-ttu-id="21bab-151">Autorise la redirection de cette connexion vers un autre URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="21bab-151">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="21bab-152">Par défaut, la redirection n'est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="21bab-152">By default, redirection is not allowed.</span></span>

<span data-ttu-id="21bab-153">Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="21bab-153">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="21bab-154">Par défaut, Windows PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de le faire.</span><span class="sxs-lookup"><span data-stu-id="21bab-154">By default, Windows PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="21bab-155">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** .</span><span class="sxs-lookup"><span data-stu-id="21bab-155">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="21bab-156">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="21bab-156">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="21bab-157">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="21bab-157">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-158">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="21bab-158">-ApplicationName</span></span>

<span data-ttu-id="21bab-159">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="21bab-159">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="21bab-160">Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre **ConnectionURI** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-160">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="21bab-161">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-161">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="21bab-162">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="21bab-162">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="21bab-163">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="21bab-163">This value is appropriate for most uses.</span></span> <span data-ttu-id="21bab-164">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="21bab-164">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="21bab-165">Le service **WinRM** utilise le nom de l’application pour sélectionner un écouteur afin de traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="21bab-165">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="21bab-166">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-166">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-167">-Authentification</span><span class="sxs-lookup"><span data-stu-id="21bab-167">-Authentication</span></span>

<span data-ttu-id="21bab-168">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-168">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="21bab-169">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="21bab-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="21bab-170">Default</span><span class="sxs-lookup"><span data-stu-id="21bab-170">Default</span></span>
- <span data-ttu-id="21bab-171">Basic</span><span class="sxs-lookup"><span data-stu-id="21bab-171">Basic</span></span>
- <span data-ttu-id="21bab-172">CredSSP</span><span class="sxs-lookup"><span data-stu-id="21bab-172">Credssp</span></span>
- <span data-ttu-id="21bab-173">Digest</span><span class="sxs-lookup"><span data-stu-id="21bab-173">Digest</span></span>
- <span data-ttu-id="21bab-174">Kerberos</span><span class="sxs-lookup"><span data-stu-id="21bab-174">Kerberos</span></span>
- <span data-ttu-id="21bab-175">Negotiate</span><span class="sxs-lookup"><span data-stu-id="21bab-175">Negotiate</span></span>
- <span data-ttu-id="21bab-176">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="21bab-176">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="21bab-177">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="21bab-177">The default value is Default.</span></span>

<span data-ttu-id="21bab-178">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="21bab-178">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="21bab-179">Pour plus d’informations sur les valeurs de ce paramètre, consultez [enum AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="21bab-179">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="21bab-180">ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-180">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="21bab-181">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="21bab-181">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="21bab-182">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="21bab-182">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-183">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="21bab-183">-CertificateThumbprint</span></span>

<span data-ttu-id="21bab-184">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="21bab-184">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="21bab-185">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="21bab-185">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="21bab-186">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="21bab-186">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="21bab-187">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="21bab-187">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="21bab-188">Pour obtenir un certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur Cert : de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21bab-188">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-189">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="21bab-189">-ComputerName</span></span>

<span data-ttu-id="21bab-190">Spécifie un nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-190">Specifies a computer name.</span></span> <span data-ttu-id="21bab-191">Cette applet de commande démarre une session interactive avec l’ordinateur distant spécifié.</span><span class="sxs-lookup"><span data-stu-id="21bab-191">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="21bab-192">Entrez uniquement un nom d'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-192">Enter only one computer name.</span></span> <span data-ttu-id="21bab-193">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-193">The default is the local computer.</span></span>

<span data-ttu-id="21bab-194">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-194">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="21bab-195">Vous pouvez également diriger un nom d’ordinateur vers `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="21bab-195">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="21bab-196">Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="21bab-196">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="21bab-197">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-197">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="21bab-198">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="21bab-198">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="21bab-199">Remarque : dans Windows Vista et les versions ultérieures du système d’exploitation Windows, pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , vous devez démarrer Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-199">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start Windows PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-200">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="21bab-200">-ConfigurationName</span></span>

<span data-ttu-id="21bab-201">Spécifie la configuration de session utilisée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-201">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="21bab-202">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-202">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="21bab-203">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="21bab-203">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="21bab-204">La configuration d'une session se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-204">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="21bab-205">Si la configuration de session spécifiée n'existe pas sur l'ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="21bab-205">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="21bab-206">La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-206">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="21bab-207">Si cette variable de préférence n'est pas définie, la valeur par défaut est Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21bab-207">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="21bab-208">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="21bab-208">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-209">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="21bab-209">-ConnectionUri</span></span>

<span data-ttu-id="21bab-210">Spécifie un URI qui définit le point de terminaison de connexion pour la session.</span><span class="sxs-lookup"><span data-stu-id="21bab-210">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="21bab-211">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="21bab-211">The URI must be fully qualified.</span></span> <span data-ttu-id="21bab-212">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="21bab-212">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="21bab-213">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="21bab-213">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="21bab-214">Si vous ne spécifiez pas un **ConnectionURI** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **Port** et **ApplicationName** pour spécifier les valeurs **ConnectionURI** .</span><span class="sxs-lookup"><span data-stu-id="21bab-214">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="21bab-215">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="21bab-215">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="21bab-216">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée à l’aide des ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="21bab-216">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="21bab-217">Pour utiliser les ports par défaut pour la communication à distance Windows PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPS.</span><span class="sxs-lookup"><span data-stu-id="21bab-217">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="21bab-218">Si l'ordinateur de destination redirige la connexion vers un URI différent, Windows PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-218">If the destination computer redirects the connection to a different URI, Windows PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-219">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="21bab-219">-ContainerId</span></span>

<span data-ttu-id="21bab-220">Spécifie l’ID d’un conteneur.</span><span class="sxs-lookup"><span data-stu-id="21bab-220">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-221">-Credential</span><span class="sxs-lookup"><span data-stu-id="21bab-221">-Credential</span></span>

<span data-ttu-id="21bab-222">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="21bab-222">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="21bab-223">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="21bab-223">The default is the current user.</span></span>

<span data-ttu-id="21bab-224">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="21bab-224">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="21bab-225">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="21bab-225">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="21bab-226">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="21bab-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="21bab-227">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="21bab-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-228">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="21bab-228">-EnableNetworkAccess</span></span>

<span data-ttu-id="21bab-229">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="21bab-229">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="21bab-230">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="21bab-230">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="21bab-231">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-231">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="21bab-232">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-232">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="21bab-233">Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou affectez-lui la valeur.</span><span class="sxs-lookup"><span data-stu-id="21bab-233">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="21bab-234">(point), localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="21bab-234">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="21bab-235">Par défaut, les sessions de bouclage sont créées à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="21bab-235">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="21bab-236">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="21bab-236">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="21bab-237">Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="21bab-237">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="21bab-238">Vous pouvez également autoriser l'accès à distance dans une session de bouclage à l'aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d'identification de session à d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="21bab-238">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="21bab-239">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="21bab-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-240">-Id</span><span class="sxs-lookup"><span data-stu-id="21bab-240">-Id</span></span>

<span data-ttu-id="21bab-241">Spécifie l'ID d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="21bab-241">Specifies the ID of an existing session.</span></span> <span data-ttu-id="21bab-242">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-242">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="21bab-243">Pour Rechercher l’ID d’une session, utilisez l' `Get-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-243">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-244">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="21bab-244">-InstanceId</span></span>

<span data-ttu-id="21bab-245">Spécifie l'ID d'instance d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="21bab-245">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="21bab-246">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-246">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="21bab-247">L'ID d'instance est un GUID.</span><span class="sxs-lookup"><span data-stu-id="21bab-247">The instance ID is a GUID.</span></span> <span data-ttu-id="21bab-248">Pour Rechercher l’ID d’instance d’une session, utilisez l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="21bab-248">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="21bab-249">Vous pouvez également utiliser les paramètres **session** , **Name** ou **ID** pour spécifier une session existante.</span><span class="sxs-lookup"><span data-stu-id="21bab-249">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="21bab-250">Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="21bab-250">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-251">-Name</span><span class="sxs-lookup"><span data-stu-id="21bab-251">-Name</span></span>

<span data-ttu-id="21bab-252">Spécifie le nom convivial d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="21bab-252">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="21bab-253">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-253">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="21bab-254">Si le nom que vous spécifiez correspond à plusieurs sessions, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="21bab-254">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="21bab-255">Vous pouvez également utiliser les paramètres **session** , **InstanceID** ou **ID** pour spécifier une session existante.</span><span class="sxs-lookup"><span data-stu-id="21bab-255">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="21bab-256">Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="21bab-256">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="21bab-257">Pour établir un nom convivial pour une session, utilisez le paramètre **Name** de l' `New-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-257">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-258">-Port</span><span class="sxs-lookup"><span data-stu-id="21bab-258">-Port</span></span>

<span data-ttu-id="21bab-259">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-259">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="21bab-260">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="21bab-260">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="21bab-261">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="21bab-261">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="21bab-262">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="21bab-262">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="21bab-263">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="21bab-263">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="21bab-264">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="21bab-264">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="21bab-265">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="21bab-265">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="21bab-266">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="21bab-266">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-267">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="21bab-267">-RunAsAdministrator</span></span>

<span data-ttu-id="21bab-268">Indique que la **session PSSession** s’exécute en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="21bab-268">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-269">-Session</span><span class="sxs-lookup"><span data-stu-id="21bab-269">-Session</span></span>

<span data-ttu-id="21bab-270">Spécifie une session Windows PowerShell ( **PSSession** ) à utiliser pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-270">Specifies a Windows PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="21bab-271">Ce paramètre accepte un objet de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-271">This parameter takes a session object.</span></span> <span data-ttu-id="21bab-272">Vous pouvez également utiliser les paramètres **Name** , **InstanceID** ou **ID** pour spécifier une **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="21bab-272">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession** .</span></span>

<span data-ttu-id="21bab-273">Entrez une variable qui contient un objet de session ou une commande qui crée ou obtient un objet de session, tel qu’une `New-PSSession` `Get-PSSession` commande ou.</span><span class="sxs-lookup"><span data-stu-id="21bab-273">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="21bab-274">Vous pouvez également diriger un objet de session vers `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="21bab-274">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="21bab-275">Vous ne pouvez envoyer qu’une seule **session PSSession** à l’aide de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="21bab-275">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="21bab-276">Si vous entrez une variable qui contient plusieurs sessions **PSSession** , la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="21bab-276">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="21bab-277">Lorsque vous utilisez `Exit-PSSession` ou le mot clé **Exit** , la session interactive se termine, mais la session **PSSession** que vous avez créée reste ouverte et disponible.</span><span class="sxs-lookup"><span data-stu-id="21bab-277">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-278">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="21bab-278">-SessionOption</span></span>

<span data-ttu-id="21bab-279">Définit des options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="21bab-279">Sets advanced options for the session.</span></span> <span data-ttu-id="21bab-280">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-280">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="21bab-281">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="21bab-281">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="21bab-282">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-282">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="21bab-283">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-283">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="21bab-284">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="21bab-284">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="21bab-285">Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="21bab-285">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="21bab-286">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="21bab-286">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="21bab-287">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="21bab-287">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-288">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="21bab-288">-UseSSL</span></span>

<span data-ttu-id="21bab-289">Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-289">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="21bab-290">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="21bab-290">By default, SSL is not used.</span></span>

<span data-ttu-id="21bab-291">WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="21bab-291">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="21bab-292">Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="21bab-292">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="21bab-293">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="21bab-293">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-294">-VMId</span><span class="sxs-lookup"><span data-stu-id="21bab-294">-VMId</span></span>

<span data-ttu-id="21bab-295">Spécifie l’ID d’un ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="21bab-295">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-296">-VMName</span><span class="sxs-lookup"><span data-stu-id="21bab-296">-VMName</span></span>

<span data-ttu-id="21bab-297">Spécifie le nom d'un ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="21bab-297">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21bab-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21bab-298">CommonParameters</span></span>

<span data-ttu-id="21bab-299">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21bab-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21bab-300">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="21bab-300">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21bab-301">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="21bab-301">INPUTS</span></span>

### <span data-ttu-id="21bab-302">System. String, System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-302">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="21bab-303">Vous pouvez diriger un nom d’ordinateur, une chaîne ou un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-303">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="21bab-304">SORTIES</span><span class="sxs-lookup"><span data-stu-id="21bab-304">OUTPUTS</span></span>

### <span data-ttu-id="21bab-305">Aucun</span><span class="sxs-lookup"><span data-stu-id="21bab-305">None</span></span>

<span data-ttu-id="21bab-306">L'applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="21bab-306">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="21bab-307">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="21bab-307">NOTES</span></span>

<span data-ttu-id="21bab-308">Pour vous connecter à un ordinateur distant, vous devez être membre du groupe Administrateurs sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="21bab-308">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="21bab-309">Pour démarrer une session interactive sur l’ordinateur local, vous devez démarrer PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="21bab-309">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="21bab-310">Lorsque vous utilisez `Enter-PSSession` , votre profil utilisateur sur l’ordinateur distant est utilisé pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-310">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="21bab-311">Les commandes du profil utilisateur distant, y compris les commandes permettant d’ajouter des modules PowerShell et de changer l’invite de commandes, s’exécutent avant l’affichage de l’invite distante.</span><span class="sxs-lookup"><span data-stu-id="21bab-311">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="21bab-312">`Enter-PSSession` utilise le paramètre de culture de l’interface utilisateur sur l’ordinateur local pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="21bab-312">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="21bab-313">Pour rechercher la culture d’interface utilisateur locale, utilisez la `$UICulture` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="21bab-313">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="21bab-314">`Enter-PSSession` requiert les `Get-Command` applets de commande, `Out-Default` et `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="21bab-314">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="21bab-315">Si ces applets de commande ne sont pas incluses dans la configuration de session sur l’ordinateur distant, les `Enter-PSSession` commandes échouent.</span><span class="sxs-lookup"><span data-stu-id="21bab-315">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="21bab-316">Contrairement `Invoke-Command` à, qui analyse et interprète les commandes avant de les envoyer à l’ordinateur distant, `Enter-PSSession` envoie les commandes directement à l’ordinateur distant sans interprétation.</span><span class="sxs-lookup"><span data-stu-id="21bab-316">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="21bab-317">Si la session que vous souhaitez entrer est occupée à traiter une commande, il peut y avoir un délai avant que PowerShell réponde à la `Enter-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="21bab-317">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="21bab-318">Vous êtes connecté dès que la session est disponible.</span><span class="sxs-lookup"><span data-stu-id="21bab-318">You are connected as soon as the session is available.</span></span> <span data-ttu-id="21bab-319">Pour annuler la `Enter-PSSession` commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="21bab-319">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

## <span data-ttu-id="21bab-320">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="21bab-320">RELATED LINKS</span></span>

[<span data-ttu-id="21bab-321">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-321">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="21bab-322">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-322">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="21bab-323">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="21bab-323">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="21bab-324">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-324">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="21bab-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-325">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="21bab-326">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-326">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="21bab-327">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-327">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="21bab-328">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="21bab-328">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="21bab-329">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="21bab-329">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="21bab-330">about_Remote</span><span class="sxs-lookup"><span data-stu-id="21bab-330">about_Remote</span></span>](About/about_Remote.md)

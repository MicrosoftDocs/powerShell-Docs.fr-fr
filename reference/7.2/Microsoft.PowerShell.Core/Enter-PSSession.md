---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 9c08e78d840815a396b55eb26bf8e21d73cb81aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597334"
---
# <span data-ttu-id="86c68-102">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-102">Enter-PSSession</span></span>

## <span data-ttu-id="86c68-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="86c68-103">SYNOPSIS</span></span>
<span data-ttu-id="86c68-104">Démarre une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-104">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="86c68-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="86c68-105">SYNTAX</span></span>

### <span data-ttu-id="86c68-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="86c68-106">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-107">SSHHost</span><span class="sxs-lookup"><span data-stu-id="86c68-107">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="86c68-108">Session</span><span class="sxs-lookup"><span data-stu-id="86c68-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-109">Uri</span><span class="sxs-lookup"><span data-stu-id="86c68-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="86c68-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-111">Id</span><span class="sxs-lookup"><span data-stu-id="86c68-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-112">Nom</span><span class="sxs-lookup"><span data-stu-id="86c68-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-113">VMId</span><span class="sxs-lookup"><span data-stu-id="86c68-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="86c68-114">VMName</span><span class="sxs-lookup"><span data-stu-id="86c68-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="86c68-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="86c68-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="86c68-116">Description</span><span class="sxs-lookup"><span data-stu-id="86c68-116">DESCRIPTION</span></span>

<span data-ttu-id="86c68-117">L' `Enter-PSSession` applet de commande démarre une session interactive avec un seul ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="86c68-118">Pendant la session, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous tapiez directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="86c68-119">Vous ne pouvez avoir qu'une seule session interactive à la fois.</span><span class="sxs-lookup"><span data-stu-id="86c68-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="86c68-120">En général, vous utilisez le paramètre **ComputerName** pour spécifier le nom de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="86c68-121">Toutefois, vous pouvez également utiliser une session que vous créez à l’aide `New-PSSession` de l’applet de commande pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="86c68-122">Toutefois, vous ne pouvez pas utiliser les `Disconnect-PSSession` applets de commande, ou pour vous déconnecter `Connect-PSSession` ou vous `Receive-PSSession` reconnecter à une session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="86c68-123">À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à un ordinateur distant, si SSH est disponible sur l’ordinateur local et que l’ordinateur distant est configuré avec un point de terminaison SSH PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86c68-123">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="86c68-124">L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle fonctionne sur plusieurs plateformes (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="86c68-124">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="86c68-125">Pour la communication à distance basée sur SSH, vous utilisez le jeu de paramètres **hostname** pour spécifier l’ordinateur distant et les informations de connexion appropriées.</span><span class="sxs-lookup"><span data-stu-id="86c68-125">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="86c68-126">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="86c68-126">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="86c68-127">Pour mettre fin à la session interactive et vous déconnecter de l’ordinateur distant, utilisez l’applet de commande `Exit-PSSession` ou tapez `exit` .</span><span class="sxs-lookup"><span data-stu-id="86c68-127">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="86c68-128">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="86c68-128">EXAMPLES</span></span>

### <span data-ttu-id="86c68-129">Exemple 1 : démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="86c68-129">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="86c68-130">Cette commande démarre une session interactive sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-130">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="86c68-131">L'invite de commandes change pour vous indiquer que vous exécutez à présent les commandes dans une autre session.</span><span class="sxs-lookup"><span data-stu-id="86c68-131">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="86c68-132">Les commandes que vous entrez s'exécutent dans la nouvelle session. Les résultats sont retournés à la session par défaut sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="86c68-132">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="86c68-133">Exemple 2 : utiliser une session interactive</span><span class="sxs-lookup"><span data-stu-id="86c68-133">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="86c68-134">La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec Serveur01, un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-134">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="86c68-135">Quand la session démarre, l'invite de commandes change pour inclure le nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-135">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="86c68-136">La deuxième commande obtient le processus PowerShell et redirige la sortie vers le fichier Process.txt.</span><span class="sxs-lookup"><span data-stu-id="86c68-136">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="86c68-137">La commande est envoyée à l'ordinateur distant, et le fichier est enregistré sur ce dernier.</span><span class="sxs-lookup"><span data-stu-id="86c68-137">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="86c68-138">La troisième commande utilise le mot clé **Exit** pour mettre fin à la session interactive et fermer la connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-138">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="86c68-139">La quatrième commande vérifie que le fichier Process.txt se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-139">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="86c68-140">Une `Get-ChildItem` commande (« dir ») sur l’ordinateur local ne peut pas trouver le fichier.</span><span class="sxs-lookup"><span data-stu-id="86c68-140">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="86c68-141">Cette commande montre comment utiliser une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-141">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="86c68-142">Exemple 3 : utiliser le paramètre de session</span><span class="sxs-lookup"><span data-stu-id="86c68-142">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="86c68-143">Ces commandes utilisent le paramètre **session** de `Enter-PSSession` pour exécuter la session interactive dans une session PowerShell existante (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="86c68-143">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session (**PSSession**).</span></span>

### <span data-ttu-id="86c68-144">Exemple 4 : démarrer une session interactive et spécifier les paramètres du port et des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="86c68-144">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="86c68-145">Cette commande démarre une session interactive sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="86c68-145">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="86c68-146">Elle utilise le paramètre **port** pour spécifier le port et le paramètre **Credential** pour spécifier le compte d’un utilisateur qui a l’autorisation de se connecter à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-146">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="86c68-147">Exemple 5 : arrêter une session interactive</span><span class="sxs-lookup"><span data-stu-id="86c68-147">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="86c68-148">Cet exemple montre comment démarrer et arrêter une session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-148">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="86c68-149">La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="86c68-149">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="86c68-150">La deuxième commande utilise l' `Exit-PSSession` applet de commande pour mettre fin à la session.</span><span class="sxs-lookup"><span data-stu-id="86c68-150">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="86c68-151">Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-151">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="86c68-152">`Exit-PSSession` et **Exit** ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="86c68-152">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="86c68-153">Exemple 6 : démarrer une session interactive à l’aide de SSH</span><span class="sxs-lookup"><span data-stu-id="86c68-153">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="86c68-154">Cet exemple montre comment démarrer une session interactive à l’aide de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="86c68-154">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="86c68-155">Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous recevrez une invite de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="86c68-155">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="86c68-156">Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur une clé SSH.</span><span class="sxs-lookup"><span data-stu-id="86c68-156">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="86c68-157">Exemple 7 : démarrer une session interactive à l’aide de SSH et spécifier le port et la clé d’authentification utilisateur</span><span class="sxs-lookup"><span data-stu-id="86c68-157">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="86c68-158">Cet exemple montre comment démarrer une session interactive à l’aide de SSH.</span><span class="sxs-lookup"><span data-stu-id="86c68-158">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="86c68-159">Elle utilise le paramètre **port** pour spécifier le port à utiliser et le paramètre **keyFilePath** pour spécifier une clé RSA utilisée pour authentifier l’utilisateur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-159">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="86c68-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86c68-160">PARAMETERS</span></span>

### <span data-ttu-id="86c68-161">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="86c68-161">-AllowRedirection</span></span>

<span data-ttu-id="86c68-162">Autorise la redirection de cette connexion vers un autre URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="86c68-162">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="86c68-163">Par défaut, la redirection n'est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="86c68-163">By default, redirection is not allowed.</span></span>

<span data-ttu-id="86c68-164">Quand vous utilisez le paramètre **ConnectionURI**, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="86c68-164">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="86c68-165">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-165">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="86c68-166">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**.</span><span class="sxs-lookup"><span data-stu-id="86c68-166">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="86c68-167">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="86c68-167">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="86c68-168">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="86c68-168">The default value is 5.</span></span>

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

### <span data-ttu-id="86c68-169">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="86c68-169">-ApplicationName</span></span>

<span data-ttu-id="86c68-170">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-170">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="86c68-171">Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre **ConnectionURI** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-171">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="86c68-172">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-172">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="86c68-173">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="86c68-173">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="86c68-174">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="86c68-174">This value is appropriate for most uses.</span></span> <span data-ttu-id="86c68-175">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="86c68-175">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="86c68-176">Le service **WinRM** utilise le nom de l’application pour sélectionner un écouteur afin de traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-176">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="86c68-177">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-177">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="86c68-178">-Authentification</span><span class="sxs-lookup"><span data-stu-id="86c68-178">-Authentication</span></span>

<span data-ttu-id="86c68-179">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-179">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="86c68-180">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="86c68-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="86c68-181">Default</span><span class="sxs-lookup"><span data-stu-id="86c68-181">Default</span></span>
- <span data-ttu-id="86c68-182">Basic</span><span class="sxs-lookup"><span data-stu-id="86c68-182">Basic</span></span>
- <span data-ttu-id="86c68-183">CredSSP</span><span class="sxs-lookup"><span data-stu-id="86c68-183">Credssp</span></span>
- <span data-ttu-id="86c68-184">Digest</span><span class="sxs-lookup"><span data-stu-id="86c68-184">Digest</span></span>
- <span data-ttu-id="86c68-185">Kerberos</span><span class="sxs-lookup"><span data-stu-id="86c68-185">Kerberos</span></span>
- <span data-ttu-id="86c68-186">Negotiate</span><span class="sxs-lookup"><span data-stu-id="86c68-186">Negotiate</span></span>
- <span data-ttu-id="86c68-187">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="86c68-187">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="86c68-188">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="86c68-188">The default value is Default.</span></span>

<span data-ttu-id="86c68-189">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="86c68-189">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="86c68-190">Pour plus d’informations sur les valeurs de ce paramètre, consultez [enum AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="86c68-190">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="86c68-191">ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-191">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="86c68-192">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="86c68-192">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="86c68-193">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="86c68-193">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="86c68-194">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="86c68-194">-CertificateThumbprint</span></span>

<span data-ttu-id="86c68-195">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="86c68-195">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="86c68-196">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="86c68-196">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="86c68-197">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="86c68-197">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="86c68-198">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="86c68-198">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="86c68-199">Pour obtenir un certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :</span><span class="sxs-lookup"><span data-stu-id="86c68-199">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="86c68-200">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="86c68-200">-ComputerName</span></span>

<span data-ttu-id="86c68-201">Spécifie un nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-201">Specifies a computer name.</span></span> <span data-ttu-id="86c68-202">Cette applet de commande démarre une session interactive avec l’ordinateur distant spécifié.</span><span class="sxs-lookup"><span data-stu-id="86c68-202">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="86c68-203">Entrez uniquement un nom d'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-203">Enter only one computer name.</span></span> <span data-ttu-id="86c68-204">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-204">The default is the local computer.</span></span>

<span data-ttu-id="86c68-205">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-205">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="86c68-206">Vous pouvez également diriger un nom d’ordinateur vers `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="86c68-206">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="86c68-207">Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="86c68-207">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="86c68-208">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-208">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="86c68-209">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="86c68-209">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="86c68-210">Remarque : dans Windows Vista et les versions ultérieures du système d’exploitation Windows, pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , vous devez démarrer PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-210">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="86c68-211">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="86c68-211">-ConfigurationName</span></span>

<span data-ttu-id="86c68-212">Spécifie la configuration de session utilisée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-212">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="86c68-213">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-213">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="86c68-214">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="86c68-214">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="86c68-215">Lorsqu’il est utilisé avec SSH, il spécifie le sous-système à utiliser sur la cible, comme défini dans sshd_config.</span><span class="sxs-lookup"><span data-stu-id="86c68-215">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="86c68-216">La valeur par défaut pour SSH est le `powershell` sous-système.</span><span class="sxs-lookup"><span data-stu-id="86c68-216">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="86c68-217">La configuration d'une session se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-217">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="86c68-218">Si la configuration de session spécifiée n'existe pas sur l'ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="86c68-218">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="86c68-219">La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-219">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="86c68-220">Si cette variable de préférence n'est pas définie, la valeur par défaut est Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86c68-220">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="86c68-221">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="86c68-221">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="86c68-222">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="86c68-222">-ConnectionUri</span></span>

<span data-ttu-id="86c68-223">Spécifie un URI qui définit le point de terminaison de connexion pour la session.</span><span class="sxs-lookup"><span data-stu-id="86c68-223">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="86c68-224">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="86c68-224">The URI must be fully qualified.</span></span> <span data-ttu-id="86c68-225">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="86c68-225">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="86c68-226">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="86c68-226">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="86c68-227">Si vous ne spécifiez pas un **ConnectionURI**, vous pouvez utiliser les paramètres **UseSSL**, **ComputerName**, **Port** et **ApplicationName** pour spécifier les valeurs **ConnectionURI**.</span><span class="sxs-lookup"><span data-stu-id="86c68-227">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="86c68-228">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="86c68-228">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="86c68-229">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée à l’aide des ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="86c68-229">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="86c68-230">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="86c68-230">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="86c68-231">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-231">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="86c68-232">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="86c68-232">-ContainerId</span></span>

<span data-ttu-id="86c68-233">Spécifie l’ID d’un conteneur.</span><span class="sxs-lookup"><span data-stu-id="86c68-233">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="86c68-234">-Credential</span><span class="sxs-lookup"><span data-stu-id="86c68-234">-Credential</span></span>

<span data-ttu-id="86c68-235">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="86c68-235">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="86c68-236">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="86c68-236">The default is the current user.</span></span>

<span data-ttu-id="86c68-237">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="86c68-237">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="86c68-238">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="86c68-238">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="86c68-239">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="86c68-239">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="86c68-240">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="86c68-240">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="86c68-241">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="86c68-241">-EnableNetworkAccess</span></span>

<span data-ttu-id="86c68-242">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="86c68-242">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="86c68-243">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="86c68-243">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="86c68-244">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-244">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="86c68-245">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-245">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="86c68-246">Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou affectez-lui la valeur.</span><span class="sxs-lookup"><span data-stu-id="86c68-246">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="86c68-247">(point), localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="86c68-247">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="86c68-248">Par défaut, les sessions de bouclage sont créées à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="86c68-248">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="86c68-249">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="86c68-249">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="86c68-250">Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="86c68-250">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="86c68-251">Vous pouvez également autoriser l'accès à distance dans une session de bouclage à l'aide de la valeur **CredSSP** du paramètre **Authentication**, qui délègue les informations d'identification de session à d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="86c68-251">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="86c68-252">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="86c68-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="86c68-253">-HostName</span><span class="sxs-lookup"><span data-stu-id="86c68-253">-HostName</span></span>

<span data-ttu-id="86c68-254">Spécifie un nom d’ordinateur pour une connexion Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="86c68-254">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="86c68-255">Cela est similaire au paramètre **ComputerName** , à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="86c68-255">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="86c68-256">Ce paramètre prend en charge la spécification du nom d’utilisateur et/ou du port dans le cadre de la valeur de paramètre de nom d’hôte à l’aide du formulaire `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="86c68-256">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="86c68-257">Le nom d’utilisateur et/ou le port spécifié dans le cadre du nom d’hôte est prioritaire sur les `-UserName` `-Port` paramètres et, s’ils sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="86c68-257">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="86c68-258">Cela permet de transmettre plusieurs noms d’ordinateur à ce paramètre, où certains ont des noms d’utilisateur et/ou des ports spécifiques, tandis que d’autres utilisent le nom d’utilisateur et/ou le port à partir des `-UserName` `-Port` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="86c68-258">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="86c68-259">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86c68-259">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-260">-Id</span><span class="sxs-lookup"><span data-stu-id="86c68-260">-Id</span></span>

<span data-ttu-id="86c68-261">Spécifie l'ID d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="86c68-261">Specifies the ID of an existing session.</span></span> <span data-ttu-id="86c68-262">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-262">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="86c68-263">Pour Rechercher l’ID d’une session, utilisez l' `Get-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-263">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="86c68-264">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="86c68-264">-InstanceId</span></span>

<span data-ttu-id="86c68-265">Spécifie l'ID d'instance d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="86c68-265">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="86c68-266">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-266">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="86c68-267">L'ID d'instance est un GUID.</span><span class="sxs-lookup"><span data-stu-id="86c68-267">The instance ID is a GUID.</span></span> <span data-ttu-id="86c68-268">Pour Rechercher l’ID d’instance d’une session, utilisez l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="86c68-268">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="86c68-269">Vous pouvez également utiliser les paramètres **session**, **Name** ou **ID** pour spécifier une session existante.</span><span class="sxs-lookup"><span data-stu-id="86c68-269">You can also use the **Session**, **Name**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="86c68-270">Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="86c68-270">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="86c68-271">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="86c68-271">-KeyFilePath</span></span>

<span data-ttu-id="86c68-272">Spécifie un chemin de fichier de clé utilisé par Secure Shell (SSH) pour authentifier un utilisateur sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-272">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="86c68-273">SSH permet d’effectuer l’authentification des utilisateurs via des clés privées/publiques comme alternative à l’authentification de base par mot de passe.</span><span class="sxs-lookup"><span data-stu-id="86c68-273">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="86c68-274">Si l’ordinateur distant est configuré pour l’authentification de clé, ce paramètre peut être utilisé pour fournir la clé qui identifie l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-274">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="86c68-275">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86c68-275">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-276">-Name</span><span class="sxs-lookup"><span data-stu-id="86c68-276">-Name</span></span>

<span data-ttu-id="86c68-277">Spécifie le nom convivial d'une session existante.</span><span class="sxs-lookup"><span data-stu-id="86c68-277">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="86c68-278">`Enter-PSSession` utilise la session spécifiée pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-278">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="86c68-279">Si le nom que vous spécifiez correspond à plusieurs sessions, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="86c68-279">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="86c68-280">Vous pouvez également utiliser les paramètres **session**, **InstanceID** ou **ID** pour spécifier une session existante.</span><span class="sxs-lookup"><span data-stu-id="86c68-280">You can also use the **Session**, **InstanceID**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="86c68-281">Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="86c68-281">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="86c68-282">Pour établir un nom convivial pour une session, utilisez le paramètre **Name** de l' `New-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-282">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="86c68-283">-Port</span><span class="sxs-lookup"><span data-stu-id="86c68-283">-Port</span></span>

<span data-ttu-id="86c68-284">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-284">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="86c68-285">Dans PowerShell 6,0, ce paramètre était inclus dans le jeu de paramètres de **nom d’hôte** qui prend en charge les connexions Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="86c68-285">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="86c68-286">**WinRM (jeu de paramètres ComputerName)**</span><span class="sxs-lookup"><span data-stu-id="86c68-286">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="86c68-287">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-287">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="86c68-288">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="86c68-288">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="86c68-289">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="86c68-289">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="86c68-290">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="86c68-290">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="86c68-291">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="86c68-291">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="86c68-292">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="86c68-292">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="86c68-293">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="86c68-293">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="86c68-294">**SSH (jeu de paramètres HostName)**</span><span class="sxs-lookup"><span data-stu-id="86c68-294">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="86c68-295">Pour se connecter à un ordinateur distant, l’ordinateur distant doit être configuré avec le service SSH (SSHD) et doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-295">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="86c68-296">Le port par défaut pour SSH est 22.</span><span class="sxs-lookup"><span data-stu-id="86c68-296">The default port for SSH is 22.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-297">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="86c68-297">-RunAsAdministrator</span></span>

<span data-ttu-id="86c68-298">Indique que la **session PSSession** s’exécute en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-298">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="86c68-299">-Session</span><span class="sxs-lookup"><span data-stu-id="86c68-299">-Session</span></span>

<span data-ttu-id="86c68-300">Spécifie une session PowerShell (**PSSession**) à utiliser pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-300">Specifies a PowerShell session (**PSSession**) to use for the interactive session.</span></span> <span data-ttu-id="86c68-301">Ce paramètre accepte un objet de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-301">This parameter takes a session object.</span></span> <span data-ttu-id="86c68-302">Vous pouvez également utiliser les paramètres **Name**, **InstanceID** ou **ID** pour spécifier une **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="86c68-302">You can also use the **Name**, **InstanceID**, or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="86c68-303">Entrez une variable qui contient un objet de session ou une commande qui crée ou obtient un objet de session, tel qu’une `New-PSSession` `Get-PSSession` commande ou.</span><span class="sxs-lookup"><span data-stu-id="86c68-303">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="86c68-304">Vous pouvez également diriger un objet de session vers `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="86c68-304">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="86c68-305">Vous ne pouvez envoyer qu’une seule **session PSSession** à l’aide de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="86c68-305">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="86c68-306">Si vous entrez une variable qui contient plusieurs sessions **PSSession**, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="86c68-306">If you enter a variable that contains more than one **PSSession**, the command fails.</span></span>

<span data-ttu-id="86c68-307">Lorsque vous utilisez `Exit-PSSession` ou le mot clé **Exit** , la session interactive se termine, mais la session **PSSession** que vous avez créée reste ouverte et disponible.</span><span class="sxs-lookup"><span data-stu-id="86c68-307">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="86c68-308">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="86c68-308">-SessionOption</span></span>

<span data-ttu-id="86c68-309">Définit des options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="86c68-309">Sets advanced options for the session.</span></span> <span data-ttu-id="86c68-310">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-310">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="86c68-311">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="86c68-311">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="86c68-312">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-312">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="86c68-313">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-313">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="86c68-314">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="86c68-314">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="86c68-315">Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="86c68-315">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="86c68-316">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="86c68-316">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="86c68-317">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="86c68-317">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="86c68-318">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="86c68-318">-SSHTransport</span></span>

<span data-ttu-id="86c68-319">Indique que la connexion à distance est établie à l’aide d’Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="86c68-319">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="86c68-320">Par défaut, PowerShell utilise Windows WinRM pour se connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-320">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="86c68-321">Ce commutateur force PowerShell à utiliser le jeu de paramètres HostName pour établir une connexion à distance basée sur SSH.</span><span class="sxs-lookup"><span data-stu-id="86c68-321">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="86c68-322">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86c68-322">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-323">-Sous-système</span><span class="sxs-lookup"><span data-stu-id="86c68-323">-Subsystem</span></span>

<span data-ttu-id="86c68-324">Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="86c68-324">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="86c68-325">Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config.</span><span class="sxs-lookup"><span data-stu-id="86c68-325">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="86c68-326">Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="86c68-326">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="86c68-327">Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="86c68-327">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="86c68-328">Si ce paramètre n’est pas utilisé, la valeur par défaut est le sous-système « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="86c68-328">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-329">-UserName</span><span class="sxs-lookup"><span data-stu-id="86c68-329">-UserName</span></span>

<span data-ttu-id="86c68-330">Spécifie le nom d’utilisateur du compte utilisé pour créer une session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-330">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="86c68-331">La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-331">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="86c68-332">Si SSH est configuré pour l’authentification de base par mot de passe, vous êtes invité à entrer le mot de passe de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-332">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="86c68-333">Si SSH est configuré pour l’authentification utilisateur basée sur une clé, un chemin d’accès de fichier de clé peut être fourni via le paramètre **keyFilePath** et aucune invite de mot de passe n’est générée.</span><span class="sxs-lookup"><span data-stu-id="86c68-333">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="86c68-334">Notez que si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre **keyFilePath** n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur aura lieu automatiquement en fonction du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86c68-334">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="86c68-335">Pour plus d’informations, consultez la documentation SSH sur l’authentification des utilisateurs basée sur les clés.</span><span class="sxs-lookup"><span data-stu-id="86c68-335">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="86c68-336">Ce paramètre n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="86c68-336">This is not a required parameter.</span></span> <span data-ttu-id="86c68-337">Si aucun paramètre de **nom d'** utilisateur n’est spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="86c68-337">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="86c68-338">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86c68-338">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="86c68-339">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="86c68-339">-UseSSL</span></span>

<span data-ttu-id="86c68-340">Indique que cette applet de commande utilise le protocole SSL (Secure Sockets Layer) (SSL) pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-340">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="86c68-341">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="86c68-341">By default, SSL is not used.</span></span>

<span data-ttu-id="86c68-342">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="86c68-342">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="86c68-343">Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="86c68-343">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="86c68-344">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="86c68-344">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="86c68-345">-VMId</span><span class="sxs-lookup"><span data-stu-id="86c68-345">-VMId</span></span>

<span data-ttu-id="86c68-346">Spécifie l’ID d’un ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="86c68-346">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="86c68-347">-VMName</span><span class="sxs-lookup"><span data-stu-id="86c68-347">-VMName</span></span>

<span data-ttu-id="86c68-348">Spécifie le nom d'un ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="86c68-348">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="86c68-349">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86c68-349">CommonParameters</span></span>

<span data-ttu-id="86c68-350">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86c68-350">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86c68-351">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="86c68-351">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86c68-352">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="86c68-352">INPUTS</span></span>

### <span data-ttu-id="86c68-353">System. String, System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-353">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="86c68-354">Vous pouvez diriger un nom d’ordinateur, une chaîne ou un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-354">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="86c68-355">SORTIES</span><span class="sxs-lookup"><span data-stu-id="86c68-355">OUTPUTS</span></span>

### <span data-ttu-id="86c68-356">None</span><span class="sxs-lookup"><span data-stu-id="86c68-356">None</span></span>

<span data-ttu-id="86c68-357">L'applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="86c68-357">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="86c68-358">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="86c68-358">NOTES</span></span>

<span data-ttu-id="86c68-359">Pour vous connecter à un ordinateur distant, vous devez être membre du groupe Administrateurs sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="86c68-359">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="86c68-360">Pour démarrer une session interactive sur l’ordinateur local, vous devez démarrer PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="86c68-360">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="86c68-361">Lorsque vous utilisez `Enter-PSSession` , votre profil utilisateur sur l’ordinateur distant est utilisé pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-361">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="86c68-362">Les commandes du profil utilisateur distant, y compris les commandes permettant d’ajouter des modules PowerShell et de changer l’invite de commandes, s’exécutent avant l’affichage de l’invite distante.</span><span class="sxs-lookup"><span data-stu-id="86c68-362">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="86c68-363">`Enter-PSSession` utilise le paramètre de culture de l’interface utilisateur sur l’ordinateur local pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-363">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="86c68-364">Pour rechercher la culture d’interface utilisateur locale, utilisez la `$UICulture` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="86c68-364">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="86c68-365">`Enter-PSSession` requiert les `Get-Command` applets de commande, `Out-Default` et `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="86c68-365">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="86c68-366">Si ces applets de commande ne sont pas incluses dans la configuration de session sur l’ordinateur distant, les `Enter-PSSession` commandes échouent.</span><span class="sxs-lookup"><span data-stu-id="86c68-366">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="86c68-367">Contrairement `Invoke-Command` à, qui analyse et interprète les commandes avant de les envoyer à l’ordinateur distant, `Enter-PSSession` envoie les commandes directement à l’ordinateur distant sans interprétation.</span><span class="sxs-lookup"><span data-stu-id="86c68-367">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="86c68-368">Si la session que vous souhaitez entrer est occupée à traiter une commande, il peut y avoir un délai avant que PowerShell réponde à la `Enter-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="86c68-368">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="86c68-369">Vous êtes connecté dès que la session est disponible.</span><span class="sxs-lookup"><span data-stu-id="86c68-369">You are connected as soon as the session is available.</span></span> <span data-ttu-id="86c68-370">Pour annuler la `Enter-PSSession` commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="86c68-370">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="86c68-371">Le jeu de paramètres **hostname** a été inclus à partir de PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86c68-371">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="86c68-372">Il a été ajouté pour fournir la communication à distance PowerShell basée sur Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="86c68-372">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="86c68-373">SSH et PowerShell sont tous deux pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés.</span><span class="sxs-lookup"><span data-stu-id="86c68-373">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="86c68-374">Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM, et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas.</span><span class="sxs-lookup"><span data-stu-id="86c68-374">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="86c68-375">Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="86c68-375">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="86c68-376">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="86c68-376">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="86c68-377">Avant PowerShell 7.1, la communication à distance via SSH ne prenait pas en charge les sessions à distance de deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="86c68-377">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="86c68-378">Cette fonctionnalité était limitée aux sessions qui utilisaient WinRM.</span><span class="sxs-lookup"><span data-stu-id="86c68-378">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="86c68-379">PowerShell 7.1 permet à `Enter-PSSession` et `Enter-PSHostProcess` de fonctionner dans n’importe quelle session à distance interactive.</span><span class="sxs-lookup"><span data-stu-id="86c68-379">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="86c68-380">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="86c68-380">RELATED LINKS</span></span>

[<span data-ttu-id="86c68-381">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-381">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="86c68-382">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-382">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="86c68-383">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="86c68-383">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="86c68-384">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-384">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="86c68-385">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-385">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="86c68-386">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-386">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="86c68-387">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-387">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="86c68-388">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="86c68-388">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="86c68-389">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="86c68-389">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="86c68-390">about_Remote</span><span class="sxs-lookup"><span data-stu-id="86c68-390">about_Remote</span></span>](About/about_Remote.md)

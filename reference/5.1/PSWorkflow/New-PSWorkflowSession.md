---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202969"
---
# <span data-ttu-id="31c20-103">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="31c20-103">New-PSWorkflowSession</span></span>

## <span data-ttu-id="31c20-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="31c20-104">SYNOPSIS</span></span>
<span data-ttu-id="31c20-105">Crée une session de workflow.</span><span class="sxs-lookup"><span data-stu-id="31c20-105">Creates a workflow session.</span></span>

## <span data-ttu-id="31c20-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31c20-106">SYNTAX</span></span>

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## <span data-ttu-id="31c20-107">Description</span><span class="sxs-lookup"><span data-stu-id="31c20-107">DESCRIPTION</span></span>

<span data-ttu-id="31c20-108">L' `New-PSWorkflowSession` applet de commande crée une session gérée par l’utilisateur ( **PSSession** ) qui est spécialement conçue pour exécuter des workflows Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31c20-108">The `New-PSWorkflowSession` cmdlet creates a user-managed session ( **PSSession** ) that is especially designed for running Windows PowerShell workflows.</span></span> <span data-ttu-id="31c20-109">Elle utilise la configuration de session Microsoft.PowerShell.Workflow, qui inclut les scripts, les fichiers de type et de mise en forme, ainsi que les options requises pour les workflows.</span><span class="sxs-lookup"><span data-stu-id="31c20-109">It uses the Microsoft.PowerShell.Workflow session configuration, which includes scripts, type and formatting files, and options that are required for workflows.</span></span>

<span data-ttu-id="31c20-110">Vous pouvez utiliser `New-PSWorkflowSession` ou son alias, `nwsn` .</span><span class="sxs-lookup"><span data-stu-id="31c20-110">You can use `New-PSWorkflowSession` or its alias, `nwsn`.</span></span>

<span data-ttu-id="31c20-111">Vous pouvez également ajouter des paramètres communs de workflow à cette commande.</span><span class="sxs-lookup"><span data-stu-id="31c20-111">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="31c20-112">Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="31c20-112">For more information about workflow common parameters, see [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="31c20-113">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="31c20-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="31c20-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="31c20-114">EXAMPLES</span></span>

### <span data-ttu-id="31c20-115">Exemple 1 : créer une session de workflow sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="31c20-115">Example 1: Create a workflow session on a remote computer</span></span>

<span data-ttu-id="31c20-116">Cet exemple crée la session **workflowtests** sur l’ordinateur distant ServerNode01.</span><span class="sxs-lookup"><span data-stu-id="31c20-116">This example creates the **WorkflowTests** session on the ServerNode01 remote computer.</span></span>

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

<span data-ttu-id="31c20-117">La valeur du paramètre **SessionOption** est une `New-PSSessionOption` commande qui définit le mode de mise en mémoire tampon de sortie dans la session à **supprimer** .</span><span class="sxs-lookup"><span data-stu-id="31c20-117">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that sets the output buffering mode in the session to **Drop** .</span></span>

### <span data-ttu-id="31c20-118">Exemple 2 : créer des sessions de workflow sur plusieurs ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="31c20-118">Example 2: Create workflow sessions on multiple remote computers</span></span>

<span data-ttu-id="31c20-119">Cet exemple crée des sessions de workflow sur les ordinateurs ServerNode01 et Server12.</span><span class="sxs-lookup"><span data-stu-id="31c20-119">This example creates workflow sessions on the ServerNode01 and Server12 computers.</span></span> <span data-ttu-id="31c20-120">La commande utilise le paramètre **Credential** à exécuter avec les autorisations de l'administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="31c20-120">The command uses the **Credential** parameter to run with the permissions of the domain administrator.</span></span>

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

<span data-ttu-id="31c20-121">La commande utilise le paramètre **ThrottleLimit** pour augmenter le seuil de limitation par commande à 150.</span><span class="sxs-lookup"><span data-stu-id="31c20-121">The command uses the **ThrottleLimit** parameter to increase the per-command throttle limit to 150.</span></span>
<span data-ttu-id="31c20-122">Cette valeur est prioritaire sur la limite de limitation par défaut de 100 qui est définie dans la configuration de session **Microsoft. PowerShell. Workflow** .</span><span class="sxs-lookup"><span data-stu-id="31c20-122">This value takes precedence over the default throttle limit of 100 that is set in the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

## <span data-ttu-id="31c20-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31c20-123">PARAMETERS</span></span>

### <span data-ttu-id="31c20-124">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="31c20-124">-ApplicationName</span></span>

<span data-ttu-id="31c20-125">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="31c20-125">Specifies the application name segment of the connection URI.</span></span>

<span data-ttu-id="31c20-126">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c20-126">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="31c20-127">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="31c20-127">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="31c20-128">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="31c20-128">This value is appropriate for most uses.</span></span> <span data-ttu-id="31c20-129">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="31c20-129">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="31c20-130">Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="31c20-130">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="31c20-131">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="31c20-131">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-132">-Authentification</span><span class="sxs-lookup"><span data-stu-id="31c20-132">-Authentication</span></span>

<span data-ttu-id="31c20-133">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31c20-133">Specifies the mechanism that is used to authenticate the user credentials.</span></span>
<span data-ttu-id="31c20-134">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="31c20-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="31c20-135">Default</span><span class="sxs-lookup"><span data-stu-id="31c20-135">Default</span></span>
- <span data-ttu-id="31c20-136">Basic</span><span class="sxs-lookup"><span data-stu-id="31c20-136">Basic</span></span>
- <span data-ttu-id="31c20-137">CredSSP</span><span class="sxs-lookup"><span data-stu-id="31c20-137">Credssp</span></span>
- <span data-ttu-id="31c20-138">Digest</span><span class="sxs-lookup"><span data-stu-id="31c20-138">Digest</span></span>
- <span data-ttu-id="31c20-139">Kerberos</span><span class="sxs-lookup"><span data-stu-id="31c20-139">Kerberos</span></span>
- <span data-ttu-id="31c20-140">Negotiate</span><span class="sxs-lookup"><span data-stu-id="31c20-140">Negotiate</span></span>
- <span data-ttu-id="31c20-141">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="31c20-141">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="31c20-142">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="31c20-142">The default value is Default.</span></span>

<span data-ttu-id="31c20-143">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="31c20-143">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="31c20-144">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="31c20-144">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="31c20-145">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="31c20-145">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="31c20-146">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="31c20-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="31c20-147">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="31c20-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="31c20-148">-CertificateThumbprint</span></span>

<span data-ttu-id="31c20-149">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="31c20-149">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="31c20-150">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="31c20-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="31c20-151">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="31c20-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="31c20-152">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="31c20-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="31c20-153">Pour obtenir une empreinte numérique de certificat, utilisez l' `Get-Item` applet `Get-ChildItem` de commande ou l’applet de commande dans le lecteur Cert : de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31c20-153">To get a certificate thumbprint, use the `Get-Item` cmdlet or the `Get-ChildItem` cmdlet in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="31c20-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="31c20-154">-ComputerName</span></span>

<span data-ttu-id="31c20-155">Crée une connexion persistante ( **PSSession** ) sur l’ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="31c20-155">Creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="31c20-156">Si vous entrez plusieurs noms d’ordinateur, Windows PowerShell crée plusieurs **sessions PSSession** , une pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c20-156">If you enter multiple computer names, Windows PowerShell creates multiple **PSSessions** , one for each computer.</span></span> <span data-ttu-id="31c20-157">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c20-157">The default is the local computer.</span></span>

<span data-ttu-id="31c20-158">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="31c20-158">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="31c20-159">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="31c20-159">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="31c20-160">Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'utilisateur, le nom de domaine complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="31c20-160">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="31c20-161">Vous pouvez également diriger un nom d’ordinateur, entre guillemets, vers `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="31c20-161">You can also pipe a computer name, in quotation marks to `New-PSWorkflowSession`.</span></span>

<span data-ttu-id="31c20-162">Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="31c20-162">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="31c20-163">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c20-163">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="31c20-164">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="31c20-164">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="31c20-165">-Credential</span></span>

<span data-ttu-id="31c20-166">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="31c20-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="31c20-167">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="31c20-167">The default is the current user.</span></span> <span data-ttu-id="31c20-168">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com , ou entrez un objet **PSCredential** , tel que celui retourné par l' `Get-Credential` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31c20-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com, or enter a **PSCredential** object, such as one returned by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="31c20-169">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="31c20-169">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-170">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="31c20-170">-EnableNetworkAccess</span></span>

<span data-ttu-id="31c20-171">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="31c20-171">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="31c20-172">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="31c20-172">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="31c20-173">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c20-173">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="31c20-174">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c20-174">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="31c20-175">Pour créer une session de bouclage, ne spécifiez pas le paramètre **ComputerName** ou affectez-lui la valeur dot, localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c20-175">To create a loopback session, do not specify the **ComputerName** parameter or set its value to dot, localhost, or the name of the local computer.</span></span>

<span data-ttu-id="31c20-176">Par défaut, les sessions de bouclage sont créées avec un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="31c20-176">By default, loopback sessions are created that have a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="31c20-177">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="31c20-177">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="31c20-178">Si vous spécifiez le paramètre **EnableNetworkAccess** lorsque vous créez une session sur un ordinateur distant, la commande se déroule correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="31c20-178">If you specify the **EnableNetworkAccess** parameter when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="31c20-179">Vous pouvez également autoriser l'accès à distance dans une session de bouclage à l'aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d'identification de session à d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="31c20-179">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="31c20-180">Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, celles créées à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="31c20-180">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="31c20-181">Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="31c20-181">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="31c20-182">Pour plus d'informations, consultez l'applet de commande `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="31c20-182">For more information, see the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="31c20-183">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="31c20-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="31c20-184">-Name</span><span class="sxs-lookup"><span data-stu-id="31c20-184">-Name</span></span>

<span data-ttu-id="31c20-185">Spécifie un nom convivial pour la session de workflow.</span><span class="sxs-lookup"><span data-stu-id="31c20-185">Specifies a friendly name for the workflow session.</span></span> <span data-ttu-id="31c20-186">Vous pouvez utiliser le nom avec d’autres applets de commande, telles que `Get-PSSession` et `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="31c20-186">You can use the name with other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="31c20-187">Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.</span><span class="sxs-lookup"><span data-stu-id="31c20-187">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-188">-Port</span><span class="sxs-lookup"><span data-stu-id="31c20-188">-Port</span></span>

<span data-ttu-id="31c20-189">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="31c20-189">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="31c20-190">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="31c20-190">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="31c20-191">Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPs).</span><span class="sxs-lookup"><span data-stu-id="31c20-191">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="31c20-192">Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="31c20-192">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="31c20-193">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="31c20-193">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="31c20-194">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="31c20-194">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="31c20-195">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="31c20-195">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="31c20-196">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="31c20-196">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-197">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="31c20-197">-SessionOption</span></span>

<span data-ttu-id="31c20-198">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="31c20-198">Specifies advanced options for the session.</span></span> <span data-ttu-id="31c20-199">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="31c20-199">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="31c20-200">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="31c20-200">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="31c20-201">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="31c20-201">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="31c20-202">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="31c20-202">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="31c20-203">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="31c20-203">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="31c20-204">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="31c20-204">For more information about session configurations, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="31c20-205">Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="31c20-205">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="31c20-206">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="31c20-206">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-207">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="31c20-207">-ThrottleLimit</span></span>

<span data-ttu-id="31c20-208">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="31c20-208">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="31c20-209">Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut de la configuration de session **Microsoft. PowerShellWorkflow** , 100, est utilisée.</span><span class="sxs-lookup"><span data-stu-id="31c20-209">If you omit this parameter or enter a value of 0 (zero), the default value for the **Microsoft.PowerShellWorkflow** session configuration, 100, is used.</span></span>

<span data-ttu-id="31c20-210">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c20-210">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31c20-211">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="31c20-211">-UseSSL</span></span>

<span data-ttu-id="31c20-212">Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="31c20-212">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="31c20-213">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="31c20-213">By default, SSL is not used.</span></span>

<span data-ttu-id="31c20-214">WS-Management chiffre tout le contenu Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="31c20-214">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="31c20-215">Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="31c20-215">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="31c20-216">Si vous spécifiez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="31c20-216">If you specify this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="31c20-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31c20-217">CommonParameters</span></span>

<span data-ttu-id="31c20-218">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31c20-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31c20-219">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="31c20-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31c20-220">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="31c20-220">INPUTS</span></span>

### <span data-ttu-id="31c20-221">System. Management. Automation. instances d’exécution. PSSession [], System. String</span><span class="sxs-lookup"><span data-stu-id="31c20-221">System.Management.Automation.Runspaces.PSSession[], System.String</span></span>

<span data-ttu-id="31c20-222">Vous pouvez diriger une session ou un nom d’ordinateur vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31c20-222">You can pipe a session or a computer name to this cmdlet.</span></span>

## <span data-ttu-id="31c20-223">SORTIES</span><span class="sxs-lookup"><span data-stu-id="31c20-223">OUTPUTS</span></span>

### <span data-ttu-id="31c20-224">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="31c20-224">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="31c20-225">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="31c20-225">NOTES</span></span>

<span data-ttu-id="31c20-226">Une `New-PSWorkflowSession` commande est équivalente à la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="31c20-226">A `New-PSWorkflowSession` command is equivalent to the following command:</span></span>

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## <span data-ttu-id="31c20-227">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="31c20-227">RELATED LINKS</span></span>

[<span data-ttu-id="31c20-228">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="31c20-228">Disconnect-PSSession</span></span>](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[<span data-ttu-id="31c20-229">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="31c20-229">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="31c20-230">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="31c20-230">New-PSTransportOption</span></span>](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[<span data-ttu-id="31c20-231">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c20-231">Register-PSSessionConfiguration</span></span>](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[<span data-ttu-id="31c20-232">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="31c20-232">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="31c20-233">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="31c20-233">about_Session_Configurations</span></span>](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[<span data-ttu-id="31c20-234">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="31c20-234">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="31c20-235">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="31c20-235">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)

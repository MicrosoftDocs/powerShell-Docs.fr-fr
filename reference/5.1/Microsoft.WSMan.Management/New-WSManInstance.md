---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: 3936fb0a68b029ca2fcacbd2ab04853fccf09f0c
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208694"
---
# <span data-ttu-id="b18a2-103">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b18a2-103">New-WSManInstance</span></span>

## <span data-ttu-id="b18a2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b18a2-104">SYNOPSIS</span></span>
<span data-ttu-id="b18a2-105">Crée une instance d'une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-105">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="b18a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b18a2-106">SYNTAX</span></span>

### <span data-ttu-id="b18a2-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b18a2-107">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="b18a2-108">URI</span><span class="sxs-lookup"><span data-stu-id="b18a2-108">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="b18a2-109">Description</span><span class="sxs-lookup"><span data-stu-id="b18a2-109">DESCRIPTION</span></span>

<span data-ttu-id="b18a2-110">L' `New-WSManInstance` applet de commande crée une nouvelle instance d’une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-110">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="b18a2-111">Elle utilise un URI de ressource et une valeur définie ou un fichier d'entrée pour créer l'instance de la ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-111">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="b18a2-112">Cette applet de commande utilise la couche de connexion/transport WinRM pour créer l'instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-112">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="b18a2-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b18a2-113">EXAMPLES</span></span>

### <span data-ttu-id="b18a2-114">Exemple 1 : créer un écouteur HTTPs</span><span class="sxs-lookup"><span data-stu-id="b18a2-114">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="b18a2-115">Cette commande crée une instance d'un écouteur HTTPS WS-Management sur toutes les adresses IP.</span><span class="sxs-lookup"><span data-stu-id="b18a2-115">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="b18a2-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b18a2-116">PARAMETERS</span></span>

### <span data-ttu-id="b18a2-117">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="b18a2-117">-ApplicationName</span></span>

<span data-ttu-id="b18a2-118">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-118">Specifies the application name in the connection.</span></span> <span data-ttu-id="b18a2-119">La valeur par défaut du paramètre **applicationName** est **WSMan** .</span><span class="sxs-lookup"><span data-stu-id="b18a2-119">The default value of the **ApplicationName** parameter is **WSMAN** .</span></span> <span data-ttu-id="b18a2-120">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="b18a2-120">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="b18a2-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b18a2-121">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="b18a2-122">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b18a2-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="b18a2-123">Ce paramètre par défaut de **WSMan** est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="b18a2-123">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="b18a2-124">Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b18a2-124">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="b18a2-125">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="b18a2-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-126">-Authentification</span><span class="sxs-lookup"><span data-stu-id="b18a2-126">-Authentication</span></span>

<span data-ttu-id="b18a2-127">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="b18a2-127">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="b18a2-128">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b18a2-128">Possible values are:</span></span>

- <span data-ttu-id="b18a2-129">De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="b18a2-129">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="b18a2-130">Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b18a2-130">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="b18a2-131">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b18a2-131">This is the default.</span></span>
- <span data-ttu-id="b18a2-132">Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.</span><span class="sxs-lookup"><span data-stu-id="b18a2-132">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="b18a2-133">Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="b18a2-133">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="b18a2-134">Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="b18a2-134">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="b18a2-135">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b18a2-135">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="b18a2-136">CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b18a2-136">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="b18a2-137">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="b18a2-137">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="b18a2-138">CredSSP délègue les informations d'identification de l'utilisateur d'un ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b18a2-138">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="b18a2-139">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="b18a2-139">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="b18a2-140">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="b18a2-140">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b18a2-141">-CertificateThumbprint</span></span>

<span data-ttu-id="b18a2-142">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="b18a2-142">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="b18a2-143">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b18a2-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="b18a2-144">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="b18a2-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="b18a2-145">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="b18a2-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="b18a2-146">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :.</span><span class="sxs-lookup"><span data-stu-id="b18a2-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="b18a2-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b18a2-147">-ComputerName</span></span>

<span data-ttu-id="b18a2-148">Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-148">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="b18a2-149">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="b18a2-149">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="b18a2-150">Utilisez le nom de l’ordinateur local, utilisez localhost ou un point ( `.` ) pour spécifier l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b18a2-150">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="b18a2-151">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b18a2-151">The local computer is the default.</span></span> <span data-ttu-id="b18a2-152">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="b18a2-152">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="b18a2-153">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b18a2-153">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-154">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="b18a2-154">-ConnectionURI</span></span>

<span data-ttu-id="b18a2-155">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-155">Specifies the connection endpoint.</span></span>
<span data-ttu-id="b18a2-156">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="b18a2-156">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="b18a2-157">La chaîne suivante est une valeur au format correct pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="b18a2-157">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="b18a2-158">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="b18a2-158">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="b18a2-159">-Credential</span></span>

<span data-ttu-id="b18a2-160">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="b18a2-160">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b18a2-161">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="b18a2-161">The default is the current user.</span></span> <span data-ttu-id="b18a2-162">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ».</span><span class="sxs-lookup"><span data-stu-id="b18a2-162">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="b18a2-163">Ou entrez un objet PSCredential, tel que celui retourné par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b18a2-163">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b18a2-164">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b18a2-164">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-165">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b18a2-165">-FilePath</span></span>

<span data-ttu-id="b18a2-166">Spécifie le chemin d'accès d'un fichier qui est utilisé pour créer une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-166">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="b18a2-167">Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="b18a2-167">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="b18a2-168">Par exemple, la commande suivante utilise le paramètre **file** :</span><span class="sxs-lookup"><span data-stu-id="b18a2-168">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="b18a2-169">Cette commande appelle la méthode **StopService** sur le service Spooler en utilisant l’entrée d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="b18a2-169">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="b18a2-170">Le fichier, `Input.xml` , contient le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="b18a2-170">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### <span data-ttu-id="b18a2-171">-A</span><span class="sxs-lookup"><span data-stu-id="b18a2-171">-OptionSet</span></span>

<span data-ttu-id="b18a2-172">Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="b18a2-172">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="b18a2-173">Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="b18a2-173">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="b18a2-174">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="b18a2-174">Any number of options can be specified.</span></span>

<span data-ttu-id="b18a2-175">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="b18a2-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-176">-Port</span><span class="sxs-lookup"><span data-stu-id="b18a2-176">-Port</span></span>

<span data-ttu-id="b18a2-177">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="b18a2-177">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="b18a2-178">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="b18a2-178">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="b18a2-179">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="b18a2-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="b18a2-180">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre **ComputerName** doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="b18a2-180">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="b18a2-181">Toutefois, si le paramètre **SkipCNCheck** est spécifié dans le cadre du paramètre **SessionOption** , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="b18a2-181">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="b18a2-182">Le paramètre **SkipCNCheck** doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="b18a2-182">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="b18a2-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="b18a2-183">-ResourceURI</span></span>

<span data-ttu-id="b18a2-184">Contient l'URI de l'instance ou de la classe de ressource.</span><span class="sxs-lookup"><span data-stu-id="b18a2-184">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="b18a2-185">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b18a2-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="b18a2-186">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="b18a2-186">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="b18a2-187">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b18a2-187">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="b18a2-188">-SelectorSet</span></span>

<span data-ttu-id="b18a2-189">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="b18a2-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="b18a2-190">Le paramètre **SelectorSet** est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="b18a2-190">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="b18a2-191">La valeur du paramètre **SelectorSet** doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="b18a2-191">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="b18a2-192">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="b18a2-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="b18a2-193">-SessionOption</span></span>

<span data-ttu-id="b18a2-194">Définit un ensemble d'options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b18a2-194">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="b18a2-195">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="b18a2-195">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="b18a2-196">Pour plus d’informations sur les options disponibles, consultez `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="b18a2-196">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b18a2-197">-UseSSL</span></span>

<span data-ttu-id="b18a2-198">Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b18a2-198">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="b18a2-199">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="b18a2-199">By default, SSL is not used.</span></span>

<span data-ttu-id="b18a2-200">WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="b18a2-200">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="b18a2-201">Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="b18a2-201">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="b18a2-202">Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="b18a2-202">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="b18a2-203">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="b18a2-203">-ValueSet</span></span>

<span data-ttu-id="b18a2-204">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b18a2-204">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="b18a2-205">Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="b18a2-205">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="b18a2-206">La valeur du paramètre **ValueSet** doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="b18a2-206">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b18a2-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b18a2-207">CommonParameters</span></span>

<span data-ttu-id="b18a2-208">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b18a2-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b18a2-209">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b18a2-209">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b18a2-210">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b18a2-210">INPUTS</span></span>

### <span data-ttu-id="b18a2-211">Aucun</span><span class="sxs-lookup"><span data-stu-id="b18a2-211">None</span></span>

<span data-ttu-id="b18a2-212">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="b18a2-212">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="b18a2-213">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b18a2-213">OUTPUTS</span></span>

### <span data-ttu-id="b18a2-214">Aucun</span><span class="sxs-lookup"><span data-stu-id="b18a2-214">None</span></span>

<span data-ttu-id="b18a2-215">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b18a2-215">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b18a2-216">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b18a2-216">NOTES</span></span>

<span data-ttu-id="b18a2-217">L' `Set-WmiInstance` applet de commande, une applet de commande Windows Management Instrumentation (WMI), est similaire.</span><span class="sxs-lookup"><span data-stu-id="b18a2-217">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="b18a2-218">`Set-WmiInstance` utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.</span><span class="sxs-lookup"><span data-stu-id="b18a2-218">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="b18a2-219">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b18a2-219">RELATED LINKS</span></span>

[<span data-ttu-id="b18a2-220">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b18a2-220">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b18a2-221">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b18a2-221">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b18a2-222">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b18a2-222">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b18a2-223">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b18a2-223">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b18a2-224">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b18a2-224">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b18a2-225">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b18a2-225">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b18a2-226">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b18a2-226">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b18a2-227">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b18a2-227">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b18a2-228">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b18a2-228">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="b18a2-229">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b18a2-229">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="b18a2-230">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b18a2-230">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="b18a2-231">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b18a2-231">Test-WSMan</span></span>](Test-WSMan.md)

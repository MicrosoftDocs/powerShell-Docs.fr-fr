---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: dd0343e9b6014e079c322309b699874683bacd6a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598144"
---
# <span data-ttu-id="73b8b-102">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="73b8b-102">New-WSManInstance</span></span>

## <span data-ttu-id="73b8b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="73b8b-103">SYNOPSIS</span></span>
<span data-ttu-id="73b8b-104">Crée une instance d'une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-104">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="73b8b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="73b8b-105">SYNTAX</span></span>

### <span data-ttu-id="73b8b-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="73b8b-106">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="73b8b-107">URI</span><span class="sxs-lookup"><span data-stu-id="73b8b-107">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="73b8b-108">Description</span><span class="sxs-lookup"><span data-stu-id="73b8b-108">DESCRIPTION</span></span>

<span data-ttu-id="73b8b-109">L' `New-WSManInstance` applet de commande crée une nouvelle instance d’une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-109">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="73b8b-110">Elle utilise un URI de ressource et une valeur définie ou un fichier d'entrée pour créer l'instance de la ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-110">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="73b8b-111">Cette applet de commande utilise la couche de connexion/transport WinRM pour créer l'instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-111">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="73b8b-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="73b8b-112">EXAMPLES</span></span>

### <span data-ttu-id="73b8b-113">Exemple 1 : créer un écouteur HTTPs</span><span class="sxs-lookup"><span data-stu-id="73b8b-113">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="73b8b-114">Cette commande crée une instance d'un écouteur HTTPS WS-Management sur toutes les adresses IP.</span><span class="sxs-lookup"><span data-stu-id="73b8b-114">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="73b8b-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73b8b-115">PARAMETERS</span></span>

### <span data-ttu-id="73b8b-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="73b8b-116">-ApplicationName</span></span>

<span data-ttu-id="73b8b-117">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-117">Specifies the application name in the connection.</span></span> <span data-ttu-id="73b8b-118">La valeur par défaut du paramètre **applicationName** est **WSMan**.</span><span class="sxs-lookup"><span data-stu-id="73b8b-118">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="73b8b-119">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="73b8b-119">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="73b8b-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="73b8b-120">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="73b8b-121">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73b8b-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="73b8b-122">Ce paramètre par défaut de **WSMan** est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="73b8b-122">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="73b8b-123">Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73b8b-123">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="73b8b-124">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="73b8b-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="73b8b-125">-Authentification</span><span class="sxs-lookup"><span data-stu-id="73b8b-125">-Authentication</span></span>

<span data-ttu-id="73b8b-126">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="73b8b-126">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="73b8b-127">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73b8b-127">Possible values are:</span></span>

- <span data-ttu-id="73b8b-128">De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="73b8b-128">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="73b8b-129">Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="73b8b-129">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="73b8b-130">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="73b8b-130">This is the default.</span></span>
- <span data-ttu-id="73b8b-131">Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.</span><span class="sxs-lookup"><span data-stu-id="73b8b-131">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="73b8b-132">Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="73b8b-132">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="73b8b-133">Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="73b8b-133">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="73b8b-134">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="73b8b-134">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="73b8b-135">CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="73b8b-135">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="73b8b-136">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="73b8b-136">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="73b8b-137">CredSSP délègue les informations d'identification de l'utilisateur d'un ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="73b8b-137">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="73b8b-138">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="73b8b-138">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="73b8b-139">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="73b8b-139">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="73b8b-140">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="73b8b-140">-CertificateThumbprint</span></span>

<span data-ttu-id="73b8b-141">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="73b8b-141">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="73b8b-142">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="73b8b-142">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="73b8b-143">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="73b8b-143">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="73b8b-144">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="73b8b-144">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="73b8b-145">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :.</span><span class="sxs-lookup"><span data-stu-id="73b8b-145">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="73b8b-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="73b8b-146">-ComputerName</span></span>

<span data-ttu-id="73b8b-147">Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-147">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="73b8b-148">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="73b8b-148">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="73b8b-149">Utilisez le nom de l’ordinateur local, utilisez localhost ou un point ( `.` ) pour spécifier l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="73b8b-149">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="73b8b-150">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="73b8b-150">The local computer is the default.</span></span> <span data-ttu-id="73b8b-151">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="73b8b-151">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="73b8b-152">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73b8b-152">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="73b8b-153">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="73b8b-153">-ConnectionURI</span></span>

<span data-ttu-id="73b8b-154">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-154">Specifies the connection endpoint.</span></span>
<span data-ttu-id="73b8b-155">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="73b8b-155">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="73b8b-156">La chaîne suivante est une valeur au format correct pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="73b8b-156">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="73b8b-157">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="73b8b-157">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="73b8b-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="73b8b-158">-Credential</span></span>

<span data-ttu-id="73b8b-159">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="73b8b-159">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="73b8b-160">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="73b8b-160">The default is the current user.</span></span> <span data-ttu-id="73b8b-161">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ».</span><span class="sxs-lookup"><span data-stu-id="73b8b-161">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="73b8b-162">Ou entrez un objet PSCredential, tel que celui retourné par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="73b8b-162">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="73b8b-163">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="73b8b-163">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="73b8b-164">-FilePath</span><span class="sxs-lookup"><span data-stu-id="73b8b-164">-FilePath</span></span>

<span data-ttu-id="73b8b-165">Spécifie le chemin d'accès d'un fichier qui est utilisé pour créer une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-165">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="73b8b-166">Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="73b8b-166">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="73b8b-167">Par exemple, la commande suivante utilise le paramètre **file** :</span><span class="sxs-lookup"><span data-stu-id="73b8b-167">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="73b8b-168">Cette commande appelle la méthode **StopService** sur le service Spooler en utilisant l’entrée d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="73b8b-168">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="73b8b-169">Le fichier, `Input.xml` , contient le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="73b8b-169">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73b8b-170">-A</span><span class="sxs-lookup"><span data-stu-id="73b8b-170">-OptionSet</span></span>

<span data-ttu-id="73b8b-171">Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="73b8b-171">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="73b8b-172">Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="73b8b-172">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="73b8b-173">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="73b8b-173">Any number of options can be specified.</span></span>

<span data-ttu-id="73b8b-174">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="73b8b-174">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="73b8b-175">-Port</span><span class="sxs-lookup"><span data-stu-id="73b8b-175">-Port</span></span>

<span data-ttu-id="73b8b-176">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="73b8b-176">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="73b8b-177">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="73b8b-177">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="73b8b-178">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="73b8b-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="73b8b-179">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre **ComputerName** doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="73b8b-179">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="73b8b-180">Toutefois, si le paramètre **SkipCNCheck** est spécifié dans le cadre du paramètre **SessionOption** , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="73b8b-180">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="73b8b-181">Le paramètre **SkipCNCheck** doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="73b8b-181">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="73b8b-182">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="73b8b-182">-ResourceURI</span></span>

<span data-ttu-id="73b8b-183">Contient l'URI de l'instance ou de la classe de ressource.</span><span class="sxs-lookup"><span data-stu-id="73b8b-183">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="73b8b-184">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="73b8b-184">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="73b8b-185">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="73b8b-185">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="73b8b-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="73b8b-186">For example:</span></span>

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

### <span data-ttu-id="73b8b-187">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="73b8b-187">-SelectorSet</span></span>

<span data-ttu-id="73b8b-188">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="73b8b-188">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="73b8b-189">Le paramètre **SelectorSet** est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="73b8b-189">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="73b8b-190">La valeur du paramètre **SelectorSet** doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="73b8b-190">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="73b8b-191">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="73b8b-191">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="73b8b-192">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="73b8b-192">-SessionOption</span></span>

<span data-ttu-id="73b8b-193">Définit un ensemble d'options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="73b8b-193">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="73b8b-194">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="73b8b-194">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="73b8b-195">Pour plus d’informations sur les options disponibles, consultez `New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="73b8b-195">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="73b8b-196">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="73b8b-196">-UseSSL</span></span>

<span data-ttu-id="73b8b-197">Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="73b8b-197">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="73b8b-198">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="73b8b-198">By default, SSL is not used.</span></span>

<span data-ttu-id="73b8b-199">WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="73b8b-199">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="73b8b-200">Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="73b8b-200">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="73b8b-201">Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="73b8b-201">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="73b8b-202">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="73b8b-202">-ValueSet</span></span>

<span data-ttu-id="73b8b-203">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="73b8b-203">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="73b8b-204">Vous spécifiez la ressource de gestion à l’aide du paramètre **resourceuri** et du paramètre **SelectorSet** .</span><span class="sxs-lookup"><span data-stu-id="73b8b-204">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="73b8b-205">La valeur du paramètre **ValueSet** doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="73b8b-205">The value of the **ValueSet** parameter must be a hash table.</span></span>

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

### <span data-ttu-id="73b8b-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73b8b-206">CommonParameters</span></span>

<span data-ttu-id="73b8b-207">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73b8b-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73b8b-208">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="73b8b-208">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="73b8b-209">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="73b8b-209">INPUTS</span></span>

### <span data-ttu-id="73b8b-210">None</span><span class="sxs-lookup"><span data-stu-id="73b8b-210">None</span></span>

<span data-ttu-id="73b8b-211">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="73b8b-211">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="73b8b-212">SORTIES</span><span class="sxs-lookup"><span data-stu-id="73b8b-212">OUTPUTS</span></span>

### <span data-ttu-id="73b8b-213">None</span><span class="sxs-lookup"><span data-stu-id="73b8b-213">None</span></span>

<span data-ttu-id="73b8b-214">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="73b8b-214">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="73b8b-215">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="73b8b-215">NOTES</span></span>

<span data-ttu-id="73b8b-216">L' `Set-WmiInstance` applet de commande, une applet de commande Windows Management Instrumentation (WMI), est similaire.</span><span class="sxs-lookup"><span data-stu-id="73b8b-216">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="73b8b-217">`Set-WmiInstance` utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.</span><span class="sxs-lookup"><span data-stu-id="73b8b-217">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="73b8b-218">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="73b8b-218">RELATED LINKS</span></span>

[<span data-ttu-id="73b8b-219">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="73b8b-219">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="73b8b-220">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="73b8b-220">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="73b8b-221">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="73b8b-221">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="73b8b-222">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="73b8b-222">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="73b8b-223">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="73b8b-223">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="73b8b-224">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="73b8b-224">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="73b8b-225">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="73b8b-225">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="73b8b-226">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="73b8b-226">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="73b8b-227">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="73b8b-227">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="73b8b-228">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="73b8b-228">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="73b8b-229">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="73b8b-229">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="73b8b-230">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="73b8b-230">Test-WSMan</span></span>](Test-WSMan.md)


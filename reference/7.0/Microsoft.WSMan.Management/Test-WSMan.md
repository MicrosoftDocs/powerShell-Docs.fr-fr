---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 602f390aa6474d56e2ac1865dbad20fbb73dc4f1
ms.sourcegitcommit: 87b9b989f261b52969e99159e99ee28ad8d8839a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "93205330"
---
# <span data-ttu-id="82a4d-103">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="82a4d-103">Test-WSMan</span></span>

## <span data-ttu-id="82a4d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="82a4d-104">SYNOPSIS</span></span>
<span data-ttu-id="82a4d-105">Teste si le service WinRM est en cours d'exécution sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="82a4d-105">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="82a4d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82a4d-106">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="82a4d-107">Description</span><span class="sxs-lookup"><span data-stu-id="82a4d-107">DESCRIPTION</span></span>

<span data-ttu-id="82a4d-108">L’applet de commande **Test-WSMan** soumet une demande d’identification qui détermine si le service WinRM est en cours d’exécution sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="82a4d-108">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="82a4d-109">Si l'ordinateur testé exécute le service, l'applet de commande affiche le schéma d'identité WS-Management, la version du protocole, le fournisseur du produit et la version du produit du service testé.</span><span class="sxs-lookup"><span data-stu-id="82a4d-109">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="82a4d-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="82a4d-110">EXAMPLES</span></span>

### <span data-ttu-id="82a4d-111">Exemple 1 : déterminer l’état du service WinRM</span><span class="sxs-lookup"><span data-stu-id="82a4d-111">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="82a4d-112">Cette commande détermine si le service WinRM est en cours d'exécution sur l'ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="82a4d-112">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="82a4d-113">Exemple 2 : déterminer l’état du service WinRM sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="82a4d-113">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="82a4d-114">Cette commande détermine si le service WinRM est en cours d’exécution sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="82a4d-114">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="82a4d-115">Exemple 3 : déterminer l’état du service WinRM et la version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="82a4d-115">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="82a4d-116">Cette commande vérifie si le service WS-Management (WinRM) est en cours d’exécution sur l’ordinateur local à l’aide du paramètre d’authentification.</span><span class="sxs-lookup"><span data-stu-id="82a4d-116">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="82a4d-117">L’utilisation du paramètre d’authentification permet à **Test-WSMan** de retourner la version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="82a4d-117">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="82a4d-118">Exemple 4 : déterminer l’état du service WinRM et la version du système d’exploitation sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="82a4d-118">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="82a4d-119">Cette commande vérifie si le service WS-Management (WinRM) est en cours d’exécution sur l’ordinateur nommé SERVEUR01 à l’aide du paramètre d’authentification.</span><span class="sxs-lookup"><span data-stu-id="82a4d-119">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="82a4d-120">L’utilisation du paramètre d’authentification permet à **Test-WSMan** de retourner la version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="82a4d-120">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="82a4d-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82a4d-121">PARAMETERS</span></span>

### <span data-ttu-id="82a4d-122">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="82a4d-122">-ApplicationName</span></span>

<span data-ttu-id="82a4d-123">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="82a4d-123">Specifies the application name in the connection.</span></span>
<span data-ttu-id="82a4d-124">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="82a4d-124">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="82a4d-125">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="82a4d-125">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="82a4d-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="82a4d-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="82a4d-127">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="82a4d-127">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="82a4d-128">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="82a4d-128">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="82a4d-129">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="82a4d-129">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="82a4d-130">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82a4d-130">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="82a4d-131">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="82a4d-131">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="82a4d-132">-Authentification</span><span class="sxs-lookup"><span data-stu-id="82a4d-132">-Authentication</span></span>

<span data-ttu-id="82a4d-133">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="82a4d-133">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="82a4d-134">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="82a4d-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82a4d-135">De base.</span><span class="sxs-lookup"><span data-stu-id="82a4d-135">Basic.</span></span>
<span data-ttu-id="82a4d-136">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="82a4d-136">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="82a4d-137">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="82a4d-137">Default.</span></span>
<span data-ttu-id="82a4d-138">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="82a4d-138">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="82a4d-139">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="82a4d-139">This is the default.</span></span>
- <span data-ttu-id="82a4d-140">Digest.</span><span class="sxs-lookup"><span data-stu-id="82a4d-140">Digest.</span></span>
<span data-ttu-id="82a4d-141">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="82a4d-141">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="82a4d-142">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="82a4d-142">Kerberos.</span></span>
<span data-ttu-id="82a4d-143">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="82a4d-143">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="82a4d-144">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="82a4d-144">Negotiate.</span></span>
<span data-ttu-id="82a4d-145">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="82a4d-145">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="82a4d-146">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="82a4d-146">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="82a4d-147">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="82a4d-147">CredSSP.</span></span>
<span data-ttu-id="82a4d-148">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="82a4d-148">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="82a4d-149">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="82a4d-149">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="82a4d-150">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="82a4d-150">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="82a4d-151">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="82a4d-151">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="82a4d-152">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="82a4d-152">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="82a4d-153">Important : Si vous ne spécifiez pas le paramètre *d’authentification* ,, la demande **Test-WSMan** est envoyée de manière anonyme à l’ordinateur distant, sans utiliser l’authentification.</span><span class="sxs-lookup"><span data-stu-id="82a4d-153">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="82a4d-154">Si la demande est rendue anonyme, elle ne retourne aucune information spécifique à la version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="82a4d-154">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="82a4d-155">Au lieu de cela, cette applet de commande affiche des valeurs NULL pour la version du système d’exploitation et le niveau de Service Pack (système d’exploitation : 0.0.0 SP : 0,0).</span><span class="sxs-lookup"><span data-stu-id="82a4d-155">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="82a4d-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="82a4d-156">-CertificateThumbprint</span></span>

<span data-ttu-id="82a4d-157">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="82a4d-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="82a4d-158">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="82a4d-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="82a4d-159">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="82a4d-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="82a4d-160">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="82a4d-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="82a4d-161">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82a4d-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="82a4d-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="82a4d-162">-ComputerName</span></span>

<span data-ttu-id="82a4d-163">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="82a4d-163">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="82a4d-164">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="82a4d-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="82a4d-165">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="82a4d-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="82a4d-166">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="82a4d-166">The local computer is the default.</span></span>
<span data-ttu-id="82a4d-167">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="82a4d-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="82a4d-168">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82a4d-168">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82a4d-169">-Credential</span><span class="sxs-lookup"><span data-stu-id="82a4d-169">-Credential</span></span>

<span data-ttu-id="82a4d-170">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="82a4d-170">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="82a4d-171">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="82a4d-171">The default is the current user.</span></span>
<span data-ttu-id="82a4d-172">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="82a4d-172">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="82a4d-173">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="82a4d-173">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="82a4d-174">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="82a4d-174">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="82a4d-175">-Port</span><span class="sxs-lookup"><span data-stu-id="82a4d-175">-Port</span></span>

<span data-ttu-id="82a4d-176">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="82a4d-176">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="82a4d-177">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="82a4d-177">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="82a4d-178">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="82a4d-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="82a4d-179">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="82a4d-179">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="82a4d-180">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="82a4d-180">-UseSSL</span></span>

<span data-ttu-id="82a4d-181">Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="82a4d-181">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="82a4d-182">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="82a4d-182">By default, SSL is not used.</span></span>

<span data-ttu-id="82a4d-183">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="82a4d-183">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="82a4d-184">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="82a4d-184">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="82a4d-185">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="82a4d-185">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="82a4d-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82a4d-186">CommonParameters</span></span>

<span data-ttu-id="82a4d-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82a4d-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82a4d-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82a4d-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82a4d-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="82a4d-189">INPUTS</span></span>

### <span data-ttu-id="82a4d-190">Aucun</span><span class="sxs-lookup"><span data-stu-id="82a4d-190">None</span></span>

<span data-ttu-id="82a4d-191">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="82a4d-191">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="82a4d-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="82a4d-192">OUTPUTS</span></span>

### <span data-ttu-id="82a4d-193">Aucun</span><span class="sxs-lookup"><span data-stu-id="82a4d-193">None</span></span>

<span data-ttu-id="82a4d-194">Cette applet de commande ne génère aucun objet de sortie.</span><span class="sxs-lookup"><span data-stu-id="82a4d-194">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="82a4d-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="82a4d-195">NOTES</span></span>

* <span data-ttu-id="82a4d-196">Par défaut, l’applet de commande **Test-WSMan** interroge le service WinRM sans utiliser l’authentification, et ne retourne aucune information spécifique à la version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="82a4d-196">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="82a4d-197">Au lieu de cela, elle affiche des valeurs NULL pour la version du système d’exploitation et le niveau de Service Pack (système d’exploitation : 0.0.0 SP : 0,0).</span><span class="sxs-lookup"><span data-stu-id="82a4d-197">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

## <span data-ttu-id="82a4d-198">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="82a4d-198">RELATED LINKS</span></span>

[<span data-ttu-id="82a4d-199">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="82a4d-199">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="82a4d-200">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82a4d-200">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="82a4d-201">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="82a4d-201">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="82a4d-202">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82a4d-202">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="82a4d-203">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="82a4d-203">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="82a4d-204">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82a4d-204">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="82a4d-205">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="82a4d-205">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="82a4d-206">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82a4d-206">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="82a4d-207">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="82a4d-207">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="82a4d-208">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82a4d-208">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="82a4d-209">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="82a4d-209">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="82a4d-210">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="82a4d-210">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

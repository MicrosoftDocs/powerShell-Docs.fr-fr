---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 4d1273fe1ed643f8d45b627db9863b75212b6b24
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595723"
---
# <span data-ttu-id="70f62-102">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="70f62-102">Remove-WSManInstance</span></span>

## <span data-ttu-id="70f62-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="70f62-103">SYNOPSIS</span></span>
<span data-ttu-id="70f62-104">Supprime une instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="70f62-104">Deletes a management resource instance.</span></span>

## <span data-ttu-id="70f62-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="70f62-105">SYNTAX</span></span>

### <span data-ttu-id="70f62-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="70f62-106">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="70f62-107">URI</span><span class="sxs-lookup"><span data-stu-id="70f62-107">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="70f62-108">Description</span><span class="sxs-lookup"><span data-stu-id="70f62-108">DESCRIPTION</span></span>

<span data-ttu-id="70f62-109">L’applet de commande **Remove-WSManInstance** supprime une instance d’une ressource de gestion qui est spécifiée dans les paramètres *resourceuri* et *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="70f62-109">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="70f62-110">Cette applet de commande utilise la couche de connexion/transport WinRM pour supprimer l'instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="70f62-110">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="70f62-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="70f62-111">EXAMPLES</span></span>

### <span data-ttu-id="70f62-112">Exemple 1 : supprimer un écouteur</span><span class="sxs-lookup"><span data-stu-id="70f62-112">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="70f62-113">Cette commande supprime l’écouteur HTTP WS-Management sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70f62-113">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="70f62-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70f62-114">PARAMETERS</span></span>

### <span data-ttu-id="70f62-115">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="70f62-115">-ApplicationName</span></span>

<span data-ttu-id="70f62-116">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="70f62-116">Specifies the application name in the connection.</span></span>
<span data-ttu-id="70f62-117">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="70f62-117">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="70f62-118">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="70f62-118">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="70f62-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="70f62-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="70f62-120">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="70f62-120">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="70f62-121">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="70f62-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="70f62-122">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="70f62-122">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="70f62-123">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70f62-123">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="70f62-124">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="70f62-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70f62-125">-Authentification</span><span class="sxs-lookup"><span data-stu-id="70f62-125">-Authentication</span></span>

<span data-ttu-id="70f62-126">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="70f62-126">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="70f62-127">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="70f62-127">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="70f62-128">De base.</span><span class="sxs-lookup"><span data-stu-id="70f62-128">Basic.</span></span>
<span data-ttu-id="70f62-129">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="70f62-129">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="70f62-130">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="70f62-130">Default.</span></span>
<span data-ttu-id="70f62-131">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="70f62-131">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="70f62-132">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="70f62-132">This is the default.</span></span>
- <span data-ttu-id="70f62-133">Digest.</span><span class="sxs-lookup"><span data-stu-id="70f62-133">Digest.</span></span>
<span data-ttu-id="70f62-134">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="70f62-134">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="70f62-135">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="70f62-135">Kerberos.</span></span>
<span data-ttu-id="70f62-136">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="70f62-136">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="70f62-137">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="70f62-137">Negotiate.</span></span>
<span data-ttu-id="70f62-138">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="70f62-138">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="70f62-139">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="70f62-139">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="70f62-140">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="70f62-140">CredSSP.</span></span>
<span data-ttu-id="70f62-141">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="70f62-141">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="70f62-142">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="70f62-142">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="70f62-143">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="70f62-143">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="70f62-144">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="70f62-144">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="70f62-145">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="70f62-145">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="70f62-146">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="70f62-146">-CertificateThumbprint</span></span>

<span data-ttu-id="70f62-147">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="70f62-147">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="70f62-148">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="70f62-148">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="70f62-149">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="70f62-149">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="70f62-150">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="70f62-150">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="70f62-151">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70f62-151">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="70f62-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="70f62-152">-ComputerName</span></span>

<span data-ttu-id="70f62-153">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="70f62-153">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="70f62-154">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="70f62-154">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="70f62-155">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="70f62-155">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="70f62-156">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="70f62-156">The local computer is the default.</span></span>
<span data-ttu-id="70f62-157">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="70f62-157">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="70f62-158">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70f62-158">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70f62-159">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="70f62-159">-ConnectionURI</span></span>

<span data-ttu-id="70f62-160">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="70f62-160">Specifies the connection endpoint.</span></span>
<span data-ttu-id="70f62-161">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="70f62-161">The format of this string is as follows:</span></span>

<span data-ttu-id="70f62-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="70f62-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="70f62-163">La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="70f62-163">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="70f62-164">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="70f62-164">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70f62-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="70f62-165">-Credential</span></span>

<span data-ttu-id="70f62-166">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="70f62-166">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="70f62-167">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="70f62-167">The default is the current user.</span></span>
<span data-ttu-id="70f62-168">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="70f62-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="70f62-169">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="70f62-169">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="70f62-170">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="70f62-170">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="70f62-171">-A</span><span class="sxs-lookup"><span data-stu-id="70f62-171">-OptionSet</span></span>

<span data-ttu-id="70f62-172">Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="70f62-172">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="70f62-173">Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="70f62-173">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="70f62-174">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="70f62-174">Any number of options can be specified.</span></span>

<span data-ttu-id="70f62-175">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="70f62-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="70f62-176">-Port</span><span class="sxs-lookup"><span data-stu-id="70f62-176">-Port</span></span>

<span data-ttu-id="70f62-177">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="70f62-177">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="70f62-178">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="70f62-178">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="70f62-179">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="70f62-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="70f62-180">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="70f62-180">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="70f62-181">Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="70f62-181">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="70f62-182">Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="70f62-182">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="70f62-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="70f62-183">-ResourceURI</span></span>

<span data-ttu-id="70f62-184">Spécifie l’URI de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="70f62-184">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="70f62-185">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70f62-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="70f62-186">Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="70f62-186">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="70f62-187">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="70f62-187">For example:</span></span>

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

### <span data-ttu-id="70f62-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="70f62-188">-SelectorSet</span></span>

<span data-ttu-id="70f62-189">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="70f62-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="70f62-190">Le paramètre *SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="70f62-190">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="70f62-191">La valeur de *SelectorSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="70f62-191">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="70f62-192">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="70f62-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="70f62-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="70f62-193">-SessionOption</span></span>

<span data-ttu-id="70f62-194">Spécifie les options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="70f62-194">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="70f62-195">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="70f62-195">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="70f62-196">Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="70f62-196">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="70f62-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="70f62-197">-UseSSL</span></span>

<span data-ttu-id="70f62-198">Spécifie que le protocole SSL (Secure Sockets Layer) (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="70f62-198">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="70f62-199">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="70f62-199">By default, SSL is not used.</span></span>

<span data-ttu-id="70f62-200">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="70f62-200">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="70f62-201">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="70f62-201">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="70f62-202">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="70f62-202">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70f62-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70f62-203">CommonParameters</span></span>

<span data-ttu-id="70f62-204">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70f62-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70f62-205">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="70f62-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70f62-206">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="70f62-206">INPUTS</span></span>

### <span data-ttu-id="70f62-207">None</span><span class="sxs-lookup"><span data-stu-id="70f62-207">None</span></span>

<span data-ttu-id="70f62-208">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="70f62-208">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="70f62-209">SORTIES</span><span class="sxs-lookup"><span data-stu-id="70f62-209">OUTPUTS</span></span>

### <span data-ttu-id="70f62-210">None</span><span class="sxs-lookup"><span data-stu-id="70f62-210">None</span></span>

<span data-ttu-id="70f62-211">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="70f62-211">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="70f62-212">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="70f62-212">NOTES</span></span>

* <span data-ttu-id="70f62-213">L'applet de commande Remove-WmiObject, une applet de commande WMI (Windows Management Instrumentation), est similaire.</span><span class="sxs-lookup"><span data-stu-id="70f62-213">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="70f62-214">**Remove-WmiObject** utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.</span><span class="sxs-lookup"><span data-stu-id="70f62-214">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="70f62-215">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="70f62-215">RELATED LINKS</span></span>

[<span data-ttu-id="70f62-216">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="70f62-216">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="70f62-217">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="70f62-217">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="70f62-218">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="70f62-218">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="70f62-219">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="70f62-219">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="70f62-220">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="70f62-220">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="70f62-221">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="70f62-221">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="70f62-222">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="70f62-222">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="70f62-223">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="70f62-223">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="70f62-224">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="70f62-224">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="70f62-225">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="70f62-225">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="70f62-226">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="70f62-226">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="70f62-227">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="70f62-227">Test-WSMan</span></span>](Test-WSMan.md)


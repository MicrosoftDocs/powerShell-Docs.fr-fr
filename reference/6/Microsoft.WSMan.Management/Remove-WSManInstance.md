---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 9cddfbe90e352b2099a8f999044f20ba4cba5cc4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205573"
---
# <span data-ttu-id="a95bd-103">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a95bd-103">Remove-WSManInstance</span></span>

## <span data-ttu-id="a95bd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a95bd-104">SYNOPSIS</span></span>
<span data-ttu-id="a95bd-105">Supprime une instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="a95bd-105">Deletes a management resource instance.</span></span>

## <span data-ttu-id="a95bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a95bd-106">SYNTAX</span></span>

### <span data-ttu-id="a95bd-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a95bd-107">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="a95bd-108">URI</span><span class="sxs-lookup"><span data-stu-id="a95bd-108">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="a95bd-109">Description</span><span class="sxs-lookup"><span data-stu-id="a95bd-109">DESCRIPTION</span></span>

<span data-ttu-id="a95bd-110">L’applet de commande **Remove-WSManInstance** supprime une instance d’une ressource de gestion qui est spécifiée dans les paramètres *resourceuri* et *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="a95bd-110">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="a95bd-111">Cette applet de commande utilise la couche de connexion/transport WinRM pour supprimer l'instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="a95bd-111">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="a95bd-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a95bd-112">EXAMPLES</span></span>

### <span data-ttu-id="a95bd-113">Exemple 1 : supprimer un écouteur</span><span class="sxs-lookup"><span data-stu-id="a95bd-113">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="a95bd-114">Cette commande supprime l’écouteur HTTP WS-Management sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a95bd-114">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="a95bd-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a95bd-115">PARAMETERS</span></span>

### <span data-ttu-id="a95bd-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="a95bd-116">-ApplicationName</span></span>

<span data-ttu-id="a95bd-117">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="a95bd-117">Specifies the application name in the connection.</span></span>
<span data-ttu-id="a95bd-118">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="a95bd-118">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="a95bd-119">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="a95bd-119">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="a95bd-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="a95bd-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="a95bd-121">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="a95bd-121">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="a95bd-122">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a95bd-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="a95bd-123">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="a95bd-123">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="a95bd-124">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a95bd-124">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="a95bd-125">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="a95bd-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="a95bd-126">-Authentification</span><span class="sxs-lookup"><span data-stu-id="a95bd-126">-Authentication</span></span>

<span data-ttu-id="a95bd-127">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="a95bd-127">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="a95bd-128">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="a95bd-128">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a95bd-129">De base.</span><span class="sxs-lookup"><span data-stu-id="a95bd-129">Basic.</span></span>
<span data-ttu-id="a95bd-130">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="a95bd-130">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="a95bd-131">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="a95bd-131">Default.</span></span>
<span data-ttu-id="a95bd-132">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="a95bd-132">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="a95bd-133">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a95bd-133">This is the default.</span></span>
- <span data-ttu-id="a95bd-134">Digest.</span><span class="sxs-lookup"><span data-stu-id="a95bd-134">Digest.</span></span>
<span data-ttu-id="a95bd-135">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="a95bd-135">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="a95bd-136">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="a95bd-136">Kerberos.</span></span>
<span data-ttu-id="a95bd-137">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="a95bd-137">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="a95bd-138">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="a95bd-138">Negotiate.</span></span>
<span data-ttu-id="a95bd-139">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="a95bd-139">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="a95bd-140">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a95bd-140">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="a95bd-141">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="a95bd-141">CredSSP.</span></span>
<span data-ttu-id="a95bd-142">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a95bd-142">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="a95bd-143">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a95bd-143">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="a95bd-144">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a95bd-144">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="a95bd-145">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="a95bd-145">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="a95bd-146">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="a95bd-146">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="a95bd-147">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="a95bd-147">-CertificateThumbprint</span></span>

<span data-ttu-id="a95bd-148">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="a95bd-148">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a95bd-149">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="a95bd-149">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="a95bd-150">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="a95bd-150">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="a95bd-151">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="a95bd-151">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="a95bd-152">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a95bd-152">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="a95bd-153">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a95bd-153">-ComputerName</span></span>

<span data-ttu-id="a95bd-154">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="a95bd-154">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="a95bd-155">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="a95bd-155">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="a95bd-156">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a95bd-156">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="a95bd-157">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a95bd-157">The local computer is the default.</span></span>
<span data-ttu-id="a95bd-158">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="a95bd-158">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="a95bd-159">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a95bd-159">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="a95bd-160">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="a95bd-160">-ConnectionURI</span></span>

<span data-ttu-id="a95bd-161">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="a95bd-161">Specifies the connection endpoint.</span></span>
<span data-ttu-id="a95bd-162">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="a95bd-162">The format of this string is as follows:</span></span>

<span data-ttu-id="a95bd-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="a95bd-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="a95bd-164">La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="a95bd-164">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="a95bd-165">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="a95bd-165">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="a95bd-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="a95bd-166">-Credential</span></span>

<span data-ttu-id="a95bd-167">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="a95bd-167">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a95bd-168">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a95bd-168">The default is the current user.</span></span>
<span data-ttu-id="a95bd-169">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="a95bd-169">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="a95bd-170">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="a95bd-170">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="a95bd-171">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a95bd-171">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="a95bd-172">-A</span><span class="sxs-lookup"><span data-stu-id="a95bd-172">-OptionSet</span></span>

<span data-ttu-id="a95bd-173">Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="a95bd-173">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="a95bd-174">Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="a95bd-174">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="a95bd-175">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="a95bd-175">Any number of options can be specified.</span></span>

<span data-ttu-id="a95bd-176">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="a95bd-176">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="a95bd-177">-Port</span><span class="sxs-lookup"><span data-stu-id="a95bd-177">-Port</span></span>

<span data-ttu-id="a95bd-178">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="a95bd-178">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="a95bd-179">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="a95bd-179">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="a95bd-180">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="a95bd-180">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="a95bd-181">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="a95bd-181">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="a95bd-182">Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="a95bd-182">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="a95bd-183">Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="a95bd-183">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="a95bd-184">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="a95bd-184">-ResourceURI</span></span>

<span data-ttu-id="a95bd-185">Spécifie l’URI de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="a95bd-185">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="a95bd-186">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a95bd-186">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a95bd-187">Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="a95bd-187">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="a95bd-188">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a95bd-188">For example:</span></span>

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

### <span data-ttu-id="a95bd-189">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="a95bd-189">-SelectorSet</span></span>

<span data-ttu-id="a95bd-190">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="a95bd-190">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="a95bd-191">Le paramètre *SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="a95bd-191">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="a95bd-192">La valeur de *SelectorSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="a95bd-192">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="a95bd-193">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="a95bd-193">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="a95bd-194">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="a95bd-194">-SessionOption</span></span>

<span data-ttu-id="a95bd-195">Spécifie les options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="a95bd-195">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="a95bd-196">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="a95bd-196">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="a95bd-197">Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="a95bd-197">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="a95bd-198">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="a95bd-198">-UseSSL</span></span>

<span data-ttu-id="a95bd-199">Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a95bd-199">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="a95bd-200">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="a95bd-200">By default, SSL is not used.</span></span>

<span data-ttu-id="a95bd-201">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="a95bd-201">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="a95bd-202">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="a95bd-202">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="a95bd-203">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="a95bd-203">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="a95bd-204">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a95bd-204">CommonParameters</span></span>

<span data-ttu-id="a95bd-205">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a95bd-205">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a95bd-206">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a95bd-206">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a95bd-207">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a95bd-207">INPUTS</span></span>

### <span data-ttu-id="a95bd-208">Aucun</span><span class="sxs-lookup"><span data-stu-id="a95bd-208">None</span></span>

<span data-ttu-id="a95bd-209">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="a95bd-209">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="a95bd-210">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a95bd-210">OUTPUTS</span></span>

### <span data-ttu-id="a95bd-211">Aucun</span><span class="sxs-lookup"><span data-stu-id="a95bd-211">None</span></span>

<span data-ttu-id="a95bd-212">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a95bd-212">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a95bd-213">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a95bd-213">NOTES</span></span>

* <span data-ttu-id="a95bd-214">L'applet de commande Remove-WmiObject, une applet de commande WMI (Windows Management Instrumentation), est similaire.</span><span class="sxs-lookup"><span data-stu-id="a95bd-214">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="a95bd-215">**Remove-WmiObject** utilise la couche de connexion/transport DCOM pour créer ou mettre à jour des instances WMI.</span><span class="sxs-lookup"><span data-stu-id="a95bd-215">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="a95bd-216">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a95bd-216">RELATED LINKS</span></span>

[<span data-ttu-id="a95bd-217">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a95bd-217">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a95bd-218">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a95bd-218">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a95bd-219">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a95bd-219">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a95bd-220">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a95bd-220">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="a95bd-221">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a95bd-221">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="a95bd-222">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a95bd-222">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a95bd-223">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a95bd-223">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="a95bd-224">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a95bd-224">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a95bd-225">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a95bd-225">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="a95bd-226">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a95bd-226">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a95bd-227">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a95bd-227">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a95bd-228">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="a95bd-228">Test-WSMan</span></span>](Test-WSMan.md)

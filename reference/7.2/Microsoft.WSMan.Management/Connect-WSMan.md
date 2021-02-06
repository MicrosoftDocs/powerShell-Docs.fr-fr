---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: 5dfd0b355a3589bf45ea92b92ae8778023132bcd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595734"
---
# <span data-ttu-id="ec7b7-102">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec7b7-102">Connect-WSMan</span></span>

## <span data-ttu-id="ec7b7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ec7b7-103">SYNOPSIS</span></span>
<span data-ttu-id="ec7b7-104">Se connecte au service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-104">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="ec7b7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ec7b7-105">SYNTAX</span></span>

### <span data-ttu-id="ec7b7-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-106">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="ec7b7-107">URI</span><span class="sxs-lookup"><span data-stu-id="ec7b7-107">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="ec7b7-108">Description</span><span class="sxs-lookup"><span data-stu-id="ec7b7-108">DESCRIPTION</span></span>
<span data-ttu-id="ec7b7-109">L’applet de commande **connect-wsman** se connecte au service WinRM sur un ordinateur distant et établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-109">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="ec7b7-110">Vous pouvez utiliser cette applet de commande dans le contexte du fournisseur WSMan pour vous connecter au service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-110">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="ec7b7-111">Toutefois, vous pouvez également utiliser cette applet de commande pour vous connecter au service WinRM sur un ordinateur distant avant de choisir le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-111">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="ec7b7-112">L’ordinateur distant s’affiche dans le répertoire racine du fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-112">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="ec7b7-113">Des informations d'identification explicites sont requises quand les ordinateurs client et serveur se trouvent dans des domaines ou des groupes de travail différents.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-113">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="ec7b7-114">Pour plus d’informations sur la façon de se déconnecter du service WinRM sur un ordinateur distant, consultez l’applet de commande Disconnect-WSMan.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-114">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="ec7b7-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ec7b7-115">EXAMPLES</span></span>

### <span data-ttu-id="ec7b7-116">Exemple 1 : se connecter à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="ec7b7-116">Example 1: Connect to a remote computer</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="ec7b7-117">Cette commande crée une connexion à l'ordinateur distant server01.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-117">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="ec7b7-118">L’applet de commande **connect-wsman** est généralement utilisée dans le contexte du fournisseur WSMan pour se connecter à un ordinateur distant, dans le cas présent l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-118">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="ec7b7-119">Toutefois, vous pouvez utiliser l'applet de commande pour établir des connexions aux ordinateurs distants avant de choisir le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-119">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="ec7b7-120">Ces connexions s’affichent dans la liste **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="ec7b7-120">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="ec7b7-121">Exemple 2 : se connecter à un ordinateur distant à l’aide des informations d’identification d’administrateur</span><span class="sxs-lookup"><span data-stu-id="ec7b7-121">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="ec7b7-122">Cette commande crée une connexion au système distant server01 en utilisant les informations d'identification du compte administrateur.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-122">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="ec7b7-123">La première commande utilise l'applet de commande Get-Credential pour obtenir les informations d'identification de l'administrateur, puis les stocke dans la variable $cred.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-123">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="ec7b7-124">La commande **obtenir-Credential** vous invite à entrer le nom d’utilisateur et le mot de passe dans une boîte de dialogue ou sur la ligne de commande, en fonction des paramètres du Registre système.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-124">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="ec7b7-125">La deuxième commande utilise le paramètre *Credential* pour transmettre les informations d’identification stockées dans $cred à **connect-wsman**.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-125">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan**.</span></span>
<span data-ttu-id="ec7b7-126">**Connect-wsman** se connecte ensuite au système SERVEUR01 distant à l’aide des informations d’identification d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-126">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="ec7b7-127">Exemple 3 : connexion à un ordinateur distant sur un port spécifié</span><span class="sxs-lookup"><span data-stu-id="ec7b7-127">Example 3: Connect to a remote computer over a specified port</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="ec7b7-128">Cette commande crée une connexion à l'ordinateur distant server01 via le port 80.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-128">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="ec7b7-129">Exemple 4 : se connecter à un ordinateur distant à l’aide des options de connexion</span><span class="sxs-lookup"><span data-stu-id="ec7b7-129">Example 4: Connect to a remote computer by using connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="ec7b7-130">Cet exemple crée une connexion à l’ordinateur SERVEUR01 distant à l’aide des options de connexion définies dans la commande **New-WSManSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="ec7b7-130">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="ec7b7-131">La première commande utilise **New-WSManSessionOption** pour stocker un ensemble d’options de paramètres de connexion dans la variable $a.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-131">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="ec7b7-132">Dans cet exemple, les options de session définissent un délai de connexion de 30 secondes (30 000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="ec7b7-132">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="ec7b7-133">La deuxième commande utilise le paramètre *SessionOption* pour transmettre les informations d’identification stockées dans la variable $A à **connect-wsman**.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-133">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="ec7b7-134">Ensuite, **connect-wsman** se connecte à l’ordinateur SERVEUR01 distant à l’aide des options de session spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-134">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="ec7b7-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ec7b7-135">PARAMETERS</span></span>

### <span data-ttu-id="ec7b7-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="ec7b7-136">-ApplicationName</span></span>
<span data-ttu-id="ec7b7-137">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="ec7b7-138">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="ec7b7-139">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="ec7b7-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="ec7b7-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="ec7b7-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="ec7b7-141">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="ec7b7-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="ec7b7-142">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="ec7b7-143">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="ec7b7-144">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="ec7b7-145">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-145">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="ec7b7-146">-Authentification</span><span class="sxs-lookup"><span data-stu-id="ec7b7-146">-Authentication</span></span>
<span data-ttu-id="ec7b7-147">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-147">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="ec7b7-148">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="ec7b7-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ec7b7-149">De base.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-149">Basic.</span></span>
<span data-ttu-id="ec7b7-150">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-150">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="ec7b7-151">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-151">Default.</span></span>
<span data-ttu-id="ec7b7-152">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-152">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="ec7b7-153">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-153">This is the default.</span></span>
- <span data-ttu-id="ec7b7-154">Digest.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-154">Digest.</span></span>
<span data-ttu-id="ec7b7-155">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-155">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="ec7b7-156">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-156">Kerberos.</span></span>
<span data-ttu-id="ec7b7-157">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-157">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="ec7b7-158">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-158">Negotiate.</span></span>
<span data-ttu-id="ec7b7-159">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-159">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="ec7b7-160">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-160">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="ec7b7-161">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-161">CredSSP.</span></span>
<span data-ttu-id="ec7b7-162">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-162">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="ec7b7-163">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-163">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="ec7b7-164">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-164">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="ec7b7-165">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-165">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="ec7b7-166">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-166">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="ec7b7-167">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="ec7b7-167">-CertificateThumbprint</span></span>
<span data-ttu-id="ec7b7-168">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-168">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ec7b7-169">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-169">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="ec7b7-170">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-170">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="ec7b7-171">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-171">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="ec7b7-172">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-172">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="ec7b7-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ec7b7-173">-ComputerName</span></span>
<span data-ttu-id="ec7b7-174">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-174">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="ec7b7-175">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-175">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="ec7b7-176">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-176">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="ec7b7-177">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-177">The local computer is the default.</span></span>
<span data-ttu-id="ec7b7-178">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-178">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="ec7b7-179">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-179">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ec7b7-180">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="ec7b7-180">-ConnectionURI</span></span>
<span data-ttu-id="ec7b7-181">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-181">Specifies the connection endpoint.</span></span>
<span data-ttu-id="ec7b7-182">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="ec7b7-182">The format of this string is as follows:</span></span>

<span data-ttu-id="ec7b7-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="ec7b7-183">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="ec7b7-184">La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="ec7b7-184">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="ec7b7-185">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-185">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="ec7b7-186">-Credential</span><span class="sxs-lookup"><span data-stu-id="ec7b7-186">-Credential</span></span>
<span data-ttu-id="ec7b7-187">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-187">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ec7b7-188">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-188">The default is the current user.</span></span>
<span data-ttu-id="ec7b7-189">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="ec7b7-189">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="ec7b7-190">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-190">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="ec7b7-191">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-191">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="ec7b7-192">-A</span><span class="sxs-lookup"><span data-stu-id="ec7b7-192">-OptionSet</span></span>
<span data-ttu-id="ec7b7-193">Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-193">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="ec7b7-194">Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-194">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="ec7b7-195">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-195">Any number of options can be specified.</span></span>

<span data-ttu-id="ec7b7-196">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="ec7b7-196">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="ec7b7-197">-Port</span><span class="sxs-lookup"><span data-stu-id="ec7b7-197">-Port</span></span>
<span data-ttu-id="ec7b7-198">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-198">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="ec7b7-199">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-199">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="ec7b7-200">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-200">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="ec7b7-201">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-201">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="ec7b7-202">Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-202">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="ec7b7-203">Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-203">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="ec7b7-204">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="ec7b7-204">-SessionOption</span></span>
<span data-ttu-id="ec7b7-205">Spécifie les options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-205">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="ec7b7-206">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-206">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="ec7b7-207">Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="ec7b7-207">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="ec7b7-208">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="ec7b7-208">-UseSSL</span></span>
<span data-ttu-id="ec7b7-209">Spécifie que le protocole SSL (Secure Sockets Layer) (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-209">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="ec7b7-210">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-210">By default, SSL is not used.</span></span>

<span data-ttu-id="ec7b7-211">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-211">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="ec7b7-212">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-212">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="ec7b7-213">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-213">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="ec7b7-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec7b7-214">CommonParameters</span></span>
<span data-ttu-id="ec7b7-215">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ec7b7-216">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ec7b7-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ec7b7-217">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ec7b7-217">INPUTS</span></span>

### <span data-ttu-id="ec7b7-218">None</span><span class="sxs-lookup"><span data-stu-id="ec7b7-218">None</span></span>
<span data-ttu-id="ec7b7-219">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-219">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="ec7b7-220">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ec7b7-220">OUTPUTS</span></span>

### <span data-ttu-id="ec7b7-221">None</span><span class="sxs-lookup"><span data-stu-id="ec7b7-221">None</span></span>
<span data-ttu-id="ec7b7-222">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-222">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ec7b7-223">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ec7b7-223">NOTES</span></span>

* <span data-ttu-id="ec7b7-224">Vous pouvez exécuter des commandes de gestion ou interroger des données de gestion sur un ordinateur distant sans création d'une session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-224">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="ec7b7-225">Pour ce faire, vous pouvez utiliser les paramètres *ComputerName* de Invoke-WSManAction et de la WSManInstance.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-225">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="ec7b7-226">Quand vous utilisez le paramètre *ComputerName* , PowerShell crée une connexion temporaire qui est utilisée pour la commande unique.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-226">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="ec7b7-227">Une fois la commande exécutée, la connexion est fermée.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-227">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="ec7b7-228">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ec7b7-228">RELATED LINKS</span></span>

[<span data-ttu-id="ec7b7-229">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec7b7-229">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="ec7b7-230">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec7b7-230">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="ec7b7-231">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec7b7-231">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="ec7b7-232">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ec7b7-232">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="ec7b7-233">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec7b7-233">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="ec7b7-234">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ec7b7-234">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="ec7b7-235">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec7b7-235">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="ec7b7-236">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="ec7b7-236">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="ec7b7-237">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec7b7-237">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="ec7b7-238">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ec7b7-238">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="ec7b7-239">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="ec7b7-239">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="ec7b7-240">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="ec7b7-240">Test-WSMan</span></span>](Test-WSMan.md)


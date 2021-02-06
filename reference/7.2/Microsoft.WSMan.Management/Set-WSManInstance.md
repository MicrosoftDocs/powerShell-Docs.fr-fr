---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2e5d68c2a75ea3040fd3998d2dc469200c054e58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603907"
---
# <span data-ttu-id="2a7ab-102">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2a7ab-102">Set-WSManInstance</span></span>

## <span data-ttu-id="2a7ab-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2a7ab-103">SYNOPSIS</span></span>
<span data-ttu-id="2a7ab-104">Modifie les informations de gestion qui sont associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-104">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="2a7ab-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2a7ab-105">SYNTAX</span></span>

### <span data-ttu-id="2a7ab-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2a7ab-106">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="2a7ab-107">URI</span><span class="sxs-lookup"><span data-stu-id="2a7ab-107">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="2a7ab-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a7ab-108">DESCRIPTION</span></span>

<span data-ttu-id="2a7ab-109">L'applet de commande Set-WSManInstance modifie les informations de gestion qui sont associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-109">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="2a7ab-110">Cette applet de commande utilise la couche de connexion/transport WinRM pour modifier les informations.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-110">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="2a7ab-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2a7ab-111">EXAMPLES</span></span>

### <span data-ttu-id="2a7ab-112">Exemple 1 : désactiver un écouteur sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2a7ab-112">Example 1: Disable a listener on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

<span data-ttu-id="2a7ab-113">Cette commande désactive l'écouteur https sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-113">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="2a7ab-114">Important : le paramètre *ValueSet* respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-114">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="2a7ab-115">Par exemple, dans cette commande,</span><span class="sxs-lookup"><span data-stu-id="2a7ab-115">For example, in this command,</span></span>

<span data-ttu-id="2a7ab-116">Cette opération échoue : `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="2a7ab-116">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="2a7ab-117">Cela s’effectue comme suit : `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="2a7ab-117">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="2a7ab-118">Exemple 2 : définir la taille d’enveloppe maximale sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2a7ab-118">Example 2: Set the maximum envelope size on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

<span data-ttu-id="2a7ab-119">Cette commande affecte à MaxEnvelopeSizekb la valeur 200 sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-119">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="2a7ab-120">Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-120">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="2a7ab-121">Ainsi, voici ce qui se passe avec la commande ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-121">For example, using the above command.</span></span>

<span data-ttu-id="2a7ab-122">Échec :-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-122">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="2a7ab-123">Cette opération a échoué :-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-123">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="2a7ab-124">Exemple 3 : désactiver un écouteur sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="2a7ab-124">Example 3: Disable a listener on a remote computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

<span data-ttu-id="2a7ab-125">Cette commande désactive l'écouteur https sur l'ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-125">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="2a7ab-126">Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-126">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="2a7ab-127">Ainsi, voici ce qui se passe avec la commande ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-127">For example, using the above command.</span></span>

<span data-ttu-id="2a7ab-128">Échec :-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-128">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="2a7ab-129">Cette opération a échoué :-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-129">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="2a7ab-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a7ab-130">PARAMETERS</span></span>

### <span data-ttu-id="2a7ab-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2a7ab-131">-ApplicationName</span></span>

<span data-ttu-id="2a7ab-132">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="2a7ab-133">La valeur par défaut du paramètre ApplicationName est « WSMAN ».</span><span class="sxs-lookup"><span data-stu-id="2a7ab-133">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="2a7ab-134">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="2a7ab-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="2a7ab-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="2a7ab-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-136">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="2a7ab-137">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="2a7ab-138">La valeur par défaut « WSMAN » est appropriée pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-138">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="2a7ab-139">Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-139">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="2a7ab-140">Dans ce cas, IIS héberge WS-Management (Web Services for Management) pour plus d'efficacité.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-140">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="2a7ab-141">-Authentification</span><span class="sxs-lookup"><span data-stu-id="2a7ab-141">-Authentication</span></span>

<span data-ttu-id="2a7ab-142">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="2a7ab-143">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-143">Possible values are:</span></span>

- <span data-ttu-id="2a7ab-144">De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-144">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="2a7ab-145">Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-145">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="2a7ab-146">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-146">This is the default.</span></span>
- <span data-ttu-id="2a7ab-147">Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-147">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="2a7ab-148">Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide de certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-148">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="2a7ab-149">Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-149">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="2a7ab-150">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-150">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="2a7ab-151">CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-151">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="2a7ab-152">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-152">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="2a7ab-153">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-153">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="2a7ab-154">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-154">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="2a7ab-155">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-155">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a7ab-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2a7ab-156">-CertificateThumbprint</span></span>

<span data-ttu-id="2a7ab-157">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="2a7ab-158">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2a7ab-159">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="2a7ab-160">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="2a7ab-161">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="2a7ab-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2a7ab-162">-ComputerName</span></span>

<span data-ttu-id="2a7ab-163">Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-163">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="2a7ab-164">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="2a7ab-165">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="2a7ab-166">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-166">The local computer is the default.</span></span>
<span data-ttu-id="2a7ab-167">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="2a7ab-168">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-168">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="2a7ab-169">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="2a7ab-169">-ConnectionURI</span></span>

<span data-ttu-id="2a7ab-170">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-170">Specifies the connection endpoint.</span></span>
<span data-ttu-id="2a7ab-171">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-171">The format of this string is:</span></span>

<span data-ttu-id="2a7ab-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="2a7ab-172">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="2a7ab-173">La chaîne suivante est une valeur au format correct pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-173">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="2a7ab-174">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-174">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="2a7ab-175">-Credential</span><span class="sxs-lookup"><span data-stu-id="2a7ab-175">-Credential</span></span>

<span data-ttu-id="2a7ab-176">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-176">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="2a7ab-177">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-177">The default is the current user.</span></span>
<span data-ttu-id="2a7ab-178">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ».</span><span class="sxs-lookup"><span data-stu-id="2a7ab-178">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="2a7ab-179">Vous pouvez également entrer un objet PSCredential, tel que celui généré par l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-179">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="2a7ab-180">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-180">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="2a7ab-181">-Dialecte</span><span class="sxs-lookup"><span data-stu-id="2a7ab-181">-Dialect</span></span>

<span data-ttu-id="2a7ab-182">Spécifie le dialecte à utiliser dans le prédicat de filtre.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-182">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="2a7ab-183">Ce peut être n'importe quel dialecte pris en charge par le service distant.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-183">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="2a7ab-184">Les alias suivants peuvent être utilisés pour l'URI de dialecte :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-184">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="2a7ab-185">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="2a7ab-185">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="2a7ab-186">Sélection `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="2a7ab-186">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="2a7ab-187">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="2a7ab-187">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a7ab-188">-FilePath</span><span class="sxs-lookup"><span data-stu-id="2a7ab-188">-FilePath</span></span>

<span data-ttu-id="2a7ab-189">Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-189">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="2a7ab-190">Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-190">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="2a7ab-191">Par exemple, la commande suivante utilise le paramètre de FilePath :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-191">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="2a7ab-192">Cette commande appelle la méthode StopService sur le service Spouleur à l'aide des entrées fournies par un fichier.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-192">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="2a7ab-193">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-193">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a7ab-194">-Fragment</span><span class="sxs-lookup"><span data-stu-id="2a7ab-194">-Fragment</span></span>

<span data-ttu-id="2a7ab-195">Spécifie une section à l'intérieur de l'instance qui doit être mise à jour ou récupérée pour l'opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-195">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="2a7ab-196">Par exemple, pour obtenir l'état d'un service Spouleur, spécifiez « -Fragment Status ».</span><span class="sxs-lookup"><span data-stu-id="2a7ab-196">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="2a7ab-197">-A</span><span class="sxs-lookup"><span data-stu-id="2a7ab-197">-OptionSet</span></span>

<span data-ttu-id="2a7ab-198">Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-198">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="2a7ab-199">Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-199">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="2a7ab-200">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-200">Any number of options can be specified.</span></span>

<span data-ttu-id="2a7ab-201">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-201">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="2a7ab-202">-OptionSet @{a=1;b=2;c=3}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-202">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="2a7ab-203">-Port</span><span class="sxs-lookup"><span data-stu-id="2a7ab-203">-Port</span></span>

<span data-ttu-id="2a7ab-204">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-204">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="2a7ab-205">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-205">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="2a7ab-206">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-206">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="2a7ab-207">Lorsque vous utilisez le protocole HTTPS, la valeur du paramètre ComputerName doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-207">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="2a7ab-208">Toutefois, si le paramètre SkipCNCheck est spécifié dans le cadre du paramètre SessionOption, le nom commun du certificat du serveur n'a pas à correspondre au nom d'hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-208">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="2a7ab-209">Le paramètre SkipCNCheck doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-209">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="2a7ab-210">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="2a7ab-210">-ResourceURI</span></span>

<span data-ttu-id="2a7ab-211">Contient l'URI de l'instance ou de la classe de ressource.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-211">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="2a7ab-212">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-212">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="2a7ab-213">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-213">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="2a7ab-214">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-214">For example:</span></span>

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

### <span data-ttu-id="2a7ab-215">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="2a7ab-215">-SelectorSet</span></span>

<span data-ttu-id="2a7ab-216">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-216">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="2a7ab-217">Le paramètre SelectorSet est utilisé lorsqu'il existe plusieurs instances de la ressource.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-217">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="2a7ab-218">La valeur du paramètre SelectorSet doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-218">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="2a7ab-219">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="2a7ab-219">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="2a7ab-220">-SelectorSet @{Name="WinRM";ID="yyy"}</span><span class="sxs-lookup"><span data-stu-id="2a7ab-220">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2a7ab-221">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="2a7ab-221">-SessionOption</span></span>

<span data-ttu-id="2a7ab-222">Définit un ensemble d'options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-222">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="2a7ab-223">Entrez un objet SessionOption que vous créez à l'aide de l'applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-223">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="2a7ab-224">Pour plus d'informations sur les options disponibles, consultez New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-224">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="2a7ab-225">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="2a7ab-225">-UseSSL</span></span>

<span data-ttu-id="2a7ab-226">Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-226">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="2a7ab-227">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-227">By default, SSL is not used.</span></span>

<span data-ttu-id="2a7ab-228">WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-228">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="2a7ab-229">Le paramètre UseSSL vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-229">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="2a7ab-230">Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-230">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="2a7ab-231">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="2a7ab-231">-ValueSet</span></span>

<span data-ttu-id="2a7ab-232">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-232">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="2a7ab-233">Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-233">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="2a7ab-234">La valeur du paramètre ValueSet doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-234">The value of the ValueSet parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a7ab-235">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a7ab-235">CommonParameters</span></span>

<span data-ttu-id="2a7ab-236">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-236">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a7ab-237">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2a7ab-237">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2a7ab-238">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2a7ab-238">INPUTS</span></span>

### <span data-ttu-id="2a7ab-239">None</span><span class="sxs-lookup"><span data-stu-id="2a7ab-239">None</span></span>

<span data-ttu-id="2a7ab-240">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-240">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="2a7ab-241">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2a7ab-241">OUTPUTS</span></span>

### <span data-ttu-id="2a7ab-242">None</span><span class="sxs-lookup"><span data-stu-id="2a7ab-242">None</span></span>

<span data-ttu-id="2a7ab-243">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="2a7ab-243">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2a7ab-244">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2a7ab-244">NOTES</span></span>

## <span data-ttu-id="2a7ab-245">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2a7ab-245">RELATED LINKS</span></span>

[<span data-ttu-id="2a7ab-246">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2a7ab-246">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="2a7ab-247">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2a7ab-247">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="2a7ab-248">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="2a7ab-248">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="2a7ab-249">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2a7ab-249">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="2a7ab-250">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2a7ab-250">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="2a7ab-251">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2a7ab-251">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="2a7ab-252">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="2a7ab-252">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="2a7ab-253">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2a7ab-253">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="2a7ab-254">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="2a7ab-254">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="2a7ab-255">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2a7ab-255">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="2a7ab-256">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="2a7ab-256">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="2a7ab-257">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="2a7ab-257">Test-WSMan</span></span>](Test-WSMan.md)


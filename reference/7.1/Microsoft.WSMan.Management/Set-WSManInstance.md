---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 9060f683372617b3a01365ceb81668c75986f46d
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205641"
---
# <span data-ttu-id="30c77-103">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="30c77-103">Set-WSManInstance</span></span>

## <span data-ttu-id="30c77-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="30c77-104">SYNOPSIS</span></span>
<span data-ttu-id="30c77-105">Modifie les informations de gestion qui sont associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="30c77-105">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="30c77-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30c77-106">SYNTAX</span></span>

### <span data-ttu-id="30c77-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="30c77-107">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="30c77-108">URI</span><span class="sxs-lookup"><span data-stu-id="30c77-108">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="30c77-109">Description</span><span class="sxs-lookup"><span data-stu-id="30c77-109">DESCRIPTION</span></span>

<span data-ttu-id="30c77-110">L'applet de commande Set-WSManInstance modifie les informations de gestion qui sont associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="30c77-110">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="30c77-111">Cette applet de commande utilise la couche de connexion/transport WinRM pour modifier les informations.</span><span class="sxs-lookup"><span data-stu-id="30c77-111">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="30c77-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="30c77-112">EXAMPLES</span></span>

### <span data-ttu-id="30c77-113">Exemple 1 : désactiver un écouteur sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="30c77-113">Example 1: Disable a listener on the local computer</span></span>

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

<span data-ttu-id="30c77-114">Cette commande désactive l'écouteur https sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="30c77-114">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="30c77-115">Important : le paramètre *ValueSet* respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="30c77-115">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="30c77-116">Par exemple, dans cette commande,</span><span class="sxs-lookup"><span data-stu-id="30c77-116">For example, in this command,</span></span>

<span data-ttu-id="30c77-117">Cette opération échoue : `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="30c77-117">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="30c77-118">Cela s’effectue comme suit : `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="30c77-118">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="30c77-119">Exemple 2 : définir la taille d’enveloppe maximale sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="30c77-119">Example 2: Set the maximum envelope size on the local computer</span></span>

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

<span data-ttu-id="30c77-120">Cette commande affecte à MaxEnvelopeSizekb la valeur 200 sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="30c77-120">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="30c77-121">Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="30c77-121">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="30c77-122">Ainsi, voici ce qui se passe avec la commande ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="30c77-122">For example, using the above command.</span></span>

<span data-ttu-id="30c77-123">Échec :-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="30c77-123">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="30c77-124">Cette opération a échoué :-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="30c77-124">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="30c77-125">Exemple 3 : désactiver un écouteur sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="30c77-125">Example 3: Disable a listener on a remote computer</span></span>

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

<span data-ttu-id="30c77-126">Cette commande désactive l'écouteur https sur l'ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="30c77-126">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="30c77-127">Important : le paramètre ValueSet respecte la casse lors de la correspondance avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="30c77-127">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="30c77-128">Ainsi, voici ce qui se passe avec la commande ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="30c77-128">For example, using the above command.</span></span>

<span data-ttu-id="30c77-129">Échec :-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="30c77-129">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="30c77-130">Cette opération a échoué :-ValueSet @ {Enabled = "false"}</span><span class="sxs-lookup"><span data-stu-id="30c77-130">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="30c77-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30c77-131">PARAMETERS</span></span>

### <span data-ttu-id="30c77-132">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="30c77-132">-ApplicationName</span></span>

<span data-ttu-id="30c77-133">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="30c77-133">Specifies the application name in the connection.</span></span>
<span data-ttu-id="30c77-134">La valeur par défaut du paramètre ApplicationName est « WSMAN ».</span><span class="sxs-lookup"><span data-stu-id="30c77-134">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="30c77-135">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="30c77-135">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="30c77-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="30c77-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="30c77-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30c77-137">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="30c77-138">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="30c77-138">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="30c77-139">La valeur par défaut « WSMAN » est appropriée pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="30c77-139">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="30c77-140">Ce paramètre est conçu pour être utilisé lorsque de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30c77-140">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="30c77-141">Dans ce cas, IIS héberge WS-Management (Web Services for Management) pour plus d'efficacité.</span><span class="sxs-lookup"><span data-stu-id="30c77-141">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="30c77-142">-Authentification</span><span class="sxs-lookup"><span data-stu-id="30c77-142">-Authentication</span></span>

<span data-ttu-id="30c77-143">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="30c77-143">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="30c77-144">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="30c77-144">Possible values are:</span></span>

- <span data-ttu-id="30c77-145">De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="30c77-145">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="30c77-146">Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="30c77-146">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="30c77-147">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="30c77-147">This is the default.</span></span>
- <span data-ttu-id="30c77-148">Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.</span><span class="sxs-lookup"><span data-stu-id="30c77-148">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="30c77-149">Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide de certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="30c77-149">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="30c77-150">Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="30c77-150">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="30c77-151">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="30c77-151">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="30c77-152">CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="30c77-152">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="30c77-153">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="30c77-153">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="30c77-154">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="30c77-154">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="30c77-155">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="30c77-155">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="30c77-156">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="30c77-156">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="30c77-157">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="30c77-157">-CertificateThumbprint</span></span>

<span data-ttu-id="30c77-158">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="30c77-158">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="30c77-159">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="30c77-159">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="30c77-160">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="30c77-160">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="30c77-161">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="30c77-161">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="30c77-162">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30c77-162">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="30c77-163">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="30c77-163">-ComputerName</span></span>

<span data-ttu-id="30c77-164">Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="30c77-164">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="30c77-165">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="30c77-165">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="30c77-166">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="30c77-166">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="30c77-167">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="30c77-167">The local computer is the default.</span></span>
<span data-ttu-id="30c77-168">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="30c77-168">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="30c77-169">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="30c77-169">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="30c77-170">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="30c77-170">-ConnectionURI</span></span>

<span data-ttu-id="30c77-171">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="30c77-171">Specifies the connection endpoint.</span></span>
<span data-ttu-id="30c77-172">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="30c77-172">The format of this string is:</span></span>

<span data-ttu-id="30c77-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="30c77-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="30c77-174">La chaîne suivante est une valeur au format correct pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="30c77-174">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="30c77-175">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="30c77-175">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="30c77-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="30c77-176">-Credential</span></span>

<span data-ttu-id="30c77-177">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="30c77-177">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="30c77-178">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="30c77-178">The default is the current user.</span></span>
<span data-ttu-id="30c77-179">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou « User@Domain.com ».</span><span class="sxs-lookup"><span data-stu-id="30c77-179">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="30c77-180">Vous pouvez également entrer un objet PSCredential, tel que celui généré par l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="30c77-180">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="30c77-181">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="30c77-181">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="30c77-182">-Dialecte</span><span class="sxs-lookup"><span data-stu-id="30c77-182">-Dialect</span></span>

<span data-ttu-id="30c77-183">Spécifie le dialecte à utiliser dans le prédicat de filtre.</span><span class="sxs-lookup"><span data-stu-id="30c77-183">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="30c77-184">Ce peut être n'importe quel dialecte pris en charge par le service distant.</span><span class="sxs-lookup"><span data-stu-id="30c77-184">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="30c77-185">Les alias suivants peuvent être utilisés pour l'URI de dialecte :</span><span class="sxs-lookup"><span data-stu-id="30c77-185">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="30c77-186">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="30c77-186">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="30c77-187">Sélection `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="30c77-187">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="30c77-188">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="30c77-188">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

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

### <span data-ttu-id="30c77-189">-FilePath</span><span class="sxs-lookup"><span data-stu-id="30c77-189">-FilePath</span></span>

<span data-ttu-id="30c77-190">Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="30c77-190">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="30c77-191">Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="30c77-191">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="30c77-192">Par exemple, la commande suivante utilise le paramètre de FilePath :</span><span class="sxs-lookup"><span data-stu-id="30c77-192">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="30c77-193">Cette commande appelle la méthode StopService sur le service Spouleur à l'aide des entrées fournies par un fichier.</span><span class="sxs-lookup"><span data-stu-id="30c77-193">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="30c77-194">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="30c77-194">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="30c77-195">-Fragment</span><span class="sxs-lookup"><span data-stu-id="30c77-195">-Fragment</span></span>

<span data-ttu-id="30c77-196">Spécifie une section à l'intérieur de l'instance qui doit être mise à jour ou récupérée pour l'opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="30c77-196">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="30c77-197">Par exemple, pour obtenir l'état d'un service Spouleur, spécifiez « -Fragment Status ».</span><span class="sxs-lookup"><span data-stu-id="30c77-197">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="30c77-198">-A</span><span class="sxs-lookup"><span data-stu-id="30c77-198">-OptionSet</span></span>

<span data-ttu-id="30c77-199">Transmet un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="30c77-199">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="30c77-200">Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="30c77-200">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="30c77-201">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="30c77-201">Any number of options can be specified.</span></span>

<span data-ttu-id="30c77-202">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="30c77-202">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="30c77-203">-OptionSet @{a=1;b=2;c=3}</span><span class="sxs-lookup"><span data-stu-id="30c77-203">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="30c77-204">-Port</span><span class="sxs-lookup"><span data-stu-id="30c77-204">-Port</span></span>

<span data-ttu-id="30c77-205">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="30c77-205">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="30c77-206">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="30c77-206">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="30c77-207">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="30c77-207">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="30c77-208">Lorsque vous utilisez le protocole HTTPS, la valeur du paramètre ComputerName doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="30c77-208">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="30c77-209">Toutefois, si le paramètre SkipCNCheck est spécifié dans le cadre du paramètre SessionOption, le nom commun du certificat du serveur n'a pas à correspondre au nom d'hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="30c77-209">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="30c77-210">Le paramètre SkipCNCheck doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="30c77-210">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="30c77-211">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="30c77-211">-ResourceURI</span></span>

<span data-ttu-id="30c77-212">Contient l'URI de l'instance ou de la classe de ressource.</span><span class="sxs-lookup"><span data-stu-id="30c77-212">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="30c77-213">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="30c77-213">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="30c77-214">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="30c77-214">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="30c77-215">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30c77-215">For example:</span></span>

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

### <span data-ttu-id="30c77-216">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="30c77-216">-SelectorSet</span></span>

<span data-ttu-id="30c77-217">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="30c77-217">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="30c77-218">Le paramètre SelectorSet est utilisé lorsqu'il existe plusieurs instances de la ressource.</span><span class="sxs-lookup"><span data-stu-id="30c77-218">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="30c77-219">La valeur du paramètre SelectorSet doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="30c77-219">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="30c77-220">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="30c77-220">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="30c77-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span><span class="sxs-lookup"><span data-stu-id="30c77-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

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

### <span data-ttu-id="30c77-222">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="30c77-222">-SessionOption</span></span>

<span data-ttu-id="30c77-223">Définit un ensemble d'options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="30c77-223">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="30c77-224">Entrez un objet SessionOption que vous créez à l'aide de l'applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="30c77-224">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="30c77-225">Pour plus d'informations sur les options disponibles, consultez New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="30c77-225">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="30c77-226">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="30c77-226">-UseSSL</span></span>

<span data-ttu-id="30c77-227">Spécifie que le protocole SSL (Secure Sockets Layer) doit être utilisé pour établir une connexion à l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="30c77-227">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="30c77-228">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="30c77-228">By default, SSL is not used.</span></span>

<span data-ttu-id="30c77-229">WS-Management chiffre tout le contenu de Windows PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="30c77-229">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="30c77-230">Le paramètre UseSSL vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="30c77-230">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="30c77-231">Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="30c77-231">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="30c77-232">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="30c77-232">-ValueSet</span></span>

<span data-ttu-id="30c77-233">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="30c77-233">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="30c77-234">Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="30c77-234">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="30c77-235">La valeur du paramètre ValueSet doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="30c77-235">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="30c77-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30c77-236">CommonParameters</span></span>

<span data-ttu-id="30c77-237">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30c77-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30c77-238">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="30c77-238">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="30c77-239">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="30c77-239">INPUTS</span></span>

### <span data-ttu-id="30c77-240">Aucun</span><span class="sxs-lookup"><span data-stu-id="30c77-240">None</span></span>

<span data-ttu-id="30c77-241">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="30c77-241">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="30c77-242">SORTIES</span><span class="sxs-lookup"><span data-stu-id="30c77-242">OUTPUTS</span></span>

### <span data-ttu-id="30c77-243">Aucun</span><span class="sxs-lookup"><span data-stu-id="30c77-243">None</span></span>

<span data-ttu-id="30c77-244">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="30c77-244">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="30c77-245">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="30c77-245">NOTES</span></span>

## <span data-ttu-id="30c77-246">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="30c77-246">RELATED LINKS</span></span>

[<span data-ttu-id="30c77-247">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="30c77-247">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="30c77-248">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="30c77-248">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="30c77-249">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="30c77-249">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="30c77-250">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="30c77-250">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="30c77-251">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="30c77-251">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="30c77-252">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="30c77-252">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="30c77-253">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="30c77-253">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="30c77-254">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="30c77-254">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="30c77-255">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="30c77-255">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="30c77-256">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="30c77-256">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="30c77-257">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="30c77-257">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="30c77-258">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="30c77-258">Test-WSMan</span></span>](Test-WSMan.md)


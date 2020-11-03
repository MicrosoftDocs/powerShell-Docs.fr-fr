---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: b969449d3e2e888138f783c17e16fa696fe40efe
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205586"
---
# <span data-ttu-id="8b174-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8b174-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="8b174-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8b174-104">SYNOPSIS</span></span>
<span data-ttu-id="8b174-105">Appelle une action sur l'objet qui est spécifié par l'URI de ressource et par les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="8b174-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="8b174-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b174-106">SYNTAX</span></span>

### <span data-ttu-id="8b174-107">URI (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8b174-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="8b174-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8b174-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="8b174-109">Description</span><span class="sxs-lookup"><span data-stu-id="8b174-109">DESCRIPTION</span></span>
<span data-ttu-id="8b174-110">**Invoke-wsmanaction** exécute une action sur l’objet spécifié par RESOURCE_URI, où les paramètres sont spécifiés par les paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="8b174-110">The **Invoke-WSManAction** runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="8b174-111">Cette applet de commande utilise la couche de connexion/transport WSMan pour exécuter l'action.</span><span class="sxs-lookup"><span data-stu-id="8b174-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="8b174-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8b174-112">EXAMPLES</span></span>

### <span data-ttu-id="8b174-113">Exemple 1 : appeler une méthode</span><span class="sxs-lookup"><span data-stu-id="8b174-113">Example 1: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="8b174-114">Cette commande appelle la méthode **StartService** de l’instance de classe WMI Win32_Service qui correspond au service du spouleur.</span><span class="sxs-lookup"><span data-stu-id="8b174-114">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="8b174-115">La valeur de retour indique si l'action a réussi.</span><span class="sxs-lookup"><span data-stu-id="8b174-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="8b174-116">Si c'est le cas, la valeur de retour est 0.</span><span class="sxs-lookup"><span data-stu-id="8b174-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="8b174-117">Une valeur de retour de 5 indique que le service est déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="8b174-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="8b174-118">Exemple 2 : appeler une méthode</span><span class="sxs-lookup"><span data-stu-id="8b174-118">Example 2: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="8b174-119">Cette commande appelle la méthode **StopService** sur le service Spooler en utilisant l’entrée d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="8b174-119">This command calls the **StopService** method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="8b174-120">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="8b174-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### <span data-ttu-id="8b174-121">Exemple 3 : appeler une méthode avec des valeurs de paramètre spécifiées</span><span class="sxs-lookup"><span data-stu-id="8b174-121">Example 3: Invoke a method with specified parameter values</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="8b174-122">Cette commande appelle la méthode **Create** de la classe Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="8b174-122">This command calls the **Create** method of the Win32_Process class.</span></span>
<span data-ttu-id="8b174-123">Il passe à la méthode deux valeurs de paramètre, Notepad.exe et C:\.</span><span class="sxs-lookup"><span data-stu-id="8b174-123">It passes the method two parameter values, Notepad.exe and C:\.</span></span>
<span data-ttu-id="8b174-124">Par conséquent, un nouveau processus est créé pour exécuter le bloc-notes et le répertoire actif du nouveau processus est défini sur C:\.</span><span class="sxs-lookup"><span data-stu-id="8b174-124">As a result, a new process is created to run Notepad, and the current directory of the new process is set to C:\.</span></span>

### <span data-ttu-id="8b174-125">Exemple 4 : appeler une méthode sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8b174-125">Example 4: Invoke a method on a remote computer</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="8b174-126">Cette commande appelle la méthode **StartService** de l’instance de classe WMI Win32_Service qui correspond au service du spouleur.</span><span class="sxs-lookup"><span data-stu-id="8b174-126">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="8b174-127">Étant donné que le paramètre *ComputerName* est spécifié, la commande s’exécute sur l’ordinateur SERVEUR01 distant.</span><span class="sxs-lookup"><span data-stu-id="8b174-127">Because the *ComputerName* parameter is specified, the command runs against the remote server01 computer.</span></span>

## <span data-ttu-id="8b174-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b174-128">PARAMETERS</span></span>

### <span data-ttu-id="8b174-129">-Action</span><span class="sxs-lookup"><span data-stu-id="8b174-129">-Action</span></span>
<span data-ttu-id="8b174-130">Spécifie la méthode à exécuter sur l’objet de gestion spécifié par l’ResourceURI et les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="8b174-130">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8b174-131">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="8b174-131">-ApplicationName</span></span>
<span data-ttu-id="8b174-132">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="8b174-132">Specifies the application name in the connection.</span></span>
<span data-ttu-id="8b174-133">La valeur par défaut du paramètre *applicationName* est WSMan.</span><span class="sxs-lookup"><span data-stu-id="8b174-133">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="8b174-134">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="8b174-134">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="8b174-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="8b174-135">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="8b174-136">Par exemple : `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="8b174-136">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="8b174-137">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b174-137">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="8b174-138">Ce paramètre par défaut de WSMAN est adapté à la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="8b174-138">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="8b174-139">Ce paramètre est conçu pour être utilisé si de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b174-139">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="8b174-140">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="8b174-140">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="8b174-141">-Authentification</span><span class="sxs-lookup"><span data-stu-id="8b174-141">-Authentication</span></span>
<span data-ttu-id="8b174-142">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="8b174-142">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="8b174-143">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="8b174-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8b174-144">De base.</span><span class="sxs-lookup"><span data-stu-id="8b174-144">Basic.</span></span>
<span data-ttu-id="8b174-145">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="8b174-145">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="8b174-146">Par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b174-146">Default.</span></span>
<span data-ttu-id="8b174-147">Utilisez la méthode d'authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="8b174-147">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="8b174-148">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b174-148">This is the default.</span></span>
- <span data-ttu-id="8b174-149">Digest.</span><span class="sxs-lookup"><span data-stu-id="8b174-149">Digest.</span></span>
<span data-ttu-id="8b174-150">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="8b174-150">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="8b174-151">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8b174-151">Kerberos.</span></span>
<span data-ttu-id="8b174-152">L'ordinateur client et le serveur s'authentifient mutuellement à l'aide des certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8b174-152">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="8b174-153">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="8b174-153">Negotiate.</span></span>
<span data-ttu-id="8b174-154">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="8b174-154">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="8b174-155">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8b174-155">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="8b174-156">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="8b174-156">CredSSP.</span></span>
<span data-ttu-id="8b174-157">Utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet aux utilisateurs de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="8b174-157">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="8b174-158">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="8b174-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="8b174-159">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8b174-159">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="8b174-160">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="8b174-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="8b174-161">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="8b174-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="8b174-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="8b174-162">-CertificateThumbprint</span></span>
<span data-ttu-id="8b174-163">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="8b174-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8b174-164">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="8b174-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="8b174-165">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="8b174-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="8b174-166">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="8b174-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="8b174-167">Pour obtenir une empreinte numérique de certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b174-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="8b174-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8b174-168">-ComputerName</span></span>
<span data-ttu-id="8b174-169">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="8b174-169">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="8b174-170">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="8b174-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="8b174-171">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8b174-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="8b174-172">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b174-172">The local computer is the default.</span></span>
<span data-ttu-id="8b174-173">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="8b174-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="8b174-174">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8b174-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="8b174-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="8b174-175">-ConnectionURI</span></span>
<span data-ttu-id="8b174-176">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="8b174-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="8b174-177">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="8b174-177">The format of this string is as follows:</span></span>

<span data-ttu-id="8b174-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="8b174-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="8b174-179">La chaîne suivante est une valeur correctement mise en forme pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="8b174-179">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="8b174-180">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="8b174-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="8b174-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="8b174-181">-Credential</span></span>
<span data-ttu-id="8b174-182">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="8b174-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8b174-183">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8b174-183">The default is the current user.</span></span>
<span data-ttu-id="8b174-184">Tapez un nom d’utilisateur, tel que User01, Domaine01\utilisateur01 ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="8b174-184">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="8b174-185">Ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="8b174-185">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="8b174-186">Lorsque vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8b174-186">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="8b174-187">-FilePath</span><span class="sxs-lookup"><span data-stu-id="8b174-187">-FilePath</span></span>
<span data-ttu-id="8b174-188">Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="8b174-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="8b174-189">Vous spécifiez la ressource de gestion à l’aide du paramètre *resourceuri* et du paramètre *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="8b174-189">You specify the management resource by using the *ResourceURI* parameter and the *SelectorSet* parameter.</span></span>
<span data-ttu-id="8b174-190">Par exemple, la commande suivante utilise le paramètre *filePath* :</span><span class="sxs-lookup"><span data-stu-id="8b174-190">For example, the following command uses the *FilePath* parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="8b174-191">Cette commande appelle la méthode **StopService** sur le service **Spooler** en utilisant l’entrée d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="8b174-191">This command calls the **StopService** method on the **Spooler** service by using input from a file.</span></span>
<span data-ttu-id="8b174-192">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="8b174-192">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="8b174-193">-A</span><span class="sxs-lookup"><span data-stu-id="8b174-193">-OptionSet</span></span>
<span data-ttu-id="8b174-194">Spécifie un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="8b174-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="8b174-195">Ces commutateurs sont similaires à ceux utilisés dans les interpréteurs de ligne de commande, car ils sont spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="8b174-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="8b174-196">N'importe quel nombre d'options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="8b174-196">Any number of options can be specified.</span></span>

<span data-ttu-id="8b174-197">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="8b174-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8b174-198">-Port</span><span class="sxs-lookup"><span data-stu-id="8b174-198">-Port</span></span>
<span data-ttu-id="8b174-199">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="8b174-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="8b174-200">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="8b174-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="8b174-201">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="8b174-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="8b174-202">Lorsque vous utilisez le protocole HTTPs comme transport, la valeur du paramètre *ComputerName* doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="8b174-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="8b174-203">Toutefois, si le paramètre *SkipCNCheck* est spécifié dans le cadre du paramètre *SessionOption* , le nom commun du certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="8b174-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="8b174-204">Le paramètre *SkipCNCheck* doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="8b174-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="8b174-205">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="8b174-205">-ResourceURI</span></span>
<span data-ttu-id="8b174-206">Spécifie l’URI de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="8b174-206">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="8b174-207">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8b174-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="8b174-208">Un URI se compose d’un préfixe et d’un chemin d’accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="8b174-208">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="8b174-209">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b174-209">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8b174-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="8b174-210">-SelectorSet</span></span>
<span data-ttu-id="8b174-211">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="8b174-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="8b174-212">*SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="8b174-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="8b174-213">La valeur de *SelectorSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b174-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="8b174-214">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="8b174-214">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8b174-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="8b174-215">-SessionOption</span></span>
<span data-ttu-id="8b174-216">Spécifie les options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="8b174-216">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="8b174-217">Entrez un objet **SessionOption** que vous créez à l’aide de l’applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="8b174-217">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="8b174-218">Pour plus d’informations sur les options disponibles, tapez `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="8b174-218">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="8b174-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="8b174-219">-UseSSL</span></span>
<span data-ttu-id="8b174-220">Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8b174-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="8b174-221">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="8b174-221">By default, SSL is not used.</span></span>

<span data-ttu-id="8b174-222">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="8b174-222">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="8b174-223">Le paramètre *UseSSL* vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="8b174-223">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="8b174-224">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="8b174-224">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="8b174-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="8b174-225">-ValueSet</span></span>
<span data-ttu-id="8b174-226">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="8b174-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="8b174-227">Vous spécifiez la ressource de gestion à l’aide de *resourceuri* et *SelectorSet* .</span><span class="sxs-lookup"><span data-stu-id="8b174-227">You specify the management resource by using *ResourceURI* and *SelectorSet* .</span></span>
<span data-ttu-id="8b174-228">La valeur du paramètre *ValueSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8b174-228">The value of the *ValueSet* parameter must be a hash table.</span></span>

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

### <span data-ttu-id="8b174-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b174-229">CommonParameters</span></span>
<span data-ttu-id="8b174-230">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b174-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b174-231">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b174-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b174-232">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8b174-232">INPUTS</span></span>

### <span data-ttu-id="8b174-233">Aucun</span><span class="sxs-lookup"><span data-stu-id="8b174-233">None</span></span>
<span data-ttu-id="8b174-234">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="8b174-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="8b174-235">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8b174-235">OUTPUTS</span></span>

### <span data-ttu-id="8b174-236">Aucun</span><span class="sxs-lookup"><span data-stu-id="8b174-236">None</span></span>
<span data-ttu-id="8b174-237">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8b174-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8b174-238">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8b174-238">NOTES</span></span>

## <span data-ttu-id="8b174-239">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8b174-239">RELATED LINKS</span></span>

[<span data-ttu-id="8b174-240">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="8b174-240">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="8b174-241">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8b174-241">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="8b174-242">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="8b174-242">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="8b174-243">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8b174-243">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="8b174-244">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8b174-244">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="8b174-245">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8b174-245">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="8b174-246">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8b174-246">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="8b174-247">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="8b174-247">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="8b174-248">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8b174-248">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="8b174-249">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8b174-249">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="8b174-250">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="8b174-250">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="8b174-251">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="8b174-251">Test-WSMan</span></span>](Test-WSMan.md)

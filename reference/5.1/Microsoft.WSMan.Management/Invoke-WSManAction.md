---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 1eeeb912ab32ec5334959daba1e352f20fec15b1
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208686"
---
# <span data-ttu-id="f0553-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="f0553-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="f0553-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f0553-104">SYNOPSIS</span></span>
<span data-ttu-id="f0553-105">Appelle une action sur l'objet qui est spécifié par l'URI de ressource et par les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="f0553-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="f0553-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0553-106">SYNTAX</span></span>

### <span data-ttu-id="f0553-107">URI (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0553-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="f0553-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="f0553-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="f0553-109">Description</span><span class="sxs-lookup"><span data-stu-id="f0553-109">DESCRIPTION</span></span>

<span data-ttu-id="f0553-110">Invoke-WSManAction exécute une action sur l'objet spécifié par URI_RESSOURCE, où les paramètres sont spécifiés par les paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="f0553-110">The Invoke-WSManAction runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="f0553-111">Cette applet de commande utilise la couche de connexion/transport WSMan pour exécuter l'action.</span><span class="sxs-lookup"><span data-stu-id="f0553-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="f0553-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f0553-112">EXAMPLES</span></span>

### <span data-ttu-id="f0553-113">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="f0553-113">Example 1</span></span>

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

<span data-ttu-id="f0553-114">Cette commande appelle la méthode StartService de l'instance de classe WMI Win32_Service qui correspond au service Spooler.</span><span class="sxs-lookup"><span data-stu-id="f0553-114">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="f0553-115">La valeur de retour indique si l'action a réussi.</span><span class="sxs-lookup"><span data-stu-id="f0553-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="f0553-116">Si c'est le cas, la valeur de retour est 0.</span><span class="sxs-lookup"><span data-stu-id="f0553-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="f0553-117">Une valeur de retour de 5 indique que le service est déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="f0553-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="f0553-118">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="f0553-118">Example 2</span></span>

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

<span data-ttu-id="f0553-119">Cette commande appelle la méthode StopService sur le service Spouleur à l'aide des entrées fournies par un fichier.</span><span class="sxs-lookup"><span data-stu-id="f0553-119">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="f0553-120">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="f0553-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

<span data-ttu-id="f0553-121">La valeur de retour indique si l'action a réussi.</span><span class="sxs-lookup"><span data-stu-id="f0553-121">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="f0553-122">Si c'est le cas, la valeur de retour est 0.</span><span class="sxs-lookup"><span data-stu-id="f0553-122">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="f0553-123">Une valeur de retour de 5 indique que le service est déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="f0553-123">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="f0553-124">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="f0553-124">Example 3</span></span>

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

<span data-ttu-id="f0553-125">Cette commande appelle la méthode Create de la classe Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="f0553-125">This command calls the Create method of the Win32_Process class.</span></span>
<span data-ttu-id="f0553-126">Il passe à la méthode deux valeurs de paramètre, Notepad.exe et «C : \" .</span><span class="sxs-lookup"><span data-stu-id="f0553-126">It passes the method two parameter values, Notepad.exe and "C:\".</span></span>
<span data-ttu-id="f0553-127">Par conséquent, un nouveau processus est créé pour exécuter le bloc-notes et le répertoire actif du nouveau processus est défini sur «C : \" .</span><span class="sxs-lookup"><span data-stu-id="f0553-127">As a result, a new process is created to run Notepad, and the current directory of the new process is set to "C:\".</span></span>

### <span data-ttu-id="f0553-128">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="f0553-128">Example 4</span></span>

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

<span data-ttu-id="f0553-129">Cette commande appelle la méthode StartService de l'instance de classe WMI Win32_Service qui correspond au service Spooler.</span><span class="sxs-lookup"><span data-stu-id="f0553-129">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="f0553-130">Comme le paramètre ComputerName est spécifié, la commande s'exécute sur l'ordinateur distant server01.</span><span class="sxs-lookup"><span data-stu-id="f0553-130">Because the ComputerName parameter is specified, the command runs against the remote server01 computer.</span></span>

<span data-ttu-id="f0553-131">La valeur de retour indique si l'action a réussi.</span><span class="sxs-lookup"><span data-stu-id="f0553-131">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="f0553-132">Si c'est le cas, la valeur de retour est 0.</span><span class="sxs-lookup"><span data-stu-id="f0553-132">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="f0553-133">Une valeur de retour de 5 indique que le service est déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="f0553-133">A return value of 5 indicates that the service is already started.</span></span>

## <span data-ttu-id="f0553-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0553-134">PARAMETERS</span></span>

### <span data-ttu-id="f0553-135">-Action</span><span class="sxs-lookup"><span data-stu-id="f0553-135">-Action</span></span>

<span data-ttu-id="f0553-136">Spécifie la méthode à exécuter sur l’objet de gestion spécifié par l’ResourceURI et les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="f0553-136">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

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

### <span data-ttu-id="f0553-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="f0553-137">-ApplicationName</span></span>

<span data-ttu-id="f0553-138">Spécifie le nom d'application de la connexion.</span><span class="sxs-lookup"><span data-stu-id="f0553-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="f0553-139">La valeur par défaut du paramètre ApplicationName est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="f0553-139">The default value of the ApplicationName parameter is WSMAN.</span></span>
<span data-ttu-id="f0553-140">L'identificateur complet du point de terminaison distant est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="f0553-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="f0553-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="f0553-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="f0553-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f0553-142">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="f0553-143">Internet Information Services, qui héberge la session, transfère les demandes avec ce point de terminaison à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0553-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="f0553-144">La valeur par défaut « WSMAN » est appropriée pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="f0553-144">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="f0553-145">Ce paramètre est conçu pour être utilisé quand de nombreux ordinateurs établissent des connexions à distance à un ordinateur qui exécute Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0553-145">This parameter is designed to be used when numerous computers establish remote connections to one computer running Windows PowerShell.</span></span>
<span data-ttu-id="f0553-146">Dans ce cas, IIS héberge Web Services for Management (WS-Management) pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="f0553-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="f0553-147">-Authentification</span><span class="sxs-lookup"><span data-stu-id="f0553-147">-Authentication</span></span>

<span data-ttu-id="f0553-148">Spécifie le mécanisme d’authentification à utiliser au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="f0553-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="f0553-149">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0553-149">Possible values are:</span></span>

- <span data-ttu-id="f0553-150">De base : le mode de base est un modèle dans lequel le nom d’utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="f0553-150">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="f0553-151">Par défaut : utilisez la méthode d’authentification implémentée par le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="f0553-151">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="f0553-152">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f0553-152">This is the default.</span></span>
- <span data-ttu-id="f0553-153">Digest : Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour le défi.</span><span class="sxs-lookup"><span data-stu-id="f0553-153">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="f0553-154">Kerberos : l’ordinateur client et le serveur s’authentifient mutuellement à l’aide de certificats Kerberos.</span><span class="sxs-lookup"><span data-stu-id="f0553-154">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="f0553-155">Negotiate : Negotiate est un modèle de stimulation-réponse qui négocie avec le serveur ou le proxy pour déterminer le schéma à utiliser pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="f0553-155">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="f0553-156">Par exemple, cette valeur de paramètre permet à la négociation de déterminer si le protocole Kerberos ou NTLM est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f0553-156">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="f0553-157">CredSSP : utilisez l’authentification CredSSP (Credential Security Support Provider), qui permet à l’utilisateur de déléguer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="f0553-157">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="f0553-158">Cette option est conçue pour les commandes qui s'exécutent sur un ordinateur distant, mais qui collectent des données ou exécutent des commandes supplémentaires à partir d'autres ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f0553-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="f0553-159">ATTENTION : CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f0553-159">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="f0553-160">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="f0553-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="f0553-161">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="f0553-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="f0553-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f0553-162">-CertificateThumbprint</span></span>

<span data-ttu-id="f0553-163">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="f0553-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="f0553-164">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="f0553-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f0553-165">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="f0553-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="f0553-166">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="f0553-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="f0553-167">Pour obtenir une empreinte numérique du certificat, utilisez la commande Get-Item ou Get-ChildItem dans le lecteur de certificats de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0553-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="f0553-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f0553-168">-ComputerName</span></span>

<span data-ttu-id="f0553-169">Spécifie l'ordinateur sur lequel vous souhaitez exécuter l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="f0553-169">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="f0553-170">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="f0553-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="f0553-171">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f0553-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="f0553-172">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f0553-172">The local computer is the default.</span></span>
<span data-ttu-id="f0553-173">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="f0553-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="f0553-174">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0553-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="f0553-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="f0553-175">-ConnectionURI</span></span>

<span data-ttu-id="f0553-176">Spécifie le point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="f0553-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="f0553-177">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="f0553-177">The format of this string is:</span></span>

<span data-ttu-id="f0553-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="f0553-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="f0553-179">La chaîne suivante est une valeur au format correct pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="f0553-179">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="f0553-180">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="f0553-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="f0553-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="f0553-181">-Credential</span></span>

<span data-ttu-id="f0553-182">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="f0553-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="f0553-183">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="f0553-183">The default is the current user.</span></span>
<span data-ttu-id="f0553-184">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="f0553-184">Type a user name, such as "User01", "Domain01\User01", or User@Domain.com.</span></span>
<span data-ttu-id="f0553-185">Vous pouvez également entrer un objet PSCredential, tel que celui généré par l'applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="f0553-185">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="f0553-186">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f0553-186">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="f0553-187">-FilePath</span><span class="sxs-lookup"><span data-stu-id="f0553-187">-FilePath</span></span>

<span data-ttu-id="f0553-188">Spécifie le chemin d'accès d'un fichier qui est utilisé pour mettre à jour une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="f0553-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="f0553-189">Vous spécifiez la ressource de gestion à l'aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="f0553-189">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="f0553-190">Par exemple, la commande suivante utilise le paramètre de FilePath :</span><span class="sxs-lookup"><span data-stu-id="f0553-190">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="f0553-191">Cette commande appelle la méthode StopService sur le service Spouleur à l'aide des entrées fournies par un fichier.</span><span class="sxs-lookup"><span data-stu-id="f0553-191">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="f0553-192">Le contenu du fichier, Input.xml, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="f0553-192">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="f0553-193">-A</span><span class="sxs-lookup"><span data-stu-id="f0553-193">-OptionSet</span></span>

<span data-ttu-id="f0553-194">Passe un ensemble de commutateurs à un service pour modifier ou affiner la nature de la demande.</span><span class="sxs-lookup"><span data-stu-id="f0553-194">Passes a set of switches  to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="f0553-195">Ceux-ci sont similaires aux commutateurs utilisés dans des shells de ligne de commande, car spécifiques au service.</span><span class="sxs-lookup"><span data-stu-id="f0553-195">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="f0553-196">N’importe quel nombre d’options peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0553-196">Any number of options  can be specified.</span></span>

<span data-ttu-id="f0553-197">L'exemple suivant illustre la syntaxe qui passe les valeurs 1, 2 et 3 pour les paramètres a, b et c :</span><span class="sxs-lookup"><span data-stu-id="f0553-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="f0553-198">-Port</span><span class="sxs-lookup"><span data-stu-id="f0553-198">-Port</span></span>

<span data-ttu-id="f0553-199">Spécifie le port à utiliser lorsque le client se connecte au service WinRM.</span><span class="sxs-lookup"><span data-stu-id="f0553-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="f0553-200">Lorsque le transport est HTTP, le port par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="f0553-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="f0553-201">Lorsque le transport est HTTPS, le port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="f0553-201">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="f0553-202">Lorsque vous utilisez le protocole HTTPS, la valeur du paramètre ComputerName doit correspondre au nom commun du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="f0553-202">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="f0553-203">Toutefois, si le paramètre SkipCNCheck est spécifié dans le cadre du paramètre SessionOption, le nom commun du certificat du serveur n'a pas à correspondre au nom d'hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="f0553-203">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="f0553-204">Le paramètre SkipCNCheck doit être utilisé uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="f0553-204">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="f0553-205">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="f0553-205">-ResourceURI</span></span>

<span data-ttu-id="f0553-206">Contient l'URI de l'instance ou de la classe de ressource.</span><span class="sxs-lookup"><span data-stu-id="f0553-206">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="f0553-207">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f0553-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f0553-208">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="f0553-208">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="f0553-209">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f0553-209">For example:</span></span>

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

### <span data-ttu-id="f0553-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="f0553-210">-SelectorSet</span></span>

<span data-ttu-id="f0553-211">Spécifie un jeu de paires de valeur utilisées pour sélectionner des instances de ressources de gestion particulières.</span><span class="sxs-lookup"><span data-stu-id="f0553-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="f0553-212">*SelectorSet* est utilisé lorsque plusieurs instances de la ressource existent.</span><span class="sxs-lookup"><span data-stu-id="f0553-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="f0553-213">La valeur de *SelectorSet* doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="f0553-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="f0553-214">L'exemple suivant montre comment spécifier une valeur pour ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="f0553-214">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="f0553-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="f0553-215">-SessionOption</span></span>

<span data-ttu-id="f0553-216">Définit un ensemble d'options étendues pour la session WS-Management.</span><span class="sxs-lookup"><span data-stu-id="f0553-216">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="f0553-217">Entrez un objet SessionOption que vous créez à l'aide de l'applet de commande New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="f0553-217">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="f0553-218">Pour plus d'informations sur les options disponibles, consultez New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="f0553-218">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="f0553-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="f0553-219">-UseSSL</span></span>

<span data-ttu-id="f0553-220">Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f0553-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="f0553-221">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="f0553-221">By default, SSL is not used.</span></span>

<span data-ttu-id="f0553-222">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="f0553-222">WS-Management encrypts all the PowerShell content  that is transmitted over the network.</span></span>
<span data-ttu-id="f0553-223">Le paramètre UseSSL vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="f0553-223">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="f0553-224">Si SSL n'est pas disponible sur le port qui est utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="f0553-224">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="f0553-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="f0553-225">-ValueSet</span></span>

<span data-ttu-id="f0553-226">Spécifie une table de hachage qui permet de modifier une ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="f0553-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="f0553-227">Vous spécifiez la ressource de gestion à l’aide des paramètres ResourceURI et SelectorSet.</span><span class="sxs-lookup"><span data-stu-id="f0553-227">You specify the management resource using the ResourceURI and SelectorSet parameters.</span></span>
<span data-ttu-id="f0553-228">La valeur du paramètre ValueSet doit être une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="f0553-228">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="f0553-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0553-229">CommonParameters</span></span>

<span data-ttu-id="f0553-230">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0553-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0553-231">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0553-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0553-232">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f0553-232">INPUTS</span></span>

### <span data-ttu-id="f0553-233">Aucun</span><span class="sxs-lookup"><span data-stu-id="f0553-233">None</span></span>

<span data-ttu-id="f0553-234">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="f0553-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="f0553-235">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f0553-235">OUTPUTS</span></span>

### <span data-ttu-id="f0553-236">Aucun</span><span class="sxs-lookup"><span data-stu-id="f0553-236">None</span></span>

<span data-ttu-id="f0553-237">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="f0553-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f0553-238">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f0553-238">NOTES</span></span>

## <span data-ttu-id="f0553-239">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f0553-239">RELATED LINKS</span></span>

[<span data-ttu-id="f0553-240">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="f0553-240">Invoke-WmiMethod</span></span>](../Microsoft.PowerShell.Management/Invoke-WmiMethod.md)

[<span data-ttu-id="f0553-241">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f0553-241">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="f0553-242">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f0553-242">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="f0553-243">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f0553-243">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="f0553-244">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f0553-244">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="f0553-245">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f0553-245">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="f0553-246">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f0553-246">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="f0553-247">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f0553-247">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="f0553-248">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="f0553-248">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="f0553-249">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f0553-249">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="f0553-250">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f0553-250">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="f0553-251">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="f0553-251">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="f0553-252">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="f0553-252">Test-WSMan</span></span>](Test-WSMan.md)

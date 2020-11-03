---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/13/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: c89f7351e9c874cea2cc0cd5e0912e3ca0d8b0bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203209"
---
# <span data-ttu-id="6709d-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="6709d-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="6709d-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6709d-104">Synopsis</span></span>
<span data-ttu-id="6709d-105">Envoie une demande HTTP ou HTTPS à un service web RESTful.</span><span class="sxs-lookup"><span data-stu-id="6709d-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="6709d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6709d-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="6709d-107">Description</span><span class="sxs-lookup"><span data-stu-id="6709d-107">Description</span></span>

<span data-ttu-id="6709d-108">L' `Invoke-RestMethod` applet de commande envoie des requêtes http et HTTPS à des services Web REST qui retournent des données structurées.</span><span class="sxs-lookup"><span data-stu-id="6709d-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="6709d-109">Windows PowerShell met en forme la réponse en fonction du type de données.</span><span class="sxs-lookup"><span data-stu-id="6709d-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="6709d-110">Pour un flux RSS ou ATOM, Windows PowerShell retourne les nœuds XML Item ou Entry.</span><span class="sxs-lookup"><span data-stu-id="6709d-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="6709d-111">Pour JSON (JavaScript Objet Notation) ou XML, Windows PowerShell convertit (ou désérialise) le contenu en objets.</span><span class="sxs-lookup"><span data-stu-id="6709d-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="6709d-112">Cette applet de commande est introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6709d-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="6709d-113">Par défaut, le code de script de la page Web peut être exécuté lorsque la page est analysée pour remplir la `ParsedHtml` propriété.</span><span class="sxs-lookup"><span data-stu-id="6709d-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="6709d-114">Utilisez le commutateur **UseBasicParsing** pour supprimer ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6709d-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="6709d-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="6709d-115">Examples</span></span>

### <span data-ttu-id="6709d-116">Exemple 1 : récupérer le flux RSS PowerShell</span><span class="sxs-lookup"><span data-stu-id="6709d-116">Example 1: Get the PowerShell RSS feed</span></span>

```powershell
Invoke-RestMethod -Uri https://devblogs.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

<span data-ttu-id="6709d-117">Cette commande utilise la `Invoke-RestMethod` cmdlet pour récupérer des informations à partir du flux RSS du blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6709d-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="6709d-118">La commande utilise l' `Format-Table` applet de commande pour afficher les valeurs des propriétés **title** et **pubDate** de chaque blog dans une table.</span><span class="sxs-lookup"><span data-stu-id="6709d-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="6709d-119">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="6709d-119">Example 2</span></span>

<span data-ttu-id="6709d-120">Dans l’exemple suivant, un utilisateur exécute `Invoke-RestMethod` pour effectuer une demande de publication sur un site Web intranet dans l’organisation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6709d-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

```powershell
$Cred = Get-Credential

# Next, allow the use of self-signed SSL certificates.

[System.Net.ServicePointManager]::ServerCertificateValidationCallback = { $True }

# Create variables to store the values consumed by the Invoke-RestMethod command.
# The search variable contents are later embedded in the body variable.

$Server = 'server.contoso.com'
$Url = "https://${server}:8089/services/search/jobs/export"
$Search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"

# The cmdlet handles URL encoding. The body variable describes the search criteria, specifies CSV as
# the output mode, and specifies a time period for returned data that starts two days ago and ends
# one day ago. The body variable specifies values for parameters that apply to the particular REST
# API with which Invoke-RestMethod is communicating.

$Body = @{
    search = $Search
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}

# Now, run the Invoke-RestMethod command with all variables in place, specifying a path and file
# name for the resulting CSV output file.

Invoke-RestMethod -Method Post -Uri $url -Credential $Cred -Body $body -OutFile output.csv

{"preview":true,"offset":0,"result":{"sourcetype":"contoso1","count":"9624"}}

{"preview":true,"offset":1,"result":{"sourcetype":"contoso2","count":"152"}}

{"preview":true,"offset":2,"result":{"sourcetype":"contoso3","count":"88494"}}

{"preview":true,"offset":3,"result":{"sourcetype":"contoso4","count":"15277"}}
```

### <span data-ttu-id="6709d-121">Exemple 3 : passer plusieurs en-têtes</span><span class="sxs-lookup"><span data-stu-id="6709d-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="6709d-122">Cet exemple montre comment passer plusieurs en-têtes de à partir d’un `hash-table` à une API REST.</span><span class="sxs-lookup"><span data-stu-id="6709d-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="6709d-123">Les API requièrent souvent des en-têtes passés pour l’authentification, la validation, etc.</span><span class="sxs-lookup"><span data-stu-id="6709d-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="6709d-124">Exemple 3 : envoi de données de formulaire</span><span class="sxs-lookup"><span data-stu-id="6709d-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="6709d-125">Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un autre `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.</span><span class="sxs-lookup"><span data-stu-id="6709d-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="6709d-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6709d-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="6709d-127">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6709d-127">Parameters</span></span>

### <span data-ttu-id="6709d-128">-Corps</span><span class="sxs-lookup"><span data-stu-id="6709d-128">-Body</span></span>

<span data-ttu-id="6709d-129">Spécifie le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="6709d-129">Specifies the body of the request.</span></span> <span data-ttu-id="6709d-130">Le corps est le contenu de la demande qui suit les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="6709d-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="6709d-131">Vous pouvez également diriger une valeur de corps vers `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="6709d-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="6709d-132">Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="6709d-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="6709d-133">Quand l'entrée est une demande GET et que le corps est un IDictionary (en général, une table de hachage), le corps est ajouté à l'URI en tant que paramètres de requête.</span><span class="sxs-lookup"><span data-stu-id="6709d-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="6709d-134">Pour d'autres types de demandes (par exemple POST), le corps est défini comme valeur du corps de la demande au format nom standard=valeur.</span><span class="sxs-lookup"><span data-stu-id="6709d-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="6709d-135">La sortie détaillée d’un corps de publication se termine par `with -1-byte payload` , même si la taille du corps est à la fois connue et envoyée dans l' `Content-Length` en-tête http.</span><span class="sxs-lookup"><span data-stu-id="6709d-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-136">-Certificat</span><span class="sxs-lookup"><span data-stu-id="6709d-136">-Certificate</span></span>

<span data-ttu-id="6709d-137">Spécifie le certificat client utilisé pour une demande web sécurisée.</span><span class="sxs-lookup"><span data-stu-id="6709d-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="6709d-138">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="6709d-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="6709d-139">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="6709d-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="6709d-140">Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="6709d-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6709d-141">-CertificateThumbprint</span></span>

<span data-ttu-id="6709d-142">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="6709d-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="6709d-143">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="6709d-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6709d-144">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="6709d-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6709d-145">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="6709d-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="6709d-146">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur Windows PowerShell ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="6709d-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="6709d-147">-ContentType</span><span class="sxs-lookup"><span data-stu-id="6709d-147">-ContentType</span></span>

<span data-ttu-id="6709d-148">Spécifie le type de contenu de la demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="6709d-149">Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-RestMethod` définit le type de contenu sur « application/x-www-form-urlencoded ».</span><span class="sxs-lookup"><span data-stu-id="6709d-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="6709d-150">Sinon, le type de contenu n'est pas spécifié dans l'appel.</span><span class="sxs-lookup"><span data-stu-id="6709d-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="6709d-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="6709d-151">-Credential</span></span>

<span data-ttu-id="6709d-152">Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="6709d-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="6709d-153">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="6709d-153">The default is the current user.</span></span>

<span data-ttu-id="6709d-154">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6709d-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="6709d-155">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="6709d-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6709d-156">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="6709d-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="6709d-157">-DisableKeepAlive</span></span>

<span data-ttu-id="6709d-158">Affecte la valeur False à **KeepAlive** dans l'en-tête HTTP.</span><span class="sxs-lookup"><span data-stu-id="6709d-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="6709d-159">Par défaut, **KeepAlive** a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="6709d-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="6709d-160">**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="6709d-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: KeepAlive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-161">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="6709d-161">-Headers</span></span>

<span data-ttu-id="6709d-162">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="6709d-163">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="6709d-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="6709d-164">Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="6709d-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="6709d-165">Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes UserAgent ou de cookie.</span><span class="sxs-lookup"><span data-stu-id="6709d-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-166">-INFILE</span><span class="sxs-lookup"><span data-stu-id="6709d-166">-InFile</span></span>

<span data-ttu-id="6709d-167">Obtient le contenu de la demande web à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="6709d-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="6709d-168">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="6709d-168">Enter a path and file name.</span></span> <span data-ttu-id="6709d-169">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="6709d-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="6709d-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="6709d-170">-MaximumRedirection</span></span>

<span data-ttu-id="6709d-171">Détermine combien de fois Windows PowerShell redirige une connexion vers un autre URI (Uniform Resource Identifier) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="6709d-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="6709d-172">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="6709d-172">The default value is 5.</span></span> <span data-ttu-id="6709d-173">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="6709d-173">A value of 0 (zero) prevents all redirection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-174">-Méthode</span><span class="sxs-lookup"><span data-stu-id="6709d-174">-Method</span></span>

<span data-ttu-id="6709d-175">Spécifie la méthode utilisée pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="6709d-176">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="6709d-176">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6709d-177">Default</span><span class="sxs-lookup"><span data-stu-id="6709d-177">Default</span></span>
- <span data-ttu-id="6709d-178">DELETE</span><span class="sxs-lookup"><span data-stu-id="6709d-178">Delete</span></span>
- <span data-ttu-id="6709d-179">Obtenir</span><span class="sxs-lookup"><span data-stu-id="6709d-179">Get</span></span>
- <span data-ttu-id="6709d-180">Head</span><span class="sxs-lookup"><span data-stu-id="6709d-180">Head</span></span>
- <span data-ttu-id="6709d-181">Fusionner</span><span class="sxs-lookup"><span data-stu-id="6709d-181">Merge</span></span>
- <span data-ttu-id="6709d-182">Options</span><span class="sxs-lookup"><span data-stu-id="6709d-182">Options</span></span>
- <span data-ttu-id="6709d-183">Correctif</span><span class="sxs-lookup"><span data-stu-id="6709d-183">Patch</span></span>
- <span data-ttu-id="6709d-184">Publier</span><span class="sxs-lookup"><span data-stu-id="6709d-184">Post</span></span>
- <span data-ttu-id="6709d-185">Put</span><span class="sxs-lookup"><span data-stu-id="6709d-185">Put</span></span>
- <span data-ttu-id="6709d-186">Trace</span><span class="sxs-lookup"><span data-stu-id="6709d-186">Trace</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-187">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="6709d-187">-OutFile</span></span>

<span data-ttu-id="6709d-188">Enregistre le corps de la réponse dans le fichier de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="6709d-188">Saves the response body in the specified output file.</span></span> <span data-ttu-id="6709d-189">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="6709d-189">Enter a path and file name.</span></span> <span data-ttu-id="6709d-190">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="6709d-190">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="6709d-191">Par défaut, `Invoke-RestMethod` retourne les résultats au pipeline.</span><span class="sxs-lookup"><span data-stu-id="6709d-191">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="6709d-192">Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="6709d-192">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="6709d-193">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6709d-193">-PassThru</span></span>

<span data-ttu-id="6709d-194">Retourne les résultats, en plus de les écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="6709d-194">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="6709d-195">Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-195">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="6709d-196">-Proxy</span></span>

<span data-ttu-id="6709d-197">Utilise un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="6709d-197">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="6709d-198">Entrez l'URI d'un serveur proxy du réseau.</span><span class="sxs-lookup"><span data-stu-id="6709d-198">Enter the URI of a network proxy server.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-199">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6709d-199">-ProxyCredential</span></span>

<span data-ttu-id="6709d-200">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="6709d-200">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="6709d-201">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="6709d-201">The default is the current user.</span></span>

<span data-ttu-id="6709d-202">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="6709d-202">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="6709d-203">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-203">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="6709d-204">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-204">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-205">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="6709d-205">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="6709d-206">Utilise les informations d'identification de l'utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="6709d-206">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="6709d-207">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-207">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="6709d-208">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-208">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="6709d-209">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="6709d-209">-SessionVariable</span></span>

<span data-ttu-id="6709d-210">Crée une session de demande web et l'enregistre dans la valeur de la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6709d-210">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="6709d-211">Entrez un nom de variable sans le symbole dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="6709d-211">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="6709d-212">Lorsque vous spécifiez une variable de session, `Invoke-RestMethod` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6709d-212">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="6709d-213">Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="6709d-213">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="6709d-214">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="6709d-214">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="6709d-215">Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6709d-215">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="6709d-216">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="6709d-216">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="6709d-217">Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="6709d-217">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="6709d-218">Windows PowerShell utilise les données de l'objet de session de demande web au moment de l'établissement de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="6709d-218">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="6709d-219">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="6709d-219">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="6709d-220">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-220">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="6709d-221">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-221">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-222">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6709d-222">-TimeoutSec</span></span>

<span data-ttu-id="6709d-223">Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="6709d-223">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="6709d-224">La valeur par défaut, 0, spécifie un délai d'attente indéfini.</span><span class="sxs-lookup"><span data-stu-id="6709d-224">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="6709d-225">Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à TimeoutSec une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.</span><span class="sxs-lookup"><span data-stu-id="6709d-225">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-226">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="6709d-226">-TransferEncoding</span></span>

<span data-ttu-id="6709d-227">Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert.</span><span class="sxs-lookup"><span data-stu-id="6709d-227">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="6709d-228">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="6709d-228">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6709d-229">Mémorisé en bloc</span><span class="sxs-lookup"><span data-stu-id="6709d-229">Chunked</span></span>
- <span data-ttu-id="6709d-230">Compresser</span><span class="sxs-lookup"><span data-stu-id="6709d-230">Compress</span></span>
- <span data-ttu-id="6709d-231">Deflate</span><span class="sxs-lookup"><span data-stu-id="6709d-231">Deflate</span></span>
- <span data-ttu-id="6709d-232">GZip</span><span class="sxs-lookup"><span data-stu-id="6709d-232">GZip</span></span>
- <span data-ttu-id="6709d-233">Identité</span><span class="sxs-lookup"><span data-stu-id="6709d-233">Identity</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-234">-URI</span><span class="sxs-lookup"><span data-stu-id="6709d-234">-Uri</span></span>

<span data-ttu-id="6709d-235">Spécifie l'URI (Uniform Resource Identifier) de la ressource Internet à laquelle la demande web est envoyée.</span><span class="sxs-lookup"><span data-stu-id="6709d-235">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="6709d-236">Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.</span><span class="sxs-lookup"><span data-stu-id="6709d-236">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="6709d-237">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6709d-237">This parameter is required.</span></span> <span data-ttu-id="6709d-238">Le nom du paramètre ( **URI** ) est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6709d-238">The parameter name ( **Uri** ) is optional.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-239">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="6709d-239">-UseBasicParsing</span></span>

<span data-ttu-id="6709d-240">Indique que l’applet de commande utilise l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="6709d-240">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="6709d-241">L’applet de commande retourne le code HTML brut dans un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="6709d-241">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="6709d-242">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="6709d-242">-UseDefaultCredentials</span></span>

<span data-ttu-id="6709d-243">Utilise les informations d'identification de l'utilisateur actuel pour envoyer la demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-243">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="6709d-244">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="6709d-244">-UserAgent</span></span>

<span data-ttu-id="6709d-245">Spécifie une chaîne d'agent utilisateur pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-245">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="6709d-246">L'agent utilisateur par défaut est semblable à « Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0 » avec de légères variantes selon le système d'exploitation et la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6709d-246">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="6709d-247">Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands) , par exemple chrome, Firefox, Internet Explorer, Opera et Safari.</span><span class="sxs-lookup"><span data-stu-id="6709d-247">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="6709d-248">-Websession</span><span class="sxs-lookup"><span data-stu-id="6709d-248">-WebSession</span></span>

<span data-ttu-id="6709d-249">Spécifie une session de demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-249">Specifies a web request session.</span></span> <span data-ttu-id="6709d-250">Entrez le nom de la variable, y compris le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="6709d-250">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="6709d-251">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="6709d-251">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="6709d-252">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="6709d-252">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="6709d-253">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="6709d-253">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="6709d-254">Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6709d-254">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="6709d-255">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="6709d-255">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="6709d-256">Pour créer une session de demande Web, entrez un nom de variable (sans signe dollar) dans la valeur du paramètre **SessionVariable** d’une `Invoke-RestMethod` commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-256">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="6709d-257">`Invoke-RestMethod` crée la session et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="6709d-257">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="6709d-258">Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="6709d-258">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="6709d-259">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6709d-259">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6709d-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6709d-260">CommonParameters</span></span>

<span data-ttu-id="6709d-261">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6709d-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6709d-262">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6709d-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6709d-263">Entrées</span><span class="sxs-lookup"><span data-stu-id="6709d-263">Inputs</span></span>

### <span data-ttu-id="6709d-264">System.Object</span><span class="sxs-lookup"><span data-stu-id="6709d-264">System.Object</span></span>

<span data-ttu-id="6709d-265">Vous pouvez diriger le corps d’une requête Web vers `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="6709d-265">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="6709d-266">Sorties</span><span class="sxs-lookup"><span data-stu-id="6709d-266">Outputs</span></span>

### <span data-ttu-id="6709d-267">System.Xml.Xmldocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System. String</span><span class="sxs-lookup"><span data-stu-id="6709d-267">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="6709d-268">La sortie de l'applet de commande varie selon la mise en forme du contenu qui est récupéré.</span><span class="sxs-lookup"><span data-stu-id="6709d-268">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="6709d-269">PSObject</span><span class="sxs-lookup"><span data-stu-id="6709d-269">PSObject</span></span>

<span data-ttu-id="6709d-270">Si la demande retourne des chaînes JSON, `Invoke-RestMethod` retourne un PSObject qui représente les chaînes.</span><span class="sxs-lookup"><span data-stu-id="6709d-270">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="6709d-271">Notes</span><span class="sxs-lookup"><span data-stu-id="6709d-271">Notes</span></span>

## <span data-ttu-id="6709d-272">Liens associés</span><span class="sxs-lookup"><span data-stu-id="6709d-272">Related Links</span></span>

[<span data-ttu-id="6709d-273">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="6709d-273">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="6709d-274">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="6709d-274">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="6709d-275">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="6709d-275">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

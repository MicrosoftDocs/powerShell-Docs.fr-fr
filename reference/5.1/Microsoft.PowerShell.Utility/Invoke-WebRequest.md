---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 25da6262e93be3e3749aabaf4950e2fbcd91ff5c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205901"
---
# <span data-ttu-id="607ae-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="607ae-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="607ae-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="607ae-104">SYNOPSIS</span></span>
<span data-ttu-id="607ae-105">Obtient le contenu d'une page web sur Internet.</span><span class="sxs-lookup"><span data-stu-id="607ae-105">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="607ae-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="607ae-106">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="607ae-107">Description</span><span class="sxs-lookup"><span data-stu-id="607ae-107">DESCRIPTION</span></span>

<span data-ttu-id="607ae-108">L' `Invoke-WebRequest` applet de commande envoie des demandes http, HTTPS, FTP et file à une page Web ou à un service Web.</span><span class="sxs-lookup"><span data-stu-id="607ae-108">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="607ae-109">Elle analyse la réponse et retourne des collections de formulaires, des liens, des images et d'autres éléments HTML significatifs.</span><span class="sxs-lookup"><span data-stu-id="607ae-109">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="607ae-110">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="607ae-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="607ae-111">Par défaut, le code de script de la page Web peut être exécuté lorsque la page est analysée pour remplir la `ParsedHtml` propriété.</span><span class="sxs-lookup"><span data-stu-id="607ae-111">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="607ae-112">Utilisez le `-UseBasicParsing` commutateur pour supprimer ce.</span><span class="sxs-lookup"><span data-stu-id="607ae-112">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="607ae-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="607ae-113">EXAMPLES</span></span>

### <span data-ttu-id="607ae-114">Exemple 1 : envoyer une requête Web</span><span class="sxs-lookup"><span data-stu-id="607ae-114">Example 1: Send a web request</span></span>

<span data-ttu-id="607ae-115">Cette commande utilise la `Invoke-WebRequest` cmdlet pour envoyer une requête Web au site Bing.com.</span><span class="sxs-lookup"><span data-stu-id="607ae-115">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

<span data-ttu-id="607ae-116">La première commande émet la demande et enregistre la réponse dans la `$R` variable.</span><span class="sxs-lookup"><span data-stu-id="607ae-116">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="607ae-117">La deuxième commande filtre les objets dans la propriété des **allèles** où la propriété **Name** est semblable à « \* value » et le **tagname** à « Input ».</span><span class="sxs-lookup"><span data-stu-id="607ae-117">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="607ae-118">Les résultats filtrés sont dirigés vers `Select-Object` pour sélectionner les propriétés **Name** et **value** .</span><span class="sxs-lookup"><span data-stu-id="607ae-118">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="607ae-119">Exemple 2 : utiliser un service Web avec état</span><span class="sxs-lookup"><span data-stu-id="607ae-119">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="607ae-120">Cet exemple montre comment utiliser l' `Invoke-WebRequest` applet de commande avec un service Web avec état, tel que Facebook.</span><span class="sxs-lookup"><span data-stu-id="607ae-120">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

<span data-ttu-id="607ae-121">La première commande utilise l' `Invoke-WebRequest` applet de commande pour envoyer une demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="607ae-121">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="607ae-122">La commande spécifie la valeur « FB » pour la valeur du paramètre **SessionVariable** et enregistre le résultat dans la `$R` variable.</span><span class="sxs-lookup"><span data-stu-id="607ae-122">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="607ae-123">Une fois la commande terminée, la `$R` variable contient un **HtmlWebResponseObject** et la `$FB` variable contient un objet **WebRequestSession** .</span><span class="sxs-lookup"><span data-stu-id="607ae-123">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="607ae-124">Une fois que l’applet de commande `Invoke-WebRequest` se connecte à Facebook, la propriété **StatusDescription** de l’objet de réponse Web dans la `$R` variable indique que l’utilisateur s’est connecté avec succès.</span><span class="sxs-lookup"><span data-stu-id="607ae-124">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="607ae-125">Exemple 3 : obtenir des liens à partir d’une page Web</span><span class="sxs-lookup"><span data-stu-id="607ae-125">Example 3: Get links from a web page</span></span>

<span data-ttu-id="607ae-126">Cette commande obtient les liens dans une page web.</span><span class="sxs-lookup"><span data-stu-id="607ae-126">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="607ae-127">L' `Invoke-WebRequest` applet de commande obtient le contenu de la page Web.</span><span class="sxs-lookup"><span data-stu-id="607ae-127">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="607ae-128">La propriété **Links** du **HtmlWebResponseObject** retourné est ensuite utilisée pour afficher la propriété **href** de chaque lien.</span><span class="sxs-lookup"><span data-stu-id="607ae-128">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="607ae-129">Exemple 4 : intercepter les messages non réussis de Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="607ae-129">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="607ae-130">Lorsque `Invoke-WebRequest` rencontre un message http sans succès (404, 500, etc.), il ne retourne aucune sortie et lève une erreur de fin d’opération.</span><span class="sxs-lookup"><span data-stu-id="607ae-130">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="607ae-131">Pour intercepter l’erreur et afficher le **statusCode** , vous pouvez l’encadrer dans un `try/catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="607ae-131">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="607ae-132">L’exemple suivant montre comment effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="607ae-132">The following example shows how to accomplish this.</span></span>

```powershell
try
{
    $response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

<span data-ttu-id="607ae-133">La première commande appelle `Invoke-WebRequest` avec un **ErrorAction** **Stop** , qui force `Invoke-WebRequest` à lever une erreur d’arrêt sur les demandes ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="607ae-133">The first command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="607ae-134">L’erreur de fin est interceptée par le `catch` bloc qui récupère le **statusCode** de l’objet **exception** .</span><span class="sxs-lookup"><span data-stu-id="607ae-134">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="607ae-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="607ae-135">PARAMETERS</span></span>

### <span data-ttu-id="607ae-136">-Corps</span><span class="sxs-lookup"><span data-stu-id="607ae-136">-Body</span></span>

<span data-ttu-id="607ae-137">Spécifie le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="607ae-137">Specifies the body of the request.</span></span>
<span data-ttu-id="607ae-138">Le corps est le contenu de la demande qui suit les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="607ae-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="607ae-139">Vous pouvez également diriger une valeur de corps vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="607ae-139">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="607ae-140">Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="607ae-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="607ae-141">Lorsque l’entrée est une requête d’extraction et que le corps est un **IDictionary** (en général, une table de hachage), le corps est ajouté à l’URI en tant que paramètres de requête.</span><span class="sxs-lookup"><span data-stu-id="607ae-141">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="607ae-142">Pour les autres requêtes d’extraction, le corps est défini comme valeur du corps de la requête au `name=value` format standard.</span><span class="sxs-lookup"><span data-stu-id="607ae-142">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="607ae-143">Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.</span><span class="sxs-lookup"><span data-stu-id="607ae-143">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="607ae-144">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="607ae-144">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="607ae-145">ou -</span><span class="sxs-lookup"><span data-stu-id="607ae-145">or -</span></span>

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

### <span data-ttu-id="607ae-146">-Certificat</span><span class="sxs-lookup"><span data-stu-id="607ae-146">-Certificate</span></span>

<span data-ttu-id="607ae-147">Spécifie le certificat client utilisé pour une demande web sécurisée.</span><span class="sxs-lookup"><span data-stu-id="607ae-147">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="607ae-148">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="607ae-148">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="607ae-149">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de **certificat** ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="607ae-149">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="607ae-150">Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="607ae-150">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="607ae-151">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="607ae-151">-CertificateThumbprint</span></span>

<span data-ttu-id="607ae-152">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="607ae-152">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="607ae-153">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="607ae-153">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="607ae-154">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="607ae-154">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="607ae-155">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="607ae-155">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="607ae-156">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="607ae-156">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="607ae-157">-ContentType</span><span class="sxs-lookup"><span data-stu-id="607ae-157">-ContentType</span></span>

<span data-ttu-id="607ae-158">Spécifie le type de contenu de la demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-158">Specifies the content type of the web request.</span></span>

<span data-ttu-id="607ae-159">Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-WebRequest` définit le type de contenu sur application/x-www-form-urlencoded.</span><span class="sxs-lookup"><span data-stu-id="607ae-159">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="607ae-160">Sinon, le type de contenu n'est pas spécifié dans l'appel.</span><span class="sxs-lookup"><span data-stu-id="607ae-160">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="607ae-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="607ae-161">-Credential</span></span>

<span data-ttu-id="607ae-162">Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="607ae-162">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="607ae-163">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="607ae-163">The default is the current user.</span></span>

<span data-ttu-id="607ae-164">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="607ae-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="607ae-165">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="607ae-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="607ae-166">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="607ae-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="607ae-167">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="607ae-167">-DisableKeepAlive</span></span>

<span data-ttu-id="607ae-168">Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur **false** .</span><span class="sxs-lookup"><span data-stu-id="607ae-168">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="607ae-169">Par défaut, **KeepAlive** a la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="607ae-169">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="607ae-170">**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="607ae-170">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="607ae-171">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="607ae-171">-Headers</span></span>

<span data-ttu-id="607ae-172">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-172">Specifies the headers of the web request.</span></span> <span data-ttu-id="607ae-173">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="607ae-173">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="607ae-174">Pour définir des en-têtes **UserAgent** , utilisez le paramètre **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="607ae-174">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="607ae-175">Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes **UserAgent** ou de cookie.</span><span class="sxs-lookup"><span data-stu-id="607ae-175">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="607ae-176">-INFILE</span><span class="sxs-lookup"><span data-stu-id="607ae-176">-InFile</span></span>

<span data-ttu-id="607ae-177">Obtient le contenu de la demande web à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="607ae-177">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="607ae-178">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="607ae-178">Enter a path and file name.</span></span> <span data-ttu-id="607ae-179">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="607ae-179">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="607ae-180">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="607ae-180">-MaximumRedirection</span></span>

<span data-ttu-id="607ae-181">Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="607ae-181">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="607ae-182">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="607ae-182">The default value is 5.</span></span> <span data-ttu-id="607ae-183">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="607ae-183">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="607ae-184">-Méthode</span><span class="sxs-lookup"><span data-stu-id="607ae-184">-Method</span></span>

<span data-ttu-id="607ae-185">Spécifie la méthode utilisée pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-185">Specifies the method used for the web request.</span></span> <span data-ttu-id="607ae-186">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="607ae-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="607ae-187">Default</span><span class="sxs-lookup"><span data-stu-id="607ae-187">Default</span></span>
- <span data-ttu-id="607ae-188">DELETE</span><span class="sxs-lookup"><span data-stu-id="607ae-188">Delete</span></span>
- <span data-ttu-id="607ae-189">Obtenir</span><span class="sxs-lookup"><span data-stu-id="607ae-189">Get</span></span>
- <span data-ttu-id="607ae-190">Head</span><span class="sxs-lookup"><span data-stu-id="607ae-190">Head</span></span>
- <span data-ttu-id="607ae-191">Fusionner</span><span class="sxs-lookup"><span data-stu-id="607ae-191">Merge</span></span>
- <span data-ttu-id="607ae-192">Options</span><span class="sxs-lookup"><span data-stu-id="607ae-192">Options</span></span>
- <span data-ttu-id="607ae-193">Correctif</span><span class="sxs-lookup"><span data-stu-id="607ae-193">Patch</span></span>
- <span data-ttu-id="607ae-194">Publier</span><span class="sxs-lookup"><span data-stu-id="607ae-194">Post</span></span>
- <span data-ttu-id="607ae-195">Put</span><span class="sxs-lookup"><span data-stu-id="607ae-195">Put</span></span>
- <span data-ttu-id="607ae-196">Trace</span><span class="sxs-lookup"><span data-stu-id="607ae-196">Trace</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="607ae-197">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="607ae-197">-OutFile</span></span>

<span data-ttu-id="607ae-198">Spécifie le fichier de sortie pour lequel cette applet de commande enregistre le corps de la réponse.</span><span class="sxs-lookup"><span data-stu-id="607ae-198">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="607ae-199">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="607ae-199">Enter a path and file name.</span></span>
<span data-ttu-id="607ae-200">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="607ae-200">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="607ae-201">Par défaut, `Invoke-WebRequest` retourne les résultats au pipeline.</span><span class="sxs-lookup"><span data-stu-id="607ae-201">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="607ae-202">Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="607ae-202">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="607ae-203">-PassThru</span><span class="sxs-lookup"><span data-stu-id="607ae-203">-PassThru</span></span>

<span data-ttu-id="607ae-204">Indique que l’applet de commande retourne les résultats, en plus de les écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="607ae-204">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="607ae-205">Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-205">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="607ae-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="607ae-206">-Proxy</span></span>

<span data-ttu-id="607ae-207">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="607ae-207">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="607ae-208">Entrez l'URI d'un serveur proxy du réseau.</span><span class="sxs-lookup"><span data-stu-id="607ae-208">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="607ae-209">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="607ae-209">-ProxyCredential</span></span>

<span data-ttu-id="607ae-210">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="607ae-210">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="607ae-211">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="607ae-211">The default is the current user.</span></span>

<span data-ttu-id="607ae-212">Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="607ae-212">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="607ae-213">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-213">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="607ae-214">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-214">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="607ae-215">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="607ae-215">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="607ae-216">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="607ae-216">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="607ae-217">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-217">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="607ae-218">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-218">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="607ae-219">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="607ae-219">-SessionVariable</span></span>

<span data-ttu-id="607ae-220">Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="607ae-220">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="607ae-221">Entrez un nom de variable sans le symbole dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="607ae-221">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="607ae-222">Lorsque vous spécifiez une variable de session, `Invoke-WebRequest` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="607ae-222">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="607ae-223">Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="607ae-223">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="607ae-224">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="607ae-224">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="607ae-225">Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="607ae-225">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="607ae-226">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="607ae-226">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="607ae-227">Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="607ae-227">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="607ae-228">PowerShell utilise les données de l’objet session de demande Web lors de l’établissement de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="607ae-228">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="607ae-229">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="607ae-229">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="607ae-230">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-230">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="607ae-231">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-231">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="607ae-232">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="607ae-232">-TimeoutSec</span></span>

<span data-ttu-id="607ae-233">Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="607ae-233">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="607ae-234">La valeur par défaut, 0, spécifie un délai d'attente indéfini.</span><span class="sxs-lookup"><span data-stu-id="607ae-234">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="607ae-235">Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une **WebException** soit levée, et votre demande expire.</span><span class="sxs-lookup"><span data-stu-id="607ae-235">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="607ae-236">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="607ae-236">-TransferEncoding</span></span>

<span data-ttu-id="607ae-237">Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert.</span><span class="sxs-lookup"><span data-stu-id="607ae-237">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="607ae-238">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="607ae-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="607ae-239">Mémorisé en bloc</span><span class="sxs-lookup"><span data-stu-id="607ae-239">Chunked</span></span>
- <span data-ttu-id="607ae-240">Compresser</span><span class="sxs-lookup"><span data-stu-id="607ae-240">Compress</span></span>
- <span data-ttu-id="607ae-241">Deflate</span><span class="sxs-lookup"><span data-stu-id="607ae-241">Deflate</span></span>
- <span data-ttu-id="607ae-242">GZip</span><span class="sxs-lookup"><span data-stu-id="607ae-242">GZip</span></span>
- <span data-ttu-id="607ae-243">Identité</span><span class="sxs-lookup"><span data-stu-id="607ae-243">Identity</span></span>

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

### <span data-ttu-id="607ae-244">-URI</span><span class="sxs-lookup"><span data-stu-id="607ae-244">-Uri</span></span>

<span data-ttu-id="607ae-245">Spécifie l'URI (Uniform Resource Identifier) de la ressource Internet à laquelle la demande web est envoyée.</span><span class="sxs-lookup"><span data-stu-id="607ae-245">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="607ae-246">Entrez un URI.</span><span class="sxs-lookup"><span data-stu-id="607ae-246">Enter a URI.</span></span> <span data-ttu-id="607ae-247">Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.</span><span class="sxs-lookup"><span data-stu-id="607ae-247">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="607ae-248">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="607ae-248">This parameter is required.</span></span>

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

### <span data-ttu-id="607ae-249">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="607ae-249">-UseBasicParsing</span></span>

<span data-ttu-id="607ae-250">Indique que l’applet de commande utilise l’objet de réponse pour le contenu HTML sans analyse du modèle DOM (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="607ae-250">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="607ae-251">Ce paramètre est obligatoire quand Internet Explorer n'est pas installé sur les ordinateurs, comme sur une installation minimale du serveur d'un système d'exploitation Windows Server.</span><span class="sxs-lookup"><span data-stu-id="607ae-251">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="607ae-252">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="607ae-252">-UseDefaultCredentials</span></span>

<span data-ttu-id="607ae-253">Indique que le cmdet utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web.</span><span class="sxs-lookup"><span data-stu-id="607ae-253">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="607ae-254">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="607ae-254">-UserAgent</span></span>

<span data-ttu-id="607ae-255">Spécifie une chaîne d'agent utilisateur pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-255">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="607ae-256">L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` avec de légères variations pour chaque système d’exploitation et plateforme.</span><span class="sxs-lookup"><span data-stu-id="607ae-256">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="607ae-257">Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari.</span><span class="sxs-lookup"><span data-stu-id="607ae-257">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="607ae-258">Par exemple, la commande suivante utilise la chaîne de l’agent utilisateur pour Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="607ae-258">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="607ae-259">-Websession</span><span class="sxs-lookup"><span data-stu-id="607ae-259">-WebSession</span></span>

<span data-ttu-id="607ae-260">Spécifie une session de demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-260">Specifies a web request session.</span></span> <span data-ttu-id="607ae-261">Entrez le nom de la variable, y compris le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="607ae-261">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="607ae-262">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="607ae-262">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="607ae-263">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="607ae-263">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="607ae-264">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="607ae-264">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="607ae-265">Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="607ae-265">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="607ae-266">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="607ae-266">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="607ae-267">Pour créer une session de demande Web, entrez un nom de variable (sans signe dollar) dans la valeur du paramètre **SessionVariable** d’une `Invoke-WebRequest` commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-267">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="607ae-268">`Invoke-WebRequest` crée la session et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="607ae-268">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="607ae-269">Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="607ae-269">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="607ae-270">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="607ae-270">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="607ae-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="607ae-271">CommonParameters</span></span>

<span data-ttu-id="607ae-272">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="607ae-272">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="607ae-273">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="607ae-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="607ae-274">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="607ae-274">INPUTS</span></span>

### <span data-ttu-id="607ae-275">System.Object</span><span class="sxs-lookup"><span data-stu-id="607ae-275">System.Object</span></span>

<span data-ttu-id="607ae-276">Vous pouvez diriger le corps d’une requête Web vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="607ae-276">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="607ae-277">SORTIES</span><span class="sxs-lookup"><span data-stu-id="607ae-277">OUTPUTS</span></span>

### <span data-ttu-id="607ae-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="607ae-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="607ae-279">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="607ae-279">NOTES</span></span>

## <span data-ttu-id="607ae-280">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="607ae-280">RELATED LINKS</span></span>

[<span data-ttu-id="607ae-281">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="607ae-281">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="607ae-282">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="607ae-282">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="607ae-283">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="607ae-283">ConvertTo-Json</span></span>](ConvertTo-Json.md)

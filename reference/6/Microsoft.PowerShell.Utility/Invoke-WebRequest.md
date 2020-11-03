---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 09270fd74fd256858faacaae399e05b40985ddb5
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206002"
---
# <span data-ttu-id="adaa8-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="adaa8-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="adaa8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="adaa8-104">SYNOPSIS</span></span>
<span data-ttu-id="adaa8-105">Obtient le contenu d’une page Web sur Internet.</span><span class="sxs-lookup"><span data-stu-id="adaa8-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="adaa8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="adaa8-106">SYNTAX</span></span>

### <span data-ttu-id="adaa8-107">StandardMethod (par défaut)</span><span class="sxs-lookup"><span data-stu-id="adaa8-107">StandardMethod (Default)</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="adaa8-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="adaa8-108">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="adaa8-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="adaa8-109">CustomMethod</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="adaa8-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="adaa8-110">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="adaa8-111">Description</span><span class="sxs-lookup"><span data-stu-id="adaa8-111">DESCRIPTION</span></span>

<span data-ttu-id="adaa8-112">L' `Invoke-WebRequest` applet de commande envoie des requêtes http et HTTPS à une page Web ou à un service Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="adaa8-113">Elle analyse la réponse et retourne des collections de liens, d’images et d’autres éléments HTML significatifs.</span><span class="sxs-lookup"><span data-stu-id="adaa8-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="adaa8-114">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="adaa8-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="adaa8-115">EXAMPLES</span></span>

### <span data-ttu-id="adaa8-116">Exemple 1 : envoyer une requête Web</span><span class="sxs-lookup"><span data-stu-id="adaa8-116">Example 1: Send a web request</span></span>

<span data-ttu-id="adaa8-117">Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour envoyer une requête Web au site Bing.com.</span><span class="sxs-lookup"><span data-stu-id="adaa8-117">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

<span data-ttu-id="adaa8-118">La première commande émet la demande et enregistre la réponse dans la `$Response` variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-118">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="adaa8-119">La deuxième commande obtient tout **InputField** où la propriété **Name** est similaire `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-119">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="adaa8-120">Les résultats filtrés sont dirigés vers `Select-Object` pour sélectionner les propriétés **Name** et **value** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-120">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="adaa8-121">Exemple 2 : utiliser un service Web avec état</span><span class="sxs-lookup"><span data-stu-id="adaa8-121">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="adaa8-122">Cet exemple montre comment utiliser l' `Invoke-WebRequest` applet de commande avec un service Web avec état.</span><span class="sxs-lookup"><span data-stu-id="adaa8-122">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

<span data-ttu-id="adaa8-123">Le premier appel à `Invoke-WebRequest` envoie une demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="adaa8-123">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="adaa8-124">La commande spécifie la valeur « session » pour la valeur du paramètre **-SessionVariable** et enregistre le résultat dans la `$LoginResponse` variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-124">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="adaa8-125">Une fois la commande terminée, la `$LoginResponse` variable contient un `BasicHtmlWebResponseObject` et la `$Session` variable contient un `WebRequestSession` objet.</span><span class="sxs-lookup"><span data-stu-id="adaa8-125">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="adaa8-126">L’utilisateur est alors connecté au site.</span><span class="sxs-lookup"><span data-stu-id="adaa8-126">This logs the user into the site.</span></span>

<span data-ttu-id="adaa8-127">L’appel à `$Session` par lui-même affiche l' `WebRequestSession` objet dans la variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-127">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="adaa8-128">Le deuxième appel à `Invoke-WebRequest` récupère le profil de l’utilisateur, ce qui nécessite que l’utilisateur soit connecté au site.</span><span class="sxs-lookup"><span data-stu-id="adaa8-128">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="adaa8-129">Les données de session stockées dans la `$Session` variable sont utilisées pour fournir des cookies de session au site créé pendant la connexion.</span><span class="sxs-lookup"><span data-stu-id="adaa8-129">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="adaa8-130">Le résultat est enregistré dans la `$ProfileResponse` variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-130">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="adaa8-131">L’appel à `$ProfileResponse` par lui-même affiche le `BasicHtmlWebResponseObject` dans la variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-131">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="adaa8-132">Exemple 3 : obtenir des liens à partir d’une page Web</span><span class="sxs-lookup"><span data-stu-id="adaa8-132">Example 3: Get links from a web page</span></span>

<span data-ttu-id="adaa8-133">Cet exemple obtient les liens dans une page Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-133">This example gets the links in a web page.</span></span> <span data-ttu-id="adaa8-134">Elle utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-134">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="adaa8-135">Elle utilise ensuite la propriété **Links** du `BasicHtmlWebResponseObject` qui `Invoke-WebRequest` retourne et la propriété **href** de chaque lien.</span><span class="sxs-lookup"><span data-stu-id="adaa8-135">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="adaa8-136">Exemple 4 : écrit le contenu de la réponse dans un fichier à l’aide de l’encodage défini dans la page demandée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-136">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="adaa8-137">Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web d’une page de documentation PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa8-137">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

<span data-ttu-id="adaa8-138">La première commande récupère la page et enregistre l’objet de réponse dans la `$Response` variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-138">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="adaa8-139">La deuxième commande crée un `StreamWriter` à utiliser pour écrire le contenu de la réponse dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-139">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="adaa8-140">La propriété **Encoding** de l’objet Response est utilisée pour définir l’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-140">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="adaa8-141">Les dernières commandes écrivent la propriété de **contenu** dans le fichier, puis suppriment le `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-141">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="adaa8-142">Notez que la propriété **Encoding** a la valeur null si la demande Web ne retourne pas de contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="adaa8-142">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="adaa8-143">Exemple 5 : envoyer un fichier multipart/form-data</span><span class="sxs-lookup"><span data-stu-id="adaa8-143">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="adaa8-144">Cet exemple utilise l' `Invoke-WebRequest` applet de commande upload a file as a `multipart/form-data` submission.</span><span class="sxs-lookup"><span data-stu-id="adaa8-144">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="adaa8-145">Le fichier `c:\document.txt` est soumis en tant que champ `document` de formulaire avec le `Content-Type` de `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-145">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### <span data-ttu-id="adaa8-146">Exemple 6 : envoi de données multipart/formulaire simplifié</span><span class="sxs-lookup"><span data-stu-id="adaa8-146">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="adaa8-147">Certaines API requièrent des `multipart/form-data` envois pour télécharger des fichiers et du contenu mixte.</span><span class="sxs-lookup"><span data-stu-id="adaa8-147">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="adaa8-148">Cet exemple illustre la mise à jour d’un profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-148">This example demonstrates updating a user profile.</span></span>

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="adaa8-149">Le formulaire de profil requiert les champs suivants : `firstName` ,,,, `lastName` `email` `avatar` `birthday` et `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-149">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="adaa8-150">L’API attend une image pour le profil utilisateur pic à fournir dans le `avatar` champ.</span><span class="sxs-lookup"><span data-stu-id="adaa8-150">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="adaa8-151">L’API accepte également l' `hobbies` envoi de plusieurs entrées sous la même forme.</span><span class="sxs-lookup"><span data-stu-id="adaa8-151">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="adaa8-152">Lors de la création de la `$Form` Hashtable, les noms de clé sont utilisés comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="adaa8-152">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="adaa8-153">Par défaut, les valeurs de la HashTable sont converties en chaînes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-153">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="adaa8-154">Si une valeur **System. IO. FileInfo** est présente, le contenu du fichier est envoyé.</span><span class="sxs-lookup"><span data-stu-id="adaa8-154">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="adaa8-155">Si une collection telle que des tableaux ou des listes est présente, le champ de formulaire est envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="adaa8-155">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="adaa8-156">En utilisant `Get-Item` sur la `avatar` clé, l' `FileInfo` objet est défini comme valeur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-156">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="adaa8-157">Le résultat est que les données d’image de `jdoe.png` sont envoyées.</span><span class="sxs-lookup"><span data-stu-id="adaa8-157">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="adaa8-158">En fournissant une liste à la `hobbies` clé, le `hobbies` champ est présent dans les envois une fois pour chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="adaa8-158">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="adaa8-159">Exemple 7 : intercepter les messages non réussis de Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="adaa8-159">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="adaa8-160">Lorsque `Invoke-WebRequest` rencontre un message http sans succès (404, 500, etc.), il ne retourne aucune sortie et lève une erreur de fin d’opération.</span><span class="sxs-lookup"><span data-stu-id="adaa8-160">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="adaa8-161">Pour intercepter l’erreur et afficher le **statusCode** , vous pouvez l’encadrer dans un `try/catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="adaa8-161">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

<span data-ttu-id="adaa8-162">La commande appelle `Invoke-WebRequest` avec un **ErrorAction** **Stop** , qui force `Invoke-WebRequest` à lever une erreur d’arrêt sur les demandes ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="adaa8-162">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="adaa8-163">L’erreur de fin est interceptée par le `catch` bloc qui récupère le **statusCode** de l’objet **exception** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-163">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="adaa8-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="adaa8-164">PARAMETERS</span></span>

### <span data-ttu-id="adaa8-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="adaa8-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="adaa8-166">Autorise l’envoi d’informations d’identification et de secrets sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="adaa8-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="adaa8-167">Par défaut, le fait de fournir des **informations d’identification** ou toute option **d’authentification** avec un **URI** qui ne commence pas par `https://` génère une erreur et la demande est abandonnée pour empêcher la communication accidentelle de secrets en texte brut sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="adaa8-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="adaa8-168">Pour remplacer ce comportement à vos propres risques, fournissez le paramètre **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="adaa8-169">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="adaa8-170">Elle est fournie uniquement pour la compatibilité avec les systèmes hérités qui ne peuvent pas fournir de connexions chiffrées.</span><span class="sxs-lookup"><span data-stu-id="adaa8-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="adaa8-171">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="adaa8-171">Use at your own risk.</span></span>

<span data-ttu-id="adaa8-172">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="adaa8-173">-Authentification</span><span class="sxs-lookup"><span data-stu-id="adaa8-173">-Authentication</span></span>

<span data-ttu-id="adaa8-174">Spécifie le type d’authentification explicite à utiliser pour la requête.</span><span class="sxs-lookup"><span data-stu-id="adaa8-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="adaa8-175">La valeur par défaut est **None** (Aucun).</span><span class="sxs-lookup"><span data-stu-id="adaa8-175">The default is **None** .</span></span>
<span data-ttu-id="adaa8-176">**L’authentification** ne peut pas être utilisée avec **UseDefaultCredentials** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-176">**Authentication** cannot be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="adaa8-177">Options d’authentification disponibles :</span><span class="sxs-lookup"><span data-stu-id="adaa8-177">Available Authentication Options:</span></span>

- <span data-ttu-id="adaa8-178">**None** : il s’agit de l’option par défaut lorsque **l’authentification** n’est pas fournie ; aucune authentification explicite n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-178">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="adaa8-179">De **base** : requiert des **informations d’identification** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-179">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="adaa8-180">Les informations d’identification sont envoyées dans un en-tête d’authentification de base RFC 7617 au format `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="adaa8-181">**Bearer** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-181">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="adaa8-182">Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="adaa8-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="adaa8-183">Il s’agit d’un alias pour **OAuth**</span><span class="sxs-lookup"><span data-stu-id="adaa8-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="adaa8-184">**OAuth** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-184">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="adaa8-185">Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="adaa8-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="adaa8-186">Il s’agit d’un alias pour le **porteur**</span><span class="sxs-lookup"><span data-stu-id="adaa8-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="adaa8-187">La spécification de **l’authentification** remplace tous les `Authorization` en-têtes fournis aux **en-têtes** ou inclus dans **websession** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="adaa8-188">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-188">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-189">-Corps</span><span class="sxs-lookup"><span data-stu-id="adaa8-189">-Body</span></span>

<span data-ttu-id="adaa8-190">Spécifie le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-190">Specifies the body of the request.</span></span> <span data-ttu-id="adaa8-191">Le corps est le contenu de la demande qui suit les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="adaa8-192">Vous pouvez également diriger une valeur de corps vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="adaa8-193">Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="adaa8-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="adaa8-194">Lorsque l’entrée est une requête d’extraction et que le corps est un `IDictionary` (en général, une table de hachage), le corps est ajouté à l’URI en tant que paramètres de requête.</span><span class="sxs-lookup"><span data-stu-id="adaa8-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="adaa8-195">Pour les autres types de demande (par exemple, la publication), le corps est défini comme valeur du corps de la requête au `name=value` format standard.</span><span class="sxs-lookup"><span data-stu-id="adaa8-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="adaa8-196">Le paramètre **Body** peut également accepter un `System.Net.Http.MultipartFormDataContent` objet.</span><span class="sxs-lookup"><span data-stu-id="adaa8-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="adaa8-197">Cela facilite les `multipart/form-data` demandes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="adaa8-198">Lorsqu’un objet **MultipartFormDataContent** est fourni pour **le corps** , tous les en-têtes associés au contenu fournis aux paramètres **ContentType** , **headers** ou **websession** sont remplacés par les en-têtes de contenu de l’objet **MultipartFormDataContent** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-198">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="adaa8-199">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-199">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="adaa8-200">-Certificat</span><span class="sxs-lookup"><span data-stu-id="adaa8-200">-Certificate</span></span>

<span data-ttu-id="adaa8-201">Spécifie le certificat client utilisé pour une demande Web sécurisée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="adaa8-202">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="adaa8-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="adaa8-203">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="adaa8-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="adaa8-204">Si le certificat n’est pas valide ou ne dispose pas des autorisations suffisantes, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="adaa8-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="adaa8-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="adaa8-205">-CertificateThumbprint</span></span>

<span data-ttu-id="adaa8-206">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="adaa8-207">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="adaa8-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="adaa8-208">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="adaa8-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="adaa8-209">Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="adaa8-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="adaa8-210">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa8-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="adaa8-211">Cette fonctionnalité n’est actuellement prise en charge que sur les plateformes de système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="adaa8-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="adaa8-212">-ContentType</span><span class="sxs-lookup"><span data-stu-id="adaa8-212">-ContentType</span></span>

<span data-ttu-id="adaa8-213">Spécifie le type de contenu de la demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="adaa8-214">Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-WebRequest` définit le type de contenu sur `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="adaa8-215">Dans le cas contraire, le type de contenu n’est pas spécifié dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="adaa8-216">**ContentType** est substitué lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="adaa8-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="adaa8-217">-Credential</span></span>

<span data-ttu-id="adaa8-218">Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="adaa8-219">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-219">The default is the current user.</span></span>

<span data-ttu-id="adaa8-220">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="adaa8-221">Les **informations d’identification** peuvent être utilisées seules ou conjointement avec certaines options de paramètres **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="adaa8-222">Lorsqu’il est utilisé seul, il fournit uniquement des informations d’identification au serveur distant si le serveur distant envoie une demande de stimulation d’authentification.</span><span class="sxs-lookup"><span data-stu-id="adaa8-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="adaa8-223">Lorsqu’elles sont utilisées avec les options **d’authentification** , les informations d’identification sont envoyées explicitement.</span><span class="sxs-lookup"><span data-stu-id="adaa8-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="adaa8-224">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="adaa8-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="adaa8-225">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="adaa8-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="adaa8-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="adaa8-226">-CustomMethod</span></span>

<span data-ttu-id="adaa8-227">Spécifie une méthode personnalisée utilisée pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="adaa8-228">Cela peut être utilisé si la méthode de demande requise par le point de terminaison n’est pas une option disponible sur la **méthode** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method** .</span></span> <span data-ttu-id="adaa8-229">La **méthode** et **CustomMethod** ne peuvent pas être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="adaa8-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="adaa8-230">Cet exemple envoie une `TEST` requête HTTP à l’API :</span><span class="sxs-lookup"><span data-stu-id="adaa8-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="adaa8-231">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="adaa8-232">-DisableKeepAlive</span></span>

<span data-ttu-id="adaa8-233">Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur **false** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="adaa8-234">Par défaut, **KeepAlive** a la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-234">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="adaa8-235">**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="adaa8-236">-Formulaire</span><span class="sxs-lookup"><span data-stu-id="adaa8-236">-Form</span></span>

<span data-ttu-id="adaa8-237">Convertit un dictionnaire en `multipart/form-data` soumission.</span><span class="sxs-lookup"><span data-stu-id="adaa8-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="adaa8-238">Le **formulaire** ne peut pas être utilisé avec le **corps** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-238">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="adaa8-239">Si **ContentType** est utilisé, il est ignoré.</span><span class="sxs-lookup"><span data-stu-id="adaa8-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="adaa8-240">Les clés du dictionnaire sont utilisées comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="adaa8-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="adaa8-241">Par défaut, les valeurs de formulaire sont converties en valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="adaa8-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="adaa8-242">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis.</span><span class="sxs-lookup"><span data-stu-id="adaa8-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="adaa8-243">Le nom du fichier est soumis en tant que propriété **filename** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="adaa8-244">Le type MIME est défini sur `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="adaa8-245">`Get-Item` peut être utilisé pour simplifier la fourniture de l’objet **System. IO. FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="adaa8-246">Si la valeur est un type de collection, tels que des tableaux ou des listes, le champ for est envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="adaa8-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="adaa8-247">Les valeurs de la liste sont traitées par défaut en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="adaa8-248">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis.</span><span class="sxs-lookup"><span data-stu-id="adaa8-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="adaa8-249">Les collections imbriquées ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="adaa8-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="adaa8-250">Dans l’exemple ci-dessus `tags` , le champ est fourni trois fois dans le formulaire, une fois pour chaque `Vacation` , `Italy` et `2017` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="adaa8-251">Le `pictures` champ est également envoyé une fois pour chaque fichier dans le `2017-Italy` dossier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="adaa8-252">Le contenu binaire des fichiers de ce dossier est soumis en tant que valeurs.</span><span class="sxs-lookup"><span data-stu-id="adaa8-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="adaa8-253">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-253">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="adaa8-254">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="adaa8-254">-Headers</span></span>

<span data-ttu-id="adaa8-255">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="adaa8-256">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="adaa8-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="adaa8-257">Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="adaa8-258">Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes **user-agent** ou cookie.</span><span class="sxs-lookup"><span data-stu-id="adaa8-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="adaa8-259">Les en-têtes associés au contenu, tels que, `Content-Type` sont remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="adaa8-260">-INFILE</span><span class="sxs-lookup"><span data-stu-id="adaa8-260">-InFile</span></span>

<span data-ttu-id="adaa8-261">Obtient le contenu de la demande web à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="adaa8-262">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-262">Enter a path and file name.</span></span> <span data-ttu-id="adaa8-263">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="adaa8-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="adaa8-264">-MaximumRedirection</span></span>

<span data-ttu-id="adaa8-265">Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="adaa8-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="adaa8-266">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="adaa8-266">The default value is 5.</span></span> <span data-ttu-id="adaa8-267">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="adaa8-267">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="adaa8-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="adaa8-268">-MaximumRetryCount</span></span>

<span data-ttu-id="adaa8-269">Spécifie le nombre de tentatives de connexion de PowerShell lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="adaa8-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="adaa8-270">Consultez également le paramètre **RetryIntervalSec** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="adaa8-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="adaa8-271">-Méthode</span><span class="sxs-lookup"><span data-stu-id="adaa8-271">-Method</span></span>

<span data-ttu-id="adaa8-272">Spécifie la méthode utilisée pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="adaa8-273">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="adaa8-273">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="adaa8-274">Default</span><span class="sxs-lookup"><span data-stu-id="adaa8-274">Default</span></span>
- <span data-ttu-id="adaa8-275">DELETE</span><span class="sxs-lookup"><span data-stu-id="adaa8-275">Delete</span></span>
- <span data-ttu-id="adaa8-276">Obtenir</span><span class="sxs-lookup"><span data-stu-id="adaa8-276">Get</span></span>
- <span data-ttu-id="adaa8-277">Head</span><span class="sxs-lookup"><span data-stu-id="adaa8-277">Head</span></span>
- <span data-ttu-id="adaa8-278">Fusionner</span><span class="sxs-lookup"><span data-stu-id="adaa8-278">Merge</span></span>
- <span data-ttu-id="adaa8-279">Options</span><span class="sxs-lookup"><span data-stu-id="adaa8-279">Options</span></span>
- <span data-ttu-id="adaa8-280">Correctif</span><span class="sxs-lookup"><span data-stu-id="adaa8-280">Patch</span></span>
- <span data-ttu-id="adaa8-281">Publier</span><span class="sxs-lookup"><span data-stu-id="adaa8-281">Post</span></span>
- <span data-ttu-id="adaa8-282">Put</span><span class="sxs-lookup"><span data-stu-id="adaa8-282">Put</span></span>
- <span data-ttu-id="adaa8-283">Trace</span><span class="sxs-lookup"><span data-stu-id="adaa8-283">Trace</span></span>

<span data-ttu-id="adaa8-284">Le paramètre **CustomMethod** peut être utilisé pour les méthodes de demande non listées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="adaa8-284">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-285">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="adaa8-285">-NoProxy</span></span>

<span data-ttu-id="adaa8-286">Indique que l’applet de commande ne doit pas utiliser de proxy pour atteindre la destination.</span><span class="sxs-lookup"><span data-stu-id="adaa8-286">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="adaa8-287">Lorsque vous avez besoin de contourner le proxy configuré dans l’environnement, utilisez ce commutateur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-287">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="adaa8-288">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-288">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-289">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="adaa8-289">-OutFile</span></span>

<span data-ttu-id="adaa8-290">Spécifie le fichier de sortie pour lequel cette applet de commande enregistre le corps de la réponse.</span><span class="sxs-lookup"><span data-stu-id="adaa8-290">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="adaa8-291">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-291">Enter a path and file name.</span></span>
<span data-ttu-id="adaa8-292">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-292">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="adaa8-293">Par défaut, `Invoke-WebRequest` retourne les résultats au pipeline.</span><span class="sxs-lookup"><span data-stu-id="adaa8-293">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="adaa8-294">Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-294">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="adaa8-295">-PassThru</span><span class="sxs-lookup"><span data-stu-id="adaa8-295">-PassThru</span></span>

<span data-ttu-id="adaa8-296">Indique que l’applet de commande retourne les résultats, en plus de les écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-296">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="adaa8-297">Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-297">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="adaa8-298">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="adaa8-298">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="adaa8-299">Indique que l’applet de commande doit conserver l' `Authorization` en-tête, le cas échéant, entre les redirections.</span><span class="sxs-lookup"><span data-stu-id="adaa8-299">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="adaa8-300">Par défaut, l’applet de commande supprime l' `Authorization` en-tête avant la redirection.</span><span class="sxs-lookup"><span data-stu-id="adaa8-300">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="adaa8-301">La spécification de ce paramètre désactive cette logique pour les cas où l’en-tête doit être envoyé à l’emplacement de redirection.</span><span class="sxs-lookup"><span data-stu-id="adaa8-301">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="adaa8-302">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-302">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="adaa8-303">-Proxy</span><span class="sxs-lookup"><span data-stu-id="adaa8-303">-Proxy</span></span>

<span data-ttu-id="adaa8-304">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="adaa8-304">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="adaa8-305">Entrez l'URI d'un serveur proxy du réseau.</span><span class="sxs-lookup"><span data-stu-id="adaa8-305">Enter the URI of a network proxy server.</span></span>

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="adaa8-306">-ProxyCredential</span></span>

<span data-ttu-id="adaa8-307">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="adaa8-308">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-308">The default is the current user.</span></span>

<span data-ttu-id="adaa8-309">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , **User@Domain.Com** ou entrez un `PSCredential` objet, tel que celui généré par l' `Get-Credential` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-309">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="adaa8-310">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="adaa8-311">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="adaa8-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="adaa8-313">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="adaa8-314">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="adaa8-315">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-316">-RESUME</span><span class="sxs-lookup"><span data-stu-id="adaa8-316">-Resume</span></span>

<span data-ttu-id="adaa8-317">Effectue le meilleur effort pour reprendre le téléchargement d’un fichier partiel.</span><span class="sxs-lookup"><span data-stu-id="adaa8-317">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="adaa8-318">**Resume** requiert un **fichier** out.</span><span class="sxs-lookup"><span data-stu-id="adaa8-318">**Resume** requires **OutFile** .</span></span>

<span data-ttu-id="adaa8-319">**Resume** fonctionne uniquement sur la taille du fichier local et du fichier distant et n’effectue aucune autre validation que le fichier local et le fichier distant sont identiques.</span><span class="sxs-lookup"><span data-stu-id="adaa8-319">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="adaa8-320">Si la taille du fichier local est inférieure à la taille du fichier distant, l’applet de commande tente de reprendre le téléchargement du fichier et ajoute les octets restants à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="adaa8-320">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="adaa8-321">Si la taille du fichier local est identique à la taille du fichier distant, aucune action n’est effectuée et l’applet de commande suppose que le téléchargement est déjà terminé.</span><span class="sxs-lookup"><span data-stu-id="adaa8-321">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="adaa8-322">Si la taille du fichier local est supérieure à la taille du fichier distant, le fichier local est remplacé et l’intégralité du fichier distant est retéléchargée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-322">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="adaa8-323">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-323">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="adaa8-324">Si le serveur distant ne prend pas en charge la reprise du téléchargement, le fichier local est remplacé et l’intégralité du fichier distant est téléchargée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="adaa8-324">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="adaa8-325">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-325">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="adaa8-326">Si le fichier local n’existe pas, le fichier local est créé et l’intégralité du fichier distant est téléchargée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-326">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="adaa8-327">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-327">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="adaa8-328">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-328">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="adaa8-329">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="adaa8-329">-RetryIntervalSec</span></span>

<span data-ttu-id="adaa8-330">Spécifie l’intervalle entre les nouvelles tentatives pour la connexion lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="adaa8-330">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="adaa8-331">Consultez également le paramètre **MaximumRetryCount** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="adaa8-331">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="adaa8-332">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="adaa8-332">-SessionVariable</span></span>

<span data-ttu-id="adaa8-333">Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-333">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="adaa8-334">Entrez un nom de variable sans le symbole dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="adaa8-334">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="adaa8-335">Lorsque vous spécifiez une variable de session, `Invoke-WebRequest` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adaa8-335">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="adaa8-336">Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-336">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="adaa8-337">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="adaa8-337">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="adaa8-338">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-338">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="adaa8-339">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-339">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="adaa8-340">Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-340">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="adaa8-341">PowerShell utilise les données de l’objet session de demande Web lors de l’établissement de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="adaa8-341">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="adaa8-342">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-342">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="adaa8-343">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-343">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="adaa8-344">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-344">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="adaa8-345">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="adaa8-345">-SkipCertificateCheck</span></span>

<span data-ttu-id="adaa8-346">Ignore les vérifications de validation des certificats.</span><span class="sxs-lookup"><span data-stu-id="adaa8-346">Skips certificate validation checks.</span></span> <span data-ttu-id="adaa8-347">Cela comprend toutes les validations, telles que l’expiration, la révocation, l’autorité racine approuvée, etc.</span><span class="sxs-lookup"><span data-stu-id="adaa8-347">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="adaa8-348">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-348">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="adaa8-349">Ce commutateur est destiné uniquement à être utilisé sur des hôtes connus à l’aide d’un certificat auto-signé à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="adaa8-349">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="adaa8-350">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="adaa8-350">Use at your own risk.</span></span>

<span data-ttu-id="adaa8-351">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-351">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="adaa8-352">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="adaa8-352">-SkipHeaderValidation</span></span>

<span data-ttu-id="adaa8-353">Indique que l’applet de commande doit ajouter des en-têtes à la demande sans validation.</span><span class="sxs-lookup"><span data-stu-id="adaa8-353">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="adaa8-354">Ce commutateur doit être utilisé pour les sites qui requièrent des valeurs d’en-tête qui ne sont pas conformes aux normes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-354">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="adaa8-355">Si vous spécifiez ce commutateur, la validation est désactivée pour permettre la désélection de la valeur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-355">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="adaa8-356">Lorsqu’ils sont spécifiés, tous les en-têtes sont ajoutés sans validation.</span><span class="sxs-lookup"><span data-stu-id="adaa8-356">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="adaa8-357">Ce commutateur désactive la validation pour les valeurs transmises aux paramètres **ContentType** , **headers** et **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-357">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="adaa8-358">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="adaa8-359">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="adaa8-359">-SslProtocol</span></span>

<span data-ttu-id="adaa8-360">Définit les protocoles SSL/TLS qui sont autorisés pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-360">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="adaa8-361">Par défaut, tous les protocoles SSL/TLS pris en charge par le système sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="adaa8-361">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="adaa8-362">**SslProtocol** permet de limiter à des protocoles spécifiques à des fins de conformité.</span><span class="sxs-lookup"><span data-stu-id="adaa8-362">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="adaa8-363">**SslProtocol** utilise l’énumération de l’indicateur **WebSslProtocol** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-363">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="adaa8-364">Il est possible de fournir plusieurs protocoles à l’aide de la notation d’indicateur ou de combiner plusieurs options **WebSslProtocol** avec **Bor** , mais le fait de fournir plusieurs protocoles n’est pas pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-364">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="adaa8-365">Sur les plateformes non-Windows, il n’est pas possible de fournir `'Tls, Tls12'` une option.</span><span class="sxs-lookup"><span data-stu-id="adaa8-365">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="adaa8-366">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-366">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-367">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="adaa8-367">-TimeoutSec</span></span>

<span data-ttu-id="adaa8-368">Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-368">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="adaa8-369">La valeur par défaut, 0, spécifie un délai d'attente indéfini.</span><span class="sxs-lookup"><span data-stu-id="adaa8-369">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="adaa8-370">Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.</span><span class="sxs-lookup"><span data-stu-id="adaa8-370">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="adaa8-371">-Jeton</span><span class="sxs-lookup"><span data-stu-id="adaa8-371">-Token</span></span>

<span data-ttu-id="adaa8-372">Jeton OAuth ou du porteur à inclure dans la demande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-372">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="adaa8-373">Le **jeton** est requis par certaines options **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-373">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="adaa8-374">Elle ne peut pas être utilisée de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="adaa8-374">It cannot be used independently.</span></span>

<span data-ttu-id="adaa8-375">Le **jeton** prend un `SecureString` contenant le jeton.</span><span class="sxs-lookup"><span data-stu-id="adaa8-375">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="adaa8-376">Pour fournir le jeton manuellement, utilisez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="adaa8-376">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="adaa8-377">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="adaa8-377">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="adaa8-378">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="adaa8-378">-TransferEncoding</span></span>

<span data-ttu-id="adaa8-379">Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert.</span><span class="sxs-lookup"><span data-stu-id="adaa8-379">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="adaa8-380">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="adaa8-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="adaa8-381">Mémorisé en bloc</span><span class="sxs-lookup"><span data-stu-id="adaa8-381">Chunked</span></span>
- <span data-ttu-id="adaa8-382">Compresser</span><span class="sxs-lookup"><span data-stu-id="adaa8-382">Compress</span></span>
- <span data-ttu-id="adaa8-383">Deflate</span><span class="sxs-lookup"><span data-stu-id="adaa8-383">Deflate</span></span>
- <span data-ttu-id="adaa8-384">GZip</span><span class="sxs-lookup"><span data-stu-id="adaa8-384">GZip</span></span>
- <span data-ttu-id="adaa8-385">Identité</span><span class="sxs-lookup"><span data-stu-id="adaa8-385">Identity</span></span>

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

### <span data-ttu-id="adaa8-386">-URI</span><span class="sxs-lookup"><span data-stu-id="adaa8-386">-Uri</span></span>

<span data-ttu-id="adaa8-387">Spécifie le Uniform Resource Identifier (URI) de la ressource Internet à laquelle la demande Web est envoyée.</span><span class="sxs-lookup"><span data-stu-id="adaa8-387">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="adaa8-388">Entrez un URI.</span><span class="sxs-lookup"><span data-stu-id="adaa8-388">Enter a URI.</span></span> <span data-ttu-id="adaa8-389">Ce paramètre prend en charge uniquement HTTP ou HTTPs.</span><span class="sxs-lookup"><span data-stu-id="adaa8-389">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="adaa8-390">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="adaa8-390">This parameter is required.</span></span> <span data-ttu-id="adaa8-391">L' **URI** du nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="adaa8-391">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="adaa8-392">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="adaa8-392">-UseBasicParsing</span></span>

<span data-ttu-id="adaa8-393">Ce paramètre est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="adaa8-393">This parameter has been deprecated.</span></span> <span data-ttu-id="adaa8-394">À partir de PowerShell 6.0.0, toutes les requêtes Web utilisent uniquement l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="adaa8-394">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="adaa8-395">Ce paramètre est inclus à des fins de compatibilité descendante uniquement et n’a aucun effet sur le fonctionnement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-395">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="adaa8-396">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="adaa8-396">-UseDefaultCredentials</span></span>

<span data-ttu-id="adaa8-397">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-397">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="adaa8-398">Cela ne peut pas être utilisé avec **l’authentification** ou les **informations d’identification** et peut ne pas être pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="adaa8-398">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="adaa8-399">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="adaa8-399">-UserAgent</span></span>

<span data-ttu-id="adaa8-400">Spécifie une chaîne d'agent utilisateur pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-400">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="adaa8-401">L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` avec de légères variations pour chaque système d’exploitation et plateforme.</span><span class="sxs-lookup"><span data-stu-id="adaa8-401">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="adaa8-402">Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari.</span><span class="sxs-lookup"><span data-stu-id="adaa8-402">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="adaa8-403">Par exemple, la commande suivante utilise la chaîne de l’agent utilisateur pour Internet Explorer :</span><span class="sxs-lookup"><span data-stu-id="adaa8-403">For example, the following command uses the user agent string for Internet Explorer:</span></span>

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

### <span data-ttu-id="adaa8-404">-Websession</span><span class="sxs-lookup"><span data-stu-id="adaa8-404">-WebSession</span></span>

<span data-ttu-id="adaa8-405">Spécifie une session de demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-405">Specifies a web request session.</span></span> <span data-ttu-id="adaa8-406">Entrez le nom de la variable, y compris le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="adaa8-406">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="adaa8-407">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-407">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="adaa8-408">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-408">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="adaa8-409">Les en-têtes associés au contenu, tels que `Content-Type` , sont également remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-409">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="adaa8-410">Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente.</span><span class="sxs-lookup"><span data-stu-id="adaa8-410">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="adaa8-411">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adaa8-411">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="adaa8-412">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="adaa8-412">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="adaa8-413">Pour créer une session de demande Web, entrez un nom de variable, sans signe dollar, dans la valeur du paramètre **SessionVariable** d’une `Invoke-WebRequest` commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-413">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="adaa8-414">`Invoke-WebRequest` crée la session et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-414">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="adaa8-415">Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="adaa8-415">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="adaa8-416">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="adaa8-416">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="adaa8-417">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="adaa8-417">CommonParameters</span></span>

<span data-ttu-id="adaa8-418">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="adaa8-418">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="adaa8-419">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="adaa8-419">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="adaa8-420">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="adaa8-420">INPUTS</span></span>

### <span data-ttu-id="adaa8-421">System.Object</span><span class="sxs-lookup"><span data-stu-id="adaa8-421">System.Object</span></span>

<span data-ttu-id="adaa8-422">Vous pouvez diriger le corps d’une requête Web vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="adaa8-422">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="adaa8-423">SORTIES</span><span class="sxs-lookup"><span data-stu-id="adaa8-423">OUTPUTS</span></span>

### <span data-ttu-id="adaa8-424">Microsoft. PowerShell. Commands. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="adaa8-424">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="adaa8-425">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="adaa8-425">NOTES</span></span>

<span data-ttu-id="adaa8-426">À partir de PowerShell 6.0.0 `Invoke-WebRequest` prend uniquement en charge l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="adaa8-426">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="adaa8-427">Pour plus d’informations sur le type d’objet **Microsoft. PowerShell. Commands. BasicHtmlWebResponseObject** , consultez [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span><span class="sxs-lookup"><span data-stu-id="adaa8-427">For more information about the **Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject** object type, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="adaa8-428">Pour plus d’informations sur la façon dont .NET fournit les services proxy à PowerShell, consultez [accès à Internet via un proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span><span class="sxs-lookup"><span data-stu-id="adaa8-428">For more information about how .NET provides proxy services to PowerShell, see [Accessing the Internet Through a Proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span></span>

## <span data-ttu-id="adaa8-429">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="adaa8-429">RELATED LINKS</span></span>

[<span data-ttu-id="adaa8-430">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="adaa8-430">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="adaa8-431">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="adaa8-431">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="adaa8-432">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="adaa8-432">ConvertTo-Json</span></span>](ConvertTo-Json.md)

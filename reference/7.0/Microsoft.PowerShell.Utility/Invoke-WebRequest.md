---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: b81074e14461b0bf481232553b614e06c23b90b6
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205997"
---
# <span data-ttu-id="46231-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="46231-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="46231-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="46231-104">SYNOPSIS</span></span>
<span data-ttu-id="46231-105">Obtient le contenu d’une page Web sur Internet.</span><span class="sxs-lookup"><span data-stu-id="46231-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="46231-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46231-106">SYNTAX</span></span>

### <span data-ttu-id="46231-107">StandardMethod (par défaut)</span><span class="sxs-lookup"><span data-stu-id="46231-107">StandardMethod (Default)</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="46231-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="46231-108">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="46231-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="46231-109">CustomMethod</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="46231-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="46231-110">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="46231-111">Description</span><span class="sxs-lookup"><span data-stu-id="46231-111">DESCRIPTION</span></span>

<span data-ttu-id="46231-112">L' `Invoke-WebRequest` applet de commande envoie des requêtes http et HTTPS à une page Web ou à un service Web.</span><span class="sxs-lookup"><span data-stu-id="46231-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="46231-113">Elle analyse la réponse et retourne des collections de liens, d’images et d’autres éléments HTML significatifs.</span><span class="sxs-lookup"><span data-stu-id="46231-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="46231-114">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="46231-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="46231-115">À compter de PowerShell 7,0, `Invoke-WebRequest` prend en charge la configuration de proxy définie par les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="46231-115">Beginning in PowerShell 7.0, `Invoke-WebRequest` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="46231-116">Consultez la section [Remarques](#notes) de cet article.</span><span class="sxs-lookup"><span data-stu-id="46231-116">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="46231-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="46231-117">EXAMPLES</span></span>

### <span data-ttu-id="46231-118">Exemple 1 : envoyer une requête Web</span><span class="sxs-lookup"><span data-stu-id="46231-118">Example 1: Send a web request</span></span>

<span data-ttu-id="46231-119">Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour envoyer une requête Web au site Bing.com.</span><span class="sxs-lookup"><span data-stu-id="46231-119">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="46231-120">La première commande émet la demande et enregistre la réponse dans la `$Response` variable.</span><span class="sxs-lookup"><span data-stu-id="46231-120">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="46231-121">La deuxième commande obtient tout **InputField** où la propriété **Name** est similaire `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="46231-121">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="46231-122">Les résultats filtrés sont dirigés vers `Select-Object` pour sélectionner les propriétés **Name** et **value** .</span><span class="sxs-lookup"><span data-stu-id="46231-122">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="46231-123">Exemple 2 : utiliser un service Web avec état</span><span class="sxs-lookup"><span data-stu-id="46231-123">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="46231-124">Cet exemple montre comment utiliser l' `Invoke-WebRequest` applet de commande avec un service Web avec état.</span><span class="sxs-lookup"><span data-stu-id="46231-124">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="46231-125">Le premier appel à `Invoke-WebRequest` envoie une demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="46231-125">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="46231-126">La commande spécifie la valeur « session » pour la valeur du paramètre **-SessionVariable** et enregistre le résultat dans la `$LoginResponse` variable.</span><span class="sxs-lookup"><span data-stu-id="46231-126">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="46231-127">Une fois la commande terminée, la `$LoginResponse` variable contient un `BasicHtmlWebResponseObject` et la `$Session` variable contient un `WebRequestSession` objet.</span><span class="sxs-lookup"><span data-stu-id="46231-127">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="46231-128">L’utilisateur est alors connecté au site.</span><span class="sxs-lookup"><span data-stu-id="46231-128">This logs the user into the site.</span></span>

<span data-ttu-id="46231-129">L’appel à `$Session` par lui-même affiche l' `WebRequestSession` objet dans la variable.</span><span class="sxs-lookup"><span data-stu-id="46231-129">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="46231-130">Le deuxième appel à `Invoke-WebRequest` récupère le profil de l’utilisateur, ce qui nécessite que l’utilisateur soit connecté au site.</span><span class="sxs-lookup"><span data-stu-id="46231-130">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="46231-131">Les données de session stockées dans la `$Session` variable sont utilisées pour fournir des cookies de session au site créé pendant la connexion.</span><span class="sxs-lookup"><span data-stu-id="46231-131">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="46231-132">Le résultat est enregistré dans la `$ProfileResponse` variable.</span><span class="sxs-lookup"><span data-stu-id="46231-132">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="46231-133">L’appel à `$ProfileResponse` par lui-même affiche le `BasicHtmlWebResponseObject` dans la variable.</span><span class="sxs-lookup"><span data-stu-id="46231-133">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="46231-134">Exemple 3 : obtenir des liens à partir d’une page Web</span><span class="sxs-lookup"><span data-stu-id="46231-134">Example 3: Get links from a web page</span></span>

<span data-ttu-id="46231-135">Cet exemple obtient les liens dans une page Web.</span><span class="sxs-lookup"><span data-stu-id="46231-135">This example gets the links in a web page.</span></span> <span data-ttu-id="46231-136">Elle utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web.</span><span class="sxs-lookup"><span data-stu-id="46231-136">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="46231-137">Elle utilise ensuite la propriété **Links** du `BasicHtmlWebResponseObject` qui `Invoke-WebRequest` retourne et la propriété **href** de chaque lien.</span><span class="sxs-lookup"><span data-stu-id="46231-137">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="46231-138">Exemple 4 : écrit le contenu de la réponse dans un fichier à l’aide de l’encodage défini dans la page demandée.</span><span class="sxs-lookup"><span data-stu-id="46231-138">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="46231-139">Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web d’une page de documentation PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46231-139">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="46231-140">La première commande récupère la page et enregistre l’objet de réponse dans la `$Response` variable.</span><span class="sxs-lookup"><span data-stu-id="46231-140">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="46231-141">La deuxième commande crée un `StreamWriter` à utiliser pour écrire le contenu de la réponse dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-141">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="46231-142">La propriété **Encoding** de l’objet Response est utilisée pour définir l’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-142">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="46231-143">Les dernières commandes écrivent la propriété de **contenu** dans le fichier, puis suppriment le `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="46231-143">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="46231-144">Notez que la propriété **Encoding** a la valeur null si la demande Web ne retourne pas de contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="46231-144">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="46231-145">Exemple 5 : envoyer un fichier multipart/form-data</span><span class="sxs-lookup"><span data-stu-id="46231-145">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="46231-146">Cet exemple utilise l' `Invoke-WebRequest` applet de commande upload a file as a `multipart/form-data` submission.</span><span class="sxs-lookup"><span data-stu-id="46231-146">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="46231-147">Le fichier `c:\document.txt` est soumis en tant que champ `document` de formulaire avec le `Content-Type` de `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="46231-147">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="46231-148">Exemple 6 : envoi de données multipart/formulaire simplifié</span><span class="sxs-lookup"><span data-stu-id="46231-148">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="46231-149">Certaines API requièrent des `multipart/form-data` envois pour télécharger des fichiers et du contenu mixte.</span><span class="sxs-lookup"><span data-stu-id="46231-149">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="46231-150">Cet exemple illustre la mise à jour d’un profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46231-150">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="46231-151">Le formulaire de profil requiert les champs suivants : `firstName` ,,,, `lastName` `email` `avatar` `birthday` et `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="46231-151">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="46231-152">L’API attend une image pour le profil utilisateur pic à fournir dans le `avatar` champ.</span><span class="sxs-lookup"><span data-stu-id="46231-152">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="46231-153">L’API accepte également l' `hobbies` envoi de plusieurs entrées sous la même forme.</span><span class="sxs-lookup"><span data-stu-id="46231-153">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="46231-154">Lors de la création de la `$Form` Hashtable, les noms de clé sont utilisés comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="46231-154">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="46231-155">Par défaut, les valeurs de la HashTable sont converties en chaînes.</span><span class="sxs-lookup"><span data-stu-id="46231-155">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="46231-156">Si une valeur **System. IO. FileInfo** est présente, le contenu du fichier est envoyé.</span><span class="sxs-lookup"><span data-stu-id="46231-156">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="46231-157">Si une collection telle que des tableaux ou des listes est présente, le champ de formulaire est envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="46231-157">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="46231-158">En utilisant `Get-Item` sur la `avatar` clé, l' `FileInfo` objet est défini comme valeur.</span><span class="sxs-lookup"><span data-stu-id="46231-158">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="46231-159">Le résultat est que les données d’image de `jdoe.png` sont envoyées.</span><span class="sxs-lookup"><span data-stu-id="46231-159">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="46231-160">En fournissant une liste à la `hobbies` clé, le `hobbies` champ est présent dans les envois une fois pour chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="46231-160">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="46231-161">Exemple 7 : intercepter les messages non réussis de Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="46231-161">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="46231-162">Lorsque `Invoke-WebRequest` rencontre un message http sans succès (404, 500, etc.), il ne retourne aucune sortie et lève une erreur de fin d’opération.</span><span class="sxs-lookup"><span data-stu-id="46231-162">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="46231-163">Pour intercepter l’erreur et afficher le **statusCode** , vous pouvez l’encadrer dans un `try/catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="46231-163">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

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

<span data-ttu-id="46231-164">La commande appelle `Invoke-WebRequest` avec un **ErrorAction** **Stop** , qui force `Invoke-WebRequest` à lever une erreur d’arrêt sur les demandes ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="46231-164">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="46231-165">L’erreur de fin est interceptée par le `catch` bloc qui récupère le **statusCode** de l’objet **exception** .</span><span class="sxs-lookup"><span data-stu-id="46231-165">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="46231-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46231-166">PARAMETERS</span></span>

### <span data-ttu-id="46231-167">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="46231-167">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="46231-168">Autorise l’envoi d’informations d’identification et de secrets sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="46231-168">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="46231-169">Par défaut, le fait de fournir des **informations d’identification** ou toute option **d’authentification** avec un **URI** qui ne commence pas par `https://` génère une erreur et la demande est abandonnée pour empêcher la communication accidentelle de secrets en texte brut sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="46231-169">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="46231-170">Pour remplacer ce comportement à vos propres risques, fournissez le paramètre **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="46231-170">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="46231-171">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="46231-171">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="46231-172">Elle est fournie uniquement pour la compatibilité avec les systèmes hérités qui ne peuvent pas fournir de connexions chiffrées.</span><span class="sxs-lookup"><span data-stu-id="46231-172">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="46231-173">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="46231-173">Use at your own risk.</span></span>

<span data-ttu-id="46231-174">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-175">-Authentification</span><span class="sxs-lookup"><span data-stu-id="46231-175">-Authentication</span></span>

<span data-ttu-id="46231-176">Spécifie le type d’authentification explicite à utiliser pour la requête.</span><span class="sxs-lookup"><span data-stu-id="46231-176">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="46231-177">La valeur par défaut est **None** (Aucun).</span><span class="sxs-lookup"><span data-stu-id="46231-177">The default is **None** .</span></span>
<span data-ttu-id="46231-178">**L’authentification** ne peut pas être utilisée avec **UseDefaultCredentials** .</span><span class="sxs-lookup"><span data-stu-id="46231-178">**Authentication** cannot be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="46231-179">Options d’authentification disponibles :</span><span class="sxs-lookup"><span data-stu-id="46231-179">Available Authentication Options:</span></span>

- <span data-ttu-id="46231-180">**None** : il s’agit de l’option par défaut lorsque **l’authentification** n’est pas fournie ; aucune authentification explicite n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="46231-180">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="46231-181">De **base** : requiert des **informations d’identification** .</span><span class="sxs-lookup"><span data-stu-id="46231-181">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="46231-182">Les informations d’identification sont envoyées dans un en-tête d’authentification de base RFC 7617 au format `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="46231-182">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="46231-183">**Bearer** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="46231-183">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="46231-184">Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="46231-184">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="46231-185">Il s’agit d’un alias pour **OAuth**</span><span class="sxs-lookup"><span data-stu-id="46231-185">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="46231-186">**OAuth** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="46231-186">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="46231-187">Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="46231-187">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="46231-188">Il s’agit d’un alias pour le **porteur**</span><span class="sxs-lookup"><span data-stu-id="46231-188">This is an alias for **Bearer**</span></span>

<span data-ttu-id="46231-189">La spécification de **l’authentification** remplace tous les `Authorization` en-têtes fournis aux **en-têtes** ou inclus dans **websession** .</span><span class="sxs-lookup"><span data-stu-id="46231-189">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="46231-190">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-190">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-191">-Corps</span><span class="sxs-lookup"><span data-stu-id="46231-191">-Body</span></span>

<span data-ttu-id="46231-192">Spécifie le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="46231-192">Specifies the body of the request.</span></span> <span data-ttu-id="46231-193">Le corps est le contenu de la demande qui suit les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="46231-193">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="46231-194">Vous pouvez également diriger une valeur de corps vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="46231-194">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="46231-195">Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="46231-195">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="46231-196">Lorsque l’entrée est une requête d’extraction et que le corps est un `IDictionary` (en général, une table de hachage), le corps est ajouté à l’URI en tant que paramètres de requête.</span><span class="sxs-lookup"><span data-stu-id="46231-196">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="46231-197">Pour les autres types de demande (par exemple, la publication), le corps est défini comme valeur du corps de la requête au `name=value` format standard.</span><span class="sxs-lookup"><span data-stu-id="46231-197">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="46231-198">Le paramètre **Body** peut également accepter un `System.Net.Http.MultipartFormDataContent` objet.</span><span class="sxs-lookup"><span data-stu-id="46231-198">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="46231-199">Cela facilite les `multipart/form-data` demandes.</span><span class="sxs-lookup"><span data-stu-id="46231-199">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="46231-200">Lorsqu’un objet **MultipartFormDataContent** est fourni pour **le corps** , tous les en-têtes associés au contenu fournis aux paramètres **ContentType** , **headers** ou **websession** sont remplacés par les en-têtes de contenu de l’objet **MultipartFormDataContent** .</span><span class="sxs-lookup"><span data-stu-id="46231-200">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="46231-201">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-201">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-202">-Certificat</span><span class="sxs-lookup"><span data-stu-id="46231-202">-Certificate</span></span>

<span data-ttu-id="46231-203">Spécifie le certificat client utilisé pour une demande Web sécurisée.</span><span class="sxs-lookup"><span data-stu-id="46231-203">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="46231-204">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="46231-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="46231-205">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="46231-205">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="46231-206">Si le certificat n’est pas valide ou ne dispose pas des autorisations suffisantes, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="46231-206">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="46231-207">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="46231-207">-CertificateThumbprint</span></span>

<span data-ttu-id="46231-208">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="46231-208">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="46231-209">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="46231-209">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="46231-210">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="46231-210">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="46231-211">Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="46231-211">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="46231-212">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46231-212">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="46231-213">Cette fonctionnalité n’est actuellement prise en charge que sur les plateformes de système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="46231-213">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="46231-214">-ContentType</span><span class="sxs-lookup"><span data-stu-id="46231-214">-ContentType</span></span>

<span data-ttu-id="46231-215">Spécifie le type de contenu de la demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-215">Specifies the content type of the web request.</span></span>

<span data-ttu-id="46231-216">Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-WebRequest` définit le type de contenu sur `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="46231-216">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="46231-217">Dans le cas contraire, le type de contenu n’est pas spécifié dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="46231-217">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="46231-218">**ContentType** est substitué lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="46231-218">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="46231-219">-Credential</span><span class="sxs-lookup"><span data-stu-id="46231-219">-Credential</span></span>

<span data-ttu-id="46231-220">Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="46231-220">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="46231-221">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="46231-221">The default is the current user.</span></span>

<span data-ttu-id="46231-222">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="46231-222">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="46231-223">Les **informations d’identification** peuvent être utilisées seules ou conjointement avec certaines options de paramètres **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="46231-223">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="46231-224">Lorsqu’il est utilisé seul, il fournit uniquement des informations d’identification au serveur distant si le serveur distant envoie une demande de stimulation d’authentification.</span><span class="sxs-lookup"><span data-stu-id="46231-224">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="46231-225">Lorsqu’elles sont utilisées avec les options **d’authentification** , les informations d’identification sont envoyées explicitement.</span><span class="sxs-lookup"><span data-stu-id="46231-225">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="46231-226">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="46231-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="46231-227">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="46231-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="46231-228">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="46231-228">-CustomMethod</span></span>

<span data-ttu-id="46231-229">Spécifie une méthode personnalisée utilisée pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="46231-229">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="46231-230">Cela peut être utilisé si la méthode de demande requise par le point de terminaison n’est pas une option disponible sur la **méthode** .</span><span class="sxs-lookup"><span data-stu-id="46231-230">This can be used if the Request Method required by the endpoint isn't an available option on the **Method** .</span></span> <span data-ttu-id="46231-231">La **méthode** et **CustomMethod** ne peuvent pas être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="46231-231">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="46231-232">Cet exemple envoie une `TEST` requête HTTP à l’API :</span><span class="sxs-lookup"><span data-stu-id="46231-232">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="46231-233">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-233">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-234">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="46231-234">-DisableKeepAlive</span></span>

<span data-ttu-id="46231-235">Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur **false** .</span><span class="sxs-lookup"><span data-stu-id="46231-235">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="46231-236">Par défaut, **KeepAlive** a la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="46231-236">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="46231-237">**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="46231-237">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="46231-238">-Formulaire</span><span class="sxs-lookup"><span data-stu-id="46231-238">-Form</span></span>

<span data-ttu-id="46231-239">Convertit un dictionnaire en `multipart/form-data` soumission.</span><span class="sxs-lookup"><span data-stu-id="46231-239">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="46231-240">Le **formulaire** ne peut pas être utilisé avec le **corps** .</span><span class="sxs-lookup"><span data-stu-id="46231-240">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="46231-241">Si **ContentType** est utilisé, il est ignoré.</span><span class="sxs-lookup"><span data-stu-id="46231-241">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="46231-242">Les clés du dictionnaire sont utilisées comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="46231-242">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="46231-243">Par défaut, les valeurs de formulaire sont converties en valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="46231-243">By default, form values are converted to string values.</span></span>

<span data-ttu-id="46231-244">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis.</span><span class="sxs-lookup"><span data-stu-id="46231-244">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="46231-245">Le nom du fichier est soumis en tant que propriété **filename** .</span><span class="sxs-lookup"><span data-stu-id="46231-245">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="46231-246">Le type MIME est défini sur `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="46231-246">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="46231-247">`Get-Item` peut être utilisé pour simplifier la fourniture de l’objet **System. IO. FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="46231-247">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="46231-248">Si la valeur est un type de collection, tels que des tableaux ou des listes, le champ for est envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="46231-248">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="46231-249">Les valeurs de la liste sont traitées par défaut en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="46231-249">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="46231-250">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis.</span><span class="sxs-lookup"><span data-stu-id="46231-250">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="46231-251">Les collections imbriquées ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="46231-251">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="46231-252">Dans l’exemple ci-dessus `tags` , le champ est fourni trois fois dans le formulaire, une fois pour chaque `Vacation` , `Italy` et `2017` .</span><span class="sxs-lookup"><span data-stu-id="46231-252">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="46231-253">Le `pictures` champ est également envoyé une fois pour chaque fichier dans le `2017-Italy` dossier.</span><span class="sxs-lookup"><span data-stu-id="46231-253">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="46231-254">Le contenu binaire des fichiers de ce dossier est soumis en tant que valeurs.</span><span class="sxs-lookup"><span data-stu-id="46231-254">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="46231-255">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="46231-255">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="46231-256">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="46231-256">-Headers</span></span>

<span data-ttu-id="46231-257">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-257">Specifies the headers of the web request.</span></span> <span data-ttu-id="46231-258">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="46231-258">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="46231-259">Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="46231-259">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="46231-260">Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes **user-agent** ou cookie.</span><span class="sxs-lookup"><span data-stu-id="46231-260">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="46231-261">Les en-têtes associés au contenu, tels que, `Content-Type` sont remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="46231-261">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="46231-262">-INFILE</span><span class="sxs-lookup"><span data-stu-id="46231-262">-InFile</span></span>

<span data-ttu-id="46231-263">Obtient le contenu de la demande web à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-263">Gets the content of the web request from a file.</span></span> <span data-ttu-id="46231-264">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-264">Enter a path and file name.</span></span> <span data-ttu-id="46231-265">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="46231-265">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="46231-266">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="46231-266">-MaximumRedirection</span></span>

<span data-ttu-id="46231-267">Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="46231-267">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="46231-268">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="46231-268">The default value is 5.</span></span> <span data-ttu-id="46231-269">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="46231-269">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="46231-270">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="46231-270">-MaximumRetryCount</span></span>

<span data-ttu-id="46231-271">Spécifie le nombre de tentatives de connexion de PowerShell lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="46231-271">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="46231-272">Consultez également le paramètre **RetryIntervalSec** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="46231-272">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="46231-273">-Méthode</span><span class="sxs-lookup"><span data-stu-id="46231-273">-Method</span></span>

<span data-ttu-id="46231-274">Spécifie la méthode utilisée pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-274">Specifies the method used for the web request.</span></span> <span data-ttu-id="46231-275">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="46231-275">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="46231-276">Default</span><span class="sxs-lookup"><span data-stu-id="46231-276">Default</span></span>
- <span data-ttu-id="46231-277">DELETE</span><span class="sxs-lookup"><span data-stu-id="46231-277">Delete</span></span>
- <span data-ttu-id="46231-278">Obtenir</span><span class="sxs-lookup"><span data-stu-id="46231-278">Get</span></span>
- <span data-ttu-id="46231-279">Head</span><span class="sxs-lookup"><span data-stu-id="46231-279">Head</span></span>
- <span data-ttu-id="46231-280">Fusionner</span><span class="sxs-lookup"><span data-stu-id="46231-280">Merge</span></span>
- <span data-ttu-id="46231-281">Options</span><span class="sxs-lookup"><span data-stu-id="46231-281">Options</span></span>
- <span data-ttu-id="46231-282">Correctif</span><span class="sxs-lookup"><span data-stu-id="46231-282">Patch</span></span>
- <span data-ttu-id="46231-283">Publier</span><span class="sxs-lookup"><span data-stu-id="46231-283">Post</span></span>
- <span data-ttu-id="46231-284">Put</span><span class="sxs-lookup"><span data-stu-id="46231-284">Put</span></span>
- <span data-ttu-id="46231-285">Trace</span><span class="sxs-lookup"><span data-stu-id="46231-285">Trace</span></span>

<span data-ttu-id="46231-286">Le paramètre **CustomMethod** peut être utilisé pour les méthodes de demande non listées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="46231-286">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="46231-287">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="46231-287">-NoProxy</span></span>

<span data-ttu-id="46231-288">Indique que l’applet de commande ne doit pas utiliser de proxy pour atteindre la destination.</span><span class="sxs-lookup"><span data-stu-id="46231-288">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="46231-289">Lorsque vous avez besoin de contourner le proxy configuré dans l’environnement, utilisez ce commutateur.</span><span class="sxs-lookup"><span data-stu-id="46231-289">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="46231-290">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-290">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-291">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="46231-291">-OutFile</span></span>

<span data-ttu-id="46231-292">Spécifie le fichier de sortie pour lequel cette applet de commande enregistre le corps de la réponse.</span><span class="sxs-lookup"><span data-stu-id="46231-292">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="46231-293">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-293">Enter a path and file name.</span></span>
<span data-ttu-id="46231-294">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="46231-294">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="46231-295">Par défaut, `Invoke-WebRequest` retourne les résultats au pipeline.</span><span class="sxs-lookup"><span data-stu-id="46231-295">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="46231-296">Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="46231-296">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="46231-297">-PassThru</span><span class="sxs-lookup"><span data-stu-id="46231-297">-PassThru</span></span>

<span data-ttu-id="46231-298">Indique que l’applet de commande retourne les résultats, en plus de les écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-298">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="46231-299">Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="46231-299">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="46231-300">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="46231-300">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="46231-301">Indique que l’applet de commande doit conserver l' `Authorization` en-tête, le cas échéant, entre les redirections.</span><span class="sxs-lookup"><span data-stu-id="46231-301">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="46231-302">Par défaut, l’applet de commande supprime l' `Authorization` en-tête avant la redirection.</span><span class="sxs-lookup"><span data-stu-id="46231-302">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="46231-303">La spécification de ce paramètre désactive cette logique pour les cas où l’en-tête doit être envoyé à l’emplacement de redirection.</span><span class="sxs-lookup"><span data-stu-id="46231-303">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="46231-304">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-304">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-305">-Proxy</span><span class="sxs-lookup"><span data-stu-id="46231-305">-Proxy</span></span>

<span data-ttu-id="46231-306">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="46231-306">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="46231-307">Entrez l'URI d'un serveur proxy du réseau.</span><span class="sxs-lookup"><span data-stu-id="46231-307">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="46231-308">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="46231-308">-ProxyCredential</span></span>

<span data-ttu-id="46231-309">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="46231-309">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="46231-310">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="46231-310">The default is the current user.</span></span>

<span data-ttu-id="46231-311">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , **User@Domain.Com** ou entrez un `PSCredential` objet, tel que celui généré par l' `Get-Credential` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="46231-311">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="46231-312">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="46231-312">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="46231-313">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="46231-313">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="46231-314">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="46231-314">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="46231-315">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="46231-315">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="46231-316">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="46231-316">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="46231-317">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="46231-317">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="46231-318">-RESUME</span><span class="sxs-lookup"><span data-stu-id="46231-318">-Resume</span></span>

<span data-ttu-id="46231-319">Effectue le meilleur effort pour reprendre le téléchargement d’un fichier partiel.</span><span class="sxs-lookup"><span data-stu-id="46231-319">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="46231-320">**Resume** requiert un **fichier** out.</span><span class="sxs-lookup"><span data-stu-id="46231-320">**Resume** requires **OutFile** .</span></span>

<span data-ttu-id="46231-321">**Resume** fonctionne uniquement sur la taille du fichier local et du fichier distant et n’effectue aucune autre validation que le fichier local et le fichier distant sont identiques.</span><span class="sxs-lookup"><span data-stu-id="46231-321">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="46231-322">Si la taille du fichier local est inférieure à la taille du fichier distant, l’applet de commande tente de reprendre le téléchargement du fichier et ajoute les octets restants à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="46231-322">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="46231-323">Si la taille du fichier local est identique à la taille du fichier distant, aucune action n’est effectuée et l’applet de commande suppose que le téléchargement est déjà terminé.</span><span class="sxs-lookup"><span data-stu-id="46231-323">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="46231-324">Si la taille du fichier local est supérieure à la taille du fichier distant, le fichier local est remplacé et l’intégralité du fichier distant est retéléchargée.</span><span class="sxs-lookup"><span data-stu-id="46231-324">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="46231-325">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="46231-325">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="46231-326">Si le serveur distant ne prend pas en charge la reprise du téléchargement, le fichier local est remplacé et l’intégralité du fichier distant est téléchargée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="46231-326">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="46231-327">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="46231-327">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="46231-328">Si le fichier local n’existe pas, le fichier local est créé et l’intégralité du fichier distant est téléchargée.</span><span class="sxs-lookup"><span data-stu-id="46231-328">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="46231-329">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="46231-329">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="46231-330">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="46231-330">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="46231-331">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="46231-331">-RetryIntervalSec</span></span>

<span data-ttu-id="46231-332">Spécifie l’intervalle entre les nouvelles tentatives pour la connexion lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="46231-332">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="46231-333">Consultez également le paramètre **MaximumRetryCount** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="46231-333">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="46231-334">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="46231-334">-SessionVariable</span></span>

<span data-ttu-id="46231-335">Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="46231-335">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="46231-336">Entrez un nom de variable sans le symbole dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="46231-336">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="46231-337">Lorsque vous spécifiez une variable de session, `Invoke-WebRequest` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46231-337">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="46231-338">Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="46231-338">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="46231-339">Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante.</span><span class="sxs-lookup"><span data-stu-id="46231-339">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="46231-340">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46231-340">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="46231-341">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="46231-341">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="46231-342">Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="46231-342">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="46231-343">PowerShell utilise les données de l’objet session de demande Web lors de l’établissement de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="46231-343">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="46231-344">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="46231-344">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="46231-345">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-345">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="46231-346">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="46231-346">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="46231-347">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="46231-347">-SkipCertificateCheck</span></span>

<span data-ttu-id="46231-348">Ignore les vérifications de validation des certificats.</span><span class="sxs-lookup"><span data-stu-id="46231-348">Skips certificate validation checks.</span></span> <span data-ttu-id="46231-349">Cela comprend toutes les validations, telles que l’expiration, la révocation, l’autorité racine approuvée, etc.</span><span class="sxs-lookup"><span data-stu-id="46231-349">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="46231-350">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="46231-350">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="46231-351">Ce commutateur est destiné uniquement à être utilisé sur des hôtes connus à l’aide d’un certificat auto-signé à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="46231-351">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="46231-352">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="46231-352">Use at your own risk.</span></span>

<span data-ttu-id="46231-353">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-353">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-354">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="46231-354">-SkipHeaderValidation</span></span>

<span data-ttu-id="46231-355">Indique que l’applet de commande doit ajouter des en-têtes à la demande sans validation.</span><span class="sxs-lookup"><span data-stu-id="46231-355">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="46231-356">Ce commutateur doit être utilisé pour les sites qui requièrent des valeurs d’en-tête qui ne sont pas conformes aux normes.</span><span class="sxs-lookup"><span data-stu-id="46231-356">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="46231-357">Si vous spécifiez ce commutateur, la validation est désactivée pour permettre la désélection de la valeur.</span><span class="sxs-lookup"><span data-stu-id="46231-357">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="46231-358">Lorsqu’ils sont spécifiés, tous les en-têtes sont ajoutés sans validation.</span><span class="sxs-lookup"><span data-stu-id="46231-358">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="46231-359">Ce commutateur désactive la validation pour les valeurs transmises aux paramètres **ContentType** , **headers** et **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="46231-359">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="46231-360">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-360">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-361">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="46231-361">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="46231-362">Ce paramètre fait en sorte que l’applet de commande ignore les États d’erreur HTTP et continue à traiter les réponses.</span><span class="sxs-lookup"><span data-stu-id="46231-362">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="46231-363">Les réponses d’erreur sont écrites dans le pipeline comme si elles se trouvaient correctement.</span><span class="sxs-lookup"><span data-stu-id="46231-363">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="46231-364">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="46231-364">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46231-365">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="46231-365">-SslProtocol</span></span>

<span data-ttu-id="46231-366">Définit les protocoles SSL/TLS qui sont autorisés pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="46231-366">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="46231-367">Par défaut, tous les protocoles SSL/TLS pris en charge par le système sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="46231-367">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="46231-368">**SslProtocol** permet de limiter à des protocoles spécifiques à des fins de conformité.</span><span class="sxs-lookup"><span data-stu-id="46231-368">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="46231-369">**SslProtocol** utilise l’énumération de l’indicateur **WebSslProtocol** .</span><span class="sxs-lookup"><span data-stu-id="46231-369">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="46231-370">Il est possible de fournir plusieurs protocoles à l’aide de la notation d’indicateur ou de combiner plusieurs options **WebSslProtocol** avec **Bor** , mais le fait de fournir plusieurs protocoles n’est pas pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="46231-370">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="46231-371">Sur les plateformes non-Windows, il n’est pas possible de fournir `'Tls, Tls12'` une option.</span><span class="sxs-lookup"><span data-stu-id="46231-371">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="46231-372">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="46231-372">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="46231-373">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="46231-373">-TimeoutSec</span></span>

<span data-ttu-id="46231-374">Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="46231-374">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="46231-375">La valeur par défaut, 0, spécifie un délai d'attente indéfini.</span><span class="sxs-lookup"><span data-stu-id="46231-375">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="46231-376">Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.</span><span class="sxs-lookup"><span data-stu-id="46231-376">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="46231-377">-Jeton</span><span class="sxs-lookup"><span data-stu-id="46231-377">-Token</span></span>

<span data-ttu-id="46231-378">Jeton OAuth ou du porteur à inclure dans la demande.</span><span class="sxs-lookup"><span data-stu-id="46231-378">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="46231-379">Le **jeton** est requis par certaines options **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="46231-379">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="46231-380">Elle ne peut pas être utilisée de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="46231-380">It cannot be used independently.</span></span>

<span data-ttu-id="46231-381">Le **jeton** prend un `SecureString` contenant le jeton.</span><span class="sxs-lookup"><span data-stu-id="46231-381">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="46231-382">Pour fournir le jeton manuellement, utilisez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="46231-382">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="46231-383">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="46231-383">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="46231-384">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="46231-384">-TransferEncoding</span></span>

<span data-ttu-id="46231-385">Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert.</span><span class="sxs-lookup"><span data-stu-id="46231-385">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="46231-386">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="46231-386">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="46231-387">Mémorisé en bloc</span><span class="sxs-lookup"><span data-stu-id="46231-387">Chunked</span></span>
- <span data-ttu-id="46231-388">Compresser</span><span class="sxs-lookup"><span data-stu-id="46231-388">Compress</span></span>
- <span data-ttu-id="46231-389">Deflate</span><span class="sxs-lookup"><span data-stu-id="46231-389">Deflate</span></span>
- <span data-ttu-id="46231-390">GZip</span><span class="sxs-lookup"><span data-stu-id="46231-390">GZip</span></span>
- <span data-ttu-id="46231-391">Identité</span><span class="sxs-lookup"><span data-stu-id="46231-391">Identity</span></span>

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

### <span data-ttu-id="46231-392">-URI</span><span class="sxs-lookup"><span data-stu-id="46231-392">-Uri</span></span>

<span data-ttu-id="46231-393">Spécifie le Uniform Resource Identifier (URI) de la ressource Internet à laquelle la demande Web est envoyée.</span><span class="sxs-lookup"><span data-stu-id="46231-393">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="46231-394">Entrez un URI.</span><span class="sxs-lookup"><span data-stu-id="46231-394">Enter a URI.</span></span> <span data-ttu-id="46231-395">Ce paramètre prend en charge uniquement HTTP ou HTTPs.</span><span class="sxs-lookup"><span data-stu-id="46231-395">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="46231-396">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="46231-396">This parameter is required.</span></span> <span data-ttu-id="46231-397">L' **URI** du nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="46231-397">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="46231-398">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="46231-398">-UseBasicParsing</span></span>

<span data-ttu-id="46231-399">Ce paramètre est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="46231-399">This parameter has been deprecated.</span></span> <span data-ttu-id="46231-400">À partir de PowerShell 6.0.0, toutes les requêtes Web utilisent uniquement l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="46231-400">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="46231-401">Ce paramètre est inclus à des fins de compatibilité descendante uniquement et n’a aucun effet sur le fonctionnement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="46231-401">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="46231-402">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="46231-402">-UseDefaultCredentials</span></span>

<span data-ttu-id="46231-403">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web.</span><span class="sxs-lookup"><span data-stu-id="46231-403">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="46231-404">Cela ne peut pas être utilisé avec **l’authentification** ou les **informations d’identification** et peut ne pas être pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="46231-404">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="46231-405">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="46231-405">-UserAgent</span></span>

<span data-ttu-id="46231-406">Spécifie une chaîne d'agent utilisateur pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-406">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="46231-407">L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` avec de légères variations pour chaque système d’exploitation et plateforme.</span><span class="sxs-lookup"><span data-stu-id="46231-407">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="46231-408">Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari.</span><span class="sxs-lookup"><span data-stu-id="46231-408">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="46231-409">Par exemple, la commande suivante utilise la chaîne de l’agent utilisateur pour Internet Explorer :</span><span class="sxs-lookup"><span data-stu-id="46231-409">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="46231-410">-Websession</span><span class="sxs-lookup"><span data-stu-id="46231-410">-WebSession</span></span>

<span data-ttu-id="46231-411">Spécifie une session de demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-411">Specifies a web request session.</span></span> <span data-ttu-id="46231-412">Entrez le nom de la variable, y compris le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="46231-412">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="46231-413">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="46231-413">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="46231-414">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="46231-414">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="46231-415">Les en-têtes associés au contenu, tels que `Content-Type` , sont également remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="46231-415">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="46231-416">Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente.</span><span class="sxs-lookup"><span data-stu-id="46231-416">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="46231-417">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46231-417">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="46231-418">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="46231-418">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="46231-419">Pour créer une session de demande Web, entrez un nom de variable, sans signe dollar, dans la valeur du paramètre **SessionVariable** d’une `Invoke-WebRequest` commande.</span><span class="sxs-lookup"><span data-stu-id="46231-419">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="46231-420">`Invoke-WebRequest` crée la session et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="46231-420">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="46231-421">Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="46231-421">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="46231-422">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="46231-422">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="46231-423">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46231-423">CommonParameters</span></span>

<span data-ttu-id="46231-424">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46231-424">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46231-425">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="46231-425">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46231-426">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="46231-426">INPUTS</span></span>

### <span data-ttu-id="46231-427">System.Object</span><span class="sxs-lookup"><span data-stu-id="46231-427">System.Object</span></span>

<span data-ttu-id="46231-428">Vous pouvez diriger le corps d’une requête Web vers `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="46231-428">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="46231-429">SORTIES</span><span class="sxs-lookup"><span data-stu-id="46231-429">OUTPUTS</span></span>

### <span data-ttu-id="46231-430">Microsoft. PowerShell. Commands. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="46231-430">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="46231-431">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="46231-431">NOTES</span></span>

<span data-ttu-id="46231-432">À partir de PowerShell 6.0.0 `Invoke-WebRequest` prend uniquement en charge l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="46231-432">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="46231-433">Pour plus d’informations, consultez [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span><span class="sxs-lookup"><span data-stu-id="46231-433">For more information, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="46231-434">En raison des modifications apportées à .NET Core 3,1, PowerShell 7,0 et versions ultérieures utilisent la propriété [httpclient. defaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) pour déterminer la configuration du proxy.</span><span class="sxs-lookup"><span data-stu-id="46231-434">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="46231-435">La valeur de cette propriété est déterminée par votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="46231-435">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="46231-436">**Pour Windows** : lit la configuration du proxy à partir des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="46231-436">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="46231-437">Si ces variables ne sont pas définies, la propriété est dérivée des paramètres de proxy de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46231-437">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="46231-438">**Pour MacOS** : lit la configuration du proxy à partir des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="46231-438">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="46231-439">Si ces variables ne sont pas définies, la propriété est dérivée des paramètres de proxy du système.</span><span class="sxs-lookup"><span data-stu-id="46231-439">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="46231-440">**Pour Linux** : lit la configuration du proxy à partir des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="46231-440">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="46231-441">Si ces variables ne sont pas définies, la propriété Initialise une instance non configurée qui ignore toutes les adresses.</span><span class="sxs-lookup"><span data-stu-id="46231-441">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="46231-442">Les variables d’environnement utilisées pour `DefaultProxy` l’initialisation sur des plateformes basées sur Windows et UNIX sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="46231-442">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="46231-443">` HTTP_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="46231-443">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="46231-444">`HTTPS_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTPs.</span><span class="sxs-lookup"><span data-stu-id="46231-444">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="46231-445">`ALL_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP et HTTPs en cas d' `HTTP_PROXY` `HTTPS_PROXY` absence de définition.</span><span class="sxs-lookup"><span data-stu-id="46231-445">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="46231-446">`NO_PROXY`: liste séparée par des virgules des noms d’hôtes qui doivent être exclus du proxy.</span><span class="sxs-lookup"><span data-stu-id="46231-446">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="46231-447">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="46231-447">RELATED LINKS</span></span>

[<span data-ttu-id="46231-448">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="46231-448">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="46231-449">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="46231-449">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="46231-450">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="46231-450">ConvertTo-Json</span></span>](ConvertTo-Json.md)

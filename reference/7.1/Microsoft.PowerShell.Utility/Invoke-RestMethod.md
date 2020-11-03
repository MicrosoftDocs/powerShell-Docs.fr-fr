---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: d00885d0911d20dee0e5c498e5e339af4fa39a34
ms.sourcegitcommit: eaac7af89171379df2e20464ebee9fc7e7d7674a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "93206214"
---
# <span data-ttu-id="e2517-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="e2517-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="e2517-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e2517-104">SYNOPSIS</span></span>
<span data-ttu-id="e2517-105">Envoie une demande HTTP ou HTTPS à un service web RESTful.</span><span class="sxs-lookup"><span data-stu-id="e2517-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="e2517-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2517-106">SYNTAX</span></span>

### <span data-ttu-id="e2517-107">StandardMethod (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e2517-107">StandardMethod (Default)</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="e2517-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="e2517-108">StandardMethodNoProxy</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="e2517-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="e2517-109">CustomMethodNoProxy</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="e2517-110">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="e2517-110">CustomMethod</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="e2517-111">Description</span><span class="sxs-lookup"><span data-stu-id="e2517-111">Description</span></span>

<span data-ttu-id="e2517-112">L' `Invoke-RestMethod` applet de commande envoie des requêtes http et HTTPS à des services Web REST qui retournent des données structurées de façon riche.</span><span class="sxs-lookup"><span data-stu-id="e2517-112">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="e2517-113">PowerShell met en forme la réponse en fonction du type de données.</span><span class="sxs-lookup"><span data-stu-id="e2517-113">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="e2517-114">Pour un flux RSS ou ATOM, PowerShell retourne les nœuds XML Item ou entry.</span><span class="sxs-lookup"><span data-stu-id="e2517-114">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="e2517-115">Pour les JavaScript Object Notation (JSON) ou XML, PowerShell convertit, ou désérialise, le contenu en objets.</span><span class="sxs-lookup"><span data-stu-id="e2517-115">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into objects.</span></span>

<span data-ttu-id="e2517-116">Cette applet de commande est introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-116">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="e2517-117">À compter de PowerShell 7,0, `Invoke-RestMethod` prend en charge la configuration de proxy définie par les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="e2517-117">Beginning in PowerShell 7.0, `Invoke-RestMethod` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="e2517-118">Consultez la section [Remarques](#notes) de cet article.</span><span class="sxs-lookup"><span data-stu-id="e2517-118">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="e2517-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e2517-119">EXAMPLES</span></span>

### <span data-ttu-id="e2517-120">Exemple 1 : récupérer le flux RSS PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2517-120">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="e2517-121">Cet exemple utilise l' `Invoke-RestMethod` applet de commande pour récupérer des informations à partir du flux RSS du blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2517-121">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="e2517-122">La commande utilise l' `Format-Table` applet de commande pour afficher les valeurs des propriétés **title** et **pubDate** de chaque blog dans une table.</span><span class="sxs-lookup"><span data-stu-id="e2517-122">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
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

### <span data-ttu-id="e2517-123">Exemple 2 : exécuter une demande de publication</span><span class="sxs-lookup"><span data-stu-id="e2517-123">Example 2: Run a POST request</span></span>

<span data-ttu-id="e2517-124">Dans cet exemple, un utilisateur exécute `Invoke-RestMethod` pour effectuer une demande de publication sur un site Web intranet dans l’organisation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-124">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

<span data-ttu-id="e2517-125">Les informations d’identification sont demandées, puis stockées dans `$Cred` et l’URL à laquelle vous accédez est définie dans `$Url` .</span><span class="sxs-lookup"><span data-stu-id="e2517-125">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="e2517-126">La `$Body` variable décrit les critères de recherche, spécifie le volume partagé de cluster comme mode de sortie et spécifie une période de temps pour les données retournées qui démarrent il y a deux jours et se termine il y a un jour.</span><span class="sxs-lookup"><span data-stu-id="e2517-126">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="e2517-127">La variable Body spécifie des valeurs pour les paramètres qui s’appliquent à l’API REST particulière avec laquelle `Invoke-RestMethod` communique.</span><span class="sxs-lookup"><span data-stu-id="e2517-127">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="e2517-128">La `Invoke-RestMethod` commande est exécutée avec toutes les variables sur place, en spécifiant un chemin d’accès et un nom de fichier pour le fichier de sortie CSV résultant.</span><span class="sxs-lookup"><span data-stu-id="e2517-128">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="e2517-129">Exemple 3 : suivre les liens de relation</span><span class="sxs-lookup"><span data-stu-id="e2517-129">Example 3: Follow relation links</span></span>

<span data-ttu-id="e2517-130">Certaines API REST prennent en charge la pagination via des liens de relation par [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="e2517-130">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="e2517-131">Au lieu d’analyser l’en-tête pour obtenir l’URL de la page suivante, vous pouvez faire en sorte que l’applet de commande le fasse pour vous.</span><span class="sxs-lookup"><span data-stu-id="e2517-131">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="e2517-132">Cet exemple retourne les deux premières pages de problèmes à partir du référentiel GitHub de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2517-132">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="e2517-133">Exemple 4 : envoi de données multipart/formulaire simplifié</span><span class="sxs-lookup"><span data-stu-id="e2517-133">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="e2517-134">Certaines API requièrent des `multipart/form-data` envois pour télécharger des fichiers et du contenu mixte.</span><span class="sxs-lookup"><span data-stu-id="e2517-134">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="e2517-135">Cet exemple montre comment mettre à jour le profil d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-135">This example demonstrates how to update a user's profile.</span></span>

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
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="e2517-136">Le formulaire de profil requiert les champs suivants : `firstName` ,,,, `lastName` `email` `avatar` `birthday` et `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="e2517-136">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="e2517-137">L’API attend une image pour le profil utilisateur pic à fournir dans le `avatar` champ.</span><span class="sxs-lookup"><span data-stu-id="e2517-137">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="e2517-138">L’API accepte également plusieurs `hobbies` entrées à soumettre sous la même forme.</span><span class="sxs-lookup"><span data-stu-id="e2517-138">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="e2517-139">Lors de la création de la `$Form` Hashtable, les noms de clé sont utilisés comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2517-139">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="e2517-140">Par défaut, les valeurs de la HashTable sont converties en chaînes.</span><span class="sxs-lookup"><span data-stu-id="e2517-140">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="e2517-141">Si une `System.IO.FileInfo` valeur est présente, le contenu du fichier est envoyé.</span><span class="sxs-lookup"><span data-stu-id="e2517-141">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="e2517-142">Si une collection telle que des tableaux ou des listes est présente, le champ de formulaire sera envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e2517-142">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="e2517-143">En utilisant `Get-Item` sur la `avatar` clé, l' `FileInfo` objet est défini comme valeur.</span><span class="sxs-lookup"><span data-stu-id="e2517-143">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="e2517-144">Le résultat est que les données d’image de `jdoe.png` seront envoyées.</span><span class="sxs-lookup"><span data-stu-id="e2517-144">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="e2517-145">En fournissant une liste à la `hobbies` clé, le `hobbies` champ est présent dans les envois une fois pour chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="e2517-145">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="e2517-146">Exemple 5 : passer plusieurs en-têtes</span><span class="sxs-lookup"><span data-stu-id="e2517-146">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="e2517-147">Les API requièrent souvent des en-têtes passés pour l’authentification ou la validation.</span><span class="sxs-lookup"><span data-stu-id="e2517-147">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="e2517-148">Cet exemple montre comment passer plusieurs en-têtes d’un `hash-table` à une API REST.</span><span class="sxs-lookup"><span data-stu-id="e2517-148">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## <span data-ttu-id="e2517-149">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2517-149">Parameters</span></span>

### <span data-ttu-id="e2517-150">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="e2517-150">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="e2517-151">Autorise l’envoi d’informations d’identification et de secrets sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="e2517-151">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="e2517-152">Par défaut, fournir des **informations d’identification** ou une option **d’authentification** avec un **URI** qui ne commence pas par génère `https://` une erreur et la demande est abandonnée pour empêcher la communication accidentelle de secrets en texte brut sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="e2517-152">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="e2517-153">Pour remplacer ce comportement à vos propres risques, fournissez le paramètre **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="e2517-153">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="e2517-154">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="e2517-154">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="e2517-155">Elle est fournie uniquement pour la compatibilité avec les systèmes hérités qui ne peuvent pas fournir de connexions chiffrées.</span><span class="sxs-lookup"><span data-stu-id="e2517-155">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="e2517-156">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="e2517-156">Use at your own risk.</span></span>

<span data-ttu-id="e2517-157">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-157">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-158">-Authentification</span><span class="sxs-lookup"><span data-stu-id="e2517-158">-Authentication</span></span>

<span data-ttu-id="e2517-159">Spécifie le type d’authentification explicite à utiliser pour la requête.</span><span class="sxs-lookup"><span data-stu-id="e2517-159">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="e2517-160">La valeur par défaut est **None** (Aucun).</span><span class="sxs-lookup"><span data-stu-id="e2517-160">The default is **None** .</span></span>
<span data-ttu-id="e2517-161">**L’authentification** ne peut pas être utilisée avec **UseDefaultCredentials** .</span><span class="sxs-lookup"><span data-stu-id="e2517-161">**Authentication** can't be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="e2517-162">Options d’authentification disponibles :</span><span class="sxs-lookup"><span data-stu-id="e2517-162">Available Authentication Options:</span></span>

- <span data-ttu-id="e2517-163">**None** : il s’agit de l’option par défaut lorsque **l’authentification** n’est pas fournie.</span><span class="sxs-lookup"><span data-stu-id="e2517-163">**None** : This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="e2517-164">Aucune authentification explicite n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e2517-164">No explicit authentication will be used.</span></span>
- <span data-ttu-id="e2517-165">De **base** : requiert des **informations d’identification** .</span><span class="sxs-lookup"><span data-stu-id="e2517-165">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="e2517-166">Les informations d’identification seront utilisées pour envoyer un en-tête d’authentification de base RFC 7617 au `Authorization: Basic` format `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="e2517-166">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="e2517-167">**Bearer** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="e2517-167">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="e2517-168">Enverra `Authorization: Bearer` l’en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="e2517-168">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="e2517-169">Il s’agit d’un alias pour **OAuth**</span><span class="sxs-lookup"><span data-stu-id="e2517-169">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="e2517-170">**OAuth** : requiert un **jeton** .</span><span class="sxs-lookup"><span data-stu-id="e2517-170">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="e2517-171">Enverra un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni.</span><span class="sxs-lookup"><span data-stu-id="e2517-171">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="e2517-172">Il s’agit d’un alias pour le **porteur**</span><span class="sxs-lookup"><span data-stu-id="e2517-172">This is an alias for **Bearer**</span></span>

<span data-ttu-id="e2517-173">La spécification de **l’authentification** remplacera tous les `Authorization` en-têtes fournis aux **en-têtes** ou inclus dans **websession** .</span><span class="sxs-lookup"><span data-stu-id="e2517-173">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="e2517-174">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-175">-Corps</span><span class="sxs-lookup"><span data-stu-id="e2517-175">-Body</span></span>

<span data-ttu-id="e2517-176">Spécifie le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="e2517-176">Specifies the body of the request.</span></span> <span data-ttu-id="e2517-177">Le corps est le contenu de la demande qui suit les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="e2517-177">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="e2517-178">Vous pouvez également diriger une valeur de corps vers `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="e2517-178">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="e2517-179">Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="e2517-179">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="e2517-180">Lorsque l’entrée est une requête d’extraction et que le corps est un `IDictionary` (en général, une table de hachage), le corps est ajouté à la Uniform Resource Identifier (Uri) en tant que paramètres de requête.</span><span class="sxs-lookup"><span data-stu-id="e2517-180">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="e2517-181">Pour d'autres types de demandes (par exemple POST), le corps est défini comme valeur du corps de la demande au format nom standard=valeur.</span><span class="sxs-lookup"><span data-stu-id="e2517-181">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="e2517-182">Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un autre `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2517-182">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="e2517-183">Le paramètre **Body** peut également accepter un objet **System .net. http. MultipartFormDataContent** .</span><span class="sxs-lookup"><span data-stu-id="e2517-183">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="e2517-184">Cela facilitera les `multipart/form-data` demandes.</span><span class="sxs-lookup"><span data-stu-id="e2517-184">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="e2517-185">Lorsqu’un **objet MultipartFormDataContent** est fourni pour **le corps** , tous les en-têtes associés au contenu fournis aux paramètres **ContentType** , **headers** ou **websession** sont remplacés par les en-têtes de contenu de l' `MultipartFormDataContent` objet.</span><span class="sxs-lookup"><span data-stu-id="e2517-185">When a **MultipartFormDataContent** object is supplied for **Body** , any content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="e2517-186">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-186">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-187">-Certificat</span><span class="sxs-lookup"><span data-stu-id="e2517-187">-Certificate</span></span>

<span data-ttu-id="e2517-188">Spécifie le certificat client utilisé pour une demande web sécurisée.</span><span class="sxs-lookup"><span data-stu-id="e2517-188">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="e2517-189">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="e2517-189">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="e2517-190">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="e2517-190">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="e2517-191">Si le certificat n’est pas valide ou ne dispose pas des autorisations suffisantes, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="e2517-191">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="e2517-192">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e2517-192">-CertificateThumbprint</span></span>

<span data-ttu-id="e2517-193">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="e2517-193">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="e2517-194">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="e2517-194">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e2517-195">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="e2517-195">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="e2517-196">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="e2517-196">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="e2517-197">Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2517-197">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="e2517-198">Cette fonctionnalité n’est actuellement prise en charge que sur les plateformes de système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="e2517-198">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="e2517-199">-ContentType</span><span class="sxs-lookup"><span data-stu-id="e2517-199">-ContentType</span></span>

<span data-ttu-id="e2517-200">Spécifie le type de contenu de la demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-200">Specifies the content type of the web request.</span></span>

<span data-ttu-id="e2517-201">Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-RestMethod` définit le type de contenu sur `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="e2517-201">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="e2517-202">Dans le cas contraire, le type de contenu n’est pas spécifié dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="e2517-202">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="e2517-203">**ContentType** est substitué lorsqu’un `MultipartFormDataContent` objet est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="e2517-203">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="e2517-204">-Credential</span><span class="sxs-lookup"><span data-stu-id="e2517-204">-Credential</span></span>

<span data-ttu-id="e2517-205">Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande.</span><span class="sxs-lookup"><span data-stu-id="e2517-205">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="e2517-206">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e2517-206">The default is the current user.</span></span>

<span data-ttu-id="e2517-207">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e2517-207">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="e2517-208">Les **informations d’identification** peuvent être utilisées seules ou conjointement avec certaines options de paramètres **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="e2517-208">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="e2517-209">Lorsqu’il est utilisé seul, il fournit uniquement des informations d’identification au serveur distant si le serveur distant envoie une demande de stimulation d’authentification.</span><span class="sxs-lookup"><span data-stu-id="e2517-209">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="e2517-210">Lorsqu’elles sont utilisées avec les options **d’authentification** , les informations d’identification sont envoyées de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="e2517-210">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="e2517-211">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="e2517-211">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="e2517-212">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="e2517-212">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="e2517-213">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="e2517-213">-CustomMethod</span></span>

<span data-ttu-id="e2517-214">Spécifie la méthode personnalisée utilisée pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="e2517-214">Specifies custom method used for the web request.</span></span> <span data-ttu-id="e2517-215">Cela peut être utilisé avec la méthode de demande requise par le point de terminaison n’est pas une option disponible sur la **méthode** .</span><span class="sxs-lookup"><span data-stu-id="e2517-215">This can be used with the Request Method required by the endpoint is not an available option on the **Method** .</span></span> <span data-ttu-id="e2517-216">Les **méthodes** et **CustomMethod** ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="e2517-216">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="e2517-217">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e2517-217">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="e2517-218">Une `TEST` requête HTTP est alors envoyée à l’API.</span><span class="sxs-lookup"><span data-stu-id="e2517-218">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="e2517-219">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-219">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-220">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="e2517-220">-DisableKeepAlive</span></span>

<span data-ttu-id="e2517-221">Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur false.</span><span class="sxs-lookup"><span data-stu-id="e2517-221">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="e2517-222">Par défaut, **KeepAlive** a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="e2517-222">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="e2517-223">**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="e2517-223">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="e2517-224">-FollowRelLink</span><span class="sxs-lookup"><span data-stu-id="e2517-224">-FollowRelLink</span></span>

<span data-ttu-id="e2517-225">Indique que l’applet de commande doit suivre les liens de relation.</span><span class="sxs-lookup"><span data-stu-id="e2517-225">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="e2517-226">Certaines API REST prennent en charge la pagination via des liens de relation par [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="e2517-226">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="e2517-227">Au lieu d’analyser l’en-tête pour obtenir l’URL de la page suivante, vous pouvez faire en sorte que l’applet de commande le fasse pour vous.</span><span class="sxs-lookup"><span data-stu-id="e2517-227">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="e2517-228">Pour définir le nombre de fois où les liens de relation doivent être suivis, utilisez le paramètre **MaximumFollowRelLink** .</span><span class="sxs-lookup"><span data-stu-id="e2517-228">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="e2517-229">Lors de l’utilisation de ce commutateur, l’applet de commande retourne une collection de pages de résultats.</span><span class="sxs-lookup"><span data-stu-id="e2517-229">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="e2517-230">Chaque page de résultats peut contenir plusieurs éléments de résultat.</span><span class="sxs-lookup"><span data-stu-id="e2517-230">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="e2517-231">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-232">-Formulaire</span><span class="sxs-lookup"><span data-stu-id="e2517-232">-Form</span></span>

<span data-ttu-id="e2517-233">Convertit un dictionnaire en `multipart/form-data` soumission.</span><span class="sxs-lookup"><span data-stu-id="e2517-233">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="e2517-234">Le **formulaire** ne peut pas être utilisé avec le **corps** .</span><span class="sxs-lookup"><span data-stu-id="e2517-234">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="e2517-235">Si **ContentType** sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="e2517-235">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="e2517-236">Les clés du dictionnaire seront utilisées comme noms de champs de formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2517-236">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="e2517-237">Par défaut, les valeurs de formulaire sont converties en valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e2517-237">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="e2517-238">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire sera envoyé.</span><span class="sxs-lookup"><span data-stu-id="e2517-238">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="e2517-239">Le nom du fichier sera envoyé en tant que `filename` .</span><span class="sxs-lookup"><span data-stu-id="e2517-239">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="e2517-240">Le MIME sera défini sur `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="e2517-240">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="e2517-241">`Get-Item` peut être utilisé pour simplifier la fourniture de l’objet **System. IO. FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="e2517-241">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="e2517-242">Si la valeur est un type de collection, tel qu’un tableau ou une liste, le champ for est envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e2517-242">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="e2517-243">Les valeurs de la liste sont traitées par défaut en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="e2517-243">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="e2517-244">Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire sera envoyé.</span><span class="sxs-lookup"><span data-stu-id="e2517-244">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="e2517-245">Les collections imbriquées ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e2517-245">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="e2517-246">Dans l’exemple ci-dessus, le `tags` champ sera fourni trois fois dans le formulaire, une fois pour chaque `Vacation` , `Italy` et `2017` .</span><span class="sxs-lookup"><span data-stu-id="e2517-246">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="e2517-247">Le `pictures` champ est également envoyé une fois pour chaque fichier dans le `2017-Italy` dossier.</span><span class="sxs-lookup"><span data-stu-id="e2517-247">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="e2517-248">Le contenu binaire des fichiers de ce dossier sera soumis en tant que valeurs.</span><span class="sxs-lookup"><span data-stu-id="e2517-248">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="e2517-249">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-249">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="e2517-250">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="e2517-250">-Headers</span></span>

<span data-ttu-id="e2517-251">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-251">Specifies the headers of the web request.</span></span> <span data-ttu-id="e2517-252">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="e2517-252">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="e2517-253">Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="e2517-253">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="e2517-254">Vous ne pouvez pas utiliser ce paramètre pour spécifier des `User-Agent` en-têtes ou des cookies.</span><span class="sxs-lookup"><span data-stu-id="e2517-254">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="e2517-255">Les en-têtes associés au contenu, tels que, `Content-Type` sont remplacés lorsqu’un `MultipartFormDataContent` objet est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="e2517-255">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="e2517-256">-INFILE</span><span class="sxs-lookup"><span data-stu-id="e2517-256">-InFile</span></span>

<span data-ttu-id="e2517-257">Obtient le contenu de la demande web à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="e2517-257">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="e2517-258">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e2517-258">Enter a path and file name.</span></span> <span data-ttu-id="e2517-259">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="e2517-259">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="e2517-260">-MaximumFollowRelLink</span><span class="sxs-lookup"><span data-stu-id="e2517-260">-MaximumFollowRelLink</span></span>

<span data-ttu-id="e2517-261">Spécifie le nombre de fois où les liens de relation doivent être suivis si **FollowRelLink** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e2517-261">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="e2517-262">Une valeur inférieure peut être nécessaire si l’API REST est limitée en raison d’un trop grand nombre de requêtes.</span><span class="sxs-lookup"><span data-stu-id="e2517-262">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="e2517-263">La valeur par défaut est `[Int32]::MaxValue`.</span><span class="sxs-lookup"><span data-stu-id="e2517-263">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="e2517-264">La valeur 0 (zéro) empêche les liens de relation suivants.</span><span class="sxs-lookup"><span data-stu-id="e2517-264">A value of 0 (zero) prevents following relation links.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-265">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="e2517-265">-MaximumRedirection</span></span>

<span data-ttu-id="e2517-266">Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="e2517-266">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="e2517-267">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="e2517-267">The default value is 5.</span></span> <span data-ttu-id="e2517-268">La valeur 0 (zéro) empêche toute redirection.</span><span class="sxs-lookup"><span data-stu-id="e2517-268">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="e2517-269">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="e2517-269">-MaximumRetryCount</span></span>

<span data-ttu-id="e2517-270">Spécifie le nombre de tentatives de connexion de PowerShell lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="e2517-270">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="e2517-271">Consultez également le paramètre **RetryIntervalSec** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="e2517-271">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="e2517-272">-Méthode</span><span class="sxs-lookup"><span data-stu-id="e2517-272">-Method</span></span>

<span data-ttu-id="e2517-273">Spécifie la méthode utilisée pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-273">Specifies the method used for the web request.</span></span> <span data-ttu-id="e2517-274">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="e2517-274">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e2517-275">Default</span><span class="sxs-lookup"><span data-stu-id="e2517-275">Default</span></span>
- <span data-ttu-id="e2517-276">DELETE</span><span class="sxs-lookup"><span data-stu-id="e2517-276">Delete</span></span>
- <span data-ttu-id="e2517-277">Obtenir</span><span class="sxs-lookup"><span data-stu-id="e2517-277">Get</span></span>
- <span data-ttu-id="e2517-278">Head</span><span class="sxs-lookup"><span data-stu-id="e2517-278">Head</span></span>
- <span data-ttu-id="e2517-279">Fusionner</span><span class="sxs-lookup"><span data-stu-id="e2517-279">Merge</span></span>
- <span data-ttu-id="e2517-280">Options</span><span class="sxs-lookup"><span data-stu-id="e2517-280">Options</span></span>
- <span data-ttu-id="e2517-281">Correctif</span><span class="sxs-lookup"><span data-stu-id="e2517-281">Patch</span></span>
- <span data-ttu-id="e2517-282">Publier</span><span class="sxs-lookup"><span data-stu-id="e2517-282">Post</span></span>
- <span data-ttu-id="e2517-283">Put</span><span class="sxs-lookup"><span data-stu-id="e2517-283">Put</span></span>
- <span data-ttu-id="e2517-284">Trace</span><span class="sxs-lookup"><span data-stu-id="e2517-284">Trace</span></span>

<span data-ttu-id="e2517-285">Le paramètre **CustomMethod** peut être utilisé pour les méthodes de demande non listées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e2517-285">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="e2517-286">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="e2517-286">-NoProxy</span></span>

<span data-ttu-id="e2517-287">Indique que l’applet de commande n’utilisera pas de proxy pour atteindre la destination.</span><span class="sxs-lookup"><span data-stu-id="e2517-287">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="e2517-288">Si vous avez besoin de contourner le proxy configuré dans Internet Explorer, ou un proxy spécifié dans l’environnement, utilisez ce commutateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-288">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="e2517-289">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e2517-289">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="e2517-290">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="e2517-290">-OutFile</span></span>

<span data-ttu-id="e2517-291">Enregistre le corps de la réponse dans le fichier de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2517-291">Saves the response body in the specified output file.</span></span> <span data-ttu-id="e2517-292">Entrez un chemin d'accès et un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e2517-292">Enter a path and file name.</span></span> <span data-ttu-id="e2517-293">Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="e2517-293">If you omit the path, the default is the current location.</span></span> <span data-ttu-id="e2517-294">Le nom est traité comme un chemin d’accès littéral.</span><span class="sxs-lookup"><span data-stu-id="e2517-294">The name is treated as a literal path.</span></span> <span data-ttu-id="e2517-295">Les noms qui contiennent des crochets ( `[]` ) doivent être placés entre guillemets simples ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="e2517-295">Names that contain brackets (`[]`) must be enclosed in single quotes (`'`).</span></span>

<span data-ttu-id="e2517-296">Par défaut, `Invoke-RestMethod` retourne les résultats au pipeline.</span><span class="sxs-lookup"><span data-stu-id="e2517-296">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="e2517-297">Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="e2517-297">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="e2517-298">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e2517-298">-PassThru</span></span>

<span data-ttu-id="e2517-299">Retourne les résultats, en plus de les écrire dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="e2517-299">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="e2517-300">Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-300">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="e2517-301">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="e2517-301">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="e2517-302">Indique que l’applet de commande doit conserver l' `Authorization` en-tête, le cas échéant, entre les redirections.</span><span class="sxs-lookup"><span data-stu-id="e2517-302">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="e2517-303">Par défaut, l’applet de commande supprime l' `Authorization` en-tête avant la redirection.</span><span class="sxs-lookup"><span data-stu-id="e2517-303">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="e2517-304">La spécification de ce paramètre désactive cette logique pour les cas où l’en-tête doit être envoyé à l’emplacement de redirection.</span><span class="sxs-lookup"><span data-stu-id="e2517-304">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="e2517-305">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-305">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-306">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e2517-306">-Proxy</span></span>

<span data-ttu-id="e2517-307">Utilise un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="e2517-307">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="e2517-308">Entrez le Uniform Resource Identifier (URI) d’un serveur proxy réseau.</span><span class="sxs-lookup"><span data-stu-id="e2517-308">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="e2517-309">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-309">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-310">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e2517-310">-ProxyCredential</span></span>

<span data-ttu-id="e2517-311">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="e2517-311">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="e2517-312">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e2517-312">The default is the current user.</span></span>

<span data-ttu-id="e2517-313">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , **User@Domain.Com** ou entrez un `PSCredential` objet, tel que celui généré par l' `Get-Credential` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-313">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="e2517-314">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="e2517-315">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-316">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="e2517-316">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="e2517-317">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="e2517-317">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="e2517-318">Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-318">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="e2517-319">Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-319">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="e2517-320">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="e2517-320">-ResponseHeadersVariable</span></span>

<span data-ttu-id="e2517-321">Crée un dictionnaire d’en-têtes de réponse et l’enregistre dans la valeur de la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e2517-321">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="e2517-322">Les clés du dictionnaire contiendront les noms de champs de l’en-tête de réponse renvoyé par le serveur Web et les valeurs seront les valeurs de champ respectives.</span><span class="sxs-lookup"><span data-stu-id="e2517-322">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="e2517-323">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-323">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-324">-RESUME</span><span class="sxs-lookup"><span data-stu-id="e2517-324">-Resume</span></span>

<span data-ttu-id="e2517-325">Effectue le meilleur effort pour reprendre le téléchargement d’un fichier partiel.</span><span class="sxs-lookup"><span data-stu-id="e2517-325">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="e2517-326">Le paramètre **Resume** requiert le paramètre de **fichier** out.</span><span class="sxs-lookup"><span data-stu-id="e2517-326">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="e2517-327">**Resume** fonctionne uniquement sur la taille du fichier local et du fichier distant et n’effectue aucune autre validation que le fichier local et le fichier distant sont identiques.</span><span class="sxs-lookup"><span data-stu-id="e2517-327">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="e2517-328">Si la taille du fichier local est inférieure à la taille du fichier distant, l’applet de commande tente de reprendre le téléchargement du fichier et ajoute les octets restants à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="e2517-328">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="e2517-329">Si la taille du fichier local est identique à la taille du fichier distant, aucune action n’est effectuée et l’applet de commande suppose que le téléchargement est déjà terminé.</span><span class="sxs-lookup"><span data-stu-id="e2517-329">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="e2517-330">Si la taille du fichier local est supérieure à la taille du fichier distant, le fichier local est remplacé et l’intégralité du fichier distant est retéléchargée.</span><span class="sxs-lookup"><span data-stu-id="e2517-330">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="e2517-331">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="e2517-331">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="e2517-332">Si le serveur distant ne prend pas en charge la reprise du téléchargement, le fichier local sera remplacé et l’intégralité du fichier distant sera à nouveau téléchargée.</span><span class="sxs-lookup"><span data-stu-id="e2517-332">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="e2517-333">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="e2517-333">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="e2517-334">Si le fichier local n’existe pas, le fichier local est créé et l’intégralité du fichier distant est entièrement téléchargée.</span><span class="sxs-lookup"><span data-stu-id="e2517-334">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="e2517-335">Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .</span><span class="sxs-lookup"><span data-stu-id="e2517-335">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="e2517-336">Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-336">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="e2517-337">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e2517-337">-RetryIntervalSec</span></span>

<span data-ttu-id="e2517-338">Spécifie l’intervalle entre les nouvelles tentatives pour la connexion lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu.</span><span class="sxs-lookup"><span data-stu-id="e2517-338">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="e2517-339">Consultez également le paramètre **MaximumRetryCount** pour spécifier le nombre de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="e2517-339">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="e2517-340">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="e2517-340">-SessionVariable</span></span>

<span data-ttu-id="e2517-341">Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="e2517-341">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="e2517-342">Entrez un nom de variable sans le symbole dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="e2517-342">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="e2517-343">Lorsque vous spécifiez une variable de session, `Invoke-RestMethod` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2517-343">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="e2517-344">Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="e2517-344">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="e2517-345">Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente.</span><span class="sxs-lookup"><span data-stu-id="e2517-345">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="e2517-346">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-346">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="e2517-347">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="e2517-347">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="e2517-348">Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="e2517-348">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="e2517-349">PowerShell utilise les données de l’objet session de demande Web lors de l’établissement de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="e2517-349">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="e2517-350">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="e2517-350">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="e2517-351">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-351">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="e2517-352">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-352">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="e2517-353">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="e2517-353">-SkipCertificateCheck</span></span>

<span data-ttu-id="e2517-354">Ignore les vérifications de validation de certificat qui incluent toutes les validations, telles que l’expiration, la révocation, l’autorité racine de confiance, etc.</span><span class="sxs-lookup"><span data-stu-id="e2517-354">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="e2517-355">L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="e2517-355">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="e2517-356">Ce commutateur est destiné uniquement à être utilisé sur des hôtes connus à l’aide d’un certificat auto-signé à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="e2517-356">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="e2517-357">Utilisez à vos propres risques.</span><span class="sxs-lookup"><span data-stu-id="e2517-357">Use at your own risk.</span></span>

<span data-ttu-id="e2517-358">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-359">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="e2517-359">-SkipHeaderValidation</span></span>

<span data-ttu-id="e2517-360">Indique que l’applet de commande doit ajouter des en-têtes à la demande sans validation.</span><span class="sxs-lookup"><span data-stu-id="e2517-360">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="e2517-361">Ce commutateur doit être utilisé pour les sites qui requièrent des valeurs d’en-tête qui ne sont pas conformes aux normes.</span><span class="sxs-lookup"><span data-stu-id="e2517-361">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="e2517-362">Si vous spécifiez ce commutateur, la validation est désactivée pour permettre la désélection de la valeur.</span><span class="sxs-lookup"><span data-stu-id="e2517-362">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="e2517-363">Lorsqu’ils sont spécifiés, tous les en-têtes sont ajoutés sans validation.</span><span class="sxs-lookup"><span data-stu-id="e2517-363">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="e2517-364">Cette opération désactive la validation des valeurs transmises aux paramètres **ContentType** , **headers** et **UserAgent** .</span><span class="sxs-lookup"><span data-stu-id="e2517-364">This will disable validation for values passed to the **ContentType** , **Headers** , and **UserAgent** parameters.</span></span>

<span data-ttu-id="e2517-365">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="e2517-365">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="e2517-366">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="e2517-366">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="e2517-367">Ce paramètre fait en sorte que l’applet de commande ignore les États d’erreur HTTP et continue à traiter les réponses.</span><span class="sxs-lookup"><span data-stu-id="e2517-367">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="e2517-368">Les réponses d’erreur sont écrites dans le pipeline comme si elles se trouvaient correctement.</span><span class="sxs-lookup"><span data-stu-id="e2517-368">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="e2517-369">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e2517-369">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="e2517-370">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="e2517-370">-SslProtocol</span></span>

<span data-ttu-id="e2517-371">Définit les protocoles SSL/TLS qui sont autorisés pour la demande Web.</span><span class="sxs-lookup"><span data-stu-id="e2517-371">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="e2517-372">Par défaut, tous les protocoles SSL/TLS pris en charge par le système sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e2517-372">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="e2517-373">**SslProtocol** permet de limiter à des protocoles spécifiques à des fins de conformité.</span><span class="sxs-lookup"><span data-stu-id="e2517-373">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="e2517-374">**SslProtocol** utilise l' `WebSslProtocol` énumération d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-374">**SslProtocol** uses the `WebSslProtocol` Flag Enum.</span></span> <span data-ttu-id="e2517-375">Il est possible de fournir plus d’un protocole à l’aide de la notation d’indicateur ou de combiner plusieurs `WebSslProtocol` options avec `-bor` , mais le fait de fournir plusieurs protocoles n’est pas pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e2517-375">It is possible to supply more than one protocol using flag notation or combining multiple `WebSslProtocol` options with `-bor`, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="e2517-376">Sur les plateformes non-Windows, il se peut qu’il ne soit pas possible de fournir `Tls` ou `Tls12` en tant qu’option.</span><span class="sxs-lookup"><span data-stu-id="e2517-376">On non-Windows platforms it may not be possible to supply `Tls` or `Tls12` as an option.</span></span> <span data-ttu-id="e2517-377">La prise en charge de `Tls13` n’est pas disponible sur tous les systèmes d’exploitation et doit être vérifiée sur la base du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e2517-377">Support for `Tls13` is not available on all operating systems and will need to be verified on a per operating system basis.</span></span>

<span data-ttu-id="e2517-378">Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0 et la prise en charge de `Tls13` a été ajoutée dans powershell 7,1.</span><span class="sxs-lookup"><span data-stu-id="e2517-378">This feature was added in PowerShell 6.0.0 and support for `Tls13` was added in PowerShell 7.1.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12, Tls13

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-379">-StatusCodeVariable</span><span class="sxs-lookup"><span data-stu-id="e2517-379">-StatusCodeVariable</span></span>

<span data-ttu-id="e2517-380">Ce paramètre spécifie une variable à laquelle est affectée la valeur entière d’un code d’État.</span><span class="sxs-lookup"><span data-stu-id="e2517-380">This parameter specifies a variable that's assigned a status code's integer value.</span></span> <span data-ttu-id="e2517-381">Le paramètre peut identifier les messages de réussite ou d’échec lorsqu’il est utilisé avec le paramètre **SkipHttpErrorCheck** .</span><span class="sxs-lookup"><span data-stu-id="e2517-381">The parameter can identify success messages or failure messages when used with the **SkipHttpErrorCheck** parameter.</span></span>

<span data-ttu-id="e2517-382">Entrez le nom de la variable du paramètre sous la forme d’une chaîne comme `-StatusCodeVariable "scv"` .</span><span class="sxs-lookup"><span data-stu-id="e2517-382">Input the parameter's variable name as a string such as `-StatusCodeVariable "scv"`.</span></span>

<span data-ttu-id="e2517-383">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e2517-383">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e2517-384">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="e2517-384">-TimeoutSec</span></span>

<span data-ttu-id="e2517-385">Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes.</span><span class="sxs-lookup"><span data-stu-id="e2517-385">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="e2517-386">La valeur par défaut, 0, spécifie un délai d'attente indéfini.</span><span class="sxs-lookup"><span data-stu-id="e2517-386">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="e2517-387">Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.</span><span class="sxs-lookup"><span data-stu-id="e2517-387">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="e2517-388">-Jeton</span><span class="sxs-lookup"><span data-stu-id="e2517-388">-Token</span></span>

<span data-ttu-id="e2517-389">Jeton OAuth ou du porteur à inclure dans la demande.</span><span class="sxs-lookup"><span data-stu-id="e2517-389">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="e2517-390">Le **jeton** est requis par certaines options **d’authentification** .</span><span class="sxs-lookup"><span data-stu-id="e2517-390">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="e2517-391">Elle ne peut pas être utilisée de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="e2517-391">It can't be used independently.</span></span>

<span data-ttu-id="e2517-392">Le **jeton** accepte un `SecureString` qui contient le jeton.</span><span class="sxs-lookup"><span data-stu-id="e2517-392">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="e2517-393">Pour fournir le jeton, utilisez manuellement les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e2517-393">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="e2517-394">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e2517-394">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="e2517-395">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="e2517-395">-TransferEncoding</span></span>

<span data-ttu-id="e2517-396">Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert.</span><span class="sxs-lookup"><span data-stu-id="e2517-396">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="e2517-397">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="e2517-397">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e2517-398">Mémorisé en bloc</span><span class="sxs-lookup"><span data-stu-id="e2517-398">Chunked</span></span>
- <span data-ttu-id="e2517-399">Compresser</span><span class="sxs-lookup"><span data-stu-id="e2517-399">Compress</span></span>
- <span data-ttu-id="e2517-400">Deflate</span><span class="sxs-lookup"><span data-stu-id="e2517-400">Deflate</span></span>
- <span data-ttu-id="e2517-401">GZip</span><span class="sxs-lookup"><span data-stu-id="e2517-401">GZip</span></span>
- <span data-ttu-id="e2517-402">Identité</span><span class="sxs-lookup"><span data-stu-id="e2517-402">Identity</span></span>

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

### <span data-ttu-id="e2517-403">-URI</span><span class="sxs-lookup"><span data-stu-id="e2517-403">-Uri</span></span>

<span data-ttu-id="e2517-404">Spécifie le Uniform Resource Identifier (URI) de la ressource Internet à laquelle la demande Web est envoyée.</span><span class="sxs-lookup"><span data-stu-id="e2517-404">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="e2517-405">Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.</span><span class="sxs-lookup"><span data-stu-id="e2517-405">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="e2517-406">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e2517-406">This parameter is required.</span></span> <span data-ttu-id="e2517-407">Le nom du paramètre ( **URI** ) est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e2517-407">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="e2517-408">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="e2517-408">-UseBasicParsing</span></span>

<span data-ttu-id="e2517-409">Ce paramètre est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="e2517-409">This parameter has been deprecated.</span></span> <span data-ttu-id="e2517-410">À partir de PowerShell 6.0.0, toutes les requêtes Web utilisent uniquement l’analyse de base.</span><span class="sxs-lookup"><span data-stu-id="e2517-410">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="e2517-411">Ce paramètre est inclus à des fins de compatibilité descendante uniquement et toute utilisation de celui-ci n’a aucun effet sur le fonctionnement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-411">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="e2517-412">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="e2517-412">-UseDefaultCredentials</span></span>

<span data-ttu-id="e2517-413">Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web.</span><span class="sxs-lookup"><span data-stu-id="e2517-413">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="e2517-414">Cela ne peut pas être utilisé avec **l’authentification** ou les **informations d’identification** et peut ne pas être pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e2517-414">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="e2517-415">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="e2517-415">-UserAgent</span></span>

<span data-ttu-id="e2517-416">Spécifie une chaîne d'agent utilisateur pour la demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-416">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="e2517-417">L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` avec de légères variations pour chaque système d’exploitation et plateforme.</span><span class="sxs-lookup"><span data-stu-id="e2517-417">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="e2517-418">Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari.</span><span class="sxs-lookup"><span data-stu-id="e2517-418">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="e2517-419">-Websession</span><span class="sxs-lookup"><span data-stu-id="e2517-419">-WebSession</span></span>

<span data-ttu-id="e2517-420">Spécifie une session de demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-420">Specifies a web request session.</span></span> <span data-ttu-id="e2517-421">Entrez le nom de la variable, y compris le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="e2517-421">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="e2517-422">Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** .</span><span class="sxs-lookup"><span data-stu-id="e2517-422">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="e2517-423">Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.</span><span class="sxs-lookup"><span data-stu-id="e2517-423">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="e2517-424">Les en-têtes associés au contenu, tels que `Content-Type` , seront également remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .</span><span class="sxs-lookup"><span data-stu-id="e2517-424">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="e2517-425">Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente.</span><span class="sxs-lookup"><span data-stu-id="e2517-425">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="e2517-426">Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-426">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="e2517-427">Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.</span><span class="sxs-lookup"><span data-stu-id="e2517-427">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="e2517-428">Pour créer une session de demande Web, entrez un nom de variable, sans signe dollar, dans la valeur du paramètre **SessionVariable** d’une `Invoke-RestMethod` commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-428">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="e2517-429">`Invoke-RestMethod` crée la session et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="e2517-429">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="e2517-430">Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .</span><span class="sxs-lookup"><span data-stu-id="e2517-430">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="e2517-431">Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="e2517-431">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="e2517-432">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2517-432">CommonParameters</span></span>

<span data-ttu-id="e2517-433">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2517-433">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2517-434">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e2517-434">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e2517-435">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e2517-435">INPUTS</span></span>

### <span data-ttu-id="e2517-436">System.Object</span><span class="sxs-lookup"><span data-stu-id="e2517-436">System.Object</span></span>

<span data-ttu-id="e2517-437">Vous pouvez diriger le corps d’une requête Web vers `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="e2517-437">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="e2517-438">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e2517-438">OUTPUTS</span></span>

### <span data-ttu-id="e2517-439">System. Int64, System. String, System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="e2517-439">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="e2517-440">La sortie de l'applet de commande varie selon la mise en forme du contenu qui est récupéré.</span><span class="sxs-lookup"><span data-stu-id="e2517-440">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="e2517-441">PSObject</span><span class="sxs-lookup"><span data-stu-id="e2517-441">PSObject</span></span>

<span data-ttu-id="e2517-442">Si la demande retourne des chaînes JSON, `Invoke-RestMethod` retourne un **PSObject** qui représente les chaînes.</span><span class="sxs-lookup"><span data-stu-id="e2517-442">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="e2517-443">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e2517-443">NOTES</span></span>

<span data-ttu-id="e2517-444">Certaines fonctionnalités peuvent ne pas être disponibles sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e2517-444">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="e2517-445">En raison des modifications apportées à .NET Core 3,1, PowerShell 7,0 et versions ultérieures utilisent la propriété [httpclient. defaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) pour déterminer la configuration du proxy.</span><span class="sxs-lookup"><span data-stu-id="e2517-445">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="e2517-446">La valeur de cette propriété est différente selon votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="e2517-446">The value of this property is different rules depending on your platform:</span></span>

- <span data-ttu-id="e2517-447">**Pour Windows** : lit la configuration du proxy à partir de variables d’environnement ou, si celles-ci ne sont pas définies, à partir des paramètres de proxy de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2517-447">**For Windows** : Reads proxy configuration from environment variables or, if those are not defined, from the user's proxy settings.</span></span>
- <span data-ttu-id="e2517-448">**Pour MacOS** : lit la configuration du proxy à partir des variables d’environnement ou, si celles-ci ne sont pas définies, à partir des paramètres de proxy du système.</span><span class="sxs-lookup"><span data-stu-id="e2517-448">**For macOS** : Reads proxy configuration from environment variables or, if those are not defined, from the system's proxy settings.</span></span>
- <span data-ttu-id="e2517-449">**Pour Linux** : lit la configuration du proxy à partir de variables d’environnement ou, si celles-ci ne sont pas définies, cette propriété Initialise une instance non configurée qui ignore toutes les adresses.</span><span class="sxs-lookup"><span data-stu-id="e2517-449">**For Linux** : Reads proxy configuration from environment variables or, in case those are not defined, this property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="e2517-450">Les variables d’environnement utilisées pour `DefaultProxy` l’initialisation sur des plateformes basées sur Windows et UNIX sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e2517-450">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="e2517-451">` HTTP_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2517-451">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="e2517-452">`HTTPS_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e2517-452">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="e2517-453">`ALL_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP et HTTPs en cas d' `HTTP_PROXY` `HTTPS_PROXY` absence de définition.</span><span class="sxs-lookup"><span data-stu-id="e2517-453">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="e2517-454">`NO_PROXY`: liste séparée par des virgules des noms d’hôtes qui doivent être exclus du proxy.</span><span class="sxs-lookup"><span data-stu-id="e2517-454">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="e2517-455">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e2517-455">RELATED LINKS</span></span>

[<span data-ttu-id="e2517-456">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="e2517-456">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="e2517-457">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="e2517-457">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="e2517-458">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="e2517-458">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

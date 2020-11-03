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
# Invoke-WebRequest

## SYNOPSIS
Obtient le contenu d’une page Web sur Internet.

## SYNTAX

### StandardMethod (par défaut)

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

### StandardMethodNoProxy

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

### CustomMethod

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

### CustomMethodNoProxy

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

## Description

L' `Invoke-WebRequest` applet de commande envoie des requêtes http et HTTPS à une page Web ou à un service Web. Elle analyse la réponse et retourne des collections de liens, d’images et d’autres éléments HTML significatifs.

Cette applet de commande a été introduite dans PowerShell 3,0.

À compter de PowerShell 7,0, `Invoke-WebRequest` prend en charge la configuration de proxy définie par les variables d’environnement. Consultez la section [Remarques](#notes) de cet article.

## EXEMPLES

### Exemple 1 : envoyer une requête Web

Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour envoyer une requête Web au site Bing.com.

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

La première commande émet la demande et enregistre la réponse dans la `$Response` variable.

La deuxième commande obtient tout **InputField** où la propriété **Name** est similaire `"* Value"` . Les résultats filtrés sont dirigés vers `Select-Object` pour sélectionner les propriétés **Name** et **value** .

### Exemple 2 : utiliser un service Web avec état

Cet exemple montre comment utiliser l' `Invoke-WebRequest` applet de commande avec un service Web avec état.

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

Le premier appel à `Invoke-WebRequest` envoie une demande de connexion. La commande spécifie la valeur « session » pour la valeur du paramètre **-SessionVariable** et enregistre le résultat dans la `$LoginResponse` variable. Une fois la commande terminée, la `$LoginResponse` variable contient un `BasicHtmlWebResponseObject` et la `$Session` variable contient un `WebRequestSession` objet. L’utilisateur est alors connecté au site.

L’appel à `$Session` par lui-même affiche l' `WebRequestSession` objet dans la variable.

Le deuxième appel à `Invoke-WebRequest` récupère le profil de l’utilisateur, ce qui nécessite que l’utilisateur soit connecté au site. Les données de session stockées dans la `$Session` variable sont utilisées pour fournir des cookies de session au site créé pendant la connexion. Le résultat est enregistré dans la `$ProfileResponse` variable.

L’appel à `$ProfileResponse` par lui-même affiche le `BasicHtmlWebResponseObject` dans la variable.

### Exemple 3 : obtenir des liens à partir d’une page Web

Cet exemple obtient les liens dans une page Web. Elle utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web. Elle utilise ensuite la propriété **Links** du `BasicHtmlWebResponseObject` qui `Invoke-WebRequest` retourne et la propriété **href** de chaque lien.

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### Exemple 4 : écrit le contenu de la réponse dans un fichier à l’aide de l’encodage défini dans la page demandée.

Cet exemple utilise l' `Invoke-WebRequest` applet de commande pour récupérer le contenu de la page Web d’une page de documentation PowerShell.

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

La première commande récupère la page et enregistre l’objet de réponse dans la `$Response` variable.

La deuxième commande crée un `StreamWriter` à utiliser pour écrire le contenu de la réponse dans un fichier. La propriété **Encoding** de l’objet Response est utilisée pour définir l’encodage du fichier.

Les dernières commandes écrivent la propriété de **contenu** dans le fichier, puis suppriment le `StreamWriter` .

Notez que la propriété **Encoding** a la valeur null si la demande Web ne retourne pas de contenu de texte.

### Exemple 5 : envoyer un fichier multipart/form-data

Cet exemple utilise l' `Invoke-WebRequest` applet de commande upload a file as a `multipart/form-data` submission. Le fichier `c:\document.txt` est soumis en tant que champ `document` de formulaire avec le `Content-Type` de `text/plain` .

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

### Exemple 6 : envoi de données multipart/formulaire simplifié

Certaines API requièrent des `multipart/form-data` envois pour télécharger des fichiers et du contenu mixte. Cet exemple illustre la mise à jour d’un profil utilisateur.

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

Le formulaire de profil requiert les champs suivants : `firstName` ,,,, `lastName` `email` `avatar` `birthday` et `hobbies` . L’API attend une image pour le profil utilisateur pic à fournir dans le `avatar` champ. L’API accepte également l' `hobbies` envoi de plusieurs entrées sous la même forme.

Lors de la création de la `$Form` Hashtable, les noms de clé sont utilisés comme noms de champs de formulaire. Par défaut, les valeurs de la HashTable sont converties en chaînes. Si une valeur **System. IO. FileInfo** est présente, le contenu du fichier est envoyé. Si une collection telle que des tableaux ou des listes est présente, le champ de formulaire est envoyé plusieurs fois.

En utilisant `Get-Item` sur la `avatar` clé, l' `FileInfo` objet est défini comme valeur. Le résultat est que les données d’image de `jdoe.png` sont envoyées.

En fournissant une liste à la `hobbies` clé, le `hobbies` champ est présent dans les envois une fois pour chaque élément de liste.

### Exemple 7 : intercepter les messages non réussis de Invoke-WebRequest

Lorsque `Invoke-WebRequest` rencontre un message http sans succès (404, 500, etc.), il ne retourne aucune sortie et lève une erreur de fin d’opération. Pour intercepter l’erreur et afficher le **statusCode** , vous pouvez l’encadrer dans un `try/catch` bloc.

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

La commande appelle `Invoke-WebRequest` avec un **ErrorAction** **Stop** , qui force `Invoke-WebRequest` à lever une erreur d’arrêt sur les demandes ayant échoué. L’erreur de fin est interceptée par le `catch` bloc qui récupère le **statusCode** de l’objet **exception** .

## PARAMETERS

### -AllowUnencryptedAuthentication

Autorise l’envoi d’informations d’identification et de secrets sur des connexions non chiffrées. Par défaut, le fait de fournir des **informations d’identification** ou toute option **d’authentification** avec un **URI** qui ne commence pas par `https://` génère une erreur et la demande est abandonnée pour empêcher la communication accidentelle de secrets en texte brut sur des connexions non chiffrées. Pour remplacer ce comportement à vos propres risques, fournissez le paramètre **AllowUnencryptedAuthentication** .

> [!WARNING]
> L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée. Elle est fournie uniquement pour la compatibilité avec les systèmes hérités qui ne peuvent pas fournir de connexions chiffrées. Utilisez à vos propres risques.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Authentification

Spécifie le type d’authentification explicite à utiliser pour la requête. La valeur par défaut est **None** (Aucun).
**L’authentification** ne peut pas être utilisée avec **UseDefaultCredentials** .

Options d’authentification disponibles :

- **None** : il s’agit de l’option par défaut lorsque **l’authentification** n’est pas fournie ; aucune authentification explicite n’est utilisée.
- De **base** : requiert des **informations d’identification** . Les informations d’identification sont envoyées dans un en-tête d’authentification de base RFC 7617 au format `base64(user:password)` .
- **Bearer** : requiert un **jeton** . Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni. Il s’agit d’un alias pour **OAuth**
- **OAuth** : requiert un **jeton** . Envoie un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni. Il s’agit d’un alias pour le **porteur**

La spécification de **l’authentification** remplace tous les `Authorization` en-têtes fournis aux **en-têtes** ou inclus dans **websession** .

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Corps

Spécifie le corps de la demande. Le corps est le contenu de la demande qui suit les en-têtes.
Vous pouvez également diriger une valeur de corps vers `Invoke-WebRequest` .

Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.

Lorsque l’entrée est une requête d’extraction et que le corps est un `IDictionary` (en général, une table de hachage), le corps est ajouté à l’URI en tant que paramètres de requête. Pour les autres types de demande (par exemple, la publication), le corps est défini comme valeur du corps de la requête au `name=value` format standard.

Le paramètre **Body** peut également accepter un `System.Net.Http.MultipartFormDataContent` objet. Cela facilite les `multipart/form-data` demandes. Lorsqu’un objet **MultipartFormDataContent** est fourni pour **le corps** , tous les en-têtes associés au contenu fournis aux paramètres **ContentType** , **headers** ou **websession** sont remplacés par les en-têtes de contenu de l’objet **MultipartFormDataContent** . Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Certificat

Spécifie le certificat client utilisé pour une demande Web sécurisée. Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ). Si le certificat n’est pas valide ou ne dispose pas des autorisations suffisantes, la commande échoue.

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

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.

> [!NOTE]
> Cette fonctionnalité n’est actuellement prise en charge que sur les plateformes de système d’exploitation Windows.

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

### -ContentType

Spécifie le type de contenu de la demande web.

Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-WebRequest` définit le type de contenu sur `application/x-www-form-urlencoded` . Dans le cas contraire, le type de contenu n’est pas spécifié dans l’appel.

**ContentType** est substitué lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .

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

### -Credential

Spécifie un compte d'utilisateur qui a l'autorisation d'envoyer la demande. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .

Les **informations d’identification** peuvent être utilisées seules ou conjointement avec certaines options de paramètres **d’authentification** . Lorsqu’il est utilisé seul, il fournit uniquement des informations d’identification au serveur distant si le serveur distant envoie une demande de stimulation d’authentification. Lorsqu’elles sont utilisées avec les options **d’authentification** , les informations d’identification sont envoyées explicitement.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -CustomMethod

Spécifie une méthode personnalisée utilisée pour la demande Web. Cela peut être utilisé si la méthode de demande requise par le point de terminaison n’est pas une option disponible sur la **méthode** . La **méthode** et **CustomMethod** ne peuvent pas être utilisés ensemble.

Cet exemple envoie une `TEST` requête HTTP à l’API :

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -DisableKeepAlive

Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur **false** . Par défaut, **KeepAlive** a la **valeur true** . **KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.

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

### -Formulaire

Convertit un dictionnaire en `multipart/form-data` soumission. Le **formulaire** ne peut pas être utilisé avec le **corps** .
Si **ContentType** est utilisé, il est ignoré.

Les clés du dictionnaire sont utilisées comme noms de champs de formulaire. Par défaut, les valeurs de formulaire sont converties en valeurs de chaîne.

Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis. Le nom du fichier est soumis en tant que propriété **filename** . Le type MIME est défini sur `application/octet-stream` . `Get-Item` peut être utilisé pour simplifier la fourniture de l’objet **System. IO. FileInfo** .

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Si la valeur est un type de collection, tels que des tableaux ou des listes, le champ for est envoyé plusieurs fois.
Les valeurs de la liste sont traitées par défaut en tant que chaînes. Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire est soumis. Les collections imbriquées ne sont pas prises en charge.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

Dans l’exemple ci-dessus `tags` , le champ est fourni trois fois dans le formulaire, une fois pour chaque `Vacation` , `Italy` et `2017` . Le `pictures` champ est également envoyé une fois pour chaque fichier dans le `2017-Italy` dossier. Le contenu binaire des fichiers de ce dossier est soumis en tant que valeurs.

Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.

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

### -En-têtes

Spécifie les en-têtes de la demande web. Entrez une table de hachage ou un dictionnaire.

Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** . Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes **user-agent** ou cookie.

Les en-têtes associés au contenu, tels que, `Content-Type` sont remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .

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

### -INFILE

Obtient le contenu de la demande web à partir d'un fichier. Entrez un chemin d'accès et un nom de fichier. Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.

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

### -MaximumRedirection

Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue. La valeur par défaut est 5. La valeur 0 (zéro) empêche toute redirection.

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

### -MaximumRetryCount

Spécifie le nombre de tentatives de connexion de PowerShell lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu. Consultez également le paramètre **RetryIntervalSec** pour spécifier le nombre de nouvelles tentatives.

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

### -Méthode

Spécifie la méthode utilisée pour la demande web. Les valeurs valides pour ce paramètre sont :

- Default
- DELETE
- Obtenir
- Head
- Fusionner
- Options
- Correctif
- Publier
- Put
- Trace

Le paramètre **CustomMethod** peut être utilisé pour les méthodes de demande non listées ci-dessus.

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

### -NoProxy

Indique que l’applet de commande ne doit pas utiliser de proxy pour atteindre la destination. Lorsque vous avez besoin de contourner le proxy configuré dans l’environnement, utilisez ce commutateur. Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Fichier de journal

Spécifie le fichier de sortie pour lequel cette applet de commande enregistre le corps de la réponse. Entrez un chemin d'accès et un nom de fichier.
Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.

Par défaut, `Invoke-WebRequest` retourne les résultats au pipeline. Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .

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

### -PassThru

Indique que l’applet de commande retourne les résultats, en plus de les écrire dans un fichier. Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.

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

### -PreserveAuthorizationOnRedirect

Indique que l’applet de commande doit conserver l' `Authorization` en-tête, le cas échéant, entre les redirections.

Par défaut, l’applet de commande supprime l' `Authorization` en-tête avant la redirection. La spécification de ce paramètre désactive cette logique pour les cas où l’en-tête doit être envoyé à l’emplacement de redirection.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Proxy

Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.
Entrez l'URI d'un serveur proxy du réseau.

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

### -ProxyCredential

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** . La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , **User@Domain.Com** ou entrez un `PSCredential` objet, tel que celui généré par l' `Get-Credential` applet de commande.

Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande. Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.

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

### -ProxyUseDefaultCredentials

Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .

Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande. Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.

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

### -RESUME

Effectue le meilleur effort pour reprendre le téléchargement d’un fichier partiel. **Resume** requiert un **fichier** out.

**Resume** fonctionne uniquement sur la taille du fichier local et du fichier distant et n’effectue aucune autre validation que le fichier local et le fichier distant sont identiques.

Si la taille du fichier local est inférieure à la taille du fichier distant, l’applet de commande tente de reprendre le téléchargement du fichier et ajoute les octets restants à la fin du fichier.

Si la taille du fichier local est identique à la taille du fichier distant, aucune action n’est effectuée et l’applet de commande suppose que le téléchargement est déjà terminé.

Si la taille du fichier local est supérieure à la taille du fichier distant, le fichier local est remplacé et l’intégralité du fichier distant est retéléchargée. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

Si le serveur distant ne prend pas en charge la reprise du téléchargement, le fichier local est remplacé et l’intégralité du fichier distant est téléchargée à nouveau. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

Si le fichier local n’existe pas, le fichier local est créé et l’intégralité du fichier distant est téléchargée. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

Cette fonctionnalité a été ajoutée dans PowerShell 6.1.0.

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

### -RetryIntervalSec

Spécifie l’intervalle entre les nouvelles tentatives pour la connexion lorsqu’un code d’échec entre 400 et 599, inclus ou 304 est reçu. Consultez également le paramètre **MaximumRetryCount** pour spécifier le nombre de nouvelles tentatives.

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

### -SessionVariable

Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.
Entrez un nom de variable sans le symbole dollar ( `$` ).

Lorsque vous spécifiez une variable de session, `Invoke-WebRequest` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell. Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.

Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante. Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** . PowerShell utilise les données de l’objet session de demande Web lors de l’établissement de la nouvelle connexion. Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** . Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.

Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.

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

### -SkipCertificateCheck

Ignore les vérifications de validation des certificats. Cela comprend toutes les validations, telles que l’expiration, la révocation, l’autorité racine approuvée, etc.

> [!WARNING]
> L’utilisation de ce paramètre n’est pas sécurisée et n’est pas recommandée. Ce commutateur est destiné uniquement à être utilisé sur des hôtes connus à l’aide d’un certificat auto-signé à des fins de test. Utilisez à vos propres risques.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -SkipHeaderValidation

Indique que l’applet de commande doit ajouter des en-têtes à la demande sans validation.

Ce commutateur doit être utilisé pour les sites qui requièrent des valeurs d’en-tête qui ne sont pas conformes aux normes.
Si vous spécifiez ce commutateur, la validation est désactivée pour permettre la désélection de la valeur. Lorsqu’ils sont spécifiés, tous les en-têtes sont ajoutés sans validation.

Ce commutateur désactive la validation pour les valeurs transmises aux paramètres **ContentType** , **headers** et **UserAgent** .

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -SkipHttpErrorCheck

Ce paramètre fait en sorte que l’applet de commande ignore les États d’erreur HTTP et continue à traiter les réponses.
Les réponses d’erreur sont écrites dans le pipeline comme si elles se trouvaient correctement.

Ce paramètre a été introduit dans PowerShell 7.

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

### -SslProtocol

Définit les protocoles SSL/TLS qui sont autorisés pour la demande Web. Par défaut, tous les protocoles SSL/TLS pris en charge par le système sont autorisés. **SslProtocol** permet de limiter à des protocoles spécifiques à des fins de conformité.

**SslProtocol** utilise l’énumération de l’indicateur **WebSslProtocol** . Il est possible de fournir plusieurs protocoles à l’aide de la notation d’indicateur ou de combiner plusieurs options **WebSslProtocol** avec **Bor** , mais le fait de fournir plusieurs protocoles n’est pas pris en charge sur toutes les plateformes.

> [!NOTE]
> Sur les plateformes non-Windows, il n’est pas possible de fournir `'Tls, Tls12'` une option.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -TimeoutSec

Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes. La valeur par défaut, 0, spécifie un délai d'attente indéfini.

Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.

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

### -Jeton

Jeton OAuth ou du porteur à inclure dans la demande. Le **jeton** est requis par certaines options **d’authentification** . Elle ne peut pas être utilisée de manière indépendante.

Le **jeton** prend un `SecureString` contenant le jeton. Pour fournir le jeton manuellement, utilisez les éléments suivants :

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

Ce paramètre a été introduit dans PowerShell 6,0.

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

### -TransferEncoding

Spécifie une valeur pour l'en-tête de réponse HTTP de codage de transfert. Les valeurs valides pour ce paramètre sont :

- Mémorisé en bloc
- Compresser
- Deflate
- GZip
- Identité

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

### -URI

Spécifie le Uniform Resource Identifier (URI) de la ressource Internet à laquelle la demande Web est envoyée. Entrez un URI. Ce paramètre prend en charge uniquement HTTP ou HTTPs.

Ce paramètre est obligatoire. L' **URI** du nom de paramètre est facultatif.

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

### -UseBasicParsing

Ce paramètre est déconseillé. À partir de PowerShell 6.0.0, toutes les requêtes Web utilisent uniquement l’analyse de base. Ce paramètre est inclus à des fins de compatibilité descendante uniquement et n’a aucun effet sur le fonctionnement de l’applet de commande.

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

### -UseDefaultCredentials

Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web. Cela ne peut pas être utilisé avec **l’authentification** ou les **informations d’identification** et peut ne pas être pris en charge sur toutes les plateformes.

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

### -UserAgent

Spécifie une chaîne d'agent utilisateur pour la demande web.

L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` avec de légères variations pour chaque système d’exploitation et plateforme.

Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari.

Par exemple, la commande suivante utilise la chaîne de l’agent utilisateur pour Internet Explorer :

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

### -Websession

Spécifie une session de demande web. Entrez le nom de la variable, y compris le signe dollar ( `$` ).

Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** . Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web. Les en-têtes associés au contenu, tels que `Content-Type` , sont également remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .

Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente. Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

Pour créer une session de demande Web, entrez un nom de variable, sans signe dollar, dans la valeur du paramètre **SessionVariable** d’une `Invoke-WebRequest` commande. `Invoke-WebRequest` crée la session et l’enregistre dans la variable. Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .

Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Object

Vous pouvez diriger le corps d’une requête Web vers `Invoke-WebRequest` .

## SORTIES

### Microsoft. PowerShell. Commands. BasicHtmlWebResponseObject

## REMARQUES

À partir de PowerShell 6.0.0 `Invoke-WebRequest` prend uniquement en charge l’analyse de base.

Pour plus d’informations, consultez [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).

En raison des modifications apportées à .NET Core 3,1, PowerShell 7,0 et versions ultérieures utilisent la propriété [httpclient. defaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) pour déterminer la configuration du proxy.

La valeur de cette propriété est déterminée par votre plateforme :

- **Pour Windows** : lit la configuration du proxy à partir des variables d’environnement. Si ces variables ne sont pas définies, la propriété est dérivée des paramètres de proxy de l’utilisateur.
- **Pour MacOS** : lit la configuration du proxy à partir des variables d’environnement. Si ces variables ne sont pas définies, la propriété est dérivée des paramètres de proxy du système.
- **Pour Linux** : lit la configuration du proxy à partir des variables d’environnement. Si ces variables ne sont pas définies, la propriété Initialise une instance non configurée qui ignore toutes les adresses.

Les variables d’environnement utilisées pour `DefaultProxy` l’initialisation sur des plateformes basées sur Windows et UNIX sont les suivantes :

- ` HTTP_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP.
- `HTTPS_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTPs.
- `ALL_PROXY`: nom d’hôte ou adresse IP du serveur proxy utilisé sur les requêtes HTTP et HTTPs en cas d' `HTTP_PROXY` `HTTPS_PROXY` absence de définition.
- `NO_PROXY`: liste séparée par des virgules des noms d’hôtes qui doivent être exclus du proxy.

## LIENS CONNEXES

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)

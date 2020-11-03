---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 541cceacab7462cc66483a2b75abedcd5c8abb7d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203766"
---
# Invoke-RestMethod

## SYNOPSIS
Envoie une demande HTTP ou HTTPS à un service web RESTful.

## SYNTAX

### StandardMethod (par défaut)

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## Description

L' `Invoke-RestMethod` applet de commande envoie des requêtes http et HTTPS à des services Web REST qui retournent des données structurées de façon riche.

PowerShell met en forme la réponse en fonction du type de données. Pour un flux RSS ou ATOM, PowerShell retourne les nœuds XML Item ou entry. Pour les JavaScript Object Notation (JSON) ou XML, PowerShell convertit, ou désérialise, le contenu en objets.

Cette applet de commande est introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : récupérer le flux RSS PowerShell

Cet exemple utilise l' `Invoke-RestMethod` applet de commande pour récupérer des informations à partir du flux RSS du blog PowerShell. La commande utilise l' `Format-Table` applet de commande pour afficher les valeurs des propriétés **title** et **pubDate** de chaque blog dans une table.

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

### Exemple 2 : exécuter une demande de publication

Dans cet exemple, un utilisateur exécute `Invoke-RestMethod` pour effectuer une demande de publication sur un site Web intranet dans l’organisation de l’utilisateur.

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

Les informations d’identification sont demandées, puis stockées dans `$Cred` et l’URL à laquelle vous accédez est définie dans `$Url` .

La `$Body` variable décrit les critères de recherche, spécifie le volume partagé de cluster comme mode de sortie et spécifie une période de temps pour les données retournées qui démarrent il y a deux jours et se termine il y a un jour. La variable Body spécifie des valeurs pour les paramètres qui s’appliquent à l’API REST particulière avec laquelle `Invoke-RestMethod` communique.

La `Invoke-RestMethod` commande est exécutée avec toutes les variables sur place, en spécifiant un chemin d’accès et un nom de fichier pour le fichier de sortie CSV résultant.

### Exemple 3 : suivre les liens de relation

Certaines API REST prennent en charge la pagination via des liens de relation par [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). Au lieu d’analyser l’en-tête pour obtenir l’URL de la page suivante, vous pouvez faire en sorte que l’applet de commande le fasse pour vous. Cet exemple retourne les deux premières pages de problèmes à partir du référentiel GitHub de PowerShell.

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### Exemple 4 : envoi de données multipart/formulaire simplifié

Certaines API requièrent des `multipart/form-data` envois pour télécharger des fichiers et du contenu mixte. Cet exemple montre comment mettre à jour le profil d’un utilisateur.

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

Le formulaire de profil requiert les champs suivants : `firstName` ,,,, `lastName` `email` `avatar` `birthday` et `hobbies` . L’API attend une image pour le profil utilisateur pic à fournir dans le `avatar` champ. L’API accepte également plusieurs `hobbies` entrées à soumettre sous la même forme.

Lors de la création de la `$Form` Hashtable, les noms de clé sont utilisés comme noms de champs de formulaire. Par défaut, les valeurs de la HashTable sont converties en chaînes. Si une `System.IO.FileInfo` valeur est présente, le contenu du fichier est envoyé. Si une collection telle que des tableaux ou des listes est présente, le champ de formulaire sera envoyé plusieurs fois.

En utilisant `Get-Item` sur la `avatar` clé, l' `FileInfo` objet est défini comme valeur. Le résultat est que les données d’image de `jdoe.png` seront envoyées.

En fournissant une liste à la `hobbies` clé, le `hobbies` champ est présent dans les envois une fois pour chaque élément de liste.

### Exemple 5 : passer plusieurs en-têtes

Les API requièrent souvent des en-têtes passés pour l’authentification ou la validation. Cet exemple montre comment passer plusieurs en-têtes d’un `hash-table` à une API REST.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## Paramètres

### -AllowUnencryptedAuthentication

Autorise l’envoi d’informations d’identification et de secrets sur des connexions non chiffrées. Par défaut, fournir des **informations d’identification** ou une option **d’authentification** avec un **URI** qui ne commence pas par génère `https://` une erreur et la demande est abandonnée pour empêcher la communication accidentelle de secrets en texte brut sur des connexions non chiffrées. Pour remplacer ce comportement à vos propres risques, fournissez le paramètre **AllowUnencryptedAuthentication** .

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

- **None** : il s’agit de l’option par défaut lorsque **l’authentification** n’est pas fournie. Aucune authentification explicite n’est utilisée.
- De **base** : requiert des **informations d’identification** . Les informations d’identification seront utilisées pour envoyer un en-tête d’authentification de base RFC 7617 au `Authorization: Basic` format `base64(user:password)` .
- **Bearer** : requiert un **jeton** . Enverra `Authorization: Bearer` l’en-tête RFC 6750 avec le jeton fourni. Il s’agit d’un alias pour **OAuth**
- **OAuth** : requiert un **jeton** . Enverra un `Authorization: Bearer` en-tête RFC 6750 avec le jeton fourni. Il s’agit d’un alias pour le **porteur**

La spécification de **l’authentification** remplacera tous les `Authorization` en-têtes fournis aux **en-têtes** ou inclus dans **websession** .

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
Vous pouvez également diriger une valeur de corps vers `Invoke-RestMethod` .

Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.

Lorsque l’entrée est une requête d’extraction et que le corps est un `IDictionary` (en général, une table de hachage), le corps est ajouté à la Uniform Resource Identifier (Uri) en tant que paramètres de requête. Pour d'autres types de demandes (par exemple POST), le corps est défini comme valeur du corps de la demande au format nom standard=valeur.

Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un autre `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.

Le paramètre **Body** peut également accepter un objet **System .net. http. MultipartFormDataContent** . Cela facilitera les `multipart/form-data` demandes. Lorsqu’un **objet MultipartFormDataContent** est fourni pour **le corps** , tous les en-têtes associés au contenu fournis aux paramètres **ContentType** , **headers** ou **websession** sont remplacés par les en-têtes de contenu de l' `MultipartFormDataContent` objet. Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

Spécifie le certificat client utilisé pour une demande web sécurisée. Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

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

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

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

Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-RestMethod` définit le type de contenu sur `application/x-www-form-urlencoded` . Dans le cas contraire, le type de contenu n’est pas spécifié dans l’appel.

**ContentType** est substitué lorsqu’un `MultipartFormDataContent` objet est fourni pour le **corps** .

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

Les **informations d’identification** peuvent être utilisées seules ou conjointement avec certaines options de paramètres **d’authentification** . Lorsqu’il est utilisé seul, il fournit uniquement des informations d’identification au serveur distant si le serveur distant envoie une demande de stimulation d’authentification. Lorsqu’elles sont utilisées avec les options **d’authentification** , les informations d’identification sont envoyées de manière explicite.

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

Spécifie la méthode personnalisée utilisée pour la demande Web. Cela peut être utilisé avec la méthode de demande requise par le point de terminaison n’est pas une option disponible sur la **méthode** . Les **méthodes** et **CustomMethod** ne peuvent pas être utilisées ensemble.

Exemple :

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Une `TEST` requête HTTP est alors envoyée à l’API.

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

Indique que l’applet de commande définit la valeur **KeepAlive** dans l’en-tête http sur false. Par défaut, **KeepAlive** a la valeur True. **KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.

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

### -FollowRelLink

Indique que l’applet de commande doit suivre les liens de relation.

Certaines API REST prennent en charge la pagination via des liens de relation par [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). Au lieu d’analyser l’en-tête pour obtenir l’URL de la page suivante, vous pouvez faire en sorte que l’applet de commande le fasse pour vous. Pour définir le nombre de fois où les liens de relation doivent être suivis, utilisez le paramètre **MaximumFollowRelLink** .

Lors de l’utilisation de ce commutateur, l’applet de commande retourne une collection de pages de résultats. Chaque page de résultats peut contenir plusieurs éléments de résultat.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -Formulaire

Convertit un dictionnaire en `multipart/form-data` soumission. Le **formulaire** ne peut pas être utilisé avec le **corps** .
Si **ContentType** sera ignoré.

Les clés du dictionnaire seront utilisées comme noms de champs de formulaire. Par défaut, les valeurs de formulaire sont converties en valeurs de chaîne.

Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire sera envoyé.
Le nom du fichier sera envoyé en tant que `filename` . Le MIME sera défini sur `application/octet-stream` . `Get-Item` peut être utilisé pour simplifier la fourniture de l’objet **System. IO. FileInfo** .

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Si la valeur est un type de collection, tel qu’un tableau ou une liste, le champ for est envoyé plusieurs fois. Les valeurs de la liste sont traitées par défaut en tant que chaînes. Si la valeur est un objet **System. IO. FileInfo** , le contenu du fichier binaire sera envoyé. Les collections imbriquées ne sont pas prises en charge.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

Dans l’exemple ci-dessus, le `tags` champ sera fourni trois fois dans le formulaire, une fois pour chaque `Vacation` , `Italy` et `2017` . Le `pictures` champ est également envoyé une fois pour chaque fichier dans le `2017-Italy` dossier. Le contenu binaire des fichiers de ce dossier sera soumis en tant que valeurs.

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

Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** . Vous ne pouvez pas utiliser ce paramètre pour spécifier des `User-Agent` en-têtes ou des cookies.

Les en-têtes associés au contenu, tels que, `Content-Type` sont remplacés lorsqu’un `MultipartFormDataContent` objet est fourni pour le **corps** .

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

Obtient le contenu de la demande web à partir d'un fichier.

Entrez un chemin d'accès et un nom de fichier. Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.

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

### -MaximumFollowRelLink

Spécifie le nombre de fois où les liens de relation doivent être suivis si **FollowRelLink** est utilisé. Une valeur inférieure peut être nécessaire si l’API REST est limitée en raison d’un trop grand nombre de requêtes. La valeur par défaut est `[Int32]::MaxValue`. La valeur 0 (zéro) empêche les liens de relation suivants.

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

### -MaximumRedirection

Spécifie le nombre de fois que PowerShell redirige une connexion vers un autre Uniform Resource Identifier (URI) avant que la connexion échoue. La valeur par défaut est 5. La valeur 0 (zéro) empêche toute redirection.

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

Indique que l’applet de commande n’utilisera pas de proxy pour atteindre la destination.

Si vous avez besoin de contourner le proxy configuré dans Internet Explorer, ou un proxy spécifié dans l’environnement, utilisez ce commutateur.

Ce paramètre a été introduit dans PowerShell 6,0.

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

Enregistre le corps de la réponse dans le fichier de sortie spécifié. Entrez un chemin d'accès et un nom de fichier. Si vous omettez le chemin d'accès, la valeur par défaut est l'emplacement actuel.

Par défaut, `Invoke-RestMethod` retourne les résultats au pipeline. Pour envoyer les résultats à un fichier et au pipeline, utilisez le paramètre **Passthru** .

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

Retourne les résultats, en plus de les écrire dans un fichier. Ce paramètre n'est valide que quand le paramètre **OutFile** est également utilisé dans la commande.

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

Utilise un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet. Entrez le Uniform Resource Identifier (URI) d’un serveur proxy réseau.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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
Default value: None
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

### -ResponseHeadersVariable

Crée un dictionnaire d’en-têtes de réponse et l’enregistre dans la valeur de la variable spécifiée. Les clés du dictionnaire contiendront les noms de champs de l’en-tête de réponse renvoyé par le serveur Web et les valeurs seront les valeurs de champ respectives.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

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

### -RESUME

Effectue le meilleur effort pour reprendre le téléchargement d’un fichier partiel. Le paramètre **Resume** requiert le paramètre de **fichier** out.

**Resume** fonctionne uniquement sur la taille du fichier local et du fichier distant et n’effectue aucune autre validation que le fichier local et le fichier distant sont identiques.

Si la taille du fichier local est inférieure à la taille du fichier distant, l’applet de commande tente de reprendre le téléchargement du fichier et ajoute les octets restants à la fin du fichier.

Si la taille du fichier local est identique à la taille du fichier distant, aucune action n’est effectuée et l’applet de commande suppose que le téléchargement est déjà terminé.

Si la taille du fichier local est supérieure à la taille du fichier distant, le fichier local est remplacé et l’intégralité du fichier distant est retéléchargée. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

Si le serveur distant ne prend pas en charge la reprise du téléchargement, le fichier local sera remplacé et l’intégralité du fichier distant sera à nouveau téléchargée. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

Si le fichier local n’existe pas, le fichier local est créé et l’intégralité du fichier distant est entièrement téléchargée. Ce comportement est identique à l’utilisation de sort **file** sans **Resume** .

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

Lorsque vous spécifiez une variable de session, `Invoke-RestMethod` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell. Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.

Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente. Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

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

Ignore les vérifications de validation de certificat qui incluent toutes les validations, telles que l’expiration, la révocation, l’autorité racine de confiance, etc.

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

Cette opération désactive la validation des valeurs transmises aux paramètres **ContentType** , **headers** et **UserAgent** .

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

### -SslProtocol

Définit les protocoles SSL/TLS qui sont autorisés pour la demande Web. Par défaut, tous les protocoles SSL/TLS pris en charge par le système sont autorisés. **SslProtocol** permet de limiter à des protocoles spécifiques à des fins de conformité.

**SslProtocol** utilise l' `WebSslProtocol` énumération d’indicateur. Il est possible de fournir plus d’un protocole à l’aide de la notation d’indicateur ou de combiner plusieurs `WebSslProtocol` options avec `-bor` , mais le fait de fournir plusieurs protocoles n’est pas pris en charge sur toutes les plateformes.

> [!NOTE]
> Sur les plateformes non-Windows, il n’est pas possible de fournir `'Tls, Tls12'` une option.

Cette fonctionnalité a été ajoutée dans PowerShell 6.0.0.

```yaml
Type: WebSslProtocol
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
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Jeton

Jeton OAuth ou du porteur à inclure dans la demande. Le **jeton** est requis par certaines options **d’authentification** . Elle ne peut pas être utilisée de manière indépendante.

Le **jeton** accepte un `SecureString` qui contient le jeton. Pour fournir le jeton, utilisez manuellement les éléments suivants :

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: SecureString
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
Type: String
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

Spécifie le Uniform Resource Identifier (URI) de la ressource Internet à laquelle la demande Web est envoyée. Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.

Ce paramètre est obligatoire. Le nom du paramètre ( **URI** ) est facultatif.

```yaml
Type: Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseBasicParsing

Ce paramètre est déconseillé. À partir de PowerShell 6.0.0, toutes les requêtes Web utilisent uniquement l’analyse de base. Ce paramètre est inclus à des fins de compatibilité descendante uniquement et toute utilisation de celui-ci n’a aucun effet sur le fonctionnement de l’applet de commande.

```yaml
Type: SwitchParameter
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
Type: SwitchParameter
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

```yaml
Type: String
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

Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** . Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web. Les en-têtes associés au contenu, tels que `Content-Type` , seront également remplacés lorsqu’un objet **MultipartFormDataContent** est fourni pour le **corps** .

Contrairement à une session à distance, la session de demande Web n’est pas une connexion permanente. Il s’agit d’un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d’identification, la valeur maximale de la redirection et la chaîne de l’agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

Pour créer une session de demande Web, entrez un nom de variable, sans signe dollar, dans la valeur du paramètre **SessionVariable** d’une `Invoke-RestMethod` commande. `Invoke-RestMethod` crée la session et l’enregistre dans la variable. Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .

Vous ne pouvez pas utiliser les paramètres **SessionVariable** et **websession** dans la même commande.

```yaml
Type: WebRequestSession
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

Vous pouvez diriger le corps d’une requête Web vers `Invoke-RestMethod` .

## SORTIES

### System. Int64, System. String, System.Xml.Xmldocument

La sortie de l'applet de commande varie selon la mise en forme du contenu qui est récupéré.

### PSObject

Si la demande retourne des chaînes JSON, `Invoke-RestMethod` retourne un **PSObject** qui représente les chaînes.

## REMARQUES

Certaines fonctionnalités peuvent ne pas être disponibles sur toutes les plateformes.

Pour plus d’informations sur la façon dont .NET fournit les services proxy à PowerShell, consultez [accès à Internet via un proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).

## LIENS CONNEXES

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

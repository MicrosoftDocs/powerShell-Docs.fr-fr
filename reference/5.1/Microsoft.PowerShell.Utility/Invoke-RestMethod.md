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
# Invoke-RestMethod

## Synopsis
Envoie une demande HTTP ou HTTPS à un service web RESTful.

## Syntaxe

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## Description

L' `Invoke-RestMethod` applet de commande envoie des requêtes http et HTTPS à des services Web REST qui retournent des données structurées.

Windows PowerShell met en forme la réponse en fonction du type de données. Pour un flux RSS ou ATOM, Windows PowerShell retourne les nœuds XML Item ou Entry. Pour JSON (JavaScript Objet Notation) ou XML, Windows PowerShell convertit (ou désérialise) le contenu en objets.

Cette applet de commande est introduite dans Windows PowerShell 3.0.

> [!NOTE]
> Par défaut, le code de script de la page Web peut être exécuté lorsque la page est analysée pour remplir la `ParsedHtml` propriété. Utilisez le commutateur **UseBasicParsing** pour supprimer ce paramètre.

## Exemples

### Exemple 1 : récupérer le flux RSS PowerShell

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

Cette commande utilise la `Invoke-RestMethod` cmdlet pour récupérer des informations à partir du flux RSS du blog PowerShell. La commande utilise l' `Format-Table` applet de commande pour afficher les valeurs des propriétés **title** et **pubDate** de chaque blog dans une table.

### Exemple 2

Dans l’exemple suivant, un utilisateur exécute `Invoke-RestMethod` pour effectuer une demande de publication sur un site Web intranet dans l’organisation de l’utilisateur.

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

### Exemple 3 : passer plusieurs en-têtes

Cet exemple montre comment passer plusieurs en-têtes de à partir d’un `hash-table` à une API REST.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

Les API requièrent souvent des en-têtes passés pour l’authentification, la validation, etc.

### Exemple 3 : envoi de données de formulaire

Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un autre `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.

Par exemple :

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## Paramètres

### -Corps

Spécifie le corps de la demande. Le corps est le contenu de la demande qui suit les en-têtes.
Vous pouvez également diriger une valeur de corps vers `Invoke-RestMethod` .

Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.

Quand l'entrée est une demande GET et que le corps est un IDictionary (en général, une table de hachage), le corps est ajouté à l'URI en tant que paramètres de requête. Pour d'autres types de demandes (par exemple POST), le corps est défini comme valeur du corps de la demande au format nom standard=valeur.

> [!WARNING]
> La sortie détaillée d’un corps de publication se termine par `with -1-byte payload` , même si la taille du corps est à la fois connue et envoyée dans l' `Content-Length` en-tête http.

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

Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat ( `Cert:` ). Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.

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

Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur Windows PowerShell ( `Cert:` ).

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

Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-RestMethod` définit le type de contenu sur « application/x-www-form-urlencoded ». Sinon, le type de contenu n'est pas spécifié dans l'appel.

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

### -DisableKeepAlive

Affecte la valeur False à **KeepAlive** dans l'en-tête HTTP. Par défaut, **KeepAlive** a la valeur True.
**KeepAlive** établit une connexion permanente au serveur pour faciliter les demandes suivantes.

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

### -En-têtes

Spécifie les en-têtes de la demande web. Entrez une table de hachage ou un dictionnaire.

Pour définir des en-têtes UserAgent, utilisez le paramètre **UserAgent** . Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes UserAgent ou de cookie.

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

### -MaximumRedirection

Détermine combien de fois Windows PowerShell redirige une connexion vers un autre URI (Uniform Resource Identifier) avant que la connexion échoue. La valeur par défaut est 5. La valeur 0 (zéro) empêche toute redirection.

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

### -Proxy

Utilise un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet. Entrez l'URI d'un serveur proxy du réseau.

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

### -ProxyCredential

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** . La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.

Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande. Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.

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

### -ProxyUseDefaultCredentials

Utilise les informations d'identification de l'utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **Proxy** .

Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande. Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.

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

### -SessionVariable

Crée une session de demande web et l'enregistre dans la valeur de la variable spécifiée. Entrez un nom de variable sans le symbole dollar ( `$` ).

Lorsque vous spécifiez une variable de session, `Invoke-RestMethod` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell. Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.

Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante. Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

Pour utiliser la session de demande web dans les demandes web suivantes, spécifiez la variable de session dans la valeur du paramètre **WebSession** . Windows PowerShell utilise les données de l'objet de session de demande web au moment de l'établissement de la nouvelle connexion. Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** . Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.

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

### -TimeoutSec

Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes. La valeur par défaut, 0, spécifie un délai d'attente indéfini.

Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à TimeoutSec une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une WebException soit levée, et votre demande expire.

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

Spécifie l'URI (Uniform Resource Identifier) de la ressource Internet à laquelle la demande web est envoyée. Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.

Ce paramètre est obligatoire. Le nom du paramètre ( **URI** ) est facultatif.

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

Indique que l’applet de commande utilise l’analyse de base. L’applet de commande retourne le code HTML brut dans un objet **String** .

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

Utilise les informations d'identification de l'utilisateur actuel pour envoyer la demande web.

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

L'agent utilisateur par défaut est semblable à « Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0 » avec de légères variantes selon le système d'exploitation et la plateforme.

Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands) , par exemple chrome, Firefox, Internet Explorer, Opera et Safari.

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

Pour remplacer une valeur dans la session de demande web, utilisez un paramètre d'applet de commande, comme **UserAgent** ou **Credential** . Les valeurs de paramètre sont prioritaires sur les valeurs de la session de demande web.

Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante. Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

Pour créer une session de demande Web, entrez un nom de variable (sans signe dollar) dans la valeur du paramètre **SessionVariable** d’une `Invoke-RestMethod` commande. `Invoke-RestMethod` crée la session et l’enregistre dans la variable. Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .

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

## Entrées

### System.Object

Vous pouvez diriger le corps d’une requête Web vers `Invoke-RestMethod` .

## Sorties

### System.Xml.Xmldocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System. String

La sortie de l'applet de commande varie selon la mise en forme du contenu qui est récupéré.

### PSObject

Si la demande retourne des chaînes JSON, `Invoke-RestMethod` retourne un PSObject qui représente les chaînes.

## Notes

## Liens associés

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

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
# Invoke-WebRequest

## SYNOPSIS
Obtient le contenu d'une page web sur Internet.

## SYNTAX

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## Description

L' `Invoke-WebRequest` applet de commande envoie des demandes http, HTTPS, FTP et file à une page Web ou à un service Web.
Elle analyse la réponse et retourne des collections de formulaires, des liens, des images et d'autres éléments HTML significatifs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

> [!NOTE]
> Par défaut, le code de script de la page Web peut être exécuté lorsque la page est analysée pour remplir la `ParsedHtml` propriété.
> Utilisez le `-UseBasicParsing` commutateur pour supprimer ce.

## EXEMPLES

### Exemple 1 : envoyer une requête Web

Cette commande utilise la `Invoke-WebRequest` cmdlet pour envoyer une requête Web au site Bing.com.

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

La première commande émet la demande et enregistre la réponse dans la `$R` variable.

La deuxième commande filtre les objets dans la propriété des **allèles** où la propriété **Name** est semblable à « * value » et le **tagname** à « Input ». Les résultats filtrés sont dirigés vers `Select-Object` pour sélectionner les propriétés **Name** et **value** .

### Exemple 2 : utiliser un service Web avec état

Cet exemple montre comment utiliser l' `Invoke-WebRequest` applet de commande avec un service Web avec état, tel que Facebook.

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

La première commande utilise l' `Invoke-WebRequest` applet de commande pour envoyer une demande de connexion. La commande spécifie la valeur « FB » pour la valeur du paramètre **SessionVariable** et enregistre le résultat dans la `$R` variable. Une fois la commande terminée, la `$R` variable contient un **HtmlWebResponseObject** et la `$FB` variable contient un objet **WebRequestSession** .

Une fois que l’applet de commande `Invoke-WebRequest` se connecte à Facebook, la propriété **StatusDescription** de l’objet de réponse Web dans la `$R` variable indique que l’utilisateur s’est connecté avec succès.

### Exemple 3 : obtenir des liens à partir d’une page Web

Cette commande obtient les liens dans une page web.

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

L' `Invoke-WebRequest` applet de commande obtient le contenu de la page Web. La propriété **Links** du **HtmlWebResponseObject** retourné est ensuite utilisée pour afficher la propriété **href** de chaque lien.

### Exemple 4 : intercepter les messages non réussis de Invoke-WebRequest

Lorsque `Invoke-WebRequest` rencontre un message http sans succès (404, 500, etc.), il ne retourne aucune sortie et lève une erreur de fin d’opération. Pour intercepter l’erreur et afficher le **statusCode** , vous pouvez l’encadrer dans un `try/catch` bloc. L’exemple suivant montre comment effectuer cette procédure.

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

La première commande appelle `Invoke-WebRequest` avec un **ErrorAction** **Stop** , qui force `Invoke-WebRequest` à lever une erreur d’arrêt sur les demandes ayant échoué. L’erreur de fin est interceptée par le `catch` bloc qui récupère le **statusCode** de l’objet **exception** .

## PARAMETERS

### -Corps

Spécifie le corps de la demande.
Le corps est le contenu de la demande qui suit les en-têtes.
Vous pouvez également diriger une valeur de corps vers `Invoke-WebRequest` .

Le paramètre **Body** peut être utilisé pour spécifier une liste de paramètres de demande ou le contenu de la réponse.

Lorsque l’entrée est une requête d’extraction et que le corps est un **IDictionary** (en général, une table de hachage), le corps est ajouté à l’URI en tant que paramètres de requête. Pour les autres requêtes d’extraction, le corps est défini comme valeur du corps de la requête au `name=value` format standard.

Lorsque le corps est un formulaire ou qu’il s’agit de la sortie d’un `Invoke-WebRequest` appel, PowerShell définit le contenu de la demande sur les champs du formulaire.
Par exemple :

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- ou -

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

### -Certificat

Spécifie le certificat client utilisé pour une demande web sécurisée. Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de **certificat** ( `Cert:` ). Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.

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

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'envoyer la demande. Entrez l’empreinte numérique du certificat. Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.

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

Si ce paramètre est omis et que la méthode de demande est publication, `Invoke-WebRequest` définit le type de contenu sur application/x-www-form-urlencoded. Sinon, le type de contenu n'est pas spécifié dans l'appel.

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

### -En-têtes

Spécifie les en-têtes de la demande web. Entrez une table de hachage ou un dictionnaire.

Pour définir des en-têtes **UserAgent** , utilisez le paramètre **UserAgent** . Vous ne pouvez pas utiliser ce paramètre pour spécifier des en-têtes **UserAgent** ou de cookie.

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

### -Proxy

Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.
Entrez l'URI d'un serveur proxy du réseau.

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

Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .

Ce paramètre est valide uniquement lorsque le paramètre **proxy** est également utilisé dans la commande. Vous ne pouvez pas utiliser les paramètres **ProxyCredential** et **ProxyUseDefaultCredentials** dans la même commande.

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

### -ProxyUseDefaultCredentials

Indique que l’applet de commande utilise les informations d’identification de l’utilisateur actuel pour accéder au serveur proxy spécifié par le paramètre **proxy** .

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

Spécifie une variable pour laquelle cette applet de commande crée une session de demande Web et l’enregistre dans la valeur.
Entrez un nom de variable sans le symbole dollar ( `$` ).

Lorsque vous spécifiez une variable de session, `Invoke-WebRequest` crée un objet de session de demande Web et l’assigne à une variable avec le nom spécifié dans votre session PowerShell. Vous pouvez utiliser la variable dans votre session dès que la commande est terminée.

Contrairement à une session à distance, la session de demande web n'est pas une connexion persistante. Il s'agit d'un objet qui contient des informations sur la connexion et la demande, notamment les cookies, les informations d'identification, la valeur maximale de la redirection et la chaîne d'agent utilisateur. Vous pouvez l'utiliser pour partager l'état et les données entre les demandes web.

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

### -TimeoutSec

Spécifie la durée pendant laquelle la demande peut être en attente avant d’expirer. Entrez une valeur en secondes. La valeur par défaut, 0, spécifie un délai d'attente indéfini.

Le retour ou l’expiration d’une requête DNS (Domain Name System) peut prendre jusqu’à 15 secondes. Si votre requête contient un nom d’hôte qui requiert une résolution, et que vous affectez à **TimeoutSec** une valeur supérieure à zéro, mais inférieure à 15 secondes, elle peut prendre 15 secondes ou plus avant qu’une **WebException** soit levée, et votre demande expire.

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

Spécifie l'URI (Uniform Resource Identifier) de la ressource Internet à laquelle la demande web est envoyée. Entrez un URI. Ce paramètre prend en charge les valeurs HTTP, HTTPS, FTP et FILE.

Ce paramètre est obligatoire.

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

Indique que l’applet de commande utilise l’objet de réponse pour le contenu HTML sans analyse du modèle DOM (Document Object Model). Ce paramètre est obligatoire quand Internet Explorer n'est pas installé sur les ordinateurs, comme sur une installation minimale du serveur d'un système d'exploitation Windows Server.

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

Indique que le cmdet utilise les informations d’identification de l’utilisateur actuel pour envoyer la demande Web.

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

Spécifie une chaîne d'agent utilisateur pour la demande web. L’agent utilisateur par défaut est semblable à `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` avec de légères variations pour chaque système d’exploitation et plateforme.

Pour tester un site Web avec la chaîne de l’agent utilisateur standard qui est utilisée par la plupart des navigateurs Internet, utilisez les propriétés de la classe [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) , par exemple chrome, Firefox, InternetExplorer, Opera et Safari. Par exemple, la commande suivante utilise la chaîne de l’agent utilisateur pour Internet Explorer

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

Pour créer une session de demande Web, entrez un nom de variable (sans signe dollar) dans la valeur du paramètre **SessionVariable** d’une `Invoke-WebRequest` commande. `Invoke-WebRequest` crée la session et l’enregistre dans la variable. Dans les commandes suivantes, utilisez la variable comme valeur du paramètre **WebSession** .

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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Object

Vous pouvez diriger le corps d’une requête Web vers `Invoke-WebRequest` .

## SORTIES

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## REMARQUES

## LIENS CONNEXES

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)

---
description: Certificat
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Certificate
ms.openlocfilehash: 78536024e8e953a70485a7d950b187ba9a3fc405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599157"
---
# <a name="certificate-provider"></a>Fournisseur Certificate

## <a name="provider-name"></a>Nom du fournisseur

Certificat

## <a name="drives"></a>Lecteurs

`Cert:`

## <a name="capabilities"></a>Fonctions

**ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l’accès aux magasins de certificats X. 509 et aux certificats dans PowerShell.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur de **certificats** PowerShell vous permet d’acquérir, d’ajouter, de modifier, d’effacer et de supprimer des certificats et des magasins de certificats dans PowerShell.

Le lecteur de **certificat** est un espace de noms hiérarchique contenant les magasins de certificats et les certificats sur votre ordinateur.

Le fournisseur de **certificats** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Le lecteur de certificat expose les types suivants.

- Emplacements de stockage (Microsoft. PowerShell. Commands. X509StoreLocation), qui sont des conteneurs de haut niveau qui regroupent les certificats pour l’utilisateur actuel et pour tous les utilisateurs. Chaque système a un emplacement des magasins de l'utilisateur actuel (CurrentUser) et de l'ordinateur local (LocalMachine) (tous les utilisateurs).

- Les magasins de certificats (System. Security. Cryptography. X509Certificates. X509Store), qui sont des magasins physiques dans lesquels les certificats sont enregistrés et gérés.

- Les certificats **System. Security. Cryptography. X509Certificates. X509Certificate2** x. 509, chacun représentant un certificat X. 509 sur l’ordinateur.
  Les certificats sont identifiés par leurs empreintes numériques.

## <a name="navigating-the-certificate-drive"></a>Navigation dans le lecteur de certificat

Le fournisseur de **certificats** expose l’espace de noms de certificat en tant que `Cert:` lecteur dans PowerShell. Cette commande utilise la `Set-Location` commande pour changer l’emplacement actuel du magasin de certificats racine dans l’emplacement de magasin LocalMachine. Utilisez une barre oblique inverse ( \\ ) ou une barre oblique (/) pour indiquer un niveau du `Cert:` lecteur.

```powershell
Set-Location Cert:
```

Vous pouvez également utiliser le fournisseur de certificats à partir de n’importe quel autre lecteur PowerShell. Pour référencer un alias à partir d’un autre emplacement, utilisez le `Cert:` nom du lecteur dans le chemin d’accès.

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).
> et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-contents-of-the-cert-drive"></a>Affichage du contenu du lecteur Cert :

Cette commande utilise l' `Get-ChildItem` applet de commande pour afficher les magasins de certificats dans l’emplacement du magasin de certificats CurrentUser.

Si vous n’êtes pas dans le `Cert:` lecteur, utilisez un chemin d’accès absolu.

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>Affichage des propriétés de certificat dans le lecteur Cert :

Cet exemple obtient un certificat avec `Get-Item` et le stocke dans une variable.
L’exemple montre les nouvelles propriétés de script de certificat (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) à l’aide de `Select-Object` .

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>Rechercher tous les certificats de coconception

Cette commande utilise les paramètres **CodeSigningCert** et **recurse** de l' `Get-ChildItem` applet de commande pour obtenir tous les certificats sur l’ordinateur qui disposent de l’autorité de signature de code.

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>Rechercher les certificats expirés

Cette commande utilise le paramètre **ExpiringInDays** de l' `Get-ChildItem` applet de commande pour récupérer les certificats qui expirent dans les 30 prochains jours.

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>Rechercher des certificats SSL de serveur

Cette commande utilise le paramètre **SSLServerAuthentication** de l' `Get-ChildItem` applet de commande pour récupérer tous les certificats SSL du serveur dans les magasins My et Webhosting.

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>Rechercher les certificats expirés sur les ordinateurs distants

Cette commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-ChildItem` commande sur les ordinateurs Srv01 et Srv02. La valeur zéro (0) dans le paramètre **ExpiringInDays** obtient les certificats sur les ordinateurs Srv01 et Srv02 qui ont expiré.

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>Combinaison de filtres pour rechercher un ensemble spécifique de certificats

Cette commande obtient tous les certificats de l’emplacement de magasin LocalMachine qui ont les attributs suivants :

- « Fabrikam » dans leur nom DNS
- « Authentification du client » dans leur utilisation améliorée de la EKU
- valeur de `$true` pour la propriété **SendAsTrustedIssuer**
- n’expirent pas dans les 30 prochains jours.

La propriété **notAfter** stocke la date d’expiration du certificat.

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>Ouverture du composant logiciel enfichable MMC Certificats

L' `Invoke-Item` applet de commande utilise l’application par défaut pour ouvrir un chemin d’accès que vous spécifiez. Pour les certificats, l’application par défaut est le composant logiciel enfichable Certificats de la console MMC.

Cette commande ouvre le composant logiciel enfichable MMC Certificats pour gérer le certificat spécifié.

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>Copie des certificats

La copie de certificats n’est pas prise en charge par le fournisseur de **certificats** . Lorsque vous tentez de copier un certificat, vous voyez cette erreur.

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>Déplacement de certificats

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>Déplacer tous les certificats d’authentification de serveur SSL vers le magasin d’hébergement.

Cette commande utilise l' `Move-Item` applet de commande pour déplacer un certificat du magasin My vers le magasin d’hébergement.

`Move-Item` ne déplace pas les magasins de certificats et les certificats ne sont pas déplacés vers un autre emplacement de stockage, par exemple le déplacement d’un certificat de LocalMachine à CurrentUser. L' `Move-Item` applet de commande déplace les certificats, mais ne déplace pas les clés privées.

Cette commande utilise le paramètre **SSLServerAuthentication** de l' `Get-ChildItem` applet de commande pour récupérer les certificats d’authentification de serveur SSL dans le magasin de certificats My.

Les certificats retournés sont dirigés vers l’applet de commande `Move-Item` , qui déplace les certificats vers le magasin d’hébergement.

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>Suppression de certificats et de clés privées

L' `Remove-Item` applet de commande supprime les certificats que vous spécifiez. Le `-DeleteKey` paramètre Dynamic supprime la clé privée.

### <a name="delete-a-certificate-from-the-ca-store"></a>Supprimer un certificat du magasin de l’autorité de certification

Cette commande supprime un certificat dans le magasin de certificats d'autorité de certification, mais laisse la clé privée associée intacte.

Dans le `Cert:` lecteur, l' `Remove-Item` applet de commande prend en charge uniquement les paramètres **DeleteKey**, **path**, **WhatIf** et **Confirm** . Tous les autres paramètres sont ignorés.

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>Supprimer un certificat à l’aide de caractères génériques dans le nom DNS

Cette commande supprime tous les certificats qui ont un nom DNS contenant « Fabrikam ». Elle utilise le paramètre **dNSName** de l' `Get-ChildItem` applet de commande pour récupérer les certificats et l' `Remove-Item` applet de commande pour les supprimer.

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>Supprimer des clés privées d’un ordinateur distant

Cette série de commandes active la délégation, puis supprime le certificat et la clé privée associée sur un ordinateur distant. Pour supprimer une clé privée sur un ordinateur distant, vous devez utiliser des informations d'identification déléguées.

Utilisez l' `Enable-WSManCredSSP` applet de commande pour activer l’authentification CredSSP (Credential Security Service Provider) sur un client sur l’ordinateur distant S1.
CredSSP autorise l'authentification déléguée.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

Utilisez l' `Connect-WSMan` applet de commande pour connecter l’ordinateur S1 au service WinRM sur l’ordinateur local. Lorsque cette commande est terminée, l’ordinateur S1 apparaît sur le `WSMan:` lecteur local dans PowerShell.

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

À présent, vous pouvez utiliser l’applet de commande Set-Item dans le lecteur WSMan : pour activer l’attribut CredSSP pour le service WinRM.

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

Démarrez une session à distance sur l’ordinateur S1 à l’aide de l’applet de commande `New-PSSession` et spécifiez l’authentification CredSSP. Enregistre la session dans la `$s` variable.

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

Enfin, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Remove-Item` commande dans la session dans la `$s` variable. La `Remove-Item` commande utilise le paramètre **DeleteKey** pour supprimer la clé privée avec le certificat spécifié.

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>Supprimer les certificats expirés

Cette commande utilise le paramètre **ExpiringInDays** de l' `Get-ChildItem` applet de commande avec la valeur 0 pour obtenir les certificats dans le magasin d’hébergement de contenus qui ont expiré.

La variable contenant les certificats renvoyés est dirigée vers l’applet de commande `Remove-Item` , qui les supprime. La commande utilise le paramètre **DeleteKey** pour supprimer la clé privée avec le certificat.

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>Création de certificats

L' `New-Item` applet de commande ne crée pas de certificats dans le fournisseur de **certificats** . Utilisez l’applet de commande [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) pour créer un certificat à des fins de test.

## <a name="creating-certificate-stores"></a>Création de magasins de certificats

Dans le lecteur Cert :, l' `New-Item` applet de commande crée des magasins de certificats dans l’emplacement de magasin LocalMachine. Il prend en charge les paramètres **Name**, **path**, **WhatIf** et **Confirm** . Tous les autres paramètres sont ignorés. La commande retourne un **System. Security. Cryptography. X509Certificates. X509Store** qui représente le nouveau magasin de certificats.

Cette commande crée un magasin de certificats nommé « CustomStore » à l'emplacement des magasins de l'ordinateur local.

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>Créer un nouveau magasin de certificats sur un ordinateur distant

Cette commande crée un nouveau magasin de certificats nommé « HostingStore » à l'emplacement des magasins de l'ordinateur local sur l'ordinateur Server01.

La commande utilise l' `Invoke-Command` applet de commande pour exécuter une `New-Item` commande sur l’ordinateur SERVEUR01. La commande retourne un **System. Security. Cryptography. X509Certificates. X509Store** qui représente le nouveau magasin de certificats.

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>Création de certificats clients pour WS-Man

Cette commande crée l’entrée **ClientCertificate** qui peut être utilisée par le client **WS-Management** . Le nouveau **ClientCertificate** s’affichera sous le répertoire **ClientCertificate** en tant que « ClientCertificate_1234567890 ». Tous les paramètres sont obligatoires. L' **émetteur** doit être l’empreinte numérique du certificat de l’émetteur.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>Suppression de magasins de certificats

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>Supprimer un magasin de certificats d’un ordinateur distant

Cette commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Remove-Item` commande sur les ordinateurs S1 et S2. La `Remove-Item` commande comprend le paramètre **recurse** , qui supprime les certificats dans le magasin avant de supprimer le magasin.

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur. Ces paramètres sont valides dans tous les sous-répertoires du fournisseur de certificats, mais ils s’appliquent uniquement aux certificats.

> [!NOTE]
> Les paramètres qui effectuent un filtrage sur la `EnhancedKeyUsageList` propriété retournent également des éléments avec une `EnhancedKeyUsageList` valeur de propriété vide.
> Les certificats qui ont un **EnhancedKeyUsageList** vide peuvent être utilisés dans tous les cas.

Les paramètres du fournisseur de certificats suivants ont été réintroduits dans PowerShell 7,1.

- DNSName
- DocumentEncryptionCert
- EKU
- ExpiringInDays
- SSLServerAuthentication

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert <System. Management. Automation. Paramètre_booléen>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Ce paramètre obtient les certificats dont la valeur de propriété **EnhancedKeyUsageList** est « signature du code ».

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey <System. Management. Automation. Paramètre_booléen>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

Ce paramètre supprime la clé privée associée quand elle supprime le certificat.

> [!IMPORTANT]
> Pour supprimer une clé privée associée à un certificat d’utilisateur dans le `Cert:\CurrentUser` magasin sur un ordinateur distant, vous devez utiliser des informations d’identification déléguées. L' `Invoke-Command` applet de commande prend en charge la délégation des informations d’identification à l’aide du paramètre **CredSSP** . Vous devez prendre en compte tous les risques de sécurité avant d’utiliser `Remove-Item` avec `Invoke-Command` et la délégation des informations d’identification.

Ce paramètre a été réintroduit dans PowerShell 7,1

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a>DnsName <Microsoft. PowerShell. Commands. DnsNameRepresentation>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Ce paramètre obtient les certificats qui ont le nom de domaine ou le modèle de nom spécifié dans la propriété **DNSNameList** du certificat. La valeur de ce paramètre peut être « Unicode » ou « ASCII ». Les valeurs Punycode sont converties en Unicode. Les caractères génériques ( `*` ) sont autorisés.

Ce paramètre a été réintroduit dans PowerShell 7,1

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a>DocumentEncryptionCert <System. Management. Automation. Paramètre_booléen>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Ce paramètre obtient les certificats dont la valeur de propriété **EnhancedKeyUsageList** est « chiffrement de document ».

### <a name="eku-systemstring"></a>EKU <System. String>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Ce paramètre obtient les certificats qui ont le texte ou le modèle de texte spécifié dans la `EnhancedKeyUsageList` propriété du certificat. Les caractères génériques ( `*` ) sont autorisés. La `EnhancedKeyUsageList` propriété contient le nom convivial et les champs OID de l’utilisation améliorée de la EKU.

Ce paramètre a été réintroduit dans PowerShell 7,1

### <a name="expiringindays-systemint32"></a>ExpiringInDays <System. Int32>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Ce paramètre obtient les certificats qui expirent dans ou avant le nombre de jours spécifié. Une valeur de 0 (zéro) obtient les certificats qui sont expirés.

Ce paramètre a été réintroduit dans PowerShell 7,1

### <a name="itemtype-string"></a>ItemType \<String\>

Ce paramètre vous permet de spécifier le type d’élément créé par `New-Item` .

Dans un `Certificate` lecteur, les valeurs suivantes sont autorisées :

- Fournisseur Certificate
- Certificat
- Magasin
- StoreLocation

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a>SSLServerAuthentication <System. Management. Automation. Paramètre_booléen>

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Obtient seulement les certificats serveur pour l'hébergement web SSL. Ce paramètre obtient les certificats qui ont une valeur de propriété « authentification du serveur » `EnhancedKeyUsageList` .

Ce paramètre a été réintroduit dans PowerShell 7,1

## <a name="script-properties"></a>Propriétés du script

De nouvelles propriétés de script ont été ajoutées à l’objet **X509Certificate2** qui représente les certificats pour faciliter la recherche et la gestion des certificats.

- `DnsNameList`: Pour remplir la `DnsNameList` propriété, le fournisseur de certificats copie le contenu de l’entrée dNSName dans l’extension SubjectAlternativeName (San). Si l'extension SAN est vide, la propriété est affectée du contenu du champ Objet du certificat.

- `EnhancedKeyUsageList`: Pour remplir la `EnhancedKeyUsageList` propriété, le fournisseur de certificats copie les propriétés OID du champ champ EnhancedKeyUsage (EKU) dans le certificat et crée un nom convivial pour celui-ci.

- `SendAsTrustedIssuer`: Pour remplir la `SendAsTrustedIssuer` propriété, le fournisseur de certificats copie la `SendAsTrustedIssuer` propriété du certificat.  Pour plus d’informations, consultez [gestion des émetteurs approuvés pour l’authentification du client](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).

Ces nouvelles fonctionnalités vous permettent de rechercher des certificats d'après leur nom DNS et leur date d'expiration, et de distinguer les certificats d'authentification client et serveur par la valeur de leurs propriétés d'utilisation améliorée de la clé (EKU).

## <a name="using-the-pipeline"></a>Utilisation du pipeline

Les applets de commande du fournisseur acceptent l’entrée du pipeline. Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.
Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.

## <a name="getting-help"></a>Obtenir de l’aide

Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.

Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de `Get-Help` pour spécifier un lecteur du système de fichiers.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>Voir aussi

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-PfxCertificate](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)

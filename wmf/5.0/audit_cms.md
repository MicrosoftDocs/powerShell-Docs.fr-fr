---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058996"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Applets de commande CMS (Cryptographic Message Syntax)

Les applets de commande Cryptographic Message Syntax prennent en charge le chiffrement et le déchiffrement de contenu au format IETF pour la protection par chiffrement des messages comme documenté dans la [RFC5652](https://tools.ietf.org/html/rfc5652).

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

La norme de chiffrement CMS implémente le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la *clé publique*) et les clés utilisées pour déchiffrer le contenu (la *clé privée*) sont distinctes.

Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles. Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer. Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).

Pour être reconnus dans PowerShell, les certificats de chiffrement nécessitent un identificateur EKU (Unique Key Usage) pour être identifiés comme certificats de chiffrement de données (comme les identificateurs de « signature du code » ou de « courrier chiffré »).

Voici un exemple de création de certificat adapté au chiffrement de document :

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

Ensuite, exécutez :
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

Et vous pouvez maintenant chiffrer et déchiffrer le contenu :

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

Tout paramètre de type **CMSMessageRecipient** prend en charge les identificateurs aux formats suivants :
- Un certificat réel (tel que récupéré auprès du fournisseur)
- Chemin d’un fichier contenant le certificat
- Chemin d’un répertoire contenant le certificat
- Empreinte numérique du certificat (utilisé pour rechercher dans le magasin de certificats)
- Nom du sujet du certificat (utilisé pour rechercher dans le magasin de certificats)

Pour afficher des certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez utiliser le paramètre dynamique **-DocumentEncryptionCert** :

```powershell
dir -DocumentEncryptionCert
```

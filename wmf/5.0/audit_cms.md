---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="b1b25-102">Applets de commande CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="b1b25-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="b1b25-103">Les applets de commande Cryptographic Message Syntax prennent en charge le chiffrement et le déchiffrement de contenu au format IETF pour la protection par chiffrement des messages comme documenté dans la [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="b1b25-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

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

<span data-ttu-id="b1b25-104">La norme de chiffrement CMS implémente le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la *clé publique*) et les clés utilisées pour déchiffrer le contenu (la *clé privée*) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="b1b25-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="b1b25-105">Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="b1b25-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="b1b25-106">Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="b1b25-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="b1b25-107">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="b1b25-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="b1b25-108">Pour être reconnus dans PowerShell, les certificats de chiffrement nécessitent un identificateur EKU (Unique Key Usage) pour être identifiés comme certificats de chiffrement de données (comme les identificateurs de « signature du code » ou de « courrier chiffré »).</span><span class="sxs-lookup"><span data-stu-id="b1b25-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="b1b25-109">Voici un exemple de création de certificat adapté au chiffrement de document :</span><span class="sxs-lookup"><span data-stu-id="b1b25-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

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

<span data-ttu-id="b1b25-110">Ensuite, exécutez :</span><span class="sxs-lookup"><span data-stu-id="b1b25-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="b1b25-111">Et vous pouvez maintenant chiffrer et déchiffrer le contenu :</span><span class="sxs-lookup"><span data-stu-id="b1b25-111">And you can now encrypt and decrypt content:</span></span>

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

<span data-ttu-id="b1b25-112">Tout paramètre de type **CMSMessageRecipient** prend en charge les identificateurs aux formats suivants :</span><span class="sxs-lookup"><span data-stu-id="b1b25-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="b1b25-113">Un certificat réel (tel que récupéré auprès du fournisseur)</span><span class="sxs-lookup"><span data-stu-id="b1b25-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="b1b25-114">Chemin d’un fichier contenant le certificat</span><span class="sxs-lookup"><span data-stu-id="b1b25-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="b1b25-115">Chemin d’un répertoire contenant le certificat</span><span class="sxs-lookup"><span data-stu-id="b1b25-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="b1b25-116">Empreinte numérique du certificat (utilisé pour rechercher dans le magasin de certificats)</span><span class="sxs-lookup"><span data-stu-id="b1b25-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="b1b25-117">Nom du sujet du certificat (utilisé pour rechercher dans le magasin de certificats)</span><span class="sxs-lookup"><span data-stu-id="b1b25-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="b1b25-118">Pour afficher des certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez utiliser le paramètre dynamique **-DocumentEncryptionCert** :</span><span class="sxs-lookup"><span data-stu-id="b1b25-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```

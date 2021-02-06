---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 57213b72bee5733f6e8089ff7dcbb9be82104d8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598581"
---
# <span data-ttu-id="b8cbe-102">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b8cbe-102">Protect-CmsMessage</span></span>

## <span data-ttu-id="b8cbe-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b8cbe-103">SYNOPSIS</span></span>
<span data-ttu-id="b8cbe-104">Chiffre le contenu à l’aide du format de syntaxe de message de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-104">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="b8cbe-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b8cbe-105">SYNTAX</span></span>

### <span data-ttu-id="b8cbe-106">ByContent (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b8cbe-106">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b8cbe-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="b8cbe-107">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="b8cbe-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b8cbe-108">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="b8cbe-109">Description</span><span class="sxs-lookup"><span data-stu-id="b8cbe-109">DESCRIPTION</span></span>

<span data-ttu-id="b8cbe-110">L' `Protect-CmsMessage` applet de commande chiffre le contenu à l’aide du format CMS (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-110">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="b8cbe-111">Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF, comme documenté par [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-111">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="b8cbe-112">La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="b8cbe-113">Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="b8cbe-114">Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="b8cbe-115">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="b8cbe-116">Avant de pouvoir exécuter l' `Protect-CmsMessage` applet de commande, vous devez disposer d’un certificat de chiffrement configuré.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-116">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="b8cbe-117">Pour être reconnus dans PowerShell, les certificats de chiffrement requièrent un ID d’utilisation[améliorée](/windows/desktop/SecCrypto/eku)de la clé unique pour les identifier en tant que certificats de chiffrement de données (tels que les ID pour la signature de code et le courrier chiffré).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-117">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="b8cbe-118">Pour obtenir un exemple de certificat qui fonctionnerait pour le chiffrement de document, consultez l’exemple 1 de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-118">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

<span data-ttu-id="b8cbe-119">La prise en charge de Linux et macOS a été ajoutée dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-119">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="b8cbe-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b8cbe-120">EXAMPLES</span></span>

### <span data-ttu-id="b8cbe-121">Exemple 1 : créer un certificat pour le chiffrement du contenu</span><span class="sxs-lookup"><span data-stu-id="b8cbe-121">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="b8cbe-122">Avant de pouvoir exécuter l' `Protect-CmsMessage` applet de commande, vous devez créer un certificat de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-122">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="b8cbe-123">À l’aide du texte suivant, remplacez le nom de la ligne d’objet par votre nom, votre adresse de messagerie ou tout autre identificateur, puis enregistrez le certificat dans un fichier (tel que `DocumentEncryption.inf` , comme illustré dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-123">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### <span data-ttu-id="b8cbe-124">Exemple 2 : chiffrer un message envoyé par courrier électronique</span><span class="sxs-lookup"><span data-stu-id="b8cbe-124">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="b8cbe-125">Dans l’exemple suivant, vous chiffrez un message, « Hello World », en le canalisant vers l’applet de commande, puis vous `Protect-CmsMessage` Enregistrez le message chiffré dans une variable.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-125">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="b8cbe-126">Le paramètre **to** utilise la valeur de la ligne d’objet dans le certificat.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-126">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="b8cbe-127">Exemple 3 : afficher les certificats de chiffrement de document</span><span class="sxs-lookup"><span data-stu-id="b8cbe-127">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="b8cbe-128">Pour afficher les certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez ajouter le paramètre dynamique **DocumentEncryptionCert** de l’opérateur [« obtenir-ChildItem »](../Microsoft.PowerShell.Management/Get-ChildItem.md), disponible uniquement lorsque le fournisseur de certificats est chargé.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-128">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="b8cbe-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8cbe-129">PARAMETERS</span></span>

### <span data-ttu-id="b8cbe-130">-Contenu</span><span class="sxs-lookup"><span data-stu-id="b8cbe-130">-Content</span></span>

<span data-ttu-id="b8cbe-131">Spécifie un **PSObject** qui contient le contenu que vous souhaitez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-131">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="b8cbe-132">Par exemple, vous pouvez chiffrer le contenu d’un message d’événement, puis utiliser la variable contenant le message ( `$Event` , dans cet exemple) comme valeur du paramètre de **contenu** : `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` .</span><span class="sxs-lookup"><span data-stu-id="b8cbe-132">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="b8cbe-133">Vous pouvez également utiliser l' `Get-Content` applet de commande pour obtenir le contenu d’un fichier, tel qu’un document Microsoft Word, et enregistrer le contenu dans une variable que vous utilisez comme valeur du paramètre de **contenu** .</span><span class="sxs-lookup"><span data-stu-id="b8cbe-133">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8cbe-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b8cbe-134">-LiteralPath</span></span>

<span data-ttu-id="b8cbe-135">Spécifie le chemin d’accès au contenu que vous souhaitez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-135">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="b8cbe-136">Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-136">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b8cbe-137">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b8cbe-138">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b8cbe-139">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8cbe-140">-Fichier de journal</span><span class="sxs-lookup"><span data-stu-id="b8cbe-140">-OutFile</span></span>

<span data-ttu-id="b8cbe-141">Spécifie le chemin d’accès et le nom de fichier d’un fichier auquel vous souhaitez envoyer le contenu chiffré.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-141">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8cbe-142">-Path</span><span class="sxs-lookup"><span data-stu-id="b8cbe-142">-Path</span></span>

<span data-ttu-id="b8cbe-143">Spécifie le chemin d’accès au contenu que vous souhaitez chiffrer.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-143">Specifies the path to content that you want to encrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8cbe-144">-To</span><span class="sxs-lookup"><span data-stu-id="b8cbe-144">-To</span></span>

<span data-ttu-id="b8cbe-145">Spécifie un ou plusieurs destinataires de message CMS, identifiés dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="b8cbe-145">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="b8cbe-146">Un certificat réel (tel que récupéré auprès du fournisseur de certificats).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-146">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="b8cbe-147">Chemin d’accès au fichier contenant le certificat.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-147">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="b8cbe-148">Chemin d’accès à un répertoire contenant le certificat.</span><span class="sxs-lookup"><span data-stu-id="b8cbe-148">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="b8cbe-149">Empreinte numérique du certificat (utilisé pour rechercher dans le magasin de certificats).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-149">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="b8cbe-150">Nom du sujet du certificat (utilisé pour rechercher dans le magasin de certificats).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-150">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8cbe-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8cbe-151">CommonParameters</span></span>

<span data-ttu-id="b8cbe-152">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b8cbe-152">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b8cbe-153">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b8cbe-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b8cbe-154">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b8cbe-154">INPUTS</span></span>

## <span data-ttu-id="b8cbe-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b8cbe-155">OUTPUTS</span></span>

## <span data-ttu-id="b8cbe-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b8cbe-156">NOTES</span></span>

## <span data-ttu-id="b8cbe-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b8cbe-157">RELATED LINKS</span></span>

[<span data-ttu-id="b8cbe-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b8cbe-158">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="b8cbe-159">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b8cbe-159">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="b8cbe-160">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b8cbe-160">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)

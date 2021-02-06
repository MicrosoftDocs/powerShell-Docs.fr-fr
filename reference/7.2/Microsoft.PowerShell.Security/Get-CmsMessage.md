---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 421b49139f4750787b6c1c04d8a41a624755109a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597549"
---
# <span data-ttu-id="c34ee-102">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c34ee-102">Get-CmsMessage</span></span>

## <span data-ttu-id="c34ee-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c34ee-103">SYNOPSIS</span></span>
<span data-ttu-id="c34ee-104">Obtient le contenu qui a été chiffré à l’aide du format de syntaxe de message de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="c34ee-104">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="c34ee-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c34ee-105">SYNTAX</span></span>

### <span data-ttu-id="c34ee-106">ByContent</span><span class="sxs-lookup"><span data-stu-id="c34ee-106">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="c34ee-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="c34ee-107">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="c34ee-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="c34ee-108">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="c34ee-109">Description</span><span class="sxs-lookup"><span data-stu-id="c34ee-109">DESCRIPTION</span></span>

<span data-ttu-id="c34ee-110">L' `Get-CmsMessage` applet de commande obtient le contenu qui a été chiffré à l’aide du format CMS (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="c34ee-110">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="c34ee-111">Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF pour la protection par chiffrement des messages, comme indiqué par [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="c34ee-111">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="c34ee-112">La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="c34ee-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="c34ee-113">Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="c34ee-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="c34ee-114">Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="c34ee-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="c34ee-115">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="c34ee-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="c34ee-116">`Get-CmsMessage` Obtient le contenu qui a été chiffré au format CMS.</span><span class="sxs-lookup"><span data-stu-id="c34ee-116">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="c34ee-117">Il ne déchiffre pas ou n’annule pas la protection du contenu.</span><span class="sxs-lookup"><span data-stu-id="c34ee-117">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="c34ee-118">Vous pouvez exécuter cette applet de commande pour obtenir le contenu que vous avez chiffré en exécutant l’applet de commande `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="c34ee-118">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="c34ee-119">Vous pouvez spécifier le contenu que vous souhaitez déchiffrer sous forme de chaîne ou le chemin d’accès au contenu chiffré.</span><span class="sxs-lookup"><span data-stu-id="c34ee-119">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="c34ee-120">Vous pouvez diriger les résultats de `Get-CmsMessage` vers pour `Unprotect-CmsMessage` déchiffrer le contenu, à condition que vous disposiez d’informations sur le certificat de chiffrement de document qui a été utilisé pour chiffrer le contenu.</span><span class="sxs-lookup"><span data-stu-id="c34ee-120">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

<span data-ttu-id="c34ee-121">La prise en charge de Linux et macOS a été ajoutée dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="c34ee-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="c34ee-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c34ee-122">EXAMPLES</span></span>

### <span data-ttu-id="c34ee-123">Exemple 1 : recevoir du contenu chiffré</span><span class="sxs-lookup"><span data-stu-id="c34ee-123">Example 1: Get encrypted content</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

<span data-ttu-id="c34ee-124">Cette commande obtient le contenu chiffré situé dans C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span><span class="sxs-lookup"><span data-stu-id="c34ee-124">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="c34ee-125">Exemple 2 : contenu chiffré de canal à Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c34ee-125">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="c34ee-126">Cette commande envoie les résultats de l' `Get-CmsMessage` applet de commande de l’exemple 1 à `Unprotect-CmsMessage` , pour déchiffrer le message et le lire en texte brut.</span><span class="sxs-lookup"><span data-stu-id="c34ee-126">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="c34ee-127">Dans ce cas, la valeur du paramètre **to** est la valeur de la ligne subject du certificat de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="c34ee-127">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="c34ee-128">Le message déchiffré « essayez la nouvelle commande Break All » est le résultat.</span><span class="sxs-lookup"><span data-stu-id="c34ee-128">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="c34ee-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c34ee-129">PARAMETERS</span></span>

### <span data-ttu-id="c34ee-130">-Contenu</span><span class="sxs-lookup"><span data-stu-id="c34ee-130">-Content</span></span>

<span data-ttu-id="c34ee-131">Spécifie une chaîne chiffrée ou une variable contenant une chaîne chiffrée.</span><span class="sxs-lookup"><span data-stu-id="c34ee-131">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c34ee-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c34ee-132">-LiteralPath</span></span>

<span data-ttu-id="c34ee-133">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez obtenir.</span><span class="sxs-lookup"><span data-stu-id="c34ee-133">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="c34ee-134">Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="c34ee-134">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c34ee-135">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="c34ee-135">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="c34ee-136">Si le chemin d’accès comprend des caractères d’échappement, mettez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="c34ee-136">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="c34ee-137">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères entourés comme des caractères d’échappement.</span><span class="sxs-lookup"><span data-stu-id="c34ee-137">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="c34ee-138">-Path</span><span class="sxs-lookup"><span data-stu-id="c34ee-138">-Path</span></span>

<span data-ttu-id="c34ee-139">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="c34ee-139">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="c34ee-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c34ee-140">CommonParameters</span></span>

<span data-ttu-id="c34ee-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c34ee-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c34ee-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c34ee-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c34ee-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c34ee-143">INPUTS</span></span>

## <span data-ttu-id="c34ee-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c34ee-144">OUTPUTS</span></span>

## <span data-ttu-id="c34ee-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c34ee-145">NOTES</span></span>

## <span data-ttu-id="c34ee-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c34ee-146">RELATED LINKS</span></span>

[<span data-ttu-id="c34ee-147">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c34ee-147">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c34ee-148">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c34ee-148">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="c34ee-149">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c34ee-149">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)


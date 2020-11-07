---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: bbb4fe84a1c41afa6d16f4b127475b3405c7f81d
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347089"
---
# <span data-ttu-id="7a22d-103">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7a22d-103">Get-CmsMessage</span></span>

## <span data-ttu-id="7a22d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7a22d-104">SYNOPSIS</span></span>
<span data-ttu-id="7a22d-105">Obtient le contenu qui a été chiffré à l’aide du format de syntaxe de message de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="7a22d-105">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="7a22d-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="7a22d-106">SYNTAX</span></span>

### <span data-ttu-id="7a22d-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="7a22d-107">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="7a22d-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="7a22d-108">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="7a22d-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a22d-109">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="7a22d-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7a22d-110">DESCRIPTION</span></span>

<span data-ttu-id="7a22d-111">L' `Get-CmsMessage` applet de commande obtient le contenu qui a été chiffré à l’aide du format CMS (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="7a22d-111">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="7a22d-112">Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF pour la protection par chiffrement des messages, comme indiqué par [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="7a22d-112">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="7a22d-113">La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="7a22d-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="7a22d-114">Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="7a22d-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="7a22d-115">Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="7a22d-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="7a22d-116">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="7a22d-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="7a22d-117">`Get-CmsMessage` Obtient le contenu qui a été chiffré au format CMS.</span><span class="sxs-lookup"><span data-stu-id="7a22d-117">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="7a22d-118">Il ne déchiffre pas ou n’annule pas la protection du contenu.</span><span class="sxs-lookup"><span data-stu-id="7a22d-118">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="7a22d-119">Vous pouvez exécuter cette applet de commande pour obtenir le contenu que vous avez chiffré en exécutant l’applet de commande `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="7a22d-119">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="7a22d-120">Vous pouvez spécifier le contenu que vous souhaitez déchiffrer sous forme de chaîne ou le chemin d’accès au contenu chiffré.</span><span class="sxs-lookup"><span data-stu-id="7a22d-120">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="7a22d-121">Vous pouvez diriger les résultats de `Get-CmsMessage` vers pour `Unprotect-CmsMessage` déchiffrer le contenu, à condition que vous disposiez d’informations sur le certificat de chiffrement de document qui a été utilisé pour chiffrer le contenu.</span><span class="sxs-lookup"><span data-stu-id="7a22d-121">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

> [!NOTE]
> <span data-ttu-id="7a22d-122">Cette applet de commande est disponible uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="7a22d-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="7a22d-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7a22d-123">EXAMPLES</span></span>

### <span data-ttu-id="7a22d-124">Exemple 1 : recevoir du contenu chiffré</span><span class="sxs-lookup"><span data-stu-id="7a22d-124">Example 1: Get encrypted content</span></span>

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

<span data-ttu-id="7a22d-125">Cette commande obtient le contenu chiffré situé dans C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span><span class="sxs-lookup"><span data-stu-id="7a22d-125">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="7a22d-126">Exemple 2 : contenu chiffré de canal à Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7a22d-126">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="7a22d-127">Cette commande envoie les résultats de l' `Get-CmsMessage` applet de commande de l’exemple 1 à `Unprotect-CmsMessage` , pour déchiffrer le message et le lire en texte brut.</span><span class="sxs-lookup"><span data-stu-id="7a22d-127">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="7a22d-128">Dans ce cas, la valeur du paramètre **to** est la valeur de la ligne subject du certificat de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="7a22d-128">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="7a22d-129">Le message déchiffré « essayez la nouvelle commande Break All » est le résultat.</span><span class="sxs-lookup"><span data-stu-id="7a22d-129">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="7a22d-130">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="7a22d-130">PARAMETERS</span></span>

### <span data-ttu-id="7a22d-131">-Contenu</span><span class="sxs-lookup"><span data-stu-id="7a22d-131">-Content</span></span>

<span data-ttu-id="7a22d-132">Spécifie une chaîne chiffrée ou une variable contenant une chaîne chiffrée.</span><span class="sxs-lookup"><span data-stu-id="7a22d-132">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="7a22d-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a22d-133">-LiteralPath</span></span>

<span data-ttu-id="7a22d-134">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez obtenir.</span><span class="sxs-lookup"><span data-stu-id="7a22d-134">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="7a22d-135">Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="7a22d-135">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7a22d-136">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="7a22d-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="7a22d-137">Si le chemin d’accès comprend des caractères d’échappement, mettez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="7a22d-137">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="7a22d-138">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères entourés comme des caractères d’échappement.</span><span class="sxs-lookup"><span data-stu-id="7a22d-138">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="7a22d-139">-Path</span><span class="sxs-lookup"><span data-stu-id="7a22d-139">-Path</span></span>

<span data-ttu-id="7a22d-140">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="7a22d-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="7a22d-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a22d-141">CommonParameters</span></span>

<span data-ttu-id="7a22d-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a22d-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a22d-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7a22d-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a22d-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7a22d-144">INPUTS</span></span>

## <span data-ttu-id="7a22d-145">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7a22d-145">OUTPUTS</span></span>

## <span data-ttu-id="7a22d-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7a22d-146">NOTES</span></span>

<span data-ttu-id="7a22d-147">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="7a22d-147">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="7a22d-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7a22d-148">RELATED LINKS</span></span>

[<span data-ttu-id="7a22d-149">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7a22d-149">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="7a22d-150">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7a22d-150">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="7a22d-151">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7a22d-151">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)

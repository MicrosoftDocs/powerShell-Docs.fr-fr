---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.x&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 394e8c1b18d7ba0f4b65e1681faffe795592b97d
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347667"
---
# <span data-ttu-id="7e771-103">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7e771-103">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="7e771-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7e771-104">SYNOPSIS</span></span>
<span data-ttu-id="7e771-105">Déchiffre le contenu qui a été chiffré à l’aide du format de syntaxe de message de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="7e771-105">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="7e771-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="7e771-106">SYNTAX</span></span>

### <span data-ttu-id="7e771-107">ByWinEvent (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7e771-107">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="7e771-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="7e771-108">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="7e771-109">ByPath</span><span class="sxs-lookup"><span data-stu-id="7e771-109">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="7e771-110">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e771-110">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="7e771-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7e771-111">DESCRIPTION</span></span>

<span data-ttu-id="7e771-112">L' `Unprotect-CmsMessage` applet de commande déchiffre le contenu qui a été chiffré à l’aide du format CMS (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="7e771-112">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="7e771-113">Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format standard IETF pour la protection par chiffrement des messages, comme indiqué par [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="7e771-113">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="7e771-114">La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="7e771-114">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="7e771-115">Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="7e771-115">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="7e771-116">Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="7e771-116">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="7e771-117">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="7e771-117">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="7e771-118">`Unprotect-CmsMessage` déchiffre le contenu qui a été chiffré au format CMS.</span><span class="sxs-lookup"><span data-stu-id="7e771-118">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="7e771-119">Vous pouvez exécuter cette applet de commande pour déchiffrer le contenu que vous avez chiffré en exécutant l’applet de commande `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="7e771-119">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="7e771-120">Vous pouvez spécifier le contenu que vous souhaitez déchiffrer sous forme de chaîne, le numéro d’ID d’enregistrement du journal des événements de chiffrement ou le chemin d’accès au contenu chiffré.</span><span class="sxs-lookup"><span data-stu-id="7e771-120">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="7e771-121">L' `Unprotect-CmsMessage` applet de commande retourne le contenu déchiffré.</span><span class="sxs-lookup"><span data-stu-id="7e771-121">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

> [!NOTE]
> <span data-ttu-id="7e771-122">Cette applet de commande est disponible uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="7e771-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="7e771-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7e771-123">EXAMPLES</span></span>

### <span data-ttu-id="7e771-124">Exemple 1 : déchiffrer un message</span><span class="sxs-lookup"><span data-stu-id="7e771-124">Example 1: Decrypt a message</span></span>

<span data-ttu-id="7e771-125">Dans l’exemple suivant, vous déchiffrez le contenu qui se trouve dans le chemin d’accès littéral `C:\Users\Test\Documents\PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="7e771-125">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="7e771-126">Pour la valeur du paramètre requis **pour** , cet exemple utilise l’empreinte numérique du certificat qui a été utilisé pour effectuer le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="7e771-126">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="7e771-127">Le message déchiffré « essayez la nouvelle commande Break All » est le résultat.</span><span class="sxs-lookup"><span data-stu-id="7e771-127">The decrypted message, "Try the new Break All command," is the result.</span></span>

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

## <span data-ttu-id="7e771-128">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="7e771-128">PARAMETERS</span></span>

### <span data-ttu-id="7e771-129">-Contenu</span><span class="sxs-lookup"><span data-stu-id="7e771-129">-Content</span></span>

<span data-ttu-id="7e771-130">Spécifie une chaîne chiffrée ou une variable contenant une chaîne chiffrée.</span><span class="sxs-lookup"><span data-stu-id="7e771-130">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7e771-131">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="7e771-131">-EventLogRecord</span></span>

<span data-ttu-id="7e771-132">Spécifie un ID d’enregistrement de journal des événements qui représente une opération de chiffrement CMS.</span><span class="sxs-lookup"><span data-stu-id="7e771-132">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7e771-133">-IncludeContext</span><span class="sxs-lookup"><span data-stu-id="7e771-133">-IncludeContext</span></span>

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

### <span data-ttu-id="7e771-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e771-134">-LiteralPath</span></span>

<span data-ttu-id="7e771-135">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="7e771-135">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="7e771-136">Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="7e771-136">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7e771-137">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="7e771-137">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="7e771-138">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="7e771-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7e771-139">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="7e771-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e771-140">-Path</span><span class="sxs-lookup"><span data-stu-id="7e771-140">-Path</span></span>

<span data-ttu-id="7e771-141">Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="7e771-141">Specifies the path to encrypted content that you want to decrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e771-142">-To</span><span class="sxs-lookup"><span data-stu-id="7e771-142">-To</span></span>

<span data-ttu-id="7e771-143">Spécifie un ou plusieurs destinataires de message CMS, identifiés dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="7e771-143">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="7e771-144">Un certificat réel (tel que récupéré auprès du fournisseur de certificats).</span><span class="sxs-lookup"><span data-stu-id="7e771-144">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="7e771-145">Chemin d’accès au fichier contenant le certificat.</span><span class="sxs-lookup"><span data-stu-id="7e771-145">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="7e771-146">Chemin d’accès à un répertoire contenant le certificat.</span><span class="sxs-lookup"><span data-stu-id="7e771-146">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="7e771-147">Empreinte numérique du certificat (utilisé pour rechercher dans le magasin de certificats).</span><span class="sxs-lookup"><span data-stu-id="7e771-147">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="7e771-148">Nom du sujet du certificat (utilisé pour rechercher dans le magasin de certificats).</span><span class="sxs-lookup"><span data-stu-id="7e771-148">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e771-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e771-149">CommonParameters</span></span>

<span data-ttu-id="7e771-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e771-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e771-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e771-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e771-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7e771-152">INPUTS</span></span>

### <span data-ttu-id="7e771-153">System. Diagnostics. Eventing. Reader. EventLogRecord ou System. String</span><span class="sxs-lookup"><span data-stu-id="7e771-153">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="7e771-154">Vous pouvez diriger un objet contenant du contenu chiffré vers `Unprotect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="7e771-154">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="7e771-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7e771-155">OUTPUTS</span></span>

### <span data-ttu-id="7e771-156">System.String</span><span class="sxs-lookup"><span data-stu-id="7e771-156">System.String</span></span>

<span data-ttu-id="7e771-157">Message non chiffré.</span><span class="sxs-lookup"><span data-stu-id="7e771-157">The unencrypted message.</span></span>

## <span data-ttu-id="7e771-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7e771-158">NOTES</span></span>

<span data-ttu-id="7e771-159">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="7e771-159">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="7e771-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7e771-160">RELATED LINKS</span></span>

[<span data-ttu-id="7e771-161">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7e771-161">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="7e771-162">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7e771-162">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="7e771-163">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="7e771-163">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

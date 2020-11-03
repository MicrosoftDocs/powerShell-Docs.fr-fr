---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ed9ef1102c1e34670b3cb5664a227f86124812a0
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205786"
---
# <span data-ttu-id="9a47c-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="9a47c-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="9a47c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9a47c-104">SYNOPSIS</span></span>
<span data-ttu-id="9a47c-105">Convertit une chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="9a47c-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="9a47c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a47c-106">SYNTAX</span></span>

### <span data-ttu-id="9a47c-107">Sécurisé (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9a47c-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="9a47c-108">AsPlainText</span><span class="sxs-lookup"><span data-stu-id="9a47c-108">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="9a47c-109">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="9a47c-109">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="9a47c-110">Description</span><span class="sxs-lookup"><span data-stu-id="9a47c-110">DESCRIPTION</span></span>

<span data-ttu-id="9a47c-111">L’applet de commande **ConvertFrom-SecureString** convertit une chaîne sécurisée ( **System. Security. SecureString** ) en une chaîne chiffrée standard ( **System. String** ).</span><span class="sxs-lookup"><span data-stu-id="9a47c-111">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="9a47c-112">Contrairement à une chaîne sécurisée, une chaîne chiffrée standard peut être enregistrée dans un fichier pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9a47c-112">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="9a47c-113">La chaîne standard chiffrée peut être reconvertie dans son format de chaîne sécurisée à l’aide de l’applet de commande `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="9a47c-113">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="9a47c-114">Si une clé de chiffrement est spécifiée à l'aide des paramètres **Key** ou **SecureKey** , l'algorithme de chiffrement AES (Advanced Encryption Standard) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9a47c-114">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="9a47c-115">La clé spécifiée doit avoir une longueur égale à 128, 192 ou 256 bits, car ce sont les longueurs de clé prises en charge par l'algorithme de chiffrement AES.</span><span class="sxs-lookup"><span data-stu-id="9a47c-115">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="9a47c-116">Si aucune clé n'est spécifiée, l'API de protection des données (DPAPI) Windows est utilisée pour chiffrer la représentation de chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="9a47c-116">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="9a47c-117">Notez que, selon [dotnet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), le contenu d’une SecureString n’est pas chiffré sur les systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="9a47c-117">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="9a47c-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9a47c-118">EXAMPLES</span></span>

### <span data-ttu-id="9a47c-119">Exemple 1 : créer une chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="9a47c-119">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="9a47c-120">Cette commande crée une chaîne sécurisée à partir de caractères que vous tapez à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="9a47c-120">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="9a47c-121">Après avoir entré la commande, tapez la chaîne que vous souhaitez stocker en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="9a47c-121">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="9a47c-122">Un astérisque ( `*` ) s’affiche pour représenter chaque caractère que vous tapez.</span><span class="sxs-lookup"><span data-stu-id="9a47c-122">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="9a47c-123">Exemple 2 : convertir une chaîne sécurisée en chaîne standard chiffrée</span><span class="sxs-lookup"><span data-stu-id="9a47c-123">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="9a47c-124">Cette commande convertit la chaîne sécurisée dans la `$SecureString` variable en une chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="9a47c-124">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="9a47c-125">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="9a47c-125">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="9a47c-126">Exemple 3 : convertir une chaîne sécurisée en chaîne standard chiffrée avec une clé de 192 bits</span><span class="sxs-lookup"><span data-stu-id="9a47c-126">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="9a47c-127">Ces commandes utilisent l’algorithme Advanced Encryption Standard (AES) pour convertir la chaîne sécurisée stockée dans la `$SecureString` variable en chaîne standard chiffrée avec une clé de 192 bits.</span><span class="sxs-lookup"><span data-stu-id="9a47c-127">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="9a47c-128">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="9a47c-128">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="9a47c-129">La première commande stocke une clé dans la `$Key` variable.</span><span class="sxs-lookup"><span data-stu-id="9a47c-129">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="9a47c-130">La clé est un tableau de 24 chiffres décimaux, chacun d’entre eux devant être inférieur à 256 pour tenir dans un seul octet non signé.</span><span class="sxs-lookup"><span data-stu-id="9a47c-130">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="9a47c-131">Étant donné que chaque chiffre décimal représente un seul octet (8 bits), la clé a 24 chiffres pour un total de 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="9a47c-131">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="9a47c-132">Il s'agit d'une longueur de clé valide pour l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="9a47c-132">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="9a47c-133">La deuxième commande utilise la clé de la `$Key` variable pour convertir la chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="9a47c-133">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="9a47c-134">Exemple 4 : convertir directement une chaîne sécurisée en une chaîne de texte en clair</span><span class="sxs-lookup"><span data-stu-id="9a47c-134">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="9a47c-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a47c-135">PARAMETERS</span></span>

### <span data-ttu-id="9a47c-136">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="9a47c-136">-AsPlainText</span></span>

<span data-ttu-id="9a47c-137">Quand `ConvertFrom-SecureString` elle est définie, elle convertit les chaînes sécurisées en une chaîne de texte en clair déchiffrée en sortie.</span><span class="sxs-lookup"><span data-stu-id="9a47c-137">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="9a47c-138">Ce paramètre a été ajouté dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="9a47c-138">This paramater was added in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a47c-139">-Clé</span><span class="sxs-lookup"><span data-stu-id="9a47c-139">-Key</span></span>

<span data-ttu-id="9a47c-140">Spécifie la clé de chiffrement en tant que tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="9a47c-140">Specifies the encryption key as a byte array.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a47c-141">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="9a47c-141">-SecureKey</span></span>

<span data-ttu-id="9a47c-142">Spécifie la clé de chiffrement en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="9a47c-142">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="9a47c-143">La valeur de chaîne sécurisée est convertie en un tableau d'octets avant d'être utilisée comme clé.</span><span class="sxs-lookup"><span data-stu-id="9a47c-143">The secure string value is converted to a byte array before being used as the key.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a47c-144">-SecureString</span><span class="sxs-lookup"><span data-stu-id="9a47c-144">-SecureString</span></span>

<span data-ttu-id="9a47c-145">Spécifie la chaîne sécurisée à convertir en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="9a47c-145">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9a47c-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a47c-146">CommonParameters</span></span>

<span data-ttu-id="9a47c-147">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="9a47c-147">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="9a47c-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9a47c-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a47c-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9a47c-149">INPUTS</span></span>

### <span data-ttu-id="9a47c-150">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="9a47c-150">System.Security.SecureString</span></span>

<span data-ttu-id="9a47c-151">Vous pouvez diriger un objet **SecureString** vers ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="9a47c-151">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="9a47c-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9a47c-152">OUTPUTS</span></span>

### <span data-ttu-id="9a47c-153">System.String</span><span class="sxs-lookup"><span data-stu-id="9a47c-153">System.String</span></span>

<span data-ttu-id="9a47c-154">ConvertFrom-SecureString retourne un objet chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="9a47c-154">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="9a47c-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9a47c-155">NOTES</span></span>

- <span data-ttu-id="9a47c-156">Pour créer une chaîne sécurisée à partir de caractères tapés à l’invite de commandes, utilisez le paramètre **AsSecureString** de l’applet de commande `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="9a47c-156">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="9a47c-157">Lorsque vous utilisez les paramètres **Key** ou **SecureKey** pour spécifier une clé, la longueur de la clé doit être correcte.</span><span class="sxs-lookup"><span data-stu-id="9a47c-157">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="9a47c-158">Par exemple, une clé de 128 bits peut être spécifiée sous la forme d’un tableau d’octets de 16 chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="9a47c-158">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="9a47c-159">De même, les clés 192 bits et 256 bits correspondent aux tableaux d’octets de 24 et 32 chiffres décimaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9a47c-159">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="9a47c-160">Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient.</span><span class="sxs-lookup"><span data-stu-id="9a47c-160">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="9a47c-161">Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9a47c-161">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="9a47c-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9a47c-162">RELATED LINKS</span></span>

[<span data-ttu-id="9a47c-163">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="9a47c-163">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="9a47c-164">Read-Host</span><span class="sxs-lookup"><span data-stu-id="9a47c-164">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

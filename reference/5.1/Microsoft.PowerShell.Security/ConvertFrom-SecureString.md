---
external help file: Microsoft.PowerShell.Security.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4dae7806cbec85347a8dfa01348be72061214c6c
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205281"
---
# <span data-ttu-id="8ddc2-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="8ddc2-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="8ddc2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8ddc2-104">SYNOPSIS</span></span>
<span data-ttu-id="8ddc2-105">Convertit une chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="8ddc2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ddc2-106">SYNTAX</span></span>

### <span data-ttu-id="8ddc2-107">Sécurisé (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8ddc2-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="8ddc2-108">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="8ddc2-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="8ddc2-109">Description</span><span class="sxs-lookup"><span data-stu-id="8ddc2-109">DESCRIPTION</span></span>

<span data-ttu-id="8ddc2-110">L’applet de commande **ConvertFrom-SecureString** convertit une chaîne sécurisée ( **System. Security. SecureString** ) en une chaîne chiffrée standard ( **System. String** ).</span><span class="sxs-lookup"><span data-stu-id="8ddc2-110">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="8ddc2-111">Contrairement à une chaîne sécurisée, une chaîne chiffrée standard peut être enregistrée dans un fichier pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="8ddc2-112">La chaîne standard chiffrée peut être reconvertie dans son format de chaîne sécurisée à l’aide de l’applet de commande `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="8ddc2-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="8ddc2-113">Si une clé de chiffrement est spécifiée à l'aide des paramètres **Key** ou **SecureKey** , l'algorithme de chiffrement AES (Advanced Encryption Standard) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="8ddc2-114">La clé spécifiée doit avoir une longueur égale à 128, 192 ou 256 bits, car ce sont les longueurs de clé prises en charge par l'algorithme de chiffrement AES.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="8ddc2-115">Si aucune clé n'est spécifiée, l'API de protection des données (DPAPI) Windows est utilisée pour chiffrer la représentation de chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

## <span data-ttu-id="8ddc2-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8ddc2-116">EXAMPLES</span></span>

### <span data-ttu-id="8ddc2-117">Exemple 1 : créer une chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="8ddc2-117">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="8ddc2-118">Cette commande crée une chaîne sécurisée à partir de caractères que vous tapez à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-118">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="8ddc2-119">Après avoir entré la commande, tapez la chaîne que vous souhaitez stocker en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-119">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="8ddc2-120">Un astérisque ( `*` ) s’affiche pour représenter chaque caractère que vous tapez.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-120">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="8ddc2-121">Exemple 2 : convertir une chaîne sécurisée en chaîne standard chiffrée</span><span class="sxs-lookup"><span data-stu-id="8ddc2-121">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="8ddc2-122">Cette commande convertit la chaîne sécurisée dans la `$SecureString` variable en une chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-122">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="8ddc2-123">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-123">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="8ddc2-124">Exemple 3 : convertir une chaîne sécurisée en chaîne standard chiffrée avec une clé de 192 bits</span><span class="sxs-lookup"><span data-stu-id="8ddc2-124">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="8ddc2-125">Ces commandes utilisent l’algorithme Advanced Encryption Standard (AES) pour convertir la chaîne sécurisée stockée dans la `$SecureString` variable en chaîne standard chiffrée avec une clé de 192 bits.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-125">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="8ddc2-126">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-126">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="8ddc2-127">La première commande stocke une clé dans la `$Key` variable.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-127">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="8ddc2-128">La clé est un tableau de 24 chiffres décimaux, chacun d’entre eux devant être inférieur à 256 pour tenir dans un seul octet non signé.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-128">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="8ddc2-129">Étant donné que chaque chiffre décimal représente un seul octet (8 bits), la clé a 24 chiffres pour un total de 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="8ddc2-129">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="8ddc2-130">Il s'agit d'une longueur de clé valide pour l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-130">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="8ddc2-131">La deuxième commande utilise la clé de la `$Key` variable pour convertir la chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-131">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="8ddc2-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ddc2-132">PARAMETERS</span></span>

### <span data-ttu-id="8ddc2-133">-Clé</span><span class="sxs-lookup"><span data-stu-id="8ddc2-133">-Key</span></span>

<span data-ttu-id="8ddc2-134">Spécifie la clé de chiffrement en tant que tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-134">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="8ddc2-135">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="8ddc2-135">-SecureKey</span></span>

<span data-ttu-id="8ddc2-136">Spécifie la clé de chiffrement en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-136">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="8ddc2-137">La valeur de chaîne sécurisée est convertie en un tableau d'octets avant d'être utilisée comme clé.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-137">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="8ddc2-138">-SecureString</span><span class="sxs-lookup"><span data-stu-id="8ddc2-138">-SecureString</span></span>

<span data-ttu-id="8ddc2-139">Spécifie la chaîne sécurisée à convertir en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-139">Specifies the secure string to convert to an encrypted standard string.</span></span>

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

### <span data-ttu-id="8ddc2-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ddc2-140">CommonParameters</span></span>

<span data-ttu-id="8ddc2-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ddc2-142">Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8ddc2-142">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ddc2-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8ddc2-143">INPUTS</span></span>

### <span data-ttu-id="8ddc2-144">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="8ddc2-144">System.Security.SecureString</span></span>

<span data-ttu-id="8ddc2-145">Vous pouvez diriger un objet **SecureString** vers ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-145">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="8ddc2-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8ddc2-146">OUTPUTS</span></span>

### <span data-ttu-id="8ddc2-147">System.String</span><span class="sxs-lookup"><span data-stu-id="8ddc2-147">System.String</span></span>

<span data-ttu-id="8ddc2-148">ConvertFrom-SecureString retourne un objet chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-148">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="8ddc2-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8ddc2-149">NOTES</span></span>

- <span data-ttu-id="8ddc2-150">Pour créer une chaîne sécurisée à partir de caractères tapés à l’invite de commandes, utilisez le paramètre **AsSecureString** de l’applet de commande `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="8ddc2-150">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="8ddc2-151">Lorsque vous utilisez les paramètres **Key** ou **SecureKey** pour spécifier une clé, la longueur de la clé doit être correcte.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-151">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="8ddc2-152">Par exemple, une clé de 128 bits peut être spécifiée sous la forme d’un tableau d’octets de 16 chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-152">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="8ddc2-153">De même, les clés 192 bits et 256 bits correspondent aux tableaux d’octets de 24 et 32 chiffres décimaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-153">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="8ddc2-154">Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-154">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="8ddc2-155">Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8ddc2-155">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="8ddc2-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8ddc2-156">RELATED LINKS</span></span>

[<span data-ttu-id="8ddc2-157">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="8ddc2-157">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="8ddc2-158">Read-Host</span><span class="sxs-lookup"><span data-stu-id="8ddc2-158">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

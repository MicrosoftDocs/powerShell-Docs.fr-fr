---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 9dcc79755854cc7b9f1928cfbc5d602632eca3cc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597149"
---
# <span data-ttu-id="f0f62-102">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="f0f62-102">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="f0f62-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f0f62-103">SYNOPSIS</span></span>
<span data-ttu-id="f0f62-104">Convertit une chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="f0f62-104">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="f0f62-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f0f62-105">SYNTAX</span></span>

### <span data-ttu-id="f0f62-106">Sécurisé (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0f62-106">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="f0f62-107">AsPlainText</span><span class="sxs-lookup"><span data-stu-id="f0f62-107">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="f0f62-108">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="f0f62-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="f0f62-109">Description</span><span class="sxs-lookup"><span data-stu-id="f0f62-109">DESCRIPTION</span></span>

<span data-ttu-id="f0f62-110">L’applet de commande **ConvertFrom-SecureString** convertit une chaîne sécurisée (**System. Security. SecureString**) en une chaîne chiffrée standard (**System. String**).</span><span class="sxs-lookup"><span data-stu-id="f0f62-110">The **ConvertFrom-SecureString** cmdlet converts a secure string (**System.Security.SecureString**) into an encrypted standard string (**System.String**).</span></span> <span data-ttu-id="f0f62-111">Contrairement à une chaîne sécurisée, une chaîne chiffrée standard peut être enregistrée dans un fichier pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f0f62-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="f0f62-112">La chaîne standard chiffrée peut être reconvertie dans son format de chaîne sécurisée à l’aide de l’applet de commande `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="f0f62-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="f0f62-113">Si une clé de chiffrement est spécifiée à l'aide des paramètres **Key** ou **SecureKey**, l'algorithme de chiffrement AES (Advanced Encryption Standard) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f0f62-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="f0f62-114">La clé spécifiée doit avoir une longueur égale à 128, 192 ou 256 bits, car ce sont les longueurs de clé prises en charge par l'algorithme de chiffrement AES.</span><span class="sxs-lookup"><span data-stu-id="f0f62-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="f0f62-115">Si aucune clé n'est spécifiée, l'API de protection des données (DPAPI) Windows est utilisée pour chiffrer la représentation de chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="f0f62-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="f0f62-116">Notez que, selon [dotnet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), le contenu d’une SecureString n’est pas chiffré sur les systèmes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="f0f62-116">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="f0f62-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f0f62-117">EXAMPLES</span></span>

### <span data-ttu-id="f0f62-118">Exemple 1 : créer une chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="f0f62-118">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="f0f62-119">Cette commande crée une chaîne sécurisée à partir de caractères que vous tapez à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f0f62-119">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="f0f62-120">Après avoir entré la commande, tapez la chaîne que vous souhaitez stocker en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f0f62-120">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="f0f62-121">Un astérisque ( `*` ) s’affiche pour représenter chaque caractère que vous tapez.</span><span class="sxs-lookup"><span data-stu-id="f0f62-121">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="f0f62-122">Exemple 2 : convertir une chaîne sécurisée en chaîne standard chiffrée</span><span class="sxs-lookup"><span data-stu-id="f0f62-122">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="f0f62-123">Cette commande convertit la chaîne sécurisée dans la `$SecureString` variable en une chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="f0f62-123">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="f0f62-124">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="f0f62-124">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="f0f62-125">Exemple 3 : convertir une chaîne sécurisée en chaîne standard chiffrée avec une clé de 192 bits</span><span class="sxs-lookup"><span data-stu-id="f0f62-125">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="f0f62-126">Ces commandes utilisent l’algorithme Advanced Encryption Standard (AES) pour convertir la chaîne sécurisée stockée dans la `$SecureString` variable en chaîne standard chiffrée avec une clé de 192 bits.</span><span class="sxs-lookup"><span data-stu-id="f0f62-126">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="f0f62-127">La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.</span><span class="sxs-lookup"><span data-stu-id="f0f62-127">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="f0f62-128">La première commande stocke une clé dans la `$Key` variable.</span><span class="sxs-lookup"><span data-stu-id="f0f62-128">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="f0f62-129">La clé est un tableau de 24 chiffres décimaux, chacun d’entre eux devant être inférieur à 256 pour tenir dans un seul octet non signé.</span><span class="sxs-lookup"><span data-stu-id="f0f62-129">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="f0f62-130">Étant donné que chaque chiffre décimal représente un seul octet (8 bits), la clé a 24 chiffres pour un total de 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="f0f62-130">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="f0f62-131">Il s'agit d'une longueur de clé valide pour l'algorithme AES.</span><span class="sxs-lookup"><span data-stu-id="f0f62-131">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="f0f62-132">La deuxième commande utilise la clé de la `$Key` variable pour convertir la chaîne sécurisée en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="f0f62-132">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="f0f62-133">Exemple 4 : convertir directement une chaîne sécurisée en une chaîne de texte en clair</span><span class="sxs-lookup"><span data-stu-id="f0f62-133">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="f0f62-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0f62-134">PARAMETERS</span></span>

### <span data-ttu-id="f0f62-135">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="f0f62-135">-AsPlainText</span></span>

<span data-ttu-id="f0f62-136">Quand `ConvertFrom-SecureString` elle est définie, elle convertit les chaînes sécurisées en une chaîne de texte en clair déchiffrée en sortie.</span><span class="sxs-lookup"><span data-stu-id="f0f62-136">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="f0f62-137">Ce paramètre a été ajouté dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="f0f62-137">This paramater was added in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="f0f62-138">-Key</span><span class="sxs-lookup"><span data-stu-id="f0f62-138">-Key</span></span>

<span data-ttu-id="f0f62-139">Spécifie la clé de chiffrement en tant que tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="f0f62-139">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="f0f62-140">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="f0f62-140">-SecureKey</span></span>

<span data-ttu-id="f0f62-141">Spécifie la clé de chiffrement en tant que chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f0f62-141">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="f0f62-142">La valeur de chaîne sécurisée est convertie en un tableau d'octets avant d'être utilisée comme clé.</span><span class="sxs-lookup"><span data-stu-id="f0f62-142">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="f0f62-143">-SecureString</span><span class="sxs-lookup"><span data-stu-id="f0f62-143">-SecureString</span></span>

<span data-ttu-id="f0f62-144">Spécifie la chaîne sécurisée à convertir en chaîne standard chiffrée.</span><span class="sxs-lookup"><span data-stu-id="f0f62-144">Specifies the secure string to convert to an encrypted standard string.</span></span>

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

### <span data-ttu-id="f0f62-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0f62-145">CommonParameters</span></span>

<span data-ttu-id="f0f62-146">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="f0f62-146">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="f0f62-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0f62-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0f62-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f0f62-148">INPUTS</span></span>

### <span data-ttu-id="f0f62-149">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="f0f62-149">System.Security.SecureString</span></span>

<span data-ttu-id="f0f62-150">Vous pouvez diriger un objet **SecureString** vers ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="f0f62-150">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="f0f62-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f0f62-151">OUTPUTS</span></span>

### <span data-ttu-id="f0f62-152">System.String</span><span class="sxs-lookup"><span data-stu-id="f0f62-152">System.String</span></span>

<span data-ttu-id="f0f62-153">ConvertFrom-SecureString retourne un objet chaîne standard.</span><span class="sxs-lookup"><span data-stu-id="f0f62-153">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="f0f62-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f0f62-154">NOTES</span></span>

- <span data-ttu-id="f0f62-155">Pour créer une chaîne sécurisée à partir de caractères tapés à l’invite de commandes, utilisez le paramètre **AsSecureString** de l’applet de commande `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="f0f62-155">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="f0f62-156">Lorsque vous utilisez les paramètres **Key** ou **SecureKey** pour spécifier une clé, la longueur de la clé doit être correcte.</span><span class="sxs-lookup"><span data-stu-id="f0f62-156">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="f0f62-157">Par exemple, une clé de 128 bits peut être spécifiée sous la forme d’un tableau d’octets de 16 chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="f0f62-157">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="f0f62-158">De même, les clés 192 bits et 256 bits correspondent aux tableaux d’octets de 24 et 32 chiffres décimaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f0f62-158">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="f0f62-159">Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient.</span><span class="sxs-lookup"><span data-stu-id="f0f62-159">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="f0f62-160">Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f0f62-160">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="f0f62-161">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f0f62-161">RELATED LINKS</span></span>

[<span data-ttu-id="f0f62-162">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="f0f62-162">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="f0f62-163">Read-Host</span><span class="sxs-lookup"><span data-stu-id="f0f62-163">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

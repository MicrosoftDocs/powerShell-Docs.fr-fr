---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 6e536681f78a79660e80951d0dcc446fbba32553
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208861"
---
# <span data-ttu-id="7b0e1-103">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="7b0e1-103">ConvertTo-SecureString</span></span>

## <span data-ttu-id="7b0e1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7b0e1-104">SYNOPSIS</span></span>
<span data-ttu-id="7b0e1-105">Convertit des chaînes de texte brut ou chiffrées en chaînes sécurisées.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-105">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="7b0e1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b0e1-106">SYNTAX</span></span>

### <span data-ttu-id="7b0e1-107">Sécurisé (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7b0e1-107">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="7b0e1-108">Texte brut</span><span class="sxs-lookup"><span data-stu-id="7b0e1-108">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="7b0e1-109">Ouvrir</span><span class="sxs-lookup"><span data-stu-id="7b0e1-109">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="7b0e1-110">Description</span><span class="sxs-lookup"><span data-stu-id="7b0e1-110">DESCRIPTION</span></span>

<span data-ttu-id="7b0e1-111">L' `ConvertTo-SecureString` applet de commande convertit les chaînes standard chiffrées en chaînes sécurisées.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-111">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="7b0e1-112">Cette commande peut également convertir du texte brut en chaînes sécurisées.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-112">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="7b0e1-113">Il est utilisé avec `ConvertFrom-SecureString` et `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-113">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="7b0e1-114">La chaîne sécurisée créée par l’applet de commande peut être utilisée avec des applets de commande ou des fonctions qui requièrent un paramètre de type **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-114">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="7b0e1-115">La chaîne sécurisée peut être reconvertie en une chaîne chiffrée standard à l’aide de l’applet de commande `ConvertFrom-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-115">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="7b0e1-116">Cela permet de la stocker dans un fichier pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-116">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="7b0e1-117">Si la chaîne standard en cours de conversion a été chiffrée à `ConvertFrom-SecureString` l’aide d’une clé spécifiée, la même clé doit être fournie comme valeur du paramètre **Key** ou **SecureKey** de l’applet de commande `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-117">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

## <span data-ttu-id="7b0e1-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7b0e1-118">EXAMPLES</span></span>

### <span data-ttu-id="7b0e1-119">Exemple 1 : convertir une chaîne sécurisée en chaîne chiffrée</span><span class="sxs-lookup"><span data-stu-id="7b0e1-119">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="7b0e1-120">Cet exemple montre comment créer une chaîne sécurisée à partir de l'entrée utilisateur, convertir la chaîne sécurisée en chaîne standard chiffrée, puis convertir la chaîne cryptée standard en chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-120">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="7b0e1-121">La première commande utilise le paramètre **AsSecureString** de l' `Read-Host` applet de commande pour créer une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-121">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="7b0e1-122">Une fois que vous avez entré la commande, tous les caractères que vous tapez sont convertis en une chaîne sécurisée, puis enregistrés dans la `$Secure` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-122">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="7b0e1-123">La deuxième commande affiche le contenu de la `$Secure` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-123">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="7b0e1-124">Étant donné que la `$Secure` variable contient une chaîne sécurisée, PowerShell affiche uniquement le type **System. Security. SecureString** .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-124">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="7b0e1-125">La troisième commande utilise l' `ConvertFrom-SecureString` applet de commande pour convertir la chaîne sécurisée dans la `$Secure` variable en une chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-125">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="7b0e1-126">Elle enregistre le résultat dans la `$Encrypted` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-126">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="7b0e1-127">La quatrième commande affiche la chaîne chiffrée dans la valeur de la `$Encrypted` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-127">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="7b0e1-128">La cinquième commande utilise l' `ConvertTo-SecureString` applet de commande pour convertir la chaîne standard chiffrée dans la `$Encrypted` variable en une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-128">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="7b0e1-129">Elle enregistre le résultat dans la `$Secure2` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-129">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="7b0e1-130">La sixième commande affiche la valeur de la `$Secure2` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-130">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="7b0e1-131">Le type SecureString indique que la commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-131">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="7b0e1-132">Exemple 2 : créer une chaîne sécurisée à partir d’une chaîne chiffrée dans un fichier</span><span class="sxs-lookup"><span data-stu-id="7b0e1-132">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="7b0e1-133">Cet exemple montre comment créer une chaîne sécurisée à partir d'une chaîne chiffrée standard qui est enregistrée dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-133">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="7b0e1-134">La première commande utilise le paramètre **AsSecureString** de l' `Read-Host` applet de commande pour créer une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-134">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="7b0e1-135">Une fois que vous avez entré la commande, tous les caractères que vous tapez sont convertis en une chaîne sécurisée, puis enregistrés dans la `$Secure` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-135">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="7b0e1-136">La deuxième commande utilise l' `ConvertFrom-SecureString` applet de commande pour convertir la chaîne sécurisée dans la `$Secure` variable en une chaîne chiffrée standard à l’aide de la clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-136">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="7b0e1-137">Le contenu est enregistré dans la `$Encrypted` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-137">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="7b0e1-138">La troisième commande utilise un opérateur de pipeline ( `|` ) pour envoyer la valeur de la `$Encrypted` variable à l’applet de commande `Set-Content` , qui enregistre la valeur dans le fichier Encrypted.txt.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-138">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="7b0e1-139">La quatrième commande utilise l' `Get-Content` applet de commande pour récupérer la chaîne standard chiffrée dans le fichier Encrypted.txt.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-139">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="7b0e1-140">La commande utilise un opérateur de pipeline pour envoyer la chaîne chiffrée à l’applet de commande `ConvertTo-SecureString` , qui la convertit en une chaîne sécurisée à l’aide de la clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-140">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="7b0e1-141">Les résultats sont enregistrés dans la `$Secure2` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-141">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="7b0e1-142">Exemple 3 : convertir une chaîne de texte brut en chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="7b0e1-142">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="7b0e1-143">Cette commande convertit la chaîne de texte brut `P@ssW0rD!` en une chaîne sécurisée et stocke le résultat dans la `$Secure_String_Pwd` variable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-143">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="7b0e1-144">Pour utiliser le paramètre **AsPlainText** , le paramètre **force** doit également être inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-144">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="7b0e1-145">Vous devez éviter d’utiliser des chaînes de texte brut dans le script ou à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-145">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="7b0e1-146">Le texte brut peut apparaître dans les journaux des événements et les journaux d’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-146">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="7b0e1-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b0e1-147">PARAMETERS</span></span>

### <span data-ttu-id="7b0e1-148">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="7b0e1-148">-AsPlainText</span></span>

<span data-ttu-id="7b0e1-149">Spécifie une chaîne de texte brut à convertir en chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-149">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="7b0e1-150">Les applets de commande de chaîne sécurisée protègent du texte confidentiel.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-150">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="7b0e1-151">Le texte est chiffré pour rester confidentiel et il est supprimé de la mémoire de l'ordinateur après son utilisation.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-151">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="7b0e1-152">Si vous utilisez ce paramètre pour fournir du texte brut en entrée, le système ne peut pas protéger cette entrée de cette manière.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-152">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="7b0e1-153">Pour utiliser ce paramètre, vous devez également spécifier le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-153">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b0e1-154">-Force</span><span class="sxs-lookup"><span data-stu-id="7b0e1-154">-Force</span></span>

<span data-ttu-id="7b0e1-155">Confirme que vous comprenez les implications de l’utilisation du paramètre **AsPlainText** et que vous souhaitez quand même l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-155">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b0e1-156">-Clé</span><span class="sxs-lookup"><span data-stu-id="7b0e1-156">-Key</span></span>

<span data-ttu-id="7b0e1-157">Spécifie la clé de chiffrement utilisée pour convertir la chaîne sécurisée d’origine dans la chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-157">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="7b0e1-158">Les longueurs de clé valides sont 16, 24 et 32 octets.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-158">Valid key lengths are 16, 24 and 32 bytes.</span></span>

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

### <span data-ttu-id="7b0e1-159">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="7b0e1-159">-SecureKey</span></span>

<span data-ttu-id="7b0e1-160">Spécifie la clé de chiffrement utilisée pour convertir la chaîne sécurisée d’origine dans la chaîne chiffrée standard.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-160">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="7b0e1-161">La clé doit être fournie au format d'une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-161">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="7b0e1-162">La chaîne sécurisée est convertie en un tableau d’octets à utiliser comme clé.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-162">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="7b0e1-163">Les longueurs de clé sécurisée valides sont 8, 12 et 16 points de code.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-163">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

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

### <span data-ttu-id="7b0e1-164">-Chaîne</span><span class="sxs-lookup"><span data-stu-id="7b0e1-164">-String</span></span>

<span data-ttu-id="7b0e1-165">Spécifie la chaîne à convertir en chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-165">Specifies the string to convert to a secure string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7b0e1-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b0e1-166">CommonParameters</span></span>

<span data-ttu-id="7b0e1-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b0e1-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7b0e1-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b0e1-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7b0e1-169">INPUTS</span></span>

### <span data-ttu-id="7b0e1-170">System.String</span><span class="sxs-lookup"><span data-stu-id="7b0e1-170">System.String</span></span>

<span data-ttu-id="7b0e1-171">Vous pouvez diriger une chaîne chiffrée standard vers `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-171">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="7b0e1-172">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7b0e1-172">OUTPUTS</span></span>

### <span data-ttu-id="7b0e1-173">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="7b0e1-173">System.Security.SecureString</span></span>

<span data-ttu-id="7b0e1-174">`ConvertTo-SecureString` retourne un objet **SecureString** .</span><span class="sxs-lookup"><span data-stu-id="7b0e1-174">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="7b0e1-175">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7b0e1-175">NOTES</span></span>

<span data-ttu-id="7b0e1-176">Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-176">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="7b0e1-177">Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="7b0e1-177">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="7b0e1-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7b0e1-178">RELATED LINKS</span></span>

[<span data-ttu-id="7b0e1-179">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="7b0e1-179">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="7b0e1-180">Read-Host</span><span class="sxs-lookup"><span data-stu-id="7b0e1-180">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

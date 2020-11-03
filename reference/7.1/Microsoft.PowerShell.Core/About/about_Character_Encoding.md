---
title: about_Character_Encoding
description: Décrit comment PowerShell utilise l’encodage de caractères pour l’entrée et la sortie de données de type chaîne.
ms.date: 10/21/2020
Locale: en-US
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: 6e2f515f774d7bc333baf6346cd6c8bd517cb6fa
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208862"
---
# <a name="about_character_encoding"></a><span data-ttu-id="95bc1-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="95bc1-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="95bc1-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="95bc1-104">Short description</span></span>
<span data-ttu-id="95bc1-105">Décrit comment PowerShell utilise l’encodage de caractères pour l’entrée et la sortie de données de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="95bc1-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="95bc1-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="95bc1-106">Long description</span></span>

<span data-ttu-id="95bc1-107">Unicode est une norme internationale d’encodage de caractères.</span><span class="sxs-lookup"><span data-stu-id="95bc1-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="95bc1-108">Le système utilise uniquement Unicode pour la manipulation de caractères et de chaînes.</span><span class="sxs-lookup"><span data-stu-id="95bc1-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="95bc1-109">Pour obtenir une description détaillée de tous les aspects d’Unicode, reportez-vous à [la norme Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="95bc1-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="95bc1-110">Windows prend en charge les jeux de caractères Unicode et traditionnels.</span><span class="sxs-lookup"><span data-stu-id="95bc1-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="95bc1-111">Les jeux de caractères traditionnels, tels que les pages de codes Windows, utilisent des valeurs 8 bits ou des combinaisons de valeurs 8 bits pour représenter les caractères utilisés dans une langue spécifique ou des paramètres de région géographique.</span><span class="sxs-lookup"><span data-stu-id="95bc1-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="95bc1-112">PowerShell utilise un jeu de caractères Unicode par défaut.</span><span class="sxs-lookup"><span data-stu-id="95bc1-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="95bc1-113">Toutefois, plusieurs applets de commande ont un paramètre d' **encodage** qui peut spécifier l’encodage d’un jeu de caractères différent.</span><span class="sxs-lookup"><span data-stu-id="95bc1-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="95bc1-114">Ce paramètre vous permet de choisir l’encodage de caractères spécifique dont vous avez besoin pour l’interopérabilité avec d’autres systèmes et applications.</span><span class="sxs-lookup"><span data-stu-id="95bc1-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="95bc1-115">Les applets de commande suivantes ont le paramètre **Encoding** :</span><span class="sxs-lookup"><span data-stu-id="95bc1-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="95bc1-116">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="95bc1-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="95bc1-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="95bc1-117">Add-Content</span></span>
  - <span data-ttu-id="95bc1-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="95bc1-118">Get-Content</span></span>
  - <span data-ttu-id="95bc1-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="95bc1-119">Set-Content</span></span>
- <span data-ttu-id="95bc1-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="95bc1-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="95bc1-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="95bc1-121">Export-Clixml</span></span>
  - <span data-ttu-id="95bc1-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="95bc1-122">Export-Csv</span></span>
  - <span data-ttu-id="95bc1-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="95bc1-123">Export-PSSession</span></span>
  - <span data-ttu-id="95bc1-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="95bc1-124">Format-Hex</span></span>
  - <span data-ttu-id="95bc1-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="95bc1-125">Import-Csv</span></span>
  - <span data-ttu-id="95bc1-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="95bc1-126">Out-File</span></span>
  - <span data-ttu-id="95bc1-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="95bc1-127">Select-String</span></span>
  - <span data-ttu-id="95bc1-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="95bc1-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="95bc1-129">Marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="95bc1-129">The byte-order-mark</span></span>

<span data-ttu-id="95bc1-130">La marque d’ordre d’octet (BOM) est une _signature Unicode_ dans les premiers octets d’un fichier ou d’un flux de texte qui indique l’encodage Unicode utilisé pour les données.</span><span class="sxs-lookup"><span data-stu-id="95bc1-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="95bc1-131">Pour plus d’informations, consultez l’article [marque d’ordre d’octet](https://wikipedia.org/wiki/Byte_order_mark) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="95bc1-131">For more information, see the [Byte order mark](https://wikipedia.org/wiki/Byte_order_mark) article in Wikipedia.</span></span>

<span data-ttu-id="95bc1-132">Dans Windows PowerShell, tout encodage Unicode, à l’exception de `UTF7` , crée toujours une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="95bc1-133">PowerShell Core a pour valeur par défaut `utf8NoBOM` pour toute la sortie de texte.</span><span class="sxs-lookup"><span data-stu-id="95bc1-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="95bc1-134">Pour une compatibilité générale optimale, évitez d’utiliser des nomenclatures dans des fichiers UTF-8.</span><span class="sxs-lookup"><span data-stu-id="95bc1-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="95bc1-135">Les plateformes UNIX et les utilitaires Unix-Heritage utilisés sur les plates-formes Windows ne prennent pas en charge les nomenclatures.</span><span class="sxs-lookup"><span data-stu-id="95bc1-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="95bc1-136">De même, l' `UTF7` encodage doit être évité.</span><span class="sxs-lookup"><span data-stu-id="95bc1-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="95bc1-137">UTF-7 n’est pas un encodage Unicode standard et il est écrit sans une nomenclature dans toutes les versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95bc1-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="95bc1-138">La création de scripts PowerShell sur une plateforme de type UNIX ou l’utilisation d’un éditeur multiplateforme sur Windows, par exemple Visual Studio Code, entraîne l’encodage d’un fichier à l’aide de `UTF8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="95bc1-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="95bc1-139">Ces fichiers fonctionnent correctement sur PowerShell Core, mais peuvent s’arrêter dans Windows PowerShell si le fichier contient des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="95bc1-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="95bc1-140">Si vous devez utiliser des caractères non-ASCII dans vos scripts, enregistrez-les au format UTF-8 avec BOM.</span><span class="sxs-lookup"><span data-stu-id="95bc1-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="95bc1-141">Sans la nomenclature, Windows PowerShell interprète votre script comme étant encodé dans la page de codes « ANSI » héritée.</span><span class="sxs-lookup"><span data-stu-id="95bc1-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="95bc1-142">À l’inverse, les fichiers qui ont la nomenclature UTF-8 peuvent être problématiques sur les plateformes de type UNIX.</span><span class="sxs-lookup"><span data-stu-id="95bc1-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="95bc1-143">De nombreux outils Unix, tels que `cat` ,, `sed` `awk` , et certains éditeurs, tels que, `gedit` ne savent pas comment traiter la nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="95bc1-144">Encodage de caractères dans Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95bc1-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="95bc1-145">Dans PowerShell 5,1, le paramètre **Encoding** prend en charge les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="95bc1-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="95bc1-146">`Ascii` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="95bc1-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="95bc1-147">`BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="95bc1-148">`BigEndianUTF32` Utilise UTF-32 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="95bc1-149">`Byte` Encode un jeu de caractères en une séquence d’octets.</span><span class="sxs-lookup"><span data-stu-id="95bc1-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="95bc1-150">`Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).</span><span class="sxs-lookup"><span data-stu-id="95bc1-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="95bc1-151">`Oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="95bc1-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="95bc1-152">`String` Identique à `Unicode`.</span><span class="sxs-lookup"><span data-stu-id="95bc1-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="95bc1-153">`Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="95bc1-154">`Unknown` Identique à `Unicode`.</span><span class="sxs-lookup"><span data-stu-id="95bc1-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="95bc1-155">`UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="95bc1-156">`UTF7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="95bc1-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="95bc1-157">`UTF8` Utilise UTF-8 (avec BOM).</span><span class="sxs-lookup"><span data-stu-id="95bc1-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="95bc1-158">En général, Windows PowerShell utilise l’encodage Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) par défaut.</span><span class="sxs-lookup"><span data-stu-id="95bc1-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="95bc1-159">Toutefois, l’encodage par défaut utilisé par les applets de commande dans Windows PowerShell n’est pas cohérent.</span><span class="sxs-lookup"><span data-stu-id="95bc1-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="95bc1-160">À l’aide de n’importe quel encodage Unicode, à l’exception de `UTF7` , crée toujours une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="95bc1-161">Pour les applets de commande qui écrivent la sortie dans des fichiers :</span><span class="sxs-lookup"><span data-stu-id="95bc1-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="95bc1-162">`Out-File` et les opérateurs de redirection `>` et `>>` créent UTF-16LE, qui diffèrent notamment de `Set-Content` et `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="95bc1-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="95bc1-163">`New-ModuleManifest` et `Export-CliXml` créent également des fichiers UTF-16LE.</span><span class="sxs-lookup"><span data-stu-id="95bc1-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="95bc1-164">Lorsque le fichier cible est vide ou n’existe pas, `Set-Content` et `Add-Content` Utilisez l' `Default` encodage.</span><span class="sxs-lookup"><span data-stu-id="95bc1-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="95bc1-165">`Default` est l’encodage spécifié par la page de codes ANSI héritée des paramètres régionaux du système.</span><span class="sxs-lookup"><span data-stu-id="95bc1-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="95bc1-166">`Export-Csv` crée des `Ascii` fichiers, mais utilise un encodage différent lors de l’utilisation du paramètre **Append** (voir ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="95bc1-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="95bc1-167">`Export-PSSession` crée des fichiers UTF-8 avec BOM par défaut.</span><span class="sxs-lookup"><span data-stu-id="95bc1-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="95bc1-168">`New-Item -Type File -Value` crée un fichier UTF-8 sans marque de nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="95bc1-169">`Send-MailMessage` utilise `Default` l’encodage par défaut.</span><span class="sxs-lookup"><span data-stu-id="95bc1-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="95bc1-170">`Start-Transcript` crée `Utf8` des fichiers avec une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="95bc1-171">Lorsque le paramètre **Append** est utilisé, l’encodage peut être différent (voir ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="95bc1-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="95bc1-172">Pour les commandes qui ajoutent à un fichier existant :</span><span class="sxs-lookup"><span data-stu-id="95bc1-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="95bc1-173">`Out-File -Append` et l' `>>` opérateur de redirection n’essaient pas de mettre en correspondance l’encodage du contenu du fichier cible existant.</span><span class="sxs-lookup"><span data-stu-id="95bc1-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="95bc1-174">Au lieu de cela, ils utilisent l’encodage par défaut, sauf si le paramètre d' **encodage** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="95bc1-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="95bc1-175">Vous devez utiliser l’encodage d’origine des fichiers lors de l’ajout de contenu.</span><span class="sxs-lookup"><span data-stu-id="95bc1-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="95bc1-176">En l’absence d’un paramètre d' **encodage** explicite, `Add-Content` détecte l’encodage existant et l’applique automatiquement au nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="95bc1-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="95bc1-177">Si le contenu existant n’a pas de nomenclature, l' `Default` encodage ANSI est utilisé.</span><span class="sxs-lookup"><span data-stu-id="95bc1-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="95bc1-178">Le comportement de `Add-Content` est le même dans PowerShell Core (V6 et versions ultérieures), sauf que l’encodage par défaut est `Utf8` .</span><span class="sxs-lookup"><span data-stu-id="95bc1-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="95bc1-179">`Export-Csv -Append` correspond à l’encodage existant lorsque le fichier cible contient une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="95bc1-180">En l’absence de nomenclature, il utilise l' `Utf8` encodage.</span><span class="sxs-lookup"><span data-stu-id="95bc1-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="95bc1-181">`Start-Transcript -Append` correspond à l’encodage existant des fichiers qui incluent une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="95bc1-182">En l’absence de nomenclature, l’encodage est utilisé par défaut `Ascii` .</span><span class="sxs-lookup"><span data-stu-id="95bc1-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="95bc1-183">Cet encodage peut entraîner une perte de données ou une altération des caractères lorsque les données de la transcription contiennent des caractères multioctets.</span><span class="sxs-lookup"><span data-stu-id="95bc1-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="95bc1-184">Pour les applets de commande qui lisent les données de chaîne en l’absence d’une nomenclature :</span><span class="sxs-lookup"><span data-stu-id="95bc1-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="95bc1-185">`Get-Content` et `Import-PowerShellDataFile` utilise l' `Default` encodage ANSI.</span><span class="sxs-lookup"><span data-stu-id="95bc1-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="95bc1-186">ANSI est également ce que le moteur PowerShell utilise lorsqu’il lit le code source à partir de fichiers.</span><span class="sxs-lookup"><span data-stu-id="95bc1-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="95bc1-187">`Import-Csv`, `Import-CliXml` et `Select-String` supposent `Utf8` en l’absence d’une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="95bc1-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="95bc1-188">Encodage de caractères dans PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="95bc1-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="95bc1-189">Dans PowerShell Core (V6 et versions ultérieures), le paramètre **Encoding** prend en charge les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="95bc1-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="95bc1-190">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="95bc1-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="95bc1-191">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="95bc1-192">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="95bc1-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="95bc1-193">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="95bc1-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="95bc1-194">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="95bc1-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="95bc1-195">`utf8`: Encode au format UTF-8 (sans BOM).</span><span class="sxs-lookup"><span data-stu-id="95bc1-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="95bc1-196">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="95bc1-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="95bc1-197">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="95bc1-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="95bc1-198">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="95bc1-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="95bc1-199">PowerShell Core a pour valeur par défaut `utf8NoBOM` pour toutes les sorties.</span><span class="sxs-lookup"><span data-stu-id="95bc1-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="95bc1-200">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="95bc1-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="95bc1-201">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage).</span><span class="sxs-lookup"><span data-stu-id="95bc1-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="95bc1-202">Modification de l’encodage par défaut</span><span class="sxs-lookup"><span data-stu-id="95bc1-202">Changing the default encoding</span></span>

<span data-ttu-id="95bc1-203">PowerShell a deux variables par défaut qui peuvent être utilisées pour modifier le comportement d’encodage par défaut.</span><span class="sxs-lookup"><span data-stu-id="95bc1-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="95bc1-204">Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="95bc1-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="95bc1-205">À compter de PowerShell 5,1, les opérateurs de redirection ( `>` et `>>` ) appellent l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="95bc1-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="95bc1-206">Par conséquent, vous pouvez définir l’encodage par défaut à l’aide de la `$PSDefaultParameterValues` variable de préférence, comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="95bc1-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="95bc1-207">Utilisez l’instruction suivante pour modifier l’encodage par défaut pour toutes les applets de commande qui ont le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="95bc1-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="95bc1-208">Le fait de placer cette commande dans votre profil PowerShell fait de la préférence un paramètre de session global qui affecte l’ensemble des commandes et des scripts qui ne spécifient pas explicitement un encodage.</span><span class="sxs-lookup"><span data-stu-id="95bc1-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="95bc1-209">De même, vous devez inclure de telles commandes dans vos scripts ou modules que vous souhaitez adopter de la même façon.</span><span class="sxs-lookup"><span data-stu-id="95bc1-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="95bc1-210">L’utilisation de ces commandes garantit que les applets de commande se comportent de la même façon, même lorsqu’elles sont exécutées par un autre utilisateur, sur un autre ordinateur ou dans une version différente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95bc1-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="95bc1-211">La variable automatique `$OutputEncoding` affecte l’encodage utilisé par PowerShell pour communiquer avec les programmes externes.</span><span class="sxs-lookup"><span data-stu-id="95bc1-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="95bc1-212">Elle n’a aucun effet sur l’encodage utilisé par les opérateurs de redirection de sortie et les applets de commande PowerShell pour enregistrer dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="95bc1-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="95bc1-213">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95bc1-213">See also</span></span>

- [<span data-ttu-id="95bc1-214">Présentation de l’encodage de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="95bc1-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="95bc1-215">Pages de codes-applications Win32</span><span class="sxs-lookup"><span data-stu-id="95bc1-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="95bc1-216">La norme Unicode</span><span class="sxs-lookup"><span data-stu-id="95bc1-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="95bc1-217">Encoding. CodePage</span><span class="sxs-lookup"><span data-stu-id="95bc1-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="95bc1-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="95bc1-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="95bc1-219">Marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="95bc1-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="95bc1-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="95bc1-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)

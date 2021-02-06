---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: a45e7919b5a24189ca7f50661795ff035c38a037
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596308"
---
# <span data-ttu-id="9c588-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="9c588-102">Format-Hex</span></span>

## <span data-ttu-id="9c588-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9c588-103">SYNOPSIS</span></span>

<span data-ttu-id="9c588-104">Affiche un fichier ou une autre entrée au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="9c588-104">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="9c588-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="9c588-105">SYNTAX</span></span>

### <span data-ttu-id="9c588-106">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="9c588-106">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="9c588-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c588-107">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="9c588-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="9c588-108">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="9c588-109">Description</span><span class="sxs-lookup"><span data-stu-id="9c588-109">DESCRIPTION</span></span>

<span data-ttu-id="9c588-110">L' `Format-Hex` applet de commande affiche un fichier ou une autre entrée sous forme de valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="9c588-110">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="9c588-111">Pour déterminer le décalage d’un caractère à partir de la sortie, ajoutez le nombre situé à l’extrême gauche de la ligne au nombre situé en haut de la colonne pour ce caractère.</span><span class="sxs-lookup"><span data-stu-id="9c588-111">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="9c588-112">L' `Format-Hex` applet de commande peut vous aider à déterminer le type de fichier d’un fichier endommagé ou d’un fichier qui n’a peut-être pas une extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="9c588-112">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="9c588-113">Vous pouvez exécuter cette applet de commande, puis lire la sortie hexadécimale pour obtenir des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="9c588-113">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="9c588-114">Lors de l’utilisation `Format-Hex` de sur un fichier, l’applet de commande ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les caractères de saut de ligne conservés.</span><span class="sxs-lookup"><span data-stu-id="9c588-114">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="9c588-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9c588-115">EXAMPLES</span></span>

### <span data-ttu-id="9c588-116">Exemple 1 : obtenir la représentation hexadécimale d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="9c588-116">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="9c588-117">Cette commande retourne les valeurs hexadécimales d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c588-117">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="9c588-118">La chaîne **Hello World** est envoyée à l’applet de commande via le pipeline `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="9c588-118">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="9c588-119">La sortie hexadécimale de `Format-Hex` indique les valeurs de chaque caractère de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c588-119">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="9c588-120">Exemple 2 : Rechercher un type de fichier à partir d’une sortie hexadécimale</span><span class="sxs-lookup"><span data-stu-id="9c588-120">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="9c588-121">Cet exemple utilise la sortie hexadécimale pour déterminer le type de fichier.</span><span class="sxs-lookup"><span data-stu-id="9c588-121">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="9c588-122">L’applet de commande affiche le chemin d’accès complet du fichier et les valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="9c588-122">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="9c588-123">Pour tester la commande suivante, effectuez une copie d’un fichier PDF existant sur votre ordinateur local et renommez le fichier copié `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="9c588-123">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="9c588-124">L' `Format-Hex` applet de commande utilise le paramètre **path** pour spécifier un nom de fichier dans le répertoire actif, `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="9c588-124">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="9c588-125">L’extension de fichier `.t7f` est rare, mais la sortie hexadécimale `%PDF` indique qu’il s’agit d’un fichier PDF.</span><span class="sxs-lookup"><span data-stu-id="9c588-125">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="9c588-126">Dans cet exemple, le paramètre **Count** est utilisé pour limiter la sortie aux 48 premiers octets du fichier.</span><span class="sxs-lookup"><span data-stu-id="9c588-126">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="9c588-127">Exemple 3 : mettre en forme un tableau de types de données différents</span><span class="sxs-lookup"><span data-stu-id="9c588-127">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="9c588-128">Cet exemple utilise un tableau de types de données différents pour mettre `Format-Hex` en évidence comment les gère dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="9c588-128">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="9c588-129">Il passera chaque objet via le pipeline et le processus individuellement.</span><span class="sxs-lookup"><span data-stu-id="9c588-129">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="9c588-130">Toutefois, s’il s’agit de données numériques et que l’objet adjacent est également numérique, il les regroupe dans un bloc de sortie unique.</span><span class="sxs-lookup"><span data-stu-id="9c588-130">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="9c588-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c588-131">PARAMETERS</span></span>

### <span data-ttu-id="9c588-132">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9c588-132">-Encoding</span></span>

<span data-ttu-id="9c588-133">Spécifie l’encodage des chaînes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9c588-133">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="9c588-134">Cela s’applique uniquement à l' `[string]` entrée.</span><span class="sxs-lookup"><span data-stu-id="9c588-134">This only applies to `[string]` input.</span></span> <span data-ttu-id="9c588-135">Le paramètre n’a aucun effet sur les types numériques.</span><span class="sxs-lookup"><span data-stu-id="9c588-135">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="9c588-136">La valeur de sortie est toujours `utf8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="9c588-136">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="9c588-137">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c588-137">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9c588-138">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="9c588-138">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9c588-139">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="9c588-139">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9c588-140">`bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="9c588-140">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9c588-141">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="9c588-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="9c588-142">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="9c588-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="9c588-143">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="9c588-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="9c588-144">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9c588-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="9c588-145">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="9c588-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9c588-146">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="9c588-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9c588-147">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="9c588-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="9c588-148">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="9c588-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="9c588-149">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="9c588-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="9c588-150">**UTF-7** _ n’est plus recommandé pour l’utilisation de.</span><span class="sxs-lookup"><span data-stu-id="9c588-150">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="9c588-151">Dans PowerShell 7,1, un avertissement est écrit si vous spécifiez `utf7` pour le paramètre _ \*Encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="9c588-151">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9c588-152">-InputObject</span></span>

<span data-ttu-id="9c588-153">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="9c588-153">Used for pipeline input.</span></span> <span data-ttu-id="9c588-154">L’entrée de pipeline prend en charge uniquement certains types scalaires et `[system.io.fileinfo]` instances pour le canalisation à partir de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="9c588-154">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="9c588-155">Les types scalaires pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="9c588-155">The supported scalar types are:</span></span>

- <span data-ttu-id="9c588-156">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="9c588-156">`[string]`, `[char]`</span></span>
- <span data-ttu-id="9c588-157">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="9c588-157">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="9c588-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="9c588-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="9c588-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="9c588-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="9c588-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="9c588-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="9c588-161">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="9c588-161">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="9c588-162">Avant PowerShell 6,2, `Format-Hex` gérerait une entrée de pipeline avec plusieurs types d’entrée en regroupant tous les objets similaires.</span><span class="sxs-lookup"><span data-stu-id="9c588-162">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="9c588-163">À présent, il traite chaque objet individuel lorsqu’il passe par le pipeline et ne regroupe pas les objets, sauf si les objets like sont adjacents.</span><span class="sxs-lookup"><span data-stu-id="9c588-163">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c588-164">-LiteralPath</span></span>

<span data-ttu-id="9c588-165">Spécifie le chemin d’accès complet à un fichier.</span><span class="sxs-lookup"><span data-stu-id="9c588-165">Specifies the complete path to a file.</span></span> <span data-ttu-id="9c588-166">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="9c588-166">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="9c588-167">Ce paramètre n’accepte pas les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="9c588-167">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="9c588-168">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="9c588-168">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="9c588-169">Si le paramètre **LiteralPath** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="9c588-169">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="9c588-170">PowerShell n’interprète pas les caractères d’une chaîne entre guillemets simples comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="9c588-170">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="9c588-171">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="9c588-171">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-172">-Path</span><span class="sxs-lookup"><span data-stu-id="9c588-172">-Path</span></span>

<span data-ttu-id="9c588-173">Spécifie le chemin d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="9c588-173">Specifies the path to files.</span></span> <span data-ttu-id="9c588-174">Utilisez un point ( `.` ) pour spécifier l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="9c588-174">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="9c588-175">Le caractère générique ( `*` ) est accepté et peut être utilisé pour spécifier tous les éléments d’un emplacement.</span><span class="sxs-lookup"><span data-stu-id="9c588-175">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="9c588-176">Si le paramètre **path** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="9c588-176">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="9c588-177">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="9c588-177">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9c588-178">-RAW</span><span class="sxs-lookup"><span data-stu-id="9c588-178">-Raw</span></span>

<span data-ttu-id="9c588-179">Ce paramètre n’effectue plus aucune action.</span><span class="sxs-lookup"><span data-stu-id="9c588-179">This parameter no longer does anything.</span></span> <span data-ttu-id="9c588-180">Elle est conservée pour la compatibilité de script.</span><span class="sxs-lookup"><span data-stu-id="9c588-180">It is retained for script compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-181">-Offset</span><span class="sxs-lookup"><span data-stu-id="9c588-181">-Offset</span></span>

<span data-ttu-id="9c588-182">Cela représente le nombre d’octets à ignorer pour faire partie de la sortie hex.</span><span class="sxs-lookup"><span data-stu-id="9c588-182">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="9c588-183">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="9c588-183">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-184">-Nombre</span><span class="sxs-lookup"><span data-stu-id="9c588-184">-Count</span></span>

<span data-ttu-id="9c588-185">Cela représente le nombre d’octets à inclure dans la sortie hex.</span><span class="sxs-lookup"><span data-stu-id="9c588-185">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="9c588-186">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="9c588-186">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c588-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c588-187">CommonParameters</span></span>

<span data-ttu-id="9c588-188">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c588-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c588-189">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9c588-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c588-190">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9c588-190">INPUTS</span></span>

### <span data-ttu-id="9c588-191">System.String</span><span class="sxs-lookup"><span data-stu-id="9c588-191">System.String</span></span>

<span data-ttu-id="9c588-192">Vous pouvez diriger une chaîne vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9c588-192">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="9c588-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9c588-193">OUTPUTS</span></span>

### <span data-ttu-id="9c588-194">Microsoft. PowerShell. Commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="9c588-194">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="9c588-195">Cette applet de commande retourne un **ByteCollection**.</span><span class="sxs-lookup"><span data-stu-id="9c588-195">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="9c588-196">Cet objet représente une collection d’octets.</span><span class="sxs-lookup"><span data-stu-id="9c588-196">This object represents a collection of bytes.</span></span> <span data-ttu-id="9c588-197">Il comprend des méthodes qui convertissent la collection d’octets en une chaîne mise en forme comme chaque ligne de sortie retournée par `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="9c588-197">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="9c588-198">La sortie indique également qu’il s’agit d’un type d’octets en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="9c588-198">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="9c588-199">Si vous spécifiez le **chemin d’accès** ou le paramètre **LiteralPath** , l’objet contient le chemin d’accès du fichier qui contient chaque octet.</span><span class="sxs-lookup"><span data-stu-id="9c588-199">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="9c588-200">Si vous transmettez une chaîne, une valeur booléenne, un entier, etc., elle est étiquetée de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="9c588-200">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="9c588-201">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9c588-201">NOTES</span></span>

<span data-ttu-id="9c588-202">La colonne la plus à droite de la sortie tente de restituer les octets sous forme de caractères ASCII :</span><span class="sxs-lookup"><span data-stu-id="9c588-202">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="9c588-203">En règle générale, chaque octet est interprété comme un point de code Unicode, ce qui signifie que :</span><span class="sxs-lookup"><span data-stu-id="9c588-203">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="9c588-204">Les caractères ASCII imprimables sont toujours restitués correctement</span><span class="sxs-lookup"><span data-stu-id="9c588-204">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="9c588-205">Les caractères UTF-8 codés sur plusieurs octets ne s’affichent pas correctement</span><span class="sxs-lookup"><span data-stu-id="9c588-205">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="9c588-206">Les caractères UTF-16 s’affichent correctement uniquement si leur octet de poids fort se produit `NUL` .</span><span class="sxs-lookup"><span data-stu-id="9c588-206">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="9c588-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9c588-207">RELATED LINKS</span></span>

[<span data-ttu-id="9c588-208">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="9c588-208">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="9c588-209">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="9c588-209">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="9c588-210">Format-List</span><span class="sxs-lookup"><span data-stu-id="9c588-210">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="9c588-211">Format-Table</span><span class="sxs-lookup"><span data-stu-id="9c588-211">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="9c588-212">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="9c588-212">Format-Wide</span></span>](Format-Wide.md)


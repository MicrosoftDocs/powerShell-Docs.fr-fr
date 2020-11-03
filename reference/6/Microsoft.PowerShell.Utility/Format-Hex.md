---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204649"
---
# <span data-ttu-id="e813c-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="e813c-103">Format-Hex</span></span>

## <span data-ttu-id="e813c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e813c-104">SYNOPSIS</span></span>

<span data-ttu-id="e813c-105">Affiche un fichier ou une autre entrée au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="e813c-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="e813c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e813c-106">SYNTAX</span></span>

### <span data-ttu-id="e813c-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e813c-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="e813c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e813c-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="e813c-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="e813c-109">InputObject</span></span>

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="e813c-110">Description</span><span class="sxs-lookup"><span data-stu-id="e813c-110">DESCRIPTION</span></span>

<span data-ttu-id="e813c-111">L' `Format-Hex` applet de commande affiche un fichier ou une autre entrée sous forme de valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="e813c-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="e813c-112">Pour déterminer le décalage d’un caractère à partir de la sortie, ajoutez le nombre situé à l’extrême gauche de la ligne au nombre situé en haut de la colonne pour ce caractère.</span><span class="sxs-lookup"><span data-stu-id="e813c-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="e813c-113">L' `Format-Hex` applet de commande peut vous aider à déterminer le type de fichier d’un fichier endommagé ou d’un fichier qui n’a peut-être pas une extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e813c-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="e813c-114">Vous pouvez exécuter cette applet de commande, puis lire la sortie hexadécimale pour obtenir des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="e813c-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="e813c-115">Lors de l’utilisation `Format-Hex` de sur un fichier, l’applet de commande ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les caractères de saut de ligne conservés.</span><span class="sxs-lookup"><span data-stu-id="e813c-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="e813c-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e813c-116">EXAMPLES</span></span>

### <span data-ttu-id="e813c-117">Exemple 1 : obtenir la représentation hexadécimale d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="e813c-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="e813c-118">Cette commande retourne les valeurs hexadécimales d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e813c-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="e813c-119">La chaîne **Hello World** est envoyée à l’applet de commande via le pipeline `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="e813c-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="e813c-120">La sortie hexadécimale de `Format-Hex` indique les valeurs de chaque caractère de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e813c-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="e813c-121">Exemple 2 : Rechercher un type de fichier à partir d’une sortie hexadécimale</span><span class="sxs-lookup"><span data-stu-id="e813c-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="e813c-122">Cet exemple utilise la sortie hexadécimale pour déterminer le type de fichier.</span><span class="sxs-lookup"><span data-stu-id="e813c-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="e813c-123">L’applet de commande affiche le chemin d’accès complet du fichier et les valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="e813c-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="e813c-124">Pour tester la commande suivante, effectuez une copie d’un fichier PDF existant sur votre ordinateur local et renommez le fichier copié `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="e813c-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

<span data-ttu-id="e813c-125">L' `Format-Hex` applet de commande utilise le paramètre **path** pour spécifier un nom de fichier dans le répertoire actif, **file. T7f** .</span><span class="sxs-lookup"><span data-stu-id="e813c-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, **File.t7f** .</span></span> <span data-ttu-id="e813c-126">L’extension de fichier **. T7f** est rare, mais la sortie hexadécimale **% PDF** indique qu’il s’agit d’un fichier PDF.</span><span class="sxs-lookup"><span data-stu-id="e813c-126">The file extension **.t7f** is uncommon, but the hexadecimal output **%PDF** shows that it is a PDF file.</span></span>

## <span data-ttu-id="e813c-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e813c-127">PARAMETERS</span></span>

### <span data-ttu-id="e813c-128">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e813c-128">-Encoding</span></span>

<span data-ttu-id="e813c-129">Spécifie l’encodage de la sortie.</span><span class="sxs-lookup"><span data-stu-id="e813c-129">Specifies the encoding of the output.</span></span> <span data-ttu-id="e813c-130">Cela s’applique uniquement à l' `[string]` entrée.</span><span class="sxs-lookup"><span data-stu-id="e813c-130">This only applies to `[string]` input.</span></span> <span data-ttu-id="e813c-131">Le paramètre n’a aucun effet sur les types numériques.</span><span class="sxs-lookup"><span data-stu-id="e813c-131">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="e813c-132">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="e813c-132">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="e813c-133">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e813c-133">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e813c-134">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="e813c-134">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e813c-135">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="e813c-135">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e813c-136">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="e813c-136">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="e813c-137">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="e813c-137">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="e813c-138">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="e813c-138">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="e813c-139">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e813c-139">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="e813c-140">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="e813c-140">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e813c-141">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="e813c-141">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e813c-142">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="e813c-142">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="e813c-143">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="e813c-143">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="e813c-144">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="e813c-144">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e813c-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e813c-145">-InputObject</span></span>

<span data-ttu-id="e813c-146">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="e813c-146">Used for pipeline input.</span></span> <span data-ttu-id="e813c-147">L’entrée de pipeline prend en charge uniquement certains types scalaires et `[system.io.fileinfo]` instances pour le canalisation à partir de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="e813c-147">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="e813c-148">Les types scalaires pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="e813c-148">The supported scalar types are:</span></span>

- <span data-ttu-id="e813c-149">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="e813c-149">`[string]`, `[char]`</span></span>
- <span data-ttu-id="e813c-150">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="e813c-150">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="e813c-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="e813c-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="e813c-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="e813c-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="e813c-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="e813c-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="e813c-154">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="e813c-154">`[single]`, `[float]`, `[double]`</span></span>

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

### <span data-ttu-id="e813c-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e813c-155">-LiteralPath</span></span>

<span data-ttu-id="e813c-156">Spécifie le chemin d’accès complet à un fichier.</span><span class="sxs-lookup"><span data-stu-id="e813c-156">Specifies the complete path to a file.</span></span> <span data-ttu-id="e813c-157">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="e813c-157">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="e813c-158">Ce paramètre n’accepte pas les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="e813c-158">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="e813c-159">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e813c-159">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="e813c-160">Si le paramètre **LiteralPath** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e813c-160">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="e813c-161">PowerShell n’interprète pas les caractères d’une chaîne entre guillemets simples comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="e813c-161">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="e813c-162">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="e813c-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="e813c-163">-Path</span><span class="sxs-lookup"><span data-stu-id="e813c-163">-Path</span></span>

<span data-ttu-id="e813c-164">Spécifie le chemin d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="e813c-164">Specifies the path to files.</span></span> <span data-ttu-id="e813c-165">Utilisez un point ( `.` ) pour spécifier l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="e813c-165">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="e813c-166">Le caractère générique ( `*` ) est accepté et peut être utilisé pour spécifier tous les éléments d’un emplacement.</span><span class="sxs-lookup"><span data-stu-id="e813c-166">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="e813c-167">Si le paramètre **path** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e813c-167">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="e813c-168">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e813c-168">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="e813c-169">-RAW</span><span class="sxs-lookup"><span data-stu-id="e813c-169">-Raw</span></span>

<span data-ttu-id="e813c-170">Ce paramètre n’effectue plus aucune action.</span><span class="sxs-lookup"><span data-stu-id="e813c-170">This parameter no longer does anything.</span></span> <span data-ttu-id="e813c-171">Elle est conservée pour la compatibilité de script.</span><span class="sxs-lookup"><span data-stu-id="e813c-171">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="e813c-172">-Offset</span><span class="sxs-lookup"><span data-stu-id="e813c-172">-Offset</span></span>

<span data-ttu-id="e813c-173">Cela représente le nombre d’octets à ignorer pour faire partie de la sortie hex.</span><span class="sxs-lookup"><span data-stu-id="e813c-173">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="e813c-174">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="e813c-174">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="e813c-175">-Nombre</span><span class="sxs-lookup"><span data-stu-id="e813c-175">-Count</span></span>

<span data-ttu-id="e813c-176">Cela représente le nombre d’octets à inclure dans la sortie hex.</span><span class="sxs-lookup"><span data-stu-id="e813c-176">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="e813c-177">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="e813c-177">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="e813c-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e813c-178">CommonParameters</span></span>

<span data-ttu-id="e813c-179">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e813c-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e813c-180">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e813c-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e813c-181">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e813c-181">INPUTS</span></span>

### <span data-ttu-id="e813c-182">System.String</span><span class="sxs-lookup"><span data-stu-id="e813c-182">System.String</span></span>

<span data-ttu-id="e813c-183">Vous pouvez diriger une chaîne vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e813c-183">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="e813c-184">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e813c-184">OUTPUTS</span></span>

### <span data-ttu-id="e813c-185">Microsoft. PowerShell. Commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="e813c-185">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="e813c-186">Cette applet de commande retourne un **ByteCollection** .</span><span class="sxs-lookup"><span data-stu-id="e813c-186">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="e813c-187">Cet objet représente une collection d’octets.</span><span class="sxs-lookup"><span data-stu-id="e813c-187">This object represents a collection of bytes.</span></span> <span data-ttu-id="e813c-188">Il comprend des méthodes qui convertissent la collection d’octets en une chaîne mise en forme comme chaque ligne de sortie retournée par `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="e813c-188">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="e813c-189">Si vous spécifiez le **chemin d’accès** ou le paramètre **LiteralPath** , l’objet contient également le chemin d’accès du fichier qui contient chaque octet.</span><span class="sxs-lookup"><span data-stu-id="e813c-189">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="e813c-190">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e813c-190">NOTES</span></span>

<span data-ttu-id="e813c-191">La colonne la plus à droite de la sortie tente de restituer les octets sous forme de caractères ASCII :</span><span class="sxs-lookup"><span data-stu-id="e813c-191">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="e813c-192">En règle générale, chaque octet est interprété comme un point de code Unicode, ce qui signifie que :</span><span class="sxs-lookup"><span data-stu-id="e813c-192">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="e813c-193">Les caractères ASCII imprimables sont toujours restitués correctement</span><span class="sxs-lookup"><span data-stu-id="e813c-193">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="e813c-194">Les caractères UTF-8 codés sur plusieurs octets ne s’affichent pas correctement</span><span class="sxs-lookup"><span data-stu-id="e813c-194">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="e813c-195">Les caractères UTF-16 s’affichent correctement uniquement si leur octet de poids fort se produit `NUL` .</span><span class="sxs-lookup"><span data-stu-id="e813c-195">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="e813c-196">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e813c-196">RELATED LINKS</span></span>

[<span data-ttu-id="e813c-197">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="e813c-197">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="e813c-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e813c-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="e813c-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="e813c-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="e813c-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e813c-200">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="e813c-201">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e813c-201">Format-Wide</span></span>](Format-Wide.md)

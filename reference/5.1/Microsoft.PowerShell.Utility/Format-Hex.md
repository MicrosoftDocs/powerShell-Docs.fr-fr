---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203301"
---
# <span data-ttu-id="00f0c-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="00f0c-103">Format-Hex</span></span>

## <span data-ttu-id="00f0c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="00f0c-104">SYNOPSIS</span></span>

<span data-ttu-id="00f0c-105">Affiche un fichier ou une autre entrée au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="00f0c-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="00f0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00f0c-106">SYNTAX</span></span>

### <span data-ttu-id="00f0c-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="00f0c-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### <span data-ttu-id="00f0c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="00f0c-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### <span data-ttu-id="00f0c-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="00f0c-109">ByInputObject</span></span>

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="00f0c-110">Description</span><span class="sxs-lookup"><span data-stu-id="00f0c-110">DESCRIPTION</span></span>

<span data-ttu-id="00f0c-111">L' `Format-Hex` applet de commande affiche un fichier ou une autre entrée sous forme de valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="00f0c-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="00f0c-112">Pour déterminer le décalage d’un caractère à partir de la sortie, ajoutez le nombre situé à l’extrême gauche de la ligne au nombre situé en haut de la colonne pour ce caractère.</span><span class="sxs-lookup"><span data-stu-id="00f0c-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="00f0c-113">L' `Format-Hex` applet de commande peut vous aider à déterminer le type de fichier d’un fichier endommagé ou d’un fichier qui n’a peut-être pas une extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="00f0c-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="00f0c-114">Vous pouvez exécuter cette applet de commande, puis lire la sortie hexadécimale pour obtenir des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="00f0c-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="00f0c-115">Lors de l’utilisation `Format-Hex` de sur un fichier, l’applet de commande ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les caractères de saut de ligne conservés.</span><span class="sxs-lookup"><span data-stu-id="00f0c-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="00f0c-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="00f0c-116">EXAMPLES</span></span>

### <span data-ttu-id="00f0c-117">Exemple 1 : obtenir la représentation hexadécimale d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="00f0c-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="00f0c-118">Cette commande retourne les valeurs hexadécimales d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="00f0c-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="00f0c-119">La chaîne **Hello World** est envoyée à l’applet de commande via le pipeline `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="00f0c-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="00f0c-120">La sortie hexadécimale de `Format-Hex` indique les valeurs de chaque caractère de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="00f0c-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="00f0c-121">Exemple 2 : Rechercher un type de fichier à partir d’une sortie hexadécimale</span><span class="sxs-lookup"><span data-stu-id="00f0c-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="00f0c-122">Cet exemple utilise la sortie hexadécimale pour déterminer le type de fichier.</span><span class="sxs-lookup"><span data-stu-id="00f0c-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="00f0c-123">L’applet de commande affiche le chemin d’accès complet du fichier et les valeurs hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="00f0c-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="00f0c-124">Pour tester la commande suivante, effectuez une copie d’un fichier PDF existant sur votre ordinateur local et renommez le fichier copié en **file. T7f** .</span><span class="sxs-lookup"><span data-stu-id="00f0c-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to **File.t7f** .</span></span>

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

<span data-ttu-id="00f0c-125">L' `Format-Hex` applet de commande utilise le paramètre **path** pour spécifier un nom de fichier dans le répertoire actif, `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="00f0c-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="00f0c-126">L’extension de fichier `.t7f` est rare, mais la sortie hexadécimale `%PDF` indique qu’il s’agit d’un fichier PDF.</span><span class="sxs-lookup"><span data-stu-id="00f0c-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span>

### <span data-ttu-id="00f0c-127">Exemple 3 : afficher une sortie hexadécimale brute</span><span class="sxs-lookup"><span data-stu-id="00f0c-127">Example 3: Display raw hexadecimal output</span></span>

<span data-ttu-id="00f0c-128">Par défaut, `Format-Hex` opte pour la sortie compacte des types de données numériques : les séquences codées sur un octet ou sur deux octets sont utilisées si la valeur est suffisamment petite.</span><span class="sxs-lookup"><span data-stu-id="00f0c-128">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="00f0c-129">Le paramètre **RAW** désactive ce comportement.</span><span class="sxs-lookup"><span data-stu-id="00f0c-129">The **Raw** parameter deactivates this behavior.</span></span>

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

<span data-ttu-id="00f0c-130">Notez la différence de sortie.</span><span class="sxs-lookup"><span data-stu-id="00f0c-130">Notice the difference in output.</span></span> <span data-ttu-id="00f0c-131">Le paramètre **RAW** affiche les nombres sous la forme de valeurs de 4 octets, true pour leurs types **Int32** .</span><span class="sxs-lookup"><span data-stu-id="00f0c-131">The **Raw** parameter displays the numbers as 4-byte values, true to their **Int32** types.</span></span>

## <span data-ttu-id="00f0c-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00f0c-132">PARAMETERS</span></span>

### <span data-ttu-id="00f0c-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="00f0c-133">-Encoding</span></span>

<span data-ttu-id="00f0c-134">Spécifie l’encodage de la sortie.</span><span class="sxs-lookup"><span data-stu-id="00f0c-134">Specifies the encoding of the output.</span></span> <span data-ttu-id="00f0c-135">Cela s’applique uniquement à l' `[string]` entrée.</span><span class="sxs-lookup"><span data-stu-id="00f0c-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="00f0c-136">Le paramètre n’a aucun effet sur les types numériques.</span><span class="sxs-lookup"><span data-stu-id="00f0c-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="00f0c-137">La valeur par défaut est `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="00f0c-137">The default value is `ASCII`.</span></span>

<span data-ttu-id="00f0c-138">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="00f0c-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="00f0c-139">`Ascii` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="00f0c-139">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="00f0c-140">`BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="00f0c-140">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="00f0c-141">`Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="00f0c-141">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="00f0c-142">`UTF7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="00f0c-142">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="00f0c-143">`UTF8` Utilise UTF-8.</span><span class="sxs-lookup"><span data-stu-id="00f0c-143">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="00f0c-144">`UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="00f0c-144">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="00f0c-145">Les caractères non-ASCII dans l’entrée sont générés en tant que caractères littéraux, `?` ce qui entraîne une perte d’informations.</span><span class="sxs-lookup"><span data-stu-id="00f0c-145">Non-ASCII characters in the input are output as literal `?` characters resulting in a loss of information.</span></span>

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00f0c-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="00f0c-146">-InputObject</span></span>

<span data-ttu-id="00f0c-147">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="00f0c-147">Used for pipeline input.</span></span> <span data-ttu-id="00f0c-148">L’entrée de pipeline prend en charge uniquement certains types scalaires et `[system.io.fileinfo]` instances pour le canalisation à partir de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="00f0c-148">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="00f0c-149">Les types scalaires pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="00f0c-149">The supported scalar types are:</span></span>

- `[string]`
- `[byte]`
- <span data-ttu-id="00f0c-150">`[int]`, `[int32]`</span><span class="sxs-lookup"><span data-stu-id="00f0c-150">`[int]`, `[int32]`</span></span>
- <span data-ttu-id="00f0c-151">`[long]`, `[int64]`</span><span class="sxs-lookup"><span data-stu-id="00f0c-151">`[long]`, `[int64]`</span></span>

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="00f0c-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="00f0c-152">-LiteralPath</span></span>

<span data-ttu-id="00f0c-153">Spécifie le chemin d’accès complet à un fichier.</span><span class="sxs-lookup"><span data-stu-id="00f0c-153">Specifies the complete path to a file.</span></span> <span data-ttu-id="00f0c-154">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="00f0c-154">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="00f0c-155">Ce paramètre n’accepte pas les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="00f0c-155">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="00f0c-156">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="00f0c-156">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="00f0c-157">Si le paramètre **LiteralPath** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="00f0c-157">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="00f0c-158">PowerShell n’interprète pas les caractères d’une chaîne entre guillemets simples comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="00f0c-158">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="00f0c-159">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="00f0c-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00f0c-160">-Path</span><span class="sxs-lookup"><span data-stu-id="00f0c-160">-Path</span></span>

<span data-ttu-id="00f0c-161">Spécifie le chemin d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="00f0c-161">Specifies the path to files.</span></span> <span data-ttu-id="00f0c-162">Utilisez un point ( `.` ) pour spécifier l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="00f0c-162">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="00f0c-163">Le caractère générique ( `*` ) est accepté et peut être utilisé pour spécifier tous les éléments d’un emplacement.</span><span class="sxs-lookup"><span data-stu-id="00f0c-163">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="00f0c-164">Si le paramètre **path** contient des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="00f0c-164">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="00f0c-165">Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.</span><span class="sxs-lookup"><span data-stu-id="00f0c-165">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="00f0c-166">-RAW</span><span class="sxs-lookup"><span data-stu-id="00f0c-166">-Raw</span></span>

<span data-ttu-id="00f0c-167">Par défaut, `Format-Hex` opte pour la sortie compacte des types de données numériques : les séquences codées sur un octet ou sur deux octets sont utilisées si la valeur est suffisamment petite.</span><span class="sxs-lookup"><span data-stu-id="00f0c-167">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="00f0c-168">Le paramètre **RAW** désactive ce comportement.</span><span class="sxs-lookup"><span data-stu-id="00f0c-168">The **Raw** parameter deactivates this behavior.</span></span>

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

### <span data-ttu-id="00f0c-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00f0c-169">CommonParameters</span></span>

<span data-ttu-id="00f0c-170">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00f0c-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00f0c-171">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="00f0c-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00f0c-172">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="00f0c-172">INPUTS</span></span>

### <span data-ttu-id="00f0c-173">System.String</span><span class="sxs-lookup"><span data-stu-id="00f0c-173">System.String</span></span>

<span data-ttu-id="00f0c-174">Vous pouvez diriger une chaîne vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="00f0c-174">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="00f0c-175">SORTIES</span><span class="sxs-lookup"><span data-stu-id="00f0c-175">OUTPUTS</span></span>

### <span data-ttu-id="00f0c-176">Microsoft. PowerShell. Commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="00f0c-176">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="00f0c-177">Cette applet de commande retourne un **ByteCollection** .</span><span class="sxs-lookup"><span data-stu-id="00f0c-177">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="00f0c-178">Cet objet représente une collection d’octets.</span><span class="sxs-lookup"><span data-stu-id="00f0c-178">This object represents a collection of bytes.</span></span> <span data-ttu-id="00f0c-179">Il comprend des méthodes qui convertissent la collection d’octets en une chaîne mise en forme comme chaque ligne de sortie retournée par `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="00f0c-179">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="00f0c-180">Si vous spécifiez le **chemin d’accès** ou le paramètre **LiteralPath** , l’objet contient également le chemin d’accès du fichier qui contient chaque octet.</span><span class="sxs-lookup"><span data-stu-id="00f0c-180">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="00f0c-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="00f0c-181">NOTES</span></span>

<span data-ttu-id="00f0c-182">La colonne la plus à droite de la sortie tente de restituer les octets sous forme de caractères :</span><span class="sxs-lookup"><span data-stu-id="00f0c-182">The right-most column of output tries to render the bytes as characters:</span></span>

<span data-ttu-id="00f0c-183">En règle générale, chaque octet est interprété comme un point de code Unicode, ce qui signifie que :</span><span class="sxs-lookup"><span data-stu-id="00f0c-183">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="00f0c-184">Les caractères ASCII imprimables sont toujours restitués correctement</span><span class="sxs-lookup"><span data-stu-id="00f0c-184">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="00f0c-185">Les caractères UTF-8 codés sur plusieurs octets ne s’affichent pas correctement</span><span class="sxs-lookup"><span data-stu-id="00f0c-185">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="00f0c-186">Les caractères UTF-16 s’affichent correctement uniquement si leur octet de poids fort se produit `NUL` .</span><span class="sxs-lookup"><span data-stu-id="00f0c-186">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="00f0c-187">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="00f0c-187">RELATED LINKS</span></span>

[<span data-ttu-id="00f0c-188">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="00f0c-188">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="00f0c-189">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="00f0c-189">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="00f0c-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="00f0c-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="00f0c-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="00f0c-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="00f0c-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="00f0c-192">Format-Wide</span></span>](Format-Wide.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 48f15f9d7018c2e58584bff80f81132fe08fea1e
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692736"
---
# <span data-ttu-id="74c84-102">Get-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-102">Get-Content</span></span>

## <span data-ttu-id="74c84-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="74c84-103">SYNOPSIS</span></span>
<span data-ttu-id="74c84-104">Obtient le contenu de l'élément à l'emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="74c84-104">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="74c84-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="74c84-105">SYNTAX</span></span>

### <span data-ttu-id="74c84-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="74c84-106">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="74c84-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74c84-107">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="74c84-108">Description</span><span class="sxs-lookup"><span data-stu-id="74c84-108">DESCRIPTION</span></span>

<span data-ttu-id="74c84-109">L' `Get-Content` applet de commande obtient le contenu de l’élément à l’emplacement spécifié par le chemin d’accès, tel que le texte d’un fichier ou le contenu d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="74c84-109">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="74c84-110">Pour les fichiers, le contenu est lu une ligne à la fois et retourne une collection d’objets, chacun d’eux représentant une ligne de contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-110">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="74c84-111">À compter de PowerShell 3,0, `Get-Content` peut également obtenir un nombre spécifié de lignes à partir du début ou de la fin d’un élément.</span><span class="sxs-lookup"><span data-stu-id="74c84-111">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="74c84-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="74c84-112">EXAMPLES</span></span>

### <span data-ttu-id="74c84-113">Exemple 1 : obtenir le contenu d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="74c84-113">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="74c84-114">Cet exemple obtient le contenu d’un fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="74c84-114">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="74c84-115">Le `LineNumbers.txt` fichier contient 100 lignes au format, **il s’agit de la ligne X** et est utilisé dans plusieurs exemples.</span><span class="sxs-lookup"><span data-stu-id="74c84-115">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="74c84-116">Les valeurs de tableau 1-100 sont envoyées par le pipeline à l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="74c84-116">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="74c84-117">`ForEach-Object` utilise un bloc de script avec l' `Add-Content` applet de commande pour créer le `LineNumbers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-117">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="74c84-118">La variable `$_` représente les valeurs de tableau lorsque chaque objet est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="74c84-118">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="74c84-119">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le `LineNumbers.txt` fichier et afficher le contenu dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74c84-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="74c84-120">Exemple 2 : limiter le nombre de lignes retournées par Get-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-120">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="74c84-121">Cette commande obtient les cinq premières lignes d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-121">This command gets the first five lines of a file.</span></span> <span data-ttu-id="74c84-122">Le paramètre **totalCount** est utilisé pour obtenir les cinq premières lignes de contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-122">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="74c84-123">Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="74c84-123">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="74c84-124">Exemple 3 : obtenir une ligne spécifique de contenu à partir d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="74c84-124">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="74c84-125">Cette commande obtient un nombre spécifique de lignes à partir d’un fichier, puis affiche uniquement la dernière ligne de ce contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-125">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="74c84-126">Le paramètre **totalCount** obtient les 25 premières lignes de contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-126">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="74c84-127">Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="74c84-127">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="74c84-128">La `Get-Content` commande est placée entre parenthèses afin que la commande se termine avant de passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="74c84-128">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="74c84-129">`Get-Content`retourne un tableau de lignes, ce qui vous permet d’ajouter la notation d’index après la parenthèse pour récupérer un numéro de ligne spécifique.</span><span class="sxs-lookup"><span data-stu-id="74c84-129">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="74c84-130">Dans ce cas, l' `[-1]` index spécifie le dernier index dans le tableau retourné de 25 lignes récupérées.</span><span class="sxs-lookup"><span data-stu-id="74c84-130">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="74c84-131">Exemple 4 : obtenir la dernière ligne d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="74c84-131">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="74c84-132">Cette commande obtient la première ligne et la dernière ligne de contenu à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-132">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="74c84-133">Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="74c84-133">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="74c84-134">Cet exemple utilise l' `Get-Item` applet de commande pour démontrer que vous pouvez diriger des fichiers vers le `Get-Content` paramètre.</span><span class="sxs-lookup"><span data-stu-id="74c84-134">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="74c84-135">Le paramètre **tail** obtient la dernière ligne du fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-135">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="74c84-136">Cette méthode est plus rapide que la récupération de toutes les lignes et l’utilisation de la `[-1]` notation d’index.</span><span class="sxs-lookup"><span data-stu-id="74c84-136">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="74c84-137">Exemple 5 : récupérer le contenu d’un flux de données de remplacement</span><span class="sxs-lookup"><span data-stu-id="74c84-137">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="74c84-138">Cet exemple décrit comment utiliser le paramètre **Stream** pour obtenir le contenu d’un flux de données de remplacement pour les fichiers stockés sur un volume NTFS Windows.</span><span class="sxs-lookup"><span data-stu-id="74c84-138">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="74c84-139">Dans cet exemple, l' `Set-Content` applet de commande est utilisée pour créer un exemple de contenu dans un fichier nommé `Stream.txt` .</span><span class="sxs-lookup"><span data-stu-id="74c84-139">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="74c84-140">Le paramètre **Stream** est un paramètre dynamique du [fournisseur FileSystem](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span><span class="sxs-lookup"><span data-stu-id="74c84-140">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="74c84-141">Par défaut `Get-Content` , récupère uniquement les données de la valeur par défaut ou du `:$DATA` flux.</span><span class="sxs-lookup"><span data-stu-id="74c84-141">By default `Get-Content` only retrieves data from the default, or `:$DATA` stream.</span></span> <span data-ttu-id="74c84-142">Les **flux** peuvent être utilisés pour stocker des données masquées telles que des attributs, des paramètres de sécurité ou d’autres données.</span><span class="sxs-lookup"><span data-stu-id="74c84-142">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span> <span data-ttu-id="74c84-143">Ils peuvent également être stockés dans des répertoires sans être des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="74c84-143">They can also be stored on directories without being child items.</span></span>

### <span data-ttu-id="74c84-144">Exemple 6 : récupérer du contenu brut</span><span class="sxs-lookup"><span data-stu-id="74c84-144">Example 6: Get raw content</span></span>

<span data-ttu-id="74c84-145">Dans cet exemple, les commandes récupèrent le contenu d’un fichier sous la forme d’une chaîne, au lieu d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="74c84-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="74c84-146">Par défaut, sans le paramètre dynamique **RAW** , le contenu est retourné sous la forme d’un tableau de chaînes délimitées par des sauts de ligne.</span><span class="sxs-lookup"><span data-stu-id="74c84-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="74c84-147">Cet exemple utilise le `LineNumbers.txt` fichier qui a été créé dans l’exemple</span><span class="sxs-lookup"><span data-stu-id="74c84-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="74c84-148">Exemple 7 : utiliser des filtres avec Get-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="74c84-149">Vous pouvez spécifier un filtre pour l' `Get-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74c84-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="74c84-150">Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="74c84-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="74c84-151">La commande suivante obtient le contenu de tous les `*.log` fichiers du `C:\Temp` répertoire.</span><span class="sxs-lookup"><span data-stu-id="74c84-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="74c84-152">Exemple 8 : obtenir le contenu d’un fichier sous la forme d’un tableau d’octets</span><span class="sxs-lookup"><span data-stu-id="74c84-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="74c84-153">Cet exemple montre comment obtenir le contenu d’un fichier en tant `[byte[]]` qu’objet unique.</span><span class="sxs-lookup"><span data-stu-id="74c84-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="74c84-154">La première commande utilise le paramètre **AsByteStream** pour récupérer le flux d’octets à partir du fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="74c84-155">Le paramètre **RAW** garantit que les octets sont retournés en tant que `[System.Byte[]]` .</span><span class="sxs-lookup"><span data-stu-id="74c84-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="74c84-156">Si le paramètre **RAW** est absent, la valeur de retour est un flux d’octets, qui est interprété par PowerShell comme `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="74c84-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="74c84-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74c84-157">PARAMETERS</span></span>

### <span data-ttu-id="74c84-158">-Path</span><span class="sxs-lookup"><span data-stu-id="74c84-158">-Path</span></span>

<span data-ttu-id="74c84-159">Spécifie le chemin d’accès à un élément où `Get-Content` obtient le contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="74c84-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="74c84-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="74c84-161">Les chemins d'accès doivent être ceux des éléments et non des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="74c84-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="74c84-162">Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="74c84-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="74c84-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74c84-163">-LiteralPath</span></span>

<span data-ttu-id="74c84-164">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="74c84-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="74c84-165">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="74c84-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="74c84-166">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="74c84-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="74c84-167">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="74c84-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="74c84-168">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="74c84-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="74c84-169">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="74c84-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="74c84-170">-ReadCount</span></span>

<span data-ttu-id="74c84-171">Spécifie le nombre de lignes de contenu envoyées simultanément via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="74c84-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="74c84-172">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="74c84-172">The default value is 1.</span></span>
<span data-ttu-id="74c84-173">La valeur 0 (zéro) envoie tout le contenu à la fois.</span><span class="sxs-lookup"><span data-stu-id="74c84-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="74c84-174">Ce paramètre ne modifie pas le contenu affiché, mais il affecte le temps requis pour afficher le contenu.</span><span class="sxs-lookup"><span data-stu-id="74c84-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="74c84-175">À mesure que la valeur de **ReadCount** augmente, le temps nécessaire pour retourner la première ligne augmente, tandis que le temps total requis pour l’opération diminue.</span><span class="sxs-lookup"><span data-stu-id="74c84-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="74c84-176">Cela peut faire une différence perceptible dans les éléments volumineux.</span><span class="sxs-lookup"><span data-stu-id="74c84-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-177">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="74c84-177">-TotalCount</span></span>

<span data-ttu-id="74c84-178">Spécifie le nombre de lignes à partir du début d’un fichier ou d’un autre élément.</span><span class="sxs-lookup"><span data-stu-id="74c84-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="74c84-179">La valeur par défaut est -1 (toutes les lignes).</span><span class="sxs-lookup"><span data-stu-id="74c84-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="74c84-180">Vous pouvez utiliser le nom du paramètre **totalCount** ou ses alias, **First** ou **Head**.</span><span class="sxs-lookup"><span data-stu-id="74c84-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-181">-Fin</span><span class="sxs-lookup"><span data-stu-id="74c84-181">-Tail</span></span>

<span data-ttu-id="74c84-182">Spécifie le nombre de lignes à partir de la fin d’un fichier ou d’un autre élément.</span><span class="sxs-lookup"><span data-stu-id="74c84-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="74c84-183">Vous pouvez utiliser le nom du paramètre de **fin** ou son alias, **Last**.</span><span class="sxs-lookup"><span data-stu-id="74c84-183">You can use the **Tail** parameter name or its alias, **Last**.</span></span> <span data-ttu-id="74c84-184">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="74c84-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="74c84-185">-Filter</span></span>

<span data-ttu-id="74c84-186">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="74c84-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="74c84-187">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="74c84-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="74c84-188">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="74c84-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="74c84-189">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="74c84-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="74c84-190">-Include</span><span class="sxs-lookup"><span data-stu-id="74c84-190">-Include</span></span>

<span data-ttu-id="74c84-191">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="74c84-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="74c84-192">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="74c84-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="74c84-193">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="74c84-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="74c84-194">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="74c84-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="74c84-195">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="74c84-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="74c84-196">-Exclude</span><span class="sxs-lookup"><span data-stu-id="74c84-196">-Exclude</span></span>

<span data-ttu-id="74c84-197">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="74c84-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="74c84-198">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="74c84-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="74c84-199">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="74c84-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="74c84-200">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="74c84-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="74c84-201">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="74c84-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="74c84-202">-Force</span><span class="sxs-lookup"><span data-stu-id="74c84-202">-Force</span></span>

<span data-ttu-id="74c84-203">**Force** remplacera un attribut en lecture seule ou créera des répertoires pour compléter un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="74c84-204">Le paramètre **force** ne tente pas de modifier les autorisations de fichier ou de remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="74c84-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="74c84-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="74c84-206">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74c84-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="74c84-207">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="74c84-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-208">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="74c84-208">-Delimiter</span></span>

<span data-ttu-id="74c84-209">Spécifie le délimiteur utilisé par `Get-Content` pour diviser le fichier en objets pendant la lecture.</span><span class="sxs-lookup"><span data-stu-id="74c84-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="74c84-210">La valeur par défaut est `\n` , le caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="74c84-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="74c84-211">Lors de la lecture d’un fichier texte, `Get-Content` retourne une collection d’objets String, chacun d’entre eux se terminant par un caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="74c84-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="74c84-212">Lorsque vous entrez un délimiteur qui n’existe pas dans le fichier, `Get-Content` retourne la totalité du fichier sous la forme d’un objet unique, non délimité.</span><span class="sxs-lookup"><span data-stu-id="74c84-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="74c84-213">Vous pouvez utiliser ce paramètre pour fractionner un fichier volumineux en fichiers plus petits en spécifiant un séparateur de fichiers comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="74c84-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="74c84-214">Le délimiteur est conservé (il n'est pas supprimé) et devient le dernier élément de chaque section du fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="74c84-215">Le **délimiteur** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l’applet de commande `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="74c84-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="74c84-216">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="74c84-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="74c84-217">Actuellement, lorsque la valeur du paramètre **Delimiter** est une chaîne vide, `Get-Content` ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="74c84-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="74c84-218">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="74c84-218">This is a known issue.</span></span> <span data-ttu-id="74c84-219">Pour forcer `Get-Content` à retourner la totalité du fichier sous la forme d’une chaîne unique et délimitée.</span><span class="sxs-lookup"><span data-stu-id="74c84-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="74c84-220">Entrez une valeur qui n’existe pas dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-221">-Wait</span><span class="sxs-lookup"><span data-stu-id="74c84-221">-Wait</span></span>

<span data-ttu-id="74c84-222">Conserve le fichier ouvert une fois que toutes les lignes existantes ont été générées.</span><span class="sxs-lookup"><span data-stu-id="74c84-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="74c84-223">En attente, `Get-Content` vérifie le fichier une fois par seconde et génère de nouvelles lignes le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="74c84-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="74c84-224">Vous pouvez interrompre l' **attente** en appuyant sur **Ctrl + C**.</span><span class="sxs-lookup"><span data-stu-id="74c84-224">You can interrupt **Wait** by pressing **CTRL+C**.</span></span> <span data-ttu-id="74c84-225">L’attente se termine également si le fichier est supprimé, auquel cas une erreur sans fin d’achèvement est signalée.</span><span class="sxs-lookup"><span data-stu-id="74c84-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="74c84-226">**Wait** est un paramètre dynamique que le fournisseur FileSystem ajoute à l' `Get-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74c84-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="74c84-227">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="74c84-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="74c84-228">**Wait** ne peut pas être combiné avec **RAW**.</span><span class="sxs-lookup"><span data-stu-id="74c84-228">**Wait** cannot be combined with **Raw**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-229">-RAW</span><span class="sxs-lookup"><span data-stu-id="74c84-229">-Raw</span></span>

<span data-ttu-id="74c84-230">Ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les nouvelles lignes conservées.</span><span class="sxs-lookup"><span data-stu-id="74c84-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="74c84-231">Par défaut, les caractères de saut de ligne dans un fichier sont utilisés comme délimiteurs pour séparer l’entrée dans un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="74c84-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="74c84-232">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="74c84-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="74c84-233">**RAW** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l' `Get-Content` applet de commande. ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="74c84-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="74c84-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="74c84-234">-Encoding</span></span>

<span data-ttu-id="74c84-235">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="74c84-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="74c84-236">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="74c84-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="74c84-237">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="74c84-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="74c84-238">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="74c84-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="74c84-239">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="74c84-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="74c84-240">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="74c84-240">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="74c84-241">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="74c84-241">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="74c84-242">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="74c84-242">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="74c84-243">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="74c84-243">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="74c84-244">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="74c84-244">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="74c84-245">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="74c84-245">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="74c84-246">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="74c84-246">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="74c84-247">L’encodage est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l’applet de commande `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="74c84-247">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="74c84-248">Ce paramètre est disponible uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="74c84-248">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="74c84-249">Lors de la lecture et de l’écriture dans des fichiers binaires, utilisez le paramètre **AsByteStream** et la valeur 0 pour le paramètre **readCount** .</span><span class="sxs-lookup"><span data-stu-id="74c84-249">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="74c84-250">Une valeur **readCount** de 0 lit le fichier entier en une seule opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="74c84-250">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="74c84-251">La valeur **readCount** par défaut, 1, lit un octet dans chaque opération de lecture et convertit chaque octet en un objet distinct, ce qui provoque des erreurs quand vous utilisez l' `Set-Content` applet de commande pour écrire les octets dans un fichier, sauf si vous utilisez le paramètre **AsByteStream** .</span><span class="sxs-lookup"><span data-stu-id="74c84-251">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="74c84-252">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="74c84-252">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="74c84-253">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="74c84-253">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-254">-Stream</span><span class="sxs-lookup"><span data-stu-id="74c84-254">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="74c84-255">Ce paramètre est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="74c84-255">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="74c84-256">Obtient le contenu du flux de fichiers NTFS alternatif spécifié du fichier.</span><span class="sxs-lookup"><span data-stu-id="74c84-256">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="74c84-257">Entrez le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="74c84-257">Enter the stream name.</span></span>
<span data-ttu-id="74c84-258">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="74c84-258">Wildcards are not supported.</span></span>

<span data-ttu-id="74c84-259">**Stream** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l' `Get-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74c84-259">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="74c84-260">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers sur les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="74c84-260">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="74c84-261">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="74c84-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74c84-262">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="74c84-262">-AsByteStream</span></span>

<span data-ttu-id="74c84-263">Spécifie que le contenu doit être lu en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="74c84-263">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="74c84-264">Le paramètre **AsByteStream** a été introduit dans Windows PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="74c84-264">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="74c84-265">Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="74c84-265">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="74c84-266">Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="74c84-266">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="74c84-267">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74c84-267">CommonParameters</span></span>

<span data-ttu-id="74c84-268">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="74c84-268">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="74c84-269">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="74c84-269">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="74c84-270">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="74c84-270">INPUTS</span></span>

### <span data-ttu-id="74c84-271">System.Int64, System.String[], System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="74c84-271">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="74c84-272">Vous pouvez diriger le nombre de lectures, le nombre total, les chemins d’accès ou les informations d’identification vers `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="74c84-272">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="74c84-273">SORTIES</span><span class="sxs-lookup"><span data-stu-id="74c84-273">OUTPUTS</span></span>

### <span data-ttu-id="74c84-274">System. Byte, System. String</span><span class="sxs-lookup"><span data-stu-id="74c84-274">System.Byte, System.String</span></span>

<span data-ttu-id="74c84-275">`Get-Content` retourne des chaînes ou des octets.</span><span class="sxs-lookup"><span data-stu-id="74c84-275">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="74c84-276">Le type de sortie dépend du type de contenu que vous spécifiez en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="74c84-276">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="74c84-277">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="74c84-277">NOTES</span></span>

<span data-ttu-id="74c84-278">L' `Get-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="74c84-278">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="74c84-279">Pour récupérer les fournisseurs dans votre session, utilisez l' `Get-PSProvider` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74c84-279">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="74c84-280">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="74c84-280">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="74c84-281">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="74c84-281">RELATED LINKS</span></span>

[<span data-ttu-id="74c84-282">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="74c84-282">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="74c84-283">about_Providers</span><span class="sxs-lookup"><span data-stu-id="74c84-283">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="74c84-284">Add-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-284">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="74c84-285">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-285">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="74c84-286">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="74c84-286">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="74c84-287">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="74c84-287">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="74c84-288">Set-Content</span><span class="sxs-lookup"><span data-stu-id="74c84-288">Set-Content</span></span>](Set-Content.md)

---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 7bf349c82133b275f0539db7b78c3583d00da31c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203845"
---
# <span data-ttu-id="d2c68-103">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="d2c68-103">Compress-Archive</span></span>

## <span data-ttu-id="d2c68-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d2c68-104">SYNOPSIS</span></span>
<span data-ttu-id="d2c68-105">Crée une archive compressée, ou un fichier compressé, à partir des fichiers et répertoires spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d2c68-105">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="d2c68-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2c68-106">SYNTAX</span></span>

### <span data-ttu-id="d2c68-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d2c68-107">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2c68-108">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="d2c68-108">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2c68-109">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="d2c68-109">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2c68-110">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="d2c68-110">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2c68-111">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="d2c68-111">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2c68-112">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2c68-112">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d2c68-113">Description</span><span class="sxs-lookup"><span data-stu-id="d2c68-113">DESCRIPTION</span></span>

<span data-ttu-id="d2c68-114">L' `Compress-Archive` applet de commande crée un fichier d’archive compressé ou compressé à partir d’un ou de plusieurs fichiers ou répertoires spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d2c68-114">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="d2c68-115">Une archive empaquette plusieurs fichiers, avec compression facultative, dans un seul fichier zippé pour faciliter la distribution et le stockage.</span><span class="sxs-lookup"><span data-stu-id="d2c68-115">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="d2c68-116">Un fichier d’archive peut être compressé à l’aide de l’algorithme de compression spécifié par le paramètre **CompressionLevel** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-116">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="d2c68-117">L' `Compress-Archive` applet de commande utilise l’API Microsoft .NET [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) pour compresser les fichiers.</span><span class="sxs-lookup"><span data-stu-id="d2c68-117">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="d2c68-118">La taille de fichier maximale est de 2 Go, car il existe une limitation de l’API sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="d2c68-118">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="d2c68-119">Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code.</span><span class="sxs-lookup"><span data-stu-id="d2c68-119">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="d2c68-120">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="d2c68-120">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="d2c68-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d2c68-121">EXAMPLES</span></span>

### <span data-ttu-id="d2c68-122">Exemple 1 : compresser des fichiers pour créer un fichier d’archive</span><span class="sxs-lookup"><span data-stu-id="d2c68-122">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="d2c68-123">Cet exemple compresse les fichiers de différents répertoires et crée un fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-123">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="d2c68-124">Un caractère générique est utilisé pour obtenir tous les fichiers avec une extension de fichier particulière.</span><span class="sxs-lookup"><span data-stu-id="d2c68-124">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="d2c68-125">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d2c68-125">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="d2c68-126">Le paramètre **path** accepte des noms de fichiers et des noms de fichiers spécifiques avec des caractères génériques, `*.vsd` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-126">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="d2c68-127">Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-127">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="d2c68-128">Le niveau de compression est **plus rapide** pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="d2c68-128">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="d2c68-129">Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-129">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="d2c68-130">Le `Draft.zip` fichier contient `Draftdoc.docx` et tous les fichiers avec une `.vsd` extension.</span><span class="sxs-lookup"><span data-stu-id="d2c68-130">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="d2c68-131">Exemple 2 : compresser des fichiers à l’aide d’un LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2c68-131">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="d2c68-132">Cet exemple compresse des fichiers nommés spécifiques et crée un nouveau fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-132">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="d2c68-133">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d2c68-133">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="d2c68-134">Le chemin d’accès absolu et les noms de fichiers sont utilisés, car le paramètre **LiteralPath** n’accepte pas les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="d2c68-134">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="d2c68-135">Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-135">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="d2c68-136">Le niveau de compression est **plus rapide** pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="d2c68-136">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="d2c68-137">Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-137">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="d2c68-138">Le `Draft.zip` fichier contient uniquement `Draftdoc.docx` et `diagram2.vsd` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-138">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="d2c68-139">Exemple 3 : compresser un répertoire qui comprend le répertoire racine</span><span class="sxs-lookup"><span data-stu-id="d2c68-139">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="d2c68-140">Cet exemple compresse un répertoire et crée un fichier d’archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-140">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="d2c68-141">Le fichier d’archive a une structure de répertoires, car le **chemin d’accès** spécifie un répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="d2c68-141">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="d2c68-142">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-142">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="d2c68-143">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-143">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="d2c68-144">L' `Draft.zip` archive comprend le `Reference` répertoire racine, ainsi que tous ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-144">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="d2c68-145">Exemple 4 : compresser un répertoire qui exclut le répertoire racine</span><span class="sxs-lookup"><span data-stu-id="d2c68-145">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="d2c68-146">Cet exemple compresse un répertoire et crée un fichier d’archive qui **exclut** le répertoire racine, car le **chemin d’accès** utilise un `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="d2c68-146">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="d2c68-147">L’archive contient une structure de répertoires qui contient les fichiers et les sous-répertoires du répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="d2c68-147">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="d2c68-148">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="d2c68-148">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="d2c68-149">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-149">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="d2c68-150">L' `Draft.zip` archive contient les fichiers et les sous-répertoires du répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="d2c68-150">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="d2c68-151">Le `Reference` répertoire racine est exclu de l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-151">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="d2c68-152">Exemple 5 : compresser uniquement les fichiers dans un répertoire racine</span><span class="sxs-lookup"><span data-stu-id="d2c68-152">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="d2c68-153">Cet exemple compresse uniquement les fichiers dans un répertoire racine et crée un fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-153">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="d2c68-154">Il n’existe aucune structure de répertoires dans l’archive, car seuls les fichiers sont compressés.</span><span class="sxs-lookup"><span data-stu-id="d2c68-154">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="d2c68-155">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un caractère générique en **étoile-point-étoile** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="d2c68-155">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="d2c68-156">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-156">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="d2c68-157">L' `Draft.zip` archive contient uniquement les `Reference` fichiers du répertoire racine et le répertoire racine est exclu.</span><span class="sxs-lookup"><span data-stu-id="d2c68-157">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="d2c68-158">Exemple 6 : utilisation du pipeline pour archiver des fichiers</span><span class="sxs-lookup"><span data-stu-id="d2c68-158">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="d2c68-159">Cet exemple envoie des fichiers vers le dessous du pipeline pour créer une archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-159">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="d2c68-160">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d2c68-160">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="d2c68-161">`Get-ChildItem` utilise le paramètre **path** pour spécifier deux fichiers de répertoires différents.</span><span class="sxs-lookup"><span data-stu-id="d2c68-161">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="d2c68-162">Chaque fichier est représenté par un objet **FileInfo** et est envoyé dans le pipeline à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-162">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="d2c68-163">Les deux fichiers spécifiés sont archivés dans `PipelineFiles.zip` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-163">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="d2c68-164">Exemple 7 : utiliser le pipeline pour archiver un répertoire</span><span class="sxs-lookup"><span data-stu-id="d2c68-164">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="d2c68-165">Cet exemple envoie un répertoire dans le pipeline pour créer une archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-165">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="d2c68-166">Les fichiers sont envoyés en tant qu’objets et répertoires **FileInfo** en tant qu’objets **DirectoryInfo** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-166">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="d2c68-167">La structure de répertoires de l’archive n’inclut pas le répertoire racine, mais ses fichiers et sous-répertoires sont inclus dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-167">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="d2c68-168">`Get-ChildItem` utilise le paramètre **path** pour spécifier le `C:\LogFiles` répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="d2c68-168">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="d2c68-169">Chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d2c68-169">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="d2c68-170">`Compress-Archive` Ajoute chaque objet à l' `PipelineDir.zip` archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-170">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="d2c68-171">Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.</span><span class="sxs-lookup"><span data-stu-id="d2c68-171">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="d2c68-172">Exemple 8 : comment la récursivité peut affecter les Archives</span><span class="sxs-lookup"><span data-stu-id="d2c68-172">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="d2c68-173">Cet exemple montre comment la récursivité peut dupliquer des fichiers dans votre archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-173">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="d2c68-174">Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-174">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="d2c68-175">En tant que processus de récursivité, chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline et ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-175">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="d2c68-176">Le `C:\TestLog` Répertoire ne contient aucun fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-176">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="d2c68-177">Elle contient un sous-répertoire nommé `testsub` qui contient le `testlog.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-177">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="d2c68-178">`Get-ChildItem` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\TestLog` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-178">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="d2c68-179">Le paramètre **recurse** traite les fichiers et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-179">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="d2c68-180">Un objet **DirectoryInfo** est créé pour `testsub` et un objet **FileInfo** `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-180">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="d2c68-181">Chaque objet est envoyé dans le pipeline à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-181">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="d2c68-182">Le **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-182">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="d2c68-183">Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.</span><span class="sxs-lookup"><span data-stu-id="d2c68-183">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="d2c68-184">Le résumé suivant décrit le `PipelineRecurse.zip` contenu de l’archive qui contient un fichier dupliqué :</span><span class="sxs-lookup"><span data-stu-id="d2c68-184">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="d2c68-185">L’objet **DirectoryInfo** crée le `testsub` répertoire et contient le `testlog.txt` fichier, qui reflète la structure de répertoire d’origine.</span><span class="sxs-lookup"><span data-stu-id="d2c68-185">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="d2c68-186">L’objet **FileInfo** crée un doublon `testlog.txt` dans la racine de l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-186">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="d2c68-187">Le fichier dupliqué est créé, car la récursivité a envoyé un objet de fichier à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-187">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="d2c68-188">Ce comportement est normal, car chaque objet envoyé dans le pipeline est ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-188">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="d2c68-189">Exemple 9 : mettre à jour un fichier d’archive existant</span><span class="sxs-lookup"><span data-stu-id="d2c68-189">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="d2c68-190">Cet exemple met à jour un fichier d’archive existant, `Draft.Zip` , dans le `C:\Archives` répertoire.</span><span class="sxs-lookup"><span data-stu-id="d2c68-190">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="d2c68-191">Dans cet exemple, le fichier d’archive existant contient le répertoire racine, ainsi que ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-191">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="d2c68-192">La commande est mise à jour `Draft.Zip` avec des versions plus récentes des fichiers existants dans le `C:\Reference` répertoire et ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="d2c68-192">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="d2c68-193">De plus, les nouveaux fichiers qui ont été ajoutés à `C:\Reference` ou à ses sous-répertoires sont inclus dans l’archive mise à jour `Draft.Zip` .</span><span class="sxs-lookup"><span data-stu-id="d2c68-193">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="d2c68-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2c68-194">PARAMETERS</span></span>

### <span data-ttu-id="d2c68-195">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="d2c68-195">-CompressionLevel</span></span>

<span data-ttu-id="d2c68-196">Spécifie la quantité de compression à appliquer lors de la création du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-196">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="d2c68-197">La compression plus rapide nécessite moins de temps pour créer le fichier, mais peut entraîner des tailles de fichier supérieures.</span><span class="sxs-lookup"><span data-stu-id="d2c68-197">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="d2c68-198">Si ce paramètre n’est pas spécifié, la commande utilise la valeur par défaut, **optimale** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-198">If this parameter isn't specified, the command uses the default value, **Optimal** .</span></span>

<span data-ttu-id="d2c68-199">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2c68-199">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="d2c68-200">**Plus rapide** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-200">**Fastest** .</span></span> <span data-ttu-id="d2c68-201">Utilisez la méthode de compression la plus rapide disponible pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="d2c68-201">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="d2c68-202">Une compression plus rapide peut entraîner des tailles de fichier supérieures.</span><span class="sxs-lookup"><span data-stu-id="d2c68-202">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="d2c68-203">**NoCompression** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-203">**NoCompression** .</span></span> <span data-ttu-id="d2c68-204">Ne compresse pas les fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="d2c68-204">Doesn't compress the source files.</span></span>
- <span data-ttu-id="d2c68-205">**Optimal** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-205">**Optimal** .</span></span> <span data-ttu-id="d2c68-206">Le temps de traitement dépend de la taille du fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-206">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d2c68-207">-Confirm</span></span>

<span data-ttu-id="d2c68-208">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2c68-208">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-209">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="d2c68-209">-DestinationPath</span></span>

<span data-ttu-id="d2c68-210">Ce paramètre est obligatoire et spécifie le chemin d’accès au fichier de sortie d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-210">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="d2c68-211">Le **DestinationPath** doit inclure le nom du fichier zippé et le chemin d’accès absolu ou relatif au fichier compressé.</span><span class="sxs-lookup"><span data-stu-id="d2c68-211">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="d2c68-212">Si le nom de fichier dans **DestinationPath** n’a pas d’extension de nom de fichier `.zip` , l’applet de commande ajoute l' `.zip` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d2c68-212">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-213">-Force</span><span class="sxs-lookup"><span data-stu-id="d2c68-213">-Force</span></span>

<span data-ttu-id="d2c68-214">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2c68-214">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-215">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d2c68-215">-LiteralPath</span></span>

<span data-ttu-id="d2c68-216">Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-216">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="d2c68-217">Contrairement au paramètre **path** , la valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="d2c68-217">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="d2c68-218">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d2c68-218">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d2c68-219">Si le chemin d’accès comprend des caractères d’échappement, mettez chaque caractère d’échappement entre des guillemets simples pour indiquer à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d2c68-219">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="d2c68-220">Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements de votre fichier compressé de sortie, utilisez des virgules pour séparer les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="d2c68-220">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-221">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d2c68-221">-PassThru</span></span>

<span data-ttu-id="d2c68-222">Fait en sorte que l’applet de commande génère un objet fichier représentant le fichier d’archive créé.</span><span class="sxs-lookup"><span data-stu-id="d2c68-222">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="d2c68-223">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="d2c68-223">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="d2c68-224">-Path</span><span class="sxs-lookup"><span data-stu-id="d2c68-224">-Path</span></span>

<span data-ttu-id="d2c68-225">Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-225">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="d2c68-226">Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements, utilisez des virgules pour séparer les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="d2c68-226">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="d2c68-227">Ce paramètre accepte les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="d2c68-227">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="d2c68-228">Les caractères génériques vous permettent d’ajouter tous les fichiers d’un répertoire à votre fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-228">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="d2c68-229">L’utilisation de caractères génériques avec un répertoire racine affecte le contenu de l’archive :</span><span class="sxs-lookup"><span data-stu-id="d2c68-229">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="d2c68-230">Pour créer une archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires, spécifiez le répertoire racine dans le **chemin** sans caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="d2c68-230">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="d2c68-231">Par exemple : `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="d2c68-231">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="d2c68-232">Pour créer une archive qui **exclut** le répertoire racine, mais compresse tous ses fichiers et sous-répertoires, utilisez le `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="d2c68-232">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="d2c68-233">Par exemple : `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="d2c68-233">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="d2c68-234">Pour créer une archive qui compresse uniquement les fichiers dans le répertoire racine, utilisez le caractère générique **étoile-point-étoile** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="d2c68-234">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="d2c68-235">Les sous-répertoires de la racine ne sont pas inclus dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-235">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="d2c68-236">Par exemple : `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="d2c68-236">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d2c68-237">-Mise à jour</span><span class="sxs-lookup"><span data-stu-id="d2c68-237">-Update</span></span>

<span data-ttu-id="d2c68-238">Met à jour l’archive spécifiée en remplaçant les anciennes versions de fichiers de l’Archive par des versions de fichier plus récentes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="d2c68-238">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="d2c68-239">Vous pouvez également ajouter ce paramètre pour ajouter des fichiers à une archive existante.</span><span class="sxs-lookup"><span data-stu-id="d2c68-239">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-240">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d2c68-240">-WhatIf</span></span>

<span data-ttu-id="d2c68-241">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d2c68-241">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d2c68-242">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d2c68-242">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2c68-243">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2c68-243">CommonParameters</span></span>

<span data-ttu-id="d2c68-244">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2c68-244">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2c68-245">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d2c68-245">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2c68-246">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d2c68-246">INPUTS</span></span>

### <span data-ttu-id="d2c68-247">System.String</span><span class="sxs-lookup"><span data-stu-id="d2c68-247">System.String</span></span>

<span data-ttu-id="d2c68-248">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="d2c68-248">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="d2c68-249">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d2c68-249">OUTPUTS</span></span>

### <span data-ttu-id="d2c68-250">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="d2c68-250">System.IO.FileInfo</span></span>

<span data-ttu-id="d2c68-251">L’applet de commande retourne uniquement un objet **FileInfo** quand vous utilisez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="d2c68-251">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="d2c68-252">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d2c68-252">NOTES</span></span>

<span data-ttu-id="d2c68-253">L’utilisation de la récursivité et l’envoi d’objets dans le pipeline peuvent dupliquer des fichiers dans votre archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-253">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="d2c68-254">Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** , chaque objet **FileInfo** et **DirectoryInfo** qui est envoyé vers le pipeline est ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-254">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="d2c68-255">La [spécification du fichier zip](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ne spécifie pas de méthode standard d’encodage des noms de fichiers qui contiennent des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="d2c68-255">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="d2c68-256">L' `Compress-Archive` applet de commande utilise l’encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d2c68-256">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="d2c68-257">D’autres outils d’archive ZIP peuvent utiliser un schéma d’encodage différent.</span><span class="sxs-lookup"><span data-stu-id="d2c68-257">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="d2c68-258">Lorsque vous extrayez des fichiers dont les noms de fichiers ne sont pas stockés à l’aide de l’encodage UTF-8, `Expand-Archive` utilise la valeur brute trouvée dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-258">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="d2c68-259">Cela peut entraîner un nom de fichier différent du nom de fichier source stocké dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="d2c68-259">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="d2c68-260">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d2c68-260">RELATED LINKS</span></span>

[<span data-ttu-id="d2c68-261">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="d2c68-261">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="d2c68-262">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d2c68-262">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

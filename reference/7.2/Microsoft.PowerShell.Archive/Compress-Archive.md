---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 58807ba0745a6b09e7956547425c489b427d4f4b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596104"
---
# <span data-ttu-id="de42d-102">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="de42d-102">Compress-Archive</span></span>

## <span data-ttu-id="de42d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="de42d-103">SYNOPSIS</span></span>
<span data-ttu-id="de42d-104">Crée une archive compressée, ou un fichier compressé, à partir des fichiers et répertoires spécifiés.</span><span class="sxs-lookup"><span data-stu-id="de42d-104">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="de42d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="de42d-105">SYNTAX</span></span>

### <span data-ttu-id="de42d-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="de42d-106">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de42d-107">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="de42d-107">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de42d-108">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="de42d-108">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de42d-109">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="de42d-109">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de42d-110">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="de42d-110">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de42d-111">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de42d-111">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="de42d-112">Description</span><span class="sxs-lookup"><span data-stu-id="de42d-112">DESCRIPTION</span></span>

<span data-ttu-id="de42d-113">L' `Compress-Archive` applet de commande crée un fichier d’archive compressé ou compressé à partir d’un ou de plusieurs fichiers ou répertoires spécifiés.</span><span class="sxs-lookup"><span data-stu-id="de42d-113">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="de42d-114">Une archive empaquette plusieurs fichiers, avec compression facultative, dans un seul fichier zippé pour faciliter la distribution et le stockage.</span><span class="sxs-lookup"><span data-stu-id="de42d-114">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="de42d-115">Un fichier d’archive peut être compressé à l’aide de l’algorithme de compression spécifié par le paramètre **CompressionLevel** .</span><span class="sxs-lookup"><span data-stu-id="de42d-115">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="de42d-116">L' `Compress-Archive` applet de commande utilise l’API Microsoft .NET [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) pour compresser les fichiers.</span><span class="sxs-lookup"><span data-stu-id="de42d-116">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="de42d-117">La taille de fichier maximale est de 2 Go, car il existe une limitation de l’API sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="de42d-117">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="de42d-118">Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code.</span><span class="sxs-lookup"><span data-stu-id="de42d-118">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="de42d-119">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="de42d-119">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="de42d-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="de42d-120">EXAMPLES</span></span>

### <span data-ttu-id="de42d-121">Exemple 1 : compresser des fichiers pour créer un fichier d’archive</span><span class="sxs-lookup"><span data-stu-id="de42d-121">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="de42d-122">Cet exemple compresse les fichiers de différents répertoires et crée un fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-122">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="de42d-123">Un caractère générique est utilisé pour obtenir tous les fichiers avec une extension de fichier particulière.</span><span class="sxs-lookup"><span data-stu-id="de42d-123">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="de42d-124">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="de42d-124">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="de42d-125">Le paramètre **path** accepte des noms de fichiers et des noms de fichiers spécifiques avec des caractères génériques, `*.vsd` .</span><span class="sxs-lookup"><span data-stu-id="de42d-125">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="de42d-126">Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-126">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="de42d-127">Le niveau de compression est **plus rapide** pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="de42d-127">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="de42d-128">Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-128">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="de42d-129">Le `Draft.zip` fichier contient `Draftdoc.docx` et tous les fichiers avec une `.vsd` extension.</span><span class="sxs-lookup"><span data-stu-id="de42d-129">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="de42d-130">Exemple 2 : compresser des fichiers à l’aide d’un LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de42d-130">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="de42d-131">Cet exemple compresse des fichiers nommés spécifiques et crée un nouveau fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-131">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="de42d-132">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="de42d-132">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="de42d-133">Le chemin d’accès absolu et les noms de fichiers sont utilisés, car le paramètre **LiteralPath** n’accepte pas les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="de42d-133">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="de42d-134">Le **chemin d’accès** utilise une liste séparée par des virgules pour obtenir les fichiers de différents répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-134">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="de42d-135">Le niveau de compression est **plus rapide** pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="de42d-135">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="de42d-136">Le paramètre **DestinationPath** spécifie l’emplacement du `Draft.zip` fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-136">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="de42d-137">Le `Draft.zip` fichier contient uniquement `Draftdoc.docx` et `diagram2.vsd` .</span><span class="sxs-lookup"><span data-stu-id="de42d-137">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="de42d-138">Exemple 3 : compresser un répertoire qui comprend le répertoire racine</span><span class="sxs-lookup"><span data-stu-id="de42d-138">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="de42d-139">Cet exemple compresse un répertoire et crée un fichier d’archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-139">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="de42d-140">Le fichier d’archive a une structure de répertoires, car le **chemin d’accès** spécifie un répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="de42d-140">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="de42d-141">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` .</span><span class="sxs-lookup"><span data-stu-id="de42d-141">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="de42d-142">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-142">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="de42d-143">L' `Draft.zip` archive comprend le `Reference` répertoire racine, ainsi que tous ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-143">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="de42d-144">Exemple 4 : compresser un répertoire qui exclut le répertoire racine</span><span class="sxs-lookup"><span data-stu-id="de42d-144">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="de42d-145">Cet exemple compresse un répertoire et crée un fichier d’archive qui **exclut** le répertoire racine, car le **chemin d’accès** utilise un `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="de42d-145">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="de42d-146">L’archive contient une structure de répertoires qui contient les fichiers et les sous-répertoires du répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="de42d-146">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="de42d-147">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="de42d-147">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="de42d-148">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-148">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="de42d-149">L' `Draft.zip` archive contient les fichiers et les sous-répertoires du répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="de42d-149">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="de42d-150">Le `Reference` répertoire racine est exclu de l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-150">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="de42d-151">Exemple 5 : compresser uniquement les fichiers dans un répertoire racine</span><span class="sxs-lookup"><span data-stu-id="de42d-151">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="de42d-152">Cet exemple compresse uniquement les fichiers dans un répertoire racine et crée un fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-152">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="de42d-153">Il n’existe aucune structure de répertoires dans l’archive, car seuls les fichiers sont compressés.</span><span class="sxs-lookup"><span data-stu-id="de42d-153">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="de42d-154">`Compress-Archive` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\Reference` avec un caractère générique en **étoile-point-étoile** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="de42d-154">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="de42d-155">Le paramètre **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-155">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="de42d-156">L' `Draft.zip` archive contient uniquement les `Reference` fichiers du répertoire racine et le répertoire racine est exclu.</span><span class="sxs-lookup"><span data-stu-id="de42d-156">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="de42d-157">Exemple 6 : utilisation du pipeline pour archiver des fichiers</span><span class="sxs-lookup"><span data-stu-id="de42d-157">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="de42d-158">Cet exemple envoie des fichiers vers le dessous du pipeline pour créer une archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-158">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="de42d-159">Il n’existe aucune structure de répertoire dans le fichier d’archive, car le **chemin d’accès** spécifie uniquement des noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="de42d-159">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="de42d-160">`Get-ChildItem` utilise le paramètre **path** pour spécifier deux fichiers de répertoires différents.</span><span class="sxs-lookup"><span data-stu-id="de42d-160">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="de42d-161">Chaque fichier est représenté par un objet **FileInfo** et est envoyé dans le pipeline à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="de42d-161">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="de42d-162">Les deux fichiers spécifiés sont archivés dans `PipelineFiles.zip` .</span><span class="sxs-lookup"><span data-stu-id="de42d-162">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="de42d-163">Exemple 7 : utiliser le pipeline pour archiver un répertoire</span><span class="sxs-lookup"><span data-stu-id="de42d-163">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="de42d-164">Cet exemple envoie un répertoire dans le pipeline pour créer une archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-164">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="de42d-165">Les fichiers sont envoyés en tant qu’objets et répertoires **FileInfo** en tant qu’objets **DirectoryInfo** .</span><span class="sxs-lookup"><span data-stu-id="de42d-165">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="de42d-166">La structure de répertoires de l’archive n’inclut pas le répertoire racine, mais ses fichiers et sous-répertoires sont inclus dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-166">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="de42d-167">`Get-ChildItem` utilise le paramètre **path** pour spécifier le `C:\LogFiles` répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="de42d-167">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="de42d-168">Chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="de42d-168">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="de42d-169">`Compress-Archive` Ajoute chaque objet à l' `PipelineDir.zip` archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-169">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="de42d-170">Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.</span><span class="sxs-lookup"><span data-stu-id="de42d-170">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="de42d-171">Exemple 8 : comment la récursivité peut affecter les Archives</span><span class="sxs-lookup"><span data-stu-id="de42d-171">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="de42d-172">Cet exemple montre comment la récursivité peut dupliquer des fichiers dans votre archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-172">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="de42d-173">Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** .</span><span class="sxs-lookup"><span data-stu-id="de42d-173">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="de42d-174">En tant que processus de récursivité, chaque objet **FileInfo** et **DirectoryInfo** est envoyé vers le pipeline et ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-174">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="de42d-175">Le `C:\TestLog` Répertoire ne contient aucun fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-175">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="de42d-176">Elle contient un sous-répertoire nommé `testsub` qui contient le `testlog.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-176">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="de42d-177">`Get-ChildItem` utilise le paramètre **path** pour spécifier le répertoire racine, `C:\TestLog` .</span><span class="sxs-lookup"><span data-stu-id="de42d-177">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="de42d-178">Le paramètre **recurse** traite les fichiers et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-178">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="de42d-179">Un objet **DirectoryInfo** est créé pour `testsub` et un objet **FileInfo** `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="de42d-179">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="de42d-180">Chaque objet est envoyé dans le pipeline à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="de42d-180">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="de42d-181">Le **DestinationPath** spécifie l’emplacement du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-181">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="de42d-182">Le paramètre **path** n’est pas spécifié, car les objets de pipeline sont reçus dans la position de paramètre 0.</span><span class="sxs-lookup"><span data-stu-id="de42d-182">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="de42d-183">Le résumé suivant décrit le `PipelineRecurse.zip` contenu de l’archive qui contient un fichier dupliqué :</span><span class="sxs-lookup"><span data-stu-id="de42d-183">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="de42d-184">L’objet **DirectoryInfo** crée le `testsub` répertoire et contient le `testlog.txt` fichier, qui reflète la structure de répertoire d’origine.</span><span class="sxs-lookup"><span data-stu-id="de42d-184">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="de42d-185">L’objet **FileInfo** crée un doublon `testlog.txt` dans la racine de l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-185">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="de42d-186">Le fichier dupliqué est créé, car la récursivité a envoyé un objet de fichier à `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="de42d-186">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="de42d-187">Ce comportement est normal, car chaque objet envoyé dans le pipeline est ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-187">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="de42d-188">Exemple 9 : mettre à jour un fichier d’archive existant</span><span class="sxs-lookup"><span data-stu-id="de42d-188">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="de42d-189">Cet exemple met à jour un fichier d’archive existant, `Draft.Zip` , dans le `C:\Archives` répertoire.</span><span class="sxs-lookup"><span data-stu-id="de42d-189">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="de42d-190">Dans cet exemple, le fichier d’archive existant contient le répertoire racine, ainsi que ses fichiers et sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-190">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="de42d-191">La commande est mise à jour `Draft.Zip` avec des versions plus récentes des fichiers existants dans le `C:\Reference` répertoire et ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="de42d-191">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="de42d-192">De plus, les nouveaux fichiers qui ont été ajoutés à `C:\Reference` ou à ses sous-répertoires sont inclus dans l’archive mise à jour `Draft.Zip` .</span><span class="sxs-lookup"><span data-stu-id="de42d-192">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="de42d-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de42d-193">PARAMETERS</span></span>

### <span data-ttu-id="de42d-194">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="de42d-194">-CompressionLevel</span></span>

<span data-ttu-id="de42d-195">Spécifie la quantité de compression à appliquer lors de la création du fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-195">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="de42d-196">La compression plus rapide nécessite moins de temps pour créer le fichier, mais peut entraîner des tailles de fichier supérieures.</span><span class="sxs-lookup"><span data-stu-id="de42d-196">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="de42d-197">Si ce paramètre n’est pas spécifié, la commande utilise la valeur par défaut, **optimale**.</span><span class="sxs-lookup"><span data-stu-id="de42d-197">If this parameter isn't specified, the command uses the default value, **Optimal**.</span></span>

<span data-ttu-id="de42d-198">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="de42d-198">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="de42d-199">**Plus rapide**.</span><span class="sxs-lookup"><span data-stu-id="de42d-199">**Fastest**.</span></span> <span data-ttu-id="de42d-200">Utilisez la méthode de compression la plus rapide disponible pour réduire le temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="de42d-200">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="de42d-201">Une compression plus rapide peut entraîner des tailles de fichier supérieures.</span><span class="sxs-lookup"><span data-stu-id="de42d-201">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="de42d-202">**NoCompression**.</span><span class="sxs-lookup"><span data-stu-id="de42d-202">**NoCompression**.</span></span> <span data-ttu-id="de42d-203">Ne compresse pas les fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="de42d-203">Doesn't compress the source files.</span></span>
- <span data-ttu-id="de42d-204">**Optimal**.</span><span class="sxs-lookup"><span data-stu-id="de42d-204">**Optimal**.</span></span> <span data-ttu-id="de42d-205">Le temps de traitement dépend de la taille du fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-205">Processing time is dependent on file size.</span></span>

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

### <span data-ttu-id="de42d-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="de42d-206">-Confirm</span></span>

<span data-ttu-id="de42d-207">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de42d-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="de42d-208">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="de42d-208">-DestinationPath</span></span>

<span data-ttu-id="de42d-209">Ce paramètre est obligatoire et spécifie le chemin d’accès au fichier de sortie d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-209">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="de42d-210">Le **DestinationPath** doit inclure le nom du fichier zippé et le chemin d’accès absolu ou relatif au fichier compressé.</span><span class="sxs-lookup"><span data-stu-id="de42d-210">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="de42d-211">Si le nom de fichier dans **DestinationPath** n’a pas d’extension de nom de fichier `.zip` , l’applet de commande ajoute l' `.zip` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="de42d-211">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

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

### <span data-ttu-id="de42d-212">-Force</span><span class="sxs-lookup"><span data-stu-id="de42d-212">-Force</span></span>

<span data-ttu-id="de42d-213">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="de42d-213">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="de42d-214">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de42d-214">-LiteralPath</span></span>

<span data-ttu-id="de42d-215">Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-215">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="de42d-216">Contrairement au paramètre **path** , la valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="de42d-216">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="de42d-217">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="de42d-217">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="de42d-218">Si le chemin d’accès comprend des caractères d’échappement, mettez chaque caractère d’échappement entre des guillemets simples pour indiquer à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="de42d-218">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="de42d-219">Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements de votre fichier compressé de sortie, utilisez des virgules pour séparer les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="de42d-219">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="de42d-220">-PassThru</span><span class="sxs-lookup"><span data-stu-id="de42d-220">-PassThru</span></span>

<span data-ttu-id="de42d-221">Fait en sorte que l’applet de commande génère un objet fichier représentant le fichier d’archive créé.</span><span class="sxs-lookup"><span data-stu-id="de42d-221">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="de42d-222">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="de42d-222">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="de42d-223">-Path</span><span class="sxs-lookup"><span data-stu-id="de42d-223">-Path</span></span>

<span data-ttu-id="de42d-224">Spécifie le ou les chemins d’accès aux fichiers que vous souhaitez ajouter au fichier compressé d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-224">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="de42d-225">Pour spécifier plusieurs chemins d’accès et inclure des fichiers dans plusieurs emplacements, utilisez des virgules pour séparer les chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="de42d-225">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="de42d-226">Ce paramètre accepte les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="de42d-226">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="de42d-227">Les caractères génériques vous permettent d’ajouter tous les fichiers d’un répertoire à votre fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-227">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="de42d-228">L’utilisation de caractères génériques avec un répertoire racine affecte le contenu de l’archive :</span><span class="sxs-lookup"><span data-stu-id="de42d-228">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="de42d-229">Pour créer une archive qui **comprend** le répertoire racine, ainsi que tous ses fichiers et sous-répertoires, spécifiez le répertoire racine dans le **chemin** sans caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="de42d-229">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="de42d-230">Par exemple : `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="de42d-230">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="de42d-231">Pour créer une archive qui **exclut** le répertoire racine, mais compresse tous ses fichiers et sous-répertoires, utilisez le `*` caractère générique astérisque ().</span><span class="sxs-lookup"><span data-stu-id="de42d-231">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="de42d-232">Par exemple : `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="de42d-232">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="de42d-233">Pour créer une archive qui compresse uniquement les fichiers dans le répertoire racine, utilisez le caractère générique **étoile-point-étoile** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="de42d-233">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="de42d-234">Les sous-répertoires de la racine ne sont pas inclus dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-234">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="de42d-235">Par exemple : `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="de42d-235">For example: `-Path C:\Reference\*.*`</span></span>

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

### <span data-ttu-id="de42d-236">-Mise à jour</span><span class="sxs-lookup"><span data-stu-id="de42d-236">-Update</span></span>

<span data-ttu-id="de42d-237">Met à jour l’archive spécifiée en remplaçant les anciennes versions de fichiers de l’Archive par des versions de fichier plus récentes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="de42d-237">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="de42d-238">Vous pouvez également ajouter ce paramètre pour ajouter des fichiers à une archive existante.</span><span class="sxs-lookup"><span data-stu-id="de42d-238">You can also add this parameter to add files to an existing archive.</span></span>

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

### <span data-ttu-id="de42d-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="de42d-239">-WhatIf</span></span>

<span data-ttu-id="de42d-240">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de42d-240">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="de42d-241">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="de42d-241">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="de42d-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de42d-242">CommonParameters</span></span>

<span data-ttu-id="de42d-243">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="de42d-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de42d-244">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="de42d-244">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de42d-245">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="de42d-245">INPUTS</span></span>

### <span data-ttu-id="de42d-246">System.String</span><span class="sxs-lookup"><span data-stu-id="de42d-246">System.String</span></span>

<span data-ttu-id="de42d-247">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="de42d-247">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="de42d-248">SORTIES</span><span class="sxs-lookup"><span data-stu-id="de42d-248">OUTPUTS</span></span>

### <span data-ttu-id="de42d-249">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="de42d-249">System.IO.FileInfo</span></span>

<span data-ttu-id="de42d-250">L’applet de commande retourne uniquement un objet **FileInfo** quand vous utilisez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="de42d-250">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="de42d-251">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="de42d-251">NOTES</span></span>

<span data-ttu-id="de42d-252">L’utilisation de la récursivité et l’envoi d’objets dans le pipeline peuvent dupliquer des fichiers dans votre archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-252">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="de42d-253">Par exemple, si vous utilisez `Get-ChildItem` avec le paramètre **recurse** , chaque objet **FileInfo** et **DirectoryInfo** qui est envoyé vers le pipeline est ajouté à l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-253">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="de42d-254">La [spécification du fichier zip](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ne spécifie pas de méthode standard d’encodage des noms de fichiers qui contiennent des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="de42d-254">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="de42d-255">L' `Compress-Archive` applet de commande utilise l’encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="de42d-255">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="de42d-256">D’autres outils d’archive ZIP peuvent utiliser un schéma d’encodage différent.</span><span class="sxs-lookup"><span data-stu-id="de42d-256">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="de42d-257">Lorsque vous extrayez des fichiers dont les noms de fichiers ne sont pas stockés à l’aide de l’encodage UTF-8, `Expand-Archive` utilise la valeur brute trouvée dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-257">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="de42d-258">Cela peut entraîner un nom de fichier différent du nom de fichier source stocké dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="de42d-258">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="de42d-259">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="de42d-259">RELATED LINKS</span></span>

[<span data-ttu-id="de42d-260">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="de42d-260">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="de42d-261">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="de42d-261">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)


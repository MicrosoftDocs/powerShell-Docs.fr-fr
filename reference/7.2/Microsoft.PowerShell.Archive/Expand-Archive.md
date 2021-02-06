---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: a4cf8970156f524578f7c9747aef1ffbf9f3eb58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597164"
---
# <span data-ttu-id="4fa9b-102">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="4fa9b-102">Expand-Archive</span></span>

## <span data-ttu-id="4fa9b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4fa9b-103">SYNOPSIS</span></span>
<span data-ttu-id="4fa9b-104">Extrait des fichiers à partir d’un fichier d’archive (zippé) spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-104">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="4fa9b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4fa9b-105">SYNTAX</span></span>

### <span data-ttu-id="4fa9b-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4fa9b-106">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4fa9b-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4fa9b-107">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4fa9b-108">Description</span><span class="sxs-lookup"><span data-stu-id="4fa9b-108">DESCRIPTION</span></span>

<span data-ttu-id="4fa9b-109">L' `Expand-Archive` applet de commande extrait les fichiers d’un fichier d’archive compressé spécifié dans un dossier de destination spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-109">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="4fa9b-110">Un fichier d’archive permet d’empaqueter plusieurs fichiers et éventuellement de les compresser dans un seul fichier zippé pour faciliter la distribution et le stockage.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-110">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="4fa9b-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4fa9b-111">EXAMPLES</span></span>

### <span data-ttu-id="4fa9b-112">Exemple 1 : extraire le contenu d’une archive</span><span class="sxs-lookup"><span data-stu-id="4fa9b-112">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="4fa9b-113">Cet exemple extrait le contenu d’un fichier d’archive existant dans le dossier spécifié par le paramètre **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="4fa9b-113">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="4fa9b-114">Dans cet exemple, le paramètre **LiteralPath** est utilisé, car le nom de fichier contient des caractères qui peuvent être interprétés comme des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-114">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="4fa9b-115">Exemple 2 : extraire le contenu d’une archive dans le dossier actif</span><span class="sxs-lookup"><span data-stu-id="4fa9b-115">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="4fa9b-116">Cet exemple extrait le contenu d’un fichier d’archive existant dans le dossier actif dans le dossier spécifié par le paramètre **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="4fa9b-116">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="4fa9b-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4fa9b-117">PARAMETERS</span></span>

### <span data-ttu-id="4fa9b-118">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="4fa9b-118">-DestinationPath</span></span>

<span data-ttu-id="4fa9b-119">Par défaut, `Expand-Archive` crée un dossier à l’emplacement actuel qui est le même nom que le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-119">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="4fa9b-120">Le paramètre vous permet de spécifier le chemin d’accès à un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-120">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="4fa9b-121">Le dossier cible est créé s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-121">The target folder is created if it does not exist.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4fa9b-122">-Force</span><span class="sxs-lookup"><span data-stu-id="4fa9b-122">-Force</span></span>

<span data-ttu-id="4fa9b-123">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4fa9b-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4fa9b-124">-LiteralPath</span></span>

<span data-ttu-id="4fa9b-125">Spécifie le chemin d’accès à un fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-125">Specifies the path to an archive file.</span></span> <span data-ttu-id="4fa9b-126">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-126">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="4fa9b-127">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-127">Wildcard characters are not supported.</span></span> <span data-ttu-id="4fa9b-128">Si le chemin d’accès comprend des caractères d’échappement, mettez chaque caractère d’échappement entre des guillemets simples pour indiquer à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-128">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4fa9b-129">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4fa9b-129">-PassThru</span></span>

<span data-ttu-id="4fa9b-130">Fait en sorte que l’applet de commande génère une liste des fichiers développés à partir de l’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-130">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="4fa9b-131">-Path</span><span class="sxs-lookup"><span data-stu-id="4fa9b-131">-Path</span></span>

<span data-ttu-id="4fa9b-132">Spécifie le chemin d’accès au fichier d’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-132">Specifies the path to the archive file.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4fa9b-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4fa9b-133">-Confirm</span></span>

<span data-ttu-id="4fa9b-134">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4fa9b-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4fa9b-135">-WhatIf</span></span>

<span data-ttu-id="4fa9b-136">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4fa9b-137">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4fa9b-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4fa9b-138">CommonParameters</span></span>
<span data-ttu-id="4fa9b-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4fa9b-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4fa9b-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4fa9b-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4fa9b-141">INPUTS</span></span>

### <span data-ttu-id="4fa9b-142">System.String</span><span class="sxs-lookup"><span data-stu-id="4fa9b-142">System.String</span></span>

<span data-ttu-id="4fa9b-143">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers un fichier d’archive existant.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-143">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="4fa9b-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4fa9b-144">OUTPUTS</span></span>

### <span data-ttu-id="4fa9b-145">System. IO. FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="4fa9b-145">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="4fa9b-146">Lorsque le `-PassThru` paramètre est utilisé, l’applet de commande génère une liste des fichiers qui ont été développés à partir de l’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-146">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="4fa9b-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4fa9b-147">NOTES</span></span>

<span data-ttu-id="4fa9b-148">La [spécification du fichier zip](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ne spécifie pas de méthode standard d’encodage des noms de fichiers qui contiennent des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-148">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="4fa9b-149">L' `Compress-Archive` applet de commande utilise l’encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-149">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="4fa9b-150">D’autres outils d’archive ZIP peuvent utiliser un schéma d’encodage différent.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-150">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="4fa9b-151">Lorsque vous extrayez des fichiers dont les noms de fichiers ne sont pas stockés à l’aide de l’encodage UTF-8, `Expand-Archive` utilise la valeur brute trouvée dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-151">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="4fa9b-152">Cela peut entraîner un nom de fichier différent du nom de fichier source stocké dans l’archive.</span><span class="sxs-lookup"><span data-stu-id="4fa9b-152">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="4fa9b-153">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4fa9b-153">RELATED LINKS</span></span>

[<span data-ttu-id="4fa9b-154">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="4fa9b-154">Compress-Archive</span></span>](compress-archive.md)

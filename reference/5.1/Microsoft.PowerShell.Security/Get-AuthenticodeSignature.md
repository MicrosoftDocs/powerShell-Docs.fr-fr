---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: cf19973acf799b25b8b598fad70f84943f958e1d
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685889"
---
# <span data-ttu-id="a077f-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a077f-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="a077f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a077f-104">SYNOPSIS</span></span>
<span data-ttu-id="a077f-105">Obtient des informations sur la signature Authenticode d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="a077f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a077f-106">SYNTAX</span></span>

### <span data-ttu-id="a077f-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a077f-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="a077f-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a077f-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="a077f-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="a077f-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="a077f-110">Description</span><span class="sxs-lookup"><span data-stu-id="a077f-110">DESCRIPTION</span></span>

<span data-ttu-id="a077f-111">L' `Get-AuthenticodeSignature` applet de commande obtient des informations sur la signature Authenticode pour un fichier ou un contenu de fichier sous la forme d’un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="a077f-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span>
<span data-ttu-id="a077f-112">Si le fichier est signé avec une signature signée et que le catalogue Windows est signé, la signature du catalogue Windows est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a077f-112">If the file is both embedded signed and Windows catalog signed, the Windows catalog signature is used.</span></span>
<span data-ttu-id="a077f-113">Si le fichier n'est pas signé, les informations sont récupérées, mais les champs sont vides.</span><span class="sxs-lookup"><span data-stu-id="a077f-113">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="a077f-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a077f-114">EXAMPLES</span></span>

### <span data-ttu-id="a077f-115">Exemple 1 : obtenir la signature Authenticode d’un fichier</span><span class="sxs-lookup"><span data-stu-id="a077f-115">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="a077f-116">Cette commande obtient des informations sur la signature Authenticode dans le fichier NewScript.ps1.</span><span class="sxs-lookup"><span data-stu-id="a077f-116">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="a077f-117">Elle utilise le paramètre **filePath** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-117">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="a077f-118">Exemple 2 : obtenir la signature Authenticode pour plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="a077f-118">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="a077f-119">Cette commande obtient des informations sur la signature Authenticode pour les quatre fichiers listés sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a077f-119">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="a077f-120">Dans cet exemple, le nom du paramètre **filePath** , qui est facultatif, est omis.</span><span class="sxs-lookup"><span data-stu-id="a077f-120">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="a077f-121">Exemple 3 : obtenir uniquement des signatures Authenticode valides pour plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="a077f-121">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="a077f-122">Cette commande répertorie tous les fichiers du `$PSHOME` répertoire qui ont une signature Authenticode valide.</span><span class="sxs-lookup"><span data-stu-id="a077f-122">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="a077f-123">La `$PSHOME` variable automatique contient le chemin d’accès au répertoire d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a077f-123">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="a077f-124">La commande utilise l' `Get-ChildItem` applet de commande pour récupérer les fichiers dans le `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a077f-124">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="a077f-125">Elle utilise un modèle de *.*</span><span class="sxs-lookup"><span data-stu-id="a077f-125">It uses a pattern of *.*</span></span> <span data-ttu-id="a077f-126">pour exclure des répertoires (bien qu’il exclue également les fichiers sans point dans le nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="a077f-126">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="a077f-127">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les fichiers dans `$PSHOME` l’applet de commande `ForEach-Object` , où `Get-AuthenticodeSignature` est appelé pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-127">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="a077f-128">Les résultats de la `Get-AuthenticodeSignature` commande sont envoyés à une `Where-Object` commande qui sélectionne uniquement les objets de signature dont l’État est valide.</span><span class="sxs-lookup"><span data-stu-id="a077f-128">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="a077f-129">Exemple 4 : obtenir la signature Authenticode pour un contenu de fichier spécifié en tant que tableau d’octets</span><span class="sxs-lookup"><span data-stu-id="a077f-129">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="a077f-130">Cette commande obtient des informations sur la signature Authenticode pour le contenu d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-130">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="a077f-131">Dans cet exemple, l’extension de fichier est spécifiée en même temps que le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-131">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="a077f-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a077f-132">PARAMETERS</span></span>

### <span data-ttu-id="a077f-133">-Contenu</span><span class="sxs-lookup"><span data-stu-id="a077f-133">-Content</span></span>

<span data-ttu-id="a077f-134">Contenu d’un fichier sous la forme d’un tableau d’octets pour lequel la signature Authenticode est récupérée.</span><span class="sxs-lookup"><span data-stu-id="a077f-134">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="a077f-135">Ce paramètre doit être utilisé avec le paramètre **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="a077f-135">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="a077f-136">Le contenu du fichier doit être au format Unicode (UTF-16LE).</span><span class="sxs-lookup"><span data-stu-id="a077f-136">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a077f-137">-FilePath</span><span class="sxs-lookup"><span data-stu-id="a077f-137">-FilePath</span></span>

<span data-ttu-id="a077f-138">Spécifie le chemin d’accès au fichier à examiner.</span><span class="sxs-lookup"><span data-stu-id="a077f-138">Specifies the path to the file to examine.</span></span> <span data-ttu-id="a077f-139">Les caractères génériques sont autorisés, mais ils doivent conduire à un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="a077f-139">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="a077f-140">Il n’est pas nécessaire de taper **filePath** sur la ligne de commande lorsque vous spécifiez une valeur pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a077f-140">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a077f-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a077f-141">-LiteralPath</span></span>

<span data-ttu-id="a077f-142">Spécifie le chemin d'accès au fichier à examiner.</span><span class="sxs-lookup"><span data-stu-id="a077f-142">Specifies the path to the file being examined.</span></span> <span data-ttu-id="a077f-143">Contrairement à **FilePath**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a077f-143">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a077f-144">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a077f-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a077f-145">Si le chemin d’accès contient un caractère d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a077f-145">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="a077f-146">Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des caractères d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a077f-146">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a077f-147">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="a077f-147">-SourcePathOrExtension</span></span>

<span data-ttu-id="a077f-148">Chemin d’accès au type de fichier ou de fichier du contenu pour lequel la signature Authenticode est récupérée.</span><span class="sxs-lookup"><span data-stu-id="a077f-148">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="a077f-149">Ce paramètre est utilisé avec le **contenu** où le contenu du fichier est passé en tant que tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="a077f-149">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a077f-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a077f-150">CommonParameters</span></span>

<span data-ttu-id="a077f-151">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a077f-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a077f-152">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a077f-152">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a077f-153">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a077f-153">INPUTS</span></span>

### <span data-ttu-id="a077f-154">System.String</span><span class="sxs-lookup"><span data-stu-id="a077f-154">System.String</span></span>

<span data-ttu-id="a077f-155">Vous pouvez diriger une chaîne qui contient un chemin d’accès de fichier vers `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="a077f-155">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="a077f-156">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a077f-156">OUTPUTS</span></span>

### <span data-ttu-id="a077f-157">System. Management. Automation. signature</span><span class="sxs-lookup"><span data-stu-id="a077f-157">System.Management.Automation.Signature</span></span>

<span data-ttu-id="a077f-158">`Get-AuthenticodeSignature` retourne un objet de signature pour chaque signature qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="a077f-158">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="a077f-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a077f-159">NOTES</span></span>

<span data-ttu-id="a077f-160">Pour plus d’informations sur les signatures Authenticode dans PowerShell, consultez [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="a077f-160">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="a077f-161">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a077f-161">RELATED LINKS</span></span>

[<span data-ttu-id="a077f-162">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a077f-162">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="a077f-163">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a077f-163">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="a077f-164">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a077f-164">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="a077f-165">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="a077f-165">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="a077f-166">about_Signing</span><span class="sxs-lookup"><span data-stu-id="a077f-166">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)

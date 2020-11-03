---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 139ebf10cd0097d55eac521cd81016f8f168d2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203397"
---
# <span data-ttu-id="6fc7f-103">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6fc7f-103">New-FileCatalog</span></span>

## <span data-ttu-id="6fc7f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6fc7f-104">SYNOPSIS</span></span>

<span data-ttu-id="6fc7f-105">`New-FileCatalog` crée un fichier catalogue de hachages de fichiers qui peuvent être utilisés pour valider l’authenticité d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-105">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="6fc7f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fc7f-106">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="6fc7f-107">Description</span><span class="sxs-lookup"><span data-stu-id="6fc7f-107">DESCRIPTION</span></span>

<span data-ttu-id="6fc7f-108">`New-FileCatalog` crée un [fichier catalogue Windows](/windows-hardware/drivers/install/catalog-files) pour un ensemble de dossiers et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-108">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span>
<span data-ttu-id="6fc7f-109">Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins d’accès fournis.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-109">This catalog file contains hashes for all files in the provided paths.</span></span>
<span data-ttu-id="6fc7f-110">Les utilisateurs peuvent ensuite distribuer le catalogue avec leurs fichiers afin que les utilisateurs puissent valider si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-110">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="6fc7f-111">Les versions de catalogues 1 et 2 sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-111">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="6fc7f-112">La version 1 utilise l’algorithme de hachage SHA1 (déconseillé) pour créer des hachages de fichier, et la version 2 utilise SHA256.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-112">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span>
<span data-ttu-id="6fc7f-113">La version de catalogue 2 n’est pas prise en charge sur Windows Server 2008 R2 ni Windows 7.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-113">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="6fc7f-114">Vous devez utiliser la version de catalogue 2 sur Windows 8, Windows Server 2012 et les systèmes d’exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-114">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="6fc7f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6fc7f-115">EXAMPLES</span></span>

### <span data-ttu-id="6fc7f-116">Exemple 1 : créer un catalogue de fichiers pour `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="6fc7f-116">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="6fc7f-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fc7f-117">PARAMETERS</span></span>

### <span data-ttu-id="6fc7f-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="6fc7f-118">-CatalogFilePath</span></span>

<span data-ttu-id="6fc7f-119">Chemin d’accès à un fichier ou dossier dans lequel le fichier catalogue (. cat) doit être placé.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-119">A path to a file or folder where the catalog file (.cat) should be placed.</span></span>
<span data-ttu-id="6fc7f-120">Si un chemin d’accès au dossier est spécifié, le nom de fichier par défaut est `catalog.cat` utilisé.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-120">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6fc7f-121">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="6fc7f-121">-CatalogVersion</span></span>

<span data-ttu-id="6fc7f-122">Accepte `1.0` ou `2.0` en tant que valeurs possibles pour la spécification de la version du catalogue.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-122">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span>
<span data-ttu-id="6fc7f-123">`1.0` doit être utilisé dans la mesure du possible, car il utilise l’algorithme de hachage SHA-1 non sécurisé, tandis que `2.0` utilise l’algorithme SHA-256 sécurisé Toutefois, `1.0` est le seul algorithme pris en charge sur Windows 7 et le serveur 2008R2.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-123">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fc7f-124">-Path</span><span class="sxs-lookup"><span data-stu-id="6fc7f-124">-Path</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6fc7f-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6fc7f-125">-Confirm</span></span>

<span data-ttu-id="6fc7f-126">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6fc7f-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6fc7f-127">-WhatIf</span></span>

<span data-ttu-id="6fc7f-128">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6fc7f-129">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6fc7f-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fc7f-130">CommonParameters</span></span>
<span data-ttu-id="6fc7f-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fc7f-132">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7f-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6fc7f-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6fc7f-133">INPUTS</span></span>

### <span data-ttu-id="6fc7f-134">System.String</span><span class="sxs-lookup"><span data-stu-id="6fc7f-134">System.String</span></span>

<span data-ttu-id="6fc7f-135">Le pipeline prend une chaîne qui est utilisée comme nom de fichier du catalogue.</span><span class="sxs-lookup"><span data-stu-id="6fc7f-135">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="6fc7f-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6fc7f-136">OUTPUTS</span></span>

### <span data-ttu-id="6fc7f-137">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="6fc7f-137">System.IO.FileInfo</span></span>

## <span data-ttu-id="6fc7f-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6fc7f-138">NOTES</span></span>

## <span data-ttu-id="6fc7f-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6fc7f-139">RELATED LINKS</span></span>

[<span data-ttu-id="6fc7f-140">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6fc7f-140">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="6fc7f-141">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6fc7f-141">PowerShellGet</span></span>](/powerShell/module/powershellget)

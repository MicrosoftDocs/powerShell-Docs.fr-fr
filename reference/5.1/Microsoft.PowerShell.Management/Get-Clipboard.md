---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206302"
---
# <span data-ttu-id="5edb9-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="5edb9-103">Get-Clipboard</span></span>

## <span data-ttu-id="5edb9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5edb9-104">SYNOPSIS</span></span>
<span data-ttu-id="5edb9-105">Obtient l’entrée actuelle du presse-papiers Windows.</span><span class="sxs-lookup"><span data-stu-id="5edb9-105">Gets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="5edb9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5edb9-106">SYNTAX</span></span>

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="5edb9-107">Description</span><span class="sxs-lookup"><span data-stu-id="5edb9-107">DESCRIPTION</span></span>

<span data-ttu-id="5edb9-108">L' `Get-Clipboard` applet de commande obtient l’entrée du presse-papiers Windows en cours.</span><span class="sxs-lookup"><span data-stu-id="5edb9-108">The `Get-Clipboard` cmdlet gets the current Windows clipboard entry.</span></span> <span data-ttu-id="5edb9-109">Plusieurs lignes de texte sont retournées sous la forme d’un tableau de chaînes similaire à `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="5edb9-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

## <span data-ttu-id="5edb9-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5edb9-110">EXAMPLES</span></span>

### <span data-ttu-id="5edb9-111">Exemple 1 : obtenir le contenu du presse-papiers et l’afficher sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="5edb9-111">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="5edb9-112">Dans cet exemple, nous avons cliqué avec le bouton droit sur une image dans un navigateur et choisi l’action de **copie** .</span><span class="sxs-lookup"><span data-stu-id="5edb9-112">In this example we have right-clicked on an image in a browser and chose the **Copy** action.</span></span> <span data-ttu-id="5edb9-113">La commande suivante affiche le lien, sous la forme d’une URL, de l’image stockée dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5edb9-113">The following command displays the link, as a URL, of the image that is stored in the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### <span data-ttu-id="5edb9-114">Exemple 2 : obtenir le contenu du presse-papiers dans un format spécifique</span><span class="sxs-lookup"><span data-stu-id="5edb9-114">Example 2: Get the content of the clipboard in a specific format</span></span>

<span data-ttu-id="5edb9-115">Dans cet exemple, nous avons copié les fichiers dans le presse-papiers de Windows Explorerby en les sélectionnant et en appuyant sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5edb9-115">In this example we copied files to the clipboard in Windows Explorerby selecting them and pressing <kbd>Ctrl-C</kbd>.</span></span> <span data-ttu-id="5edb9-116">À l’aide de la commande suivante, vous pouvez accéder au contenu du presse-papiers sous la forme d’une liste de fichiers :</span><span class="sxs-lookup"><span data-stu-id="5edb9-116">Using the following command, you can access the contents of the clipboard as a list of files:</span></span>

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## <span data-ttu-id="5edb9-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5edb9-117">PARAMETERS</span></span>

### <span data-ttu-id="5edb9-118">-Format</span><span class="sxs-lookup"><span data-stu-id="5edb9-118">-Format</span></span>

<span data-ttu-id="5edb9-119">Spécifie le type ou le format du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5edb9-119">Specifies the type, or format, of the clipboard.</span></span> <span data-ttu-id="5edb9-120">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="5edb9-120">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5edb9-121">Texte</span><span class="sxs-lookup"><span data-stu-id="5edb9-121">Text</span></span>
- <span data-ttu-id="5edb9-122">FileDropList</span><span class="sxs-lookup"><span data-stu-id="5edb9-122">FileDropList</span></span>
- <span data-ttu-id="5edb9-123">Image</span><span class="sxs-lookup"><span data-stu-id="5edb9-123">Image</span></span>
- <span data-ttu-id="5edb9-124">Audio</span><span class="sxs-lookup"><span data-stu-id="5edb9-124">Audio</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5edb9-125">-RAW</span><span class="sxs-lookup"><span data-stu-id="5edb9-125">-Raw</span></span>

<span data-ttu-id="5edb9-126">Obtient la totalité du contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5edb9-126">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="5edb9-127">Le texte multiligne est retourné sous la forme d’une chaîne multiligne unique plutôt que d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5edb9-127">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="5edb9-128">-TextFormatType</span><span class="sxs-lookup"><span data-stu-id="5edb9-128">-TextFormatType</span></span>

<span data-ttu-id="5edb9-129">Spécifie le type de format de données texte du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5edb9-129">Specifies the text data format type of the clipboard.</span></span> <span data-ttu-id="5edb9-130">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="5edb9-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5edb9-131">Texte</span><span class="sxs-lookup"><span data-stu-id="5edb9-131">Text</span></span>
- <span data-ttu-id="5edb9-132">UnicodeText</span><span class="sxs-lookup"><span data-stu-id="5edb9-132">UnicodeText</span></span>
- <span data-ttu-id="5edb9-133">RTF</span><span class="sxs-lookup"><span data-stu-id="5edb9-133">Rtf</span></span>
- <span data-ttu-id="5edb9-134">Html</span><span class="sxs-lookup"><span data-stu-id="5edb9-134">Html</span></span>
- <span data-ttu-id="5edb9-135">CommaSeparatedValue</span><span class="sxs-lookup"><span data-stu-id="5edb9-135">CommaSeparatedValue</span></span>

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5edb9-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5edb9-136">CommonParameters</span></span>

<span data-ttu-id="5edb9-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5edb9-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5edb9-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5edb9-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5edb9-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5edb9-139">INPUTS</span></span>

## <span data-ttu-id="5edb9-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5edb9-140">OUTPUTS</span></span>

### <span data-ttu-id="5edb9-141">System. String, System. IO. FileInfo, System. IO. Stream, System. Drawing. image</span><span class="sxs-lookup"><span data-stu-id="5edb9-141">System.String, System.IO.FileInfo, System.IO.Stream, System.Drawing.Image</span></span>

## <span data-ttu-id="5edb9-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5edb9-142">NOTES</span></span>

## <span data-ttu-id="5edb9-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5edb9-143">RELATED LINKS</span></span>

[<span data-ttu-id="5edb9-144">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="5edb9-144">Set-Clipboard</span></span>](Set-Clipboard.md)

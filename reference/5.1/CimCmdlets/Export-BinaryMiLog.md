---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194363"
---
# <span data-ttu-id="d8d95-103">Export-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="d8d95-103">Export-BinaryMiLog</span></span>

## <span data-ttu-id="d8d95-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d8d95-104">SYNOPSIS</span></span>
<span data-ttu-id="d8d95-105">Crée une représentation codée en binaire d’un ou de tous les objets et le stocke dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d8d95-105">Creates a binary encoded representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="d8d95-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8d95-106">SYNTAX</span></span>

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="d8d95-107">Description</span><span class="sxs-lookup"><span data-stu-id="d8d95-107">DESCRIPTION</span></span>

<span data-ttu-id="d8d95-108">L' `Export-BinaryMILog` applet de commande crée une représentation binaire d’un ou de tous les objets et la stocke dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d8d95-108">The `Export-BinaryMILog` cmdlet creates a binary-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="d8d95-109">Vous pouvez ensuite utiliser l' `Import-BinaryMiLog` applet de commande pour recréer l’objet enregistré en fonction du contenu de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="d8d95-109">You can then use the `Import-BinaryMiLog` cmdlet to re-create the saved object based on the contents of that file.</span></span>

<span data-ttu-id="d8d95-110">Cette applet de commande est semblable à `Import-Clixml` , à ceci près que `Export-BinaryMILog` stocke l’objet résultant dans un fichier encodé binaire.</span><span class="sxs-lookup"><span data-stu-id="d8d95-110">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="d8d95-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d8d95-111">EXAMPLES</span></span>

### <span data-ttu-id="d8d95-112">Exemple 1 : créer une représentation binaire de CimInstances</span><span class="sxs-lookup"><span data-stu-id="d8d95-112">Example 1 - Create a binary representation of CimInstances</span></span>

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

<span data-ttu-id="d8d95-113">Cette commande exporte **CimInstances** dans un fichier journal mi binaire spécifié par le paramètre Path.</span><span class="sxs-lookup"><span data-stu-id="d8d95-113">This command exports **CimInstances** to a binary MI log file specified by the Path parameter.</span></span> <span data-ttu-id="d8d95-114">Consultez l’exemple de Import-BinaryMiLog pour voir comment recréer le **CimInstances** en important ce fichier.</span><span class="sxs-lookup"><span data-stu-id="d8d95-114">See the example for Import-BinaryMiLog to see how to recreate the **CimInstances** by importing this file.</span></span>

## <span data-ttu-id="d8d95-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8d95-115">PARAMETERS</span></span>

### <span data-ttu-id="d8d95-116">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8d95-116">-InputObject</span></span>

<span data-ttu-id="d8d95-117">Spécifie l'entrée de cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8d95-117">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="d8d95-118">Vous pouvez utiliser ce paramètre ou vous adresser l'entrée à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8d95-118">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8d95-119">-Path</span><span class="sxs-lookup"><span data-stu-id="d8d95-119">-Path</span></span>

<span data-ttu-id="d8d95-120">Spécifie le chemin d’accès du fichier dans lequel stocker la représentation binaire de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d8d95-120">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="d8d95-121">Le paramètre **path** prend en charge les caractères génériques et les chemins d’accès relatifs.</span><span class="sxs-lookup"><span data-stu-id="d8d95-121">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="d8d95-122">Cette applet de commande génère une erreur si le chemin d’accès correspond à plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="d8d95-122">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d8d95-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8d95-123">CommonParameters</span></span>

<span data-ttu-id="d8d95-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8d95-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8d95-125">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8d95-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8d95-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d8d95-126">INPUTS</span></span>

### <span data-ttu-id="d8d95-127">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8d95-127">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="d8d95-128">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d8d95-128">OUTPUTS</span></span>

### <span data-ttu-id="d8d95-129">System.Object</span><span class="sxs-lookup"><span data-stu-id="d8d95-129">System.Object</span></span>

## <span data-ttu-id="d8d95-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d8d95-130">NOTES</span></span>

## <span data-ttu-id="d8d95-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d8d95-131">RELATED LINKS</span></span>

[<span data-ttu-id="d8d95-132">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8d95-132">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="d8d95-133">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="d8d95-133">Import-BinaryMiLog</span></span>](import-binarymilog.md)

[<span data-ttu-id="d8d95-134">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="d8d95-134">Import-Clixml</span></span>](../microsoft.powershell.utility/import-clixml.md)

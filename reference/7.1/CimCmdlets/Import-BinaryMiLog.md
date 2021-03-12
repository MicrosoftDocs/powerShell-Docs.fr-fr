---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce777eff8b41fe6bde3c8e00050ec9db87174265
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195880"
---
# <span data-ttu-id="21f04-103">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="21f04-103">Import-BinaryMiLog</span></span>

## <span data-ttu-id="21f04-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="21f04-104">SYNOPSIS</span></span>
<span data-ttu-id="21f04-105">Utilisé pour recréer les objets enregistrés en fonction du contenu d’un fichier d’exportation.</span><span class="sxs-lookup"><span data-stu-id="21f04-105">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="21f04-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21f04-106">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="21f04-107">Description</span><span class="sxs-lookup"><span data-stu-id="21f04-107">DESCRIPTION</span></span>

<span data-ttu-id="21f04-108">Utilisez cette applet de commande pour recréer des objets enregistrés en fonction du contenu d’un fichier d’exportation créé par `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="21f04-108">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="21f04-109">Cette applet de commande est semblable à `Import-Clixml` , à ceci près que `Export-BinaryMILog` stocke l’objet résultant dans un fichier encodé binaire.</span><span class="sxs-lookup"><span data-stu-id="21f04-109">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="21f04-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="21f04-110">EXAMPLES</span></span>

### <span data-ttu-id="21f04-111">Exemple 1 : restaurer les objets exportés vers un fichier</span><span class="sxs-lookup"><span data-stu-id="21f04-111">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="21f04-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21f04-112">PARAMETERS</span></span>

### <span data-ttu-id="21f04-113">-Path</span><span class="sxs-lookup"><span data-stu-id="21f04-113">-Path</span></span>

<span data-ttu-id="21f04-114">Spécifie le chemin d’accès du fichier dans lequel stocker la représentation binaire de l’objet.</span><span class="sxs-lookup"><span data-stu-id="21f04-114">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="21f04-115">Le paramètre **path** prend en charge les caractères génériques et les chemins d’accès relatifs.</span><span class="sxs-lookup"><span data-stu-id="21f04-115">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="21f04-116">Cette applet de commande génère une erreur si le chemin d’accès correspond à plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="21f04-116">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="21f04-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21f04-117">CommonParameters</span></span>
<span data-ttu-id="21f04-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21f04-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21f04-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="21f04-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21f04-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="21f04-120">INPUTS</span></span>

### <span data-ttu-id="21f04-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="21f04-121">None</span></span>

## <span data-ttu-id="21f04-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="21f04-122">OUTPUTS</span></span>

### <span data-ttu-id="21f04-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="21f04-123">System.Object</span></span>

## <span data-ttu-id="21f04-124">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="21f04-124">NOTES</span></span>

## <span data-ttu-id="21f04-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="21f04-125">RELATED LINKS</span></span>

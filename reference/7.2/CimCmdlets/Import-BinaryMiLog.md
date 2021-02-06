---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: 646f3e0990ce451300a28ca0de58576c70c55a9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598762"
---
# <span data-ttu-id="14bbe-102">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="14bbe-102">Import-BinaryMiLog</span></span>

## <span data-ttu-id="14bbe-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="14bbe-103">SYNOPSIS</span></span>
<span data-ttu-id="14bbe-104">Utilisé pour recréer les objets enregistrés en fonction du contenu d’un fichier d’exportation.</span><span class="sxs-lookup"><span data-stu-id="14bbe-104">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="14bbe-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="14bbe-105">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="14bbe-106">Description</span><span class="sxs-lookup"><span data-stu-id="14bbe-106">DESCRIPTION</span></span>

<span data-ttu-id="14bbe-107">Utilisez cette applet de commande pour recréer des objets enregistrés en fonction du contenu d’un fichier d’exportation créé par `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="14bbe-107">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="14bbe-108">Cette applet de commande est semblable à `Import-Clixml` , à ceci près que `Export-BinaryMILog` stocke l’objet résultant dans un fichier encodé binaire.</span><span class="sxs-lookup"><span data-stu-id="14bbe-108">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="14bbe-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="14bbe-109">EXAMPLES</span></span>

### <span data-ttu-id="14bbe-110">Exemple 1 : restaurer les objets exportés vers un fichier</span><span class="sxs-lookup"><span data-stu-id="14bbe-110">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="14bbe-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14bbe-111">PARAMETERS</span></span>

### <span data-ttu-id="14bbe-112">-Path</span><span class="sxs-lookup"><span data-stu-id="14bbe-112">-Path</span></span>

<span data-ttu-id="14bbe-113">Spécifie le chemin d’accès du fichier dans lequel stocker la représentation binaire de l’objet.</span><span class="sxs-lookup"><span data-stu-id="14bbe-113">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="14bbe-114">Le paramètre **path** prend en charge les caractères génériques et les chemins d’accès relatifs.</span><span class="sxs-lookup"><span data-stu-id="14bbe-114">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="14bbe-115">Cette applet de commande génère une erreur si le chemin d’accès correspond à plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="14bbe-115">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="14bbe-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14bbe-116">CommonParameters</span></span>
<span data-ttu-id="14bbe-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14bbe-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14bbe-118">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14bbe-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14bbe-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="14bbe-119">INPUTS</span></span>

### <span data-ttu-id="14bbe-120">None</span><span class="sxs-lookup"><span data-stu-id="14bbe-120">None</span></span>

## <span data-ttu-id="14bbe-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="14bbe-121">OUTPUTS</span></span>

### <span data-ttu-id="14bbe-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="14bbe-122">System.Object</span></span>

## <span data-ttu-id="14bbe-123">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="14bbe-123">NOTES</span></span>

## <span data-ttu-id="14bbe-124">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="14bbe-124">RELATED LINKS</span></span>

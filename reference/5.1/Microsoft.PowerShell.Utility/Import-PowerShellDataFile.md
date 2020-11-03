---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 61e3a7f941155ccf3db84a7e9ec8d2c48b4cceea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203217"
---
# <span data-ttu-id="dcb24-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="dcb24-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="dcb24-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dcb24-104">SYNOPSIS</span></span>
<span data-ttu-id="dcb24-105">Importe des valeurs à partir d’un `.PSD1` fichier sans appeler son contenu.</span><span class="sxs-lookup"><span data-stu-id="dcb24-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="dcb24-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dcb24-106">SYNTAX</span></span>

### <span data-ttu-id="dcb24-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="dcb24-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [[-Path] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="dcb24-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="dcb24-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="dcb24-109">Description</span><span class="sxs-lookup"><span data-stu-id="dcb24-109">DESCRIPTION</span></span>

<span data-ttu-id="dcb24-110">L' `Import-PowerShellDataFile` applet de commande importe en toute sécurité des paires clé-valeur à partir de tables de hachage définies dans un `.PSD1` fichier.</span><span class="sxs-lookup"><span data-stu-id="dcb24-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="dcb24-111">Les valeurs peuvent être importées à l’aide `Invoke-Expression` de sur le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="dcb24-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="dcb24-112">Toutefois, `Invoke-Expression` exécute tout code contenu dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="dcb24-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="dcb24-113">Cela peut produire des résultats indésirables ou exécuter du code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="dcb24-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="dcb24-114">`Import-PowerShellDataFile` importe les données sans appeler le code.</span><span class="sxs-lookup"><span data-stu-id="dcb24-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="dcb24-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dcb24-115">EXAMPLES</span></span>

### <span data-ttu-id="dcb24-116">Exemple 1 : récupérer des valeurs à partir de PSD1</span><span class="sxs-lookup"><span data-stu-id="dcb24-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="dcb24-117">Cet exemple récupère les paires clé-valeur stockées dans la Hashtable conservée dans le `Configuration.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="dcb24-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="dcb24-118">`Get-Content` est utilisé pour afficher le contenu du `Configuration.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="dcb24-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="dcb24-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dcb24-119">PARAMETERS</span></span>

### <span data-ttu-id="dcb24-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dcb24-120">-LiteralPath</span></span>

<span data-ttu-id="dcb24-121">Chemin d’accès au fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="dcb24-121">The path to the file being imported.</span></span> <span data-ttu-id="dcb24-122">Tous les caractères du chemin d’accès sont traités comme des valeurs littérales.</span><span class="sxs-lookup"><span data-stu-id="dcb24-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="dcb24-123">Les caractères génériques ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="dcb24-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dcb24-124">-Path</span><span class="sxs-lookup"><span data-stu-id="dcb24-124">-Path</span></span>

<span data-ttu-id="dcb24-125">Chemin d’accès au fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="dcb24-125">The path to the file being imported.</span></span> <span data-ttu-id="dcb24-126">Les caractères génériques sont autorisés, mais seul le premier fichier correspondant est importé.</span><span class="sxs-lookup"><span data-stu-id="dcb24-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="dcb24-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dcb24-127">CommonParameters</span></span>

<span data-ttu-id="dcb24-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dcb24-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dcb24-129">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dcb24-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dcb24-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dcb24-130">INPUTS</span></span>

## <span data-ttu-id="dcb24-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dcb24-131">OUTPUTS</span></span>

### <span data-ttu-id="dcb24-132">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="dcb24-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="dcb24-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dcb24-133">NOTES</span></span>

## <span data-ttu-id="dcb24-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dcb24-134">RELATED LINKS</span></span>

[<span data-ttu-id="dcb24-135">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="dcb24-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="dcb24-136">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="dcb24-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)

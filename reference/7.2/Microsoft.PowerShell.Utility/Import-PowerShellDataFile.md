---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "99599138"
---
# <span data-ttu-id="3b430-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="3b430-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="3b430-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3b430-103">SYNOPSIS</span></span>
<span data-ttu-id="3b430-104">Importe des valeurs à partir d’un `.PSD1` fichier sans appeler son contenu.</span><span class="sxs-lookup"><span data-stu-id="3b430-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="3b430-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3b430-105">SYNTAX</span></span>

### <span data-ttu-id="3b430-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3b430-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### <span data-ttu-id="3b430-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3b430-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## <span data-ttu-id="3b430-108">Description</span><span class="sxs-lookup"><span data-stu-id="3b430-108">DESCRIPTION</span></span>

<span data-ttu-id="3b430-109">L' `Import-PowerShellDataFile` applet de commande importe en toute sécurité des paires clé-valeur à partir de tables de hachage définies dans un `.PSD1` fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="3b430-110">Les valeurs peuvent être importées à l’aide `Invoke-Expression` de sur le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="3b430-111">Toutefois, `Invoke-Expression` exécute tout code contenu dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="3b430-112">Cela peut produire des résultats indésirables ou exécuter du code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="3b430-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="3b430-113">`Import-PowerShellDataFile` importe les données sans appeler le code.</span><span class="sxs-lookup"><span data-stu-id="3b430-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span> <span data-ttu-id="3b430-114">Par défaut, il existe une limite de clé de 500, mais elle peut être ignorée avec le commutateur **SkipLimitCheck** .</span><span class="sxs-lookup"><span data-stu-id="3b430-114">By default there is a 500 key limit but can be bypassed with the **SkipLimitCheck** switch.</span></span>

## <span data-ttu-id="3b430-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3b430-115">EXAMPLES</span></span>

### <span data-ttu-id="3b430-116">Exemple 1 : récupérer des valeurs à partir de PSD1</span><span class="sxs-lookup"><span data-stu-id="3b430-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="3b430-117">Cet exemple récupère les paires clé-valeur stockées dans la Hashtable conservée dans le `Configuration.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="3b430-118">`Get-Content` est utilisé pour afficher le contenu du `Configuration.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="3b430-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3b430-119">PARAMETERS</span></span>

### <span data-ttu-id="3b430-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3b430-120">-LiteralPath</span></span>

<span data-ttu-id="3b430-121">Chemin d’accès au fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="3b430-121">The path to the file being imported.</span></span> <span data-ttu-id="3b430-122">Tous les caractères du chemin d’accès sont traités comme des valeurs littérales.</span><span class="sxs-lookup"><span data-stu-id="3b430-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="3b430-123">Les caractères génériques ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="3b430-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3b430-124">-Path</span><span class="sxs-lookup"><span data-stu-id="3b430-124">-Path</span></span>

<span data-ttu-id="3b430-125">Chemin d’accès au fichier en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="3b430-125">The path to the file being imported.</span></span> <span data-ttu-id="3b430-126">Les caractères génériques sont autorisés, mais seul le premier fichier correspondant est importé.</span><span class="sxs-lookup"><span data-stu-id="3b430-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3b430-127">-SkipLimitCheck</span><span class="sxs-lookup"><span data-stu-id="3b430-127">-SkipLimitCheck</span></span>

<span data-ttu-id="3b430-128">Par défaut, `Import-PowerShellDataFile` seules les clés 500 sont importées à partir d’un `.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="3b430-128">By default `Import-PowerShellDataFile` imports only 500 keys from a `.psd1` file.</span></span> <span data-ttu-id="3b430-129">Utilisez **SkipLimitCheck** pour importer plus de 500 clés.</span><span class="sxs-lookup"><span data-stu-id="3b430-129">Use **SkipLimitCheck** to import more than 500 keys.</span></span>

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3b430-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b430-130">CommonParameters</span></span>

<span data-ttu-id="3b430-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3b430-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b430-132">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3b430-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3b430-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3b430-133">INPUTS</span></span>

## <span data-ttu-id="3b430-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3b430-134">OUTPUTS</span></span>

### <span data-ttu-id="3b430-135">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="3b430-135">System.Collections.Hashtable</span></span>

## <span data-ttu-id="3b430-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3b430-136">NOTES</span></span>

## <span data-ttu-id="3b430-137">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3b430-137">RELATED LINKS</span></span>

[<span data-ttu-id="3b430-138">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="3b430-138">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="3b430-139">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="3b430-139">Import-LocalizedData</span></span>](Import-LocalizedData.md)

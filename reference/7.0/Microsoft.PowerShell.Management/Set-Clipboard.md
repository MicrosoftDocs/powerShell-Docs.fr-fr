---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 271d9191a0968b03b1e7ec3d283eacc36e633516
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239800"
---
# <span data-ttu-id="ea8e3-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="ea8e3-103">Set-Clipboard</span></span>

## <span data-ttu-id="ea8e3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ea8e3-104">SYNOPSIS</span></span>
<span data-ttu-id="ea8e3-105">Définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="ea8e3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea8e3-106">SYNTAX</span></span>

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ea8e3-107">Description</span><span class="sxs-lookup"><span data-stu-id="ea8e3-107">DESCRIPTION</span></span>

<span data-ttu-id="ea8e3-108">L' `Set-Clipboard` applet de commande définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="ea8e3-109">Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="ea8e3-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ea8e3-110">EXAMPLES</span></span>

### <span data-ttu-id="ea8e3-111">Exemple 1 : copier du texte dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="ea8e3-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

## <span data-ttu-id="ea8e3-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea8e3-112">PARAMETERS</span></span>

### <span data-ttu-id="ea8e3-113">-Append</span><span class="sxs-lookup"><span data-stu-id="ea8e3-113">-Append</span></span>

<span data-ttu-id="ea8e3-114">Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-114">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="ea8e3-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ea8e3-115">-Confirm</span></span>

<span data-ttu-id="ea8e3-116">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ea8e3-117">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ea8e3-117">-WhatIf</span></span>

<span data-ttu-id="ea8e3-118">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-118">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ea8e3-119">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-119">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ea8e3-120">-Value</span><span class="sxs-lookup"><span data-stu-id="ea8e3-120">-Value</span></span>

<span data-ttu-id="ea8e3-121">Valeurs de chaîne à ajouter au Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-121">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ea8e3-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea8e3-122">CommonParameters</span></span>

<span data-ttu-id="ea8e3-123">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea8e3-124">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ea8e3-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea8e3-125">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ea8e3-125">INPUTS</span></span>

### <span data-ttu-id="ea8e3-126">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ea8e3-126">System.String[]</span></span>

## <span data-ttu-id="ea8e3-127">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ea8e3-127">OUTPUTS</span></span>

## <span data-ttu-id="ea8e3-128">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ea8e3-128">NOTES</span></span>

<span data-ttu-id="ea8e3-129">Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-129">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="ea8e3-130">Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="ea8e3-130">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="ea8e3-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ea8e3-131">RELATED LINKS</span></span>

[<span data-ttu-id="ea8e3-132">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="ea8e3-132">Get-Clipboard</span></span>](Get-Clipboard.md)

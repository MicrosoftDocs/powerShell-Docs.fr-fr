---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: efb24b14122ad37043636d999afaa4199eb3097b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564371"
---
# <span data-ttu-id="98414-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="98414-102">Set-Clipboard</span></span>

## <span data-ttu-id="98414-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="98414-103">SYNOPSIS</span></span>
<span data-ttu-id="98414-104">Définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="98414-104">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="98414-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="98414-105">SYNTAX</span></span>

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98414-106">Description</span><span class="sxs-lookup"><span data-stu-id="98414-106">DESCRIPTION</span></span>

<span data-ttu-id="98414-107">L' `Set-Clipboard` applet de commande définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="98414-107">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="98414-108">Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="98414-108">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="98414-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="98414-109">EXAMPLES</span></span>

### <span data-ttu-id="98414-110">Exemple 1 : copier du texte dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="98414-110">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="98414-111">Exemple 2 : copier le contenu d’un fichier dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="98414-111">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="98414-112">Cet exemple canalise le contenu d’un fichier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="98414-112">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="98414-113">Dans cet exemple, nous obtenons une clé SSH publique pour pouvoir la coller dans une autre application, par exemple GitHub.</span><span class="sxs-lookup"><span data-stu-id="98414-113">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="98414-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98414-114">PARAMETERS</span></span>

### <span data-ttu-id="98414-115">-Append</span><span class="sxs-lookup"><span data-stu-id="98414-115">-Append</span></span>

<span data-ttu-id="98414-116">Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.</span><span class="sxs-lookup"><span data-stu-id="98414-116">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="98414-117">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98414-117">-Confirm</span></span>

<span data-ttu-id="98414-118">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98414-118">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98414-119">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98414-119">-WhatIf</span></span>

<span data-ttu-id="98414-120">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98414-120">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="98414-121">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="98414-121">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="98414-122">-Value</span><span class="sxs-lookup"><span data-stu-id="98414-122">-Value</span></span>

<span data-ttu-id="98414-123">Valeurs de chaîne à ajouter au Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="98414-123">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="98414-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98414-124">CommonParameters</span></span>

<span data-ttu-id="98414-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98414-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98414-126">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98414-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98414-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="98414-127">INPUTS</span></span>

### <span data-ttu-id="98414-128">System.String[]</span><span class="sxs-lookup"><span data-stu-id="98414-128">System.String[]</span></span>

## <span data-ttu-id="98414-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="98414-129">OUTPUTS</span></span>

## <span data-ttu-id="98414-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="98414-130">NOTES</span></span>

<span data-ttu-id="98414-131">Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="98414-131">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="98414-132">Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="98414-132">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="98414-133">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="98414-133">RELATED LINKS</span></span>

[<span data-ttu-id="98414-134">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="98414-134">Get-Clipboard</span></span>](Get-Clipboard.md)

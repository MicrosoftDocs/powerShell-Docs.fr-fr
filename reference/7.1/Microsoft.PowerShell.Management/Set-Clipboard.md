---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564552"
---
# <span data-ttu-id="b2a34-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="b2a34-103">Set-Clipboard</span></span>

## <span data-ttu-id="b2a34-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b2a34-104">SYNOPSIS</span></span>
<span data-ttu-id="b2a34-105">Définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b2a34-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="b2a34-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b2a34-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b2a34-107">Description</span><span class="sxs-lookup"><span data-stu-id="b2a34-107">DESCRIPTION</span></span>

<span data-ttu-id="b2a34-108">L' `Set-Clipboard` applet de commande définit le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b2a34-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="b2a34-109">Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="b2a34-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="b2a34-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b2a34-110">EXAMPLES</span></span>

### <span data-ttu-id="b2a34-111">Exemple 1 : copier du texte dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="b2a34-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="b2a34-112">Exemple 2 : copier le contenu d’un fichier dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="b2a34-112">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="b2a34-113">Cet exemple canalise le contenu d’un fichier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b2a34-113">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="b2a34-114">Dans cet exemple, nous obtenons une clé SSH publique pour pouvoir la coller dans une autre application, par exemple GitHub.</span><span class="sxs-lookup"><span data-stu-id="b2a34-114">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="b2a34-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2a34-115">PARAMETERS</span></span>

### <span data-ttu-id="b2a34-116">-Append</span><span class="sxs-lookup"><span data-stu-id="b2a34-116">-Append</span></span>

<span data-ttu-id="b2a34-117">Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.</span><span class="sxs-lookup"><span data-stu-id="b2a34-117">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="b2a34-118">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b2a34-118">-Confirm</span></span>

<span data-ttu-id="b2a34-119">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2a34-119">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b2a34-120">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b2a34-120">-WhatIf</span></span>

<span data-ttu-id="b2a34-121">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2a34-121">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b2a34-122">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2a34-122">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b2a34-123">-Value</span><span class="sxs-lookup"><span data-stu-id="b2a34-123">-Value</span></span>

<span data-ttu-id="b2a34-124">Valeurs de chaîne à ajouter au Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b2a34-124">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="b2a34-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2a34-125">CommonParameters</span></span>

<span data-ttu-id="b2a34-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2a34-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2a34-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b2a34-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2a34-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b2a34-128">INPUTS</span></span>

### <span data-ttu-id="b2a34-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b2a34-129">System.String[]</span></span>

## <span data-ttu-id="b2a34-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b2a34-130">OUTPUTS</span></span>

## <span data-ttu-id="b2a34-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b2a34-131">NOTES</span></span>

<span data-ttu-id="b2a34-132">Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b2a34-132">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="b2a34-133">Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="b2a34-133">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="b2a34-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b2a34-134">RELATED LINKS</span></span>

[<span data-ttu-id="b2a34-135">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="b2a34-135">Get-Clipboard</span></span>](Get-Clipboard.md)

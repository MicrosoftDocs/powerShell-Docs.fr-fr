---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadline
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: e0cdd2358cfd4819285947b1f703963691088e2b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208621"
---
# <span data-ttu-id="3d5e4-103">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="3d5e4-103">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="3d5e4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3d5e4-104">SYNOPSIS</span></span>
<span data-ttu-id="3d5e4-105">Supprime une combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-105">Removes a key binding.</span></span>

## <span data-ttu-id="3d5e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d5e4-106">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="3d5e4-107">Description</span><span class="sxs-lookup"><span data-stu-id="3d5e4-107">DESCRIPTION</span></span>

<span data-ttu-id="3d5e4-108">L' `Remove-PSReadLineKeyHandler` applet de commande supprime une combinaison de touches spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-108">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="3d5e4-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3d5e4-109">EXAMPLES</span></span>

### <span data-ttu-id="3d5e4-110">Exemple 1 : supprimer une liaison</span><span class="sxs-lookup"><span data-stu-id="3d5e4-110">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="3d5e4-111">Cette commande supprime la liaison de la combinaison de touches, ou corde `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="3d5e4-111">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="3d5e4-112">Le `Ctrl+B` segment est créé dans l' `Set-PSReadLineKeyHandler` article.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-112">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="3d5e4-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d5e4-113">PARAMETERS</span></span>

### <span data-ttu-id="3d5e4-114">-Corde</span><span class="sxs-lookup"><span data-stu-id="3d5e4-114">-Chord</span></span>

<span data-ttu-id="3d5e4-115">Spécifie un tableau de clés ou de séquences de clés à supprimer.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-115">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="3d5e4-116">Une seule liaison est spécifiée à l’aide d’une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-116">A single binding is specified by using a single string.</span></span> <span data-ttu-id="3d5e4-117">Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3d5e4-117">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="3d5e4-118">Ce paramètre accepte un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-118">This parameter accepts an array of strings.</span></span> <span data-ttu-id="3d5e4-119">Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-119">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d5e4-120">-ViMode</span><span class="sxs-lookup"><span data-stu-id="3d5e4-120">-ViMode</span></span>

<span data-ttu-id="3d5e4-121">Spécifiez le mode VI auquel la liaison s’applique.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-121">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="3d5e4-122">Les valeurs possibles sont : Insert, Command.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-122">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d5e4-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d5e4-123">CommonParameters</span></span>

<span data-ttu-id="3d5e4-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d5e4-125">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3d5e4-125">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d5e4-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3d5e4-126">INPUTS</span></span>

### <span data-ttu-id="3d5e4-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="3d5e4-127">None</span></span>

<span data-ttu-id="3d5e4-128">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3d5e4-128">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3d5e4-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3d5e4-129">OUTPUTS</span></span>

### <span data-ttu-id="3d5e4-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="3d5e4-130">None</span></span>

## <span data-ttu-id="3d5e4-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3d5e4-131">NOTES</span></span>

## <span data-ttu-id="3d5e4-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3d5e4-132">RELATED LINKS</span></span>

[<span data-ttu-id="3d5e4-133">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="3d5e4-133">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="3d5e4-134">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="3d5e4-134">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="3d5e4-135">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="3d5e4-135">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="3d5e4-136">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="3d5e4-136">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

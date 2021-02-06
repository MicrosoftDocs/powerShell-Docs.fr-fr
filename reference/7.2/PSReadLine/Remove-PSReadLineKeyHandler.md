---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596928"
---
# <span data-ttu-id="4f245-102">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="4f245-102">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="4f245-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f245-103">SYNOPSIS</span></span>
<span data-ttu-id="4f245-104">Supprime une combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="4f245-104">Removes a key binding.</span></span>

## <span data-ttu-id="4f245-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4f245-105">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="4f245-106">Description</span><span class="sxs-lookup"><span data-stu-id="4f245-106">DESCRIPTION</span></span>

<span data-ttu-id="4f245-107">L' `Remove-PSReadLineKeyHandler` applet de commande supprime une combinaison de touches spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4f245-107">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="4f245-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f245-108">EXAMPLES</span></span>

### <span data-ttu-id="4f245-109">Exemple 1 : supprimer une liaison</span><span class="sxs-lookup"><span data-stu-id="4f245-109">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="4f245-110">Cette commande supprime la liaison de la combinaison de touches, ou corde `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="4f245-110">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="4f245-111">Le `Ctrl+B` segment est créé dans l' `Set-PSReadLineKeyHandler` article.</span><span class="sxs-lookup"><span data-stu-id="4f245-111">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="4f245-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f245-112">PARAMETERS</span></span>

### <span data-ttu-id="4f245-113">-Corde</span><span class="sxs-lookup"><span data-stu-id="4f245-113">-Chord</span></span>

<span data-ttu-id="4f245-114">Spécifie un tableau de clés ou de séquences de clés à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4f245-114">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="4f245-115">Une seule liaison est spécifiée à l’aide d’une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="4f245-115">A single binding is specified by using a single string.</span></span> <span data-ttu-id="4f245-116">Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4f245-116">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="4f245-117">Ce paramètre accepte un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="4f245-117">This parameter accepts an array of strings.</span></span> <span data-ttu-id="4f245-118">Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.</span><span class="sxs-lookup"><span data-stu-id="4f245-118">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="4f245-119">-ViMode</span><span class="sxs-lookup"><span data-stu-id="4f245-119">-ViMode</span></span>

<span data-ttu-id="4f245-120">Spécifiez le mode VI auquel la liaison s’applique.</span><span class="sxs-lookup"><span data-stu-id="4f245-120">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="4f245-121">Les valeurs possibles sont : Insert, Command.</span><span class="sxs-lookup"><span data-stu-id="4f245-121">Possible values are: Insert, Command.</span></span>

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

### <span data-ttu-id="4f245-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f245-122">CommonParameters</span></span>

<span data-ttu-id="4f245-123">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f245-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f245-124">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f245-124">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f245-125">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f245-125">INPUTS</span></span>

### <span data-ttu-id="4f245-126">None</span><span class="sxs-lookup"><span data-stu-id="4f245-126">None</span></span>

<span data-ttu-id="4f245-127">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4f245-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4f245-128">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f245-128">OUTPUTS</span></span>

### <span data-ttu-id="4f245-129">None</span><span class="sxs-lookup"><span data-stu-id="4f245-129">None</span></span>

## <span data-ttu-id="4f245-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f245-130">NOTES</span></span>

## <span data-ttu-id="4f245-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f245-131">RELATED LINKS</span></span>

[<span data-ttu-id="4f245-132">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="4f245-132">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="4f245-133">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="4f245-133">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="4f245-134">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="4f245-134">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="4f245-135">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="4f245-135">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)


---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 19871bcfd1e045ab30bfef0dc88aa42a4c4aecf4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204482"
---
# <span data-ttu-id="4f98b-103">Out-Default</span><span class="sxs-lookup"><span data-stu-id="4f98b-103">Out-Default</span></span>

## <span data-ttu-id="4f98b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f98b-104">SYNOPSIS</span></span>
<span data-ttu-id="4f98b-105">Envoie la sortie au formateur par défaut et à l'applet de commande de sortie par défaut.</span><span class="sxs-lookup"><span data-stu-id="4f98b-105">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="4f98b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f98b-106">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="4f98b-107">Description</span><span class="sxs-lookup"><span data-stu-id="4f98b-107">DESCRIPTION</span></span>

<span data-ttu-id="4f98b-108">PowerShell ajoute automatiquement `Out-Default` à la fin de chaque pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f98b-108">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="4f98b-109">`Out-Default` décide comment mettre en forme et sortir le flux d’objet.</span><span class="sxs-lookup"><span data-stu-id="4f98b-109">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="4f98b-110">Si le flux d’objet est un flux de chaînes, les dirige `Out-Default` directement vers `Out-Host` qui appellent les API appropriées fournies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="4f98b-110">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="4f98b-111">Si le flux d’objet ne contient pas de chaînes, `Out-Default` inspecte l’objet pour déterminer ce qu’il doit faire.</span><span class="sxs-lookup"><span data-stu-id="4f98b-111">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="4f98b-112">Tout d’abord, il examine le type d’objet et détermine s’il existe une _vue_ inscrite pour ce type d’objet.</span><span class="sxs-lookup"><span data-stu-id="4f98b-112">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="4f98b-113">PowerShell définit le schéma XML et un mécanisme (l’applet de commande `Update-FormatData` ) où tout le monde peut inscrire des vues pour un type d’objet.</span><span class="sxs-lookup"><span data-stu-id="4f98b-113">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="4f98b-114">Vous pouvez spécifier des vues **larges** , des **listes** , des **tables** ou des vues **personnalisées** pour tout type d’objet.</span><span class="sxs-lookup"><span data-stu-id="4f98b-114">You can specify **wide** , **list** , **table** , or **custom** views for any object type.</span></span> <span data-ttu-id="4f98b-115">Les vues spécifient les propriétés à afficher et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="4f98b-115">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="4f98b-116">Si une vue est inscrite, elle définit le formateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4f98b-116">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="4f98b-117">Ainsi, si la vue inscrite est une vue de **table** , `Out-Default` transmet les objets à `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="4f98b-117">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="4f98b-118">`Format-Table` transforme les objets en un flux d’enregistrements de mise en forme (piloté par les données dans la définition de la vue) et `Out-Host` transforme les enregistrements de mise en forme en appels sur l’interface hôte.</span><span class="sxs-lookup"><span data-stu-id="4f98b-118">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="4f98b-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f98b-119">EXAMPLES</span></span>

### <span data-ttu-id="4f98b-120">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="4f98b-120">Example 1</span></span>

<span data-ttu-id="4f98b-121">Bien que cette applet de commande ne soit pas destinée à être exécutée directement par l’utilisateur final, elle peut avoir la valeur.</span><span class="sxs-lookup"><span data-stu-id="4f98b-121">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="4f98b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f98b-122">PARAMETERS</span></span>

### <span data-ttu-id="4f98b-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4f98b-123">-InputObject</span></span>

<span data-ttu-id="4f98b-124">Accepte une entrée dans l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4f98b-124">Accepts input to the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f98b-125">-Transcription</span><span class="sxs-lookup"><span data-stu-id="4f98b-125">-Transcript</span></span>

<span data-ttu-id="4f98b-126">Détermine si la sortie doit être envoyée aux services de transcription de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f98b-126">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

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

### <span data-ttu-id="4f98b-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f98b-127">CommonParameters</span></span>

<span data-ttu-id="4f98b-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f98b-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f98b-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f98b-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f98b-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f98b-130">INPUTS</span></span>

## <span data-ttu-id="4f98b-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f98b-131">OUTPUTS</span></span>

## <span data-ttu-id="4f98b-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f98b-132">NOTES</span></span>

## <span data-ttu-id="4f98b-133">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f98b-133">RELATED LINKS</span></span>

[<span data-ttu-id="4f98b-134">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4f98b-134">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="4f98b-135">Format-List</span><span class="sxs-lookup"><span data-stu-id="4f98b-135">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="4f98b-136">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4f98b-136">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="4f98b-137">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4f98b-137">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="4f98b-138">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="4f98b-138">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="4f98b-139">Fonctionnement de la mise en forme et du sortir de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f98b-139">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

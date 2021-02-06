---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: d650a9280982703e09ec22698c3848a616abb067
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597958"
---
# <span data-ttu-id="0c84d-102">Out-Default</span><span class="sxs-lookup"><span data-stu-id="0c84d-102">Out-Default</span></span>

## <span data-ttu-id="0c84d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0c84d-103">SYNOPSIS</span></span>
<span data-ttu-id="0c84d-104">Envoie la sortie au formateur par défaut et à l'applet de commande de sortie par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c84d-104">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="0c84d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0c84d-105">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="0c84d-106">Description</span><span class="sxs-lookup"><span data-stu-id="0c84d-106">DESCRIPTION</span></span>

<span data-ttu-id="0c84d-107">PowerShell ajoute automatiquement `Out-Default` à la fin de chaque pipeline.</span><span class="sxs-lookup"><span data-stu-id="0c84d-107">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="0c84d-108">`Out-Default` décide comment mettre en forme et sortir le flux d’objet.</span><span class="sxs-lookup"><span data-stu-id="0c84d-108">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="0c84d-109">Si le flux d’objet est un flux de chaînes, les dirige `Out-Default` directement vers `Out-Host` qui appellent les API appropriées fournies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0c84d-109">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="0c84d-110">Si le flux d’objet ne contient pas de chaînes, `Out-Default` inspecte l’objet pour déterminer ce qu’il doit faire.</span><span class="sxs-lookup"><span data-stu-id="0c84d-110">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="0c84d-111">Tout d’abord, il examine le type d’objet et détermine s’il existe une _vue_ inscrite pour ce type d’objet.</span><span class="sxs-lookup"><span data-stu-id="0c84d-111">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="0c84d-112">PowerShell définit le schéma XML et un mécanisme (l’applet de commande `Update-FormatData` ) où tout le monde peut inscrire des vues pour un type d’objet.</span><span class="sxs-lookup"><span data-stu-id="0c84d-112">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="0c84d-113">Vous pouvez spécifier des vues **larges**, des **listes**, des **tables** ou des vues **personnalisées** pour tout type d’objet.</span><span class="sxs-lookup"><span data-stu-id="0c84d-113">You can specify **wide**, **list**, **table**, or **custom** views for any object type.</span></span> <span data-ttu-id="0c84d-114">Les vues spécifient les propriétés à afficher et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="0c84d-114">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="0c84d-115">Si une vue est inscrite, elle définit le formateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0c84d-115">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="0c84d-116">Ainsi, si la vue inscrite est une vue de **table** , `Out-Default` transmet les objets à `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="0c84d-116">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="0c84d-117">`Format-Table` transforme les objets en un flux d’enregistrements de mise en forme (piloté par les données dans la définition de la vue) et `Out-Host` transforme les enregistrements de mise en forme en appels sur l’interface hôte.</span><span class="sxs-lookup"><span data-stu-id="0c84d-117">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="0c84d-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0c84d-118">EXAMPLES</span></span>

### <span data-ttu-id="0c84d-119">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="0c84d-119">Example 1</span></span>

<span data-ttu-id="0c84d-120">Bien que cette applet de commande ne soit pas destinée à être exécutée directement par l’utilisateur final, elle peut avoir la valeur.</span><span class="sxs-lookup"><span data-stu-id="0c84d-120">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

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

## <span data-ttu-id="0c84d-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c84d-121">PARAMETERS</span></span>

### <span data-ttu-id="0c84d-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0c84d-122">-InputObject</span></span>

<span data-ttu-id="0c84d-123">Accepte une entrée dans l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0c84d-123">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="0c84d-124">-Transcription</span><span class="sxs-lookup"><span data-stu-id="0c84d-124">-Transcript</span></span>

<span data-ttu-id="0c84d-125">Détermine si la sortie doit être envoyée aux services de transcription de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c84d-125">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

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

### <span data-ttu-id="0c84d-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c84d-126">CommonParameters</span></span>

<span data-ttu-id="0c84d-127">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0c84d-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c84d-128">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0c84d-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c84d-129">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0c84d-129">INPUTS</span></span>

## <span data-ttu-id="0c84d-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0c84d-130">OUTPUTS</span></span>

## <span data-ttu-id="0c84d-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0c84d-131">NOTES</span></span>

## <span data-ttu-id="0c84d-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0c84d-132">RELATED LINKS</span></span>

[<span data-ttu-id="0c84d-133">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="0c84d-133">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="0c84d-134">Format-List</span><span class="sxs-lookup"><span data-stu-id="0c84d-134">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="0c84d-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="0c84d-135">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="0c84d-136">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="0c84d-136">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="0c84d-137">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="0c84d-137">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="0c84d-138">Fonctionnement de la mise en forme et du sortir de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c84d-138">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)


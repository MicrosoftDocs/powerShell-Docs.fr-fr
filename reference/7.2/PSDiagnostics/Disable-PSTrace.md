---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 0e246a0e3737f4ed693ed31096fc76e878a4af54
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598590"
---
# <span data-ttu-id="f5184-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f5184-102">Disable-PSTrace</span></span>

## <span data-ttu-id="f5184-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f5184-103">SYNOPSIS</span></span>
<span data-ttu-id="f5184-104">Désactive les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5184-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="f5184-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f5184-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="f5184-106">Description</span><span class="sxs-lookup"><span data-stu-id="f5184-106">DESCRIPTION</span></span>

<span data-ttu-id="f5184-107">Cette applet de commande désactive les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5184-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="f5184-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f5184-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f5184-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f5184-109">EXAMPLES</span></span>

### <span data-ttu-id="f5184-110">Exemple 1 : désactiver le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5184-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="f5184-111">L’exemple suivant désactive uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5184-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="f5184-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f5184-112">PARAMETERS</span></span>

### <span data-ttu-id="f5184-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="f5184-113">-AnalyticOnly</span></span>

<span data-ttu-id="f5184-114">Lorsque ce paramètre est utilisé, l’applet de commande désactive le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5184-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="f5184-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="f5184-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="f5184-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f5184-116">CommonParameters</span></span>
<span data-ttu-id="f5184-117">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f5184-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f5184-118">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f5184-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f5184-119">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f5184-119">INPUTS</span></span>

### <span data-ttu-id="f5184-120">None</span><span class="sxs-lookup"><span data-stu-id="f5184-120">None</span></span>

## <span data-ttu-id="f5184-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f5184-121">OUTPUTS</span></span>

### <span data-ttu-id="f5184-122">None</span><span class="sxs-lookup"><span data-stu-id="f5184-122">None</span></span>

## <span data-ttu-id="f5184-123">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f5184-123">NOTES</span></span>

<span data-ttu-id="f5184-124">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="f5184-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="f5184-125">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f5184-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f5184-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f5184-126">RELATED LINKS</span></span>

[<span data-ttu-id="f5184-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f5184-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="f5184-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f5184-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="f5184-129">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f5184-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)


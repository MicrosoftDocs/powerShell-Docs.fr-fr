---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194521"
---
# <span data-ttu-id="d89b2-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d89b2-102">Disable-PSTrace</span></span>

## <span data-ttu-id="d89b2-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d89b2-103">SYNOPSIS</span></span>
<span data-ttu-id="d89b2-104">Désactive les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d89b2-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="d89b2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d89b2-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="d89b2-106">Description</span><span class="sxs-lookup"><span data-stu-id="d89b2-106">DESCRIPTION</span></span>

<span data-ttu-id="d89b2-107">Cette applet de commande désactive les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d89b2-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="d89b2-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="d89b2-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d89b2-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d89b2-109">EXAMPLES</span></span>

### <span data-ttu-id="d89b2-110">Exemple 1 : désactiver le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="d89b2-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="d89b2-111">L’exemple suivant désactive uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d89b2-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="d89b2-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d89b2-112">PARAMETERS</span></span>

### <span data-ttu-id="d89b2-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="d89b2-113">-AnalyticOnly</span></span>

<span data-ttu-id="d89b2-114">Lorsque ce paramètre est utilisé, l’applet de commande désactive le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d89b2-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="d89b2-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="d89b2-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="d89b2-116">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d89b2-116">INPUTS</span></span>

### <span data-ttu-id="d89b2-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="d89b2-117">None</span></span>

## <span data-ttu-id="d89b2-118">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d89b2-118">OUTPUTS</span></span>

### <span data-ttu-id="d89b2-119">System.Object</span><span class="sxs-lookup"><span data-stu-id="d89b2-119">System.Object</span></span>

## <span data-ttu-id="d89b2-120">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d89b2-120">NOTES</span></span>

<span data-ttu-id="d89b2-121">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="d89b2-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="d89b2-122">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="d89b2-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d89b2-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d89b2-123">RELATED LINKS</span></span>

[<span data-ttu-id="d89b2-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d89b2-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="d89b2-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d89b2-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="d89b2-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d89b2-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)

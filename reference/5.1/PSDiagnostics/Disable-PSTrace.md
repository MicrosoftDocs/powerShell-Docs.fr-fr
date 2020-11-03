---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: fc58e0bcfdd0b4ee7c7ee383b44f7d7f428c34c0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203069"
---
# <span data-ttu-id="fade6-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="fade6-102">Disable-PSTrace</span></span>

## <span data-ttu-id="fade6-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fade6-103">SYNOPSIS</span></span>
<span data-ttu-id="fade6-104">Désactive les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fade6-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="fade6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fade6-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="fade6-106">Description</span><span class="sxs-lookup"><span data-stu-id="fade6-106">DESCRIPTION</span></span>

<span data-ttu-id="fade6-107">Cette applet de commande désactive les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fade6-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="fade6-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="fade6-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fade6-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fade6-109">EXAMPLES</span></span>

### <span data-ttu-id="fade6-110">Exemple 1 : désactiver le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="fade6-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="fade6-111">L’exemple suivant désactive uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fade6-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="fade6-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fade6-112">PARAMETERS</span></span>

### <span data-ttu-id="fade6-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="fade6-113">-AnalyticOnly</span></span>

<span data-ttu-id="fade6-114">Lorsque ce paramètre est utilisé, l’applet de commande désactive le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fade6-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="fade6-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="fade6-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="fade6-116">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fade6-116">INPUTS</span></span>

### <span data-ttu-id="fade6-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="fade6-117">None</span></span>

## <span data-ttu-id="fade6-118">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fade6-118">OUTPUTS</span></span>

### <span data-ttu-id="fade6-119">System.Object</span><span class="sxs-lookup"><span data-stu-id="fade6-119">System.Object</span></span>

## <span data-ttu-id="fade6-120">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fade6-120">NOTES</span></span>

<span data-ttu-id="fade6-121">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="fade6-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="fade6-122">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="fade6-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fade6-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fade6-123">RELATED LINKS</span></span>

[<span data-ttu-id="fade6-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="fade6-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="fade6-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="fade6-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="fade6-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="fade6-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)

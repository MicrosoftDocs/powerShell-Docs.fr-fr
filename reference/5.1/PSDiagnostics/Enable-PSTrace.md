---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 2ec01393a46de84b59f06995473bdff6bd5b2b4f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195024"
---
# <span data-ttu-id="dc619-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="dc619-102">Enable-PSTrace</span></span>

## <span data-ttu-id="dc619-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dc619-103">SYNOPSIS</span></span>
<span data-ttu-id="dc619-104">Active les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc619-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="dc619-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc619-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="dc619-106">Description</span><span class="sxs-lookup"><span data-stu-id="dc619-106">DESCRIPTION</span></span>

<span data-ttu-id="dc619-107">Cette applet de commande active les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc619-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="dc619-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="dc619-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="dc619-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dc619-109">EXAMPLES</span></span>

### <span data-ttu-id="dc619-110">Exemple 1 : activer le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc619-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="dc619-111">L’exemple suivant active uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc619-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="dc619-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc619-112">PARAMETERS</span></span>

### <span data-ttu-id="dc619-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="dc619-113">-AnalyticOnly</span></span>

<span data-ttu-id="dc619-114">Lorsque ce paramètre est utilisé, l’applet de commande active le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc619-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="dc619-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="dc619-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="dc619-116">-Force</span><span class="sxs-lookup"><span data-stu-id="dc619-116">-Force</span></span>

<span data-ttu-id="dc619-117">Utilisé pour forcer la modification sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="dc619-117">Used to force the change without prompting.</span></span>

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

## <span data-ttu-id="dc619-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dc619-118">INPUTS</span></span>

### <span data-ttu-id="dc619-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="dc619-119">None</span></span>

## <span data-ttu-id="dc619-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dc619-120">OUTPUTS</span></span>

### <span data-ttu-id="dc619-121">System.Object</span><span class="sxs-lookup"><span data-stu-id="dc619-121">System.Object</span></span>

## <span data-ttu-id="dc619-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dc619-122">NOTES</span></span>

<span data-ttu-id="dc619-123">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="dc619-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="dc619-124">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="dc619-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="dc619-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dc619-125">RELATED LINKS</span></span>

[<span data-ttu-id="dc619-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="dc619-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="dc619-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="dc619-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="dc619-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="dc619-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)

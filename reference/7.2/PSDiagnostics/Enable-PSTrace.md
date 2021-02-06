---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597153"
---
# <span data-ttu-id="fc648-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="fc648-102">Enable-PSTrace</span></span>

## <span data-ttu-id="fc648-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fc648-103">SYNOPSIS</span></span>
<span data-ttu-id="fc648-104">Active les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc648-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="fc648-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="fc648-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="fc648-106">Description</span><span class="sxs-lookup"><span data-stu-id="fc648-106">DESCRIPTION</span></span>

<span data-ttu-id="fc648-107">Cette applet de commande active les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc648-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="fc648-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="fc648-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fc648-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fc648-109">EXAMPLES</span></span>

### <span data-ttu-id="fc648-110">Exemple 1 : activer le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc648-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="fc648-111">L’exemple suivant active uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc648-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="fc648-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc648-112">PARAMETERS</span></span>

### <span data-ttu-id="fc648-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="fc648-113">-AnalyticOnly</span></span>

<span data-ttu-id="fc648-114">Lorsque ce paramètre est utilisé, l’applet de commande active le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc648-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="fc648-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="fc648-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="fc648-116">-Force</span><span class="sxs-lookup"><span data-stu-id="fc648-116">-Force</span></span>

<span data-ttu-id="fc648-117">Utilisé pour forcer la modification sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="fc648-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="fc648-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc648-118">CommonParameters</span></span>
<span data-ttu-id="fc648-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fc648-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc648-120">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fc648-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc648-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fc648-121">INPUTS</span></span>

### <span data-ttu-id="fc648-122">None</span><span class="sxs-lookup"><span data-stu-id="fc648-122">None</span></span>

## <span data-ttu-id="fc648-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fc648-123">OUTPUTS</span></span>

### <span data-ttu-id="fc648-124">None</span><span class="sxs-lookup"><span data-stu-id="fc648-124">None</span></span>

## <span data-ttu-id="fc648-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fc648-125">NOTES</span></span>

<span data-ttu-id="fc648-126">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="fc648-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="fc648-127">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="fc648-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fc648-128">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fc648-128">RELATED LINKS</span></span>

[<span data-ttu-id="fc648-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="fc648-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="fc648-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="fc648-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="fc648-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="fc648-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)


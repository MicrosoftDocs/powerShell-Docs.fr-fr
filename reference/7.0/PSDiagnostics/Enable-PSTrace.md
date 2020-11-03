---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: fea84d9ae83eae88f9a665e8a49aaf2e6743127d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201966"
---
# <span data-ttu-id="74717-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="74717-102">Enable-PSTrace</span></span>

## <span data-ttu-id="74717-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="74717-103">SYNOPSIS</span></span>
<span data-ttu-id="74717-104">Active les journaux du fournisseur d’événements Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74717-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="74717-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74717-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="74717-106">Description</span><span class="sxs-lookup"><span data-stu-id="74717-106">DESCRIPTION</span></span>

<span data-ttu-id="74717-107">Cette applet de commande active les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74717-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="74717-108">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="74717-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="74717-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="74717-109">EXAMPLES</span></span>

### <span data-ttu-id="74717-110">Exemple 1 : activer le journal des événements d’analyse pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="74717-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="74717-111">L’exemple suivant active uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74717-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="74717-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74717-112">PARAMETERS</span></span>

### <span data-ttu-id="74717-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="74717-113">-AnalyticOnly</span></span>

<span data-ttu-id="74717-114">Lorsque ce paramètre est utilisé, l’applet de commande active le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74717-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="74717-115">Le journal des événements opérationnels n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="74717-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="74717-116">-Force</span><span class="sxs-lookup"><span data-stu-id="74717-116">-Force</span></span>

<span data-ttu-id="74717-117">Utilisé pour forcer la modification sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="74717-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="74717-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74717-118">CommonParameters</span></span>
<span data-ttu-id="74717-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74717-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74717-120">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74717-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74717-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="74717-121">INPUTS</span></span>

### <span data-ttu-id="74717-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="74717-122">None</span></span>

## <span data-ttu-id="74717-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="74717-123">OUTPUTS</span></span>

### <span data-ttu-id="74717-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="74717-124">None</span></span>

## <span data-ttu-id="74717-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="74717-125">NOTES</span></span>

<span data-ttu-id="74717-126">Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="74717-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="74717-127">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="74717-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="74717-128">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="74717-128">RELATED LINKS</span></span>

[<span data-ttu-id="74717-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="74717-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="74717-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="74717-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="74717-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="74717-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

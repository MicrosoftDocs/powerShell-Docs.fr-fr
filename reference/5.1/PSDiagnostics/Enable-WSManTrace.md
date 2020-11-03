---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 08c9d61f210761e2ed7a3a5014812b2bd362201b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203054"
---
# <span data-ttu-id="4f2b0-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="4f2b0-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="4f2b0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f2b0-104">SYNOPSIS</span></span>
<span data-ttu-id="4f2b0-105">Démarrez une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="4f2b0-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="4f2b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f2b0-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="4f2b0-107">Description</span><span class="sxs-lookup"><span data-stu-id="4f2b0-107">DESCRIPTION</span></span>
<span data-ttu-id="4f2b0-108">Cette applet de commande démarre une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="4f2b0-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="4f2b0-109">Les fournisseurs d’événements suivants sont activés :</span><span class="sxs-lookup"><span data-stu-id="4f2b0-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="4f2b0-110">Transfert d’événements</span><span class="sxs-lookup"><span data-stu-id="4f2b0-110">Event Forwarding</span></span>
- <span data-ttu-id="4f2b0-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="4f2b0-111">IpmiDrv</span></span>
- <span data-ttu-id="4f2b0-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="4f2b0-112">IPMIPrv</span></span>
- <span data-ttu-id="4f2b0-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="4f2b0-113">WinRM</span></span>
- <span data-ttu-id="4f2b0-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="4f2b0-114">WinrsCmd</span></span>
- <span data-ttu-id="4f2b0-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="4f2b0-115">WinrsExe</span></span>
- <span data-ttu-id="4f2b0-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="4f2b0-116">WinrsMgr</span></span>
- <span data-ttu-id="4f2b0-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="4f2b0-117">WSManProvHost</span></span>

<span data-ttu-id="4f2b0-118">La session est nommée « wsmlog ».</span><span class="sxs-lookup"><span data-stu-id="4f2b0-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="4f2b0-119">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="4f2b0-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="4f2b0-120">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="4f2b0-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="4f2b0-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f2b0-121">EXAMPLES</span></span>

### <span data-ttu-id="4f2b0-122">Exemple 1 : démarrer une session de journalisation WSMan.</span><span class="sxs-lookup"><span data-stu-id="4f2b0-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="4f2b0-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f2b0-123">PARAMETERS</span></span>

### <span data-ttu-id="4f2b0-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f2b0-124">CommonParameters</span></span>

<span data-ttu-id="4f2b0-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f2b0-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f2b0-126">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f2b0-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f2b0-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f2b0-127">INPUTS</span></span>

### <span data-ttu-id="4f2b0-128">Aucun</span><span class="sxs-lookup"><span data-stu-id="4f2b0-128">None</span></span>

## <span data-ttu-id="4f2b0-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f2b0-129">OUTPUTS</span></span>

### <span data-ttu-id="4f2b0-130">System.Object</span><span class="sxs-lookup"><span data-stu-id="4f2b0-130">System.Object</span></span>

## <span data-ttu-id="4f2b0-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f2b0-131">NOTES</span></span>

## <span data-ttu-id="4f2b0-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f2b0-132">RELATED LINKS</span></span>

[<span data-ttu-id="4f2b0-133">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="4f2b0-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="4f2b0-134">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="4f2b0-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="4f2b0-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="4f2b0-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

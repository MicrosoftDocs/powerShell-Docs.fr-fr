---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: c872b57186a854a67908bb07daac7f1a31bbb995
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200965"
---
# <span data-ttu-id="b0159-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b0159-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="b0159-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b0159-104">SYNOPSIS</span></span>
<span data-ttu-id="b0159-105">Démarrez une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="b0159-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="b0159-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0159-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="b0159-107">Description</span><span class="sxs-lookup"><span data-stu-id="b0159-107">DESCRIPTION</span></span>
<span data-ttu-id="b0159-108">Cette applet de commande démarre une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="b0159-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="b0159-109">Les fournisseurs d’événements suivants sont activés :</span><span class="sxs-lookup"><span data-stu-id="b0159-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="b0159-110">Transfert d’événements</span><span class="sxs-lookup"><span data-stu-id="b0159-110">Event Forwarding</span></span>
- <span data-ttu-id="b0159-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="b0159-111">IpmiDrv</span></span>
- <span data-ttu-id="b0159-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="b0159-112">IPMIPrv</span></span>
- <span data-ttu-id="b0159-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="b0159-113">WinRM</span></span>
- <span data-ttu-id="b0159-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="b0159-114">WinrsCmd</span></span>
- <span data-ttu-id="b0159-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="b0159-115">WinrsExe</span></span>
- <span data-ttu-id="b0159-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="b0159-116">WinrsMgr</span></span>
- <span data-ttu-id="b0159-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="b0159-117">WSManProvHost</span></span>

<span data-ttu-id="b0159-118">La session est nommée « wsmlog ».</span><span class="sxs-lookup"><span data-stu-id="b0159-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="b0159-119">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="b0159-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="b0159-120">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="b0159-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b0159-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b0159-121">EXAMPLES</span></span>

### <span data-ttu-id="b0159-122">Exemple 1 : démarrer une session de journalisation WSMan.</span><span class="sxs-lookup"><span data-stu-id="b0159-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="b0159-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0159-123">PARAMETERS</span></span>

### <span data-ttu-id="b0159-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0159-124">CommonParameters</span></span>

<span data-ttu-id="b0159-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0159-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0159-126">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b0159-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0159-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b0159-127">INPUTS</span></span>

### <span data-ttu-id="b0159-128">Aucun</span><span class="sxs-lookup"><span data-stu-id="b0159-128">None</span></span>

## <span data-ttu-id="b0159-129">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b0159-129">OUTPUTS</span></span>

### <span data-ttu-id="b0159-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="b0159-130">None</span></span>

## <span data-ttu-id="b0159-131">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b0159-131">NOTES</span></span>

## <span data-ttu-id="b0159-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b0159-132">RELATED LINKS</span></span>

[<span data-ttu-id="b0159-133">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="b0159-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b0159-134">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="b0159-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="b0159-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b0159-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

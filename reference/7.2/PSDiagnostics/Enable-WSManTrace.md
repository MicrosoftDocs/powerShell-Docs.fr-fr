---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595488"
---
# <span data-ttu-id="c2a0a-102">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c2a0a-102">Enable-WSManTrace</span></span>

## <span data-ttu-id="c2a0a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c2a0a-103">SYNOPSIS</span></span>
<span data-ttu-id="c2a0a-104">Démarrez une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="c2a0a-104">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="c2a0a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c2a0a-105">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="c2a0a-106">Description</span><span class="sxs-lookup"><span data-stu-id="c2a0a-106">DESCRIPTION</span></span>
<span data-ttu-id="c2a0a-107">Cette applet de commande démarre une session de journalisation avec les fournisseurs WSMan activés.</span><span class="sxs-lookup"><span data-stu-id="c2a0a-107">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="c2a0a-108">Les fournisseurs d’événements suivants sont activés :</span><span class="sxs-lookup"><span data-stu-id="c2a0a-108">The following event providers are enabled:</span></span>

- <span data-ttu-id="c2a0a-109">Transfert d’événements</span><span class="sxs-lookup"><span data-stu-id="c2a0a-109">Event Forwarding</span></span>
- <span data-ttu-id="c2a0a-110">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="c2a0a-110">IpmiDrv</span></span>
- <span data-ttu-id="c2a0a-111">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="c2a0a-111">IPMIPrv</span></span>
- <span data-ttu-id="c2a0a-112">WinRM</span><span class="sxs-lookup"><span data-stu-id="c2a0a-112">WinRM</span></span>
- <span data-ttu-id="c2a0a-113">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="c2a0a-113">WinrsCmd</span></span>
- <span data-ttu-id="c2a0a-114">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="c2a0a-114">WinrsExe</span></span>
- <span data-ttu-id="c2a0a-115">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="c2a0a-115">WinrsMgr</span></span>
- <span data-ttu-id="c2a0a-116">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="c2a0a-116">WSManProvHost</span></span>

<span data-ttu-id="c2a0a-117">La session est nommée « wsmlog ».</span><span class="sxs-lookup"><span data-stu-id="c2a0a-117">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="c2a0a-118">Cette applet de commande utilise l’applet de commande `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="c2a0a-118">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c2a0a-119">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="c2a0a-119">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c2a0a-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c2a0a-120">EXAMPLES</span></span>

### <span data-ttu-id="c2a0a-121">Exemple 1 : démarrer une session de journalisation WSMan.</span><span class="sxs-lookup"><span data-stu-id="c2a0a-121">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="c2a0a-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2a0a-122">PARAMETERS</span></span>

### <span data-ttu-id="c2a0a-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2a0a-123">CommonParameters</span></span>

<span data-ttu-id="c2a0a-124">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2a0a-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2a0a-125">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c2a0a-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2a0a-126">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c2a0a-126">INPUTS</span></span>

### <span data-ttu-id="c2a0a-127">None</span><span class="sxs-lookup"><span data-stu-id="c2a0a-127">None</span></span>

## <span data-ttu-id="c2a0a-128">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c2a0a-128">OUTPUTS</span></span>

### <span data-ttu-id="c2a0a-129">None</span><span class="sxs-lookup"><span data-stu-id="c2a0a-129">None</span></span>

## <span data-ttu-id="c2a0a-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c2a0a-130">NOTES</span></span>

## <span data-ttu-id="c2a0a-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c2a0a-131">RELATED LINKS</span></span>

[<span data-ttu-id="c2a0a-132">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="c2a0a-132">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c2a0a-133">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="c2a0a-133">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c2a0a-134">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c2a0a-134">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)


---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 5566fb2e11311990cea76e6802c84985795c3553
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200889"
---
# <span data-ttu-id="fd139-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fd139-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="fd139-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fd139-104">SYNOPSIS</span></span>
<span data-ttu-id="fd139-105">Arrêtez la session de journalisation WSMan démarrée par Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="fd139-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="fd139-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd139-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="fd139-107">Description</span><span class="sxs-lookup"><span data-stu-id="fd139-107">DESCRIPTION</span></span>
<span data-ttu-id="fd139-108">Cette applet de commande arrête la session de journalisation WSMan démarrée par Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="fd139-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="fd139-109">Cette applet de commande utilise l’applet de commande `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="fd139-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="fd139-110">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="fd139-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fd139-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fd139-111">EXAMPLES</span></span>

### <span data-ttu-id="fd139-112">Exemple 1 : arrêter une trace WSMan</span><span class="sxs-lookup"><span data-stu-id="fd139-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="fd139-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd139-113">PARAMETERS</span></span>

### <span data-ttu-id="fd139-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd139-114">CommonParameters</span></span>

<span data-ttu-id="fd139-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fd139-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd139-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fd139-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd139-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fd139-117">INPUTS</span></span>

### <span data-ttu-id="fd139-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="fd139-118">None</span></span>

## <span data-ttu-id="fd139-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fd139-119">OUTPUTS</span></span>

### <span data-ttu-id="fd139-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="fd139-120">None</span></span>

## <span data-ttu-id="fd139-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fd139-121">NOTES</span></span>

## <span data-ttu-id="fd139-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fd139-122">RELATED LINKS</span></span>

[<span data-ttu-id="fd139-123">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="fd139-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="fd139-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="fd139-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="fd139-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fd139-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)


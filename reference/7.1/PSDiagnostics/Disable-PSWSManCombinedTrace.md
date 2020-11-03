---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 854769bea9c1b3c104f87d99909f6201a39cac42
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200890"
---
# <span data-ttu-id="7def3-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7def3-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="7def3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7def3-104">SYNOPSIS</span></span>
<span data-ttu-id="7def3-105">Arrêtez la session de journalisation démarrée par Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="7def3-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="7def3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7def3-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="7def3-107">Description</span><span class="sxs-lookup"><span data-stu-id="7def3-107">DESCRIPTION</span></span>

<span data-ttu-id="7def3-108">Cette applet de commande arrête la session de journalisation démarrée par `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="7def3-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="7def3-109">Cette applet de commande utilise l’applet de commande `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="7def3-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="7def3-110">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="7def3-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7def3-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7def3-111">EXAMPLES</span></span>

### <span data-ttu-id="7def3-112">Exemple 1 : désactiver la session de journalisation combinée</span><span class="sxs-lookup"><span data-stu-id="7def3-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="7def3-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7def3-113">PARAMETERS</span></span>

### <span data-ttu-id="7def3-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7def3-114">CommonParameters</span></span>

<span data-ttu-id="7def3-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7def3-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7def3-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7def3-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7def3-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7def3-117">INPUTS</span></span>

### <span data-ttu-id="7def3-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="7def3-118">None</span></span>

## <span data-ttu-id="7def3-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7def3-119">OUTPUTS</span></span>

### <span data-ttu-id="7def3-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="7def3-120">None</span></span>

## <span data-ttu-id="7def3-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7def3-121">NOTES</span></span>

## <span data-ttu-id="7def3-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7def3-122">RELATED LINKS</span></span>

[<span data-ttu-id="7def3-123">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="7def3-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="7def3-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="7def3-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="7def3-125">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7def3-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)


---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 690a8b050fd0e16033a585df210db340f41a83a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596716"
---
# <span data-ttu-id="2167e-102">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="2167e-102">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="2167e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2167e-103">SYNOPSIS</span></span>
<span data-ttu-id="2167e-104">Arrêtez la session de journalisation démarrée par Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="2167e-104">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="2167e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2167e-105">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="2167e-106">Description</span><span class="sxs-lookup"><span data-stu-id="2167e-106">DESCRIPTION</span></span>

<span data-ttu-id="2167e-107">Cette applet de commande arrête la session de journalisation démarrée par `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="2167e-107">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="2167e-108">Cette applet de commande utilise l’applet de commande `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="2167e-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="2167e-109">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="2167e-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="2167e-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2167e-110">EXAMPLES</span></span>

### <span data-ttu-id="2167e-111">Exemple 1 : désactiver la session de journalisation combinée</span><span class="sxs-lookup"><span data-stu-id="2167e-111">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="2167e-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2167e-112">PARAMETERS</span></span>

### <span data-ttu-id="2167e-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2167e-113">CommonParameters</span></span>

<span data-ttu-id="2167e-114">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2167e-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2167e-115">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2167e-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2167e-116">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2167e-116">INPUTS</span></span>

### <span data-ttu-id="2167e-117">None</span><span class="sxs-lookup"><span data-stu-id="2167e-117">None</span></span>

## <span data-ttu-id="2167e-118">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2167e-118">OUTPUTS</span></span>

### <span data-ttu-id="2167e-119">None</span><span class="sxs-lookup"><span data-stu-id="2167e-119">None</span></span>

## <span data-ttu-id="2167e-120">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2167e-120">NOTES</span></span>

## <span data-ttu-id="2167e-121">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2167e-121">RELATED LINKS</span></span>

[<span data-ttu-id="2167e-122">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="2167e-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="2167e-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="2167e-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="2167e-124">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="2167e-124">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)


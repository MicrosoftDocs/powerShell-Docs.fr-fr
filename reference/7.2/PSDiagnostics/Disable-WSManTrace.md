---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 647a7676eddf2175bf29e02b3482cc9c7c4d8ebe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596314"
---
# <span data-ttu-id="1b39e-102">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="1b39e-102">Disable-WSManTrace</span></span>

## <span data-ttu-id="1b39e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1b39e-103">SYNOPSIS</span></span>
<span data-ttu-id="1b39e-104">Arrêtez la session de journalisation WSMan démarrée par Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="1b39e-104">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="1b39e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1b39e-105">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="1b39e-106">Description</span><span class="sxs-lookup"><span data-stu-id="1b39e-106">DESCRIPTION</span></span>
<span data-ttu-id="1b39e-107">Cette applet de commande arrête la session de journalisation WSMan démarrée par Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="1b39e-107">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="1b39e-108">Cette applet de commande utilise l’applet de commande `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="1b39e-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="1b39e-109">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="1b39e-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1b39e-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1b39e-110">EXAMPLES</span></span>

### <span data-ttu-id="1b39e-111">Exemple 1 : arrêter une trace WSMan</span><span class="sxs-lookup"><span data-stu-id="1b39e-111">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="1b39e-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b39e-112">PARAMETERS</span></span>

### <span data-ttu-id="1b39e-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b39e-113">CommonParameters</span></span>

<span data-ttu-id="1b39e-114">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b39e-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b39e-115">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b39e-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b39e-116">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1b39e-116">INPUTS</span></span>

### <span data-ttu-id="1b39e-117">None</span><span class="sxs-lookup"><span data-stu-id="1b39e-117">None</span></span>

## <span data-ttu-id="1b39e-118">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1b39e-118">OUTPUTS</span></span>

### <span data-ttu-id="1b39e-119">None</span><span class="sxs-lookup"><span data-stu-id="1b39e-119">None</span></span>

## <span data-ttu-id="1b39e-120">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1b39e-120">NOTES</span></span>

## <span data-ttu-id="1b39e-121">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1b39e-121">RELATED LINKS</span></span>

[<span data-ttu-id="1b39e-122">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="1b39e-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="1b39e-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="1b39e-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="1b39e-124">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="1b39e-124">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)


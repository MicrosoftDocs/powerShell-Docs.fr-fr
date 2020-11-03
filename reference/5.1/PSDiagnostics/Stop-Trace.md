---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 917f9f0eb4b9dfaf08c21a06f895d73c71bff5dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203042"
---
# <span data-ttu-id="b5dfa-103">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-103">Stop-Trace</span></span>

## <span data-ttu-id="b5dfa-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b5dfa-104">SYNOPSIS</span></span>
<span data-ttu-id="b5dfa-105">Arrêtez une session de journalisation du suivi des événements.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-105">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="b5dfa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5dfa-106">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="b5dfa-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5dfa-107">DESCRIPTION</span></span>

<span data-ttu-id="b5dfa-108">Cette applet de commande arrête une session de journalisation de suivi d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-108">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="b5dfa-109">Cette applet de commande est utilisée par les applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5dfa-109">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="b5dfa-110">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b5dfa-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b5dfa-111">EXAMPLES</span></span>

### <span data-ttu-id="b5dfa-112">Exemple 1 : arrêter une session de journalisation de suivi WSMan</span><span class="sxs-lookup"><span data-stu-id="b5dfa-112">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="b5dfa-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5dfa-113">PARAMETERS</span></span>

### <span data-ttu-id="b5dfa-114">-ETS</span><span class="sxs-lookup"><span data-stu-id="b5dfa-114">-ETS</span></span>
<span data-ttu-id="b5dfa-115">Envoyer des commandes aux sessions de suivi d’événements directement sans enregistrement ou planification.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-115">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="b5dfa-116">-Nom_session</span><span class="sxs-lookup"><span data-stu-id="b5dfa-116">-SessionName</span></span>
<span data-ttu-id="b5dfa-117">Nom de la session de suivi d’événements à arrêter.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-117">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5dfa-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5dfa-118">CommonParameters</span></span>
<span data-ttu-id="b5dfa-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5dfa-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5dfa-120">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b5dfa-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5dfa-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b5dfa-121">INPUTS</span></span>

### <span data-ttu-id="b5dfa-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="b5dfa-122">None</span></span>

## <span data-ttu-id="b5dfa-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b5dfa-123">OUTPUTS</span></span>

### <span data-ttu-id="b5dfa-124">System.Object</span><span class="sxs-lookup"><span data-stu-id="b5dfa-124">System.Object</span></span>

## <span data-ttu-id="b5dfa-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b5dfa-125">NOTES</span></span>

## <span data-ttu-id="b5dfa-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b5dfa-126">RELATED LINKS</span></span>

[<span data-ttu-id="b5dfa-127">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="b5dfa-127">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b5dfa-128">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-128">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="b5dfa-129">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-129">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="b5dfa-130">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-130">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="b5dfa-131">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-131">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="b5dfa-132">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b5dfa-132">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

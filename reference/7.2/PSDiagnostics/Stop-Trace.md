---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596723"
---
# <span data-ttu-id="29001-102">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="29001-102">Stop-Trace</span></span>

## <span data-ttu-id="29001-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="29001-103">SYNOPSIS</span></span>
<span data-ttu-id="29001-104">Arrêtez une session de journalisation du suivi des événements.</span><span class="sxs-lookup"><span data-stu-id="29001-104">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="29001-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="29001-105">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="29001-106">Description</span><span class="sxs-lookup"><span data-stu-id="29001-106">DESCRIPTION</span></span>

<span data-ttu-id="29001-107">Cette applet de commande arrête une session de journalisation de suivi d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="29001-107">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="29001-108">Cette applet de commande est utilisée par les applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="29001-108">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="29001-109">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="29001-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="29001-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="29001-110">EXAMPLES</span></span>

### <span data-ttu-id="29001-111">Exemple 1 : arrêter une session de journalisation de suivi WSMan</span><span class="sxs-lookup"><span data-stu-id="29001-111">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="29001-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29001-112">PARAMETERS</span></span>

### <span data-ttu-id="29001-113">-ETS</span><span class="sxs-lookup"><span data-stu-id="29001-113">-ETS</span></span>
<span data-ttu-id="29001-114">Envoyer des commandes aux sessions de suivi d’événements directement sans enregistrement ou planification.</span><span class="sxs-lookup"><span data-stu-id="29001-114">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="29001-115">-Nom_session</span><span class="sxs-lookup"><span data-stu-id="29001-115">-SessionName</span></span>
<span data-ttu-id="29001-116">Nom de la session de suivi d’événements à arrêter.</span><span class="sxs-lookup"><span data-stu-id="29001-116">The name of the Event Trace session to be stopped.</span></span>

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

### <span data-ttu-id="29001-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29001-117">CommonParameters</span></span>
<span data-ttu-id="29001-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="29001-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29001-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="29001-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29001-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="29001-120">INPUTS</span></span>

### <span data-ttu-id="29001-121">None</span><span class="sxs-lookup"><span data-stu-id="29001-121">None</span></span>

## <span data-ttu-id="29001-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="29001-122">OUTPUTS</span></span>

### <span data-ttu-id="29001-123">None</span><span class="sxs-lookup"><span data-stu-id="29001-123">None</span></span>

## <span data-ttu-id="29001-124">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="29001-124">NOTES</span></span>

## <span data-ttu-id="29001-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="29001-125">RELATED LINKS</span></span>

[<span data-ttu-id="29001-126">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="29001-126">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="29001-127">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="29001-127">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="29001-128">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="29001-128">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="29001-129">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="29001-129">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="29001-130">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="29001-130">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="29001-131">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="29001-131">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)


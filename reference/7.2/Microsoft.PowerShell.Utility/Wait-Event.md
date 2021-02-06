---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: caf2a1c80848d3140e7ad46fdf54dbe71886c633
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596916"
---
# <span data-ttu-id="c799f-102">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-102">Wait-Event</span></span>

## <span data-ttu-id="c799f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c799f-103">SYNOPSIS</span></span>
<span data-ttu-id="c799f-104">Attend qu'un événement particulier soit déclenché avant de poursuivre son exécution.</span><span class="sxs-lookup"><span data-stu-id="c799f-104">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="c799f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c799f-105">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="c799f-106">Description</span><span class="sxs-lookup"><span data-stu-id="c799f-106">DESCRIPTION</span></span>

<span data-ttu-id="c799f-107">L' `Wait-Event` applet de commande suspend l’exécution d’un script ou d’une fonction jusqu’à ce qu’un événement particulier soit déclenché.</span><span class="sxs-lookup"><span data-stu-id="c799f-107">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="c799f-108">L'exécution reprend quand l'événement est détecté.</span><span class="sxs-lookup"><span data-stu-id="c799f-108">Execution resumes when the event is detected.</span></span> <span data-ttu-id="c799f-109">Pour annuler l’attente, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c799f-109">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="c799f-110">Cette fonctionnalité fournit une alternative à l'interrogation d'un événement.</span><span class="sxs-lookup"><span data-stu-id="c799f-110">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="c799f-111">Elle vous permet également de déterminer la réponse à un événement de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="c799f-111">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="c799f-112">utilisation du paramètre **action** de l’abonnement aux événements</span><span class="sxs-lookup"><span data-stu-id="c799f-112">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="c799f-113">attente du retour d’un événement, puis réponse avec une action</span><span class="sxs-lookup"><span data-stu-id="c799f-113">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="c799f-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c799f-114">EXAMPLES</span></span>

### <span data-ttu-id="c799f-115">Exemple 1 : attendre l’événement suivant</span><span class="sxs-lookup"><span data-stu-id="c799f-115">Example 1: Wait for the next event</span></span>

<span data-ttu-id="c799f-116">Cet exemple attend la levée de l’événement suivant.</span><span class="sxs-lookup"><span data-stu-id="c799f-116">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="c799f-117">Exemple 2 : attendre un événement avec un identificateur source spécifié</span><span class="sxs-lookup"><span data-stu-id="c799f-117">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="c799f-118">Cet exemple attend l’événement suivant qui est déclenché et qui a un identificateur source de ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="c799f-118">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="c799f-119">Exemple 3 : attendre un événement de minuteur écoulé</span><span class="sxs-lookup"><span data-stu-id="c799f-119">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="c799f-120">Cet exemple utilise l' `Wait-Event` applet de commande pour attendre un événement de minuterie sur un minuteur défini pour 2000 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="c799f-120">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### <span data-ttu-id="c799f-121">Exemple 4 : attendre un événement après un délai d’attente spécifié</span><span class="sxs-lookup"><span data-stu-id="c799f-121">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="c799f-122">Cet exemple attend jusqu’à 90 secondes pour l’événement suivant qui est déclenché et qui a un identificateur source de **ProcessStarted**.</span><span class="sxs-lookup"><span data-stu-id="c799f-122">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="c799f-123">Si le délai spécifié expire, l'attente se termine.</span><span class="sxs-lookup"><span data-stu-id="c799f-123">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="c799f-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c799f-124">PARAMETERS</span></span>

### <span data-ttu-id="c799f-125">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="c799f-125">-SourceIdentifier</span></span>

<span data-ttu-id="c799f-126">Spécifie l’identificateur source que cette applet de commande attend pour les événements.</span><span class="sxs-lookup"><span data-stu-id="c799f-126">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="c799f-127">Par défaut, `Wait-Event` attend un événement.</span><span class="sxs-lookup"><span data-stu-id="c799f-127">By default, `Wait-Event` waits for any event.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c799f-128">-Timeout</span><span class="sxs-lookup"><span data-stu-id="c799f-128">-Timeout</span></span>

<span data-ttu-id="c799f-129">Spécifie la durée maximale, en secondes, pendant laquelle `Wait-Event` attend que l’événement se produise.</span><span class="sxs-lookup"><span data-stu-id="c799f-129">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="c799f-130">La valeur par défaut, -1, stipule d'attendre indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="c799f-130">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="c799f-131">Le minutage démarre lorsque vous envoyez la `Wait-Event` commande.</span><span class="sxs-lookup"><span data-stu-id="c799f-131">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="c799f-132">Si la durée spécifiée est dépassée, l'attente se termine et l'invite de commandes réapparaît, même si l'événement n'a pas été déclenché.</span><span class="sxs-lookup"><span data-stu-id="c799f-132">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="c799f-133">Aucun message d'erreur ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="c799f-133">No error message is displayed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c799f-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c799f-134">CommonParameters</span></span>

<span data-ttu-id="c799f-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c799f-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c799f-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c799f-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c799f-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c799f-137">INPUTS</span></span>

### <span data-ttu-id="c799f-138">System.String</span><span class="sxs-lookup"><span data-stu-id="c799f-138">System.String</span></span>

## <span data-ttu-id="c799f-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c799f-139">OUTPUTS</span></span>

### <span data-ttu-id="c799f-140">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="c799f-140">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="c799f-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c799f-141">NOTES</span></span>

<span data-ttu-id="c799f-142">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c799f-142">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="c799f-143">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="c799f-143">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="c799f-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c799f-144">RELATED LINKS</span></span>

[<span data-ttu-id="c799f-145">Get-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-145">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="c799f-146">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="c799f-146">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="c799f-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="c799f-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="c799f-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="c799f-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="c799f-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="c799f-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="c799f-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="c799f-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="c799f-152">Wait-Event</span></span>](Wait-Event.md)


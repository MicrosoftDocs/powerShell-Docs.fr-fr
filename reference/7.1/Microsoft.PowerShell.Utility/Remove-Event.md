---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2ef1125320141d0a16a2a0120560efbe65017b4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202749"
---
# <span data-ttu-id="a8b9b-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-103">Remove-Event</span></span>

## <span data-ttu-id="a8b9b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a8b9b-104">SYNOPSIS</span></span>
<span data-ttu-id="a8b9b-105">Supprime les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="a8b9b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8b9b-106">SYNTAX</span></span>

### <span data-ttu-id="a8b9b-107">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a8b9b-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a8b9b-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="a8b9b-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a8b9b-109">Description</span><span class="sxs-lookup"><span data-stu-id="a8b9b-109">DESCRIPTION</span></span>
<span data-ttu-id="a8b9b-110">L’applet de commande **Remove-Event** supprime les événements de la file d’attente d’événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-110">The **Remove-Event** cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="a8b9b-111">Cette applet de commande ne supprime que les événements actuellement dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-111">This cmdlet deletes only the events currently in the queue.</span></span>
<span data-ttu-id="a8b9b-112">Pour annuler les inscriptions d'événement ou annuler votre abonnement, utilisez l'applet de commande Unregister-Event.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-112">To cancel event registrations or unsubscribe, use the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="a8b9b-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a8b9b-113">EXAMPLES</span></span>

### <span data-ttu-id="a8b9b-114">Exemple 1 : supprimer un événement par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="a8b9b-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="a8b9b-115">Cette commande supprime les événements avec un identificateur de source de processus démarré à partir de la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="a8b9b-116">Exemple 2 : supprimer un événement par identificateur d’événement</span><span class="sxs-lookup"><span data-stu-id="a8b9b-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="a8b9b-117">Cette commande supprime l'événement avec un ID d'événement égal à 30 de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="a8b9b-118">Exemple 3 : supprimer tous les événements</span><span class="sxs-lookup"><span data-stu-id="a8b9b-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="a8b9b-119">Cette commande supprime tous les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="a8b9b-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8b9b-120">PARAMETERS</span></span>

### <span data-ttu-id="a8b9b-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="a8b9b-121">-EventIdentifier</span></span>
<span data-ttu-id="a8b9b-122">Spécifie l’identificateur d’événement pour lequel l’applet de commande est supprimée.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-122">Specifies the event identifier for which the cmdlet deletes.</span></span>
<span data-ttu-id="a8b9b-123">Un paramètre *EventIdentifier* ou *SourceIdentifier* est requis dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-123">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a8b9b-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="a8b9b-124">-SourceIdentifier</span></span>
<span data-ttu-id="a8b9b-125">Spécifie l’identificateur source pour lequel cette applet de commande supprime les événements.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span>
<span data-ttu-id="a8b9b-126">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-126">Wildcards are not permitted.</span></span>
<span data-ttu-id="a8b9b-127">Un paramètre *EventIdentifier* ou *SourceIdentifier* est requis dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-127">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8b9b-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a8b9b-128">-Confirm</span></span>
<span data-ttu-id="a8b9b-129">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-129">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8b9b-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a8b9b-130">-WhatIf</span></span>
<span data-ttu-id="a8b9b-131">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-131">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a8b9b-132">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-132">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8b9b-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8b9b-133">CommonParameters</span></span>
<span data-ttu-id="a8b9b-134">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8b9b-135">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a8b9b-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8b9b-136">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a8b9b-136">INPUTS</span></span>

### <span data-ttu-id="a8b9b-137">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="a8b9b-137">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="a8b9b-138">Vous pouvez diriger les événements de Get-Event vers **Remove-Event** .</span><span class="sxs-lookup"><span data-stu-id="a8b9b-138">You can pipe events from Get-Event to **Remove-Event** .</span></span>

## <span data-ttu-id="a8b9b-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a8b9b-139">OUTPUTS</span></span>

### <span data-ttu-id="a8b9b-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="a8b9b-140">None</span></span>
<span data-ttu-id="a8b9b-141">L'applet de commande ne génère pas de résultat.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a8b9b-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a8b9b-142">NOTES</span></span>

* <span data-ttu-id="a8b9b-143">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="a8b9b-144">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="a8b9b-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="a8b9b-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a8b9b-145">RELATED LINKS</span></span>

[<span data-ttu-id="a8b9b-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="a8b9b-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="a8b9b-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="a8b9b-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="a8b9b-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="a8b9b-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="a8b9b-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="a8b9b-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="a8b9b-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="a8b9b-152">Wait-Event</span></span>](Wait-Event.md)


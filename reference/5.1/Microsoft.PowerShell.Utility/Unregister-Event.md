---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 3cc2983def049e705a67bad05ee39bdbd71d3888
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344420"
---
# <span data-ttu-id="18b23-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-103">Unregister-Event</span></span>

## <span data-ttu-id="18b23-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="18b23-104">SYNOPSIS</span></span>
<span data-ttu-id="18b23-105">Annule un abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="18b23-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="18b23-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="18b23-106">SYNTAX</span></span>

### <span data-ttu-id="18b23-107">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="18b23-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="18b23-108">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="18b23-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="18b23-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="18b23-109">DESCRIPTION</span></span>

<span data-ttu-id="18b23-110">L' `Unregister-Event` applet de commande annule un abonnement aux événements qui a été créé à l’aide de l’applet de commande `Register-EngineEvent` , `Register-ObjectEvent` ou `Register-WmiEvent` .</span><span class="sxs-lookup"><span data-stu-id="18b23-110">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="18b23-111">Quand un abonnement aux événements est annulé, l'abonné aux événements est supprimé de la session et les événements ayant fait l'objet d'un abonnement ne sont plus ajoutés à la file d'attente d'événements.</span><span class="sxs-lookup"><span data-stu-id="18b23-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="18b23-112">Lorsque vous annulez un abonnement à un événement créé à l’aide de l’applet de commande `New-Event` , le nouvel événement est également supprimé de la session.</span><span class="sxs-lookup"><span data-stu-id="18b23-112">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="18b23-113">`Unregister-Event` ne supprime pas les événements de la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="18b23-113">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="18b23-114">Pour supprimer des événements, utilisez l’applet de commande `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="18b23-114">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="18b23-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="18b23-115">EXAMPLES</span></span>

### <span data-ttu-id="18b23-116">Exemple 1 : annuler un abonnement à un événement par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="18b23-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="18b23-117">Cette commande annule l’abonnement aux événements qui a un identificateur source de ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="18b23-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="18b23-118">Pour Rechercher l’identificateur source d’un événement, utilisez l’applet de commande `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="18b23-118">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="18b23-119">Pour Rechercher l’identificateur source d’un abonnement aux événements, utilisez l' `Get-EventSubscriber` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="18b23-119">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="18b23-120">Exemple 2 : annuler un abonnement aux événements par identificateur d’abonnement</span><span class="sxs-lookup"><span data-stu-id="18b23-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="18b23-121">Cette commande annule l'abonnement aux événements qui a l'identificateur d'abonnement 2.</span><span class="sxs-lookup"><span data-stu-id="18b23-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="18b23-122">Pour Rechercher l’identificateur d’abonnement d’un abonnement aux événements, utilisez l’applet de commande `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="18b23-122">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="18b23-123">Exemple 3 : annuler tous les abonnements aux événements</span><span class="sxs-lookup"><span data-stu-id="18b23-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="18b23-124">Cette commande annule tous les abonnements aux événements dans la session.</span><span class="sxs-lookup"><span data-stu-id="18b23-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="18b23-125">La commande utilise l' `Get-EventSubscriber` applet de commande pour récupérer tous les objets d’abonné aux événements dans la session, y compris les abonnés qui sont masqués à l’aide du paramètre **SupportEvent** des applets de commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="18b23-125">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="18b23-126">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les objets de l’abonné à `Unregister-Event` , qui les supprime de la session.</span><span class="sxs-lookup"><span data-stu-id="18b23-126">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="18b23-127">Pour effectuer la tâche, le paramètre **force** est également requis sur `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="18b23-127">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="18b23-128">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="18b23-128">PARAMETERS</span></span>

### <span data-ttu-id="18b23-129">-Force</span><span class="sxs-lookup"><span data-stu-id="18b23-129">-Force</span></span>

<span data-ttu-id="18b23-130">Annule tous les abonnements aux événements, y compris les abonnements qui ont été masqués à l’aide du paramètre **SupportEvent** de `Register-ObjectEvent` , `Register-WmiEvent` et `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="18b23-130">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

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

### <span data-ttu-id="18b23-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="18b23-131">-SourceIdentifier</span></span>

<span data-ttu-id="18b23-132">Spécifie un identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="18b23-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="18b23-133">Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="18b23-133">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18b23-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="18b23-134">-SubscriptionId</span></span>

<span data-ttu-id="18b23-135">Spécifie un ID d’identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="18b23-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="18b23-136">Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="18b23-136">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="18b23-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="18b23-137">-Confirm</span></span>

<span data-ttu-id="18b23-138">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="18b23-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="18b23-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="18b23-139">-WhatIf</span></span>

<span data-ttu-id="18b23-140">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="18b23-140">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="18b23-141">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="18b23-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="18b23-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="18b23-142">CommonParameters</span></span>

<span data-ttu-id="18b23-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18b23-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="18b23-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="18b23-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="18b23-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="18b23-145">INPUTS</span></span>

### <span data-ttu-id="18b23-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="18b23-146">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="18b23-147">Vous pouvez diriger la sortie de `Get-EventSubscriber` vers `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="18b23-147">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="18b23-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="18b23-148">OUTPUTS</span></span>

### <span data-ttu-id="18b23-149">Aucun</span><span class="sxs-lookup"><span data-stu-id="18b23-149">None</span></span>

<span data-ttu-id="18b23-150">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="18b23-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="18b23-151">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="18b23-151">NOTES</span></span>


<span data-ttu-id="18b23-152">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="18b23-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="18b23-153">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="18b23-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="18b23-154">`Unregister-Event` Impossible de supprimer les événements créés à l’aide de l’applet de commande `New-Event` , sauf si vous êtes abonné à l’événement à l’aide de l’applet de commande `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="18b23-154">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="18b23-155">Pour supprimer un événement personnalisé de la session, vous devez le supprimer par programmation ou fermer la session.</span><span class="sxs-lookup"><span data-stu-id="18b23-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="18b23-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="18b23-156">RELATED LINKS</span></span>

[<span data-ttu-id="18b23-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="18b23-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="18b23-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="18b23-159">New-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="18b23-160">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="18b23-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="18b23-161">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="18b23-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="18b23-162">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="18b23-163">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="18b23-164">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="18b23-164">Wait-Event</span></span>](Wait-Event.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: b132e842167bb6684519bfd196a3f4a03d078a62
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201974"
---
# <span data-ttu-id="9894f-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-103">Unregister-Event</span></span>

## <span data-ttu-id="9894f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9894f-104">SYNOPSIS</span></span>
<span data-ttu-id="9894f-105">Annule un abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="9894f-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="9894f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9894f-106">SYNTAX</span></span>

### <span data-ttu-id="9894f-107">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9894f-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9894f-108">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="9894f-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9894f-109">Description</span><span class="sxs-lookup"><span data-stu-id="9894f-109">DESCRIPTION</span></span>
<span data-ttu-id="9894f-110">L’applet **de commande Unregister-Event** annule un abonnement aux événements qui a été créé à l’aide de l’applet de commande Register-EngineEvent, Register-ObjectEvent ou Register-WmiEvent.</span><span class="sxs-lookup"><span data-stu-id="9894f-110">The **Unregister-Event** cmdlet cancels an event subscription that was created by using the Register-EngineEvent, Register-ObjectEvent, or Register-WmiEvent cmdlet.</span></span>

<span data-ttu-id="9894f-111">Quand un abonnement aux événements est annulé, l'abonné aux événements est supprimé de la session et les événements ayant fait l'objet d'un abonnement ne sont plus ajoutés à la file d'attente d'événements.</span><span class="sxs-lookup"><span data-stu-id="9894f-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span>
<span data-ttu-id="9894f-112">Quand vous annulez un abonnement à un événement créé à l'aide de l'applet de commande New-Event, le nouvel événement est également supprimé de la session.</span><span class="sxs-lookup"><span data-stu-id="9894f-112">When you cancel a subscription to an event created by using the New-Event cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="9894f-113">**Unregister-Event** ne supprime pas les événements de la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="9894f-113">**Unregister-Event** does not delete events from the event queue.</span></span>
<span data-ttu-id="9894f-114">Pour supprimer des événements, utilisez l'applet de commande Remove-Event.</span><span class="sxs-lookup"><span data-stu-id="9894f-114">To delete events, use the Remove-Event cmdlet.</span></span>

## <span data-ttu-id="9894f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9894f-115">EXAMPLES</span></span>

### <span data-ttu-id="9894f-116">Exemple 1 : annuler un abonnement à un événement par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="9894f-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="9894f-117">Cette commande annule l’abonnement aux événements qui a un identificateur source de ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="9894f-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="9894f-118">Pour rechercher l'identificateur source d'un événement, utilisez l'applet de commande Get-Event.</span><span class="sxs-lookup"><span data-stu-id="9894f-118">To find the source identifier of an event, use the Get-Event cmdlet.</span></span>
<span data-ttu-id="9894f-119">Pour Rechercher l’identificateur source d’un abonnement aux événements, utilisez l’applet de commande **EventSubscriber** .</span><span class="sxs-lookup"><span data-stu-id="9894f-119">To find the source identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="9894f-120">Exemple 2 : annuler un abonnement aux événements par identificateur d’abonnement</span><span class="sxs-lookup"><span data-stu-id="9894f-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="9894f-121">Cette commande annule l'abonnement aux événements qui a l'identificateur d'abonnement 2.</span><span class="sxs-lookup"><span data-stu-id="9894f-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="9894f-122">Pour Rechercher l’identificateur d’abonnement d’un abonnement aux événements, utilisez l’applet de commande **EventSubscriber** .</span><span class="sxs-lookup"><span data-stu-id="9894f-122">To find the subscription identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="9894f-123">Exemple 3 : annuler tous les abonnements aux événements</span><span class="sxs-lookup"><span data-stu-id="9894f-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="9894f-124">Cette commande annule tous les abonnements aux événements dans la session.</span><span class="sxs-lookup"><span data-stu-id="9894f-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="9894f-125">La commande utilise l’applet de commande **EventSubscriber** pour récupérer tous les objets d’abonné aux événements dans la session, y compris les abonnés qui sont masqués à l’aide du paramètre *SupportEvent* des applets de commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="9894f-125">The command uses the **Get-EventSubscriber** cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the *SupportEvent* parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="9894f-126">Elle utilise un opérateur de pipeline (|) pour envoyer les objets d’abonné à **Unregister-Event** , ce qui les supprime de la session.</span><span class="sxs-lookup"><span data-stu-id="9894f-126">It uses a pipeline operator (|) to send the subscriber objects to **Unregister-Event** , which deletes them from the session.</span></span>
<span data-ttu-id="9894f-127">Pour effectuer la tâche, le paramètre *force* est également requis sur **Unregister-Event** .</span><span class="sxs-lookup"><span data-stu-id="9894f-127">To complete the task, the *Force* parameter is also required on **Unregister-Event** .</span></span>

## <span data-ttu-id="9894f-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9894f-128">PARAMETERS</span></span>

### <span data-ttu-id="9894f-129">-Force</span><span class="sxs-lookup"><span data-stu-id="9894f-129">-Force</span></span>
<span data-ttu-id="9894f-130">Annule tous les abonnements aux événements, y compris les abonnements qui ont été masqués à l’aide du paramètre *SupportEvent* de **Register-ObjectEvent** , **Register-WmiEvent** et **Register-EngineEvent** .</span><span class="sxs-lookup"><span data-stu-id="9894f-130">Cancels all event subscriptions, including subscriptions that were hidden by using the *SupportEvent* parameter of **Register-ObjectEvent** , **Register-WmiEvent** , and **Register-EngineEvent** .</span></span>

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

### <span data-ttu-id="9894f-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="9894f-131">-SourceIdentifier</span></span>
<span data-ttu-id="9894f-132">Spécifie un identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="9894f-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="9894f-133">Un paramètre *SourceIdentifier* ou *SubscriptionId* doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="9894f-133">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="9894f-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="9894f-134">-SubscriptionId</span></span>
<span data-ttu-id="9894f-135">Spécifie un ID d’identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="9894f-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="9894f-136">Un paramètre *SourceIdentifier* ou *SubscriptionId* doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="9894f-136">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="9894f-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9894f-137">-Confirm</span></span>
<span data-ttu-id="9894f-138">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9894f-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9894f-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9894f-139">-WhatIf</span></span>
<span data-ttu-id="9894f-140">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9894f-140">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9894f-141">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9894f-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9894f-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9894f-142">CommonParameters</span></span>
<span data-ttu-id="9894f-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9894f-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9894f-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9894f-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9894f-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9894f-145">INPUTS</span></span>

### <span data-ttu-id="9894f-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="9894f-146">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="9894f-147">Vous pouvez diriger la sortie de Get-EventSubscriber vers **Unregister-Event** .</span><span class="sxs-lookup"><span data-stu-id="9894f-147">You can pipe the output from Get-EventSubscriber to **Unregister-Event** .</span></span>

## <span data-ttu-id="9894f-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9894f-148">OUTPUTS</span></span>

### <span data-ttu-id="9894f-149">Aucun</span><span class="sxs-lookup"><span data-stu-id="9894f-149">None</span></span>
<span data-ttu-id="9894f-150">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="9894f-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="9894f-151">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9894f-151">NOTES</span></span>

* <span data-ttu-id="9894f-152">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="9894f-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="9894f-153">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="9894f-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="9894f-154">**Unregister-Event** ne peut pas supprimer les événements créés à l’aide de l’applet de commande New-Event, sauf si vous êtes abonné à l’événement à l’aide de l’applet de commande **Register-EngineEvent** .</span><span class="sxs-lookup"><span data-stu-id="9894f-154">**Unregister-Event** cannot delete events created by using the New-Event cmdlet unless you have subscribed to the event by using the **Register-EngineEvent** cmdlet.</span></span>
<span data-ttu-id="9894f-155">Pour supprimer un événement personnalisé de la session, vous devez le supprimer par programmation ou fermer la session.</span><span class="sxs-lookup"><span data-stu-id="9894f-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

*

## <span data-ttu-id="9894f-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9894f-156">RELATED LINKS</span></span>

[<span data-ttu-id="9894f-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="9894f-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="9894f-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="9894f-159">New-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="9894f-160">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="9894f-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="9894f-161">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="9894f-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="9894f-162">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="9894f-163">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="9894f-164">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="9894f-164">Wait-Event</span></span>](Wait-Event.md)

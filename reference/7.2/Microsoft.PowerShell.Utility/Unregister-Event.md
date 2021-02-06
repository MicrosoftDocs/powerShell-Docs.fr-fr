---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 863dbba4c106f1f57c9396823692620bb358b646
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598566"
---
# <span data-ttu-id="ff347-102">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-102">Unregister-Event</span></span>

## <span data-ttu-id="ff347-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ff347-103">SYNOPSIS</span></span>
<span data-ttu-id="ff347-104">Annule un abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="ff347-104">Cancels an event subscription.</span></span>

## <span data-ttu-id="ff347-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ff347-105">SYNTAX</span></span>

### <span data-ttu-id="ff347-106">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ff347-106">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ff347-107">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="ff347-107">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ff347-108">Description</span><span class="sxs-lookup"><span data-stu-id="ff347-108">DESCRIPTION</span></span>

<span data-ttu-id="ff347-109">L' `Unregister-Event` applet de commande annule un abonnement aux événements qui a été créé à l’aide de l’applet de commande `Register-EngineEvent` , `Register-ObjectEvent` ou `Register-WmiEvent` .</span><span class="sxs-lookup"><span data-stu-id="ff347-109">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="ff347-110">Quand un abonnement aux événements est annulé, l'abonné aux événements est supprimé de la session et les événements ayant fait l'objet d'un abonnement ne sont plus ajoutés à la file d'attente d'événements.</span><span class="sxs-lookup"><span data-stu-id="ff347-110">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="ff347-111">Lorsque vous annulez un abonnement à un événement créé à l’aide de l’applet de commande `New-Event` , le nouvel événement est également supprimé de la session.</span><span class="sxs-lookup"><span data-stu-id="ff347-111">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="ff347-112">`Unregister-Event` ne supprime pas les événements de la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="ff347-112">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="ff347-113">Pour supprimer des événements, utilisez l’applet de commande `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="ff347-113">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="ff347-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ff347-114">EXAMPLES</span></span>

### <span data-ttu-id="ff347-115">Exemple 1 : annuler un abonnement à un événement par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="ff347-115">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="ff347-116">Cette commande annule l’abonnement aux événements qui a un identificateur source de ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="ff347-116">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="ff347-117">Pour Rechercher l’identificateur source d’un événement, utilisez l’applet de commande `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="ff347-117">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="ff347-118">Pour Rechercher l’identificateur source d’un abonnement aux événements, utilisez l' `Get-EventSubscriber` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ff347-118">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="ff347-119">Exemple 2 : annuler un abonnement aux événements par identificateur d’abonnement</span><span class="sxs-lookup"><span data-stu-id="ff347-119">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="ff347-120">Cette commande annule l'abonnement aux événements qui a l'identificateur d'abonnement 2.</span><span class="sxs-lookup"><span data-stu-id="ff347-120">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="ff347-121">Pour Rechercher l’identificateur d’abonnement d’un abonnement aux événements, utilisez l’applet de commande `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="ff347-121">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="ff347-122">Exemple 3 : annuler tous les abonnements aux événements</span><span class="sxs-lookup"><span data-stu-id="ff347-122">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="ff347-123">Cette commande annule tous les abonnements aux événements dans la session.</span><span class="sxs-lookup"><span data-stu-id="ff347-123">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="ff347-124">La commande utilise l' `Get-EventSubscriber` applet de commande pour récupérer tous les objets d’abonné aux événements dans la session, y compris les abonnés qui sont masqués à l’aide du paramètre **SupportEvent** des applets de commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="ff347-124">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="ff347-125">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les objets de l’abonné à `Unregister-Event` , qui les supprime de la session.</span><span class="sxs-lookup"><span data-stu-id="ff347-125">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="ff347-126">Pour effectuer la tâche, le paramètre **force** est également requis sur `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="ff347-126">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="ff347-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff347-127">PARAMETERS</span></span>

### <span data-ttu-id="ff347-128">-Force</span><span class="sxs-lookup"><span data-stu-id="ff347-128">-Force</span></span>

<span data-ttu-id="ff347-129">Annule tous les abonnements aux événements, y compris les abonnements qui ont été masqués à l’aide du paramètre **SupportEvent** de `Register-ObjectEvent` , `Register-WmiEvent` et `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="ff347-129">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

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

### <span data-ttu-id="ff347-130">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="ff347-130">-SourceIdentifier</span></span>

<span data-ttu-id="ff347-131">Spécifie un identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="ff347-131">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="ff347-132">Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="ff347-132">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

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

### <span data-ttu-id="ff347-133">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="ff347-133">-SubscriptionId</span></span>

<span data-ttu-id="ff347-134">Spécifie un ID d’identificateur de source que cette applet de commande annule les abonnements aux événements.</span><span class="sxs-lookup"><span data-stu-id="ff347-134">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="ff347-135">Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="ff347-135">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

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

### <span data-ttu-id="ff347-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ff347-136">-Confirm</span></span>

<span data-ttu-id="ff347-137">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ff347-137">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ff347-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ff347-138">-WhatIf</span></span>

<span data-ttu-id="ff347-139">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ff347-139">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ff347-140">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ff347-140">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ff347-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff347-141">CommonParameters</span></span>

<span data-ttu-id="ff347-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ff347-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff347-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ff347-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff347-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ff347-144">INPUTS</span></span>

### <span data-ttu-id="ff347-145">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="ff347-145">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="ff347-146">Vous pouvez diriger la sortie de `Get-EventSubscriber` vers `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="ff347-146">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="ff347-147">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ff347-147">OUTPUTS</span></span>

### <span data-ttu-id="ff347-148">None</span><span class="sxs-lookup"><span data-stu-id="ff347-148">None</span></span>

<span data-ttu-id="ff347-149">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ff347-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="ff347-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ff347-150">NOTES</span></span>

<span data-ttu-id="ff347-151">Aucune source d’événements disponible sur les plateformes Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="ff347-151">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="ff347-152">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ff347-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="ff347-153">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="ff347-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="ff347-154">`Unregister-Event` Impossible de supprimer les événements créés à l’aide de l’applet de commande `New-Event` , sauf si vous êtes abonné à l’événement à l’aide de l’applet de commande `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="ff347-154">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="ff347-155">Pour supprimer un événement personnalisé de la session, vous devez le supprimer par programmation ou fermer la session.</span><span class="sxs-lookup"><span data-stu-id="ff347-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="ff347-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ff347-156">RELATED LINKS</span></span>

[<span data-ttu-id="ff347-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="ff347-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="ff347-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="ff347-159">New-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="ff347-160">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="ff347-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="ff347-161">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="ff347-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="ff347-162">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="ff347-163">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="ff347-164">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="ff347-164">Wait-Event</span></span>](Wait-Event.md)

---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 3193de9020f2f54795bde9d5cce1bb86c4431ef9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598339"
---
# <span data-ttu-id="f4856-102">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-102">Remove-Event</span></span>

## <span data-ttu-id="f4856-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f4856-103">SYNOPSIS</span></span>
<span data-ttu-id="f4856-104">Supprime les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="f4856-104">Deletes events from the event queue.</span></span>

## <span data-ttu-id="f4856-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f4856-105">SYNTAX</span></span>

### <span data-ttu-id="f4856-106">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f4856-106">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4856-107">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="f4856-107">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f4856-108">Description</span><span class="sxs-lookup"><span data-stu-id="f4856-108">DESCRIPTION</span></span>

<span data-ttu-id="f4856-109">L' `Remove-Event` applet de commande supprime les événements de la file d’attente d’événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f4856-109">The `Remove-Event` cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="f4856-110">Cette applet de commande ne supprime que les événements actuellement dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f4856-110">This cmdlet deletes only the events currently in the queue.</span></span> <span data-ttu-id="f4856-111">Pour annuler les inscriptions d’événements ou vous désabonner, utilisez l’applet de commande `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="f4856-111">To cancel event registrations or unsubscribe, use the `Unregister-Event` cmdlet.</span></span>

## <span data-ttu-id="f4856-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f4856-112">EXAMPLES</span></span>

### <span data-ttu-id="f4856-113">Exemple 1 : supprimer un événement par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="f4856-113">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="f4856-114">Cette commande supprime les événements avec un identificateur de source de processus démarré à partir de la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="f4856-114">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="f4856-115">Exemple 2 : supprimer un événement par identificateur d’événement</span><span class="sxs-lookup"><span data-stu-id="f4856-115">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="f4856-116">Cette commande supprime l'événement avec un ID d'événement égal à 30 de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="f4856-116">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="f4856-117">Exemple 3 : supprimer tous les événements</span><span class="sxs-lookup"><span data-stu-id="f4856-117">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="f4856-118">Cette commande supprime tous les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="f4856-118">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="f4856-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4856-119">PARAMETERS</span></span>

### <span data-ttu-id="f4856-120">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="f4856-120">-EventIdentifier</span></span>

<span data-ttu-id="f4856-121">Spécifie l’identificateur d’événement pour lequel l’applet de commande est supprimée.</span><span class="sxs-lookup"><span data-stu-id="f4856-121">Specifies the event identifier for which the cmdlet deletes.</span></span> <span data-ttu-id="f4856-122">Un paramètre **EventIdentifier** ou **SourceIdentifier** est requis dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="f4856-122">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

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

### <span data-ttu-id="f4856-123">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="f4856-123">-SourceIdentifier</span></span>

<span data-ttu-id="f4856-124">Spécifie l’identificateur source pour lequel cette applet de commande supprime les événements.</span><span class="sxs-lookup"><span data-stu-id="f4856-124">Specifies the source identifier for which this cmdlet deletes events from.</span></span> <span data-ttu-id="f4856-125">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="f4856-125">Wildcards are not permitted.</span></span> <span data-ttu-id="f4856-126">Un paramètre **EventIdentifier** ou **SourceIdentifier** est requis dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="f4856-126">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

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

### <span data-ttu-id="f4856-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f4856-127">-Confirm</span></span>

<span data-ttu-id="f4856-128">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f4856-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f4856-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f4856-129">-WhatIf</span></span>

<span data-ttu-id="f4856-130">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f4856-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f4856-131">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="f4856-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f4856-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4856-132">CommonParameters</span></span>

<span data-ttu-id="f4856-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4856-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4856-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f4856-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4856-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f4856-135">INPUTS</span></span>

### <span data-ttu-id="f4856-136">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="f4856-136">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="f4856-137">Vous pouvez diriger les événements de `Get-Event` vers `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="f4856-137">You can pipe events from `Get-Event` to `Remove-Event`.</span></span>

## <span data-ttu-id="f4856-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f4856-138">OUTPUTS</span></span>

### <span data-ttu-id="f4856-139">None</span><span class="sxs-lookup"><span data-stu-id="f4856-139">None</span></span>

<span data-ttu-id="f4856-140">L'applet de commande ne génère pas de résultat.</span><span class="sxs-lookup"><span data-stu-id="f4856-140">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f4856-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f4856-141">NOTES</span></span>

<span data-ttu-id="f4856-142">Aucune source d’événements disponible sur les plateformes Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="f4856-142">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="f4856-143">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f4856-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="f4856-144">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="f4856-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="f4856-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f4856-145">RELATED LINKS</span></span>

[<span data-ttu-id="f4856-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="f4856-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="f4856-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="f4856-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="f4856-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="f4856-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="f4856-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="f4856-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="f4856-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="f4856-152">Wait-Event</span></span>](Wait-Event.md)

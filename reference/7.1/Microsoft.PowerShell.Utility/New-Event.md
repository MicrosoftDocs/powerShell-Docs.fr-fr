---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 0e7f263d309908a4a62187d3d1cc5ef08283e0c3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344403"
---
# <span data-ttu-id="826c5-103">New-Event</span><span class="sxs-lookup"><span data-stu-id="826c5-103">New-Event</span></span>

## <span data-ttu-id="826c5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="826c5-104">SYNOPSIS</span></span>
<span data-ttu-id="826c5-105">Crée un événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-105">Creates a new event.</span></span>

## <span data-ttu-id="826c5-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="826c5-106">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="826c5-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="826c5-107">DESCRIPTION</span></span>

<span data-ttu-id="826c5-108">L' `New-Event` applet de commande crée un nouvel événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="826c5-108">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="826c5-109">Vous pouvez utiliser des événements personnalisés pour informer les utilisateurs des changements d'état dans votre programme et de toute modification que votre programme peut détecter, y compris des conditions liées au matériel ou au système, de l'état de l'application, de l'état du disque, de l'état du réseau ou de l'achèvement d'une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="826c5-109">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="826c5-110">Les événements personnalisés sont automatiquement ajoutés à la file d'attente des événements dans votre session chaque fois qu'ils sont déclenchés. Vous n'avez pas besoin de vous y abonner.</span><span class="sxs-lookup"><span data-stu-id="826c5-110">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="826c5-111">Toutefois, si vous souhaitez transférer un événement à la session locale ou spécifier une action pour répondre à l’événement, utilisez l' `Register-EngineEvent` applet de commande pour vous abonner à l’événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="826c5-111">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="826c5-112">Quand vous vous abonnez à un événement personnalisé, l'abonné aux événements est ajouté à votre session.</span><span class="sxs-lookup"><span data-stu-id="826c5-112">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="826c5-113">Si vous annulez l’abonnement à un événement à l’aide de l’applet de commande `Unregister-Event` , l’abonné aux événements et l’événement personnalisé sont supprimés de la session.</span><span class="sxs-lookup"><span data-stu-id="826c5-113">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="826c5-114">Si vous ne vous abonnez pas à l’événement personnalisé, vous devez modifier les conditions du programme ou fermer la session PowerShell pour supprimer l’événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-114">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="826c5-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="826c5-115">EXAMPLES</span></span>

### <span data-ttu-id="826c5-116">Exemple 1 : créer un événement dans la file d’attente des événements</span><span class="sxs-lookup"><span data-stu-id="826c5-116">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="826c5-117">Cette commande crée un nouvel événement dans la file d’attente des événements PowerShell.</span><span class="sxs-lookup"><span data-stu-id="826c5-117">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="826c5-118">Elle utilise un objet **Windows. Timer** pour envoyer l’événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-118">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="826c5-119">Exemple 2 : déclencher un événement en réponse à un autre événement</span><span class="sxs-lookup"><span data-stu-id="826c5-119">Example 2: Raise an event in response to another event</span></span>

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

<span data-ttu-id="826c5-120">Cet exemple de fonction utilise l' `New-Event` applet de commande pour déclencher un événement en réponse à un autre événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-120">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="826c5-121">La commande utilise l' `Register-ObjectEvent` applet de commande pour s’abonner à l’événement Windows Management Instrumentation (WMI) qui est déclenché lors de la création d’un nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="826c5-121">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="826c5-122">La commande utilise le paramètre **action** de l’applet de commande pour appeler l’applet de commande `New-Event` , qui crée le nouvel événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-122">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="826c5-123">Étant donné que les événements `New-Event` déclenchés sont automatiquement ajoutés à la file d’attente des événements PowerShell, vous n’avez pas besoin de vous inscrire à cet événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-123">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="826c5-124">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="826c5-124">PARAMETERS</span></span>

### <span data-ttu-id="826c5-125">-Arguments</span><span class="sxs-lookup"><span data-stu-id="826c5-125">-EventArguments</span></span>

<span data-ttu-id="826c5-126">Spécifie un objet qui contient des options relatives à l'événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-126">Specifies an object that contains options for the event.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="826c5-127">-MessageData</span><span class="sxs-lookup"><span data-stu-id="826c5-127">-MessageData</span></span>

<span data-ttu-id="826c5-128">Spécifie des données supplémentaires associées à l'événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-128">Specifies additional data associated with the event.</span></span> <span data-ttu-id="826c5-129">La valeur de ce paramètre apparaît dans la propriété **MessageData** de l'objet d'événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-129">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="826c5-130">-Expéditeur</span><span class="sxs-lookup"><span data-stu-id="826c5-130">-Sender</span></span>

<span data-ttu-id="826c5-131">Spécifie l'objet qui déclenche l'événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-131">Specifies the object that raises the event.</span></span> <span data-ttu-id="826c5-132">La valeur par défaut est le moteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="826c5-132">The default is the PowerShell engine.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="826c5-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="826c5-133">-SourceIdentifier</span></span>

<span data-ttu-id="826c5-134">Spécifie un nom pour le nouvel événement.</span><span class="sxs-lookup"><span data-stu-id="826c5-134">Specifies a name for the new event.</span></span> <span data-ttu-id="826c5-135">Ce paramètre est obligatoire et il doit être unique dans la session.</span><span class="sxs-lookup"><span data-stu-id="826c5-135">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="826c5-136">La valeur de ce paramètre apparaît dans la propriété **SourceIdentifier** des événements.</span><span class="sxs-lookup"><span data-stu-id="826c5-136">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="826c5-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="826c5-137">CommonParameters</span></span>

<span data-ttu-id="826c5-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="826c5-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="826c5-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="826c5-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="826c5-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="826c5-140">INPUTS</span></span>

### <span data-ttu-id="826c5-141">Aucun</span><span class="sxs-lookup"><span data-stu-id="826c5-141">None</span></span>

<span data-ttu-id="826c5-142">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="826c5-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="826c5-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="826c5-143">OUTPUTS</span></span>

### <span data-ttu-id="826c5-144">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="826c5-144">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="826c5-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="826c5-145">NOTES</span></span>

<span data-ttu-id="826c5-146">Aucune source d’événements disponible sur les plateformes Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="826c5-146">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="826c5-147">Le nouvel événement personnalisé, l'abonnement aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="826c5-147">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="826c5-148">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="826c5-148">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="826c5-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="826c5-149">RELATED LINKS</span></span>

[<span data-ttu-id="826c5-150">Get-Event</span><span class="sxs-lookup"><span data-stu-id="826c5-150">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="826c5-151">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="826c5-151">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="826c5-152">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="826c5-152">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="826c5-153">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="826c5-153">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="826c5-154">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="826c5-154">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="826c5-155">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="826c5-155">Wait-Event</span></span>](Wait-Event.md)

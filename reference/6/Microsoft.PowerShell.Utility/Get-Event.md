---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 1920d7a834de133b377cdab7e16851c86477c3da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204642"
---
# <span data-ttu-id="35fc0-103">Get-Event</span><span class="sxs-lookup"><span data-stu-id="35fc0-103">Get-Event</span></span>

## <span data-ttu-id="35fc0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="35fc0-104">SYNOPSIS</span></span>
<span data-ttu-id="35fc0-105">Obtient les événements présents dans la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-105">Gets the events in the event queue.</span></span>

## <span data-ttu-id="35fc0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35fc0-106">SYNTAX</span></span>

### <span data-ttu-id="35fc0-107">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="35fc0-107">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="35fc0-108">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="35fc0-108">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="35fc0-109">Description</span><span class="sxs-lookup"><span data-stu-id="35fc0-109">DESCRIPTION</span></span>

<span data-ttu-id="35fc0-110">L’applet de commande **obtenir-Event** obtient les événements de la file d’attente des événements PowerShell pour la session active.</span><span class="sxs-lookup"><span data-stu-id="35fc0-110">The **Get-Event** cmdlet gets events in the PowerShell event queue for the current session.</span></span>
<span data-ttu-id="35fc0-111">Vous pouvez récupérer tous les événements ou utiliser le paramètre *EventIdentifier* ou *SourceIdentifier* pour spécifier les événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-111">You can get all events or use the *EventIdentifier* or *SourceIdentifier* parameter to specify the events.</span></span>

<span data-ttu-id="35fc0-112">Quand un événement se produit, il est ajouté à la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-112">When an event occurs, it is added to the event queue.</span></span>
<span data-ttu-id="35fc0-113">La file d’attente d’événements comprend les événements que vous avez enregistrés, les événements créés à l’aide de l’applet de commande New-Event et l’événement qui est déclenché lorsque PowerShell se ferme.</span><span class="sxs-lookup"><span data-stu-id="35fc0-113">The event queue includes events for which you have registered, events created by using the New-Event cmdlet, and the event that is raised when PowerShell exits.</span></span>
<span data-ttu-id="35fc0-114">Vous pouvez utiliser la Wait-Event de l’accès en cas d’utilisation d' **un événement** ou d’une pour récupérer les événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-114">You can use **Get-Event** or Wait-Event to get the events.</span></span>

<span data-ttu-id="35fc0-115">Cette applet de commande n'obtient pas les événements des journaux de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-115">This cmdlet does not get events from the Event Viewer logs.</span></span>
<span data-ttu-id="35fc0-116">Pour obtenir ces événements, utilisez Get-WinEvent ou Get-EventLog.</span><span class="sxs-lookup"><span data-stu-id="35fc0-116">To get those events, use Get-WinEvent or Get-EventLog.</span></span>

## <span data-ttu-id="35fc0-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="35fc0-117">EXAMPLES</span></span>

### <span data-ttu-id="35fc0-118">Exemple 1 : récupération de tous les événements</span><span class="sxs-lookup"><span data-stu-id="35fc0-118">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="35fc0-119">Cette commande obtient tous les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-119">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="35fc0-120">Exemple 2 : récupérer des événements par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="35fc0-120">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="35fc0-121">Cette commande obtient les événements dans lesquels la valeur de la propriété SourceIdentifier est PowerShell. ProcessCreated.</span><span class="sxs-lookup"><span data-stu-id="35fc0-121">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="35fc0-122">Exemple 3 : récupération d’un événement en fonction de l’heure à laquelle il a été généré</span><span class="sxs-lookup"><span data-stu-id="35fc0-122">Example 3: Get an event based on the time it was generated</span></span>

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

<span data-ttu-id="35fc0-123">Cet exemple montre comment obtenir des événements à l'aide d'autres propriétés que SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="35fc0-123">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="35fc0-124">La première commande récupère tous les événements dans la file d’attente d’événements et les enregistre dans la variable $Events.</span><span class="sxs-lookup"><span data-stu-id="35fc0-124">The first command gets all events in the event queue and saves them in the $Events variable.</span></span>

<span data-ttu-id="35fc0-125">La deuxième commande utilise la notation de tableau pour récupérer le premier événement (index 0) dans le tableau dans la variable $Events.</span><span class="sxs-lookup"><span data-stu-id="35fc0-125">The second command uses array notation to get the first (0-index) event in the array in the $Events variable.</span></span>
<span data-ttu-id="35fc0-126">La commande utilise un opérateur de pipeline (|) pour envoyer l'événement à la commande Format-List, qui affiche toutes les propriétés de l'événement dans une liste.</span><span class="sxs-lookup"><span data-stu-id="35fc0-126">The command uses a pipeline operator (|) to send the event to the Format-List command, which displays all properties of the event in a list.</span></span>
<span data-ttu-id="35fc0-127">Cela vous permet d'examiner les propriétés de l'objet d'événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-127">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="35fc0-128">La troisième commande montre comment utiliser l’applet de commande Where-Object pour récupérer un événement en fonction de l’heure à laquelle il a été généré.</span><span class="sxs-lookup"><span data-stu-id="35fc0-128">The third command shows how to use the Where-Object cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="35fc0-129">Exemple 4 : récupération d’un événement à l’aide de son identificateur</span><span class="sxs-lookup"><span data-stu-id="35fc0-129">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="35fc0-130">Cette commande obtient l'événement ayant l'identificateur d'événement 2.</span><span class="sxs-lookup"><span data-stu-id="35fc0-130">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="35fc0-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35fc0-131">PARAMETERS</span></span>

### <span data-ttu-id="35fc0-132">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="35fc0-132">-EventIdentifier</span></span>

<span data-ttu-id="35fc0-133">Spécifie les identificateurs d’événements pour lesquels cette applet de commande obtient des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-133">Specifies the event identifiers for which this cmdlet gets events.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35fc0-134">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="35fc0-134">-SourceIdentifier</span></span>

<span data-ttu-id="35fc0-135">Spécifie les identificateurs sources pour lesquels cette applet de commande obtient des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-135">Specifies source identifiers for which this cmdlet gets events.</span></span>
<span data-ttu-id="35fc0-136">La valeur par défaut correspond à l'ensemble des événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="35fc0-136">The default is all events in the event queue.</span></span>
<span data-ttu-id="35fc0-137">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="35fc0-137">Wildcards are not permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35fc0-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35fc0-138">CommonParameters</span></span>

<span data-ttu-id="35fc0-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35fc0-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35fc0-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="35fc0-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35fc0-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="35fc0-141">INPUTS</span></span>

### <span data-ttu-id="35fc0-142">Aucun</span><span class="sxs-lookup"><span data-stu-id="35fc0-142">None</span></span>

<span data-ttu-id="35fc0-143">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35fc0-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="35fc0-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="35fc0-144">OUTPUTS</span></span>

### <span data-ttu-id="35fc0-145">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="35fc0-145">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="35fc0-146">L' **événement de récupération** renvoie un objet **PSEventArgs** pour chaque événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-146">**Get-Event** returns a **PSEventArgs** object for each event.</span></span>
<span data-ttu-id="35fc0-147">Pour afficher une description de cet objet, tapez `Get-Help Get-Event -Full` et consultez la section Remarques de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="35fc0-147">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="35fc0-148">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="35fc0-148">NOTES</span></span>

* <span data-ttu-id="35fc0-149">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="35fc0-149">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="35fc0-150">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="35fc0-150">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="35fc0-151">L’applet de commande **obtenir-Event** retourne un objet **PSEventArgs** ( **System. Management. Automation. PSEventArgs** ) avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="35fc0-151">The **Get-Event** cmdlet returns a **PSEventArgs** object ( **System.Management.Automation.PSEventArgs** ) with the following properties:</span></span>

  - <span data-ttu-id="35fc0-152">Nomd’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-152">ComputerName.</span></span>
<span data-ttu-id="35fc0-153">nom de l'ordinateur sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="35fc0-153">The name of the computer on which the event occurred.</span></span>
<span data-ttu-id="35fc0-154">La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="35fc0-154">This property value is populated only when the event is forwarded from a remote computer.</span></span>

  - <span data-ttu-id="35fc0-155">RunspaceId.</span><span class="sxs-lookup"><span data-stu-id="35fc0-155">RunspaceId.</span></span>
<span data-ttu-id="35fc0-156">GUID qui identifie de façon unique la session dans laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="35fc0-156">A GUID that uniquely identifies the session in which the event occurred.</span></span>
<span data-ttu-id="35fc0-157">La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="35fc0-157">This property value is populated only when the event is forwarded from a remote computer.</span></span>

  - <span data-ttu-id="35fc0-158">EventIdentifier.</span><span class="sxs-lookup"><span data-stu-id="35fc0-158">EventIdentifier.</span></span>
<span data-ttu-id="35fc0-159">entier (Int32) qui identifie de façon unique la notification d'événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="35fc0-159">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

  - <span data-ttu-id="35fc0-160">Expéditeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-160">Sender.</span></span>
<span data-ttu-id="35fc0-161">objet qui a généré l'événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-161">The object that generated the event.</span></span>
<span data-ttu-id="35fc0-162">Dans la valeur du paramètre *action* , la variable automatique $sender contient l’objet sender.</span><span class="sxs-lookup"><span data-stu-id="35fc0-162">In the value of the *Action* parameter, the $Sender automatic variable contains the sender object.</span></span>

  - <span data-ttu-id="35fc0-163">SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="35fc0-163">SourceEventArgs.</span></span>
<span data-ttu-id="35fc0-164">premier paramètre qui dérive d'EventArgs, s'il existe.</span><span class="sxs-lookup"><span data-stu-id="35fc0-164">The first parameter that derives from EventArgs, if it exists.</span></span>
<span data-ttu-id="35fc0-165">Par exemple, dans un événement de minuteur écoulé dans lequel la signature a le formulaire sender Object sender, Timers. ElapsedEventArgs e, la propriété SourceEventArgs contient Timers. ElapsedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="35fc0-165">For example, in a timer elapsed event in which the signature has the form Object sender, Timers.ElapsedEventArgs e, the SourceEventArgs property would contain the Timers.ElapsedEventArgs.</span></span>
<span data-ttu-id="35fc0-166">Dans la valeur du paramètre *action* , la variable automatique $EventArgs contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-166">In the value of the *Action* parameter, the $EventArgs automatic variable contains this value.</span></span>

  - <span data-ttu-id="35fc0-167">SourceArgs.</span><span class="sxs-lookup"><span data-stu-id="35fc0-167">SourceArgs.</span></span>
<span data-ttu-id="35fc0-168">tous les paramètres de la signature d'événement d'origine.</span><span class="sxs-lookup"><span data-stu-id="35fc0-168">All parameters of the original event signature.</span></span>
<span data-ttu-id="35fc0-169">Pour une signature d’événement standard, $Args \[ 0 \] représente l’expéditeur, et $args \[ 1 \] représente le SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="35fc0-169">For a standard event signature, $Args\[0\] represents the sender, and $Args\[1\] represents the SourceEventArgs.</span></span>
<span data-ttu-id="35fc0-170">Dans la valeur du paramètre *action* , la variable automatique $args contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-170">In the value of the *Action* parameter, the $Args automatic variable contains this value.</span></span>

  - <span data-ttu-id="35fc0-171">SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="35fc0-171">SourceIdentifier.</span></span>
<span data-ttu-id="35fc0-172">chaîne qui identifie l'abonnement à l'événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-172">A string that identifies the event subscription.</span></span>
<span data-ttu-id="35fc0-173">Dans la valeur du paramètre *action* , la propriété SourceIdentifier de la variable automatique $Event contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-173">In the value of the *Action* parameter, the SourceIdentifier property of the $Event automatic variable contains this value.</span></span>

  - <span data-ttu-id="35fc0-174">TimeGenerated.</span><span class="sxs-lookup"><span data-stu-id="35fc0-174">TimeGenerated.</span></span>
<span data-ttu-id="35fc0-175">Objet **DateTime** qui représente l’heure à laquelle l’événement a été généré.</span><span class="sxs-lookup"><span data-stu-id="35fc0-175">A **DateTime** object that represents the time at which the event was generated.</span></span>
<span data-ttu-id="35fc0-176">Dans la valeur du paramètre *action* , la propriété TimeGenerated de la variable automatique $Event contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-176">In the value of the *Action* parameter, the TimeGenerated property of the $Event automatic variable contains this value.</span></span>

  - <span data-ttu-id="35fc0-177">MessageData.</span><span class="sxs-lookup"><span data-stu-id="35fc0-177">MessageData.</span></span>
<span data-ttu-id="35fc0-178">données associées à l'abonnement à l'événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-178">Data associated with the event subscription.</span></span>
<span data-ttu-id="35fc0-179">Les utilisateurs spécifient ces données quand ils s'inscrivent à un événement.</span><span class="sxs-lookup"><span data-stu-id="35fc0-179">Users specify this data when they register an event.</span></span>
<span data-ttu-id="35fc0-180">Dans la valeur du paramètre *action* , la propriété MessageData de la variable automatique $Event contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="35fc0-180">In the value of the *Action* parameter, the MessageData property of the $Event automatic variable contains this value.</span></span>

## <span data-ttu-id="35fc0-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="35fc0-181">RELATED LINKS</span></span>

[<span data-ttu-id="35fc0-182">New-Event</span><span class="sxs-lookup"><span data-stu-id="35fc0-182">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="35fc0-183">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="35fc0-183">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="35fc0-184">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="35fc0-184">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="35fc0-185">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="35fc0-185">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="35fc0-186">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="35fc0-186">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="35fc0-187">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="35fc0-187">Wait-Event</span></span>](Wait-Event.md)

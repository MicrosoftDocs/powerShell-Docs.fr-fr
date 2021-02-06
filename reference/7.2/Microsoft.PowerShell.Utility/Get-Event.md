---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 4b275d489984f85aea401b781e38c80fbc4b2177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597767"
---
# <span data-ttu-id="5419b-102">Get-Event</span><span class="sxs-lookup"><span data-stu-id="5419b-102">Get-Event</span></span>

## <span data-ttu-id="5419b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5419b-103">SYNOPSIS</span></span>
<span data-ttu-id="5419b-104">Obtient les événements présents dans la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-104">Gets the events in the event queue.</span></span>

## <span data-ttu-id="5419b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5419b-105">SYNTAX</span></span>

### <span data-ttu-id="5419b-106">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5419b-106">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="5419b-107">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="5419b-107">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="5419b-108">Description</span><span class="sxs-lookup"><span data-stu-id="5419b-108">DESCRIPTION</span></span>

<span data-ttu-id="5419b-109">L' `Get-Event` applet de commande obtient les événements de la file d’attente des événements PowerShell pour la session active.</span><span class="sxs-lookup"><span data-stu-id="5419b-109">The `Get-Event` cmdlet gets events in the PowerShell event queue for the current session.</span></span> <span data-ttu-id="5419b-110">Vous pouvez récupérer tous les événements ou utiliser le paramètre **EventIdentifier** ou **SourceIdentifier** pour spécifier les événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-110">You can get all events or use the **EventIdentifier** or **SourceIdentifier** parameter to specify the events.</span></span>

<span data-ttu-id="5419b-111">Quand un événement se produit, il est ajouté à la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-111">When an event occurs, it is added to the event queue.</span></span> <span data-ttu-id="5419b-112">La file d’attente d’événements comprend les événements que vous avez enregistrés, les événements créés à l’aide de l’applet de commande `New-Event` et l’événement qui est déclenché lorsque PowerShell se ferme.</span><span class="sxs-lookup"><span data-stu-id="5419b-112">The event queue includes events for which you have registered, events created by using the `New-Event` cmdlet, and the event that is raised when PowerShell exits.</span></span> <span data-ttu-id="5419b-113">Vous pouvez utiliser `Get-Event` ou `Wait-Event` pour récupérer les événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-113">You can use `Get-Event` or `Wait-Event` to get the events.</span></span>

<span data-ttu-id="5419b-114">Cette applet de commande n'obtient pas les événements des journaux de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-114">This cmdlet does not get events from the Event Viewer logs.</span></span> <span data-ttu-id="5419b-115">Pour accéder à ces événements, utilisez `Get-WinEvent` ou `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="5419b-115">To get those events, use `Get-WinEvent` or `Get-EventLog`.</span></span>

## <span data-ttu-id="5419b-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5419b-116">EXAMPLES</span></span>

### <span data-ttu-id="5419b-117">Exemple 1 : récupération de tous les événements</span><span class="sxs-lookup"><span data-stu-id="5419b-117">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="5419b-118">Cette commande obtient tous les événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-118">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="5419b-119">Exemple 2 : récupérer des événements par identificateur de source</span><span class="sxs-lookup"><span data-stu-id="5419b-119">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="5419b-120">Cette commande obtient les événements dans lesquels la valeur de la propriété SourceIdentifier est PowerShell. ProcessCreated.</span><span class="sxs-lookup"><span data-stu-id="5419b-120">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="5419b-121">Exemple 3 : récupération d’un événement en fonction de l’heure à laquelle il a été généré</span><span class="sxs-lookup"><span data-stu-id="5419b-121">Example 3: Get an event based on the time it was generated</span></span>

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

<span data-ttu-id="5419b-122">Cet exemple montre comment obtenir des événements à l'aide d'autres propriétés que SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="5419b-122">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="5419b-123">La première commande récupère tous les événements dans la file d’attente d’événements et les enregistre dans la `$Events` variable.</span><span class="sxs-lookup"><span data-stu-id="5419b-123">The first command gets all events in the event queue and saves them in the `$Events` variable.</span></span>

<span data-ttu-id="5419b-124">La deuxième commande utilise la notation de tableau pour récupérer le premier événement (index 0) dans le tableau de la `$Events` variable.</span><span class="sxs-lookup"><span data-stu-id="5419b-124">The second command uses array notation to get the first (0-index) event in the array in the `$Events` variable.</span></span> <span data-ttu-id="5419b-125">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer l’événement à la `Format-List` commande, qui affiche toutes les propriétés de l’événement dans une liste.</span><span class="sxs-lookup"><span data-stu-id="5419b-125">The command uses a pipeline operator (`|`) to send the event to the `Format-List` command, which displays all properties of the event in a list.</span></span> <span data-ttu-id="5419b-126">Cela vous permet d'examiner les propriétés de l'objet d'événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-126">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="5419b-127">La troisième commande montre comment utiliser l' `Where-Object` applet de commande pour récupérer un événement en fonction de l’heure à laquelle il a été généré.</span><span class="sxs-lookup"><span data-stu-id="5419b-127">The third command shows how to use the `Where-Object` cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="5419b-128">Exemple 4 : récupération d’un événement à l’aide de son identificateur</span><span class="sxs-lookup"><span data-stu-id="5419b-128">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="5419b-129">Cette commande obtient l'événement ayant l'identificateur d'événement 2.</span><span class="sxs-lookup"><span data-stu-id="5419b-129">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="5419b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5419b-130">PARAMETERS</span></span>

### <span data-ttu-id="5419b-131">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="5419b-131">-EventIdentifier</span></span>

<span data-ttu-id="5419b-132">Spécifie les identificateurs d’événements pour lesquels cette applet de commande obtient des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-132">Specifies the event identifiers for which this cmdlet gets events.</span></span>

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

### <span data-ttu-id="5419b-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="5419b-133">-SourceIdentifier</span></span>

<span data-ttu-id="5419b-134">Spécifie les identificateurs sources pour lesquels cette applet de commande obtient des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-134">Specifies source identifiers for which this cmdlet gets events.</span></span> <span data-ttu-id="5419b-135">La valeur par défaut correspond à l'ensemble des événements de la file d'attente des événements.</span><span class="sxs-lookup"><span data-stu-id="5419b-135">The default is all events in the event queue.</span></span> <span data-ttu-id="5419b-136">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="5419b-136">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="5419b-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5419b-137">CommonParameters</span></span>

<span data-ttu-id="5419b-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5419b-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5419b-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5419b-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5419b-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5419b-140">INPUTS</span></span>

### <span data-ttu-id="5419b-141">None</span><span class="sxs-lookup"><span data-stu-id="5419b-141">None</span></span>

<span data-ttu-id="5419b-142">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5419b-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5419b-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5419b-143">OUTPUTS</span></span>

### <span data-ttu-id="5419b-144">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="5419b-144">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="5419b-145">`Get-Event` retourne un objet **PSEventArgs** pour chaque événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-145">`Get-Event` returns a **PSEventArgs** object for each event.</span></span> <span data-ttu-id="5419b-146">Pour afficher une description de cet objet, tapez `Get-Help Get-Event -Full` et consultez la section Remarques de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="5419b-146">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="5419b-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5419b-147">NOTES</span></span>

<span data-ttu-id="5419b-148">Aucune source d’événements disponible sur les plateformes Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="5419b-148">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="5419b-149">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5419b-149">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="5419b-150">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="5419b-150">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="5419b-151">L' `Get-Event` applet de commande retourne un objet **PSEventArgs** (**System. Management. Automation. PSEventArgs**) avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5419b-151">The `Get-Event` cmdlet returns a **PSEventArgs** object (**System.Management.Automation.PSEventArgs**) with the following properties:</span></span>

- <span data-ttu-id="5419b-152">Nomd’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5419b-152">ComputerName.</span></span> <span data-ttu-id="5419b-153">nom de l'ordinateur sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="5419b-153">The name of the computer on which the event occurred.</span></span> <span data-ttu-id="5419b-154">La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5419b-154">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="5419b-155">RunspaceId.</span><span class="sxs-lookup"><span data-stu-id="5419b-155">RunspaceId.</span></span> <span data-ttu-id="5419b-156">GUID qui identifie de façon unique la session dans laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="5419b-156">A GUID that uniquely identifies the session in which the event occurred.</span></span> <span data-ttu-id="5419b-157">La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5419b-157">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="5419b-158">EventIdentifier.</span><span class="sxs-lookup"><span data-stu-id="5419b-158">EventIdentifier.</span></span> <span data-ttu-id="5419b-159">entier (Int32) qui identifie de façon unique la notification d'événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5419b-159">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

- <span data-ttu-id="5419b-160">Expéditeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-160">Sender.</span></span> <span data-ttu-id="5419b-161">objet qui a généré l'événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-161">The object that generated the event.</span></span> <span data-ttu-id="5419b-162">Dans la valeur du paramètre **action** , la `$Sender` variable automatique contient l’objet sender.</span><span class="sxs-lookup"><span data-stu-id="5419b-162">In the value of the **Action** parameter, the `$Sender` automatic variable contains the sender object.</span></span>

- <span data-ttu-id="5419b-163">SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="5419b-163">SourceEventArgs.</span></span> <span data-ttu-id="5419b-164">premier paramètre qui dérive d'EventArgs, s'il existe.</span><span class="sxs-lookup"><span data-stu-id="5419b-164">The first parameter that derives from EventArgs, if it exists.</span></span> <span data-ttu-id="5419b-165">Par exemple, dans un événement de minuteur écoulé dans lequel la signature a le formulaire sender Object sender, **Timers. ElapsedEventArgs** e, la propriété **SourceEventArgs** contient **Timers. ElapsedEventArgs**.</span><span class="sxs-lookup"><span data-stu-id="5419b-165">For example, in a timer elapsed event in which the signature has the form Object sender, **Timers.ElapsedEventArgs** e, the **SourceEventArgs** property would contain the **Timers.ElapsedEventArgs**.</span></span> <span data-ttu-id="5419b-166">Dans la valeur du paramètre **action** , la `$EventArgs` variable automatique contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-166">In the value of the **Action** parameter, the `$EventArgs` automatic variable contains this value.</span></span>

- <span data-ttu-id="5419b-167">SourceArgs.</span><span class="sxs-lookup"><span data-stu-id="5419b-167">SourceArgs.</span></span> <span data-ttu-id="5419b-168">tous les paramètres de la signature d'événement d'origine.</span><span class="sxs-lookup"><span data-stu-id="5419b-168">All parameters of the original event signature.</span></span> <span data-ttu-id="5419b-169">Pour une signature d’événement standard, `$Args[0]` représente l’expéditeur et `$Args[1]` représente le **SourceEventArgs**.</span><span class="sxs-lookup"><span data-stu-id="5419b-169">For a standard event signature, `$Args[0]` represents the sender, and `$Args[1]` represents the **SourceEventArgs**.</span></span> <span data-ttu-id="5419b-170">Dans la valeur du paramètre **action** , la `$Args` variable automatique contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-170">In the value of the **Action** parameter, the `$Args` automatic variable contains this value.</span></span>

- <span data-ttu-id="5419b-171">SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="5419b-171">SourceIdentifier.</span></span> <span data-ttu-id="5419b-172">chaîne qui identifie l'abonnement à l'événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-172">A string that identifies the event subscription.</span></span> <span data-ttu-id="5419b-173">Dans la valeur du paramètre **action** , la propriété **SourceIdentifier** de la `$Event` variable Automatic contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-173">In the value of the **Action** parameter, the **SourceIdentifier** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="5419b-174">TimeGenerated.</span><span class="sxs-lookup"><span data-stu-id="5419b-174">TimeGenerated.</span></span> <span data-ttu-id="5419b-175">Objet **DateTime** qui représente l’heure à laquelle l’événement a été généré.</span><span class="sxs-lookup"><span data-stu-id="5419b-175">A **DateTime** object that represents the time at which the event was generated.</span></span>
  <span data-ttu-id="5419b-176">Dans la valeur du paramètre **action** , la propriété **TimeGenerated** de la `$Event` variable Automatic contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-176">In the value of the **Action** parameter, the **TimeGenerated** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="5419b-177">MessageData.</span><span class="sxs-lookup"><span data-stu-id="5419b-177">MessageData.</span></span> <span data-ttu-id="5419b-178">données associées à l'abonnement à l'événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-178">Data associated with the event subscription.</span></span> <span data-ttu-id="5419b-179">Les utilisateurs spécifient ces données quand ils s'inscrivent à un événement.</span><span class="sxs-lookup"><span data-stu-id="5419b-179">Users specify this data when they register an event.</span></span> <span data-ttu-id="5419b-180">Dans la valeur du paramètre **action** , la propriété **MessageData** de la `$Event` variable Automatic contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5419b-180">In the value of the **Action** parameter, the **MessageData** property of the `$Event` automatic variable contains this value.</span></span>

## <span data-ttu-id="5419b-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5419b-181">RELATED LINKS</span></span>

[<span data-ttu-id="5419b-182">New-Event</span><span class="sxs-lookup"><span data-stu-id="5419b-182">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="5419b-183">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="5419b-183">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="5419b-184">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="5419b-184">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="5419b-185">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="5419b-185">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="5419b-186">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="5419b-186">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="5419b-187">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="5419b-187">Wait-Event</span></span>](Wait-Event.md)

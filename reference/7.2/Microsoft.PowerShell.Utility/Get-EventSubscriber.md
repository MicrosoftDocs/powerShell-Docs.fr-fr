---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: b8f55770770fa9077f654d382818386cc480c638
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596323"
---
# <span data-ttu-id="57b42-102">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="57b42-102">Get-EventSubscriber</span></span>

## <span data-ttu-id="57b42-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="57b42-103">SYNOPSIS</span></span>
<span data-ttu-id="57b42-104">Obtient les abonnés aux événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="57b42-104">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="57b42-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="57b42-105">SYNTAX</span></span>

### <span data-ttu-id="57b42-106">BySource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="57b42-106">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="57b42-107">Méthode BYID</span><span class="sxs-lookup"><span data-stu-id="57b42-107">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="57b42-108">Description</span><span class="sxs-lookup"><span data-stu-id="57b42-108">DESCRIPTION</span></span>

<span data-ttu-id="57b42-109">L’applet de commande **obtenir-EventSubscriber** obtient les abonnés aux événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="57b42-109">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="57b42-110">Lorsque vous vous abonnez à un événement à l’aide d’une applet de commande d’événement Register, un abonné aux événements est ajouté à votre session PowerShell et les événements auxquels vous vous êtes abonné sont ajoutés à la file d’attente d’événements chaque fois qu’ils sont déclenchés.</span><span class="sxs-lookup"><span data-stu-id="57b42-110">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="57b42-111">Pour annuler l'abonnement à un événement, supprimez l'abonné aux événements à l'aide de l'applet de commande Unregister-Event.</span><span class="sxs-lookup"><span data-stu-id="57b42-111">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="57b42-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="57b42-112">EXAMPLES</span></span>

### <span data-ttu-id="57b42-113">Exemple 1 : obtenir l’abonné aux événements pour un événement de minuterie</span><span class="sxs-lookup"><span data-stu-id="57b42-113">Example 1: Get the event subscriber for a timer event</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

<span data-ttu-id="57b42-114">Cet exemple utilise une commande **EventSubscriber** pour obtenir l’abonné aux événements pour un événement de minuterie.</span><span class="sxs-lookup"><span data-stu-id="57b42-114">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="57b42-115">La première commande utilise l'applet de commande New-Object pour créer une instance d'un objet minuteur.</span><span class="sxs-lookup"><span data-stu-id="57b42-115">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="57b42-116">Elle enregistre le nouvel objet minuteur dans la variable $Timer.</span><span class="sxs-lookup"><span data-stu-id="57b42-116">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="57b42-117">La deuxième commande utilise l'applet de commande Get-Member pour afficher les événements qui sont disponibles pour les objets minuteur.</span><span class="sxs-lookup"><span data-stu-id="57b42-117">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="57b42-118">La commande utilise le paramètre de type de l’applet de commande **obten-Member** avec la valeur Event.</span><span class="sxs-lookup"><span data-stu-id="57b42-118">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="57b42-119">La troisième commande utilise l'applet de commande Register-ObjectEvent pour s'inscrire à l'événement Elapsed sur l'objet minuteur.</span><span class="sxs-lookup"><span data-stu-id="57b42-119">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="57b42-120">La quatrième commande utilise l’applet de commande **obtenir-EventSubscriber** pour obtenir l’abonné aux événements pour l’événement Elapsed.</span><span class="sxs-lookup"><span data-stu-id="57b42-120">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="57b42-121">Exemple 2 : utiliser le module dynamique dans PSEventJob dans la propriété action de l’abonné aux événements</span><span class="sxs-lookup"><span data-stu-id="57b42-121">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

<span data-ttu-id="57b42-122">Cet exemple montre comment utiliser le module dynamique dans l’objet **PSEventJob** dans la propriété action de l’abonné aux événements.</span><span class="sxs-lookup"><span data-stu-id="57b42-122">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="57b42-123">La première commande utilise l'applet de commande New-Object pour créer un objet Timer.</span><span class="sxs-lookup"><span data-stu-id="57b42-123">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="57b42-124">La deuxième commande définit l'intervalle de la minuterie à 500 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="57b42-124">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="57b42-125">La troisième commande utilise l'applet de commande Register-ObjectEvent pour inscrire l'événement Elapsed de l'objet Timer.</span><span class="sxs-lookup"><span data-stu-id="57b42-125">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="57b42-126">La commande comprend une action qui gère l'événement.</span><span class="sxs-lookup"><span data-stu-id="57b42-126">The command includes an action that handles the event.</span></span>
<span data-ttu-id="57b42-127">Chaque fois que l'intervalle de la minuterie est dépassé, un événement est déclenché et les commandes de l'action s'exécutent.</span><span class="sxs-lookup"><span data-stu-id="57b42-127">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="57b42-128">Dans ce cas, l’applet de commande Get-Random génère un nombre aléatoire compris entre 0 et 100 et l’enregistre dans la variable $Random.</span><span class="sxs-lookup"><span data-stu-id="57b42-128">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="57b42-129">L'identificateur source de l'événement est Timer.Random.</span><span class="sxs-lookup"><span data-stu-id="57b42-129">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="57b42-130">Quand vous utilisez un paramètre d' *action* dans une commande **Register-ObjectEvent** , la commande retourne un objet **PSEventJob** qui représente l’action.</span><span class="sxs-lookup"><span data-stu-id="57b42-130">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="57b42-131">La quatrième commande active la minuterie.</span><span class="sxs-lookup"><span data-stu-id="57b42-131">The fourth command enables the timer.</span></span>

<span data-ttu-id="57b42-132">La cinquième commande utilise l’applet de commande **EventSubscriber** pour récupérer l’abonné aux événements de l’événement Timer. Random.</span><span class="sxs-lookup"><span data-stu-id="57b42-132">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="57b42-133">Elle enregistre l’objet d’abonné aux événements dans la variable $Subscriber.</span><span class="sxs-lookup"><span data-stu-id="57b42-133">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="57b42-134">La sixième commande indique que la propriété action de l’objet d’abonné aux événements contient un objet **PSEventJob** .</span><span class="sxs-lookup"><span data-stu-id="57b42-134">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="57b42-135">En fait, elle contient le même objet **PSEventJob** que celui retourné par la commande **Register-ObjectEvent** .</span><span class="sxs-lookup"><span data-stu-id="57b42-135">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="57b42-136">La septième commande utilise l’applet de commande Format-List pour afficher toutes les propriétés de l’objet **PSEventJob** dans la propriété action dans une liste.</span><span class="sxs-lookup"><span data-stu-id="57b42-136">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="57b42-137">Le résultat révèle que l’objet **PSEventJob** a une propriété module qui contient un module de script dynamique qui implémente l’action.</span><span class="sxs-lookup"><span data-stu-id="57b42-137">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="57b42-138">Les commandes restantes utilisent l’opérateur d’appel (&) pour appeler la commande dans le module et afficher la valeur de la variable $Random.</span><span class="sxs-lookup"><span data-stu-id="57b42-138">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="57b42-139">Vous pouvez utiliser l'opérateur d'appel pour appeler une commande dans un module, y compris des commandes qui ne sont pas exportées.</span><span class="sxs-lookup"><span data-stu-id="57b42-139">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="57b42-140">Dans ce cas, les commandes montrent le nombre aléatoire qui est généré quand l'événement Elapsed se produit.</span><span class="sxs-lookup"><span data-stu-id="57b42-140">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="57b42-141">Pour plus d’informations sur les modules, consultez [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="57b42-141">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="57b42-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="57b42-142">PARAMETERS</span></span>

### <span data-ttu-id="57b42-143">-Force</span><span class="sxs-lookup"><span data-stu-id="57b42-143">-Force</span></span>

<span data-ttu-id="57b42-144">Indique que cette applet de commande obtient tous les abonnés aux événements, y compris les abonnés pour les événements qui sont masqués à l’aide du paramètre *SupportEvent* de Register-ObjectEvent, Register-WmiEvent et Register-EngineEvent.</span><span class="sxs-lookup"><span data-stu-id="57b42-144">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="57b42-145">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="57b42-145">-SourceIdentifier</span></span>

<span data-ttu-id="57b42-146">Spécifie la valeur de la propriété **SourceIdentifier** qui obtient uniquement les abonnés aux événements.</span><span class="sxs-lookup"><span data-stu-id="57b42-146">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="57b42-147">Par défaut, l’option **EventSubscriber** obtient tous les abonnés aux événements dans la session.</span><span class="sxs-lookup"><span data-stu-id="57b42-147">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="57b42-148">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="57b42-148">Wildcards are not permitted.</span></span>
<span data-ttu-id="57b42-149">Ce paramètre respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="57b42-149">This parameter is case-sensitive.</span></span>

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

### <span data-ttu-id="57b42-150">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="57b42-150">-SubscriptionId</span></span>

<span data-ttu-id="57b42-151">Spécifie l’identificateur d’abonnement que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="57b42-151">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="57b42-152">Par défaut, l’option **EventSubscriber** obtient tous les abonnés aux événements dans la session.</span><span class="sxs-lookup"><span data-stu-id="57b42-152">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

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

### <span data-ttu-id="57b42-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57b42-153">CommonParameters</span></span>

<span data-ttu-id="57b42-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57b42-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57b42-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57b42-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57b42-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="57b42-156">INPUTS</span></span>

### <span data-ttu-id="57b42-157">None</span><span class="sxs-lookup"><span data-stu-id="57b42-157">None</span></span>

<span data-ttu-id="57b42-158">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="57b42-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="57b42-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="57b42-159">OUTPUTS</span></span>

### <span data-ttu-id="57b42-160">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="57b42-160">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="57b42-161">La méthode **obtient-EventSubscriber** retourne un objet qui représente chaque abonné aux événements.</span><span class="sxs-lookup"><span data-stu-id="57b42-161">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="57b42-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="57b42-162">NOTES</span></span>

* <span data-ttu-id="57b42-163">L'applet de commande New-Event, qui crée un événement personnalisé, ne génère pas d'abonné.</span><span class="sxs-lookup"><span data-stu-id="57b42-163">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="57b42-164">Par conséquent, l’applet de commande **EventSubscriber** ne trouvera pas d’objet d’abonné pour ces événements.</span><span class="sxs-lookup"><span data-stu-id="57b42-164">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="57b42-165">Toutefois, si vous utilisez l’applet de commande Register-EngineEvent pour vous abonner à un événement personnalisé (afin de transférer l’événement ou de spécifier une action), la commande **EventSubscriber** trouve l’abonné généré par **Register-EngineEvent** .</span><span class="sxs-lookup"><span data-stu-id="57b42-165">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="57b42-166">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="57b42-166">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="57b42-167">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="57b42-167">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="57b42-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="57b42-168">RELATED LINKS</span></span>

[<span data-ttu-id="57b42-169">Get-Event</span><span class="sxs-lookup"><span data-stu-id="57b42-169">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="57b42-170">New-Event</span><span class="sxs-lookup"><span data-stu-id="57b42-170">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="57b42-171">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="57b42-171">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="57b42-172">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="57b42-172">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="57b42-173">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="57b42-173">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="57b42-174">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="57b42-174">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="57b42-175">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="57b42-175">Wait-Event</span></span>](Wait-Event.md)


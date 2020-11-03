---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "93205810"
---
# <span data-ttu-id="3f18b-103">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="3f18b-103">Register-WmiEvent</span></span>

## <span data-ttu-id="3f18b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3f18b-104">SYNOPSIS</span></span>
<span data-ttu-id="3f18b-105">S'abonne à un événement Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="3f18b-105">Subscribes to a Windows Management Instrumentation (WMI) event.</span></span>

## <span data-ttu-id="3f18b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3f18b-106">SYNTAX</span></span>

### <span data-ttu-id="3f18b-107">classe (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3f18b-107">class (Default)</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3f18b-108">query</span><span class="sxs-lookup"><span data-stu-id="3f18b-108">query</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3f18b-109">Description</span><span class="sxs-lookup"><span data-stu-id="3f18b-109">DESCRIPTION</span></span>

<span data-ttu-id="3f18b-110">L' `Register-WmiEvent` applet de commande s’abonne aux événements Windows Management Instrumentation (WMI) sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3f18b-110">The `Register-WmiEvent` cmdlet subscribes to Windows Management Instrumentation (WMI) events on the local computer or on a remote computer.</span></span>

<span data-ttu-id="3f18b-111">Lorsque l'événement WMI abonné se déclenche, il est ajouté à la file d'attente des événements dans votre session locale, même si l'événement se produit sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3f18b-111">When the subscribed WMI event is raised, it is added to the event queue in your local session even if the event occurs on a remote computer.</span></span> <span data-ttu-id="3f18b-112">Pour récupérer des événements dans la file d’attente d’événements, utilisez l’applet de commande `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="3f18b-112">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="3f18b-113">Vous pouvez utiliser les paramètres de `Register-WmiEvent` pour vous abonner à des événements sur des ordinateurs distants et pour spécifier les valeurs de propriété des événements qui peuvent vous aider à identifier l’événement dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="3f18b-113">You can use the parameters of `Register-WmiEvent` to subscribe to events on remote computers and to specify the property values of the events that can help you identify the event in the queue.</span></span> <span data-ttu-id="3f18b-114">Vous pouvez également utiliser le paramètre **action** pour spécifier les actions à entreprendre lorsqu’un événement abonné est déclenché.</span><span class="sxs-lookup"><span data-stu-id="3f18b-114">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised.</span></span>

<span data-ttu-id="3f18b-115">Lorsque vous vous abonnez à un événement, un abonné est ajouté à votre session.</span><span class="sxs-lookup"><span data-stu-id="3f18b-115">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="3f18b-116">Pour obtenir les abonnés aux événements dans la session, utilisez l'applet de commande `Get-EventSubscriber`.</span><span class="sxs-lookup"><span data-stu-id="3f18b-116">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="3f18b-117">Pour annuler l'abonnement, utilisez l'applet de commande `Unregister-Event`, ce qui supprime l'abonné aux événements de la session.</span><span class="sxs-lookup"><span data-stu-id="3f18b-117">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

<span data-ttu-id="3f18b-118">Les nouvelles applets de commande Common Information Model (CIM), ont introduit Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI.</span><span class="sxs-lookup"><span data-stu-id="3f18b-118">New Common Information Model (CIM) cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="3f18b-119">Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme CIM, qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs qui exécutent le système d’exploitation Windows et ceux qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3f18b-119">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those that run other operating systems.</span></span> <span data-ttu-id="3f18b-120">Au lieu d’utiliser `Register-WmiEvent` , envisagez d’utiliser l’applet [de commande Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) .</span><span class="sxs-lookup"><span data-stu-id="3f18b-120">Instead of using `Register-WmiEvent`, consider using the [Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet.</span></span>

## <span data-ttu-id="3f18b-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3f18b-121">EXAMPLES</span></span>

### <span data-ttu-id="3f18b-122">Exemple 1 : s’abonner à des événements générés par une classe</span><span class="sxs-lookup"><span data-stu-id="3f18b-122">Example 1: Subscribe to events generated by a class</span></span>

<span data-ttu-id="3f18b-123">Cette commande s’abonne aux événements générés par la classe **Win32_ProcessStartTrace** .</span><span class="sxs-lookup"><span data-stu-id="3f18b-123">This command subscribes to the events generated by the **Win32_ProcessStartTrace** class.</span></span> <span data-ttu-id="3f18b-124">Cette classe déclenche un événement à chaque démarrage d'un processus.</span><span class="sxs-lookup"><span data-stu-id="3f18b-124">This class raises an event whenever a process starts.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="3f18b-125">Exemple 2 : s’abonner aux événements de création d’un processus</span><span class="sxs-lookup"><span data-stu-id="3f18b-125">Example 2: Subscribe to creation events for a process</span></span>

<span data-ttu-id="3f18b-126">Cette commande utilise une requête pour s'abonner aux événements de création de l'instance Win32_process.</span><span class="sxs-lookup"><span data-stu-id="3f18b-126">This command uses a query to subscribe to Win32_process instance creation events.</span></span>

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### <span data-ttu-id="3f18b-127">Exemple 3 : utiliser une action pour répondre à un événement</span><span class="sxs-lookup"><span data-stu-id="3f18b-127">Example 3: Use an action to respond to an event</span></span>

<span data-ttu-id="3f18b-128">Cet exemple montre comment utiliser une action pour répondre à un événement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-128">This example shows how to use an action to respond to an event.</span></span> <span data-ttu-id="3f18b-129">Dans ce cas, lorsqu’un processus démarre, toutes les `Start-Process` commandes de la session active sont écrites dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3f18b-129">In this case, when a process starts, any `Start-Process` commands in the current session are written to an XML file.</span></span>

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

<span data-ttu-id="3f18b-130">Quand vous utilisez le paramètre d' **action** , `Register-WmiEvent` retourne une tâche en arrière-plan qui représente l’action d’événement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-130">When you use the **Action** parameter, `Register-WmiEvent` returns a background job that represents the event action.</span></span> <span data-ttu-id="3f18b-131">Vous pouvez utiliser les applets de commande **Job** , telles que `Get-Job` et `Receive-Job` , pour gérer la tâche d’événement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-131">You can use the **Job** cmdlets, such as `Get-Job` and `Receive-Job`, to manage the event job.</span></span>

<span data-ttu-id="3f18b-132">Pour plus d'informations, consultez about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="3f18b-132">For more information, see about_Jobs.</span></span>

### <span data-ttu-id="3f18b-133">Exemple 4 : s’inscrire pour des événements sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="3f18b-133">Example 4: Register for events on a remote computer</span></span>

<span data-ttu-id="3f18b-134">Cet exemple inscrit des événements sur l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="3f18b-134">This example registers for events on the Server01 remote computer.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

<span data-ttu-id="3f18b-135">WMI retourne les événements à l'ordinateur local et les stocke dans la file d'attente des événements dans la session active.</span><span class="sxs-lookup"><span data-stu-id="3f18b-135">WMI returns the events to the local computer and stores them in the event queue in the current session.</span></span> <span data-ttu-id="3f18b-136">Pour récupérer les événements, exécutez une `Get-Event` commande locale.</span><span class="sxs-lookup"><span data-stu-id="3f18b-136">To retrieve the events, run a local `Get-Event` command.</span></span>

## <span data-ttu-id="3f18b-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3f18b-137">PARAMETERS</span></span>

### <span data-ttu-id="3f18b-138">-Action</span><span class="sxs-lookup"><span data-stu-id="3f18b-138">-Action</span></span>

<span data-ttu-id="3f18b-139">Spécifie les commandes qui gèrent les événements.</span><span class="sxs-lookup"><span data-stu-id="3f18b-139">Specifies commands that handle the events.</span></span> <span data-ttu-id="3f18b-140">Les commandes dans le paramètre **action** s’exécutent quand un événement est déclenché au lieu d’envoyer l’événement à la file d’attente d’événements.</span><span class="sxs-lookup"><span data-stu-id="3f18b-140">The commands in the **Action** parameter run when an event is raised instead of sending the event to the event queue.</span></span> <span data-ttu-id="3f18b-141">Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3f18b-141">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="3f18b-142">La valeur de l' **action** peut inclure `$Event` les `$EventSubscriber` variables automatiques,,, `$Sender` `$EventArgs` et `$Args` , qui fournissent des informations sur l’événement au bloc de script de l' **action** .</span><span class="sxs-lookup"><span data-stu-id="3f18b-142">The value of **Action** can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="3f18b-143">Pour plus d'informations, consultez about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="3f18b-143">For more information, see about_Automatic_Variables.</span></span>

<span data-ttu-id="3f18b-144">Lorsque vous spécifiez une action, `Register-WmiEvent` retourne un objet de tâche d’événement qui représente cette action.</span><span class="sxs-lookup"><span data-stu-id="3f18b-144">When you specify an action, `Register-WmiEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="3f18b-145">Vous pouvez utiliser les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ) pour gérer la tâche d’événement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-145">You can use the cmdlets that contain the **Job** noun (the **Job** cmdlets) to manage the event job.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-146">-Classe</span><span class="sxs-lookup"><span data-stu-id="3f18b-146">-Class</span></span>

<span data-ttu-id="3f18b-147">Spécifie l'événement auquel vous vous abonnez.</span><span class="sxs-lookup"><span data-stu-id="3f18b-147">Specifies the event to which you are subscribing.</span></span> <span data-ttu-id="3f18b-148">Entrez la classe WMI qui génère les événements.</span><span class="sxs-lookup"><span data-stu-id="3f18b-148">Enter the WMI class that generates the events.</span></span> <span data-ttu-id="3f18b-149">Une **classe** ou un paramètre de **requête** est requis dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="3f18b-149">A **Class** or **Query** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3f18b-150">-ComputerName</span></span>

<span data-ttu-id="3f18b-151">Spécifie le nom de l’ordinateur sur lequel la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3f18b-151">Specifies the name of the computer on which the command runs.</span></span> <span data-ttu-id="3f18b-152">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3f18b-152">The default is the local computer.</span></span>

<span data-ttu-id="3f18b-153">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3f18b-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of the computer.</span></span> <span data-ttu-id="3f18b-154">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="3f18b-154">To specify the local computer, type the computer name, a dot (`.`), or localhost.</span></span>

<span data-ttu-id="3f18b-155">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f18b-155">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="3f18b-156">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="3f18b-156">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3f18b-157">-Credential</span></span>

<span data-ttu-id="3f18b-158">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="3f18b-158">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="3f18b-159">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="3f18b-159">The default is the current user.</span></span>

<span data-ttu-id="3f18b-160">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3f18b-160">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3f18b-161">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="3f18b-161">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-162">-Suivant</span><span class="sxs-lookup"><span data-stu-id="3f18b-162">-Forward</span></span>

<span data-ttu-id="3f18b-163">Indique que cette applet de commande envoie des événements pour cet abonnement à la session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3f18b-163">Indicates that this cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="3f18b-164">Utilisez ce paramètre lorsque vous vous inscrivez aux événements sur un ordinateur distant ou dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="3f18b-164">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="3f18b-165">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="3f18b-165">-MaxTriggerCount</span></span>

<span data-ttu-id="3f18b-166">Spécifie le nombre maximal de déclencheurs.</span><span class="sxs-lookup"><span data-stu-id="3f18b-166">Specifies the maximum trigger count.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-167">-MessageData</span><span class="sxs-lookup"><span data-stu-id="3f18b-167">-MessageData</span></span>

<span data-ttu-id="3f18b-168">Spécifie toutes les données supplémentaires à associer à cet abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="3f18b-168">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="3f18b-169">La valeur de ce paramètre apparaît dans la propriété **MessageData** de tous les événements associés à cet abonnement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-169">The value of this parameter appears in the **MessageData** property of all events associated with this subscription.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-170">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3f18b-170">-Namespace</span></span>

<span data-ttu-id="3f18b-171">Spécifie l'espace de noms de la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="3f18b-171">Specifies the namespace of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-172">-Query</span><span class="sxs-lookup"><span data-stu-id="3f18b-172">-Query</span></span>

<span data-ttu-id="3f18b-173">Spécifie une requête dans Langage de requêtes WMI (WQL) (WQL) qui identifie la classe d’événements WMI, par exemple : `select * from __InstanceDeletionEvent` .</span><span class="sxs-lookup"><span data-stu-id="3f18b-173">Specifies a query in WMI Query Language (WQL) that identifies the WMI event class, such as: `select * from __InstanceDeletionEvent`.</span></span>

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-174">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="3f18b-174">-SourceIdentifier</span></span>

<span data-ttu-id="3f18b-175">Spécifie un nom que vous sélectionnez pour l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-175">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="3f18b-176">Le nom que vous sélectionnez doit être unique dans la session active.</span><span class="sxs-lookup"><span data-stu-id="3f18b-176">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="3f18b-177">La valeur par défaut est le GUID affecté par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f18b-177">The default value is the GUID that Windows PowerShell assigns.</span></span>

<span data-ttu-id="3f18b-178">La valeur de ce paramètre apparaît dans la valeur de la propriété **SourceIdentifier** de l'objet d'abonné et de tous les objets d'événements associés à cet abonnement.</span><span class="sxs-lookup"><span data-stu-id="3f18b-178">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-179">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="3f18b-179">-SupportEvent</span></span>

<span data-ttu-id="3f18b-180">Indique que cette applet de commande masque l’abonnement aux événements.</span><span class="sxs-lookup"><span data-stu-id="3f18b-180">Indicates that this cmdlet hides the event subscription.</span></span> <span data-ttu-id="3f18b-181">Utilisez ce paramètre lorsque l'abonnement actuel fait partie d'un mécanisme d'inscription d'événement plus complexe et qu'il ne doit pas être découvert indépendamment.</span><span class="sxs-lookup"><span data-stu-id="3f18b-181">Use this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="3f18b-182">Pour afficher ou annuler un abonnement qui a été créé à l’aide du paramètre **SupportEvent** , spécifiez le paramètre **force** des `Get-EventSubscriber` applets de commande et `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="3f18b-182">To view or cancel a subscription that was created by using the **SupportEvent** parameter, specify the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="3f18b-183">-Timeout</span><span class="sxs-lookup"><span data-stu-id="3f18b-183">-Timeout</span></span>

<span data-ttu-id="3f18b-184">Spécifie la durée pendant laquelle Windows PowerShell attend la fin de cette commande.</span><span class="sxs-lookup"><span data-stu-id="3f18b-184">Specifies how long Windows PowerShell waits for this command to finish.</span></span>

<span data-ttu-id="3f18b-185">La valeur par défaut, 0 (zéro), indique qu'aucun délai d'attente n'est défini et fait attendre Windows PowerShell indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="3f18b-185">The default value, 0 (zero), means that there is no time-out, and it causes Windows PowerShell to wait indefinitely.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f18b-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3f18b-186">CommonParameters</span></span>

<span data-ttu-id="3f18b-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3f18b-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3f18b-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3f18b-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3f18b-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3f18b-189">INPUTS</span></span>

### <span data-ttu-id="3f18b-190">Aucun</span><span class="sxs-lookup"><span data-stu-id="3f18b-190">None</span></span>

<span data-ttu-id="3f18b-191">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3f18b-191">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3f18b-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3f18b-192">OUTPUTS</span></span>

### <span data-ttu-id="3f18b-193">Aucun</span><span class="sxs-lookup"><span data-stu-id="3f18b-193">None</span></span>

<span data-ttu-id="3f18b-194">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="3f18b-194">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3f18b-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3f18b-195">NOTES</span></span>

<span data-ttu-id="3f18b-196">Pour utiliser cette applet de commande dans Windows Vista ou une version ultérieure du système d’exploitation Windows, démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="3f18b-196">To use this cmdlet in Windows Vista or a later version of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="3f18b-197">Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="3f18b-197">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="3f18b-198">Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.</span><span class="sxs-lookup"><span data-stu-id="3f18b-198">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="3f18b-199">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3f18b-199">RELATED LINKS</span></span>

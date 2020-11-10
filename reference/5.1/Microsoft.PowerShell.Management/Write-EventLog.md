---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 4044453cb46b407344619f1edd3227213bf67250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388244"
---
# <span data-ttu-id="b9cb9-103">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-103">Write-EventLog</span></span>

## <span data-ttu-id="b9cb9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b9cb9-104">SYNOPSIS</span></span>
<span data-ttu-id="b9cb9-105">Écrit un événement dans un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-105">Writes an event to an event log.</span></span>

## <span data-ttu-id="b9cb9-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b9cb9-106">SYNTAX</span></span>

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## <span data-ttu-id="b9cb9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b9cb9-107">DESCRIPTION</span></span>
<span data-ttu-id="b9cb9-108">L' `Write-EventLog` applet de commande écrit un événement dans un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-108">The `Write-EventLog` cmdlet writes an event to an event log.</span></span>

<span data-ttu-id="b9cb9-109">Pour écrire un événement dans un journal des événements, le journal des événements doit exister sur l'ordinateur et la source du journal des événements doit être inscrite.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-109">To write an event to an event log, the event log must exist on the computer and the source must be registered for the event log.</span></span>

<span data-ttu-id="b9cb9-110">Les applets de commande qui contiennent le nom **EventLog** (les applets de commande **EventLog** ) fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="b9cb9-111">Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez l’applet de commande `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="b9cb9-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the `Get-WinEvent` cmdlet.</span></span>

## <span data-ttu-id="b9cb9-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-112">EXAMPLES</span></span>

### <span data-ttu-id="b9cb9-113">Exemple 1 : écrire un événement dans le journal des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="b9cb9-113">Example 1: Write an event to the Application event log</span></span>

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

<span data-ttu-id="b9cb9-114">Cette commande écrit un événement à partir de la source MyApp dans le journal des événements Application.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-114">This command writes an event from the MyApp source to the Application event log.</span></span>

### <span data-ttu-id="b9cb9-115">Exemple 2 : écrire un événement dans le journal des événements d’application d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="b9cb9-115">Example 2: Write an event to the Application event log of a remote computer</span></span>

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

<span data-ttu-id="b9cb9-116">Cette commande écrit un événement à partir de la source MyApp dans le journal des événements Application sur l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-116">This command writes an event from the MyApp source to the Application event log on the Server01 remote computer.</span></span>

## <span data-ttu-id="b9cb9-117">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-117">PARAMETERS</span></span>

### <span data-ttu-id="b9cb9-118">-Catégorie</span><span class="sxs-lookup"><span data-stu-id="b9cb9-118">-Category</span></span>

<span data-ttu-id="b9cb9-119">Spécifie une catégorie de tâche pour l'événement.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-119">Specifies a task category for the event.</span></span> <span data-ttu-id="b9cb9-120">Entrez un entier qui est associé aux chaînes figurant dans le fichier de messages des catégories pour le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-120">Enter an integer that is associated with the strings in the category message file for the event log.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-121">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b9cb9-121">-ComputerName</span></span>

<span data-ttu-id="b9cb9-122">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-122">Specifies a remote computer.</span></span> <span data-ttu-id="b9cb9-123">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-123">The default is the local computer.</span></span>

<span data-ttu-id="b9cb9-124">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-124">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="b9cb9-125">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-125">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="b9cb9-126">Vous pouvez utiliser le paramètre **ComputerName** de l' `Get-EventLog` applet de commande même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-126">You can use the **ComputerName** parameter of the `Get-EventLog` cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-127">-EntryType</span><span class="sxs-lookup"><span data-stu-id="b9cb9-127">-EntryType</span></span>

<span data-ttu-id="b9cb9-128">Spécifie le type d'entrée de l'événement.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-128">Specifies the entry type of the event.</span></span> <span data-ttu-id="b9cb9-129">Les valeurs acceptables pour ce paramètre sont les suivantes : Error, Warning, information, SuccessAudit et FailureAudit.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-129">The acceptable values for this parameter are: Error, Warning, Information, SuccessAudit, and FailureAudit.</span></span> <span data-ttu-id="b9cb9-130">La valeur par défaut est Information.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-130">The default value is Information.</span></span>

<span data-ttu-id="b9cb9-131">Pour obtenir une description des valeurs, consultez [énumération EventLogEntryType](/dotnet/api/system.diagnostics.eventlogentrytype).</span><span class="sxs-lookup"><span data-stu-id="b9cb9-131">For a description of the values, see [EventLogEntryType Enumeration](/dotnet/api/system.diagnostics.eventlogentrytype).</span></span>

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-132">-EventId</span><span class="sxs-lookup"><span data-stu-id="b9cb9-132">-EventId</span></span>

<span data-ttu-id="b9cb9-133">Spécifie l'identificateur de l'événement.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-133">Specifies the event identifier.</span></span> <span data-ttu-id="b9cb9-134">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-134">This parameter is required.</span></span> <span data-ttu-id="b9cb9-135">La valeur maximale du paramètre **eventID** est 65535.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-135">The maximum value for the **EventId** parameter is 65535.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-136">-LogName</span><span class="sxs-lookup"><span data-stu-id="b9cb9-136">-LogName</span></span>

<span data-ttu-id="b9cb9-137">Spécifie le nom du journal dans lequel l'événement est écrit.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-137">Specifies the name of the log to which the event is written.</span></span> <span data-ttu-id="b9cb9-138">Entrez le nom du journal.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-138">Enter the log name.</span></span> <span data-ttu-id="b9cb9-139">Le nom du journal est la valeur de la propriété **log** , et non **et non LogDisplayName**.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-139">The log name is the value of the **Log** property, not the **LogDisplayName**.</span></span> <span data-ttu-id="b9cb9-140">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-140">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="b9cb9-141">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-141">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-142">-Message</span><span class="sxs-lookup"><span data-stu-id="b9cb9-142">-Message</span></span>

<span data-ttu-id="b9cb9-143">Spécifie le message de l'événement.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-143">Specifies the event message.</span></span> <span data-ttu-id="b9cb9-144">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-144">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-145">-RawData</span><span class="sxs-lookup"><span data-stu-id="b9cb9-145">-RawData</span></span>

<span data-ttu-id="b9cb9-146">Spécifie les données binaires qui sont associées à l'événement (en octets).</span><span class="sxs-lookup"><span data-stu-id="b9cb9-146">Specifies the binary data that is associated with the event, in bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-147">-Source</span><span class="sxs-lookup"><span data-stu-id="b9cb9-147">-Source</span></span>

<span data-ttu-id="b9cb9-148">Spécifie la source d'événement, qui correspond en général au nom de l'application qui écrit l'événement dans le journal.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-148">Specifies the event source, which is typically the name of the application that is writing the event to the log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b9cb9-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9cb9-149">CommonParameters</span></span>

<span data-ttu-id="b9cb9-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9cb9-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b9cb9-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9cb9-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-152">INPUTS</span></span>

### <span data-ttu-id="b9cb9-153">Aucun</span><span class="sxs-lookup"><span data-stu-id="b9cb9-153">None</span></span>
<span data-ttu-id="b9cb9-154">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-154">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b9cb9-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-155">OUTPUTS</span></span>

### <span data-ttu-id="b9cb9-156">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="b9cb9-156">System.Diagnostics.EventLogEntry</span></span>
<span data-ttu-id="b9cb9-157">Cette applet de commande retourne des objets qui représentent les événements dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-157">This cmdlet returns objects that represents the events in the logs.</span></span>

## <span data-ttu-id="b9cb9-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-158">NOTES</span></span>

<span data-ttu-id="b9cb9-159">Pour utiliser `Write-EventLog` , démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b9cb9-159">To use `Write-EventLog`, start Windows PowerShell by using the Run as administrator option.</span></span>

## <span data-ttu-id="b9cb9-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b9cb9-160">RELATED LINKS</span></span>

[<span data-ttu-id="b9cb9-161">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-161">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="b9cb9-162">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-162">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="b9cb9-163">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-163">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="b9cb9-164">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-164">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="b9cb9-165">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-165">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="b9cb9-166">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-166">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="b9cb9-167">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="b9cb9-167">Write-EventLog</span></span>](Write-EventLog.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203597"
---
# <span data-ttu-id="bba4c-103">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-103">New-EventLog</span></span>

## <span data-ttu-id="bba4c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bba4c-104">SYNOPSIS</span></span>
<span data-ttu-id="bba4c-105">Crée un journal des événements et une source d'événement sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="bba4c-105">Creates a new event log and a new event source on a local or remote computer.</span></span>

## <span data-ttu-id="bba4c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bba4c-106">SYNTAX</span></span>

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## <span data-ttu-id="bba4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="bba4c-107">DESCRIPTION</span></span>

<span data-ttu-id="bba4c-108">Cette applet de commande crée un journal des événements classique sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="bba4c-108">This cmdlet creates a new classic event log on a local or remote computer.</span></span> <span data-ttu-id="bba4c-109">Elle peut également inscrire une source d’événement qui écrit dans le nouveau journal ou dans un journal existant.</span><span class="sxs-lookup"><span data-stu-id="bba4c-109">It can also register an event source that writes to the new log or to an existing log.</span></span>

<span data-ttu-id="bba4c-110">Les applets de commande contenant le nom EventLog (les applets de commande du journal des événements) fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="bba4c-110">The cmdlets that contain the EventLog noun (the Event log cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="bba4c-111">Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="bba4c-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use `Get-WinEvent`.</span></span>

## <span data-ttu-id="bba4c-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bba4c-112">EXAMPLES</span></span>

### <span data-ttu-id="bba4c-113">Exemple 1 : créer un journal des événements</span><span class="sxs-lookup"><span data-stu-id="bba4c-113">Example 1 - create a new event log</span></span>

<span data-ttu-id="bba4c-114">Cette commande crée le journal des événements TestLog sur l’ordinateur local et inscrit une nouvelle source pour lui.</span><span class="sxs-lookup"><span data-stu-id="bba4c-114">This command creates the TestLog event log on the local computer and registers a new source for it.</span></span>

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### <span data-ttu-id="bba4c-115">Exemple 2 : ajouter une nouvelle source d’événement à un journal existant</span><span class="sxs-lookup"><span data-stu-id="bba4c-115">Example 2 - add a new event source to an existing log</span></span>

<span data-ttu-id="bba4c-116">Cette commande ajoute une nouvelle source d’événement (NewTestApp) au journal des applications sur l’ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="bba4c-116">This command adds a new event source, NewTestApp, to the Application log on the Server01 remote computer.</span></span>

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

<span data-ttu-id="bba4c-117">La commande requiert la présence du fichier NewTestApp.dll sur l’ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="bba4c-117">The command requires that the NewTestApp.dll file is located on the Server01 computer.</span></span>

## <span data-ttu-id="bba4c-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bba4c-118">PARAMETERS</span></span>

### <span data-ttu-id="bba4c-119">-CategoryResourceFile</span><span class="sxs-lookup"><span data-stu-id="bba4c-119">-CategoryResourceFile</span></span>

<span data-ttu-id="bba4c-120">Spécifie le chemin d’accès au fichier qui contient les chaînes de catégorie des événements sources.</span><span class="sxs-lookup"><span data-stu-id="bba4c-120">Specifies the path to the file that contains category strings for the source events.</span></span> <span data-ttu-id="bba4c-121">Ce fichier est également appelé fichier de messages des catégories.</span><span class="sxs-lookup"><span data-stu-id="bba4c-121">This file is also known as the Category Message File.</span></span>

<span data-ttu-id="bba4c-122">Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé.</span><span class="sxs-lookup"><span data-stu-id="bba4c-122">The file must be present on the computer on which the event log is being created.</span></span> <span data-ttu-id="bba4c-123">Ce paramètre ne crée pas ou ne déplace pas de fichiers.</span><span class="sxs-lookup"><span data-stu-id="bba4c-123">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-124">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bba4c-124">-ComputerName</span></span>

<span data-ttu-id="bba4c-125">Crée les journaux des événements sur les ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bba4c-125">Creates the new event logs on the specified computers.</span></span> <span data-ttu-id="bba4c-126">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bba4c-126">The default is the local computer.</span></span>

<span data-ttu-id="bba4c-127">Le nom NetBIOS, l’adresse IP ou le nom de domaine complet d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="bba4c-127">The NetBIOS name, IP address, or fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="bba4c-128">Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, un point (.) ou « localhost ».</span><span class="sxs-lookup"><span data-stu-id="bba4c-128">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="bba4c-129">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bba4c-129">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="bba4c-130">Vous pouvez utiliser le paramètre **ComputerName** de `Get-EventLog` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="bba4c-130">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-131">-LogName</span><span class="sxs-lookup"><span data-stu-id="bba4c-131">-LogName</span></span>

<span data-ttu-id="bba4c-132">Spécifie le nom du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="bba4c-132">Specifies the name of the event log.</span></span>

<span data-ttu-id="bba4c-133">Si le journal n’existe pas, `New-EventLog` crée le journal et utilise cette valeur pour les propriétés **log** et **et non LogDisplayName** du nouveau journal des événements.</span><span class="sxs-lookup"><span data-stu-id="bba4c-133">If the log does not exist, `New-EventLog` creates the log and uses this value for the **Log** and **LogDisplayName** properties of the new event log.</span></span> <span data-ttu-id="bba4c-134">Si le journal existe, `New-EventLog` enregistre une nouvelle source pour le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="bba4c-134">If the log exists, `New-EventLog` registers a new source for the event log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-135">-MessageResourceFile</span><span class="sxs-lookup"><span data-stu-id="bba4c-135">-MessageResourceFile</span></span>

<span data-ttu-id="bba4c-136">Spécifie le chemin d’accès au fichier qui contient les chaînes de mise en forme de message des événements sources.</span><span class="sxs-lookup"><span data-stu-id="bba4c-136">Specifies the path to the file that contains message formatting strings for the source events.</span></span>
<span data-ttu-id="bba4c-137">Ce fichier est également appelé fichier de messages des événements.</span><span class="sxs-lookup"><span data-stu-id="bba4c-137">This file is also known as the Event Message File.</span></span>

<span data-ttu-id="bba4c-138">Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé.</span><span class="sxs-lookup"><span data-stu-id="bba4c-138">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="bba4c-139">Ce paramètre ne crée pas ou ne déplace pas de fichiers.</span><span class="sxs-lookup"><span data-stu-id="bba4c-139">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-140">-ParameterResourceFile</span><span class="sxs-lookup"><span data-stu-id="bba4c-140">-ParameterResourceFile</span></span>

<span data-ttu-id="bba4c-141">Spécifie le chemin d’accès au fichier qui contient les chaînes utilisées pour les substitutions de paramètre dans les descriptions d’événement.</span><span class="sxs-lookup"><span data-stu-id="bba4c-141">Specifies the path to the file that contains strings used for parameter substitutions in event descriptions.</span></span> <span data-ttu-id="bba4c-142">Ce fichier est également appelé fichier de messages des paramètres.</span><span class="sxs-lookup"><span data-stu-id="bba4c-142">This file is also known as the Parameter Message File.</span></span>

<span data-ttu-id="bba4c-143">Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé.</span><span class="sxs-lookup"><span data-stu-id="bba4c-143">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="bba4c-144">Ce paramètre ne crée pas ou ne déplace pas de fichiers.</span><span class="sxs-lookup"><span data-stu-id="bba4c-144">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-145">-Source</span><span class="sxs-lookup"><span data-stu-id="bba4c-145">-Source</span></span>

<span data-ttu-id="bba4c-146">Spécifie le nom des sources de journal des événements (programmes d’application qui écrivent dans le journal des événements, par exemple).</span><span class="sxs-lookup"><span data-stu-id="bba4c-146">Specifies the names of the event log sources, such as application programs that write to the event log.</span></span> <span data-ttu-id="bba4c-147">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bba4c-147">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bba4c-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bba4c-148">CommonParameters</span></span>

<span data-ttu-id="bba4c-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bba4c-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bba4c-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bba4c-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bba4c-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bba4c-151">INPUTS</span></span>

### <span data-ttu-id="bba4c-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="bba4c-152">None</span></span>

<span data-ttu-id="bba4c-153">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bba4c-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bba4c-154">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bba4c-154">OUTPUTS</span></span>

### <span data-ttu-id="bba4c-155">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="bba4c-155">System.Diagnostics.EventLogEntry</span></span>

## <span data-ttu-id="bba4c-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bba4c-156">NOTES</span></span>

<span data-ttu-id="bba4c-157">Pour utiliser `New-EventLog` sur Windows Vista et les versions ultérieures de Windows, ouvrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="bba4c-157">To use `New-EventLog` on Windows Vista and later versions of Windows, open PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="bba4c-158">Pour créer une source d’événement sous Windows Vista, Windows XP Professionnel ou Windows Server 2003, vous devez être membre du groupe Administrateurs sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bba4c-158">To create an event source in Windows Vista, Windows XP Professional, or Windows Server 2003, you must be a member of the Administrators group on the computer.</span></span>

<span data-ttu-id="bba4c-159">Lorsque vous créez un journal des événements et une source d’événement, le système inscrit la nouvelle source du nouveau journal, mais le journal n’est pas créé tant qu’une première entrée n’y est pas écrite.</span><span class="sxs-lookup"><span data-stu-id="bba4c-159">When you create a new event log and a new event source, the system registers the new source for the new log, but the log is not created until the first entry is written to it.</span></span>

<span data-ttu-id="bba4c-160">Le système d’exploitation stocke les journaux des événements sous forme de fichiers.</span><span class="sxs-lookup"><span data-stu-id="bba4c-160">The operating system stores event logs as files.</span></span>

<span data-ttu-id="bba4c-161">Lorsque vous créez un journal des événements, le fichier associé est stocké dans le `$env:SystemRoot\System32\Config` répertoire sur l’ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="bba4c-161">When you create a new event log, the associated file is stored in the `$env:SystemRoot\System32\Config` directory on the specified computer.</span></span>

<span data-ttu-id="bba4c-162">Le nom de fichier est les huit premiers caractères de la propriété **log** avec l’extension de nom de fichier. evt.</span><span class="sxs-lookup"><span data-stu-id="bba4c-162">The file name is the first eight characters of the **Log** property with an .evt file name extension.</span></span>

## <span data-ttu-id="bba4c-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bba4c-163">RELATED LINKS</span></span>

[<span data-ttu-id="bba4c-164">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-164">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="bba4c-165">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-165">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="bba4c-166">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="bba4c-166">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="bba4c-167">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-167">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="bba4c-168">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-168">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="bba4c-169">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-169">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="bba4c-170">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-170">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="bba4c-171">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="bba4c-171">Write-EventLog</span></span>](Write-EventLog.md)

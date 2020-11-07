---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 1325b1e604bc450f0aaec3ec4e99afa281aa1d91
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346173"
---
# <span data-ttu-id="be759-103">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="be759-103">Wait-Process</span></span>

## <span data-ttu-id="be759-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="be759-104">SYNOPSIS</span></span>
<span data-ttu-id="be759-105">Attend l'arrêt des processus avant d'accepter une autre entrée.</span><span class="sxs-lookup"><span data-stu-id="be759-105">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="be759-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="be759-106">SYNTAX</span></span>

### <span data-ttu-id="be759-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="be759-107">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="be759-108">Id</span><span class="sxs-lookup"><span data-stu-id="be759-108">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="be759-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="be759-109">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="be759-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="be759-110">DESCRIPTION</span></span>

<span data-ttu-id="be759-111">L’applet de commande **Wait-Process** attend l’arrêt d’un ou de plusieurs processus en cours d’exécution avant d’accepter l’entrée.</span><span class="sxs-lookup"><span data-stu-id="be759-111">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="be759-112">Dans la console PowerShell, cette applet de commande supprime l’invite de commandes jusqu’à ce que les processus soient arrêtés.</span><span class="sxs-lookup"><span data-stu-id="be759-112">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="be759-113">Vous pouvez spécifier un processus par nom de processus ou ID de processus (PID), ou diriger un objet processus vers **Wait-Process**.</span><span class="sxs-lookup"><span data-stu-id="be759-113">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process**.</span></span>

<span data-ttu-id="be759-114">**Wait-Process** fonctionne uniquement sur les processus qui s’exécutent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="be759-114">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="be759-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="be759-115">EXAMPLES</span></span>

### <span data-ttu-id="be759-116">Exemple 1 : arrêter un processus et attendre</span><span class="sxs-lookup"><span data-stu-id="be759-116">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="be759-117">Cet exemple arrête le processus Notepad, puis attend que le processus soit arrêté avant de continuer avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="be759-117">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="be759-118">La première commande utilise l’applet de commande **« obten-process »** pour récupérer l’ID du processus du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="be759-118">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="be759-119">Elle stocke l’ID dans la variable $nid.</span><span class="sxs-lookup"><span data-stu-id="be759-119">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="be759-120">La deuxième commande utilise l’applet de commande Stop-Process pour arrêter le processus avec l’ID stocké dans $nid.</span><span class="sxs-lookup"><span data-stu-id="be759-120">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="be759-121">La troisième commande utilise **Wait-Process** pour attendre jusqu’à ce que le processus Notepad soit arrêté.</span><span class="sxs-lookup"><span data-stu-id="be759-121">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="be759-122">Elle utilise le paramètre *ID* de **Wait-Process** pour identifier le processus.</span><span class="sxs-lookup"><span data-stu-id="be759-122">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="be759-123">Exemple 2 : spécification d’un processus</span><span class="sxs-lookup"><span data-stu-id="be759-123">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="be759-124">Ces commandes indiquent trois méthodes différentes pour spécifier un processus à **attendre**.</span><span class="sxs-lookup"><span data-stu-id="be759-124">These commands show three different methods of specifying a process to **Wait-Process**.</span></span>
<span data-ttu-id="be759-125">La première commande obtient le processus Notepad et le stocke dans la variable $p.</span><span class="sxs-lookup"><span data-stu-id="be759-125">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="be759-126">La deuxième commande utilise le paramètre *ID* , la troisième commande utilise le paramètre *Name* et la quatrième commande utilise le paramètre *InputObject* .</span><span class="sxs-lookup"><span data-stu-id="be759-126">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="be759-127">Ces commandes produisent les mêmes résultats et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="be759-127">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="be759-128">Exemple 3 : attendre des processus pendant une période spécifiée</span><span class="sxs-lookup"><span data-stu-id="be759-128">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="be759-129">Cette commande attend l’arrêt des processus Outlook et Winword pendant 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="be759-129">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="be759-130">Si les deux processus ne se sont pas arrêtés, l’applet de commande affiche une erreur sans fin d’exécution et l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="be759-130">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="be759-131">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="be759-131">PARAMETERS</span></span>

### <span data-ttu-id="be759-132">-Id</span><span class="sxs-lookup"><span data-stu-id="be759-132">-Id</span></span>

<span data-ttu-id="be759-133">Spécifie les identificateurs des processus.</span><span class="sxs-lookup"><span data-stu-id="be759-133">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="be759-134">Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="be759-134">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="be759-135">Pour rechercher le PID d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="be759-135">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be759-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="be759-136">-InputObject</span></span>

<span data-ttu-id="be759-137">Spécifie les processus en envoyant des objets processus.</span><span class="sxs-lookup"><span data-stu-id="be759-137">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="be759-138">Entrez une variable qui contient les objets processus, ou tapez une commande ou une expression qui obtient les objets processus, tels que l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="be759-138">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="be759-139">-Name</span><span class="sxs-lookup"><span data-stu-id="be759-139">-Name</span></span>

<span data-ttu-id="be759-140">Spécifie les noms des processus.</span><span class="sxs-lookup"><span data-stu-id="be759-140">Specifies the process names of the processes.</span></span>
<span data-ttu-id="be759-141">Pour spécifier plusieurs noms, séparez-les à l’aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="be759-141">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="be759-142">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="be759-142">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be759-143">-Timeout</span><span class="sxs-lookup"><span data-stu-id="be759-143">-Timeout</span></span>

<span data-ttu-id="be759-144">Spécifie la durée maximale, en secondes, pendant laquelle cette applet de commande attend que les processus spécifiés s’arrêtent.</span><span class="sxs-lookup"><span data-stu-id="be759-144">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="be759-145">Lorsque ce délai expire, la commande affiche une erreur sans fin d’exécution qui répertorie les processus dont l’exécution se poursuit et elle met un terme à l’attente.</span><span class="sxs-lookup"><span data-stu-id="be759-145">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="be759-146">Par défaut, il n’y a aucun délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="be759-146">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be759-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be759-147">CommonParameters</span></span>

<span data-ttu-id="be759-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be759-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be759-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="be759-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be759-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="be759-150">INPUTS</span></span>

### <span data-ttu-id="be759-151">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="be759-151">System.Diagnostics.Process</span></span>

<span data-ttu-id="be759-152">Vous pouvez diriger un objet processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be759-152">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="be759-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="be759-153">OUTPUTS</span></span>

### <span data-ttu-id="be759-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="be759-154">None</span></span>

<span data-ttu-id="be759-155">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="be759-155">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="be759-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="be759-156">NOTES</span></span>

<span data-ttu-id="be759-157">L’applet de commande est uniquement prise en charge sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="be759-157">The cmdlet is only supported on Windows platforms.</span></span>

<span data-ttu-id="be759-158">Cette applet de commande utilise la méthode **WaitForExit** de la classe **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="be759-158">This cmdlet uses the **WaitForExit** method of the **System.Diagnostics.Process** class.</span></span>

## <span data-ttu-id="be759-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="be759-159">RELATED LINKS</span></span>

[<span data-ttu-id="be759-160">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="be759-160">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="be759-161">Get-Process</span><span class="sxs-lookup"><span data-stu-id="be759-161">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="be759-162">Start-Process</span><span class="sxs-lookup"><span data-stu-id="be759-162">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="be759-163">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="be759-163">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="be759-164">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="be759-164">Wait-Process</span></span>](Wait-Process.md)

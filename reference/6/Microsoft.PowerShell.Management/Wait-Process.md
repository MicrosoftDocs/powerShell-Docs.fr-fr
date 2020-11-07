---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 88eec3461a267a03bfe3a91735ece7269aa601c2
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345032"
---
# <span data-ttu-id="01afd-103">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-103">Wait-Process</span></span>

## <span data-ttu-id="01afd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="01afd-104">SYNOPSIS</span></span>
<span data-ttu-id="01afd-105">Attend l'arrêt des processus avant d'accepter une autre entrée.</span><span class="sxs-lookup"><span data-stu-id="01afd-105">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="01afd-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="01afd-106">SYNTAX</span></span>

### <span data-ttu-id="01afd-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="01afd-107">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="01afd-108">Id</span><span class="sxs-lookup"><span data-stu-id="01afd-108">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="01afd-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="01afd-109">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="01afd-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01afd-110">DESCRIPTION</span></span>

<span data-ttu-id="01afd-111">L' `Wait-Process` applet de commande attend l’arrêt d’un ou de plusieurs processus en cours d’exécution avant d’accepter l’entrée.</span><span class="sxs-lookup"><span data-stu-id="01afd-111">The `Wait-Process` cmdlet waits for one or more running processes to be stopped before accepting input.</span></span> <span data-ttu-id="01afd-112">Dans la console PowerShell, cette applet de commande supprime l’invite de commandes jusqu’à ce que les processus soient arrêtés.</span><span class="sxs-lookup"><span data-stu-id="01afd-112">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span> <span data-ttu-id="01afd-113">Vous pouvez spécifier un processus par nom de processus ou ID de processus (PID), ou diriger un objet processus vers `Wait-Process` .</span><span class="sxs-lookup"><span data-stu-id="01afd-113">You can specify a process by process name or process ID (PID), or pipe a process object to `Wait-Process`.</span></span>

<span data-ttu-id="01afd-114">`Wait-Process` fonctionne uniquement sur les processus qui s’exécutent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="01afd-114">`Wait-Process` works only on processes running on the local computer.</span></span>

## <span data-ttu-id="01afd-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="01afd-115">EXAMPLES</span></span>

### <span data-ttu-id="01afd-116">Exemple 1 : arrêter un processus et attendre</span><span class="sxs-lookup"><span data-stu-id="01afd-116">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="01afd-117">Cet exemple arrête le processus Notepad, puis attend que le processus soit arrêté avant de continuer avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="01afd-117">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="01afd-118">La première commande utilise l' `Get-Process` applet de commande pour récupérer l’ID du processus du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="01afd-118">The first command uses the `Get-Process` cmdlet to get the ID of the Notepad process.</span></span> <span data-ttu-id="01afd-119">Elle stocke l’ID dans la `$nid` variable.</span><span class="sxs-lookup"><span data-stu-id="01afd-119">It stores the ID in the `$nid` variable.</span></span>

<span data-ttu-id="01afd-120">La deuxième commande utilise l' `Stop-Process` applet de commande pour arrêter le processus avec l’ID stocké dans `$nid` .</span><span class="sxs-lookup"><span data-stu-id="01afd-120">The second command uses the `Stop-Process` cmdlet to stop the process with the ID stored in `$nid`.</span></span>

<span data-ttu-id="01afd-121">La troisième commande utilise `Wait-Process` pour attendre que le processus Notepad soit arrêté.</span><span class="sxs-lookup"><span data-stu-id="01afd-121">The third command uses `Wait-Process` to wait until the Notepad process is stopped.</span></span> <span data-ttu-id="01afd-122">Elle utilise le paramètre **ID** de `Wait-Process` pour identifier le processus.</span><span class="sxs-lookup"><span data-stu-id="01afd-122">It uses the **Id** parameter of `Wait-Process` to identify the process.</span></span>

### <span data-ttu-id="01afd-123">Exemple 2 : spécification d’un processus</span><span class="sxs-lookup"><span data-stu-id="01afd-123">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="01afd-124">Ces commandes affichent trois méthodes différentes pour spécifier un processus à `Wait-Process` .</span><span class="sxs-lookup"><span data-stu-id="01afd-124">These commands show three different methods of specifying a process to `Wait-Process`.</span></span> <span data-ttu-id="01afd-125">La première commande obtient le processus Notepad et le stocke dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="01afd-125">The first command gets the Notepad process and stores it in the `$p` variable.</span></span>

<span data-ttu-id="01afd-126">La deuxième commande utilise le paramètre **ID** , la troisième commande utilise le paramètre **Name** et la quatrième commande utilise le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="01afd-126">The second command uses the **Id** parameter, the third command uses the **Name** parameter, and the fourth command uses the **InputObject** parameter.</span></span>

<span data-ttu-id="01afd-127">Ces commandes produisent les mêmes résultats et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="01afd-127">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="01afd-128">Exemple 3 : attendre des processus pendant une période spécifiée</span><span class="sxs-lookup"><span data-stu-id="01afd-128">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="01afd-129">Cette commande attend l’arrêt des processus Outlook et Winword pendant 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="01afd-129">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span> <span data-ttu-id="01afd-130">Si les deux processus ne se sont pas arrêtés, l’applet de commande affiche une erreur sans fin d’exécution et l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="01afd-130">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="01afd-131">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="01afd-131">PARAMETERS</span></span>

### <span data-ttu-id="01afd-132">-Id</span><span class="sxs-lookup"><span data-stu-id="01afd-132">-Id</span></span>

<span data-ttu-id="01afd-133">Spécifie les identificateurs des processus.</span><span class="sxs-lookup"><span data-stu-id="01afd-133">Specifies the process IDs of the processes.</span></span> <span data-ttu-id="01afd-134">Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="01afd-134">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="01afd-135">Pour rechercher le PID d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="01afd-135">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="01afd-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="01afd-136">-InputObject</span></span>

<span data-ttu-id="01afd-137">Spécifie les processus en envoyant des objets processus.</span><span class="sxs-lookup"><span data-stu-id="01afd-137">Specifies the processes by submitting process objects.</span></span> <span data-ttu-id="01afd-138">Entrez une variable qui contient les objets processus, ou tapez une commande ou une expression qui obtient les objets processus, tels que l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="01afd-138">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="01afd-139">-Name</span><span class="sxs-lookup"><span data-stu-id="01afd-139">-Name</span></span>

<span data-ttu-id="01afd-140">Spécifie les noms des processus.</span><span class="sxs-lookup"><span data-stu-id="01afd-140">Specifies the process names of the processes.</span></span> <span data-ttu-id="01afd-141">Pour spécifier plusieurs noms, séparez-les à l’aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="01afd-141">To specify multiple names, use commas to separate the names.</span></span> <span data-ttu-id="01afd-142">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="01afd-142">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="01afd-143">-Timeout</span><span class="sxs-lookup"><span data-stu-id="01afd-143">-Timeout</span></span>

<span data-ttu-id="01afd-144">Spécifie la durée maximale, en secondes, pendant laquelle cette applet de commande attend que les processus spécifiés s’arrêtent.</span><span class="sxs-lookup"><span data-stu-id="01afd-144">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="01afd-145">Lorsque ce délai expire, la commande affiche une erreur sans fin d’exécution qui répertorie les processus dont l’exécution se poursuit et elle met un terme à l’attente.</span><span class="sxs-lookup"><span data-stu-id="01afd-145">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span> <span data-ttu-id="01afd-146">Par défaut, il n’y a aucun délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="01afd-146">By default, there is no time-out.</span></span>

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

### <span data-ttu-id="01afd-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01afd-147">CommonParameters</span></span>

<span data-ttu-id="01afd-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01afd-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01afd-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="01afd-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01afd-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="01afd-150">INPUTS</span></span>

### <span data-ttu-id="01afd-151">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="01afd-151">System.Diagnostics.Process</span></span>

<span data-ttu-id="01afd-152">Vous pouvez diriger un objet processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="01afd-152">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="01afd-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="01afd-153">OUTPUTS</span></span>

### <span data-ttu-id="01afd-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="01afd-154">None</span></span>

<span data-ttu-id="01afd-155">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="01afd-155">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="01afd-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="01afd-156">NOTES</span></span>

<span data-ttu-id="01afd-157">L’applet de commande est uniquement prise en charge sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="01afd-157">The cmdlet is only supported on Windows platforms.</span></span>

<span data-ttu-id="01afd-158">Cette applet de commande utilise la méthode **WaitForExit** de la classe **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="01afd-158">This cmdlet uses the **WaitForExit** method of the **System.Diagnostics.Process** class.</span></span>

## <span data-ttu-id="01afd-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="01afd-159">RELATED LINKS</span></span>

[<span data-ttu-id="01afd-160">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-160">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="01afd-161">Get-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-161">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="01afd-162">Start-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-162">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="01afd-163">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-163">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="01afd-164">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="01afd-164">Wait-Process</span></span>](Wait-Process.md)

---
title: Éléments à une ligne et pipeline
description: Un one-liner PowerShell est un pipeline continu, contenant plusieurs commandes, qui permet d’accomplir une tâche unique.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 1483ec6b76d17c3dd081356ecff85a929fc43e2c
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598549"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="e0a69-103">Chapitre 4 : One-liners et pipeline</span><span class="sxs-lookup"><span data-stu-id="e0a69-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="e0a69-104">À mes débuts avec PowerShell, quand je ne réussissais pas à accomplir une tâche avec un one-liner PowerShell, je repassais dans l’interface graphique utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0a69-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="e0a69-105">J’ai appris au fur et à mesure et maintenant, je sais développer des scripts, des fonctions et des modules.</span><span class="sxs-lookup"><span data-stu-id="e0a69-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="e0a69-106">Ne vous laissez pas décourager par certains exemples les plus avancés que vous pouvez voir sur Internet.</span><span class="sxs-lookup"><span data-stu-id="e0a69-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="e0a69-107">Nul ne naît expert de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="e0a69-108">Nous avons tous été débutants à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="e0a69-108">We were all beginners at one time.</span></span>

<span data-ttu-id="e0a69-109">Je voudrais donner un petit conseil à ceux d’entre vous qui utilisent toujours l’interface utilisateur graphique pour l’administration : installez les outils de gestion sur votre station de travail d’administration et gérez vos serveurs à distance.</span><span class="sxs-lookup"><span data-stu-id="e0a69-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="e0a69-110">De cette façon, cela n’aura pas d’importance si votre serveur exécute une installation GUI ou minimale du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e0a69-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="e0a69-111">Cela vous aidera à vous préparer à la gestion des serveurs à distance avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="e0a69-112">Comme dans les chapitres précédents, assurez-vous de suivre ce chapitre sur votre ordinateur dans un environnement lab Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e0a69-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="e0a69-113">One-liners</span><span class="sxs-lookup"><span data-stu-id="e0a69-113">One-Liners</span></span>

<span data-ttu-id="e0a69-114">Un pipeline One-doublure PowerShell est un pipeline continu et pas nécessairement une commande qui se trouve sur une seule ligne physique.</span><span class="sxs-lookup"><span data-stu-id="e0a69-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that's on one physical line.</span></span> <span data-ttu-id="e0a69-115">Les commandes sur une seule ligne physique ne sont pas toutes des one-liners.</span><span class="sxs-lookup"><span data-stu-id="e0a69-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="e0a69-116">Par exemple, bien que la commande ci-dessous soit sur plusieurs lignes physiques, c’est un one-liner PowerShell, car il s’agit d’un pipeline continu.</span><span class="sxs-lookup"><span data-stu-id="e0a69-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="e0a69-117">J’aurais pu l’écrire sur une seule ligne physique, mais j’ai choisi d’insérer un saut de ligne après le symbole de barre verticale.</span><span class="sxs-lookup"><span data-stu-id="e0a69-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="e0a69-118">Le symbole de barre verticale est l’un des caractères où un saut de ligne naturel est autorisé dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="e0a69-119">Des sauts de ligne naturels peuvent se produire avec des caractères fréquemment employés, comme les virgules (`,`), les crochets ouvrants (`[`), les accolades (`{`) et les parenthèses (`(`).</span><span class="sxs-lookup"><span data-stu-id="e0a69-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="e0a69-120">D’autres caractères moins courants sont le point-virgule (`;`), le signe égal (`=`), et les guillemets ouvrants simples et doubles (`'`, `"`).</span><span class="sxs-lookup"><span data-stu-id="e0a69-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="e0a69-121">L’utilisation de l’apostrophe inversée (`` ` ``) ou accent grave comme caractère de continuation de ligne est contestée.</span><span class="sxs-lookup"><span data-stu-id="e0a69-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="e0a69-122">Ma recommandation est d’éviter de l’utiliser autant que possible.</span><span class="sxs-lookup"><span data-stu-id="e0a69-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="e0a69-123">Je vois souvent des commandes PowerShell où il y a une apostrophe inversée juste après un caractère de saut de ligne naturel.</span><span class="sxs-lookup"><span data-stu-id="e0a69-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="e0a69-124">Cette apostrophe n’a aucune raison d’être là.</span><span class="sxs-lookup"><span data-stu-id="e0a69-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="e0a69-125">Les commandes présentées dans les deux exemples précédents fonctionnent correctement dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="e0a69-126">Cependant, si vous essayez de les exécuter dans le volet console de PowerShell ISE, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="e0a69-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="e0a69-127">La raison est que le volet console de PowerShell ISE n’attend pas que le reste de la commande soit entré sur la ligne suivante comme le fait la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="e0a69-128">Pour éviter ce problème dans le volet console de PowerShell ISE, appuyez sur les deux touches <kbd>Maj</kbd>+<kbd>Entrée</kbd> au lieu d’appuyer seulement sur <kbd>Entrée</kbd> quand une commande doit continuer sur une autre ligne.</span><span class="sxs-lookup"><span data-stu-id="e0a69-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="e0a69-129">L’exemple suivant n’est pas un one-liner PowerShell, car ce n’est pas un pipeline continu.</span><span class="sxs-lookup"><span data-stu-id="e0a69-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="e0a69-130">Il s’agit en fait de deux commandes distinctes sur une seule ligne, séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="e0a69-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="e0a69-131">Dans beaucoup de langages de programmation et de script, la présence d’un point-virgule à la fin de chaque ligne est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e0a69-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="e0a69-132">Cela est possible de faire la même chose dans PowerShell, mais cela n’est pas recommandé car non nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e0a69-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="e0a69-133">Filtrage à gauche</span><span class="sxs-lookup"><span data-stu-id="e0a69-133">Filtering Left</span></span>

<span data-ttu-id="e0a69-134">Les résultats des commandes présentées dans ce chapitre ont été filtrés afin que seule une partie soit affichée.</span><span class="sxs-lookup"><span data-stu-id="e0a69-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="e0a69-135">Par exemple, `Get-Service` a été utilisé avec le paramètre **Name** pour filtrer la liste des services et retourner uniquement les données du service de temps Windows.</span><span class="sxs-lookup"><span data-stu-id="e0a69-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="e0a69-136">Filtrez toujours les résultats le plus tôt possible dans le pipeline pour les limiter aux données qui vous intéressent vraiment.</span><span class="sxs-lookup"><span data-stu-id="e0a69-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="e0a69-137">Cela se fait en utilisant les paramètres dans la première commande ou celle à l’extrême gauche.</span><span class="sxs-lookup"><span data-stu-id="e0a69-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="e0a69-138">Cette méthode est parfois appelée _filtrage à gauche_.</span><span class="sxs-lookup"><span data-stu-id="e0a69-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="e0a69-139">L’exemple suivant utilise le paramètre **Name** de `Get-Service` pour filtrer immédiatement les résultats sur le service de temps Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="e0a69-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="e0a69-140">Il n’est pas rare de voir des exemples où la commande est redirigée vers `Where-Object` pour effectuer le filtrage.</span><span class="sxs-lookup"><span data-stu-id="e0a69-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="e0a69-141">Le premier exemple filtre à la source et retourne uniquement les résultats pour le service de temps Windows.</span><span class="sxs-lookup"><span data-stu-id="e0a69-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="e0a69-142">Le deuxième exemple retourne tous les services, puis il les redirige vers une autre commande qui effectuera le filtrage.</span><span class="sxs-lookup"><span data-stu-id="e0a69-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="e0a69-143">Ce n’est pas un problème dans cet exemple, mais imaginez si vous faisiez une requête sur une liste d’utilisateurs Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e0a69-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="e0a69-144">Voudriez-vous vraiment retourner les informations de plusieurs milliers de comptes d’utilisateur à partir d’Active Directory dans le seul but de les rediriger vers une autre commande qui les filtrera pour en retourner seulement une petite partie ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="e0a69-145">Ma recommandation est de toujours filtrer à gauche, même si cela ne semble pas utile.</span><span class="sxs-lookup"><span data-stu-id="e0a69-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="e0a69-146">En adoptant cette pratique, vous filtrerez automatiquement à gauche sans même y penser quand cela sera vraiment nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e0a69-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="e0a69-147">Un jour, quelqu’un m’avait dit que l’ordre de spécification des commandes n’avait pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="e0a69-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="e0a69-148">Rien n’était plus faux.</span><span class="sxs-lookup"><span data-stu-id="e0a69-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="e0a69-149">L’ordre dans lequel les commandes sont spécifiées est bien sûr important pour le filtrage.</span><span class="sxs-lookup"><span data-stu-id="e0a69-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="e0a69-150">Imaginons le scénario dans lequel vous utilisez `Select-Object` pour sélectionner uniquement quelques propriétés et `Where-Object` pour filtrer sur des propriétés qui ne seront pas dans la sélection.</span><span class="sxs-lookup"><span data-stu-id="e0a69-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="e0a69-151">Dans ce scénario, le filtrage doit être la première opération ; sinon, la propriété n’existera pas dans le pipeline au moment où vous tenterez d’effectuer le filtrage.</span><span class="sxs-lookup"><span data-stu-id="e0a69-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="e0a69-152">La commande dans l’exemple précédent ne retourne aucun résultat, car la propriété **CanStopAndContinue** n’existe pas quand les résultats de `Select-Object` sont redirigés vers `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="e0a69-153">Cette propriété particulière n’a pas été « sélectionnée ».</span><span class="sxs-lookup"><span data-stu-id="e0a69-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="e0a69-154">En fait, elle a été filtrée. Il suffit d’inverser l’ordre de `Select-Object` et `Where-Object` pour obtenir les résultats souhaités.</span><span class="sxs-lookup"><span data-stu-id="e0a69-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="e0a69-155">Pipeline</span><span class="sxs-lookup"><span data-stu-id="e0a69-155">The Pipeline</span></span>

<span data-ttu-id="e0a69-156">Comme vous l’avez vu dans la plupart des exemples de ce livre étudiés jusqu’ici, la sortie d’une commande peut souvent être utilisée comme entrée d’une autre commande.</span><span class="sxs-lookup"><span data-stu-id="e0a69-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="e0a69-157">Dans le chapitre 3, `Get-Member` a été utilisé pour déterminer le type d’objet qu’une commande génère.</span><span class="sxs-lookup"><span data-stu-id="e0a69-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="e0a69-158">Le chapitre 3 a également montré comment utiliser le paramètre **ParameterType** de `Get-Command` pour déterminer quelles commandes acceptaient ce type d’entrée, mais pas forcément en entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="e0a69-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="e0a69-159">Si l’aide sur les commandes fournit des informations détaillées, elle peut inclure une section **INPUTS** et une section **OUTPUTS**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="e0a69-160">Seule la section pertinente de l’aide est affichée dans les résultats précédents.</span><span class="sxs-lookup"><span data-stu-id="e0a69-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="e0a69-161">Comme vous pouvez le voir, la section **INPUTS** indique qu’un objet **ServiceController** ou **String** peut être redirigé vers l’applet de commande `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="e0a69-162">Elle ne précise pas quels paramètres acceptent ce type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e0a69-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="e0a69-163">L’une des méthodes les plus simples pour avoir cette information est d’examiner les différents paramètres dans la version complète (Full) de l’aide sur l’applet de commande `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="e0a69-164">Là encore, seule la partie pertinente de l’aide est affichée dans le jeu de résultats précédent.</span><span class="sxs-lookup"><span data-stu-id="e0a69-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="e0a69-165">Notez que le paramètre **DisplayName** n’accepte pas l’entrée de pipeline, que le paramètre **InputObject** accepte l’entrée de pipeline **par valeur** (ByValue) pour les objets **ServiceController**, et que le paramètre **Name** accepte l’entrée de pipeline **par valeur** pour les objets **String**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="e0a69-166">Il accepte également l’entrée de pipeline **par nom de propriété** (ByPropertyName).</span><span class="sxs-lookup"><span data-stu-id="e0a69-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="e0a69-167">Quand un paramètre accepte l’entrée de pipeline à la fois par nom de propriété et par valeur, il tente toujours l’entrée **par valeur** en premier.</span><span class="sxs-lookup"><span data-stu-id="e0a69-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="e0a69-168">Si l’entrée **par valeur** échoue, il tente l’entrée **par nom de propriété**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="e0a69-169">Le terme **par valeur** est un peu trompeur.</span><span class="sxs-lookup"><span data-stu-id="e0a69-169">**By value** is a little misleading.</span></span> <span data-ttu-id="e0a69-170">Je préfère l’appeler **par type**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="e0a69-171">Cela signifie que si vous redirigez les résultats d’une commande qui génère un type d’objet **ServiceController** vers `Stop-Service`, elle lie cette entrée au paramètre **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="e0a69-172">Mais si vous redirigez les résultats d’une commande qui produit une sortie **String** vers `Stop-Service`, elle la lie au paramètre **Name**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="e0a69-173">Si vous redirigez les résultats d’une commande qui ne produit pas un objet **ServiceController** ou **String** vers `Stop-Service`, mais qui génère une sortie contenant une propriété appelée **Name**, elle lie la propriété **Name** de la sortie au paramètre **Name** de `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="e0a69-174">Déterminez le type de sortie que la commande `Get-Service` génère.</span><span class="sxs-lookup"><span data-stu-id="e0a69-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="e0a69-175">`Get-Service` produit un type d’objet ServiceController.</span><span class="sxs-lookup"><span data-stu-id="e0a69-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="e0a69-176">Comme vous l’avez vu précédemment dans l’aide, le paramètre **InputObject** de `Stop-Service` accepte les objets **ServiceController** via le pipeline **par valeur** (par type).</span><span class="sxs-lookup"><span data-stu-id="e0a69-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="e0a69-177">Cela signifie que lorsque les résultats de l’applet de commande `Get-Service` sont redirigés vers `Stop-Service`, ils sont liés au paramètre **InputObject** de `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="e0a69-178">Essayons à présent avec une entrée de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0a69-178">Now to try string input.</span></span> <span data-ttu-id="e0a69-179">Redirigez `w32time` vers `Get-Member` simplement pour vérifier qu’il s’agit d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0a69-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="e0a69-180">Comme nous l’avons vu précédemment dans l’aide, le fait de rediriger une chaîne vers `Stop-Service` la lie **par valeur** au paramètre **Name** de `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="e0a69-181">Testez-le en redirigeant `w32time` vers `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="e0a69-182">Notez que dans l’exemple précédent, j’ai mis des guillemets simples autour de la chaîne `w32time`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="e0a69-183">Dans PowerShell, vous devez toujours utiliser des guillemets simples au lieu de guillemets doubles, sauf si la chaîne entre guillemets contient une variable qui doit être développée à sa valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="e0a69-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="e0a69-184">Comme PowerShell n’a pas besoin d’analyser le contenu figurant entre des guillemets simples, votre code s’exécute un peu plus vite.</span><span class="sxs-lookup"><span data-stu-id="e0a69-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="e0a69-185">Créez un objet personnalisé pour tester l’entrée de pipeline par nom de propriété pour le paramètre **Name** de `Stop-Service`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

<span data-ttu-id="e0a69-186">Le contenu de la variable **CustomObject** est un type d’objet **PSCustomObject** et inclut une propriété appelée **Name**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="e0a69-187">Si vous placez la variable `$CustomObject` entre guillemets, vous devez utiliser des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="e0a69-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="e0a69-188">Si vous utilisez des guillemets simples, la chaîne littérale `$CustomObject` sera redirigée vers `Get-Member` à la place de la valeur contenue dans la variable.</span><span class="sxs-lookup"><span data-stu-id="e0a69-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="e0a69-189">Rediriger le contenu de `$CustomObject` vers l’applet de commande `Stop-Service` le lie au paramètre **Name**, mais cette fois, il est lié **par nom de propriété** et pas **par valeur**, car le contenu de `$CustomObject` est un objet qui a une propriété appelée **Name**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="e0a69-190">Dans cet exemple, je crée un autre objet personnalisé avec un nom de propriété différent, par exemple **Service**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="e0a69-191">Une erreur est générée quand je tente de rediriger `$CustomObject` vers `Stop-Service`, car la commande ne produit pas d’objet **ServiceController** ou **String**, et ne comporte pas de propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="e0a69-192">Si la sortie d’une commande n’est pas alignée avec les options d’entrée de pipeline définies pour une autre commande, `Select-Object` peut être utilisé pour renommer la propriété afin de faire correspondre les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e0a69-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="e0a69-193">Dans cet exemple, `Select-Object` a été utilisé pour renommer la propriété **Service** en une propriété appelée **Name**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="e0a69-194">La syntaxe de cet exemple peut paraître un peu compliquée de prime abord.</span><span class="sxs-lookup"><span data-stu-id="e0a69-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="e0a69-195">Par expérience, je sais qu’on n’apprend pas la syntaxe simplement en copiant et en collant du code.</span><span class="sxs-lookup"><span data-stu-id="e0a69-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="e0a69-196">Prenez le temps de taper vous-même le code.</span><span class="sxs-lookup"><span data-stu-id="e0a69-196">Take the time to type the code in.</span></span> <span data-ttu-id="e0a69-197">Après quelques temps, vous le ferez automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e0a69-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="e0a69-198">Travailler avec plusieurs moniteurs est très confortable, car vous pouvez afficher l’exemple de code sur un écran et taper votre code dans un autre.</span><span class="sxs-lookup"><span data-stu-id="e0a69-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="e0a69-199">Vous voudrez peut-être parfois utiliser un paramètre qui n’accepte pas d’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="e0a69-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="e0a69-200">L’exemple suivant illustre l’utilisation de la sortie d’une commande comme entrée d’une autre commande.</span><span class="sxs-lookup"><span data-stu-id="e0a69-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="e0a69-201">Commencez par enregistrer le nom complet de deux services Windows dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e0a69-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="e0a69-202">Vous pouvez exécuter la commande qui fournit la sortie nécessaire entre parenthèses comme valeur du paramètre de la commande qui doit utiliser l’entrée.</span><span class="sxs-lookup"><span data-stu-id="e0a69-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="e0a69-203">Pour ceux d’entre vous qui s’en souviennent, sachez que cela est similaire à l’ordre des opérations en algèbre.</span><span class="sxs-lookup"><span data-stu-id="e0a69-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="e0a69-204">La commande entre parenthèses est toujours exécutée avant la partie externe de la commande.</span><span class="sxs-lookup"><span data-stu-id="e0a69-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="e0a69-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e0a69-205">PowerShellGet</span></span>

<span data-ttu-id="e0a69-206">PowerShellGet est un module de PowerShell qui contient des commandes pour détecter, installer, publier et mettre à jour des modules PowerShell (et d’autres artefacts) vers ou à partir d’un dépôt NuGet.</span><span class="sxs-lookup"><span data-stu-id="e0a69-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="e0a69-207">PowerShellGet est fourni avec PowerShell version 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e0a69-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="e0a69-208">Il est disponible en téléchargement pour PowerShell version 3.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e0a69-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="e0a69-209">Microsoft héberge un dépôt NuGet en ligne appelé [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="e0a69-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="e0a69-210">Bien que ce dépôt soit hébergé par Microsoft, la majorité des modules contenus dans le dépôt ne sont pas développés par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0a69-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="e0a69-211">Tout code provenant du dépôt PowerShell Gallery doit être examiné minutieusement dans un environnement de test isolé avant d’être considéré comme approprié pour une utilisation dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="e0a69-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="e0a69-212">La plupart des entreprises préfèrent héberger leur propre dépôt NuGet privé interne et l’utiliser pour publier leurs modules à usage interne uniquement, ainsi que les modules qu’ils ont téléchargés à partir d’autres sources une fois qu’ils ont été validés comme non malveillants.</span><span class="sxs-lookup"><span data-stu-id="e0a69-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="e0a69-213">Utilisez l’applet de commande `Find-Module` intégrée au module PowerShellGet pour rechercher dans le dépôt PowerShell Gallery un module que j’ai écrit et nommé MrToolkit.</span><span class="sxs-lookup"><span data-stu-id="e0a69-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="e0a69-214">La première fois que vous utilisez l’une des commandes du module PowerShellGet, vous êtes invité à installer le fournisseur NuGet.</span><span class="sxs-lookup"><span data-stu-id="e0a69-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="e0a69-215">Pour installer le module MrToolkit, redirigez la commande précédente vers `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="e0a69-216">Étant donné que PowerShell Gallery est un dépôt non approuvé, vous êtes invité à approuver l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="e0a69-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="e0a69-217">Recherche d’une entrée de pipeline de manière simple</span><span class="sxs-lookup"><span data-stu-id="e0a69-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="e0a69-218">Le module MrToolkit contient une fonction nommée `Get-MrPipelineInput`.</span><span class="sxs-lookup"><span data-stu-id="e0a69-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="e0a69-219">Cette applet de commande peut être utilisée pour déterminer facilement quels paramètres d’une commande acceptent l’entrée de pipeline, quel type d’objet ils acceptent et s’ils acceptent l’entrée de pipeline **par valeur** ou **par nom de propriété**.</span><span class="sxs-lookup"><span data-stu-id="e0a69-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="e0a69-220">Comme vous le voyez, cette fonction vous permet d’obtenir facilement les mêmes informations que celles que nous avons précédemment recherchées dans l’aide.</span><span class="sxs-lookup"><span data-stu-id="e0a69-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="e0a69-221">Résumé</span><span class="sxs-lookup"><span data-stu-id="e0a69-221">Summary</span></span>

<span data-ttu-id="e0a69-222">Dans ce chapitre, vous avez découvert ce que sont les one-liners PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="e0a69-223">Vous avez appris que le nombre de lignes physiques sur lesquelles une commande est spécifiée n’a rien à voir avec le fait qu’il s’agit ou non d’un one-liner PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a69-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="e0a69-224">Vous avez également appris en quoi consistent le filtrage à gauche, le pipeline et PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="e0a69-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="e0a69-225">Révision</span><span class="sxs-lookup"><span data-stu-id="e0a69-225">Review</span></span>

1. <span data-ttu-id="e0a69-226">Qu’est-ce qu’un one-liner PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="e0a69-227">Quels sont les caractères où des sauts de ligne naturels peuvent se produire dans PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="e0a69-228">Pourquoi faut-il filtrer à gauche ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-228">Why should you filter left?</span></span>
1. <span data-ttu-id="e0a69-229">Quelles sont les deux façons dont une commande PowerShell peut accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="e0a69-230">Pourquoi ne devez-vous pas faire confiance aux commandes trouvées dans le dépôt PowerShell Gallery ?</span><span class="sxs-lookup"><span data-stu-id="e0a69-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="e0a69-231">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="e0a69-231">Recommended Reading</span></span>

- <span data-ttu-id="e0a69-232">[about_Pipelines][]</span><span class="sxs-lookup"><span data-stu-id="e0a69-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="e0a69-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="e0a69-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="e0a69-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="e0a69-234">[about_Parameters][]</span></span>
- <span data-ttu-id="e0a69-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span><span class="sxs-lookup"><span data-stu-id="e0a69-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/

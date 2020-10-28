---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des services
description: PowerShell fournit plusieurs applets de commande qui permettent de gérer les services sur des ordinateurs locaux et distants.
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500349"
---
# <a name="managing-services"></a><span data-ttu-id="2dd9b-104">Gestion des services</span><span class="sxs-lookup"><span data-stu-id="2dd9b-104">Managing Services</span></span>

<span data-ttu-id="2dd9b-105">Il existe huit principales applets de commande Service, conçues pour un vaste éventail de tâches de service.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-105">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="2dd9b-106">Nous allons uniquement examiner la liste et le changement de l’état en cours d’exécution des services. Toutefois, vous pouvez obtenir une liste d’applets de commande Service à l’aide de `Get-Help \*-Service`. Vous pouvez également trouver des informations sur chaque applet de commande Service à l’aide de`Get-Help <Cmdlet-Name>`, par exemple `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-106">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="2dd9b-107">Obtention de services</span><span class="sxs-lookup"><span data-stu-id="2dd9b-107">Getting Services</span></span>

<span data-ttu-id="2dd9b-108">Vous pouvez obtenir les services sur un ordinateur local ou distant à l’aide de l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-108">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="2dd9b-109">Comme avec `Get-Process`, l’utilisation de la commande `Get-Service` sans paramètres retourne tous les services.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-109">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="2dd9b-110">Vous pouvez filtrer par nom, même en utilisant un astérisque comme caractère générique :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-110">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="2dd9b-111">Comme il n’est pas toujours évident d’identifier le nom réel d’un service, il se peut que vous deviez rechercher des services par nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-111">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="2dd9b-112">À cette fin, vous pouvez utiliser un nom spécifique, des caractères génériques ou une liste de noms d’affichage :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-112">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="2dd9b-113">Vous pouvez utiliser le paramètre ComputerName de l’applet de commande Get-Service pour obtenir les services sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-113">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="2dd9b-114">Le paramètre ComputerName acceptant plusieurs valeurs et caractères génériques, vous pouvez obtenir les services sur plusieurs ordinateurs à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-114">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="2dd9b-115">Par exemple, la commande suivante obtient les services sur l’ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-115">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="2dd9b-116">Obtention de services requis et dépendants</span><span class="sxs-lookup"><span data-stu-id="2dd9b-116">Getting Required and Dependent Services</span></span>

<span data-ttu-id="2dd9b-117">L’applet de commande Get-Service dispose de deux paramètres très utiles dans l’administration des services.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-117">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="2dd9b-118">Le paramètre DependentServices obtient les services dépendant de ce service.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-118">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="2dd9b-119">Le paramètre RequiredServices obtient les services dont ce service dépend.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-119">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="2dd9b-120">Ces paramètres affichent simplement les valeurs des propriétés DependentServices et ServicesDependedOn (alias=RequiredServices) de l’objet System.ServiceProcess.ServiceController que l’applet de commande Get-Service retourne, mais ils simplifient les commandes et facilitent sensiblement l’obtention de ces informations.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-120">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="2dd9b-121">La commande suivante obtient les services que le service LanmanWorkstation requiert.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-121">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="2dd9b-122">La commande suivante obtient les services qui requièrent le service LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-122">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="2dd9b-123">Vous pouvez même obtenir tous les services qui ont des dépendances.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-123">You can even get all services that have dependencies.</span></span> <span data-ttu-id="2dd9b-124">C’est précisément ce que fait la commande suivante. Ensuite, elle utilise l’applet de commande Format-Table pour afficher les propriétés State, Name, RequiredServices et DependentServices des services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-124">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="2dd9b-125">Arrêt, démarrage, interruption et redémarrage de services</span><span class="sxs-lookup"><span data-stu-id="2dd9b-125">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="2dd9b-126">Les applets de commande Service ont toutes la même forme générale.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-126">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="2dd9b-127">Les services peuvent être spécifiés par un nom commun ou nom d’affichage, et prennent des listes et des caractères génériques pour valeurs.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-127">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="2dd9b-128">Pour arrêter le spouleur d’impression, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-128">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="2dd9b-129">Pour démarrer le spouleur d’impression suite à un arrêt, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-129">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="2dd9b-130">Pour interrompre le spouleur d’impression, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-130">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="2dd9b-131">L’applet de commande `Restart-Service` fonctionne de la même manière que les autres applets de commande Service. Toutefois, nous allons présenter quelques exemples plus complexes.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-131">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="2dd9b-132">Dans le cas d’utilisation le plus simple, vous spécifiez le nom du service :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-132">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="2dd9b-133">Vous pouvez remarquer que vous obtenez un message d’avertissement répété sur le démarrage du spouleur d’impression.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-133">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="2dd9b-134">Lorsque vous effectuez une opération de service qui prend un certain temps, Windows PowerShell vous informe qu’il tente toujours d’effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-134">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="2dd9b-135">Si vous souhaitez redémarrer plusieurs services, vous pouvez obtenir la liste des services, filtrer ceux-ci, puis effectuer le redémarrage :</span><span class="sxs-lookup"><span data-stu-id="2dd9b-135">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="2dd9b-136">Ces applets de commande Service ne dispose pas de paramètre ComputerName, mais vous pouvez les exécuter sur un ordinateur distant à l’aide de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-136">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="2dd9b-137">Par exemple, la commande suivante redémarre le service Spouleur sur l’ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-137">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="2dd9b-138">Définition des propriétés d’un service</span><span class="sxs-lookup"><span data-stu-id="2dd9b-138">Setting Service Properties</span></span>

<span data-ttu-id="2dd9b-139">L’applet de commande `Set-Service` change les propriétés d’un service sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-139">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="2dd9b-140">Étant donné que l’état d’un service est une propriété, vous pouvez utiliser cette applet de commande pour démarrer, arrêter et suspendre un service.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-140">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="2dd9b-141">L’applet de commande Set-Service dispose également d’un paramètre StartupType qui permet de modifier le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-141">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="2dd9b-142">Pour utiliser `Set-Service` sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2dd9b-142">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="2dd9b-143">Pour plus d’informations, consultez [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span><span class="sxs-lookup"><span data-stu-id="2dd9b-143">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="2dd9b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dd9b-144">See Also</span></span>

- [<span data-ttu-id="2dd9b-145">Get-Service</span><span class="sxs-lookup"><span data-stu-id="2dd9b-145">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="2dd9b-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="2dd9b-146">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="2dd9b-147">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="2dd9b-147">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="2dd9b-148">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="2dd9b-148">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)

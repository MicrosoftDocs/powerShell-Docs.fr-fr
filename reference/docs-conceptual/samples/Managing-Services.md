---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des services
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086185"
---
# <a name="managing-services"></a><span data-ttu-id="01b57-103">Gestion des services</span><span class="sxs-lookup"><span data-stu-id="01b57-103">Managing Services</span></span>

<span data-ttu-id="01b57-104">Il existe huit principales applets de commande Service, conçues pour un vaste éventail de tâches de service.</span><span class="sxs-lookup"><span data-stu-id="01b57-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="01b57-105">Nous allons uniquement examiner la liste et le changement de l’état en cours d’exécution des services. Toutefois, vous pouvez obtenir une liste d’applets de commande Service à l’aide de `Get-Help \*-Service`. Vous pouvez également trouver des informations sur chaque applet de commande Service à l’aide de`Get-Help <Cmdlet-Name>`, par exemple `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="01b57-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="01b57-106">Obtention de services</span><span class="sxs-lookup"><span data-stu-id="01b57-106">Getting Services</span></span>

<span data-ttu-id="01b57-107">Vous pouvez obtenir les services sur un ordinateur local ou distant à l’aide de l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="01b57-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="01b57-108">Comme avec `Get-Process`, l’utilisation de la commande `Get-Service` sans paramètres retourne tous les services.</span><span class="sxs-lookup"><span data-stu-id="01b57-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="01b57-109">Vous pouvez filtrer par nom, même en utilisant un astérisque comme caractère générique :</span><span class="sxs-lookup"><span data-stu-id="01b57-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="01b57-110">Comme il n’est pas toujours évident d’identifier le nom réel d’un service, il se peut que vous deviez rechercher des services par nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="01b57-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="01b57-111">À cette fin, vous pouvez utiliser un nom spécifique, des caractères génériques ou une liste de noms d’affichage :</span><span class="sxs-lookup"><span data-stu-id="01b57-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="01b57-112">Vous pouvez utiliser le paramètre ComputerName de l’applet de commande Get-Service pour obtenir les services sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="01b57-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="01b57-113">Le paramètre ComputerName acceptant plusieurs valeurs et caractères génériques, vous pouvez obtenir les services sur plusieurs ordinateurs à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="01b57-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="01b57-114">Par exemple, la commande suivante obtient les services sur l’ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="01b57-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="01b57-115">Obtention de services requis et dépendants</span><span class="sxs-lookup"><span data-stu-id="01b57-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="01b57-116">L’applet de commande Get-Service dispose de deux paramètres très utiles dans l’administration des services.</span><span class="sxs-lookup"><span data-stu-id="01b57-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="01b57-117">Le paramètre DependentServices obtient les services dépendant de ce service.</span><span class="sxs-lookup"><span data-stu-id="01b57-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="01b57-118">Le paramètre RequiredServices obtient les services dont ce service dépend.</span><span class="sxs-lookup"><span data-stu-id="01b57-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="01b57-119">Ces paramètres affichent simplement les valeurs des propriétés DependentServices et ServicesDependedOn (alias=RequiredServices) de l’objet System.ServiceProcess.ServiceController que l’applet de commande Get-Service retourne, mais ils simplifient les commandes et facilitent sensiblement l’obtention de ces informations.</span><span class="sxs-lookup"><span data-stu-id="01b57-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="01b57-120">La commande suivante obtient les services que le service LanmanWorkstation requiert.</span><span class="sxs-lookup"><span data-stu-id="01b57-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="01b57-121">La commande suivante obtient les services qui requièrent le service LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="01b57-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="01b57-122">Vous pouvez même obtenir tous les services qui ont des dépendances.</span><span class="sxs-lookup"><span data-stu-id="01b57-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="01b57-123">C’est précisément ce que fait la commande suivante. Ensuite, elle utilise l’applet de commande Format-Table pour afficher les propriétés State, Name, RequiredServices et DependentServices des services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01b57-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="01b57-124">Arrêt, démarrage, interruption et redémarrage de services</span><span class="sxs-lookup"><span data-stu-id="01b57-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="01b57-125">Les applets de commande Service ont toutes la même forme générale.</span><span class="sxs-lookup"><span data-stu-id="01b57-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="01b57-126">Les services peuvent être spécifiés par un nom commun ou nom d’affichage, et prennent des listes et des caractères génériques pour valeurs.</span><span class="sxs-lookup"><span data-stu-id="01b57-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="01b57-127">Pour arrêter le spouleur d’impression, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="01b57-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="01b57-128">Pour démarrer le spouleur d’impression suite à un arrêt, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="01b57-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="01b57-129">Pour interrompre le spouleur d’impression, utilisez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="01b57-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="01b57-130">L’applet de commande `Restart-Service` fonctionne de la même manière que les autres applets de commande Service. Toutefois, nous allons présenter quelques exemples plus complexes.</span><span class="sxs-lookup"><span data-stu-id="01b57-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="01b57-131">Dans le cas d’utilisation le plus simple, vous spécifiez le nom du service :</span><span class="sxs-lookup"><span data-stu-id="01b57-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="01b57-132">Vous pouvez remarquer que vous obtenez un message d’avertissement répété sur le démarrage du spouleur d’impression.</span><span class="sxs-lookup"><span data-stu-id="01b57-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="01b57-133">Lorsque vous effectuez une opération de service qui prend un certain temps, Windows PowerShell vous informe qu’il tente toujours d’effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="01b57-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="01b57-134">Si vous souhaitez redémarrer plusieurs services, vous pouvez obtenir la liste des services, filtrer ceux-ci, puis effectuer le redémarrage :</span><span class="sxs-lookup"><span data-stu-id="01b57-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="01b57-135">Ces applets de commande Service ne dispose pas de paramètre ComputerName, mais vous pouvez les exécuter sur un ordinateur distant à l’aide de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="01b57-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="01b57-136">Par exemple, la commande suivante redémarre le service Spouleur sur l’ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="01b57-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="01b57-137">Définition des propriétés d’un service</span><span class="sxs-lookup"><span data-stu-id="01b57-137">Setting Service Properties</span></span>

<span data-ttu-id="01b57-138">L’applet de commande `Set-Service` change les propriétés d’un service sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="01b57-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="01b57-139">Étant donné que l’état d’un service est une propriété, vous pouvez utiliser cette applet de commande pour démarrer, arrêter et suspendre un service.</span><span class="sxs-lookup"><span data-stu-id="01b57-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="01b57-140">L’applet de commande Set-Service dispose également d’un paramètre StartupType qui permet de modifier le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="01b57-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="01b57-141">Pour utiliser `Set-Service` sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="01b57-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="01b57-142">Pour plus d’informations, voir [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="01b57-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="01b57-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01b57-143">See Also</span></span>

- <span data-ttu-id="01b57-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="01b57-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="01b57-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="01b57-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="01b57-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="01b57-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="01b57-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="01b57-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>
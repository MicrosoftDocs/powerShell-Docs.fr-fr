---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Obtention d’objets WMI Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401179"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="81166-103">Obtention d’objets WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="81166-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="81166-104">Obtention d’objets WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="81166-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="81166-105">WMI (Windows Management Instrumentation) est une technologie majeure pour l’administration du système Windows, car elle expose un vaste éventail d’informations de manière uniforme.</span><span class="sxs-lookup"><span data-stu-id="81166-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="81166-106">Compte tenu de tout ce que WMI permet de réaliser, l’applet de commande Windows PowerShell pour l’accès aux objets WMI, **Get-WmiObject**, est l’une des plus utiles pour travailler réellement.</span><span class="sxs-lookup"><span data-stu-id="81166-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="81166-107">Nous allons aborder l’utilisation de l’applet de commande Get-WmiObject pour accéder aux objets WMI, puis expliquer comment utiliser des objets WMI pour réaliser des opérations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="81166-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="81166-108">Affichage de la liste des classes WMI</span><span class="sxs-lookup"><span data-stu-id="81166-108">Listing WMI Classes</span></span>

<span data-ttu-id="81166-109">Le premier problème que rencontrent la plupart des utilisateurs de WMI est de comprendre ce que WMI permet de faire.</span><span class="sxs-lookup"><span data-stu-id="81166-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="81166-110">Les classes WMI décrivent les ressources qui peuvent être gérées.</span><span class="sxs-lookup"><span data-stu-id="81166-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="81166-111">Il existe des centaines de classes WMI, dont certaines contiennent des dizaines de propriétés.</span><span class="sxs-lookup"><span data-stu-id="81166-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="81166-112">L’applet de commande **Get-WmiObject** résout ce problème en rendant WMI détectable.</span><span class="sxs-lookup"><span data-stu-id="81166-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="81166-113">Vous pouvez obtenir la liste des classes WMI disponibles sur l’ordinateur local en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="81166-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="81166-114">Vous pouvez récupérer les mêmes informations à partir d’un ordinateur distant à l’aide du paramètre ComputerName, en spécifiant une adresse IP ou un nom d’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="81166-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="81166-115">La liste de classes retournée par des ordinateurs distants peut varier selon le système d’exploitation que l’ordinateur exécute et les extensions WMI ajoutées par les applications installées.</span><span class="sxs-lookup"><span data-stu-id="81166-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="81166-116">Lorsque vous utilisez l’applet de commande Get-WmiObject pour vous connecter à un ordinateur distant, celui-ci doit exécuter WMI et, dans la configuration par défaut, le compte que vous utilisez doit figurer dans le groupe Administrateurs local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="81166-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="81166-117">Windows PowerShell ne doit pas nécessairement être installé sur le système distant.</span><span class="sxs-lookup"><span data-stu-id="81166-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="81166-118">Cela permet d’administrer des systèmes d’exploitation qui n’exécutent pas Windows PowerShell, mais disposent de WMI.</span><span class="sxs-lookup"><span data-stu-id="81166-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="81166-119">Lors de la connexion au système local, vous pouvez même inclure le nom d’ordinateur à l’aide du paramètre ComputerName.</span><span class="sxs-lookup"><span data-stu-id="81166-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="81166-120">Vous pouvez utiliser le nom de l’ordinateur local, son adresse IP (ou l’adresse de bouclage 127.0.0.1), ou le style de WMI « . » comme nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="81166-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="81166-121">Si vous exécutez Windows PowerShell sur un ordinateur nommé Admin01 dont l’adresse IP est 192.168.1.90, les commandes suivantes retournent toutes la classe WMI pour cet ordinateur :</span><span class="sxs-lookup"><span data-stu-id="81166-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="81166-122">Par défaut, l’applet de commande Get-WmiObject utilise l’espace de noms root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="81166-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="81166-123">Si vous souhaitez spécifier un autre espace de noms WMI, utilisez le paramètre **Namespace** en spécifiant le chemin d’accès à l’espace de noms correspondant :</span><span class="sxs-lookup"><span data-stu-id="81166-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="81166-124">Affichage des détails de classe WMI</span><span class="sxs-lookup"><span data-stu-id="81166-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="81166-125">Si vous connaissez déjà le nom d’une classe WMI, vous pouvez l’utiliser pour obtenir des informations immédiatement.</span><span class="sxs-lookup"><span data-stu-id="81166-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="81166-126">Par exemple, une des classes WMI couramment utilisées pour récupérer des informations sur un ordinateur est **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="81166-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="81166-127">Bien que nous montrions tous les paramètres, la commande peut être exprimée de façon plus concise.</span><span class="sxs-lookup"><span data-stu-id="81166-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="81166-128">Le paramètre **ComputerName** n’est pas nécessaire lors de la connexion au système local.</span><span class="sxs-lookup"><span data-stu-id="81166-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="81166-129">Nous le montrons pour illustrer le cas le plus général, et vous rappeler la disponibilité de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="81166-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="81166-130">Par défaut, l’**espace de noms** est root/cimv2. Vous pouvez également l’omettre.</span><span class="sxs-lookup"><span data-stu-id="81166-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="81166-131">Enfin, la plupart des applets de commande permettent l’omission du nom de paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="81166-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="81166-132">Avec l’applet de commande Get-WmiObject, si aucun nom n’est spécifié pour le premier paramètre, Windows PowerShell traite celui-ci en tant que paramètre **Class**.</span><span class="sxs-lookup"><span data-stu-id="81166-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="81166-133">Cela signifie que la dernière commande pourrait avoir été émise en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="81166-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="81166-134">La classe **Win32_OperatingSystem** a beaucoup plus de propriétés que celles affichées ici.</span><span class="sxs-lookup"><span data-stu-id="81166-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="81166-135">Vous pouvez utiliser l’applet de commande Get-Member pour voir toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="81166-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="81166-136">Les propriétés d’une classe WMI sont automatiquement disponibles, comme d’autres propriétés de l’objet :</span><span class="sxs-lookup"><span data-stu-id="81166-136">The properties of a WMI class are automatically available like other object properties:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="81166-137">Affichage de propriétés autres que par défaut avec les applets de commande Format</span><span class="sxs-lookup"><span data-stu-id="81166-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="81166-138">Si vous souhaitez des informations contenues dans la classe **Win32_OperatingSystem** qui ne sont pas affichées par défaut, vous pouvez les afficher à l’aide des applets de commande **Format**.</span><span class="sxs-lookup"><span data-stu-id="81166-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="81166-139">Par exemple, si vous souhaitez afficher les données de la mémoire disponible, tapez :</span><span class="sxs-lookup"><span data-stu-id="81166-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="81166-140">Les caractères génériques fonctionnant avec les noms de propriété dans **Format-Table**, l’élément final du pipeline peut être réduit à `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="81166-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="81166-141">Les données de la mémoire peuvent être plus lisibles si vous les affichez sous forme de liste en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="81166-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```

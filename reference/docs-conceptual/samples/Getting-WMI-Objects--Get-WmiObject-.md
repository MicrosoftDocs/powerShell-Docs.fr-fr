---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Obtention d’objets WMI Get WmiObject
ms.openlocfilehash: 23fd8cf596a8be7e36651ac3f9c79ca97240e647
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737217"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="7c9e6-103">Obtention d’objets WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="7c9e6-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="7c9e6-104">Obtention d’objets WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="7c9e6-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="7c9e6-105">WMI (Windows Management Instrumentation) est une technologie majeure pour l’administration du système Windows, car elle expose un vaste éventail d’informations de manière uniforme.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="7c9e6-106">Compte tenu de tout ce que WMI permet de réaliser, la cmdlet Windows PowerShell pour l’accès aux objets WMI, `Get-CimInstance`, est l’une des plus utiles pour travailler réellement.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="7c9e6-107">Nous allons aborder l’utilisation des CimCmdlets pour accéder aux objets WMI, puis expliquer comment utiliser des objets WMI pour réaliser des opérations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="7c9e6-108">Affichage de la liste des classes WMI</span><span class="sxs-lookup"><span data-stu-id="7c9e6-108">Listing WMI Classes</span></span>

<span data-ttu-id="7c9e6-109">Le premier problème que rencontrent la plupart des utilisateurs de WMI est de comprendre ce que WMI permet de faire.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="7c9e6-110">Les classes WMI décrivent les ressources qui peuvent être gérées.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="7c9e6-111">Il existe des centaines de classes WMI, dont certaines contiennent des dizaines de propriétés.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="7c9e6-112">`Get-CimClass` résout ce problème en rendant WMI détectable.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="7c9e6-113">Vous pouvez obtenir la liste des classes WMI disponibles sur l’ordinateur local en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

<span data-ttu-id="7c9e6-114">Vous pouvez récupérer les mêmes informations à partir d’un ordinateur distant à l’aide du paramètre **ComputerName**, en spécifiant une adresse IP ou un nom d’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="7c9e6-115">La liste de classes retournée par des ordinateurs distants peut varier selon le système d’exploitation que l’ordinateur exécute et les extensions WMI ajoutées par les applications installées.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7c9e6-116">Lorsque vous utilisez des cmdlets CIM pour vous connecter à un ordinateur distant, celui-ci doit exécuter WMI et le compte que vous utilisez doit figurer dans le groupe Administrateurs local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="7c9e6-117">PowerShell ne doit pas nécessairement être installé sur le système distant.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="7c9e6-118">Cela permet d’administrer des systèmes d’exploitation qui n’exécutent pas PowerShell, mais disposent de WMI.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="7c9e6-119">Affichage des détails de classe WMI</span><span class="sxs-lookup"><span data-stu-id="7c9e6-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="7c9e6-120">Si vous connaissez déjà le nom d’une classe WMI, vous pouvez l’utiliser pour obtenir des informations immédiatement.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="7c9e6-121">Par exemple, une des classes WMI couramment utilisées pour récupérer des informations sur un ordinateur est **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="7c9e6-122">Bien que nous montrions tous les paramètres, la commande peut être exprimée de façon plus concise.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="7c9e6-123">Le paramètre **ComputerName** n’est pas nécessaire lors de la connexion au système local.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="7c9e6-124">Nous le montrons pour illustrer le cas le plus général, et vous rappeler la disponibilité de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="7c9e6-125">Par défaut, l’**espace de noms** passe à `root/CIMV2`. Vous pouvez également l’omettre.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="7c9e6-126">Enfin, la plupart des applets de commande permettent l’omission du nom de paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="7c9e6-127">Avec `Get-CimInstance`, si aucun nom n’est spécifié pour le premier paramètre, PowerShell traite celui-ci en tant que paramètre **Classe**.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="7c9e6-128">Cela signifie que la dernière commande pourrait avoir été émise en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="7c9e6-129">La classe **Win32_OperatingSystem** a beaucoup plus de propriétés que celles affichées ici.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="7c9e6-130">Vous pouvez utiliser l’applet de commande Get-Member pour voir toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="7c9e6-131">Les propriétés d’une classe WMI sont automatiquement disponibles, comme d’autres propriétés de l’objet :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-131">The properties of a WMI class are automatically available like other object properties:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="7c9e6-132">Affichage de propriétés autres que par défaut avec les applets de commande Format</span><span class="sxs-lookup"><span data-stu-id="7c9e6-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="7c9e6-133">Si vous souhaitez des informations contenues dans la classe **Win32_OperatingSystem** qui ne sont pas affichées par défaut, vous pouvez les afficher à l’aide des applets de commande **Format**.</span><span class="sxs-lookup"><span data-stu-id="7c9e6-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="7c9e6-134">Par exemple, si vous souhaitez afficher les données de la mémoire disponible, tapez :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-134">For example, if you want to display available memory data, type:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> <span data-ttu-id="7c9e6-135">Les caractères génériques fonctionnant avec les noms de propriété dans `Format-Table`, l’élément final du pipeline peut être réduit à `Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="7c9e6-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="7c9e6-136">Les données de la mémoire peuvent être plus lisibles si vous les affichez sous forme de liste en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="7c9e6-136">The memory data might be more readable if you format it as a list by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```

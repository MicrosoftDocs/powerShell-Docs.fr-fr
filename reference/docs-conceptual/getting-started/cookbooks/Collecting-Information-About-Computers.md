---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Collecte d’informations sur les ordinateurs"
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c0b7ec9ed7d2b07c66d2b1cf3342f971d71da481
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="3c824-103">Collecte d’informations sur les ordinateurs</span><span class="sxs-lookup"><span data-stu-id="3c824-103">Collecting Information About Computers</span></span>
<span data-ttu-id="3c824-104">L’applet de commande **Get-WmiObject** est la plus importante pour les tâches générales de gestion du système.</span><span class="sxs-lookup"><span data-stu-id="3c824-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="3c824-105">Tous les paramètres critiques du sous-système sont exposés via WMI.</span><span class="sxs-lookup"><span data-stu-id="3c824-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="3c824-106">En outre, WMI traite les données en tant qu’objets figurant dans des collections d’un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="3c824-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="3c824-107">Étant donné que Windows PowerShell fonctionne également avec des objets et dispose d’un pipeline permettant de traiter un ou plusieurs objets de la même façon, l’accès générique à WMI permet d’effectuer des tâches avancées sans grand effort.</span><span class="sxs-lookup"><span data-stu-id="3c824-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="3c824-108">Les exemples suivants montrent comment collecter des informations spécifiques en appliquant l’applet de commande **Get-WmiObject** à un ordinateur arbitraire.</span><span class="sxs-lookup"><span data-stu-id="3c824-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="3c824-109">Nous spécifions le paramètre **ComputerName** avec la valeur de point (**.**) qui représente l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3c824-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="3c824-110">Vous pouvez spécifier un nom ou une adresse IP associés à tout ordinateur accessible via WMI.</span><span class="sxs-lookup"><span data-stu-id="3c824-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="3c824-111">Pour récupérer des informations sur l’ordinateur local, vous pourriez omettre le paramètre **-ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="3c824-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="3c824-112">Affichage de la liste des paramètres de bureau</span><span class="sxs-lookup"><span data-stu-id="3c824-112">Listing Desktop Settings</span></span>
<span data-ttu-id="3c824-113">Nous allons commencer par une commande qui collecte des informations concernant les postes de travail sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3c824-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="3c824-114">Cette commande retourne des informations sur tous les postes de travail, qu’ils soient en cours d’utilisation ou non.</span><span class="sxs-lookup"><span data-stu-id="3c824-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="3c824-115">Les informations retournées par certaines classes WMI peuvent être très détaillées, et incluent souvent des métadonnées sur la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="3c824-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="3c824-116">Étant donné que la plupart de ces propriétés de métadonnées portent des noms commençant par un trait de soulignement double, vous pouvez filtrer les propriétés à l’aide de l’applet de commande Select-Object.</span><span class="sxs-lookup"><span data-stu-id="3c824-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="3c824-117">Spécifiez uniquement les propriétés commençant par des caractères alphabétiques en utilisant **[a-z]*** comme valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="3c824-117">Specify only properties that begin with alphabetic characters by using **[a-z]*** as the Property value.</span></span> <span data-ttu-id="3c824-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3c824-118">For example:</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="3c824-119">Pour exclure les métadonnées, utilisez un opérateur de pipeline (|) pour envoyer les résultats de la commande Get-WmiObject à **Select-Object -Property [a-z]***.</span><span class="sxs-lookup"><span data-stu-id="3c824-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to **Select-Object -Property [a-z]***.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="3c824-120">Affichage d’informations sur le BIOS</span><span class="sxs-lookup"><span data-stu-id="3c824-120">Listing BIOS Information</span></span>
<span data-ttu-id="3c824-121">La classe WMI Win32_BIOS retourne des informations relativement compactes et complètes sur le BIOS de l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="3c824-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="3c824-122">Affichage d’informations sur le processeur</span><span class="sxs-lookup"><span data-stu-id="3c824-122">Listing Processor Information</span></span>
<span data-ttu-id="3c824-123">Vous pouvez récupérer des informations générales sur le processeur à l’aide de la classe **Win32_Processor** de WMI, même si vous pouvez filtrer les informations :</span><span class="sxs-lookup"><span data-stu-id="3c824-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="3c824-124">Pour une chaîne de description générique de la famille de processeurs, vous pouvez simplement retourner la propriété **SystemType** :</span><span class="sxs-lookup"><span data-stu-id="3c824-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="3c824-125">Affichage du modèle et du fabricant de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="3c824-125">Listing Computer Manufacturer and Model</span></span>
<span data-ttu-id="3c824-126">Des informations sur le modèle d’ordinateur sont également accessibles par le biais de l’applet de commande **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="3c824-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="3c824-127">La sortie standard affichée ne nécessite pas de filtrage pour fournir des données OEM :</span><span class="sxs-lookup"><span data-stu-id="3c824-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="3c824-128">La qualité de la sortie de telles commandes, qui retournent des informations directement à partir de certains composants matériels, dépend des données dont vous disposez.</span><span class="sxs-lookup"><span data-stu-id="3c824-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="3c824-129">Il se peut que des informations mal configurées par certains fabricants de matériel ne soient pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="3c824-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="3c824-130">Affichage de la liste des correctifs installés</span><span class="sxs-lookup"><span data-stu-id="3c824-130">Listing Installed Hotfixes</span></span>
<span data-ttu-id="3c824-131">Vous pouvez afficher la liste de tous les correctifs à l’aide de la classe **Win32_QuickFixEngineering** :</span><span class="sxs-lookup"><span data-stu-id="3c824-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="3c824-132">Cette classe retourne une liste des correctifs ressemblant à ceci :</span><span class="sxs-lookup"><span data-stu-id="3c824-132">This class returns a list of hotfixes that looks like this:</span></span>

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

<span data-ttu-id="3c824-133">Pour une sortie plus concise, vous pouvez exclure certaines propriétés.</span><span class="sxs-lookup"><span data-stu-id="3c824-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="3c824-134">Vous pouvez utiliser le paramètre **Property de Get-WmiObject** pour choisir uniquement le **HotFixID**. Cela permet d’obtenir plus d’informations, car toutes les métadonnées sont affichées par défaut :</span><span class="sxs-lookup"><span data-stu-id="3c824-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

<span data-ttu-id="3c824-135">Les données supplémentaires sont retournées, car le paramètre Property dans l’applet de commande **Get-WmiObject** restreint les propriétés retournées par les instances de classe WMI, pas l’objet retourné à Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c824-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="3c824-136">Pour réduire la sortie, utilisez l’applet de commande **Select-Object** :</span><span class="sxs-lookup"><span data-stu-id="3c824-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="3c824-137">Affichage d’informations sur la version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="3c824-137">Listing Operating System Version Information</span></span>
<span data-ttu-id="3c824-138">Les propriétés de la classe **Win32_OperatingSystem** incluent des informations sur la version et le Service Pack.</span><span class="sxs-lookup"><span data-stu-id="3c824-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="3c824-139">Vous ne pouvez sélectionner explicitement que ces propriétés pour obtenir un résumé d’informations sur la version à partir de la classe **Win32_OperatingSystem** :</span><span class="sxs-lookup"><span data-stu-id="3c824-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="3c824-140">Vous pouvez également utiliser des caractères génériques avec le paramètre **Property de Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="3c824-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="3c824-141">Étant donné que l’utilisation de toutes les propriétés commençant par **Build** ou **ServicePack** est importante ici, nous pouvons raccourcir cela en utilisant la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="3c824-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="3c824-142">Affichage des utilisateurs locaux et du propriétaire</span><span class="sxs-lookup"><span data-stu-id="3c824-142">Listing Local Users and Owner</span></span>
<span data-ttu-id="3c824-143">Vous pouvez trouver des informations générales sur l’utilisateur local (nombre d’utilisateurs sous licence, nombre actuel d’utilisateurs et nom du propriétaire) avec une sélection de propriétés de la classe **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="3c824-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="3c824-144">Vous pouvez sélectionner explicitement les propriétés à afficher comme suit :</span><span class="sxs-lookup"><span data-stu-id="3c824-144">You can explicitly select the properties to display like this:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="3c824-145">Une version plus concise utilisant des caractères génériques est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3c824-145">A more succinct version using wildcards is:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="3c824-146">Obtention de l’espace disque disponible</span><span class="sxs-lookup"><span data-stu-id="3c824-146">Getting Available Disk Space</span></span>
<span data-ttu-id="3c824-147">Pour afficher l’espace disque et l’espace libre sur les lecteurs locaux, vous pouvez utiliser la classe WMI Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="3c824-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="3c824-148">Vous ne devez voir que les instances dont DriveType a la valeur 3 (valeur que WMI utilise pour les disques durs fixes).</span><span class="sxs-lookup"><span data-stu-id="3c824-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="3c824-149">Obtention d’informations sur l’ouverture de session</span><span class="sxs-lookup"><span data-stu-id="3c824-149">Getting Logon Session Information</span></span>
<span data-ttu-id="3c824-150">Vous pouvez obtenir des informations générales sur les ouvertures de session associées aux utilisateurs par le biais de la classe WMI Win32_LogonSession :</span><span class="sxs-lookup"><span data-stu-id="3c824-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="3c824-151">Obtention de l’utilisateur connecté à un ordinateur</span><span class="sxs-lookup"><span data-stu-id="3c824-151">Getting the User Logged on to a Computer</span></span>
<span data-ttu-id="3c824-152">Vous pouvez afficher l’utilisateur connecté à un système informatique particulier à l’aide de la commande Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="3c824-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="3c824-153">Cette commande retourne uniquement l’utilisateur connecté au bureau du système :</span><span class="sxs-lookup"><span data-stu-id="3c824-153">This command returns only the user logged on to the system desktop:</span></span>

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="3c824-154">Obtention de l’heure locale d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="3c824-154">Getting Local Time from a Computer</span></span>
<span data-ttu-id="3c824-155">Vous pouvez récupérer l’heure locale actuelle sur un ordinateur spécifique à l’aide de la classe WMI Win32_LocalTime.</span><span class="sxs-lookup"><span data-stu-id="3c824-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="3c824-156">Cette classe par défaut affichant toutes les métadonnées, il est souhaitable de la filtrer à l’aide de l’applet de commande **Select-Object** :</span><span class="sxs-lookup"><span data-stu-id="3c824-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a><span data-ttu-id="3c824-157">Affichage de l’état du service</span><span class="sxs-lookup"><span data-stu-id="3c824-157">Displaying Service Status</span></span>
<span data-ttu-id="3c824-158">Pour afficher l’état de tous les services sur un ordinateur spécifique, vous pouvez utiliser localement l’applet de commande **Get-Service**, comme indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="3c824-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="3c824-159">Pour des systèmes distants, vous pouvez utiliser la classe WMI Win32_Service.</span><span class="sxs-lookup"><span data-stu-id="3c824-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="3c824-160">Si vous utilisez également l’applet de commande **Select-Object** pour filtrer les résultats pour **Status**, **Name** et **DisplayName**, le format de sortie est quasiment identique à celui de l’applet de commande **Get-Service** :</span><span class="sxs-lookup"><span data-stu-id="3c824-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="3c824-161">Pour permettre l’affichage complet des noms des services occasionnels portant des noms très longs, vous pouvez utiliser l’applet de commande **Format-Table** avec les paramètres **AutoSize** et **Wrap**, pour optimiser la largeur des colonnes et permettre le retour à la ligne plutôt que la troncation des noms longs :</span><span class="sxs-lookup"><span data-stu-id="3c824-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```


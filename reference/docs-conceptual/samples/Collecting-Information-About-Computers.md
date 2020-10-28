---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Collecte d’informations sur les ordinateurs
description: Cet article explique comment regrouper des informations sur la configuration de l’ordinateur à l’aide des applets de commande WMI et CIM.
ms.openlocfilehash: 5088960ab7c049085a9d7c05ec4571b6fd7e3545
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500587"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="46c89-104">Collecte d’informations sur les ordinateurs</span><span class="sxs-lookup"><span data-stu-id="46c89-104">Collecting Information About Computers</span></span>

<span data-ttu-id="46c89-105">Les applets de commande du module **CimCmdlets** sont les applets de commande les plus importants pour les tâches générales de gestion du système.</span><span class="sxs-lookup"><span data-stu-id="46c89-105">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="46c89-106">Tous les paramètres critiques du sous-système sont exposés via WMI.</span><span class="sxs-lookup"><span data-stu-id="46c89-106">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="46c89-107">En outre, WMI traite les données en tant qu’objets figurant dans des collections d’un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="46c89-107">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="46c89-108">Étant donné que Windows PowerShell fonctionne également avec des objets et dispose d’un pipeline permettant de traiter un ou plusieurs objets de la même façon, l’accès générique à WMI permet d’effectuer des tâches avancées sans grand effort.</span><span class="sxs-lookup"><span data-stu-id="46c89-108">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="46c89-109">Affichage de la liste des paramètres de bureau</span><span class="sxs-lookup"><span data-stu-id="46c89-109">Listing Desktop Settings</span></span>

<span data-ttu-id="46c89-110">Nous allons commencer par une commande qui collecte des informations concernant les postes de travail sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="46c89-110">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="46c89-111">Cette commande retourne des informations sur tous les postes de travail, qu’ils soient en cours d’utilisation ou non.</span><span class="sxs-lookup"><span data-stu-id="46c89-111">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="46c89-112">Les informations retournées par certaines classes WMI peuvent être très détaillées, et incluent souvent des métadonnées sur la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="46c89-112">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="46c89-113">Étant donné que la plupart de ces propriétés de métadonnées portent des noms commençant par **Cim** , vous pouvez filtrer les propriétés à l’aide de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="46c89-113">Because most of these metadata properties have names that begin with **Cim** , you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="46c89-114">Spécifiez le paramètre **-ExcludeProperty** avec "Cim\*" comme valeur.</span><span class="sxs-lookup"><span data-stu-id="46c89-114">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="46c89-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="46c89-115">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="46c89-116">Pour exclure les métadonnées, utilisez un opérateur de pipeline (|) pour envoyer les résultats de la commande `Get-CimInstance` à `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="46c89-116">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="46c89-117">Affichage d’informations sur le BIOS</span><span class="sxs-lookup"><span data-stu-id="46c89-117">Listing BIOS Information</span></span>

<span data-ttu-id="46c89-118">La classe WMI **Win32_BIOS** retourne des informations relativement compactes et complètes sur le BIOS de l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="46c89-118">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="46c89-119">Affichage d’informations sur le processeur</span><span class="sxs-lookup"><span data-stu-id="46c89-119">Listing Processor Information</span></span>

<span data-ttu-id="46c89-120">Vous pouvez récupérer des informations générales sur le processeur à l’aide de la classe **Win32_Processor** de WMI, même si vous pouvez filtrer les informations :</span><span class="sxs-lookup"><span data-stu-id="46c89-120">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="46c89-121">Pour une chaîne de description générique de la famille de processeurs, vous pouvez simplement retourner la propriété **SystemType**  :</span><span class="sxs-lookup"><span data-stu-id="46c89-121">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="46c89-122">Affichage du modèle et du fabricant de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="46c89-122">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="46c89-123">Des informations sur le modèle d’ordinateur sont également accessibles par le biais de l’applet de commande **Win32_ComputerSystem** .</span><span class="sxs-lookup"><span data-stu-id="46c89-123">Computer model information is also available from **Win32_ComputerSystem** .</span></span> <span data-ttu-id="46c89-124">La sortie standard affichée ne nécessite pas de filtrage pour fournir des données OEM :</span><span class="sxs-lookup"><span data-stu-id="46c89-124">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="46c89-125">La qualité de la sortie de telles commandes, qui retournent des informations directement à partir de certains composants matériels, dépend des données dont vous disposez.</span><span class="sxs-lookup"><span data-stu-id="46c89-125">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="46c89-126">Il se peut que des informations mal configurées par certains fabricants de matériel ne soient pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="46c89-126">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="46c89-127">Affichage de la liste des correctifs installés</span><span class="sxs-lookup"><span data-stu-id="46c89-127">Listing Installed Hotfixes</span></span>

<span data-ttu-id="46c89-128">Vous pouvez afficher la liste de tous les correctifs à l’aide de la classe **Win32_QuickFixEngineering**  :</span><span class="sxs-lookup"><span data-stu-id="46c89-128">You can list all installed hotfixes by using **Win32_QuickFixEngineering** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="46c89-129">Cette classe retourne une liste des correctifs ressemblant à ceci :</span><span class="sxs-lookup"><span data-stu-id="46c89-129">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="46c89-130">Pour une sortie plus concise, vous pouvez exclure certaines propriétés.</span><span class="sxs-lookup"><span data-stu-id="46c89-130">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="46c89-131">Vous pouvez utiliser le paramètre **Property** de `Get-CimInstance` pour choisir uniquement le **HotFixID** . Cela permet d’obtenir plus d’informations, car toutes les métadonnées sont affichées par défaut :</span><span class="sxs-lookup"><span data-stu-id="46c89-131">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID** , doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

<span data-ttu-id="46c89-132">Les données supplémentaires sont retournées, car le paramètre **Propriété** dans `Get-CimInstance` restreint les propriétés retournées par les instances de classe WMI, pas l’objet retourné à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46c89-132">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="46c89-133">Pour réduire la sortie, utilisez `Select-Object` :</span><span class="sxs-lookup"><span data-stu-id="46c89-133">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="46c89-134">Affichage d’informations sur la version du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="46c89-134">Listing Operating System Version Information</span></span>

<span data-ttu-id="46c89-135">Les propriétés de la classe **Win32_OperatingSystem** incluent des informations sur la version et le Service Pack.</span><span class="sxs-lookup"><span data-stu-id="46c89-135">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="46c89-136">Vous ne pouvez sélectionner explicitement que ces propriétés pour obtenir un résumé d’informations sur la version à partir de la classe **Win32_OperatingSystem**  :</span><span class="sxs-lookup"><span data-stu-id="46c89-136">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem** :</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="46c89-137">Vous pouvez également utiliser des caractères génériques avec le paramètre **Property** de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="46c89-137">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="46c89-138">Étant donné que l’utilisation de toutes les propriétés commençant par **Build** ou **ServicePack** est importante ici, nous pouvons raccourcir cela en utilisant la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="46c89-138">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="46c89-139">Affichage des utilisateurs locaux et du propriétaire</span><span class="sxs-lookup"><span data-stu-id="46c89-139">Listing Local Users and Owner</span></span>

<span data-ttu-id="46c89-140">Vous pouvez trouver des informations générales sur l’utilisateur local (nombre d’utilisateurs sous licence, nombre actuel d’utilisateurs et nom du propriétaire) avec une sélection de la classe **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="46c89-140">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="46c89-141">Vous pouvez sélectionner explicitement les propriétés à afficher comme suit :</span><span class="sxs-lookup"><span data-stu-id="46c89-141">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="46c89-142">Une version plus concise utilisant des caractères génériques est la suivante :</span><span class="sxs-lookup"><span data-stu-id="46c89-142">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="46c89-143">Obtention de l’espace disque disponible</span><span class="sxs-lookup"><span data-stu-id="46c89-143">Getting Available Disk Space</span></span>

<span data-ttu-id="46c89-144">Pour afficher l’espace disque et l’espace libre sur les lecteurs locaux, vous pouvez utiliser la classe WMI Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="46c89-144">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="46c89-145">Vous ne devez voir que les instances dont DriveType a la valeur 3 (valeur que WMI utilise pour les disques durs fixes).</span><span class="sxs-lookup"><span data-stu-id="46c89-145">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a><span data-ttu-id="46c89-146">Obtention d’informations sur l’ouverture de session</span><span class="sxs-lookup"><span data-stu-id="46c89-146">Getting Logon Session Information</span></span>

<span data-ttu-id="46c89-147">Vous pouvez obtenir des informations générales sur les ouvertures de session associées aux utilisateurs par le biais de la classe WMI **Win32_LogonSession** :</span><span class="sxs-lookup"><span data-stu-id="46c89-147">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="46c89-148">Obtention de l’utilisateur connecté à un ordinateur</span><span class="sxs-lookup"><span data-stu-id="46c89-148">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="46c89-149">Vous pouvez afficher l’utilisateur connecté à un système informatique particulier à l’aide de la commande Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="46c89-149">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="46c89-150">Cette commande retourne uniquement l’utilisateur connecté au bureau du système :</span><span class="sxs-lookup"><span data-stu-id="46c89-150">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="46c89-151">Obtention de l’heure locale d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="46c89-151">Getting Local Time from a Computer</span></span>

<span data-ttu-id="46c89-152">Vous pouvez récupérer l’heure locale actuelle sur un ordinateur spécifique à l’aide de la classe WMI **Win32_LocalTime** .</span><span class="sxs-lookup"><span data-stu-id="46c89-152">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a><span data-ttu-id="46c89-153">Affichage de l’état du service</span><span class="sxs-lookup"><span data-stu-id="46c89-153">Displaying Service Status</span></span>

<span data-ttu-id="46c89-154">Pour afficher l’état de tous les services sur un ordinateur spécifique, vous pouvez utiliser localement l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="46c89-154">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="46c89-155">Pour des systèmes distants, vous pouvez utiliser la classe WMI **Win32_Service** .</span><span class="sxs-lookup"><span data-stu-id="46c89-155">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="46c89-156">Si vous utilisez également `Select-Object` pour filtrer les résultats pour **Status** , **Name** et **DisplayName** , le format de sortie est quasiment identique à celui de `Get-Service` :</span><span class="sxs-lookup"><span data-stu-id="46c89-156">If you also use `Select-Object` to filter the results to **Status** , **Name** , and **DisplayName** , the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="46c89-157">Pour permettre l’affichage complet des noms des services occasionnels portant des noms très longs, vous pouvez utiliser l’applet de commande `Format-Table` avec les paramètres **AutoSize** et **Wrap** , pour optimiser la largeur des colonnes et permettre le retour à la ligne plutôt que la troncation des noms longs :</span><span class="sxs-lookup"><span data-stu-id="46c89-157">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```

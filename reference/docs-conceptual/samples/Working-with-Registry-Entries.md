---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des entrées de Registre
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401852"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="e0a43-103">Utilisation des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="e0a43-103">Working with Registry Entries</span></span>

<span data-ttu-id="e0a43-104">Les entrées de Registre étant des propriétés de clés, il est impossible de les parcourir directement. Il est donc nécessaire d'adopter une approche légèrement différente pour pouvoir les utiliser.</span><span class="sxs-lookup"><span data-stu-id="e0a43-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="e0a43-105">Affichage de la liste des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="e0a43-105">Listing Registry Entries</span></span>

<span data-ttu-id="e0a43-106">Vous pouvez examiner les entrées de Registre de plusieurs manières.</span><span class="sxs-lookup"><span data-stu-id="e0a43-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="e0a43-107">La façon la plus simple consiste à obtenir les noms des propriétés associées à une clé.</span><span class="sxs-lookup"><span data-stu-id="e0a43-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="e0a43-108">Par exemple, pour afficher les noms des entrées dans la clé de Registre **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilisez **Get-Item**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="e0a43-109">Les clés de Registre possèdent une propriété avec le nom générique « Property » qui contient la liste des entrées de Registre dans la clé.</span><span class="sxs-lookup"><span data-stu-id="e0a43-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="e0a43-110">La commande suivante sélectionne la propriété Property et développe les éléments pour les afficher dans une liste :</span><span class="sxs-lookup"><span data-stu-id="e0a43-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="e0a43-111">Pour afficher les entrées de Registre dans un format plus lisible, utilisez l’applet de commande **Get-ItemProperty** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="e0a43-112">Les propriétés liées à Windows PowerShell pour la clé possèdent toutes le préfixe « PS », comme **PSPath**, **PSParentPath**, **PSChildName** et **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="e0a43-113">Pour faire référence à l’emplacement actuel, vous pouvez utiliser la notation «  **.**  ».</span><span class="sxs-lookup"><span data-stu-id="e0a43-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="e0a43-114">Pour passer d’abord au conteneur de Registre **CurrentVersion**, vous pouvez utiliser l’applet de commande **Set-Location** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="e0a43-115">Vous pouvez également utiliser le PSDrive HKLM intégré avec l’applet de commande **Set-Location** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="e0a43-116">Vous pouvez ensuite utiliser la notation «  **.**  » pour l’emplacement actuel pour répertorier les propriétés sans spécifier de chemin d’accès complet :</span><span class="sxs-lookup"><span data-stu-id="e0a43-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="e0a43-117">L’expansion de chemin fonctionne de la même façon que dans le système de fichiers. Ainsi, à partir de cet emplacement, vous pouvez obtenir la liste **ItemProperty** pour **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** en utilisant l’applet de commande **Get-ItemProperty -Path ..\\Help**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="e0a43-118">Obtention d'une entrée de Registre unique</span><span class="sxs-lookup"><span data-stu-id="e0a43-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="e0a43-119">Si vous souhaitez récupérer une entrée spécifique d'une clé de Registre, plusieurs options s'offrent à vous.</span><span class="sxs-lookup"><span data-stu-id="e0a43-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="e0a43-120">Cet exemple recherche la valeur de **DevicePath** dans **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="e0a43-121">Utilisez l’applet de commande **Get-ItemProperty** avec le paramètre **Path** pour spécifier le nom de la clé, et avec le paramètre **Name** pour spécifier le nom de l’entrée **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="e0a43-122">Cette commande retourne les propriétés Windows PowerShell standard, ainsi que la propriété **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="e0a43-123">Bien que l’applet de commande **Get-ItemProperty** dispose des paramètres **Filter**, **Include** et **Exclude**, vous ne pouvez pas les utiliser pour filtrer sur le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="e0a43-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="e0a43-124">Ces paramètres font référence aux clés de Registre (qui sont des chemins d'accès à des éléments) et non à des entrées de Registre (qui sont des propriétés d'éléments).</span><span class="sxs-lookup"><span data-stu-id="e0a43-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="e0a43-125">Une autre option consiste à utiliser l'outil en ligne de commande Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="e0a43-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="e0a43-126">Pour obtenir de l’aide sur reg.exe, tapez **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="e0a43-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="e0a43-127">à une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="e0a43-127">at a command prompt.</span></span> <span data-ttu-id="e0a43-128">Pour rechercher l'entrée DevicePath, utilisez reg.exe comme indiqué dans la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0a43-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="e0a43-129">Vous pouvez aussi utiliser l’objet **COM WshShell** pour rechercher des entrées de Registre. Toutefois, cette méthode ne fonctionne ni avec des données binaires volumineuses, ni avec des noms d’entrées de Registre contenant des caractères tels que « \\ ».</span><span class="sxs-lookup"><span data-stu-id="e0a43-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="e0a43-130">Ajoutez le nom de la propriété au chemin de l’élément avec un séparateur \\ :</span><span class="sxs-lookup"><span data-stu-id="e0a43-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="e0a43-131">Création d'entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="e0a43-131">Creating New Registry Entries</span></span>

<span data-ttu-id="e0a43-132">Pour ajouter une nouvelle entrée nommée « PowerShellPath » à la clé **CurrentVersion**, utilisez l’applet de commande **New-ItemProperty** avec le chemin d’accès à la clé, le nom de l’entrée et la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="e0a43-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="e0a43-133">Pour cet exemple, nous allons prendre la valeur de la variable Windows PowerShell **$PSHome**, qui stocke le chemin d’accès au répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0a43-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="e0a43-134">Vous pouvez ajouter la nouvelle entrée à la clé à l'aide de la commande suivante. La commande retourne également des informations sur la nouvelle entrée :</span><span class="sxs-lookup"><span data-stu-id="e0a43-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="e0a43-135">**PropertyType** doit être le nom d’un membre d’énumération **Microsoft.Win32.RegistryValueKind** figurant dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="e0a43-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="e0a43-136">Valeur PropertyType</span><span class="sxs-lookup"><span data-stu-id="e0a43-136">PropertyType Value</span></span>|<span data-ttu-id="e0a43-137">Signification</span><span class="sxs-lookup"><span data-stu-id="e0a43-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="e0a43-138">Binary</span><span class="sxs-lookup"><span data-stu-id="e0a43-138">Binary</span></span>|<span data-ttu-id="e0a43-139">Données binaires</span><span class="sxs-lookup"><span data-stu-id="e0a43-139">Binary data</span></span>|
|<span data-ttu-id="e0a43-140">DWord</span><span class="sxs-lookup"><span data-stu-id="e0a43-140">DWord</span></span>|<span data-ttu-id="e0a43-141">Nombre UInt32 valide</span><span class="sxs-lookup"><span data-stu-id="e0a43-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="e0a43-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="e0a43-142">ExpandString</span></span>|<span data-ttu-id="e0a43-143">Chaîne pouvant contenir des variables d'environnement qui sont développées de manière dynamique</span><span class="sxs-lookup"><span data-stu-id="e0a43-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="e0a43-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="e0a43-144">MultiString</span></span>|<span data-ttu-id="e0a43-145">Chaîne multiligne</span><span class="sxs-lookup"><span data-stu-id="e0a43-145">A multiline string</span></span>|
|<span data-ttu-id="e0a43-146">String</span><span class="sxs-lookup"><span data-stu-id="e0a43-146">String</span></span>|<span data-ttu-id="e0a43-147">Valeur de chaîne quelconque</span><span class="sxs-lookup"><span data-stu-id="e0a43-147">Any string value</span></span>|
|<span data-ttu-id="e0a43-148">QWord</span><span class="sxs-lookup"><span data-stu-id="e0a43-148">QWord</span></span>|<span data-ttu-id="e0a43-149">8 octets de données binaires</span><span class="sxs-lookup"><span data-stu-id="e0a43-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="e0a43-150">Vous pouvez ajouter une entrée de Registre à plusieurs emplacements en spécifiant un tableau de valeurs pour le paramètre **Path** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="e0a43-151">Vous pouvez aussi remplacer une valeur d’entrée de Registre préexistante en ajoutant le paramètre **Force** à toute commande **New-ItemProperty**.</span><span class="sxs-lookup"><span data-stu-id="e0a43-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="e0a43-152">Affectation d'un nouveau nom à des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="e0a43-152">Renaming Registry Entries</span></span>

<span data-ttu-id="e0a43-153">Pour affecter à l’entrée **PowerShellPath** le nom « PSHome », utilisez **Rename-ItemProperty** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="e0a43-154">Pour afficher la valeur renommée, ajoutez le paramètre **PassThru** à la commande.</span><span class="sxs-lookup"><span data-stu-id="e0a43-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="e0a43-155">Suppression d'entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="e0a43-155">Deleting Registry Entries</span></span>

<span data-ttu-id="e0a43-156">Pour supprimer les entrées de Registre PSHome et PowerShellPath, utilisez l’applet de commande **Remove-ItemProperty** :</span><span class="sxs-lookup"><span data-stu-id="e0a43-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
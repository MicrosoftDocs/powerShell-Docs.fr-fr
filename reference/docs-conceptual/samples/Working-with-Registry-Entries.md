---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des entrées de Registre
ms.openlocfilehash: 7f8ee87cebb8b220570bcb969445071a72a68526
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758480"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="56f61-103">Utilisation des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="56f61-103">Working with Registry Entries</span></span>

<span data-ttu-id="56f61-104">Les entrées de Registre étant des propriétés de clés, il est impossible de les parcourir directement. Il est donc nécessaire d'adopter une approche légèrement différente pour pouvoir les utiliser.</span><span class="sxs-lookup"><span data-stu-id="56f61-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="56f61-105">Affichage de la liste des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="56f61-105">Listing Registry Entries</span></span>

<span data-ttu-id="56f61-106">Vous pouvez examiner les entrées de Registre de plusieurs manières.</span><span class="sxs-lookup"><span data-stu-id="56f61-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="56f61-107">La façon la plus simple consiste à obtenir les noms des propriétés associées à une clé.</span><span class="sxs-lookup"><span data-stu-id="56f61-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="56f61-108">Par exemple, pour afficher les noms des entrées dans la clé de Registre `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilisez `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="56f61-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="56f61-109">Les clés de Registre possèdent une propriété avec le nom générique « Property » qui contient la liste des entrées de Registre dans la clé.</span><span class="sxs-lookup"><span data-stu-id="56f61-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="56f61-110">La commande suivante sélectionne la propriété Property et développe les éléments pour les afficher dans une liste :</span><span class="sxs-lookup"><span data-stu-id="56f61-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="56f61-111">Pour afficher les entrées de Registre dans un format plus lisible, utilisez `Get-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="56f61-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="56f61-112">Les propriétés liées à Windows PowerShell pour la clé possèdent toutes le préfixe « PS », comme **PSPath**, **PSParentPath**, **PSChildName** et **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="56f61-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="56f61-113">Pour faire référence à l’emplacement actuel, vous pouvez utiliser la notation `*.*`.</span><span class="sxs-lookup"><span data-stu-id="56f61-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="56f61-114">Pour passer d’abord au conteneur de Registre **CurrentVersion**, vous pouvez utiliser `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="56f61-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="56f61-115">Vous pouvez également utiliser le PSDrive HKLM intégré avec `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="56f61-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="56f61-116">Vous pouvez ensuite utiliser la notation `*.*` pour l’emplacement actuel pour répertorier les propriétés sans spécifier de chemin d’accès complet :</span><span class="sxs-lookup"><span data-stu-id="56f61-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="56f61-117">L’expansion de chemin fonctionne de la même façon que dans le système de fichiers. Ainsi, à partir de cet emplacement, vous pouvez obtenir la liste **ItemProperty** pour `HKLM:\SOFTWARE\Microsoft\Windows\Help` en utilisant `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="56f61-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="56f61-118">Obtention d'une entrée de Registre unique</span><span class="sxs-lookup"><span data-stu-id="56f61-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="56f61-119">Si vous souhaitez récupérer une entrée spécifique d'une clé de Registre, plusieurs options s'offrent à vous.</span><span class="sxs-lookup"><span data-stu-id="56f61-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="56f61-120">Cet exemple détermine la valeur de **DevicePath** dans `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="56f61-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="56f61-121">Utilisez `Get-ItemProperty` avec le paramètre **Path** pour spécifier le nom de la clé, et avec le paramètre **Name** pour spécifier le nom de l’entrée **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="56f61-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="56f61-122">Cette commande retourne les propriétés Windows PowerShell standard, ainsi que la propriété **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="56f61-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="56f61-123">Bien que `Get-ItemProperty` dispose des paramètres **Filter**, **Include** et **Exclude**, vous ne pouvez pas les utiliser pour filtrer par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="56f61-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="56f61-124">Ces paramètres référencent des clés de Registre qui sont des chemins d’éléments, et non des entrées de Registre, qui sont des propriétés d’éléments.</span><span class="sxs-lookup"><span data-stu-id="56f61-124">These parameters refer to registry keys, which are item paths and not registry entries, which are item properties.</span></span>

<span data-ttu-id="56f61-125">Une autre option consiste à utiliser l'outil en ligne de commande Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="56f61-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="56f61-126">Pour obtenir de l’aide sur reg.exe, tapez `reg.exe /?` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="56f61-126">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="56f61-127">Pour rechercher l'entrée DevicePath, utilisez reg.exe comme indiqué dans la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="56f61-127">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="56f61-128">Vous pouvez aussi utiliser l’objet COM **WshShell** pour rechercher des entrées de Registre. Toutefois, cette méthode ne fonctionne ni avec des données binaires volumineuses, ni avec des noms d’entrées de Registre contenant des caractères tels que « \\ ».</span><span class="sxs-lookup"><span data-stu-id="56f61-128">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="56f61-129">Ajoutez le nom de la propriété au chemin de l’élément avec un séparateur \\ :</span><span class="sxs-lookup"><span data-stu-id="56f61-129">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="56f61-130">Définition d’une entrée de Registre unique</span><span class="sxs-lookup"><span data-stu-id="56f61-130">Setting a Single Registry Entry</span></span>

<span data-ttu-id="56f61-131">Si vous souhaitez modifier une entrée spécifique d’une clé de Registre, plusieurs options s’offrent à vous.</span><span class="sxs-lookup"><span data-stu-id="56f61-131">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="56f61-132">Cet exemple modifie l’entrée **Path** sous `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="56f61-132">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="56f61-133">L’entrée **Path** indique où trouver les fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="56f61-133">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="56f61-134">Récupérez la valeur actuelle de l’entrée **Path** à l’aide de `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="56f61-134">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="56f61-135">Ajoutez la nouvelle valeur, en la séparant avec un `;`.</span><span class="sxs-lookup"><span data-stu-id="56f61-135">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="56f61-136">Utilisez `Set-ItemProperty` avec la clé spécifiée, le nom de l’entrée et la valeur pour modifier l’entrée de Registre.</span><span class="sxs-lookup"><span data-stu-id="56f61-136">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="56f61-137">Bien que `Set-ItemProperty` dispose des paramètres **Filter**, **Include** et **Exclude**, vous ne pouvez pas les utiliser pour filtrer par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="56f61-137">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="56f61-138">Ces paramètres font référence aux clés de Registre (qui sont des chemins d'accès à des éléments) et non à des entrées de Registre (qui sont des propriétés d'éléments).</span><span class="sxs-lookup"><span data-stu-id="56f61-138">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="56f61-139">Une autre option consiste à utiliser l'outil en ligne de commande Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="56f61-139">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="56f61-140">Pour obtenir de l’aide sur reg.exe, tapez **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="56f61-140">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="56f61-141">à une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="56f61-141">at a command prompt.</span></span>

<span data-ttu-id="56f61-142">L’exemple suivant modifie l’entrée **Path** en supprimant le chemin d’accès ajouté dans l’exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="56f61-142">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="56f61-143">`Get-ItemProperty` est toujours utilisé pour récupérer la valeur actuelle pour éviter d’avoir à analyser la chaîne retournée par `reg query`.</span><span class="sxs-lookup"><span data-stu-id="56f61-143">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="56f61-144">Les méthodes **SubString** et **LastIndexOf** sont utilisées pour récupérer le dernier chemin d’accès ajouté à l’entrée **Path**.</span><span class="sxs-lookup"><span data-stu-id="56f61-144">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="56f61-145">Création d'entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="56f61-145">Creating New Registry Entries</span></span>

<span data-ttu-id="56f61-146">Pour ajouter une nouvelle entrée nommée « PowerShellPath » à la clé **CurrentVersion**, utilisez `New-ItemProperty` avec le chemin de la clé, le nom de l’entrée et la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="56f61-146">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="56f61-147">Pour cet exemple, nous allons prendre la valeur de la variable Windows PowerShell `$PSHome`, qui stocke le chemin d’accès au répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56f61-147">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="56f61-148">Vous pouvez ajouter la nouvelle entrée à la clé à l'aide de la commande suivante. La commande retourne également des informations sur la nouvelle entrée :</span><span class="sxs-lookup"><span data-stu-id="56f61-148">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="56f61-149">**PropertyType** doit être le nom d'un membre d'énumération **Microsoft.Win32.RegistryValueKind** figurant dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="56f61-149">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="56f61-150">Valeur PropertyType</span><span class="sxs-lookup"><span data-stu-id="56f61-150">PropertyType Value</span></span>|<span data-ttu-id="56f61-151">Signification</span><span class="sxs-lookup"><span data-stu-id="56f61-151">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="56f61-152">Binary</span><span class="sxs-lookup"><span data-stu-id="56f61-152">Binary</span></span>|<span data-ttu-id="56f61-153">Données binaires</span><span class="sxs-lookup"><span data-stu-id="56f61-153">Binary data</span></span>|
|<span data-ttu-id="56f61-154">DWord</span><span class="sxs-lookup"><span data-stu-id="56f61-154">DWord</span></span>|<span data-ttu-id="56f61-155">Nombre UInt32 valide</span><span class="sxs-lookup"><span data-stu-id="56f61-155">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="56f61-156">ExpandString</span><span class="sxs-lookup"><span data-stu-id="56f61-156">ExpandString</span></span>|<span data-ttu-id="56f61-157">Chaîne pouvant contenir des variables d'environnement qui sont développées de manière dynamique</span><span class="sxs-lookup"><span data-stu-id="56f61-157">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="56f61-158">MultiString</span><span class="sxs-lookup"><span data-stu-id="56f61-158">MultiString</span></span>|<span data-ttu-id="56f61-159">Chaîne multiligne</span><span class="sxs-lookup"><span data-stu-id="56f61-159">A multiline string</span></span>|
|<span data-ttu-id="56f61-160">String</span><span class="sxs-lookup"><span data-stu-id="56f61-160">String</span></span>|<span data-ttu-id="56f61-161">Valeur de chaîne quelconque</span><span class="sxs-lookup"><span data-stu-id="56f61-161">Any string value</span></span>|
|<span data-ttu-id="56f61-162">QWord</span><span class="sxs-lookup"><span data-stu-id="56f61-162">QWord</span></span>|<span data-ttu-id="56f61-163">8 octets de données binaires</span><span class="sxs-lookup"><span data-stu-id="56f61-163">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="56f61-164">Vous pouvez ajouter une entrée de Registre à plusieurs emplacements en spécifiant un tableau de valeurs pour le paramètre **Path** :</span><span class="sxs-lookup"><span data-stu-id="56f61-164">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="56f61-165">Vous pouvez aussi remplacer une valeur d’entrée de Registre préexistante en ajoutant le paramètre **Force** à toute commande `New-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="56f61-165">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="56f61-166">Affectation d'un nouveau nom à des entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="56f61-166">Renaming Registry Entries</span></span>

<span data-ttu-id="56f61-167">Pour affecter le nom « PSHome » à l’entrée **PowerShellPath**, utilisez `Rename-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="56f61-167">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="56f61-168">Pour afficher la valeur renommée, ajoutez le paramètre **PassThru** à la commande.</span><span class="sxs-lookup"><span data-stu-id="56f61-168">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="56f61-169">Suppression d'entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="56f61-169">Deleting Registry Entries</span></span>

<span data-ttu-id="56f61-170">Pour supprimer les entrées de Registre PSHome et PowerShellPath, utilisez `Remove-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="56f61-170">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```

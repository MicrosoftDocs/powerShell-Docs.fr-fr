---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des lecteurs Windows PowerShell
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215511"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="eb95b-103">Gestion des lecteurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb95b-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="eb95b-104">Un *lecteur Windows PowerShell* est un emplacement de magasin de données auquel vous pouvez accéder, au même titre qu’un lecteur du système de fichiers dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb95b-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="eb95b-105">Les fournisseurs Windows PowerShell créent pour vous certains lecteurs, comme les lecteurs du système de fichiers (y compris C: et D:), les lecteurs de Registre (HKCU: et HKLM:) et le lecteur de certificat (Cert:). Vous pouvez également créer vos propres lecteurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb95b-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="eb95b-106">Ces lecteurs sont très utiles, mais ils ne sont disponibles que dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb95b-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="eb95b-107">Vous ne pouvez pas y accéder à l'aide d'autres outils Windows, tels que l'Explorateur de fichiers ou Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="eb95b-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="eb95b-108">Les commandes associées aux lecteurs Windows PowerShell comportent le mot **PSDrive** dans leur intitulé.</span><span class="sxs-lookup"><span data-stu-id="eb95b-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="eb95b-109">Pour obtenir la liste des lecteurs Windows PowerShell dans votre session Windows PowerShell, utilisez l’applet de commande **Get-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="eb95b-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="eb95b-110">Bien que les lecteurs répertoriés varient en fonction des lecteurs de votre système, leur liste est similaire à la sortie de la commande **Get-PSDrive** ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="eb95b-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="eb95b-111">Les lecteurs du système de fichiers sont un sous-ensemble des lecteurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb95b-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="eb95b-112">Les lecteurs du système de fichiers sont identifiés par l'entrée FileSystem dans la colonne Provider.</span><span class="sxs-lookup"><span data-stu-id="eb95b-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="eb95b-113">(Les lecteurs du système de fichiers dans Windows PowerShell sont pris en charge par le fournisseur FileSystem de Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="eb95b-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="eb95b-114">Pour afficher la syntaxe de l’applet de commande **Get-PSDrive**, tapez une commande **Get-Command** avec le paramètre **Syntax** :</span><span class="sxs-lookup"><span data-stu-id="eb95b-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="eb95b-115">Le paramètre **PSProvider** permet d’afficher uniquement les lecteurs Windows PowerShell pris en charge par un fournisseur particulier.</span><span class="sxs-lookup"><span data-stu-id="eb95b-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="eb95b-116">Par exemple, pour afficher uniquement les lecteurs pris en charge par le fournisseur FileSystem de Windows PowerShell, tapez une commande **Get-PSDrive** avec le paramètre **PSProvider** et la valeur **FileSystem** :</span><span class="sxs-lookup"><span data-stu-id="eb95b-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="eb95b-117">Pour afficher les lecteurs Windows PowerShell qui représentent les ruches du Registre, utilisez le paramètre **PSProvider** pour afficher uniquement les lecteurs Windows PowerShell pris en charge par le fournisseur de Registre de Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="eb95b-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="eb95b-118">Vous pouvez également utiliser les applets de commande Location standard avec les lecteurs Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="eb95b-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="eb95b-119">Ajout de nouveaux lecteurs Windows PowerShell (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="eb95b-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="eb95b-120">Vous pouvez ajouter vos propres lecteurs Windows PowerShell à l’aide de la commande **New-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="eb95b-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="eb95b-121">Pour obtenir la syntaxe de l’applet de commande **New-PSDrive**, entrez la commande **Get-Command** avec le paramètre **Syntax** :</span><span class="sxs-lookup"><span data-stu-id="eb95b-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="eb95b-122">Pour créer un lecteur Windows PowerShell, vous devez spécifier trois paramètres :</span><span class="sxs-lookup"><span data-stu-id="eb95b-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="eb95b-123">le nom du lecteur (vous pouvez utiliser n'importe quel nom Windows PowerShell valide) ;</span><span class="sxs-lookup"><span data-stu-id="eb95b-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="eb95b-124">le fournisseur PSProvider (utilisez « FileSystem » pour les emplacements du système de fichiers et « Registry » pour les emplacements du Registre) ;</span><span class="sxs-lookup"><span data-stu-id="eb95b-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="eb95b-125">la racine, c'est-à-dire le chemin d'accès à la racine du nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="eb95b-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="eb95b-126">Par exemple, vous pouvez créer un lecteur nommé « Office » qui est mappé au dossier contenant les applications Microsoft Office sur votre ordinateur, par exemple **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="eb95b-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="eb95b-127">Pour créer le lecteur, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="eb95b-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="eb95b-128">En général, les chemins d'accès ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="eb95b-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="eb95b-129">Vous pouvez référencer le nouveau lecteur Windows PowerShell comme tout autre lecteur Windows PowerShell, c’est-à-dire en tapant son nom suivi du signe deux-points ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="eb95b-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="eb95b-130">Un lecteur Windows PowerShell peut simplifier de nombreuses tâches.</span><span class="sxs-lookup"><span data-stu-id="eb95b-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="eb95b-131">Par exemple, certaines clés importantes dans le Registre Windows ont des chemins d'accès tellement longs qu'il est difficile d'y accéder et de s'en souvenir.</span><span class="sxs-lookup"><span data-stu-id="eb95b-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="eb95b-132">Les informations de configuration critiques se trouvent sous **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="eb95b-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="eb95b-133">Pour afficher et modifier des éléments dans la clé de Registre CurrentVersion, vous pouvez créer un lecteur Windows PowerShell ayant pour racine cette clé en tapant :</span><span class="sxs-lookup"><span data-stu-id="eb95b-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="eb95b-134">Vous pouvez ensuite modifier l’emplacement du lecteur **cvkey:** comme vous le feriez pour tout autre lecteur :</span><span class="sxs-lookup"><span data-stu-id="eb95b-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="eb95b-135">ou :</span><span class="sxs-lookup"><span data-stu-id="eb95b-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="eb95b-136">L'applet de commande New-PsDrive ajoute le nouveau lecteur uniquement à la session Windows PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="eb95b-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="eb95b-137">Si vous fermez la fenêtre Windows PowerShell, le nouveau lecteur est perdu.</span><span class="sxs-lookup"><span data-stu-id="eb95b-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="eb95b-138">Pour enregistrer un lecteur Windows PowerShell, utilisez l’applet de commande Export-Console pour exporter la session Windows PowerShell active, puis utilisez le paramètre **PSConsoleFile** de PowerShell.exe pour l’importer.</span><span class="sxs-lookup"><span data-stu-id="eb95b-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="eb95b-139">Vous pouvez aussi ajouter le nouveau lecteur à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb95b-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="eb95b-140">Suppression de lecteurs Windows PowerShell (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="eb95b-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="eb95b-141">Pour supprimer des lecteurs de Windows PowerShell, utilisez l’applet de commande **Remove-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="eb95b-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="eb95b-142">L’applet de commande **Remove-PSDrive** est facile à utiliser. Pour supprimer un lecteur Windows PowerShell, vous devez simplement spécifier son nom.</span><span class="sxs-lookup"><span data-stu-id="eb95b-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="eb95b-143">Par exemple, si vous avez ajouté le lecteur Windows PowerShell **Office :** qui apparaît dans la rubrique **New-PSDrive**, vous pouvez le supprimer en saisissant :</span><span class="sxs-lookup"><span data-stu-id="eb95b-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="eb95b-144">Pour supprimer le lecteur Windows PowerShell **cvkey:** qui apparaît aussi dans la rubrique **New-PSDrive**, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="eb95b-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="eb95b-145">S'il est facile de supprimer un lecteur Windows PowerShell, vous devez toutefois vous assurer de ne pas vous trouver à l'emplacement du lecteur pour que l'opération réussisse.</span><span class="sxs-lookup"><span data-stu-id="eb95b-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="eb95b-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb95b-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="eb95b-147">Ajout et suppression de lecteurs en dehors de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb95b-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="eb95b-148">Windows PowerShell détecte les lecteurs du système de fichiers qui sont ajoutés ou supprimés dans Windows, y compris les lecteurs réseau mappés, les lecteurs USB attachés, ainsi que les lecteurs supprimés à l’aide de la commande **net use** ou des méthodes **WScript.NetworkMapNetworkDrive** et **RemoveNetworkDrive** à partir d’un script WSH (Windows Script Host).</span><span class="sxs-lookup"><span data-stu-id="eb95b-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>

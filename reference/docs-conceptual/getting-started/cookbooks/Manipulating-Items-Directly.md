---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Manipulation d'éléments de manière directe
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953665"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="4992f-103">Manipulation d'éléments de manière directe</span><span class="sxs-lookup"><span data-stu-id="4992f-103">Manipulating Items Directly</span></span>

<span data-ttu-id="4992f-104">Dans Windows PowerShell, le terme *éléments* est utilisé pour désigner ce que vous voyez dans les lecteurs Windows PowerShell, comme les fichiers et les dossiers dans les lecteurs du système de fichiers, ainsi que les clés de Registre dans les lecteurs de Registre Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4992f-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="4992f-105">Les applets de commande associées à l’utilisation de ces éléments comportent le mot **Item** dans leur intitulé.</span><span class="sxs-lookup"><span data-stu-id="4992f-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="4992f-106">La sortie de la commande **Get-Command -Noun Item** montre qu’il existe neuf applets de commande Windows PowerShell relatives aux éléments.</span><span class="sxs-lookup"><span data-stu-id="4992f-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a><span data-ttu-id="4992f-107">Création d'éléments (New-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="4992f-108">Pour créer un élément dans le système de fichiers, utilisez l’applet de commande **New-Item**.</span><span class="sxs-lookup"><span data-stu-id="4992f-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="4992f-109">Indiquez le chemin d’accès à l’élément dans le paramètre **Path**, et la valeur « File » ou « Directory » dans le paramètre **ItemType**.</span><span class="sxs-lookup"><span data-stu-id="4992f-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="4992f-110">Par exemple, pour créer un répertoire nommé « New.Directory » dans le répertoire C:\\Temp, tapez :</span><span class="sxs-lookup"><span data-stu-id="4992f-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="4992f-111">Pour créer un fichier, affectez au paramètre **ItemType** la valeur « File ».</span><span class="sxs-lookup"><span data-stu-id="4992f-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="4992f-112">Par exemple, pour créer un fichier nommé « file1.txt » dans le répertoire New.Directory, tapez :</span><span class="sxs-lookup"><span data-stu-id="4992f-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="4992f-113">Vous pouvez utiliser la même technique pour créer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="4992f-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="4992f-114">En fait, une clé de Registre est plus facile à créer, car le seul type d'élément dans le Registre Windows est une clé.</span><span class="sxs-lookup"><span data-stu-id="4992f-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="4992f-115">(Les entrées de Registre sont des *propriétés* d’élément.) Par exemple, pour créer une clé nommée « _Test » dans la sous-clé CurrentVersion, tapez :</span><span class="sxs-lookup"><span data-stu-id="4992f-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="4992f-116">Quand vous tapez un chemin d’accès au Registre, veillez à inclure le signe deux-points (**:**) dans les noms de lecteur Windows PowerShell (HKLM: et HKCU:).</span><span class="sxs-lookup"><span data-stu-id="4992f-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="4992f-117">Sans les deux-points, Windows PowerShell ne reconnaît pas le nom du lecteur dans le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="4992f-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="4992f-118">Pourquoi les valeurs de Registre ne sont pas des éléments</span><span class="sxs-lookup"><span data-stu-id="4992f-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="4992f-119">Quand vous utilisez l’applet de commande **Get-ChildItem** pour rechercher les éléments dans une clé de Registre, ni les entrées de Registre ni leurs valeurs n’apparaissent.</span><span class="sxs-lookup"><span data-stu-id="4992f-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="4992f-120">Par exemple, la clé de Registre **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** contient généralement plusieurs entrées de Registre qui représentent des applications qui s’exécutent au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="4992f-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="4992f-121">Toutefois, quand vous utilisez **Get-ChildItem** pour rechercher les éléments enfants dans la clé, la sous-clé **OptionalComponents** de la clé est la seule chose qui s’affiche :</span><span class="sxs-lookup"><span data-stu-id="4992f-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="4992f-122">Bien qu'il serait pratique de traiter les entrées de Registre en tant qu'éléments, vous ne pouvez pas spécifier un chemin d'accès à une entrée de Registre d'une façon qui garantit son unicité.</span><span class="sxs-lookup"><span data-stu-id="4992f-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="4992f-123">La notation de chemin d’accès ne fait pas la distinction entre la sous-clé de Registre nommée **Run** et l’entrée de Registre **(Default)** dans la sous-clé **Run**.</span><span class="sxs-lookup"><span data-stu-id="4992f-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="4992f-124">Par ailleurs, si les entrées de Registre étaient des éléments, du fait que les noms des entrées de Registre peuvent contenir une barre oblique inverse (**\\**), vous ne pourriez pas faire la distinction entre une entrée de Registre nommée **Windows\\CurrentVersion\\Run** et la sous-clé située dans ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4992f-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="4992f-125">Affectation d'un nouveau nom à des éléments existants (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="4992f-126">Pour modifier le nom d’un fichier ou d’un dossier, utilisez l’applet de commande **Rename-Item**.</span><span class="sxs-lookup"><span data-stu-id="4992f-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="4992f-127">La commande suivante remplace le nom du fichier **file1.txt** par **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="4992f-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="4992f-128">L’applet de commande **Rename-Item** peut modifier le nom d’un fichier ou d’un dossier, mais elle ne peut pas déplacer un élément.</span><span class="sxs-lookup"><span data-stu-id="4992f-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="4992f-129">La commande suivante échoue, car elle tente de déplacer le fichier du répertoire New.Directory vers le répertoire Temp.</span><span class="sxs-lookup"><span data-stu-id="4992f-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="4992f-130">Déplacement d'éléments (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="4992f-131">Pour déplacer un fichier ou un dossier, utilisez l’applet de commande **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="4992f-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="4992f-132">Par exemple, la commande suivante déplace le répertoire New.Directory du répertoire C:\\temp vers la racine du lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="4992f-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="4992f-133">Pour vérifier que l’élément a bien été déplacé, incluez le paramètre **PassThru** de l’applet de commande **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="4992f-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="4992f-134">Sans le paramètre **Passthru**, l’applet de commande **Move-Item** n’affiche aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="4992f-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="4992f-135">Copie d'éléments (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="4992f-136">Si vous avez déjà effectué des opérations de copie dans d’autres interpréteurs de commandes, le comportement de l’applet de commande **Copy-Item** dans Windows PowerShell peut vous sembler inhabituel.</span><span class="sxs-lookup"><span data-stu-id="4992f-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="4992f-137">Quand vous copiez un élément d'un emplacement vers un autre, Copy-Item ne copie pas par défaut son contenu.</span><span class="sxs-lookup"><span data-stu-id="4992f-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="4992f-138">Par exemple, si vous copiez le répertoire **New.Directory** du lecteur C: vers le répertoire C:\\temp, la commande aboutit, mais les fichiers du répertoire New.Directory ne sont pas copiés.</span><span class="sxs-lookup"><span data-stu-id="4992f-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="4992f-139">Si vous affichez le contenu du dossier **C:\\temp\\New.Directory**, vous pouvez constater qu’il ne comprend aucun fichier :</span><span class="sxs-lookup"><span data-stu-id="4992f-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="4992f-140">Pourquoi l’applet de commande **Copy-Item** ne copie-t-elle pas le contenu vers le nouvel emplacement ?</span><span class="sxs-lookup"><span data-stu-id="4992f-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="4992f-141">L’applet de commande **Copy-Item** a été conçue de manière générique, c’est-à-dire qu’elle ne sert pas simplement à copier des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="4992f-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="4992f-142">En outre, même si vous copiez des fichiers et des dossiers, vous pouvez être amené à copier uniquement le conteneur et non les éléments qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="4992f-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="4992f-143">Pour copier tout le contenu d’un dossier, incluez le paramètre **Recurse** de l’applet de commande **Copy-Item** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="4992f-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="4992f-144">Si vous avez déjà copié le répertoire sans son contenu, ajoutez le paramètre **Force** pour remplacer le dossier vide.</span><span class="sxs-lookup"><span data-stu-id="4992f-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a><span data-ttu-id="4992f-145">Suppression d'éléments (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="4992f-146">Pour supprimer des fichiers et des dossiers, utilisez l’applet de commande **Remove-Item**.</span><span class="sxs-lookup"><span data-stu-id="4992f-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="4992f-147">Les applets de commande Windows PowerShell telles que **Remove-Item**, qui effectuent des modifications importantes et irréversibles, affichent souvent une invite de confirmation quand vous entrez leurs commandes.</span><span class="sxs-lookup"><span data-stu-id="4992f-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="4992f-148">Par exemple, si vous essayez de supprimer le dossier **New.Directory** qui contient des fichiers, vous êtes invité à confirmer la commande :</span><span class="sxs-lookup"><span data-stu-id="4992f-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="4992f-149">**Yes** étant la réponse par défaut, pour supprimer le dossier et ses fichiers, appuyez sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="4992f-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="4992f-150">Pour supprimer le dossier sans confirmation, utilisez le paramètre **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="4992f-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="4992f-151">Exécution d'éléments (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="4992f-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="4992f-152">Windows PowerShell utilise l’applet de commande **Invoke-Item** pour effectuer une action par défaut pour un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="4992f-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="4992f-153">Cette action par défaut est déterminée par le gestionnaire d'application par défaut dans le Registre. Vous obtenez le même résultat qu'en double-cliquant sur l'élément dans l'Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4992f-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="4992f-154">Par exemple, imaginez que vous exécutiez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4992f-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="4992f-155">Une fenêtre d’explorateur située dans C:\\Windows s’affiche comme si vous aviez double-cliqué sur le dossier C:\\Windows.</span><span class="sxs-lookup"><span data-stu-id="4992f-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="4992f-156">Si vous appelez le fichier **Boot.ini** sur un système antérieur à Windows Vista :</span><span class="sxs-lookup"><span data-stu-id="4992f-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="4992f-157">Si le type de fichier .ini est associé au Bloc-notes, le fichier boot.ini s'ouvre dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="4992f-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de fichiers et dossiers
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: a8d57a1c269d95e692db6c3f1ae10df49e305e4e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401276"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="b4553-103">Utilisation de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="b4553-103">Working with Files and Folders</span></span>

<span data-ttu-id="b4553-104">La navigation dans des lecteurs Windows PowerShell et la manipulation des éléments qu’ils contiennent sont similaires à la manipulation de fichiers et dossiers sur des lecteurs de disques physiques Windows.</span><span class="sxs-lookup"><span data-stu-id="b4553-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="b4553-105">Cette section explique comment effectuer certaines tâches de manipulation de fichiers et dossiers à l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4553-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="b4553-106">Affichage de la liste de tous les fichiers et dossiers figurant dans un dossier</span><span class="sxs-lookup"><span data-stu-id="b4553-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="b4553-107">Vous pouvez obtenir tous les éléments figurant directement dans un dossier à l’aide de l’applet de commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="b4553-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="b4553-108">Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**.</span><span class="sxs-lookup"><span data-stu-id="b4553-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="b4553-109">Par exemple, cette commande affiche le contenu direct du lecteur C de Windows PowerShell (qui est le même que le lecteur physique C de Windows) :</span><span class="sxs-lookup"><span data-stu-id="b4553-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="b4553-110">La commande répertorie uniquement les éléments contenus directement, de manière très similaire à la commande **DIR** de Cmd.exe ou à la commande **ls** dans un interpréteur de commande UNIX.</span><span class="sxs-lookup"><span data-stu-id="b4553-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="b4553-111">Pour afficher les éléments contenus, vous devez également spécifier le paramètre **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="b4553-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="b4553-112">(Cela peut prendre beaucoup de temps.) Pour répertorier tout ce qui figure sur le lecteur C :</span><span class="sxs-lookup"><span data-stu-id="b4553-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="b4553-113">L’applet de commande **Get-ChildItem** peut filtrer les éléments avec ses paramètres **Path**, **Filter**, **Include** et **Exclude**, mais ceux-ci sont généralement basés uniquement sur le nom.</span><span class="sxs-lookup"><span data-stu-id="b4553-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="b4553-114">Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de l’applet de commande **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="b4553-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="b4553-115">La commande suivante recherche dans le dossier Program Files tous les exécutables modifiés après le 1er octobre 2005, dont la taille n’est pas inférieure à 1 Mo ou supérieure à 10 Mo :</span><span class="sxs-lookup"><span data-stu-id="b4553-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="b4553-116">Copie de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="b4553-116">Copying Files and Folders</span></span>

<span data-ttu-id="b4553-117">La copie s’effectue à l’aide de l’applet de commande **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="b4553-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="b4553-118">La commande suivante sauvegarde C:\\boot.ini dans C:\\boot.bak :</span><span class="sxs-lookup"><span data-stu-id="b4553-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="b4553-119">Si le fichier de destination existe déjà, la tentative de copie échoue.</span><span class="sxs-lookup"><span data-stu-id="b4553-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="b4553-120">Pour remplacer une destination existante, utilisez le paramètre **Force** :</span><span class="sxs-lookup"><span data-stu-id="b4553-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="b4553-121">Cette commande fonctionne même lorsque la destination est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b4553-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="b4553-122">La copie de dossier fonctionne de la même manière.</span><span class="sxs-lookup"><span data-stu-id="b4553-122">Folder copying works the same way.</span></span> <span data-ttu-id="b4553-123">Cette commande copie le dossier C:\\temp\\test1 vers le nouveau dossier C:\\temp\\DeleteMe de façon récursive :</span><span class="sxs-lookup"><span data-stu-id="b4553-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="b4553-124">Vous pouvez également copier une sélection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="b4553-124">You can also copy a selection of items.</span></span> <span data-ttu-id="b4553-125">La commande suivante copie tous les fichiers .txt contenus n’importe où dans C:\\data vers C:\\temp\\text :</span><span class="sxs-lookup"><span data-stu-id="b4553-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="b4553-126">Vous pouvez toujours utiliser d’autres outils pour effectuer des copies du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b4553-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="b4553-127">Les objets XCOPY, ROBOCOPY et COM, tels que **Scripting.FileSystemObject**, fonctionnent tous dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4553-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="b4553-128">Par exemple, vous pouvez utiliser la classe Windows Script Host **Scripting.FileSystem COM** pour sauvegarder C:\\boot.ini dans C:\\boot.bak :</span><span class="sxs-lookup"><span data-stu-id="b4553-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="b4553-129">Création de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="b4553-129">Creating Files and Folders</span></span>

<span data-ttu-id="b4553-130">La création de nouveaux éléments fonctionne de la même manière sur tous les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4553-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="b4553-131">Si un fournisseur Windows PowerShell a plus d’un type d’élément (par exemple, le fournisseur FileSystem de Windows PowerShell fait la distinction entre les répertoires et les fichiers), vous devez spécifier le type d’élément.</span><span class="sxs-lookup"><span data-stu-id="b4553-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="b4553-132">Cette commande crée un dossier C:\\temp\\New Folder :</span><span class="sxs-lookup"><span data-stu-id="b4553-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="b4553-133">Cette commande crée un fichier vide C:\\temp\\New Folder\\file.txt</span><span class="sxs-lookup"><span data-stu-id="b4553-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="b4553-134">Suppression de tous les fichiers et dossiers figurant dans un dossier</span><span class="sxs-lookup"><span data-stu-id="b4553-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="b4553-135">Vous pouvez supprimer des élément contenus à l’aide de l’applet de commande **Remove-Item**, mais vous devez confirmer la suppression si les éléments contiennent autre chose.</span><span class="sxs-lookup"><span data-stu-id="b4553-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="b4553-136">Par exemple, si vous tentez de supprimer le dossier C:\\temp\\DeleteMe contenant d’autres éléments, Windows PowerShell vous invite à confirmer la suppression :</span><span class="sxs-lookup"><span data-stu-id="b4553-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="b4553-137">Si vous ne souhaitez pas être invité à confirmer la suppression de chaque élément contenu, spécifiez le paramètre **Recurse**:</span><span class="sxs-lookup"><span data-stu-id="b4553-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="b4553-138">Mappage d’un dossier local en tant que lecteur Windows accessible</span><span class="sxs-lookup"><span data-stu-id="b4553-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="b4553-139">Vous pouvez également mapper un dossier local à l’aide de la commande **subst**.</span><span class="sxs-lookup"><span data-stu-id="b4553-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="b4553-140">La commande suivante crée un lecteur local P:, dans la racine du répertoire Program Files local :</span><span class="sxs-lookup"><span data-stu-id="b4553-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="b4553-141">Comme les lecteurs réseau, les lecteurs mappés à l’intérieur de Windows PowerShell avec la commande **subst** sont immédiatement visibles pour l’interpréteur de commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4553-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="b4553-142">Lecture d’un fichier texte dans un tableau</span><span class="sxs-lookup"><span data-stu-id="b4553-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="b4553-143">L’un des formats de stockage courants pour les données de texte est celui d’un fichier contenant des lignes séparées traitées en tant qu’éléments de données distincts.</span><span class="sxs-lookup"><span data-stu-id="b4553-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="b4553-144">L’applet de commande **Get-Content** permet de lire un fichier entier en une seule étape, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="b4553-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="b4553-145">L’applet de commande **Get-Content** traite déjà les données lues à partir du fichier en tant que tableau, avec un élément par ligne de contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="b4553-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="b4553-146">Vous pouvez vous en assurer en vérifiant la longueur (**longueur**) du contenu retourné :</span><span class="sxs-lookup"><span data-stu-id="b4553-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="b4553-147">Cette commande est particulièrement utile pour obtenir des listes d’informations directement dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4553-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="b4553-148">Par exemple, vous pouvez stocker une liste de noms d’ordinateur ou d’adresses IP dans un fichier C:\\temp\\domainMembers.txt, avec un nom sur chaque ligne du fichier.</span><span class="sxs-lookup"><span data-stu-id="b4553-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="b4553-149">Vous pouvez utiliser l’applet de commande **Get-Content** pour récupérer le contenu du fichier et le placer dans la variable **$Computers** :</span><span class="sxs-lookup"><span data-stu-id="b4553-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="b4553-150">La variable **$Computers** est désormais un tableau contenant un nom d’ordinateur dans chaque élément.</span><span class="sxs-lookup"><span data-stu-id="b4553-150">**$Computers** is now an array containing a computer name in each element.</span></span>
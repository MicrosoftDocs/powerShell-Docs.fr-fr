---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de fichiers et dossiers
description: Cet article explique comment effectuer certaines tâches de manipulation de fichiers et de dossiers à l’aide de PowerShell.
ms.openlocfilehash: c0c3abb082b05296daa480ac06bcbfa3a784e0c9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500026"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="4d806-104">Utilisation de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="4d806-104">Working with Files and Folders</span></span>

<span data-ttu-id="4d806-105">La navigation dans des lecteurs Windows PowerShell et la manipulation des éléments qu’ils contiennent sont similaires à la manipulation de fichiers et dossiers sur des lecteurs de disques physiques Windows.</span><span class="sxs-lookup"><span data-stu-id="4d806-105">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="4d806-106">Cet article explique comment effectuer certaines tâches de manipulation de fichiers et de dossiers à l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d806-106">This article discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="4d806-107">Affichage de la liste de tous les fichiers et dossiers figurant dans un dossier</span><span class="sxs-lookup"><span data-stu-id="4d806-107">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="4d806-108">Vous pouvez obtenir tous les éléments figurant directement dans un dossier à l’aide de `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="4d806-108">You can get all items directly within a folder by using `Get-ChildItem`.</span></span> <span data-ttu-id="4d806-109">Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force** .</span><span class="sxs-lookup"><span data-stu-id="4d806-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="4d806-110">Par exemple, cette commande affiche le contenu direct du lecteur C de Windows PowerShell (qui est le même que le lecteur physique C de Windows) :</span><span class="sxs-lookup"><span data-stu-id="4d806-110">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="4d806-111">La commande répertorie uniquement les éléments contenus directement, de manière très similaire à la commande `DIR` de `Cmd.exe` ou à `ls` dans un interpréteur de commande UNIX.</span><span class="sxs-lookup"><span data-stu-id="4d806-111">The command lists only the directly contained items, much like using `Cmd.exe`'s `DIR` command or `ls` in a UNIX shell.</span></span> <span data-ttu-id="4d806-112">Pour afficher les éléments contenus, vous devez également spécifier le paramètre `-Recurse`.</span><span class="sxs-lookup"><span data-stu-id="4d806-112">In order to show contained items, you need to specify the `-Recurse` parameter as well.</span></span> <span data-ttu-id="4d806-113">(Cela peut prendre beaucoup de temps.) Pour répertorier tout ce qui figure sur le lecteur C :</span><span class="sxs-lookup"><span data-stu-id="4d806-113">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="4d806-114">`Get-ChildItem` peut filtrer les éléments avec ses paramètres **Path** , **Filter** , **Include** et **Exclude** , mais ceux-ci sont généralement basés uniquement sur le nom.</span><span class="sxs-lookup"><span data-stu-id="4d806-114">`Get-ChildItem` can filter items with its **Path** , **Filter** , **Include** , and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="4d806-115">Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="4d806-115">You can perform complex filtering based on other properties of items by using `Where-Object`.</span></span>

<span data-ttu-id="4d806-116">La commande suivante recherche dans le dossier Program Files tous les exécutables modifiés après le 1er octobre 2005, dont la taille n’est pas inférieure à 1 Mo ou supérieure à 10 Mo :</span><span class="sxs-lookup"><span data-stu-id="4d806-116">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="4d806-117">Copie de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="4d806-117">Copying Files and Folders</span></span>

<span data-ttu-id="4d806-118">La copie s’effectue avec `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="4d806-118">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="4d806-119">La commande suivante sauvegarde C:\\boot.ini dans C:\\boot.bak :</span><span class="sxs-lookup"><span data-stu-id="4d806-119">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="4d806-120">Si le fichier de destination existe déjà, la tentative de copie échoue.</span><span class="sxs-lookup"><span data-stu-id="4d806-120">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="4d806-121">Pour remplacer une destination existante, utilisez le paramètre **Force** :</span><span class="sxs-lookup"><span data-stu-id="4d806-121">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="4d806-122">Cette commande fonctionne même lorsque la destination est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="4d806-122">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="4d806-123">La copie de dossier fonctionne de la même manière.</span><span class="sxs-lookup"><span data-stu-id="4d806-123">Folder copying works the same way.</span></span> <span data-ttu-id="4d806-124">Cette commande copie le dossier `C:\temp\test1` dans le nouveau dossier `C:\temp\DeleteMe` de manière récursive :</span><span class="sxs-lookup"><span data-stu-id="4d806-124">This command copies the folder `C:\temp\test1` to the new folder `C:\temp\DeleteMe` recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="4d806-125">Vous pouvez également copier une sélection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="4d806-125">You can also copy a selection of items.</span></span> <span data-ttu-id="4d806-126">La commande suivante copie tous les fichiers .txt contenus n’importe où dans `C:\data` vers `C:\temp\text` :</span><span class="sxs-lookup"><span data-stu-id="4d806-126">The following command copies all .txt files contained anywhere in `C:\data` to `C:\temp\text`:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="4d806-127">Vous pouvez toujours utiliser d’autres outils pour effectuer des copies du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4d806-127">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="4d806-128">Les objets XCOPY, ROBOCOPY et COM, tels que **Scripting.FileSystemObject** , fonctionnent tous dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d806-128">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="4d806-129">Par exemple, vous pouvez utiliser la classe Windows Script Host **Scripting.FileSystem COM** pour sauvegarder `C:\boot.ini` dans `C:\boot.bak` :</span><span class="sxs-lookup"><span data-stu-id="4d806-129">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up `C:\boot.ini` to `C:\boot.bak`:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="4d806-130">Création de fichiers et dossiers</span><span class="sxs-lookup"><span data-stu-id="4d806-130">Creating Files and Folders</span></span>

<span data-ttu-id="4d806-131">La création de nouveaux éléments fonctionne de la même manière sur tous les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d806-131">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="4d806-132">Si un fournisseur Windows PowerShell a plus d’un type d’élément (par exemple, le fournisseur FileSystem de Windows PowerShell fait la distinction entre les répertoires et les fichiers), vous devez spécifier le type d’élément.</span><span class="sxs-lookup"><span data-stu-id="4d806-132">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="4d806-133">Cette commande crée un nouveau dossier `C:\temp\New Folder` :</span><span class="sxs-lookup"><span data-stu-id="4d806-133">This command creates a new folder `C:\temp\New Folder`:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="4d806-134">Cette commande crée un nouveau fichier vide `C:\temp\New Folder\file.txt`</span><span class="sxs-lookup"><span data-stu-id="4d806-134">This command creates a new empty file `C:\temp\New Folder\file.txt`</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> <span data-ttu-id="4d806-135">Lorsque vous utilisez le commutateur **Force** avec la commande `New-Item` pour créer un dossier et que le dossier existe déjà, cela n’écrase ou ne remplace _pas_ le dossier.</span><span class="sxs-lookup"><span data-stu-id="4d806-135">When using the **Force** switch with the `New-Item` command to create a folder, and the folder already exists, it _won't_ overwrite or replace the folder.</span></span> <span data-ttu-id="4d806-136">L’objet de dossier existant est simplement retourné.</span><span class="sxs-lookup"><span data-stu-id="4d806-136">It will simply return the existing folder object.</span></span> <span data-ttu-id="4d806-137">Toutefois, si vous utilisez `New-Item -Force` sur un fichier qui existe déjà, le fichier _est_ entièrement remplacé.</span><span class="sxs-lookup"><span data-stu-id="4d806-137">However, if you use `New-Item -Force` on a file that already exists, the file _will_ be completely overwritten.</span></span>

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="4d806-138">Suppression de tous les fichiers et dossiers figurant dans un dossier</span><span class="sxs-lookup"><span data-stu-id="4d806-138">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="4d806-139">Vous pouvez supprimer des éléments contenus à l’aide de `Remove-Item`, mais vous devez confirmer la suppression si les éléments contiennent autre chose.</span><span class="sxs-lookup"><span data-stu-id="4d806-139">You can remove contained items using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="4d806-140">Par exemple, si vous tentez de supprimer le dossier `C:\temp\DeleteMe` contenant d’autres éléments, Windows PowerShell vous invite à confirmer la suppression :</span><span class="sxs-lookup"><span data-stu-id="4d806-140">For example, if you attempt to delete the folder `C:\temp\DeleteMe` that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="4d806-141">Si vous ne souhaitez pas être invité à confirmer la suppression de chaque élément contenu, spécifiez le paramètre **Recurse** :</span><span class="sxs-lookup"><span data-stu-id="4d806-141">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="4d806-142">Mappage d’un dossier local en tant que lecteur</span><span class="sxs-lookup"><span data-stu-id="4d806-142">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="4d806-143">Vous pouvez également mapper un dossier local à l’aide de la commande `New-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="4d806-143">You can also map a local folder, using the `New-PSDrive` command.</span></span> <span data-ttu-id="4d806-144">La commande suivante crée un lecteur local `P:` dans la racine du répertoire Program Files local, visible uniquement à partir de la session PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4d806-144">The following command creates a local drive `P:` rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="4d806-145">Comme les lecteurs réseau, les lecteurs mappés à l’intérieur de Windows PowerShell sont immédiatement visibles pour l’interpréteur de commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d806-145">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span> <span data-ttu-id="4d806-146">Pour créer un lecteur mappé visible à partir de l’Explorateur de fichiers, le paramètre `-Persist` est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="4d806-146">In order to create a mapped drive visible from File Explorer, the parameter `-Persist` is needed.</span></span> <span data-ttu-id="4d806-147">Toutefois, seuls les chemins d’accès distants peuvent être utilisés avec Persist.</span><span class="sxs-lookup"><span data-stu-id="4d806-147">However, only remote paths can be used with Persist.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="4d806-148">Lecture d’un fichier texte dans un tableau</span><span class="sxs-lookup"><span data-stu-id="4d806-148">Reading a Text File into an Array</span></span>

<span data-ttu-id="4d806-149">L’un des formats de stockage courants pour les données de texte est celui d’un fichier contenant des lignes séparées traitées en tant qu’éléments de données distincts.</span><span class="sxs-lookup"><span data-stu-id="4d806-149">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="4d806-150">La cmdlet `Get-Content` permet de lire un fichier entier en une seule étape, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="4d806-150">The `Get-Content` cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="4d806-151">`Get-Content` traite déjà les données lues à partir du fichier en tant que tableau, avec un élément par ligne de contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="4d806-151">`Get-Content` already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="4d806-152">Vous pouvez vous en assurer en vérifiant la longueur ( **longueur** ) du contenu retourné :</span><span class="sxs-lookup"><span data-stu-id="4d806-152">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="4d806-153">Cette commande est particulièrement utile pour obtenir des listes d’informations directement dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d806-153">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="4d806-154">Par exemple, vous pouvez stocker une liste de noms d’ordinateur ou d’adresses IP dans un fichier `C:\temp\domainMembers.txt`, avec un nom sur chaque ligne du fichier.</span><span class="sxs-lookup"><span data-stu-id="4d806-154">For example, you might store a list of computer names or IP addresses in a file `C:\temp\domainMembers.txt`, with one name on each line of the file.</span></span> <span data-ttu-id="4d806-155">Vous pouvez utiliser `Get-Content` pour récupérer le contenu du fichier et le placer dans la variable `$Computers` :</span><span class="sxs-lookup"><span data-stu-id="4d806-155">You can use `Get-Content` to retrieve the file contents and put them in the variable `$Computers`:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="4d806-156">`$Computers` est désormais un tableau contenant un nom d’ordinateur dans chaque élément.</span><span class="sxs-lookup"><span data-stu-id="4d806-156">`$Computers` is now an array containing a computer name in each element.</span></span>

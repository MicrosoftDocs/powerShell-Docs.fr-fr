---
description: FileSystem
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur FileSystem
ms.openlocfilehash: 8407dd11c3c9ead10b081b937fbac3db82735eb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206761"
---
# <a name="filesystem-provider"></a><span data-ttu-id="4c9b6-104">Fournisseur FileSystem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="4c9b6-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="4c9b6-105">Provider name</span></span>
<span data-ttu-id="4c9b6-106">FileSystem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="4c9b6-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="4c9b6-107">Drives</span></span>

<span data-ttu-id="4c9b6-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="4c9b6-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="4c9b6-109">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="4c9b6-109">Capabilities</span></span>

<span data-ttu-id="4c9b6-110">**Filtre** , **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-110">**Filter** , **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="4c9b6-111">Description courte</span><span class="sxs-lookup"><span data-stu-id="4c9b6-111">Short description</span></span>

<span data-ttu-id="4c9b6-112">Fournit l'accès aux fichiers et aux répertoires.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="4c9b6-113">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="4c9b6-113">Detailed description</span></span>

<span data-ttu-id="4c9b6-114">Le fournisseur **FileSystem** de PowerShell vous permet d’acquérir, d’ajouter, de modifier, d’effacer et de supprimer des fichiers et des répertoires dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="4c9b6-115">Les lecteurs de **système de fichiers** sont un espace de noms hiérarchique contenant les répertoires et les fichiers sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="4c9b6-116">Un lecteur de **système de fichiers** peut être un lecteur logique ou physiques, un répertoire ou un partage réseau mappé.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-116">A **FileSystem** drive can be a logical or phsyical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="4c9b6-117">Un lecteur appelé `TEMP:` est mappé au chemin d’accès du répertoire temporaire de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-117">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="4c9b6-118">Le contenu du lecteur TEMP : n’est pas automatiquement supprimé par PowerShell et revient à l’utilisateur ou au système d’exploitation à gérer.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-118">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span>

<span data-ttu-id="4c9b6-119">Le fournisseur **FileSystem** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-119">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="4c9b6-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="4c9b6-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="4c9b6-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="4c9b6-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="4c9b6-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="4c9b6-123">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-123">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="4c9b6-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-124">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="4c9b6-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-125">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="4c9b6-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-126">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="4c9b6-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-127">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="4c9b6-128">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4c9b6-128">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="4c9b6-129">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4c9b6-129">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="4c9b6-130">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-130">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="4c9b6-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4c9b6-131">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="4c9b6-132">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-132">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="4c9b6-133">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4c9b6-133">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="4c9b6-134">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="4c9b6-134">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="4c9b6-135">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="4c9b6-135">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="4c9b6-136">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="4c9b6-136">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="4c9b6-137">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="4c9b6-137">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="4c9b6-138">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="4c9b6-138">Types exposed by this provider</span></span>

<span data-ttu-id="4c9b6-139">Les fichiers sont des instances de la classe [System. IO. FileInfo](/dotnet/api/system.io.fileinfo) .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-139">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span>  <span data-ttu-id="4c9b6-140">Les répertoires sont des instances de la classe [System. IO. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-140">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="4c9b6-141">Navigation dans les lecteurs de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="4c9b6-141">Navigating the FileSystem drives</span></span>

<span data-ttu-id="4c9b6-142">Le fournisseur **FileSystem** expose ses magasins de données en mappant les lecteurs logiques de l’ordinateur en tant que lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-142">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="4c9b6-143">Pour utiliser un lecteur de **système de fichiers** , vous pouvez modifier votre emplacement sur un lecteur autorités le nom de lecteur suivi d’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-143">To work with a **FileSystem** drive you can change your location to a drive uing the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="4c9b6-144">Vous pouvez également utiliser le fournisseur **FileSystem** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-144">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="4c9b6-145">Pour faire référence à un fichier ou à un répertoire à partir d’un autre emplacement, utilisez le nom du lecteur ( `C:` , `D:` ,...) dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-145">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="4c9b6-146">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-146">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="4c9b6-147">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-147">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="4c9b6-148">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-148">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="4c9b6-149">Obtention de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-149">Getting files and directories</span></span>

<span data-ttu-id="4c9b6-150">L' `Get-ChildItem` applet de commande retourne tous les fichiers et répertoires à l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-150">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="4c9b6-151">Vous pouvez spécifier un autre chemin d’accès pour rechercher et utiliser des paramètres intégrés pour filtrer et contrôler la profondeur de récursivité.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-151">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="4c9b6-152">Pour en savoir plus sur l’utilisation des applets de commande, consultez la page [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-152">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="4c9b6-153">Copie de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-153">Copying files and directories</span></span>

<span data-ttu-id="4c9b6-154">L' `Copy-Item` applet de commande copie les fichiers et les répertoires vers un emplacement que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-154">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="4c9b6-155">Les paramètres sont disponibles pour filtrer et recurse, comme dans `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-155">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="4c9b6-156">La commande suivante copie tous les fichiers et répertoires sous le chemin d’accès « C:\temp \" dans le dossier «C:\Windows\Temp ».</span><span class="sxs-lookup"><span data-stu-id="4c9b6-156">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="4c9b6-157">`Copy-Item` remplace les fichiers dans le répertoire de destination sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-157">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="4c9b6-158">Cette commande copie le `a.txt` fichier du `C:\a` répertoire vers le `C:\a\bb` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-158">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="4c9b6-159">Copie tous les répertoires et fichiers du `C:\a` répertoire dans le `C:\c` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-159">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="4c9b6-160">Si un ou plusieurs des répertoires à copier existent déjà dans le répertoire de destination, la commande échoue, sauf si vous spécifiez le paramètre Force.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-160">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="4c9b6-161">Pour plus d’informations, consultez [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-161">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="4c9b6-162">Déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-162">Moving files and directories</span></span>

<span data-ttu-id="4c9b6-163">Cette commande déplace le `c.txt` fichier du `C:\a` répertoire vers le `C:\a\aa` répertoire :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-163">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="4c9b6-164">La commande ne remplacera pas automatiquement un fichier existant qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-164">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="4c9b6-165">Pour forcer l'applet de commande à remplacer un fichier existant, spécifiez le paramètre Force.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-165">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="4c9b6-166">Vous ne pouvez pas déplacer un répertoire quand ce répertoire est l'emplacement actif.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-166">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="4c9b6-167">Lorsque vous utilisez `Move-Item` pour déplacer le répertoire à l’emplacement actuel, vous voyez cette erreur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-167">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="4c9b6-168">Gestion du contenu des fichiers</span><span class="sxs-lookup"><span data-stu-id="4c9b6-168">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="4c9b6-169">Obtenir le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-169">Get the content of a file</span></span>

<span data-ttu-id="4c9b6-170">Cette commande obtient le contenu du fichier « Test.txt » et les affiche dans la console.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-170">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="4c9b6-171">Vous pouvez diriger le contenu du fichier vers une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-171">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="4c9b6-172">Par exemple, la commande suivante lit le contenu du `Test.txt` fichier, puis les fournit comme entrée à l’applet de commande [ConvertTo-HTML](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-172">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="4c9b6-173">Vous pouvez également récupérer le contenu d’un fichier en préfixant son chemin d’accès de fournisseur avec le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-173">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="4c9b6-174">Le chemin d’accès doit être placé entre accolades en raison de restrictions de nom de variable.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-174">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="4c9b6-175">Pour plus d’informations, consultez [about_Variables](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-175">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="4c9b6-176">Ajouter du contenu à un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-176">Add content to a file</span></span>

<span data-ttu-id="4c9b6-177">Cette commande ajoute la chaîne « test content » au `Test.txt` fichier :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-177">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="4c9b6-178">Le contenu existant dans le `Test.txt` fichier n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-178">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="4c9b6-179">Remplacer le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-179">Replace the content of a file</span></span>

<span data-ttu-id="4c9b6-180">Cette commande remplace le contenu du `Test.txt` fichier par la chaîne « test content » :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-180">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="4c9b6-181">Elle remplace le contenu de `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-181">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="4c9b6-182">Vous pouvez utiliser le paramètre **value** de l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour ajouter du contenu à un fichier lorsque vous le créez.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-182">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="4c9b6-183">Parcourir le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-183">Loop through the contents of a file</span></span>

<span data-ttu-id="4c9b6-184">Par défaut, l' `Get-Content` applet de commande utilise le caractère de fin de ligne comme délimiteur, de sorte qu’elle obtient un fichier sous la forme d’une collection de chaînes, chaque ligne étant une chaîne dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-184">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="4c9b6-185">Vous pouvez utiliser le `-Delimiter` paramètre pour spécifier un autre délimiteur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-185">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="4c9b6-186">Si vous choisissez pour ce paramètre les caractères qui indiquent la fin d'une section ou le début de la section suivante, vous pouvez fractionner le fichier en parties logiques.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-186">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="4c9b6-187">La première commande obtient le `Employees.txt` fichier et le fractionne en sections, chacune d’elles se terminant par les mots « end of Employee record » et l’enregistre dans la `$e` variable.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-187">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="4c9b6-188">La deuxième commande utilise la notation de tableau pour récupérer le premier élément de la collection dans `$e` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-188">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="4c9b6-189">Elle utilise un index de 0, car les tableaux PowerShell sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-189">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="4c9b6-190">Pour plus d’informations sur `Get-Content` l’applet de commande, consultez la rubrique d’aide relative à la commande [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-190">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="4c9b6-191">Pour plus d’informations sur les tableaux, consultez [about_Arrays](../About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-191">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="4c9b6-192">Gestion des descripteurs de sécurité</span><span class="sxs-lookup"><span data-stu-id="4c9b6-192">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="4c9b6-193">Afficher la liste de contrôle d’accès pour un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-193">View the ACL for a file</span></span>

<span data-ttu-id="4c9b6-194">Cette commande retourne un objet [System. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-194">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="4c9b6-195">Pour plus d’informations sur cet objet, dirigez la commande vers l’applet de commande d' [extraction de membre](xref:Microsoft.PowerShell.Utility.Get-Member) .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-195">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="4c9b6-196">Ou consultez « classe[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) » dans la bibliothèque MSDN (Microsoft Developer Network).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-196">Or, see "[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class" in the MSDN (Microsoft Developer Network) library.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="4c9b6-197">Modifier la liste de contrôle d’accès d’un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-197">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="4c9b6-198">Créer et définir une liste de contrôle d’accès pour un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-198">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="4c9b6-199">Création de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-199">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="4c9b6-200">Créer un répertoire</span><span class="sxs-lookup"><span data-stu-id="4c9b6-200">Create a directory</span></span>

<span data-ttu-id="4c9b6-201">Cette commande crée le `logfiles` répertoire sur le `C` lecteur :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-201">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="4c9b6-202">PowerShell comprend également une `mkdir` fonction (alias `md` ) qui utilise l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour créer un nouveau répertoire.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-202">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="4c9b6-203">Créer un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-203">Create a file</span></span>

<span data-ttu-id="4c9b6-204">Cette commande crée le `log2.txt` fichier dans le `C:\logfiles` répertoire, puis ajoute la chaîne « test log » au fichier :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-204">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="4c9b6-205">Créez un fichier avec du contenu</span><span class="sxs-lookup"><span data-stu-id="4c9b6-205">Create a file with content</span></span>

<span data-ttu-id="4c9b6-206">Crée un fichier appelé `log2.txt` dans le `C:\logfiles` répertoire et ajoute la chaîne « test log » au fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-206">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="4c9b6-207">Attribution d’un nouveau nom aux fichiers et répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-207">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="4c9b6-208">Renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-208">Rename a file</span></span>

<span data-ttu-id="4c9b6-209">Cette commande renomme le `a.txt` fichier dans le `C:\a` répertoire en `b.txt` :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-209">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="4c9b6-210">Renommer un répertoire</span><span class="sxs-lookup"><span data-stu-id="4c9b6-210">Rename a directory</span></span>

<span data-ttu-id="4c9b6-211">Cette commande renomme le `C:\a\cc` répertoire en `C:\a\dd` :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-211">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="4c9b6-212">Suppression de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4c9b6-212">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="4c9b6-213">Supprimer un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-213">Delete a file</span></span>

<span data-ttu-id="4c9b6-214">Cette commande supprime le `Test.txt` fichier dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-214">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="4c9b6-215">Supprimer des fichiers à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="4c9b6-215">Delete files using wildcards</span></span>

<span data-ttu-id="4c9b6-216">Cette commande supprime tous les fichiers du répertoire actif qui ont l’extension de `.xml` nom de fichier :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-216">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="4c9b6-217">Démarrage d’un programme en appelant un fichier associé</span><span class="sxs-lookup"><span data-stu-id="4c9b6-217">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="4c9b6-218">Appeler un fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-218">Invoke a file</span></span>

<span data-ttu-id="4c9b6-219">La première commande utilise l’applet de commande [obtenir-service](xref:Microsoft.PowerShell.Management.Get-Service) pour obtenir des informations sur les services locaux.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-219">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="4c9b6-220">Il dirige les informations vers l’applet de commande [Export-CSV](xref:Microsoft.PowerShell.Utility.Export-Csv) , puis stocke ces informations dans le `Services.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-220">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="4c9b6-221">La deuxième commande utilise [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) pour ouvrir le `services.csv` fichier dans le programme associé à l' `.csv` extension :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-221">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="4c9b6-222">Obtention de fichiers et de dossiers avec des attributs spécifiés</span><span class="sxs-lookup"><span data-stu-id="4c9b6-222">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="4c9b6-223">Récupération des fichiers système</span><span class="sxs-lookup"><span data-stu-id="4c9b6-223">Get System files</span></span>

<span data-ttu-id="4c9b6-224">Cette commande obtient les fichiers système du répertoire actif et de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-224">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="4c9b6-225">Elle utilise le `-File` paramètre pour récupérer uniquement des fichiers (et non des répertoires) et le `-System` paramètre pour récupérer uniquement les éléments avec l’attribut « System ».</span><span class="sxs-lookup"><span data-stu-id="4c9b6-225">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="4c9b6-226">Elle utilise le `-Recurse` paramètre pour récupérer les éléments dans le répertoire actif et tous les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-226">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="4c9b6-227">Récupérer les fichiers masqués</span><span class="sxs-lookup"><span data-stu-id="4c9b6-227">Get Hidden files</span></span>

<span data-ttu-id="4c9b6-228">Cette commande obtient tous les fichiers du répertoire actif, y compris les fichiers cachés.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-228">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="4c9b6-229">Elle utilise le paramètre **attributes** avec deux valeurs, `!Directory+Hidden` , qui obtient les fichiers masqués, et `!Directory` , qui obtient tous les autres fichiers.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-229">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="4c9b6-230">`dir -att !d,!d+h` est l’équivalent de cette commande.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-230">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="4c9b6-231">Recevoir des fichiers compressés et chiffrés</span><span class="sxs-lookup"><span data-stu-id="4c9b6-231">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="4c9b6-232">Cette commande obtient les fichiers du répertoire actif qui sont compressés ou chiffrés.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-232">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="4c9b6-233">Elle utilise le `-Attributes` paramètre avec deux valeurs, `Compressed` et `Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-233">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="4c9b6-234">Les valeurs sont séparées par une virgule `,` qui représente l’opérateur « or ».</span><span class="sxs-lookup"><span data-stu-id="4c9b6-234">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="4c9b6-235">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="4c9b6-235">Dynamic parameters</span></span>

<span data-ttu-id="4c9b6-236">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-236">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="4c9b6-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="4c9b6-238">Spécifie l'encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-238">Specifies the file encoding.</span></span> <span data-ttu-id="4c9b6-239">La valeur par défaut est ASCII.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-239">The default is ASCII.</span></span>

- <span data-ttu-id="4c9b6-240">**ASCII** : utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-240">**ASCII** :  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="4c9b6-241">**BigEndianUnicode** : encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-241">**BigEndianUnicode** :  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="4c9b6-242">**String** : utilise le type d’encodage pour une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-242">**String** :  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="4c9b6-243">**Unicode** : encode au format UTF-16 à l’aide de l’ordre d’octet avec primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-243">**Unicode** :  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="4c9b6-244">**UTF7** : encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-244">**UTF7** :   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="4c9b6-245">**UTF8** : encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-245">**UTF8** :  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="4c9b6-246">**UTF8BOM** : encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="4c9b6-246">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="4c9b6-247">**UF8NOBOM** : encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="4c9b6-247">**UF8NOBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="4c9b6-248">**UTF32** : encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-248">**UTF32** :  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="4c9b6-249">**Default** : encode dans la page de codes installée par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-249">**Default** : Encodes in the default installed code page.</span></span>
- <span data-ttu-id="4c9b6-250">**OEM** : utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-250">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="4c9b6-251">**Inconnu** : le type d’encodage est inconnu ou non valide.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-251">**Unknown** :  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="4c9b6-252">Les données peuvent être traitées sous forme binaire.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-252">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-253">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-253">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-254">Add-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-254">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="4c9b6-255">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-255">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="4c9b6-256">Set-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-256">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="4c9b6-257">Delimiter \<System.String\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-257">Delimiter \<System.String\></span></span>

<span data-ttu-id="4c9b6-258">Spécifie le délimiteur utilisé par [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) pour diviser le fichier en objets lors de la lecture.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-258">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="4c9b6-259">La valeur par défaut est `\n` , le caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-259">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="4c9b6-260">Lors de la lecture d’un fichier texte, la méthode [obten-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne une collection d’objets String, dont chacun se termine par le caractère délimiteur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-260">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="4c9b6-261">Si vous entrez un délimiteur qui n’existe pas dans le fichier, la fonctionnalité [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne l’intégralité du fichier sous la forme d’un objet unique, non délimité.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-261">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="4c9b6-262">Vous pouvez utiliser ce paramètre pour fractionner un fichier volumineux en fichiers plus petits, en spécifiant un séparateur de fichier comme « Fin de l'exemple » comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-262">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="4c9b6-263">Le délimiteur est conservé (il n'est pas supprimé) et devient le dernier élément de chaque section du fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-263">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="4c9b6-264">Actuellement, lorsque la valeur du `-Delimiter` paramètre est une chaîne vide, la valeur de l’opération [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-264">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="4c9b6-265">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-265">This is a known issue.</span></span> <span data-ttu-id="4c9b6-266">Pour forcer [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) à retourner la totalité du fichier sous la forme d'une seule chaîne non délimitée, entrez une valeur qui n'existe pas dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-266">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-267">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-267">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-268">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-268">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-269">Wait \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-269">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-270">Attend que le contenu soit ajouté au fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-270">Waits for content to be appended to the file.</span></span> <span data-ttu-id="4c9b6-271">Si le contenu est ajouté, il retourne le contenu ajouté.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-271">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="4c9b6-272">Si le contenu a changé, il retourne la totalité du fichier.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-272">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="4c9b6-273">Lors de l'attente, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) vérifie le fichier une fois par seconde jusqu'à ce que vous interrompiez l'attente, par exemple en appuyant sur Ctrl+C.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-273">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-274">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-274">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-275">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-275">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="4c9b6-276">Attributes \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-276">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="4c9b6-277">Obtient les fichiers et les dossiers avec les attributs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-277">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="4c9b6-278">Ce paramètre prend en charge tous les attributs et vous permet de spécifier des combinaisons complexes d'attributs.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-278">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="4c9b6-279">Le `-Attributes` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-279">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-280">Le `-Attributes` paramètre prend en charge les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-280">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="4c9b6-281">**Archive**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-281">**Archive**</span></span>
- <span data-ttu-id="4c9b6-282">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-282">**Compressed**</span></span>
- <span data-ttu-id="4c9b6-283">**Appareil**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-283">**Device**</span></span>
- <span data-ttu-id="4c9b6-284">**Directory**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-284">**Directory**</span></span>
- <span data-ttu-id="4c9b6-285">**Chiffré**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-285">**Encrypted**</span></span>
- <span data-ttu-id="4c9b6-286">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-286">**Hidden**</span></span>
- <span data-ttu-id="4c9b6-287">**Normal**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-287">**Normal**</span></span>
- <span data-ttu-id="4c9b6-288">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-288">**NotContentIndexed**</span></span>
- <span data-ttu-id="4c9b6-289">**Hors connexion**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-289">**Offline**</span></span>
- <span data-ttu-id="4c9b6-290">**Lecture seule**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-290">**ReadOnly**</span></span>
- <span data-ttu-id="4c9b6-291">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-291">**ReparsePoint**</span></span>
- <span data-ttu-id="4c9b6-292">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-292">**SparseFile**</span></span>
- <span data-ttu-id="4c9b6-293">**Système**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-293">**System**</span></span>
- <span data-ttu-id="4c9b6-294">**Temporaire**</span><span class="sxs-lookup"><span data-stu-id="4c9b6-294">**Temporary**</span></span>

<span data-ttu-id="4c9b6-295">Pour obtenir une description de ces attributs, consultez l’énumération [FileAttributes](/dotnet/api/system.io.fileattributes) .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-295">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="4c9b6-296">Utilisez les opérateurs suivants pour combiner des attributs.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-296">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="4c9b6-297">`!` -NON</span><span class="sxs-lookup"><span data-stu-id="4c9b6-297">`!` - NOT</span></span>
- <span data-ttu-id="4c9b6-298">`+` -ET</span><span class="sxs-lookup"><span data-stu-id="4c9b6-298">`+` - AND</span></span>
- <span data-ttu-id="4c9b6-299">`,` -OU</span><span class="sxs-lookup"><span data-stu-id="4c9b6-299">`,` - OR</span></span>

<span data-ttu-id="4c9b6-300">Les espaces ne sont pas autorisés entre un opérateur et son attribut.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-300">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="4c9b6-301">Les espaces sont cependant autorisés devant les virgules.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-301">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-302">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-302">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-303">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-303">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-304">Directory \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-304">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-305">Obtient les répertoires (dossiers).</span><span class="sxs-lookup"><span data-stu-id="4c9b6-305">Gets directories (folders).</span></span>

<span data-ttu-id="4c9b6-306">Le `-Directory` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-306">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-307">Pour accéder uniquement aux répertoires, utilisez le `-Directory` paramètre et omettez le `-File` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-307">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="4c9b6-308">Pour exclure des répertoires, utilisez le `-File` paramètre et omettez le `-Directory` paramètre, ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-308">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-309">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-309">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-310">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-310">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-311">File \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-311">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-312">Obtient les fichiers.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-312">Gets files.</span></span>

<span data-ttu-id="4c9b6-313">Le `-File` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-313">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-314">Pour récupérer uniquement des fichiers, utilisez le `-File` paramètre et omettez le `-Directory` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-314">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="4c9b6-315">Pour exclure des fichiers, utilisez le `-Directory` paramètre et omettez le paramètre `-File` , ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-315">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-316">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-316">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-317">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-317">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-318">Hidden \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-318">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-319">Obtient uniquement les fichiers et les répertoires (dossiers) cachés.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-319">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="4c9b6-320">Par défaut, l’option [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) obtient uniquement les éléments non masqués.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-320">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="4c9b6-321">Le `-Hidden` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-321">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-322">Pour récupérer uniquement les éléments masqués, utilisez le `-Hidden` paramètre, ses `h` `ah` alias ou, ou la valeur **masquée** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-322">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="4c9b6-323">Pour exclure les éléments masqués, omettez le `-Hidden` paramètre ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-323">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-324">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-324">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-327">Obtient uniquement les fichiers et les répertoires (dossiers) en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-327">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="4c9b6-328">Le `-ReadOnly` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-328">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-329">Pour obtenir uniquement les éléments en lecture seule, utilisez le `-ReadOnly` paramètre, son `ar` alias ou la valeur **ReadOnly** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-329">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="4c9b6-330">Pour exclure les éléments en lecture seule, utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-330">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-331">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-331">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-332">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-332">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="4c9b6-333">System \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-333">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-334">Obtient uniquement les fichiers et les répertoires (dossiers) système.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-334">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="4c9b6-335">Le `-System` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-335">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4c9b6-336">Pour récupérer uniquement les fichiers et dossiers système, utilisez le `-System` paramètre, son `as` alias ou la valeur **système** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-336">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="4c9b6-337">Pour exclure des fichiers et des dossiers système, utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-337">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-338">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-338">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-339">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4c9b6-339">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="4c9b6-340">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-340">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="4c9b6-341">Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est supérieure à la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-341">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="4c9b6-342">Sinon, il retourne `$False`.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-342">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="4c9b6-343">Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-343">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-344">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-344">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-345">Test-Path</span><span class="sxs-lookup"><span data-stu-id="4c9b6-345">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="4c9b6-346">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-346">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="4c9b6-347">Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est inférieure à la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-347">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="4c9b6-348">Sinon, il retourne `$False`.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-348">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="4c9b6-349">Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="4c9b6-349">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-350">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-350">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-351">Test-Path</span><span class="sxs-lookup"><span data-stu-id="4c9b6-351">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="4c9b6-352">Stream \<System.String\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-352">Stream \<System.String\></span></span>

<span data-ttu-id="4c9b6-353">Gère les flux de données alternatifs.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-353">Manages alternate data streams.</span></span> <span data-ttu-id="4c9b6-354">Entrez le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-354">Enter the stream name.</span></span> <span data-ttu-id="4c9b6-355">Les caractères génériques sont autorisés uniquement dans les commandes [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item) pour et [supprimer un élément](xref:Microsoft.PowerShell.Management.Remove-Item) dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-355">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-356">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-356">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-357">Add-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-357">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="4c9b6-358">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-358">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="4c9b6-359">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-359">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="4c9b6-360">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-360">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="4c9b6-361">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-361">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="4c9b6-362">Set-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-362">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="4c9b6-363">Raw \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-363">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="4c9b6-364">Ignore les caractères de nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-364">Ignores newline characters.</span></span> <span data-ttu-id="4c9b6-365">Retourne le contenu sous la forme d'un seul élément.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-365">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-366">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-366">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-367">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4c9b6-367">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="4c9b6-368">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="4c9b6-368">ItemType \<String\></span></span>

<span data-ttu-id="4c9b6-369">Ce paramètre vous permet de spécifier le Tye d’élément à créer avec `New-Item`</span><span class="sxs-lookup"><span data-stu-id="4c9b6-369">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="4c9b6-370">Les valeurs disponibles de ce paramètre dépendent du fournisseur actuel que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-370">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="4c9b6-371">Dans un `FileSystem` lecteur, les valeurs suivantes sont autorisées :</span><span class="sxs-lookup"><span data-stu-id="4c9b6-371">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="4c9b6-372">Fichier</span><span class="sxs-lookup"><span data-stu-id="4c9b6-372">File</span></span>
- <span data-ttu-id="4c9b6-373">Répertoire</span><span class="sxs-lookup"><span data-stu-id="4c9b6-373">Directory</span></span>
- <span data-ttu-id="4c9b6-374">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="4c9b6-374">SymbolicLink</span></span>
- <span data-ttu-id="4c9b6-375">jonction</span><span class="sxs-lookup"><span data-stu-id="4c9b6-375">Junction</span></span>
- <span data-ttu-id="4c9b6-376">HardLink</span><span class="sxs-lookup"><span data-stu-id="4c9b6-376">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="4c9b6-377">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="4c9b6-377">Cmdlets supported</span></span>

- [<span data-ttu-id="4c9b6-378">New-Item</span><span class="sxs-lookup"><span data-stu-id="4c9b6-378">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="4c9b6-379">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="4c9b6-379">Using the pipeline</span></span>

<span data-ttu-id="4c9b6-380">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-380">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="4c9b6-381">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-381">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="4c9b6-382">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-382">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="4c9b6-383">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="4c9b6-383">Getting help</span></span>

<span data-ttu-id="4c9b6-384">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-384">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="4c9b6-385">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4c9b6-385">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="4c9b6-386">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c9b6-386">See also</span></span>

[<span data-ttu-id="4c9b6-387">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4c9b6-387">about_Providers</span></span>](../About/about_Providers.md)


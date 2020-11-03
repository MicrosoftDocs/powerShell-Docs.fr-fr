---
description: FileSystem
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur FileSystem
ms.openlocfilehash: 24c30e311ba43842e759e884424ce3abfb92aae7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207118"
---
# <a name="filesystem-provider"></a><span data-ttu-id="248ce-104">Fournisseur FileSystem</span><span class="sxs-lookup"><span data-stu-id="248ce-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="248ce-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="248ce-105">Provider name</span></span>
<span data-ttu-id="248ce-106">FileSystem</span><span class="sxs-lookup"><span data-stu-id="248ce-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="248ce-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="248ce-107">Drives</span></span>

<span data-ttu-id="248ce-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="248ce-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="248ce-109">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="248ce-109">Capabilities</span></span>

<span data-ttu-id="248ce-110">**Filtre** , **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="248ce-110">**Filter** , **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="248ce-111">Description courte</span><span class="sxs-lookup"><span data-stu-id="248ce-111">Short description</span></span>

<span data-ttu-id="248ce-112">Fournit l'accès aux fichiers et aux répertoires.</span><span class="sxs-lookup"><span data-stu-id="248ce-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="248ce-113">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="248ce-113">Detailed description</span></span>

<span data-ttu-id="248ce-114">Le fournisseur **FileSystem** de PowerShell vous permet d’acquérir, d’ajouter, de modifier, d’effacer et de supprimer des fichiers et des répertoires dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="248ce-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="248ce-115">Les lecteurs de **système de fichiers** sont un espace de noms hiérarchique contenant les répertoires et les fichiers sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="248ce-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="248ce-116">Un lecteur de **système de fichiers** peut être un lecteur logique ou physiques, un répertoire ou un partage réseau mappé.</span><span class="sxs-lookup"><span data-stu-id="248ce-116">A **FileSystem** drive can be a logical or phsyical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="248ce-117">Le fournisseur **FileSystem** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="248ce-117">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="248ce-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="248ce-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="248ce-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="248ce-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="248ce-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="248ce-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="248ce-122">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="248ce-123">Move-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="248ce-124">New-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="248ce-125">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="248ce-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="248ce-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="248ce-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="248ce-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="248ce-128">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-128">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="248ce-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="248ce-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="248ce-130">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-130">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="248ce-131">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="248ce-131">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="248ce-132">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="248ce-132">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="248ce-133">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="248ce-133">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="248ce-134">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="248ce-134">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="248ce-135">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="248ce-135">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="248ce-136">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="248ce-136">Types exposed by this provider</span></span>

<span data-ttu-id="248ce-137">Les fichiers sont des instances de la classe [System. IO. FileInfo](/dotnet/api/system.io.fileinfo) .</span><span class="sxs-lookup"><span data-stu-id="248ce-137">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span>  <span data-ttu-id="248ce-138">Les répertoires sont des instances de la classe [System. IO. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="248ce-138">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="248ce-139">Navigation dans les lecteurs de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="248ce-139">Navigating the FileSystem drives</span></span>

<span data-ttu-id="248ce-140">Le fournisseur **FileSystem** expose ses magasins de données en mappant les lecteurs logiques de l’ordinateur en tant que lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="248ce-140">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="248ce-141">Pour utiliser un lecteur de **système de fichiers** , vous pouvez modifier votre emplacement sur un lecteur autorités le nom de lecteur suivi d’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="248ce-141">To work with a **FileSystem** drive you can change your location to a drive uing the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="248ce-142">Vous pouvez également utiliser le fournisseur **FileSystem** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="248ce-142">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="248ce-143">Pour faire référence à un fichier ou à un répertoire à partir d’un autre emplacement, utilisez le nom du lecteur ( `C:` , `D:` ,...) dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="248ce-143">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="248ce-144">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="248ce-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="248ce-145">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="248ce-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="248ce-146">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="248ce-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="248ce-147">Obtention de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-147">Getting files and directories</span></span>

<span data-ttu-id="248ce-148">L' `Get-ChildItem` applet de commande retourne tous les fichiers et répertoires à l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="248ce-148">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="248ce-149">Vous pouvez spécifier un autre chemin d’accès pour rechercher et utiliser des paramètres intégrés pour filtrer et contrôler la profondeur de récursivité.</span><span class="sxs-lookup"><span data-stu-id="248ce-149">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="248ce-150">Pour en savoir plus sur l’utilisation des applets de commande, consultez la page [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span><span class="sxs-lookup"><span data-stu-id="248ce-150">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="248ce-151">Copie de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-151">Copying files and directories</span></span>

<span data-ttu-id="248ce-152">L' `Copy-Item` applet de commande copie les fichiers et les répertoires vers un emplacement que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="248ce-152">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="248ce-153">Les paramètres sont disponibles pour filtrer et recurse, comme dans `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="248ce-153">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="248ce-154">La commande suivante copie tous les fichiers et répertoires sous le chemin d’accès « C:\temp \" dans le dossier «C:\Windows\Temp ».</span><span class="sxs-lookup"><span data-stu-id="248ce-154">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="248ce-155">`Copy-Item` remplace les fichiers dans le répertoire de destination sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="248ce-155">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="248ce-156">Cette commande copie le `a.txt` fichier du `C:\a` répertoire vers le `C:\a\bb` répertoire.</span><span class="sxs-lookup"><span data-stu-id="248ce-156">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="248ce-157">Copie tous les répertoires et fichiers du `C:\a` répertoire dans le `C:\c` répertoire.</span><span class="sxs-lookup"><span data-stu-id="248ce-157">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="248ce-158">Si un ou plusieurs des répertoires à copier existent déjà dans le répertoire de destination, la commande échoue, sauf si vous spécifiez le paramètre Force.</span><span class="sxs-lookup"><span data-stu-id="248ce-158">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="248ce-159">Pour plus d’informations, consultez [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span><span class="sxs-lookup"><span data-stu-id="248ce-159">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="248ce-160">Déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-160">Moving files and directories</span></span>

<span data-ttu-id="248ce-161">Cette commande déplace le `c.txt` fichier du `C:\a` répertoire vers le `C:\a\aa` répertoire :</span><span class="sxs-lookup"><span data-stu-id="248ce-161">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="248ce-162">La commande ne remplacera pas automatiquement un fichier existant qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="248ce-162">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="248ce-163">Pour forcer l'applet de commande à remplacer un fichier existant, spécifiez le paramètre Force.</span><span class="sxs-lookup"><span data-stu-id="248ce-163">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="248ce-164">Vous ne pouvez pas déplacer un répertoire quand ce répertoire est l'emplacement actif.</span><span class="sxs-lookup"><span data-stu-id="248ce-164">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="248ce-165">Lorsque vous utilisez `Move-Item` pour déplacer le répertoire à l’emplacement actuel, vous voyez cette erreur.</span><span class="sxs-lookup"><span data-stu-id="248ce-165">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="248ce-166">Gestion du contenu des fichiers</span><span class="sxs-lookup"><span data-stu-id="248ce-166">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="248ce-167">Obtenir le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-167">Get the content of a file</span></span>

<span data-ttu-id="248ce-168">Cette commande obtient le contenu du fichier « Test.txt » et les affiche dans la console.</span><span class="sxs-lookup"><span data-stu-id="248ce-168">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="248ce-169">Vous pouvez diriger le contenu du fichier vers une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="248ce-169">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="248ce-170">Par exemple, la commande suivante lit le contenu du `Test.txt` fichier, puis les fournit comme entrée à l’applet de commande [ConvertTo-HTML](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) :</span><span class="sxs-lookup"><span data-stu-id="248ce-170">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="248ce-171">Vous pouvez également récupérer le contenu d’un fichier en préfixant son chemin d’accès de fournisseur avec le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="248ce-171">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="248ce-172">Le chemin d’accès doit être placé entre accolades en raison de restrictions de nom de variable.</span><span class="sxs-lookup"><span data-stu-id="248ce-172">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="248ce-173">Pour plus d’informations, consultez [about_Variables](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="248ce-173">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="248ce-174">Ajouter du contenu à un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-174">Add content to a file</span></span>

<span data-ttu-id="248ce-175">Cette commande ajoute la chaîne « test content » au `Test.txt` fichier :</span><span class="sxs-lookup"><span data-stu-id="248ce-175">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="248ce-176">Le contenu existant dans le `Test.txt` fichier n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="248ce-176">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="248ce-177">Remplacer le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-177">Replace the content of a file</span></span>

<span data-ttu-id="248ce-178">Cette commande remplace le contenu du `Test.txt` fichier par la chaîne « test content » :</span><span class="sxs-lookup"><span data-stu-id="248ce-178">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="248ce-179">Elle remplace le contenu de `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="248ce-179">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="248ce-180">Vous pouvez utiliser le paramètre **value** de l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour ajouter du contenu à un fichier lorsque vous le créez.</span><span class="sxs-lookup"><span data-stu-id="248ce-180">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="248ce-181">Parcourir le contenu d’un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-181">Loop through the contents of a file</span></span>

<span data-ttu-id="248ce-182">Par défaut, l' `Get-Content` applet de commande utilise le caractère de fin de ligne comme délimiteur, de sorte qu’elle obtient un fichier sous la forme d’une collection de chaînes, chaque ligne étant une chaîne dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-182">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="248ce-183">Vous pouvez utiliser le `-Delimiter` paramètre pour spécifier un autre délimiteur.</span><span class="sxs-lookup"><span data-stu-id="248ce-183">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="248ce-184">Si vous choisissez pour ce paramètre les caractères qui indiquent la fin d'une section ou le début de la section suivante, vous pouvez fractionner le fichier en parties logiques.</span><span class="sxs-lookup"><span data-stu-id="248ce-184">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="248ce-185">La première commande obtient le `Employees.txt` fichier et le fractionne en sections, chacune d’elles se terminant par les mots « end of Employee record » et l’enregistre dans la `$e` variable.</span><span class="sxs-lookup"><span data-stu-id="248ce-185">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="248ce-186">La deuxième commande utilise la notation de tableau pour récupérer le premier élément de la collection dans `$e` .</span><span class="sxs-lookup"><span data-stu-id="248ce-186">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="248ce-187">Elle utilise un index de 0, car les tableaux PowerShell sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="248ce-187">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="248ce-188">Pour plus d’informations sur `Get-Content` l’applet de commande, consultez la rubrique d’aide relative à la commande [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content).</span><span class="sxs-lookup"><span data-stu-id="248ce-188">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="248ce-189">Pour plus d’informations sur les tableaux, consultez [about_Arrays](../About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="248ce-189">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="248ce-190">Gestion des descripteurs de sécurité</span><span class="sxs-lookup"><span data-stu-id="248ce-190">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="248ce-191">Afficher la liste de contrôle d’accès pour un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-191">View the ACL for a file</span></span>

<span data-ttu-id="248ce-192">Cette commande retourne un objet [System. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) :</span><span class="sxs-lookup"><span data-stu-id="248ce-192">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="248ce-193">Pour plus d’informations sur cet objet, dirigez la commande vers l’applet de commande d' [extraction de membre](xref:Microsoft.PowerShell.Utility.Get-Member) .</span><span class="sxs-lookup"><span data-stu-id="248ce-193">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="248ce-194">Ou consultez « classe[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) » dans la bibliothèque MSDN (Microsoft Developer Network).</span><span class="sxs-lookup"><span data-stu-id="248ce-194">Or, see "[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class" in the MSDN (Microsoft Developer Network) library.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="248ce-195">Modifier la liste de contrôle d’accès d’un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-195">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="248ce-196">Créer et définir une liste de contrôle d’accès pour un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-196">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="248ce-197">Création de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-197">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="248ce-198">Créer un répertoire</span><span class="sxs-lookup"><span data-stu-id="248ce-198">Create a directory</span></span>

<span data-ttu-id="248ce-199">Cette commande crée le `logfiles` répertoire sur le `C` lecteur :</span><span class="sxs-lookup"><span data-stu-id="248ce-199">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="248ce-200">PowerShell comprend également une `mkdir` fonction (alias `md` ) qui utilise l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour créer un nouveau répertoire.</span><span class="sxs-lookup"><span data-stu-id="248ce-200">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="248ce-201">Créer un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-201">Create a file</span></span>

<span data-ttu-id="248ce-202">Cette commande crée le `log2.txt` fichier dans le `C:\logfiles` répertoire, puis ajoute la chaîne « test log » au fichier :</span><span class="sxs-lookup"><span data-stu-id="248ce-202">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="248ce-203">Créez un fichier avec du contenu</span><span class="sxs-lookup"><span data-stu-id="248ce-203">Create a file with content</span></span>

<span data-ttu-id="248ce-204">Crée un fichier appelé `log2.txt` dans le `C:\logfiles` répertoire et ajoute la chaîne « test log » au fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-204">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="248ce-205">Attribution d’un nouveau nom aux fichiers et répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-205">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="248ce-206">Renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-206">Rename a file</span></span>

<span data-ttu-id="248ce-207">Cette commande renomme le `a.txt` fichier dans le `C:\a` répertoire en `b.txt` :</span><span class="sxs-lookup"><span data-stu-id="248ce-207">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="248ce-208">Renommer un répertoire</span><span class="sxs-lookup"><span data-stu-id="248ce-208">Rename a directory</span></span>

<span data-ttu-id="248ce-209">Cette commande renomme le `C:\a\cc` répertoire en `C:\a\dd` :</span><span class="sxs-lookup"><span data-stu-id="248ce-209">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="248ce-210">Suppression de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="248ce-210">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="248ce-211">Supprimer un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-211">Delete a file</span></span>

<span data-ttu-id="248ce-212">Cette commande supprime le `Test.txt` fichier dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="248ce-212">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="248ce-213">Supprimer des fichiers à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="248ce-213">Delete files using wildcards</span></span>

<span data-ttu-id="248ce-214">Cette commande supprime tous les fichiers du répertoire actif qui ont l’extension de `.xml` nom de fichier :</span><span class="sxs-lookup"><span data-stu-id="248ce-214">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="248ce-215">Démarrage d’un programme en appelant un fichier associé</span><span class="sxs-lookup"><span data-stu-id="248ce-215">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="248ce-216">Appeler un fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-216">Invoke a file</span></span>

<span data-ttu-id="248ce-217">La première commande utilise l’applet de commande [obtenir-service](xref:Microsoft.PowerShell.Management.Get-Service) pour obtenir des informations sur les services locaux.</span><span class="sxs-lookup"><span data-stu-id="248ce-217">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="248ce-218">Il dirige les informations vers l’applet de commande [Export-CSV](xref:Microsoft.PowerShell.Utility.Export-Csv) , puis stocke ces informations dans le `Services.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-218">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="248ce-219">La deuxième commande utilise [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) pour ouvrir le `services.csv` fichier dans le programme associé à l' `.csv` extension :</span><span class="sxs-lookup"><span data-stu-id="248ce-219">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="248ce-220">Obtention de fichiers et de dossiers avec des attributs spécifiés</span><span class="sxs-lookup"><span data-stu-id="248ce-220">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="248ce-221">Récupération des fichiers système</span><span class="sxs-lookup"><span data-stu-id="248ce-221">Get System files</span></span>

<span data-ttu-id="248ce-222">Cette commande obtient les fichiers système du répertoire actif et de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="248ce-222">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="248ce-223">Elle utilise le `-File` paramètre pour récupérer uniquement des fichiers (et non des répertoires) et le `-System` paramètre pour récupérer uniquement les éléments avec l’attribut « System ».</span><span class="sxs-lookup"><span data-stu-id="248ce-223">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="248ce-224">Elle utilise le `-Recurse` paramètre pour récupérer les éléments dans le répertoire actif et tous les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="248ce-224">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="248ce-225">Récupérer les fichiers masqués</span><span class="sxs-lookup"><span data-stu-id="248ce-225">Get Hidden files</span></span>

<span data-ttu-id="248ce-226">Cette commande obtient tous les fichiers du répertoire actif, y compris les fichiers cachés.</span><span class="sxs-lookup"><span data-stu-id="248ce-226">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="248ce-227">Elle utilise le paramètre **attributes** avec deux valeurs, `!Directory+Hidden` , qui obtient les fichiers masqués, et `!Directory` , qui obtient tous les autres fichiers.</span><span class="sxs-lookup"><span data-stu-id="248ce-227">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="248ce-228">`dir -att !d,!d+h` est l’équivalent de cette commande.</span><span class="sxs-lookup"><span data-stu-id="248ce-228">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="248ce-229">Recevoir des fichiers compressés et chiffrés</span><span class="sxs-lookup"><span data-stu-id="248ce-229">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="248ce-230">Cette commande obtient les fichiers du répertoire actif qui sont compressés ou chiffrés.</span><span class="sxs-lookup"><span data-stu-id="248ce-230">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="248ce-231">Elle utilise le `-Attributes` paramètre avec deux valeurs, `Compressed` et `Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="248ce-231">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="248ce-232">Les valeurs sont séparées par une virgule `,` qui représente l’opérateur « or ».</span><span class="sxs-lookup"><span data-stu-id="248ce-232">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="248ce-233">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="248ce-233">Dynamic parameters</span></span>

<span data-ttu-id="248ce-234">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="248ce-234">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="248ce-235">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="248ce-235">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="248ce-236">Spécifie l'encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-236">Specifies the file encoding.</span></span> <span data-ttu-id="248ce-237">La valeur par défaut est ASCII.</span><span class="sxs-lookup"><span data-stu-id="248ce-237">The default is ASCII.</span></span>

- <span data-ttu-id="248ce-238">**ASCII** : utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="248ce-238">**ASCII** :  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="248ce-239">**BigEndianUnicode** : encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="248ce-239">**BigEndianUnicode** :  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="248ce-240">**String** : utilise le type d’encodage pour une chaîne.</span><span class="sxs-lookup"><span data-stu-id="248ce-240">**String** :  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="248ce-241">**Unicode** : encode au format UTF-16 à l’aide de l’ordre d’octet avec primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="248ce-241">**Unicode** :  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="248ce-242">**UTF7** : encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="248ce-242">**UTF7** :   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="248ce-243">**UTF8** : encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="248ce-243">**UTF8** :  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="248ce-244">**UTF8BOM** : encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="248ce-244">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="248ce-245">**UF8NOBOM** : encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="248ce-245">**UF8NOBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="248ce-246">**UTF32** : encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="248ce-246">**UTF32** :  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="248ce-247">**Default** : encode dans la page de codes installée par défaut.</span><span class="sxs-lookup"><span data-stu-id="248ce-247">**Default** : Encodes in the default installed code page.</span></span>
- <span data-ttu-id="248ce-248">**OEM** : utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="248ce-248">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="248ce-249">**Inconnu** : le type d’encodage est inconnu ou non valide.</span><span class="sxs-lookup"><span data-stu-id="248ce-249">**Unknown** :  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="248ce-250">Les données peuvent être traitées sous forme binaire.</span><span class="sxs-lookup"><span data-stu-id="248ce-250">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-251">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-251">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-252">Add-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-252">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="248ce-253">Get-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-253">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="248ce-254">Set-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-254">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="248ce-255">Delimiter \<System.String\></span><span class="sxs-lookup"><span data-stu-id="248ce-255">Delimiter \<System.String\></span></span>

<span data-ttu-id="248ce-256">Spécifie le délimiteur utilisé par [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) pour diviser le fichier en objets lors de la lecture.</span><span class="sxs-lookup"><span data-stu-id="248ce-256">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="248ce-257">La valeur par défaut est `\n` , le caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="248ce-257">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="248ce-258">Lors de la lecture d’un fichier texte, la méthode [obten-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne une collection d’objets String, dont chacun se termine par le caractère délimiteur.</span><span class="sxs-lookup"><span data-stu-id="248ce-258">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="248ce-259">Si vous entrez un délimiteur qui n’existe pas dans le fichier, la fonctionnalité [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne l’intégralité du fichier sous la forme d’un objet unique, non délimité.</span><span class="sxs-lookup"><span data-stu-id="248ce-259">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="248ce-260">Vous pouvez utiliser ce paramètre pour fractionner un fichier volumineux en fichiers plus petits, en spécifiant un séparateur de fichier comme « Fin de l'exemple » comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="248ce-260">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="248ce-261">Le délimiteur est conservé (il n'est pas supprimé) et devient le dernier élément de chaque section du fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-261">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="248ce-262">Actuellement, lorsque la valeur du `-Delimiter` paramètre est une chaîne vide, la valeur de l’opération [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="248ce-262">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="248ce-263">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="248ce-263">This is a known issue.</span></span> <span data-ttu-id="248ce-264">Pour forcer [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) à retourner la totalité du fichier sous la forme d'une seule chaîne non délimitée, entrez une valeur qui n'existe pas dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-264">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-265">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-265">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-266">Get-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-266">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-267">Wait \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-267">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-268">Attend que le contenu soit ajouté au fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-268">Waits for content to be appended to the file.</span></span> <span data-ttu-id="248ce-269">Si le contenu est ajouté, il retourne le contenu ajouté.</span><span class="sxs-lookup"><span data-stu-id="248ce-269">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="248ce-270">Si le contenu a changé, il retourne la totalité du fichier.</span><span class="sxs-lookup"><span data-stu-id="248ce-270">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="248ce-271">Lors de l'attente, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) vérifie le fichier une fois par seconde jusqu'à ce que vous interrompiez l'attente, par exemple en appuyant sur Ctrl+C.</span><span class="sxs-lookup"><span data-stu-id="248ce-271">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-272">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-272">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-273">Get-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-273">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="248ce-274">Attributes \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="248ce-274">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="248ce-275">Obtient les fichiers et les dossiers avec les attributs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="248ce-275">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="248ce-276">Ce paramètre prend en charge tous les attributs et vous permet de spécifier des combinaisons complexes d'attributs.</span><span class="sxs-lookup"><span data-stu-id="248ce-276">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="248ce-277">Le `-Attributes` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-277">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-278">Le `-Attributes` paramètre prend en charge les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="248ce-278">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="248ce-279">**Archive**</span><span class="sxs-lookup"><span data-stu-id="248ce-279">**Archive**</span></span>
- <span data-ttu-id="248ce-280">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="248ce-280">**Compressed**</span></span>
- <span data-ttu-id="248ce-281">**Appareil**</span><span class="sxs-lookup"><span data-stu-id="248ce-281">**Device**</span></span>
- <span data-ttu-id="248ce-282">**Directory**</span><span class="sxs-lookup"><span data-stu-id="248ce-282">**Directory**</span></span>
- <span data-ttu-id="248ce-283">**Chiffré**</span><span class="sxs-lookup"><span data-stu-id="248ce-283">**Encrypted**</span></span>
- <span data-ttu-id="248ce-284">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="248ce-284">**Hidden**</span></span>
- <span data-ttu-id="248ce-285">**Normal**</span><span class="sxs-lookup"><span data-stu-id="248ce-285">**Normal**</span></span>
- <span data-ttu-id="248ce-286">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="248ce-286">**NotContentIndexed**</span></span>
- <span data-ttu-id="248ce-287">**Hors connexion**</span><span class="sxs-lookup"><span data-stu-id="248ce-287">**Offline**</span></span>
- <span data-ttu-id="248ce-288">**Lecture seule**</span><span class="sxs-lookup"><span data-stu-id="248ce-288">**ReadOnly**</span></span>
- <span data-ttu-id="248ce-289">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="248ce-289">**ReparsePoint**</span></span>
- <span data-ttu-id="248ce-290">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="248ce-290">**SparseFile**</span></span>
- <span data-ttu-id="248ce-291">**Système**</span><span class="sxs-lookup"><span data-stu-id="248ce-291">**System**</span></span>
- <span data-ttu-id="248ce-292">**Temporaire**</span><span class="sxs-lookup"><span data-stu-id="248ce-292">**Temporary**</span></span>

<span data-ttu-id="248ce-293">Pour obtenir une description de ces attributs, consultez l’énumération [FileAttributes](/dotnet/api/system.io.fileattributes) .</span><span class="sxs-lookup"><span data-stu-id="248ce-293">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="248ce-294">Utilisez les opérateurs suivants pour combiner des attributs.</span><span class="sxs-lookup"><span data-stu-id="248ce-294">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="248ce-295">`!` -NON</span><span class="sxs-lookup"><span data-stu-id="248ce-295">`!` - NOT</span></span>
- <span data-ttu-id="248ce-296">`+` -ET</span><span class="sxs-lookup"><span data-stu-id="248ce-296">`+` - AND</span></span>
- <span data-ttu-id="248ce-297">`,` -OU</span><span class="sxs-lookup"><span data-stu-id="248ce-297">`,` - OR</span></span>

<span data-ttu-id="248ce-298">Les espaces ne sont pas autorisés entre un opérateur et son attribut.</span><span class="sxs-lookup"><span data-stu-id="248ce-298">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="248ce-299">Les espaces sont cependant autorisés devant les virgules.</span><span class="sxs-lookup"><span data-stu-id="248ce-299">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-300">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-300">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-301">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-301">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-302">Directory \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-302">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-303">Obtient les répertoires (dossiers).</span><span class="sxs-lookup"><span data-stu-id="248ce-303">Gets directories (folders).</span></span>

<span data-ttu-id="248ce-304">Le `-Directory` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-304">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-305">Pour accéder uniquement aux répertoires, utilisez le `-Directory` paramètre et omettez le `-File` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-305">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="248ce-306">Pour exclure des répertoires, utilisez le `-File` paramètre et omettez le `-Directory` paramètre, ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-306">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-307">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-307">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-308">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-308">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-309">File \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-309">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-310">Obtient les fichiers.</span><span class="sxs-lookup"><span data-stu-id="248ce-310">Gets files.</span></span>

<span data-ttu-id="248ce-311">Le `-File` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-311">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-312">Pour récupérer uniquement des fichiers, utilisez le `-File` paramètre et omettez le `-Directory` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-312">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="248ce-313">Pour exclure des fichiers, utilisez le `-Directory` paramètre et omettez le paramètre `-File` , ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-313">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-314">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-314">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-315">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-315">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-316">Hidden \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-316">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-317">Obtient uniquement les fichiers et les répertoires (dossiers) cachés.</span><span class="sxs-lookup"><span data-stu-id="248ce-317">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="248ce-318">Par défaut, l’option [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) obtient uniquement les éléments non masqués.</span><span class="sxs-lookup"><span data-stu-id="248ce-318">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="248ce-319">Le `-Hidden` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-319">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-320">Pour récupérer uniquement les éléments masqués, utilisez le `-Hidden` paramètre, ses `h` `ah` alias ou, ou la valeur **masquée** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-320">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="248ce-321">Pour exclure les éléments masqués, omettez le `-Hidden` paramètre ou utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-321">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-322">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-322">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-323">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-323">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-324">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-324">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-325">Obtient uniquement les fichiers et les répertoires (dossiers) en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="248ce-325">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="248ce-326">Le `-ReadOnly` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-326">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-327">Pour obtenir uniquement les éléments en lecture seule, utilisez le `-ReadOnly` paramètre, son `ar` alias ou la valeur **ReadOnly** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-327">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="248ce-328">Pour exclure les éléments en lecture seule, utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-328">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-329">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-329">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-330">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-330">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="248ce-331">System \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-331">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="248ce-332">Obtient uniquement les fichiers et les répertoires (dossiers) système.</span><span class="sxs-lookup"><span data-stu-id="248ce-332">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="248ce-333">Le `-System` paramètre a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="248ce-333">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="248ce-334">Pour récupérer uniquement les fichiers et dossiers système, utilisez le `-System` paramètre, son `as` alias ou la valeur **système** du `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-334">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="248ce-335">Pour exclure des fichiers et des dossiers système, utilisez le `-Attributes` paramètre.</span><span class="sxs-lookup"><span data-stu-id="248ce-335">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-336">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-336">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-337">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="248ce-337">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="248ce-338">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="248ce-338">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="248ce-339">Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est supérieure à la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="248ce-339">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="248ce-340">Sinon, il retourne `$False`.</span><span class="sxs-lookup"><span data-stu-id="248ce-340">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="248ce-341">Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="248ce-341">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-342">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-342">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-343">Test-Path</span><span class="sxs-lookup"><span data-stu-id="248ce-343">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="248ce-344">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="248ce-344">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="248ce-345">Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est inférieure à la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="248ce-345">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="248ce-346">Sinon, il retourne `$False`.</span><span class="sxs-lookup"><span data-stu-id="248ce-346">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="248ce-347">Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="248ce-347">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-348">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-348">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-349">Test-Path</span><span class="sxs-lookup"><span data-stu-id="248ce-349">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="248ce-350">Stream \<System.String\></span><span class="sxs-lookup"><span data-stu-id="248ce-350">Stream \<System.String\></span></span>

<span data-ttu-id="248ce-351">Gère les flux de données alternatifs.</span><span class="sxs-lookup"><span data-stu-id="248ce-351">Manages alternate data streams.</span></span> <span data-ttu-id="248ce-352">Entrez le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="248ce-352">Enter the stream name.</span></span> <span data-ttu-id="248ce-353">Les caractères génériques sont autorisés uniquement dans les commandes [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item) pour et [supprimer un élément](xref:Microsoft.PowerShell.Management.Remove-Item) dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="248ce-353">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-354">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-354">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-355">Add-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-355">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="248ce-356">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-356">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="248ce-357">Get-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-357">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="248ce-358">Get-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-358">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="248ce-359">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-359">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="248ce-360">Set-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-360">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="248ce-361">Raw \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="248ce-361">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="248ce-362">Ignore les caractères de nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="248ce-362">Ignores newline characters.</span></span> <span data-ttu-id="248ce-363">Retourne le contenu sous la forme d'un seul élément.</span><span class="sxs-lookup"><span data-stu-id="248ce-363">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-364">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-364">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-365">Get-Content</span><span class="sxs-lookup"><span data-stu-id="248ce-365">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="248ce-366">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="248ce-366">ItemType \<String\></span></span>

<span data-ttu-id="248ce-367">Ce paramètre vous permet de spécifier le Tye d’élément à créer avec `New-Item`</span><span class="sxs-lookup"><span data-stu-id="248ce-367">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="248ce-368">Les valeurs disponibles de ce paramètre dépendent du fournisseur actuel que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="248ce-368">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="248ce-369">Dans un `FileSystem` lecteur, les valeurs suivantes sont autorisées :</span><span class="sxs-lookup"><span data-stu-id="248ce-369">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="248ce-370">Fichier</span><span class="sxs-lookup"><span data-stu-id="248ce-370">File</span></span>
- <span data-ttu-id="248ce-371">Répertoire</span><span class="sxs-lookup"><span data-stu-id="248ce-371">Directory</span></span>
- <span data-ttu-id="248ce-372">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="248ce-372">SymbolicLink</span></span>
- <span data-ttu-id="248ce-373">jonction</span><span class="sxs-lookup"><span data-stu-id="248ce-373">Junction</span></span>
- <span data-ttu-id="248ce-374">HardLink</span><span class="sxs-lookup"><span data-stu-id="248ce-374">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="248ce-375">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="248ce-375">Cmdlets supported</span></span>

- [<span data-ttu-id="248ce-376">New-Item</span><span class="sxs-lookup"><span data-stu-id="248ce-376">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="248ce-377">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="248ce-377">Using the pipeline</span></span>

<span data-ttu-id="248ce-378">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="248ce-378">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="248ce-379">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="248ce-379">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="248ce-380">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="248ce-380">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="248ce-381">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="248ce-381">Getting help</span></span>

<span data-ttu-id="248ce-382">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="248ce-382">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="248ce-383">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="248ce-383">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="248ce-384">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="248ce-384">See also</span></span>

[<span data-ttu-id="248ce-385">about_Providers</span><span class="sxs-lookup"><span data-stu-id="248ce-385">about_Providers</span></span>](../About/about_Providers.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: ee2d8b8a3b736a59b5af4a81710a0d29dd2238d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598773"
---
# <span data-ttu-id="a19b3-102">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-102">Copy-Item</span></span>

## <span data-ttu-id="a19b3-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a19b3-103">SYNOPSIS</span></span>
<span data-ttu-id="a19b3-104">Copie un élément d’un emplacement vers un autre.</span><span class="sxs-lookup"><span data-stu-id="a19b3-104">Copies an item from one location to another.</span></span>

## <span data-ttu-id="a19b3-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a19b3-105">SYNTAX</span></span>

### <span data-ttu-id="a19b3-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a19b3-106">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="a19b3-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a19b3-107">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="a19b3-108">Description</span><span class="sxs-lookup"><span data-stu-id="a19b3-108">DESCRIPTION</span></span>

<span data-ttu-id="a19b3-109">L' `Copy-Item` applet de commande copie un élément d’un emplacement vers un autre dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="a19b3-109">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="a19b3-110">Par exemple, il peut copier un fichier dans un dossier, mais il ne peut pas copier un fichier vers un lecteur de certificat.</span><span class="sxs-lookup"><span data-stu-id="a19b3-110">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="a19b3-111">Cette applet de commande ne coupe pas ou ne supprime pas les éléments copiés.</span><span class="sxs-lookup"><span data-stu-id="a19b3-111">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="a19b3-112">Les éléments spécifiques que l’applet de commande peut copier dépendent du fournisseur PowerShell qui expose l’élément.</span><span class="sxs-lookup"><span data-stu-id="a19b3-112">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="a19b3-113">Par exemple, il peut copier des fichiers et des répertoires dans un lecteur du système de fichiers et des clés de Registre et des entrées dans le lecteur du Registre.</span><span class="sxs-lookup"><span data-stu-id="a19b3-113">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="a19b3-114">Cette applet de commande peut copier et renommer des éléments dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a19b3-114">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="a19b3-115">Pour renommer un élément, entrez le nouveau nom dans la valeur du paramètre **destination** .</span><span class="sxs-lookup"><span data-stu-id="a19b3-115">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="a19b3-116">Pour renommer un élément sans le copier, utilisez l’applet de commande `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-116">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="a19b3-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a19b3-117">EXAMPLES</span></span>

### <span data-ttu-id="a19b3-118">Exemple 1 : copier un fichier dans le répertoire spécifié</span><span class="sxs-lookup"><span data-stu-id="a19b3-118">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="a19b3-119">Cet exemple copie le `mar1604.log.txt` fichier dans le `C:\Presentation` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a19b3-119">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="a19b3-120">Le fichier d’origine n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="a19b3-120">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="a19b3-121">Exemple 2 : copier le contenu d’un répertoire dans un répertoire existant</span><span class="sxs-lookup"><span data-stu-id="a19b3-121">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="a19b3-122">Cet exemple copie le contenu du `C:\Logfiles` répertoire dans le répertoire existant `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-122">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="a19b3-123">Le `Logfiles` répertoire n’est pas copié.</span><span class="sxs-lookup"><span data-stu-id="a19b3-123">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="a19b3-124">Si le `Logfiles` répertoire contient des fichiers dans des sous-répertoires, ces derniers sont copiés avec leurs arborescences de fichiers intactes.</span><span class="sxs-lookup"><span data-stu-id="a19b3-124">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="a19b3-125">Par défaut, le paramètre **Container** a la valeur **true**, ce qui permet de conserver la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="a19b3-125">By default, the **Container** parameter is set to **True**, which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="a19b3-126">Si vous devez inclure le `Logfiles` répertoire dans la copie, supprimez du `\*` chemin d' **accès**.</span><span class="sxs-lookup"><span data-stu-id="a19b3-126">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path**.</span></span>
> <span data-ttu-id="a19b3-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a19b3-127">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="a19b3-128">Exemple 3 : copier le répertoire et le contenu dans un nouveau répertoire</span><span class="sxs-lookup"><span data-stu-id="a19b3-128">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="a19b3-129">Cet exemple copie le contenu du `C:\Logfiles` répertoire source et crée un répertoire de destination.</span><span class="sxs-lookup"><span data-stu-id="a19b3-129">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="a19b3-130">Le nouveau répertoire de destination, `\Logs` est créé dans `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-130">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="a19b3-131">Pour inclure le nom du répertoire source, copiez-le dans un répertoire de destination existant, comme indiqué dans l' **exemple 2**.</span><span class="sxs-lookup"><span data-stu-id="a19b3-131">To include the source directory's name, copy to an existing destination directory as shown in **Example 2**.</span></span> <span data-ttu-id="a19b3-132">Ou, nommez le nouveau répertoire de destination avec le même nom que le répertoire source.</span><span class="sxs-lookup"><span data-stu-id="a19b3-132">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="a19b3-133">Si le **chemin d’accès** inclut `\*` , tous les contenus du fichier du répertoire, y compris les arborescences de sous-répertoires, sont copiés dans le nouveau répertoire de destination.</span><span class="sxs-lookup"><span data-stu-id="a19b3-133">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="a19b3-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a19b3-134">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="a19b3-135">Exemple 4 : copier un fichier dans le répertoire spécifié et renommer le fichier</span><span class="sxs-lookup"><span data-stu-id="a19b3-135">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="a19b3-136">Cet exemple utilise l' `Copy-Item` applet de commande pour copier le `Get-Widget.ps1` script du `\\Server01\Share` répertoire vers `\\Server12\ScriptArchive` le répertoire.</span><span class="sxs-lookup"><span data-stu-id="a19b3-136">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="a19b3-137">Dans le cadre de l’opération de copie, la commande remplace le nom d’élément par `Get-Widget.ps1` `Get-Widget.ps1.txt` , afin qu’il puisse être joint à des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a19b3-137">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="a19b3-138">Exemple 5 : copier un fichier sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a19b3-138">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="a19b3-139">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-139">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-140">L' `Copy-Item` applet de `test.log` commande copie le `D:\Folder001` dossier dans le `C:\Folder001_Copy` dossier sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-140">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-141">Le fichier d’origine n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="a19b3-141">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="a19b3-142">Exemple 6 : copier un dossier sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a19b3-142">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="a19b3-143">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-143">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-144">L' `Copy-Item` applet de commande copie le `D:\Folder002` dossier dans le `C:\Folder002_Copy` répertoire sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-144">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-145">Tous les sous-dossiers ou fichiers ne sont pas copiés sans utiliser le commutateur **recurse** .</span><span class="sxs-lookup"><span data-stu-id="a19b3-145">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="a19b3-146">L’opération crée le `Folder002_Copy` dossier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="a19b3-146">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="a19b3-147">Exemple 7 : copier de manière récursive la totalité du contenu d’un dossier sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a19b3-147">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="a19b3-148">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-148">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-149">L' `Copy-Item` applet de commande copie l’intégralité du contenu du `D:\Folder003` dossier dans le `C:\Folder003_Copy` Répertoire de l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-149">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-150">Les sous-dossiers sont copiés avec leurs arborescences de fichiers intactes.</span><span class="sxs-lookup"><span data-stu-id="a19b3-150">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="a19b3-151">L’opération crée le `Folder003_Copy` dossier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="a19b3-151">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="a19b3-152">Exemple 8 : copier un fichier sur un ordinateur distant, puis renommer le fichier</span><span class="sxs-lookup"><span data-stu-id="a19b3-152">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="a19b3-153">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-153">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-154">L' `Copy-Item` applet de `scriptingexample.ps1` commande copie le `D:\Folder004` dossier dans le `C:\Folder004_Copy` dossier sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-154">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-155">Dans le cadre de l’opération de copie, la commande remplace le nom d’élément par `scriptingexample.ps1` `scriptingexample_copy.ps1` , afin qu’il puisse être joint à des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a19b3-155">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="a19b3-156">Le fichier d’origine n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="a19b3-156">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="a19b3-157">Exemple 9 : copier un fichier distant sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="a19b3-157">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="a19b3-158">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-158">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-159">L' `Copy-Item` applet de `test.log` commande copie à partir du `C:\MyRemoteData\` dossier distant vers le `D:\MyLocalData` dossier local à l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-159">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-160">Le fichier d’origine n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="a19b3-160">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="a19b3-161">Exemple 10 : copier l’intégralité du contenu d’un dossier distant sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="a19b3-161">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="a19b3-162">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-162">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-163">L' `Copy-Item` applet de commande copie l’intégralité du contenu du dossier distant dans `C:\MyRemoteData\scripts` le dossier local à `D:\MyLocalData` l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-163">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-164">Si le dossier scripts contient des fichiers dans des sous-dossiers, ceux-ci sont copiés avec leurs arborescences de fichiers intactes.</span><span class="sxs-lookup"><span data-stu-id="a19b3-164">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="a19b3-165">Exemple 11 : copier de manière récursive la totalité du contenu d’un dossier distant sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="a19b3-165">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="a19b3-166">Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-166">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="a19b3-167">L' `Copy-Item` applet de commande copie l’intégralité du contenu du dossier distant dans `C:\MyRemoteData\scripts` le dossier local à `D:\MyLocalData\scripts` l’aide des informations de session stockées dans la `$Session` variable.</span><span class="sxs-lookup"><span data-stu-id="a19b3-167">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="a19b3-168">Étant donné que le paramètre **recurse** est utilisé, l’opération crée le dossier scripts s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="a19b3-168">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="a19b3-169">Si le dossier scripts contient des fichiers dans des sous-dossiers, ceux-ci sont copiés avec leurs arborescences de fichiers intactes.</span><span class="sxs-lookup"><span data-stu-id="a19b3-169">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="a19b3-170">Exemple 12 : copier de manière récursive les fichiers d’une arborescence de dossiers dans le dossier actif</span><span class="sxs-lookup"><span data-stu-id="a19b3-170">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="a19b3-171">Cet exemple montre comment copier des fichiers à partir d’une structure de dossiers à plusieurs niveaux dans un dossier plat unique.</span><span class="sxs-lookup"><span data-stu-id="a19b3-171">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="a19b3-172">Les trois premières commandes affichent la structure de dossiers existante et le contenu de deux fichiers, les deux noms `file3.txt` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-172">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="a19b3-173">Le `Copy-Item` paramètre **Container** de l’applet de commande est défini sur `$false` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-173">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="a19b3-174">Cela entraîne la copie du contenu du dossier source, mais ne conserve pas la structure de dossiers.</span><span class="sxs-lookup"><span data-stu-id="a19b3-174">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="a19b3-175">Notez que les fichiers portant le même nom sont remplacés dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="a19b3-175">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="a19b3-176">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a19b3-176">PARAMETERS</span></span>

### <span data-ttu-id="a19b3-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a19b3-177">-Confirm</span></span>

<span data-ttu-id="a19b3-178">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a19b3-178">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-179">-Container</span><span class="sxs-lookup"><span data-stu-id="a19b3-179">-Container</span></span>

<span data-ttu-id="a19b3-180">Indique que cette applet de commande conserve les objets conteneur pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="a19b3-180">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="a19b3-181">Par défaut, le paramètre **Container** a la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="a19b3-181">By default, the **Container** parameter is set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-182">-Credential</span><span class="sxs-lookup"><span data-stu-id="a19b3-182">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a19b3-183">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a19b3-183">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a19b3-184">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a19b3-184">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-185">-Destination</span><span class="sxs-lookup"><span data-stu-id="a19b3-185">-Destination</span></span>

<span data-ttu-id="a19b3-186">Spécifie le chemin d'accès au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="a19b3-186">Specifies the path to the new location.</span></span> <span data-ttu-id="a19b3-187">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="a19b3-187">The default is the current directory.</span></span>

<span data-ttu-id="a19b3-188">Pour renommer l’élément en cours de copie, spécifiez un nouveau nom dans la valeur du paramètre **destination** .</span><span class="sxs-lookup"><span data-stu-id="a19b3-188">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-189">-Exclude</span><span class="sxs-lookup"><span data-stu-id="a19b3-189">-Exclude</span></span>

<span data-ttu-id="a19b3-190">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="a19b3-190">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a19b3-191">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="a19b3-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a19b3-192">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-192">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a19b3-193">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a19b3-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="a19b3-194">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a19b3-194">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a19b3-195">-Filter</span><span class="sxs-lookup"><span data-stu-id="a19b3-195">-Filter</span></span>

<span data-ttu-id="a19b3-196">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="a19b3-196">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a19b3-197">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="a19b3-197">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a19b3-198">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="a19b3-198">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a19b3-199">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="a19b3-199">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a19b3-200">-Force</span><span class="sxs-lookup"><span data-stu-id="a19b3-200">-Force</span></span>

<span data-ttu-id="a19b3-201">Indique que cette applet de commande copie des éléments qui ne peuvent pas être modifiés autrement, tels que la copie sur un fichier ou un alias en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a19b3-201">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-202">-Tosession</span><span class="sxs-lookup"><span data-stu-id="a19b3-202">-FromSession</span></span>

<span data-ttu-id="a19b3-203">Spécifie l’objet **PSSession** à partir duquel un fichier distant est copié.</span><span class="sxs-lookup"><span data-stu-id="a19b3-203">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="a19b3-204">Lorsque vous utilisez ce paramètre, les paramètres **path** et **LiteralPath** font référence au chemin d’accès local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a19b3-204">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-205">-Include</span><span class="sxs-lookup"><span data-stu-id="a19b3-205">-Include</span></span>

<span data-ttu-id="a19b3-206">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="a19b3-206">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a19b3-207">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="a19b3-207">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a19b3-208">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-208">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a19b3-209">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a19b3-209">Wildcard characters are permitted.</span></span> <span data-ttu-id="a19b3-210">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a19b3-210">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a19b3-211">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a19b3-211">-LiteralPath</span></span>

<span data-ttu-id="a19b3-212">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a19b3-212">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a19b3-213">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a19b3-213">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="a19b3-214">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a19b3-214">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a19b3-215">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a19b3-215">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a19b3-216">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a19b3-216">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a19b3-217">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a19b3-217">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-218">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a19b3-218">-PassThru</span></span>

<span data-ttu-id="a19b3-219">Retourne un objet qui représente l’élément avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="a19b3-219">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="a19b3-220">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="a19b3-220">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-221">-Path</span><span class="sxs-lookup"><span data-stu-id="a19b3-221">-Path</span></span>

<span data-ttu-id="a19b3-222">Spécifie, sous forme de tableau de chaînes, le chemin d’accès aux éléments à copier.</span><span class="sxs-lookup"><span data-stu-id="a19b3-222">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="a19b3-223">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a19b3-223">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a19b3-224">-Recurse</span><span class="sxs-lookup"><span data-stu-id="a19b3-224">-Recurse</span></span>

<span data-ttu-id="a19b3-225">Indique que cette applet de commande effectue une copie récursive.</span><span class="sxs-lookup"><span data-stu-id="a19b3-225">Indicates that this cmdlet does a recursive copy.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-226">-ToSession</span><span class="sxs-lookup"><span data-stu-id="a19b3-226">-ToSession</span></span>

<span data-ttu-id="a19b3-227">Spécifie l’objet **PSSession** dans lequel un fichier distant est copié.</span><span class="sxs-lookup"><span data-stu-id="a19b3-227">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="a19b3-228">Lorsque vous utilisez ce paramètre, le paramètre de **destination** fait référence au chemin d’accès local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a19b3-228">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-229">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a19b3-229">-WhatIf</span></span>

<span data-ttu-id="a19b3-230">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a19b3-230">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a19b3-231">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a19b3-231">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19b3-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a19b3-232">CommonParameters</span></span>

<span data-ttu-id="a19b3-233">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-233">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a19b3-234">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a19b3-234">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a19b3-235">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a19b3-235">INPUTS</span></span>

### <span data-ttu-id="a19b3-236">System.String</span><span class="sxs-lookup"><span data-stu-id="a19b3-236">System.String</span></span>

<span data-ttu-id="a19b3-237">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a19b3-237">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a19b3-238">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a19b3-238">OUTPUTS</span></span>

### <span data-ttu-id="a19b3-239">Aucun ou un objet représentant l’élément copié</span><span class="sxs-lookup"><span data-stu-id="a19b3-239">None or an object representing the copied item</span></span>

<span data-ttu-id="a19b3-240">Quand vous utilisez le paramètre **PassThru** , cette applet de commande retourne un objet qui représente l’élément copié.</span><span class="sxs-lookup"><span data-stu-id="a19b3-240">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="a19b3-241">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a19b3-241">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="a19b3-242">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a19b3-242">NOTES</span></span>

<span data-ttu-id="a19b3-243">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a19b3-243">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a19b3-244">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a19b3-244">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a19b3-245">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a19b3-245">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a19b3-246">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a19b3-246">RELATED LINKS</span></span>

[<span data-ttu-id="a19b3-247">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a19b3-247">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="a19b3-248">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-248">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a19b3-249">Get-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-249">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a19b3-250">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a19b3-250">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="a19b3-251">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-251">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a19b3-252">Move-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-252">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a19b3-253">New-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-253">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a19b3-254">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-254">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="a19b3-255">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-255">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="a19b3-256">Set-Item</span><span class="sxs-lookup"><span data-stu-id="a19b3-256">Set-Item</span></span>](Set-Item.md)


---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: b1657d369d44d575ee7bed8b76d36224ea2748f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203594"
---
# <span data-ttu-id="6b8cb-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-103">New-Item</span></span>

## <span data-ttu-id="6b8cb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6b8cb-104">SYNOPSIS</span></span>
<span data-ttu-id="6b8cb-105">Crée un élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-105">Creates a new item.</span></span>

## <span data-ttu-id="6b8cb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b8cb-106">SYNTAX</span></span>

### <span data-ttu-id="6b8cb-107">pathSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6b8cb-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="6b8cb-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="6b8cb-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="6b8cb-109">Description</span><span class="sxs-lookup"><span data-stu-id="6b8cb-109">DESCRIPTION</span></span>

<span data-ttu-id="6b8cb-110">L' `New-Item` applet de commande crée un nouvel élément et définit sa valeur.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="6b8cb-111">Les types d’éléments qui peuvent être créés dépendent de l’emplacement de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="6b8cb-112">Par exemple, dans le système de fichiers, `New-Item` crée des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="6b8cb-113">Dans le registre, `New-Item` crée des clés et des entrées de registre.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="6b8cb-114">`New-Item` peut également définir la valeur des éléments qu’elle crée.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="6b8cb-115">Par exemple, lorsqu’il crée un nouveau fichier, `New-Item` peut ajouter le contenu initial au fichier.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="6b8cb-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6b8cb-116">EXAMPLES</span></span>

### <span data-ttu-id="6b8cb-117">Exemple 1 : créer un fichier dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="6b8cb-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="6b8cb-118">Cette commande crée un fichier texte nommé « testfile1.txt » dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="6b8cb-119">Le point ('. ') dans la valeur du paramètre **path** indique le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="6b8cb-120">Le texte entre guillemets qui suit le paramètre **value** est ajouté au fichier en tant que contenu.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="6b8cb-121">Exemple 2 : créer un répertoire</span><span class="sxs-lookup"><span data-stu-id="6b8cb-121">Example 2: Create a directory</span></span>

<span data-ttu-id="6b8cb-122">Cette commande crée un répertoire nommé « LogFiles » dans le `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="6b8cb-123">Le paramètre **ItemType** spécifie que le nouvel élément est un répertoire, et non un fichier ou un autre objet de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="6b8cb-124">Exemple 3 : créer un profil</span><span class="sxs-lookup"><span data-stu-id="6b8cb-124">Example 3: Create a profile</span></span>

<span data-ttu-id="6b8cb-125">Cette commande crée un profil PowerShell dans le chemin d’accès spécifié par la `$profile` variable.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="6b8cb-126">Vous pouvez utiliser des profils pour personnaliser PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="6b8cb-127">`$profile` est une variable automatique (intégrée) qui stocke le chemin d’accès et le nom de fichier du profil « CurrentUser/CurrentHost ».</span><span class="sxs-lookup"><span data-stu-id="6b8cb-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="6b8cb-128">Par défaut, le profil n’existe pas, même si PowerShell stocke un chemin d’accès et un nom de fichier pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="6b8cb-129">Dans cette commande, la `$profile` variable représente le chemin d’accès du fichier.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="6b8cb-130">Le paramètre **ItemType** spécifie que la commande crée un fichier.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="6b8cb-131">Le paramètre **force** vous permet de créer un fichier dans le chemin d’accès du profil, même si les répertoires du chemin d’accès n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="6b8cb-132">Après avoir créé un profil, vous pouvez entrer des alias, des fonctions et des scripts dans le profil pour personnaliser votre shell.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="6b8cb-133">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) et [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

> [!NOTE]
> <span data-ttu-id="6b8cb-134">Lorsque vous créez un fichier à l’aide de cette méthode, le fichier obtenu est encodé au format UTF-8 sans marque d’ordre d’octet (BOM).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-134">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

### <span data-ttu-id="6b8cb-135">Exemple 4 : créer un répertoire dans un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="6b8cb-135">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="6b8cb-136">Cet exemple crée un répertoire scripts dans le répertoire « C:\PS-test. ».</span><span class="sxs-lookup"><span data-stu-id="6b8cb-136">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="6b8cb-137">Le nom du nouvel élément de répertoire, « scripts », est inclus dans la valeur du paramètre **path** , au lieu d’être spécifié dans la valeur de **Name** .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-137">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name** .</span></span> <span data-ttu-id="6b8cb-138">Comme indiqué par la syntaxe, les deux formes de commande sont valides.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-138">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="6b8cb-139">Exemple 5 : créer plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="6b8cb-139">Example 5: Create multiple files</span></span>

<span data-ttu-id="6b8cb-140">Cet exemple crée des fichiers dans deux répertoires différents.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-140">This example creates files in two different directories.</span></span> <span data-ttu-id="6b8cb-141">Étant donné que **path** accepte plusieurs chaînes, vous pouvez l’utiliser pour créer plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-141">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="6b8cb-142">Exemple 6 : utiliser le paramètre-force pour tenter de recréer des dossiers</span><span class="sxs-lookup"><span data-stu-id="6b8cb-142">Example 6: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="6b8cb-143">Cet exemple crée un dossier avec un fichier à l’intérieur de.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-143">This example creates a folder with a file inside.</span></span> <span data-ttu-id="6b8cb-144">Tente ensuite de créer le même dossier à l’aide de `-Force` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-144">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="6b8cb-145">Il ne remplace pas le dossier, mais retourne simplement l’objet dossier existant avec le fichier créé intact.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-145">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### <span data-ttu-id="6b8cb-146">Exemple 7 : utiliser le paramètre-force pour remplacer les fichiers existants</span><span class="sxs-lookup"><span data-stu-id="6b8cb-146">Example 7: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="6b8cb-147">Cet exemple crée un fichier avec une valeur, puis recrée le fichier à l’aide de `-Force` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-147">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="6b8cb-148">Cela a pour fonction de remplacer le fichier existant et de perdre son contenu, comme vous pouvez le voir dans la propriété Length.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-148">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> <span data-ttu-id="6b8cb-149">Lors de l’utilisation `New-Item` de avec le `-Force` commutateur pour créer des clés de Registre, la commande se comporte de la même façon que lors du remplacement d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-149">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="6b8cb-150">Si la clé de Registre existe déjà, la clé et toutes les propriétés et valeurs sont remplacées par une clé de Registre vide.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-150">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="6b8cb-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b8cb-151">PARAMETERS</span></span>

### <span data-ttu-id="6b8cb-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="6b8cb-152">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="6b8cb-153">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-153">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="6b8cb-154">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-154">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="6b8cb-155">-Force</span><span class="sxs-lookup"><span data-stu-id="6b8cb-155">-Force</span></span>

<span data-ttu-id="6b8cb-156">Force cette applet de commande à créer un élément qui écrit sur un élément en lecture seule existant.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-156">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="6b8cb-157">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-157">Implementation varies from provider to provider.</span></span> <span data-ttu-id="6b8cb-158">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-158">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-159">-ItemType</span><span class="sxs-lookup"><span data-stu-id="6b8cb-159">-ItemType</span></span>

<span data-ttu-id="6b8cb-160">Spécifie le type indiqué par le fournisseur du nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-160">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="6b8cb-161">Les valeurs disponibles de ce paramètre dépendent du fournisseur actuel que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-161">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="6b8cb-162">Si votre emplacement se trouve dans un `FileSystem` lecteur, les valeurs suivantes sont autorisées :</span><span class="sxs-lookup"><span data-stu-id="6b8cb-162">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="6b8cb-163">Fichier</span><span class="sxs-lookup"><span data-stu-id="6b8cb-163">File</span></span>
- <span data-ttu-id="6b8cb-164">Répertoire</span><span class="sxs-lookup"><span data-stu-id="6b8cb-164">Directory</span></span>
- <span data-ttu-id="6b8cb-165">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="6b8cb-165">SymbolicLink</span></span>
- <span data-ttu-id="6b8cb-166">jonction</span><span class="sxs-lookup"><span data-stu-id="6b8cb-166">Junction</span></span>
- <span data-ttu-id="6b8cb-167">HardLink</span><span class="sxs-lookup"><span data-stu-id="6b8cb-167">HardLink</span></span>

<span data-ttu-id="6b8cb-168">Lorsque vous créez un fichier à l’aide de cette méthode, le fichier obtenu est encodé au format UTF-8 sans marque d’ordre d’octet (BOM).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-168">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

<span data-ttu-id="6b8cb-169">Dans un `Certificate` lecteur, les valeurs que vous pouvez spécifier sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b8cb-169">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="6b8cb-170">Fournisseur Certificate</span><span class="sxs-lookup"><span data-stu-id="6b8cb-170">Certificate Provider</span></span>
- <span data-ttu-id="6b8cb-171">Certificat</span><span class="sxs-lookup"><span data-stu-id="6b8cb-171">Certificate</span></span>
- <span data-ttu-id="6b8cb-172">Magasin</span><span class="sxs-lookup"><span data-stu-id="6b8cb-172">Store</span></span>
- <span data-ttu-id="6b8cb-173">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="6b8cb-173">StoreLocation</span></span>

<span data-ttu-id="6b8cb-174">Pour plus d’informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-174">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-175">-Name</span><span class="sxs-lookup"><span data-stu-id="6b8cb-175">-Name</span></span>

<span data-ttu-id="6b8cb-176">Spécifie le nom du nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-176">Specifies the name of the new item.</span></span> <span data-ttu-id="6b8cb-177">Vous pouvez spécifier le nom du nouvel élément dans la valeur du paramètre **Name** ou **path** , et vous pouvez spécifier le chemin d’accès du nouvel élément dans le **nom** ou la valeur du **chemin d’accès** .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-177">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="6b8cb-178">Les noms d’éléments passés à l’aide du paramètre **Name** sont créés par rapport à la valeur du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-178">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-179">-Path</span><span class="sxs-lookup"><span data-stu-id="6b8cb-179">-Path</span></span>

<span data-ttu-id="6b8cb-180">Spécifie le chemin d’accès de l’emplacement du nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-180">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="6b8cb-181">La valeur par défaut est l’emplacement actuel lorsque le **chemin d’accès** est omis.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-181">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="6b8cb-182">Vous pouvez spécifier le nom du nouvel élément dans le **nom** ou l’inclure dans **path** .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-182">You can specify the name of the new item in **Name** , or include it in **Path** .</span></span> <span data-ttu-id="6b8cb-183">Les noms d’éléments passés à l’aide du paramètre **Name** sont créés par rapport à la valeur du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-183">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="6b8cb-184">Pour cette applet de commande, le paramètre **path** fonctionne comme le paramètre **LiteralPath** d’autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-184">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="6b8cb-185">Les caractères génériques ne sont pas interprétés.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-185">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="6b8cb-186">Tous les caractères sont passés au fournisseur de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-186">All characters are passed to the location's provider.</span></span> <span data-ttu-id="6b8cb-187">Le fournisseur ne prend peut-être pas en charge tous les caractères.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-187">The provider may not support all characters.</span></span> <span data-ttu-id="6b8cb-188">Par exemple, vous ne pouvez pas créer un nom de fichier contenant un astérisque ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-188">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet, nameSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-189">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="6b8cb-189">-UseTransaction</span></span>

<span data-ttu-id="6b8cb-190">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-190">Includes the command in the active transaction.</span></span> <span data-ttu-id="6b8cb-191">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-191">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="6b8cb-192">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-192">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-193">-Value</span><span class="sxs-lookup"><span data-stu-id="6b8cb-193">-Value</span></span>

<span data-ttu-id="6b8cb-194">Spécifie la valeur du nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-194">Specifies the value of the new item.</span></span> <span data-ttu-id="6b8cb-195">Vous pouvez également diriger une valeur vers `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-195">You can also pipe a value to `New-Item`.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6b8cb-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6b8cb-196">-Confirm</span></span>

<span data-ttu-id="6b8cb-197">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6b8cb-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6b8cb-198">-WhatIf</span></span>

<span data-ttu-id="6b8cb-199">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-199">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6b8cb-200">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6b8cb-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b8cb-201">CommonParameters</span></span>

<span data-ttu-id="6b8cb-202">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="6b8cb-203">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6b8cb-204">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6b8cb-204">INPUTS</span></span>

### <span data-ttu-id="6b8cb-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="6b8cb-205">System.Object</span></span>

<span data-ttu-id="6b8cb-206">Vous pouvez diriger une valeur pour le nouvel élément vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-206">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="6b8cb-207">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6b8cb-207">OUTPUTS</span></span>

### <span data-ttu-id="6b8cb-208">System.Object</span><span class="sxs-lookup"><span data-stu-id="6b8cb-208">System.Object</span></span>

<span data-ttu-id="6b8cb-209">Cette applet de commande retourne l’élément qu’elle crée.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-209">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="6b8cb-210">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6b8cb-210">NOTES</span></span>

<span data-ttu-id="6b8cb-211">`New-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6b8cb-211">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="6b8cb-212">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="6b8cb-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="6b8cb-213">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cb-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="6b8cb-214">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6b8cb-214">RELATED LINKS</span></span>

[<span data-ttu-id="6b8cb-215">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-215">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="6b8cb-216">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-216">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="6b8cb-217">Get-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-217">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="6b8cb-218">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="6b8cb-219">Move-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="6b8cb-220">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-220">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="6b8cb-221">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-221">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="6b8cb-222">Set-Item</span><span class="sxs-lookup"><span data-stu-id="6b8cb-222">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="6b8cb-223">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6b8cb-223">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

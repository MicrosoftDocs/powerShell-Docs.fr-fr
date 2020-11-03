---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204093"
---
# <span data-ttu-id="89b85-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="89b85-103">Add-Content</span></span>

## <span data-ttu-id="89b85-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="89b85-104">SYNOPSIS</span></span>
<span data-ttu-id="89b85-105">Ajoute le contenu aux éléments spécifiés (ajout de mots à un fichier, par exemple).</span><span class="sxs-lookup"><span data-stu-id="89b85-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="89b85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89b85-106">SYNTAX</span></span>

### <span data-ttu-id="89b85-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="89b85-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="89b85-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="89b85-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="89b85-109">Description</span><span class="sxs-lookup"><span data-stu-id="89b85-109">DESCRIPTION</span></span>

<span data-ttu-id="89b85-110">L' `Add-Content` applet de commande ajoute du contenu à un élément ou un fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="89b85-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="89b85-111">Vous pouvez spécifier le contenu en le tapant dans la commande ou en spécifiant un objet renfermant le contenu.</span><span class="sxs-lookup"><span data-stu-id="89b85-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="89b85-112">Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="89b85-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="89b85-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="89b85-113">EXAMPLES</span></span>

### <span data-ttu-id="89b85-114">Exemple 1 : ajouter une chaîne à tous les fichiers texte à l’aide d’une exception</span><span class="sxs-lookup"><span data-stu-id="89b85-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="89b85-115">Cet exemple ajoute une valeur aux fichiers texte dans le répertoire actif, mais exclut les fichiers en fonction de leur nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="89b85-116">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier tous les fichiers. txt dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="89b85-116">The `Add-Content` cmdlet uses the **Path** parameter to specify all .txt files in the current directory.</span></span> <span data-ttu-id="89b85-117">Le paramètre **Exclude** ignore les noms de fichiers qui correspondent au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="89b85-117">The **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="89b85-118">Le paramètre **value** spécifie la chaîne de texte qui est écrite dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="89b85-118">The **Value** parameter specifies the text string that is written to the files.</span></span>

<span data-ttu-id="89b85-119">Utilisez la valeur [obtenir-content](Get-Content.md) pour afficher le contenu de ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="89b85-119">Use [Get-Content](Get-Content.md) to display the contents of these files.</span></span>

### <span data-ttu-id="89b85-120">Exemple 2 : ajouter une date à la fin des fichiers spécifiés</span><span class="sxs-lookup"><span data-stu-id="89b85-120">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="89b85-121">Cet exemple ajoute la date à des fichiers dans le répertoire actif et affiche la date dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89b85-121">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

<span data-ttu-id="89b85-122">L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer deux nouveaux fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="89b85-122">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create two new files in the current directory.</span></span> <span data-ttu-id="89b85-123">Le paramètre **value** spécifie l' `Get-Date` applet de commande pour récupérer la date et la transmet à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-123">The **Value** parameter specifies the `Get-Date` cmdlet to get the date and passes the date to `Add-Content`.</span></span> <span data-ttu-id="89b85-124">L' `Add-Content` applet de commande écrit la date dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-124">The `Add-Content` cmdlet writes the date to each file.</span></span> <span data-ttu-id="89b85-125">Le paramètre **PassThru** passe un objet qui représente l’objet date.</span><span class="sxs-lookup"><span data-stu-id="89b85-125">The **PassThru** parameter passes an object that represents the date object.</span></span> <span data-ttu-id="89b85-126">Étant donné qu’il n’existe aucune autre applet de commande pour recevoir l’objet passé, il est affiché dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89b85-126">Because there is no other cmdlet to receive the passed object, it is displayed in the PowerShell console.</span></span> <span data-ttu-id="89b85-127">L' `Get-Content` applet de commande affiche le fichier mis à jour, DateTimeFile1. log.</span><span class="sxs-lookup"><span data-stu-id="89b85-127">The `Get-Content` cmdlet displays the updated file, DateTimeFile1.log.</span></span>

### <span data-ttu-id="89b85-128">Exemple 3 : ajouter le contenu d’un fichier spécifié dans un autre fichier</span><span class="sxs-lookup"><span data-stu-id="89b85-128">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="89b85-129">Cet exemple obtient le contenu d’un fichier et ajoute ce contenu dans un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-129">This example gets the content from a file and appends that content into another file.</span></span>

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="89b85-130">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le nouveau fichier dans le répertoire actif, CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-130">The `Add-Content` cmdlet uses the **Path** parameter to specify the new file in the current directory, CopyToFile.txt.</span></span> <span data-ttu-id="89b85-131">Le paramètre **value** utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier, CopyFromFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-131">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of the file, CopyFromFile.txt.</span></span> <span data-ttu-id="89b85-132">Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande.</span><span class="sxs-lookup"><span data-stu-id="89b85-132">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="89b85-133">Le paramètre de **valeur** est passé à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-133">The **Value** parameter is passed to `Add-Content`.</span></span> <span data-ttu-id="89b85-134">L' `Add-Content` applet de commande ajoute les données au fichier CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-134">The `Add-Content` cmdlet appends the data to the CopyToFile.txt file.</span></span> <span data-ttu-id="89b85-135">L' `Get-Content` applet de commande affiche le fichier mis à jour, CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-135">The `Get-Content` cmdlet displays the updated file, CopyToFile.txt.</span></span>

### <span data-ttu-id="89b85-136">Exemple 4 : utiliser une variable pour ajouter le contenu d’un fichier spécifié dans un autre fichier</span><span class="sxs-lookup"><span data-stu-id="89b85-136">Example 4: Use a variable to add the contents of a specified file to another file</span></span>

<span data-ttu-id="89b85-137">Cet exemple obtient le contenu d’un fichier et stocke le contenu dans une variable.</span><span class="sxs-lookup"><span data-stu-id="89b85-137">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="89b85-138">La variable est utilisée pour ajouter le contenu dans un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-138">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="89b85-139">L' `Get-Content` applet de commande obtient le contenu de CopyFromFile.txt et stocke le contenu dans la `$From` variable.</span><span class="sxs-lookup"><span data-stu-id="89b85-139">The `Get-Content` cmdlet gets the contents of CopyFromFile.txt and stores the contents in the `$From` variable.</span></span> <span data-ttu-id="89b85-140">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier CopyToFile.txt dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="89b85-140">The `Add-Content` cmdlet uses the **Path** parameter to specify the CopyToFile.txt file in the current directory.</span></span> <span data-ttu-id="89b85-141">Le paramètre de **valeur** utilise la `$From` variable et passe le contenu à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-141">The **Value** parameter uses the `$From` variable and passes the content to `Add-Content`.</span></span> <span data-ttu-id="89b85-142">L' `Add-Content` applet de commande met à jour le fichier CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-142">The `Add-Content` cmdlet updates the CopyToFile.txt file.</span></span> <span data-ttu-id="89b85-143">L' `Get-Content` applet de commande affiche CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-143">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="89b85-144">Exemple 5 : créer un fichier et copier du contenu</span><span class="sxs-lookup"><span data-stu-id="89b85-144">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="89b85-145">Cet exemple crée un nouveau fichier et copie le contenu d’un fichier existant dans le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-145">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

<span data-ttu-id="89b85-146">L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer un nouveau fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="89b85-146">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span> <span data-ttu-id="89b85-147">Le paramètre **value** utilise l' `Get-Content` applet de commande pour récupérer le contenu d’un fichier existant, CopyFromFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-147">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of an existing file, CopyFromFile.txt.</span></span> <span data-ttu-id="89b85-148">Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande.</span><span class="sxs-lookup"><span data-stu-id="89b85-148">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="89b85-149">Le paramètre **value** passe le contenu vers `Add-Content` lequel met à jour le fichier NewFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-149">The **Value** parameter passes the content to `Add-Content` which updates the NewFile.txt file.</span></span> <span data-ttu-id="89b85-150">L' `Get-Content` applet de commande affiche le contenu du nouveau fichier, NewFile.txt.</span><span class="sxs-lookup"><span data-stu-id="89b85-150">The `Get-Content` cmdlet displays the contents of the new file, NewFile.txt.</span></span>

### <span data-ttu-id="89b85-151">Exemple 6 : ajouter du contenu à un fichier en lecture seule</span><span class="sxs-lookup"><span data-stu-id="89b85-151">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="89b85-152">Cette commande ajoute la valeur au fichier même si l’attribut de fichier **IsReadOnly** a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="89b85-152">This command adds the value to the file even if the **IsReadOnly** file attribute is set to True.</span></span>
<span data-ttu-id="89b85-153">Les étapes de création d’un fichier en lecture seule sont incluses dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="89b85-153">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

<span data-ttu-id="89b85-154">L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier IsReadOnlyTextFile.txt dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="89b85-154">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file IsReadOnlyTextFile.txt in the current directory.</span></span> <span data-ttu-id="89b85-155">L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-155">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span> <span data-ttu-id="89b85-156">L' `Get-ChildItem` applet de commande indique que le fichier est vide (0) et possède l’attribut de lecture seule ( `r` ).</span><span class="sxs-lookup"><span data-stu-id="89b85-156">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span> <span data-ttu-id="89b85-157">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-157">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="89b85-158">Le paramètre **value** comprend la chaîne de texte à ajouter au fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-158">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="89b85-159">Le paramètre **force** écrit le texte dans le fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="89b85-159">The **Force** parameter writes the text to the read-only file.</span></span> <span data-ttu-id="89b85-160">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="89b85-160">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="89b85-161">Pour supprimer l’attribut de lecture seule, utilisez la `Set-ItemProperty` commande avec le paramètre de **valeur** défini sur `False` .</span><span class="sxs-lookup"><span data-stu-id="89b85-161">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

## <span data-ttu-id="89b85-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89b85-162">PARAMETERS</span></span>

### <span data-ttu-id="89b85-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="89b85-163">-Confirm</span></span>

<span data-ttu-id="89b85-164">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89b85-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="89b85-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="89b85-165">-Credential</span></span>

<span data-ttu-id="89b85-166">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="89b85-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="89b85-167">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="89b85-167">The default is the current user.</span></span>

<span data-ttu-id="89b85-168">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="89b85-168">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="89b85-169">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="89b85-169">If you type a user name, you will be prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="89b85-170">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89b85-170">This parameter is not supported by any providers installed with PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89b85-171">-Encoding</span><span class="sxs-lookup"><span data-stu-id="89b85-171">-Encoding</span></span>

<span data-ttu-id="89b85-172">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="89b85-172">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="89b85-173">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="89b85-173">The default value is `Default`.</span></span>

<span data-ttu-id="89b85-174">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="89b85-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="89b85-175">`Ascii` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="89b85-175">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="89b85-176">`BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="89b85-176">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="89b85-177">`BigEndianUTF32` Utilise UTF-32 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="89b85-177">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="89b85-178">`Byte` Encode un jeu de caractères en une séquence d’octets.</span><span class="sxs-lookup"><span data-stu-id="89b85-178">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="89b85-179">`Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).</span><span class="sxs-lookup"><span data-stu-id="89b85-179">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="89b85-180">`Oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="89b85-180">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="89b85-181">`String` Identique au **format Unicode** .</span><span class="sxs-lookup"><span data-stu-id="89b85-181">`String` Same as **Unicode** .</span></span>
- <span data-ttu-id="89b85-182">`Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="89b85-182">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="89b85-183">`Unknown` Identique au **format Unicode** .</span><span class="sxs-lookup"><span data-stu-id="89b85-183">`Unknown` Same as **Unicode** .</span></span>
- <span data-ttu-id="89b85-184">`UTF7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="89b85-184">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="89b85-185">`UTF8` Utilise UTF-8.</span><span class="sxs-lookup"><span data-stu-id="89b85-185">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="89b85-186">`UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="89b85-186">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="89b85-187">L’encodage est un paramètre dynamique que le fournisseur FileSystem ajoute à l’applet de commande `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-187">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="89b85-188">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="89b85-188">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89b85-189">-Exclude</span><span class="sxs-lookup"><span data-stu-id="89b85-189">-Exclude</span></span>

<span data-ttu-id="89b85-190">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="89b85-190">Omits the specified items.</span></span> <span data-ttu-id="89b85-191">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="89b85-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="89b85-192">Entrez un élément ou un modèle de chemin d’accès, tel que **\* . txt** .</span><span class="sxs-lookup"><span data-stu-id="89b85-192">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="89b85-193">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="89b85-193">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="89b85-194">-Filter</span><span class="sxs-lookup"><span data-stu-id="89b85-194">-Filter</span></span>

<span data-ttu-id="89b85-195">Spécifie un filtre dans le format ou le langage du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="89b85-195">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="89b85-196">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="89b85-196">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="89b85-197">La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="89b85-197">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="89b85-198">Les **filtres** sont plus efficaces que les autres paramètres, car le fournisseur applique des filtres lorsque les objets sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="89b85-198">**Filters** are more efficient than other parameters because the provider applies filters when objects are retrieved.</span></span> <span data-ttu-id="89b85-199">Dans le cas contraire, PowerShell traite les filtres une fois les objets récupérés.</span><span class="sxs-lookup"><span data-stu-id="89b85-199">Otherwise, PowerShell processes filters after the objects are retrieved.</span></span>

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

### <span data-ttu-id="89b85-200">-Force</span><span class="sxs-lookup"><span data-stu-id="89b85-200">-Force</span></span>

<span data-ttu-id="89b85-201">Remplace l'attribut de lecture seule pour que vous puissiez ajouter le contenu à un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="89b85-201">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="89b85-202">Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="89b85-202">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="89b85-203">-Include</span><span class="sxs-lookup"><span data-stu-id="89b85-203">-Include</span></span>

<span data-ttu-id="89b85-204">Ajoute uniquement les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="89b85-204">Adds only the specified items.</span></span> <span data-ttu-id="89b85-205">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="89b85-205">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="89b85-206">Entrez un élément ou un modèle de chemin d’accès, tel que **\* . txt** .</span><span class="sxs-lookup"><span data-stu-id="89b85-206">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="89b85-207">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="89b85-207">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="89b85-208">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="89b85-208">-LiteralPath</span></span>

<span data-ttu-id="89b85-209">Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="89b85-209">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="89b85-210">Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="89b85-210">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="89b85-211">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="89b85-211">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="89b85-212">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="89b85-212">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="89b85-213">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="89b85-213">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89b85-214">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="89b85-214">-NoNewline</span></span>

<span data-ttu-id="89b85-215">Indique que cette applet de commande n’ajoute pas de nouvelle ligne ou de retour chariot au contenu.</span><span class="sxs-lookup"><span data-stu-id="89b85-215">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="89b85-216">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="89b85-216">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="89b85-217">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="89b85-217">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="89b85-218">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="89b85-218">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="89b85-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="89b85-219">-PassThru</span></span>

<span data-ttu-id="89b85-220">Retourne un objet qui représente le contenu ajouté.</span><span class="sxs-lookup"><span data-stu-id="89b85-220">Returns an object representing the added content.</span></span> <span data-ttu-id="89b85-221">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="89b85-221">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="89b85-222">-Path</span><span class="sxs-lookup"><span data-stu-id="89b85-222">-Path</span></span>

<span data-ttu-id="89b85-223">Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="89b85-223">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="89b85-224">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="89b85-224">Wildcards are permitted.</span></span> <span data-ttu-id="89b85-225">Si vous spécifiez plusieurs chemins d'accès, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="89b85-225">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="89b85-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="89b85-226">-Stream</span></span>

<span data-ttu-id="89b85-227">Spécifie un flux de données alternatif pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="89b85-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="89b85-228">Si le flux n’existe pas, cette applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="89b85-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="89b85-229">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89b85-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="89b85-230">**Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="89b85-231">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="89b85-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="89b85-232">Vous pouvez utiliser l' `Add-Content` applet de commande pour modifier le contenu du flux de données de remplacement de la **zone. identifier** .</span><span class="sxs-lookup"><span data-stu-id="89b85-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="89b85-233">Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="89b85-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="89b85-234">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89b85-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="89b85-235">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="89b85-235">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89b85-236">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="89b85-236">-UseTransaction</span></span>

<span data-ttu-id="89b85-237">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="89b85-237">Includes the command in the active transaction.</span></span> <span data-ttu-id="89b85-238">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="89b85-238">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="89b85-239">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="89b85-239">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="89b85-240">-Value</span><span class="sxs-lookup"><span data-stu-id="89b85-240">-Value</span></span>

<span data-ttu-id="89b85-241">Spécifie le contenu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="89b85-241">Specifies the content to be added.</span></span> <span data-ttu-id="89b85-242">Tapez une chaîne entre guillemets, telle que **ces données sont destinées à un usage interne uniquement** , ou spécifiez un objet qui contient du contenu, tel que l’objet **DateTime** `Get-Date` généré par.</span><span class="sxs-lookup"><span data-stu-id="89b85-242">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="89b85-243">Vous ne pouvez pas spécifier le contenu d’un fichier en tapant son chemin d’accès, car il s’agit simplement d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="89b85-243">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="89b85-244">Vous pouvez utiliser une `Get-Content` commande pour obtenir le contenu et le passer au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="89b85-244">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="89b85-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="89b85-245">-WhatIf</span></span>

<span data-ttu-id="89b85-246">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="89b85-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="89b85-247">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="89b85-247">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="89b85-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89b85-248">CommonParameters</span></span>

<span data-ttu-id="89b85-249">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="89b85-249">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="89b85-250">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="89b85-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89b85-251">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="89b85-251">INPUTS</span></span>

### <span data-ttu-id="89b85-252">System. Object, System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="89b85-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="89b85-253">Vous pouvez diriger des valeurs, des chemins d’accès ou des informations d’identification vers `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="89b85-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="89b85-254">SORTIES</span><span class="sxs-lookup"><span data-stu-id="89b85-254">OUTPUTS</span></span>

### <span data-ttu-id="89b85-255">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="89b85-255">None or System.String</span></span>

<span data-ttu-id="89b85-256">Quand vous utilisez le paramètre **PassThru** , `Add-Content` génère un objet **System. String** qui représente le contenu.</span><span class="sxs-lookup"><span data-stu-id="89b85-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="89b85-257">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="89b85-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="89b85-258">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="89b85-258">NOTES</span></span>

<span data-ttu-id="89b85-259">Quand vous dirigez un objet vers `Add-Content` , l’objet est converti en chaîne avant d’être ajouté à l’élément.</span><span class="sxs-lookup"><span data-stu-id="89b85-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="89b85-260">Le type d'objet détermine le format de la chaîne, mais le format peut être différent de l'affichage par défaut de l'objet.</span><span class="sxs-lookup"><span data-stu-id="89b85-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="89b85-261">Pour contrôler le format de la chaîne, utilisez les paramètres de formatage de l'applet de commande d'envoi.</span><span class="sxs-lookup"><span data-stu-id="89b85-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>

<span data-ttu-id="89b85-262">Vous pouvez également faire référence à `Add-Content` par son alias intégré, `ac` .</span><span class="sxs-lookup"><span data-stu-id="89b85-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="89b85-263">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="89b85-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="89b85-264">L' `Add-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="89b85-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="89b85-265">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="89b85-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="89b85-266">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="89b85-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="89b85-267">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="89b85-267">RELATED LINKS</span></span>

[<span data-ttu-id="89b85-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="89b85-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="89b85-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="89b85-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="89b85-270">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="89b85-270">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="89b85-271">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="89b85-271">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="89b85-272">Get-Content</span><span class="sxs-lookup"><span data-stu-id="89b85-272">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="89b85-273">Get-Item</span><span class="sxs-lookup"><span data-stu-id="89b85-273">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="89b85-274">New-Item</span><span class="sxs-lookup"><span data-stu-id="89b85-274">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="89b85-275">Set-Content</span><span class="sxs-lookup"><span data-stu-id="89b85-275">Set-Content</span></span>](Set-Content.md)

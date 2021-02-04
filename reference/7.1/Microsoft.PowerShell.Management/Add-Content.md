---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: ef44fefe68ef9674eb14ce494341bf04f477d55a
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693004"
---
# <span data-ttu-id="ecdad-102">Add-Content</span><span class="sxs-lookup"><span data-stu-id="ecdad-102">Add-Content</span></span>

## <span data-ttu-id="ecdad-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ecdad-103">SYNOPSIS</span></span>
<span data-ttu-id="ecdad-104">Ajoute le contenu aux éléments spécifiés (ajout de mots à un fichier, par exemple).</span><span class="sxs-lookup"><span data-stu-id="ecdad-104">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="ecdad-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ecdad-105">SYNTAX</span></span>

### <span data-ttu-id="ecdad-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ecdad-106">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="ecdad-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ecdad-107">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="ecdad-108">Description</span><span class="sxs-lookup"><span data-stu-id="ecdad-108">DESCRIPTION</span></span>

<span data-ttu-id="ecdad-109">L' `Add-Content` applet de commande ajoute du contenu à un élément ou un fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ecdad-109">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="ecdad-110">Vous pouvez spécifier le contenu en le tapant dans la commande ou en spécifiant un objet renfermant le contenu.</span><span class="sxs-lookup"><span data-stu-id="ecdad-110">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="ecdad-111">Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-111">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="ecdad-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ecdad-112">EXAMPLES</span></span>

### <span data-ttu-id="ecdad-113">Exemple 1 : ajouter une chaîne à tous les fichiers texte à l’aide d’une exception</span><span class="sxs-lookup"><span data-stu-id="ecdad-113">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="ecdad-114">Cet exemple ajoute une valeur aux fichiers texte dans le répertoire actif, mais exclut les fichiers en fonction de leur nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-114">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="ecdad-115">Le paramètre **path** spécifie tous les `.txt` fichiers dans le répertoire actif, mais le paramètre **Exclude** ignore les noms de fichiers qui correspondent au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="ecdad-115">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="ecdad-116">Le paramètre **value** spécifie la chaîne de texte qui est écrite dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="ecdad-116">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="ecdad-117">Exemple 2 : ajouter une date à la fin des fichiers spécifiés</span><span class="sxs-lookup"><span data-stu-id="ecdad-117">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="ecdad-118">Cet exemple ajoute la date à des fichiers dans le répertoire actif et affiche la date dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecdad-118">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="ecdad-119">L' `Add-Content` applet de commande crée deux nouveaux fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ecdad-119">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="ecdad-120">Le paramètre **value** contient la sortie de l' `Get-Date` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-120">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="ecdad-121">Le paramètre **PassThru** génère le contenu ajouté dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ecdad-121">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="ecdad-122">Étant donné qu’il n’existe aucune autre applet de commande pour recevoir la sortie, elle est affichée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecdad-122">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="ecdad-123">L' `Get-Content` applet de commande affiche le fichier mis à jour, `DateTimeFile1.log` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-123">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="ecdad-124">Exemple 3 : ajouter le contenu d’un fichier spécifié dans un autre fichier</span><span class="sxs-lookup"><span data-stu-id="ecdad-124">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="ecdad-125">Cet exemple obtient le contenu d’un fichier et stocke le contenu dans une variable.</span><span class="sxs-lookup"><span data-stu-id="ecdad-125">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="ecdad-126">La variable est utilisée pour ajouter le contenu dans un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-126">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="ecdad-127">L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` et stocke le contenu dans la `$From` variable.</span><span class="sxs-lookup"><span data-stu-id="ecdad-127">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="ecdad-128">L' `Add-Content` applet de commande met à jour le `CopyToFile.txt` fichier à l’aide du contenu de la `$From` variable.</span><span class="sxs-lookup"><span data-stu-id="ecdad-128">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="ecdad-129">L' `Get-Content` applet de commande affiche CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="ecdad-129">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="ecdad-130">Exemple 4 : ajouter le contenu d’un fichier spécifié à un autre fichier à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="ecdad-130">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="ecdad-131">Cet exemple obtient le contenu d’un fichier et le dirige vers l' `Add-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-131">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="ecdad-132">L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-132">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="ecdad-133">Les résultats sont dirigés vers l’applet de commande `Add-Content` , qui met à jour le `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-133">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="ecdad-134">La dernière `Get-Content` applet de commande s’affiche `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-134">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="ecdad-135">Exemple 5 : créer un fichier et copier du contenu</span><span class="sxs-lookup"><span data-stu-id="ecdad-135">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="ecdad-136">Cet exemple crée un nouveau fichier et copie le contenu d’un fichier existant dans le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-136">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="ecdad-137">L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer un nouveau fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ecdad-137">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="ecdad-138">L' `Get-Content` applet de commande obtient le contenu d’un fichier existant `CopyFromFile.txt` et le passe au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="ecdad-138">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="ecdad-139">Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-139">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="ecdad-140">L' `Get-Content` applet de commande affiche le contenu du nouveau fichier, `NewFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-140">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="ecdad-141">Exemple 6 : ajouter du contenu à un fichier en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ecdad-141">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="ecdad-142">Cette commande ajoute une valeur au fichier même si l’attribut de fichier **IsReadOnly** a la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="ecdad-142">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True**.</span></span>
<span data-ttu-id="ecdad-143">Les étapes de création d’un fichier en lecture seule sont incluses dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="ecdad-143">The steps to create a read-only file are included in the example.</span></span>

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
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="ecdad-144">L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier `IsReadOnlyTextFile.txt` dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ecdad-144">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="ecdad-145">L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-145">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="ecdad-146">L' `Get-ChildItem` applet de commande indique que le fichier est vide (0) et possède l’attribut de lecture seule ( `r` ).</span><span class="sxs-lookup"><span data-stu-id="ecdad-146">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="ecdad-147">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-147">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="ecdad-148">Le paramètre **value** comprend la chaîne de texte à ajouter au fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-148">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="ecdad-149">Le paramètre **force** écrit le texte dans le fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ecdad-149">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="ecdad-150">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="ecdad-150">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="ecdad-151">Pour supprimer l’attribut de lecture seule, utilisez la `Set-ItemProperty` commande avec le paramètre de **valeur** défini sur `False` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-151">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="ecdad-152">Exemple 7 : utiliser des filtres avec Add-Content</span><span class="sxs-lookup"><span data-stu-id="ecdad-152">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="ecdad-153">Vous pouvez spécifier un filtre pour l' `Add-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-153">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="ecdad-154">Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ecdad-154">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="ecdad-155">La commande suivante ajoute le mot « DONE » (terminé) au contenu de tous les `*.txt` fichiers dans le `C:\Temp` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ecdad-155">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="ecdad-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ecdad-156">PARAMETERS</span></span>

### <span data-ttu-id="ecdad-157">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="ecdad-157">-AsByteStream</span></span>

<span data-ttu-id="ecdad-158">Spécifie que le contenu doit être lu en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="ecdad-158">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="ecdad-159">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="ecdad-159">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="ecdad-160">Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="ecdad-160">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="ecdad-161">Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="ecdad-161">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="ecdad-162">-Credential</span><span class="sxs-lookup"><span data-stu-id="ecdad-162">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ecdad-163">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecdad-163">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ecdad-164">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-164">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="ecdad-165">-Encoding</span><span class="sxs-lookup"><span data-stu-id="ecdad-165">-Encoding</span></span>

<span data-ttu-id="ecdad-166">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="ecdad-166">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="ecdad-167">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="ecdad-167">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="ecdad-168">L’encodage est un paramètre dynamique que le fournisseur FileSystem ajoute à l’applet de commande `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-168">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="ecdad-169">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ecdad-169">This parameter works only in file system drives.</span></span>

<span data-ttu-id="ecdad-170">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ecdad-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="ecdad-171">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="ecdad-171">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="ecdad-172">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="ecdad-172">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="ecdad-173">`bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="ecdad-173">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="ecdad-174">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="ecdad-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="ecdad-175">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="ecdad-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="ecdad-176">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="ecdad-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="ecdad-177">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ecdad-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="ecdad-178">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="ecdad-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="ecdad-179">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="ecdad-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="ecdad-180">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="ecdad-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="ecdad-181">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="ecdad-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="ecdad-182">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="ecdad-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="ecdad-183">**UTF-7** _ n’est plus recommandé pour l’utilisation de.</span><span class="sxs-lookup"><span data-stu-id="ecdad-183">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="ecdad-184">Dans PowerShell 7,1, un avertissement est écrit si vous spécifiez `utf7` pour le paramètre _ \*Encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="ecdad-184">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ecdad-185">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ecdad-185">-Exclude</span></span>

<span data-ttu-id="ecdad-186">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="ecdad-186">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="ecdad-187">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="ecdad-187">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ecdad-188">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="ecdad-189">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ecdad-189">Wildcard characters are permitted.</span></span> <span data-ttu-id="ecdad-190">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ecdad-190">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ecdad-191">-Filter</span><span class="sxs-lookup"><span data-stu-id="ecdad-191">-Filter</span></span>

<span data-ttu-id="ecdad-192">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="ecdad-192">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="ecdad-193">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="ecdad-193">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="ecdad-194">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-194">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="ecdad-195">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="ecdad-195">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ecdad-196">-Force</span><span class="sxs-lookup"><span data-stu-id="ecdad-196">-Force</span></span>

<span data-ttu-id="ecdad-197">Remplace l'attribut de lecture seule pour que vous puissiez ajouter le contenu à un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ecdad-197">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="ecdad-198">Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="ecdad-198">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="ecdad-199">-Include</span><span class="sxs-lookup"><span data-stu-id="ecdad-199">-Include</span></span>

<span data-ttu-id="ecdad-200">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="ecdad-200">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ecdad-201">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="ecdad-201">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ecdad-202">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-202">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="ecdad-203">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ecdad-203">Wildcard characters are permitted.</span></span> <span data-ttu-id="ecdad-204">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ecdad-204">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ecdad-205">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ecdad-205">-LiteralPath</span></span>

<span data-ttu-id="ecdad-206">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="ecdad-206">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ecdad-207">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="ecdad-207">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="ecdad-208">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ecdad-208">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ecdad-209">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="ecdad-209">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ecdad-210">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="ecdad-210">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="ecdad-211">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-211">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="ecdad-212">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="ecdad-212">-NoNewline</span></span>

<span data-ttu-id="ecdad-213">Indique que cette applet de commande n’ajoute pas de nouvelle ligne ou de retour chariot au contenu.</span><span class="sxs-lookup"><span data-stu-id="ecdad-213">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="ecdad-214">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="ecdad-214">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="ecdad-215">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="ecdad-215">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="ecdad-216">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="ecdad-216">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="ecdad-217">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ecdad-217">-PassThru</span></span>

<span data-ttu-id="ecdad-218">Retourne un objet qui représente le contenu ajouté.</span><span class="sxs-lookup"><span data-stu-id="ecdad-218">Returns an object representing the added content.</span></span> <span data-ttu-id="ecdad-219">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="ecdad-219">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ecdad-220">-Path</span><span class="sxs-lookup"><span data-stu-id="ecdad-220">-Path</span></span>

<span data-ttu-id="ecdad-221">Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="ecdad-221">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="ecdad-222">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ecdad-222">Wildcard characters are permitted.</span></span>
<span data-ttu-id="ecdad-223">Les chemins d'accès doivent être ceux des éléments et non des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ecdad-223">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="ecdad-224">Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="ecdad-224">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="ecdad-225">Si vous spécifiez plusieurs chemins d'accès, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="ecdad-225">If you specify multiple paths, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="ecdad-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="ecdad-226">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="ecdad-227">Ce paramètre est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="ecdad-227">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="ecdad-228">Spécifie un flux de données alternatif pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="ecdad-228">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="ecdad-229">Si le flux n’existe pas, cette applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="ecdad-229">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="ecdad-230">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ecdad-230">Wildcard characters are not supported.</span></span>

<span data-ttu-id="ecdad-231">**Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-231">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="ecdad-232">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ecdad-232">This parameter works only in file system drives.</span></span>

<span data-ttu-id="ecdad-233">Vous pouvez utiliser l' `Add-Content` applet de commande pour modifier le contenu de tout autre flux de données, tel que `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-233">You can use the `Add-Content` cmdlet to change the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="ecdad-234">Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="ecdad-234">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="ecdad-235">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-235">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="ecdad-236">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ecdad-236">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ecdad-237">-Value</span><span class="sxs-lookup"><span data-stu-id="ecdad-237">-Value</span></span>

<span data-ttu-id="ecdad-238">Spécifie le contenu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ecdad-238">Specifies the content to be added.</span></span> <span data-ttu-id="ecdad-239">Tapez une chaîne entre guillemets, telle que **ces données sont destinées à un usage interne uniquement**, ou spécifiez un objet qui contient du contenu, tel que l’objet **DateTime** `Get-Date` généré par.</span><span class="sxs-lookup"><span data-stu-id="ecdad-239">Type a quoted string, such as **This data is for internal use only**, or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="ecdad-240">Vous ne pouvez pas spécifier le contenu d’un fichier en tapant son chemin d’accès, car il s’agit simplement d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ecdad-240">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="ecdad-241">Vous pouvez utiliser une `Get-Content` commande pour obtenir le contenu et le passer au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="ecdad-241">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

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

### <span data-ttu-id="ecdad-242">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ecdad-242">-Confirm</span></span>

<span data-ttu-id="ecdad-243">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-243">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ecdad-244">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ecdad-244">-WhatIf</span></span>

<span data-ttu-id="ecdad-245">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ecdad-245">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ecdad-246">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ecdad-246">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ecdad-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ecdad-247">CommonParameters</span></span>

<span data-ttu-id="ecdad-248">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ecdad-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ecdad-249">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ecdad-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ecdad-250">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ecdad-250">INPUTS</span></span>

### <span data-ttu-id="ecdad-251">System. Object, System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ecdad-251">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="ecdad-252">Vous pouvez diriger des valeurs, des chemins d’accès ou des informations d’identification vers `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-252">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="ecdad-253">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ecdad-253">OUTPUTS</span></span>

### <span data-ttu-id="ecdad-254">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="ecdad-254">None or System.String</span></span>

<span data-ttu-id="ecdad-255">Quand vous utilisez le paramètre **PassThru** , `Add-Content` génère un objet **System. String** qui représente le contenu.</span><span class="sxs-lookup"><span data-stu-id="ecdad-255">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="ecdad-256">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ecdad-256">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ecdad-257">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ecdad-257">NOTES</span></span>

- <span data-ttu-id="ecdad-258">Quand vous dirigez un objet vers `Add-Content` , l’objet est converti en chaîne avant d’être ajouté à l’élément.</span><span class="sxs-lookup"><span data-stu-id="ecdad-258">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="ecdad-259">Le type d'objet détermine le format de la chaîne, mais le format peut être différent de l'affichage par défaut de l'objet.</span><span class="sxs-lookup"><span data-stu-id="ecdad-259">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="ecdad-260">Pour contrôler le format de la chaîne, utilisez les paramètres de formatage de l'applet de commande d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ecdad-260">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="ecdad-261">Vous pouvez également faire référence à `Add-Content` par son alias intégré, `ac` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-261">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="ecdad-262">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-262">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="ecdad-263">L' `Add-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="ecdad-263">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ecdad-264">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ecdad-264">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ecdad-265">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ecdad-265">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ecdad-266">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ecdad-266">RELATED LINKS</span></span>

[<span data-ttu-id="ecdad-267">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="ecdad-267">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="ecdad-268">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ecdad-268">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="ecdad-269">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="ecdad-269">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="ecdad-270">Get-Content</span><span class="sxs-lookup"><span data-stu-id="ecdad-270">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="ecdad-271">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ecdad-271">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="ecdad-272">New-Item</span><span class="sxs-lookup"><span data-stu-id="ecdad-272">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="ecdad-273">Set-Content</span><span class="sxs-lookup"><span data-stu-id="ecdad-273">Set-Content</span></span>](Set-Content.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 86702f16683c6710b498a23c072ea9d862868694
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201865"
---
# <span data-ttu-id="84877-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="84877-103">Add-Content</span></span>

## <span data-ttu-id="84877-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="84877-104">SYNOPSIS</span></span>
<span data-ttu-id="84877-105">Ajoute le contenu aux éléments spécifiés (ajout de mots à un fichier, par exemple).</span><span class="sxs-lookup"><span data-stu-id="84877-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="84877-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84877-106">SYNTAX</span></span>

### <span data-ttu-id="84877-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="84877-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="84877-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="84877-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="84877-109">Description</span><span class="sxs-lookup"><span data-stu-id="84877-109">DESCRIPTION</span></span>

<span data-ttu-id="84877-110">L' `Add-Content` applet de commande ajoute du contenu à un élément ou un fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="84877-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="84877-111">Vous pouvez spécifier le contenu en le tapant dans la commande ou en spécifiant un objet renfermant le contenu.</span><span class="sxs-lookup"><span data-stu-id="84877-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="84877-112">Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="84877-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="84877-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="84877-113">EXAMPLES</span></span>

### <span data-ttu-id="84877-114">Exemple 1 : ajouter une chaîne à tous les fichiers texte à l’aide d’une exception</span><span class="sxs-lookup"><span data-stu-id="84877-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="84877-115">Cet exemple ajoute une valeur aux fichiers texte dans le répertoire actif, mais exclut les fichiers en fonction de leur nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="84877-116">Le paramètre **path** spécifie tous les `.txt` fichiers dans le répertoire actif, mais le paramètre **Exclude** ignore les noms de fichiers qui correspondent au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="84877-116">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="84877-117">Le paramètre **value** spécifie la chaîne de texte qui est écrite dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="84877-117">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="84877-118">Exemple 2 : ajouter une date à la fin des fichiers spécifiés</span><span class="sxs-lookup"><span data-stu-id="84877-118">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="84877-119">Cet exemple ajoute la date à des fichiers dans le répertoire actif et affiche la date dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84877-119">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="84877-120">L' `Add-Content` applet de commande crée deux nouveaux fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="84877-120">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="84877-121">Le paramètre **value** contient la sortie de l' `Get-Date` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-121">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="84877-122">Le paramètre **PassThru** génère le contenu ajouté dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="84877-122">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="84877-123">Étant donné qu’il n’existe aucune autre applet de commande pour recevoir la sortie, elle est affichée dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84877-123">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="84877-124">L' `Get-Content` applet de commande affiche le fichier mis à jour, `DateTimeFile1.log` .</span><span class="sxs-lookup"><span data-stu-id="84877-124">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="84877-125">Exemple 3 : ajouter le contenu d’un fichier spécifié dans un autre fichier</span><span class="sxs-lookup"><span data-stu-id="84877-125">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="84877-126">Cet exemple obtient le contenu d’un fichier et stocke le contenu dans une variable.</span><span class="sxs-lookup"><span data-stu-id="84877-126">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="84877-127">La variable est utilisée pour ajouter le contenu dans un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-127">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="84877-128">L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` et stocke le contenu dans la `$From` variable.</span><span class="sxs-lookup"><span data-stu-id="84877-128">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="84877-129">L' `Add-Content` applet de commande met à jour le `CopyToFile.txt` fichier à l’aide du contenu de la `$From` variable.</span><span class="sxs-lookup"><span data-stu-id="84877-129">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="84877-130">L' `Get-Content` applet de commande affiche CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="84877-130">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="84877-131">Exemple 4 : ajouter le contenu d’un fichier spécifié à un autre fichier à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="84877-131">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="84877-132">Cet exemple obtient le contenu d’un fichier et le dirige vers l' `Add-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-132">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="84877-133">L' `Get-Content` applet de commande obtient le contenu de `CopyFromFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="84877-133">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="84877-134">Les résultats sont dirigés vers l’applet de commande `Add-Content` , qui met à jour le `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="84877-134">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="84877-135">La dernière `Get-Content` applet de commande s’affiche `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="84877-135">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="84877-136">Exemple 5 : créer un fichier et copier du contenu</span><span class="sxs-lookup"><span data-stu-id="84877-136">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="84877-137">Cet exemple crée un nouveau fichier et copie le contenu d’un fichier existant dans le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-137">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="84877-138">L' `Add-Content` applet de commande utilise les paramètres **path** et **value** pour créer un nouveau fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="84877-138">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="84877-139">L' `Get-Content` applet de commande obtient le contenu d’un fichier existant `CopyFromFile.txt` et le passe au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="84877-139">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="84877-140">Les parenthèses autour de l' `Get-Content` applet de commande garantissent que la commande se termine avant le début de la `Add-Content` commande.</span><span class="sxs-lookup"><span data-stu-id="84877-140">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="84877-141">L' `Get-Content` applet de commande affiche le contenu du nouveau fichier, `NewFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="84877-141">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="84877-142">Exemple 6 : ajouter du contenu à un fichier en lecture seule</span><span class="sxs-lookup"><span data-stu-id="84877-142">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="84877-143">Cette commande ajoute une valeur au fichier même si l’attribut de fichier **IsReadOnly** a la valeur **true** .</span><span class="sxs-lookup"><span data-stu-id="84877-143">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True** .</span></span>
<span data-ttu-id="84877-144">Les étapes de création d’un fichier en lecture seule sont incluses dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="84877-144">The steps to create a read-only file are included in the example.</span></span>

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

- <span data-ttu-id="84877-145">L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier `IsReadOnlyTextFile.txt` dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="84877-145">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="84877-146">L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-146">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="84877-147">L' `Get-ChildItem` applet de commande indique que le fichier est vide (0) et possède l’attribut de lecture seule ( `r` ).</span><span class="sxs-lookup"><span data-stu-id="84877-147">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="84877-148">L' `Add-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-148">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="84877-149">Le paramètre **value** comprend la chaîne de texte à ajouter au fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-149">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="84877-150">Le paramètre **force** écrit le texte dans le fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="84877-150">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="84877-151">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="84877-151">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="84877-152">Pour supprimer l’attribut de lecture seule, utilisez la `Set-ItemProperty` commande avec le paramètre de **valeur** défini sur `False` .</span><span class="sxs-lookup"><span data-stu-id="84877-152">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="84877-153">Exemple 7 : utiliser des filtres avec Add-Content</span><span class="sxs-lookup"><span data-stu-id="84877-153">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="84877-154">Vous pouvez spécifier un filtre pour l' `Add-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-154">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="84877-155">Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="84877-155">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="84877-156">La commande suivante ajoute le mot « DONE » (terminé) au contenu de tous les `*.txt` fichiers dans le `C:\Temp` répertoire.</span><span class="sxs-lookup"><span data-stu-id="84877-156">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="84877-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84877-157">PARAMETERS</span></span>

### <span data-ttu-id="84877-158">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="84877-158">-AsByteStream</span></span>

<span data-ttu-id="84877-159">Spécifie que le contenu doit être lu en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="84877-159">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="84877-160">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="84877-160">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="84877-161">Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="84877-161">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="84877-162">Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="84877-162">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="84877-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="84877-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="84877-164">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84877-164">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="84877-165">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="84877-165">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="84877-166">-Encoding</span><span class="sxs-lookup"><span data-stu-id="84877-166">-Encoding</span></span>

<span data-ttu-id="84877-167">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="84877-167">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="84877-168">La valeur par défaut est `utf8BOM`.</span><span class="sxs-lookup"><span data-stu-id="84877-168">The default value is `utf8BOM`.</span></span>

<span data-ttu-id="84877-169">L’encodage est un paramètre dynamique que le fournisseur FileSystem ajoute à l’applet de commande `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="84877-169">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="84877-170">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="84877-170">This parameter works only in file system drives.</span></span>

<span data-ttu-id="84877-171">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="84877-171">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="84877-172">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="84877-172">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="84877-173">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="84877-173">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="84877-174">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="84877-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="84877-175">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="84877-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="84877-176">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="84877-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="84877-177">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="84877-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="84877-178">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="84877-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="84877-179">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="84877-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="84877-180">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="84877-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="84877-181">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="84877-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="84877-182">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="84877-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84877-183">-Exclude</span><span class="sxs-lookup"><span data-stu-id="84877-183">-Exclude</span></span>

<span data-ttu-id="84877-184">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="84877-184">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="84877-185">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="84877-185">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="84877-186">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="84877-186">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="84877-187">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="84877-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="84877-188">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="84877-188">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="84877-189">-Filter</span><span class="sxs-lookup"><span data-stu-id="84877-189">-Filter</span></span>

<span data-ttu-id="84877-190">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="84877-190">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="84877-191">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="84877-191">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="84877-192">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="84877-192">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="84877-193">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="84877-193">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="84877-194">-Force</span><span class="sxs-lookup"><span data-stu-id="84877-194">-Force</span></span>

<span data-ttu-id="84877-195">Remplace l'attribut de lecture seule pour que vous puissiez ajouter le contenu à un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="84877-195">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="84877-196">Par exemple, **Force** remplace l’attribut de lecture seule ou crée des répertoires pour compléter un chemin d’accès aux fichiers, mais la commande ne tente pas de modifier les autorisations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="84877-196">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="84877-197">-Include</span><span class="sxs-lookup"><span data-stu-id="84877-197">-Include</span></span>

<span data-ttu-id="84877-198">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="84877-198">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="84877-199">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="84877-199">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="84877-200">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="84877-200">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="84877-201">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="84877-201">Wildcard characters are permitted.</span></span> <span data-ttu-id="84877-202">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="84877-202">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="84877-203">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="84877-203">-LiteralPath</span></span>

<span data-ttu-id="84877-204">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="84877-204">Specifies a path to one or more locations.</span></span> <span data-ttu-id="84877-205">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="84877-205">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="84877-206">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="84877-206">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="84877-207">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="84877-207">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="84877-208">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="84877-208">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="84877-209">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="84877-209">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="84877-210">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="84877-210">-NoNewline</span></span>

<span data-ttu-id="84877-211">Indique que cette applet de commande n’ajoute pas de nouvelle ligne ou de retour chariot au contenu.</span><span class="sxs-lookup"><span data-stu-id="84877-211">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="84877-212">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="84877-212">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="84877-213">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="84877-213">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="84877-214">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="84877-214">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="84877-215">-PassThru</span><span class="sxs-lookup"><span data-stu-id="84877-215">-PassThru</span></span>

<span data-ttu-id="84877-216">Retourne un objet qui représente le contenu ajouté.</span><span class="sxs-lookup"><span data-stu-id="84877-216">Returns an object representing the added content.</span></span> <span data-ttu-id="84877-217">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="84877-217">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="84877-218">-Path</span><span class="sxs-lookup"><span data-stu-id="84877-218">-Path</span></span>

<span data-ttu-id="84877-219">Spécifie le chemin d'accès aux éléments recevant le contenu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="84877-219">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="84877-220">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="84877-220">Wildcard characters are permitted.</span></span>
<span data-ttu-id="84877-221">Les chemins d'accès doivent être ceux des éléments et non des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="84877-221">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="84877-222">Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="84877-222">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="84877-223">Si vous spécifiez plusieurs chemins d'accès, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="84877-223">If you specify multiple paths, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="84877-224">-Stream</span><span class="sxs-lookup"><span data-stu-id="84877-224">-Stream</span></span>

<span data-ttu-id="84877-225">Spécifie un flux de données alternatif pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="84877-225">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="84877-226">Si le flux n’existe pas, cette applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="84877-226">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="84877-227">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="84877-227">Wildcard characters are not supported.</span></span>

<span data-ttu-id="84877-228">**Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="84877-228">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="84877-229">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="84877-229">This parameter works only in file system drives.</span></span>

<span data-ttu-id="84877-230">Vous pouvez utiliser l' `Add-Content` applet de commande pour modifier le contenu du flux de données de remplacement de la **zone. identifier** .</span><span class="sxs-lookup"><span data-stu-id="84877-230">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="84877-231">Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="84877-231">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="84877-232">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-232">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="84877-233">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="84877-233">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="84877-234">-Value</span><span class="sxs-lookup"><span data-stu-id="84877-234">-Value</span></span>

<span data-ttu-id="84877-235">Spécifie le contenu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="84877-235">Specifies the content to be added.</span></span> <span data-ttu-id="84877-236">Tapez une chaîne entre guillemets, telle que **ces données sont destinées à un usage interne uniquement** , ou spécifiez un objet qui contient du contenu, tel que l’objet **DateTime** `Get-Date` généré par.</span><span class="sxs-lookup"><span data-stu-id="84877-236">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="84877-237">Vous ne pouvez pas spécifier le contenu d’un fichier en tapant son chemin d’accès, car il s’agit simplement d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="84877-237">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="84877-238">Vous pouvez utiliser une `Get-Content` commande pour obtenir le contenu et le passer au paramètre **value** .</span><span class="sxs-lookup"><span data-stu-id="84877-238">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

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

### <span data-ttu-id="84877-239">-Confirm</span><span class="sxs-lookup"><span data-stu-id="84877-239">-Confirm</span></span>

<span data-ttu-id="84877-240">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-240">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="84877-241">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="84877-241">-WhatIf</span></span>

<span data-ttu-id="84877-242">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84877-242">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="84877-243">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="84877-243">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="84877-244">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84877-244">CommonParameters</span></span>

<span data-ttu-id="84877-245">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="84877-245">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="84877-246">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="84877-246">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="84877-247">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="84877-247">INPUTS</span></span>

### <span data-ttu-id="84877-248">System. Object, System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="84877-248">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="84877-249">Vous pouvez diriger des valeurs, des chemins d’accès ou des informations d’identification vers `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="84877-249">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="84877-250">SORTIES</span><span class="sxs-lookup"><span data-stu-id="84877-250">OUTPUTS</span></span>

### <span data-ttu-id="84877-251">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="84877-251">None or System.String</span></span>

<span data-ttu-id="84877-252">Quand vous utilisez le paramètre **PassThru** , `Add-Content` génère un objet **System. String** qui représente le contenu.</span><span class="sxs-lookup"><span data-stu-id="84877-252">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="84877-253">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="84877-253">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="84877-254">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="84877-254">NOTES</span></span>

- <span data-ttu-id="84877-255">Quand vous dirigez un objet vers `Add-Content` , l’objet est converti en chaîne avant d’être ajouté à l’élément.</span><span class="sxs-lookup"><span data-stu-id="84877-255">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="84877-256">Le type d'objet détermine le format de la chaîne, mais le format peut être différent de l'affichage par défaut de l'objet.</span><span class="sxs-lookup"><span data-stu-id="84877-256">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="84877-257">Pour contrôler le format de la chaîne, utilisez les paramètres de formatage de l'applet de commande d'envoi.</span><span class="sxs-lookup"><span data-stu-id="84877-257">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="84877-258">Vous pouvez également faire référence à `Add-Content` par son alias intégré, `ac` .</span><span class="sxs-lookup"><span data-stu-id="84877-258">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="84877-259">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="84877-259">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="84877-260">L' `Add-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="84877-260">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="84877-261">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="84877-261">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="84877-262">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="84877-262">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="84877-263">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="84877-263">RELATED LINKS</span></span>

[<span data-ttu-id="84877-264">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="84877-264">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="84877-265">about_Providers</span><span class="sxs-lookup"><span data-stu-id="84877-265">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="84877-266">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="84877-266">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="84877-267">Get-Content</span><span class="sxs-lookup"><span data-stu-id="84877-267">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="84877-268">Get-Item</span><span class="sxs-lookup"><span data-stu-id="84877-268">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="84877-269">New-Item</span><span class="sxs-lookup"><span data-stu-id="84877-269">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="84877-270">Set-Content</span><span class="sxs-lookup"><span data-stu-id="84877-270">Set-Content</span></span>](Set-Content.md)

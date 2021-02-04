---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 2561d569fa773d279e1e54561d6005e3eef7f7e3
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692788"
---
# <span data-ttu-id="d9a8f-102">Set-Content</span><span class="sxs-lookup"><span data-stu-id="d9a8f-102">Set-Content</span></span>

## <span data-ttu-id="d9a8f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d9a8f-103">SYNOPSIS</span></span>
<span data-ttu-id="d9a8f-104">Écrit un nouveau contenu ou remplace le contenu existant dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-104">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="d9a8f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d9a8f-105">SYNTAX</span></span>

### <span data-ttu-id="d9a8f-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d9a8f-106">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="d9a8f-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d9a8f-107">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="d9a8f-108">Description</span><span class="sxs-lookup"><span data-stu-id="d9a8f-108">DESCRIPTION</span></span>

<span data-ttu-id="d9a8f-109">`Set-Content` est une applet de commande de traitement de chaîne qui écrit un nouveau contenu ou remplace le contenu d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-109">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="d9a8f-110">`Set-Content` remplace le contenu existant et diffère de l' `Add-Content` applet de commande qui ajoute le contenu à un fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-110">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="d9a8f-111">Pour envoyer du contenu à `Set-Content` , vous pouvez utiliser le paramètre **value** sur la ligne de commande ou envoyer le contenu via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-111">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="d9a8f-112">Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="d9a8f-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d9a8f-113">EXAMPLES</span></span>

### <span data-ttu-id="d9a8f-114">Exemple 1 : remplacer le contenu de plusieurs fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="d9a8f-114">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="d9a8f-115">Cet exemple remplace le contenu de plusieurs fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-115">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="d9a8f-116">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour répertorier les fichiers **. txt** qui commencent par `Test*` dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-116">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="d9a8f-117">L' `Set-Content` applet de commande utilise le paramètre **path** pour spécifier les `Test*.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-117">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="d9a8f-118">Le paramètre **value** fournit la chaîne de texte **Hello, World** qui remplace le contenu existant dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-118">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="d9a8f-119">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier les `Test*.txt` fichiers et afficher le contenu de chaque fichier dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="d9a8f-120">Exemple 2 : créer un fichier et écrire du contenu</span><span class="sxs-lookup"><span data-stu-id="d9a8f-120">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="d9a8f-121">Cet exemple crée un nouveau fichier et écrit la date et l’heure actuelles dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-121">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="d9a8f-122">`Set-Content` utilise les paramètres de **chemin d’accès** et de **valeur** pour créer un nouveau fichier nommé **DateTime.txt** dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-122">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="d9a8f-123">Le paramètre **value** utilise `Get-Date` pour connaître la date et l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-123">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="d9a8f-124">`Set-Content` écrit l’objet **DateTime** dans le fichier sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-124">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="d9a8f-125">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu de **DateTime.txt** dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-125">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="d9a8f-126">Exemple 3 : remplacer du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="d9a8f-126">Example 3: Replace text in a file</span></span>

<span data-ttu-id="d9a8f-127">Cette commande remplace toutes les instances de Word dans un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-127">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="d9a8f-128">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier **Notice.txt** dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-128">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="d9a8f-129">La `Get-Content` commande est entourée de parenthèses afin que la commande se termine avant d’être envoyée au pipeline.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-129">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="d9a8f-130">Le contenu du fichier **Notice.txt** est envoyé dans le pipeline à l' `ForEach-Object` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-130">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="d9a8f-131">`ForEach-Object` utilise la variable automatique `$_` et remplace chaque occurrence de **Warning** par **prudence**.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-131">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="d9a8f-132">Les objets sont envoyés dans le pipeline à l’applet de commande `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-132">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="d9a8f-133">`Set-Content` utilise le paramètre **path** pour spécifier le fichier **Notice.txt** et écrit le contenu mis à jour dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-133">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="d9a8f-134">La dernière `Get-Content` applet de commande affiche le contenu du fichier mis à jour dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-134">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="d9a8f-135">Exemple 4 : utiliser des filtres avec Set-Content</span><span class="sxs-lookup"><span data-stu-id="d9a8f-135">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="d9a8f-136">Vous pouvez spécifier un filtre pour l' `Set-Content` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-136">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="d9a8f-137">Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-137">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="d9a8f-138">La commande suivante permet de définir le contenu de tous les `*.txt` fichiers du `C:\Temp` répertoire à la **valeur** vide.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-138">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="d9a8f-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9a8f-139">PARAMETERS</span></span>

### <span data-ttu-id="d9a8f-140">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="d9a8f-140">-AsByteStream</span></span>

<span data-ttu-id="d9a8f-141">Spécifie que le contenu doit être lu en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-141">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="d9a8f-142">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-142">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="d9a8f-143">Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-143">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="d9a8f-144">Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-144">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="d9a8f-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="d9a8f-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d9a8f-146">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d9a8f-147">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="d9a8f-148">-Encoding</span><span class="sxs-lookup"><span data-stu-id="d9a8f-148">-Encoding</span></span>

<span data-ttu-id="d9a8f-149">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-149">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="d9a8f-150">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-150">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="d9a8f-151">Encoding est un paramètre dynamique que le fournisseur FileSystem ajoute à `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-151">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="d9a8f-152">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-152">This parameter works only in file system drives.</span></span>

<span data-ttu-id="d9a8f-153">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9a8f-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="d9a8f-154">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-154">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="d9a8f-155">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-155">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="d9a8f-156">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-156">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="d9a8f-157">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-157">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="d9a8f-158">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-158">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="d9a8f-159">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-159">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="d9a8f-160">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="d9a8f-160">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="d9a8f-161">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="d9a8f-161">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="d9a8f-162">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-162">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="d9a8f-163">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-163">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="d9a8f-164">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-164">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="d9a8f-165">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d9a8f-165">-Exclude</span></span>

<span data-ttu-id="d9a8f-166">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-166">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="d9a8f-167">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-167">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d9a8f-168">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-168">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="d9a8f-169">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="d9a8f-170">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-170">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d9a8f-171">-Filter</span><span class="sxs-lookup"><span data-stu-id="d9a8f-171">-Filter</span></span>

<span data-ttu-id="d9a8f-172">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-172">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="d9a8f-173">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-173">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="d9a8f-174">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-174">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="d9a8f-175">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-175">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d9a8f-176">-Force</span><span class="sxs-lookup"><span data-stu-id="d9a8f-176">-Force</span></span>

<span data-ttu-id="d9a8f-177">Force l’applet de commande à définir le contenu d’un fichier, même si le fichier est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-177">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="d9a8f-178">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-178">Implementation varies from provider to provider.</span></span> <span data-ttu-id="d9a8f-179">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="d9a8f-180">Le paramètre **force** ne remplace pas les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-180">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="d9a8f-181">-Include</span><span class="sxs-lookup"><span data-stu-id="d9a8f-181">-Include</span></span>

<span data-ttu-id="d9a8f-182">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-182">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="d9a8f-183">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-183">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d9a8f-184">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-184">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="d9a8f-185">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-185">Wildcard characters are permitted.</span></span> <span data-ttu-id="d9a8f-186">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-186">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d9a8f-187">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d9a8f-187">-LiteralPath</span></span>

<span data-ttu-id="d9a8f-188">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-188">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d9a8f-189">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-189">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="d9a8f-190">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-190">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d9a8f-191">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-191">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d9a8f-192">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-192">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="d9a8f-193">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-193">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d9a8f-194">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="d9a8f-194">-NoNewline</span></span>

<span data-ttu-id="d9a8f-195">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-195">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="d9a8f-196">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-196">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="d9a8f-197">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-197">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="d9a8f-198">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d9a8f-198">-PassThru</span></span>

<span data-ttu-id="d9a8f-199">Retourne un objet qui représente le contenu.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-199">Returns an object that represents the content.</span></span> <span data-ttu-id="d9a8f-200">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-200">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d9a8f-201">-Path</span><span class="sxs-lookup"><span data-stu-id="d9a8f-201">-Path</span></span>

<span data-ttu-id="d9a8f-202">Spécifie le chemin d’accès de l’élément qui reçoit le contenu.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-202">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="d9a8f-203">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-203">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d9a8f-204">-Stream</span><span class="sxs-lookup"><span data-stu-id="d9a8f-204">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="d9a8f-205">Ce paramètre est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-205">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="d9a8f-206">Spécifie un flux de données alternatif pour le contenu.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-206">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="d9a8f-207">Si le flux n’existe pas, cette applet de commande le crée.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-207">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="d9a8f-208">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-208">Wildcard characters are not supported.</span></span>

<span data-ttu-id="d9a8f-209">**Stream** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-209">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="d9a8f-210">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-210">This parameter works only in file system drives.</span></span>

<span data-ttu-id="d9a8f-211">Vous pouvez utiliser l' `Set-Content` applet de commande pour créer ou mettre à jour le contenu de tout autre flux de données, tel que `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-211">You can use the `Set-Content` cmdlet to create or update the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="d9a8f-212">Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-212">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="d9a8f-213">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-213">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="d9a8f-214">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-214">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d9a8f-215">-Value</span><span class="sxs-lookup"><span data-stu-id="d9a8f-215">-Value</span></span>

<span data-ttu-id="d9a8f-216">Spécifie le nouveau contenu pour l'élément.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-216">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="d9a8f-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d9a8f-217">-Confirm</span></span>

<span data-ttu-id="d9a8f-218">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d9a8f-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d9a8f-219">-WhatIf</span></span>

<span data-ttu-id="d9a8f-220">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-220">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d9a8f-221">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d9a8f-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9a8f-222">CommonParameters</span></span>

<span data-ttu-id="d9a8f-223">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9a8f-224">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9a8f-225">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d9a8f-225">INPUTS</span></span>

### <span data-ttu-id="d9a8f-226">System.Object</span><span class="sxs-lookup"><span data-stu-id="d9a8f-226">System.Object</span></span>

<span data-ttu-id="d9a8f-227">Vous pouvez diriger un objet qui contient la nouvelle valeur de l’élément vers `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-227">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="d9a8f-228">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d9a8f-228">OUTPUTS</span></span>

### <span data-ttu-id="d9a8f-229">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="d9a8f-229">None or System.String</span></span>

<span data-ttu-id="d9a8f-230">Quand vous utilisez le paramètre **PassThru** , `Set-Content` génère un objet **System. String** qui représente le contenu.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-230">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="d9a8f-231">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d9a8f-232">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d9a8f-232">NOTES</span></span>

- <span data-ttu-id="d9a8f-233">Vous pouvez également faire référence à `Set-Content` par son alias intégré, `sc` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-233">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="d9a8f-234">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-234">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="d9a8f-235">`Set-Content` est conçu pour le traitement des chaînes.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-235">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="d9a8f-236">Si vous dirigez des objets qui ne sont pas des chaînes vers `Set-Content` , il convertit l’objet en chaîne avant de l’écrire.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-236">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="d9a8f-237">Pour écrire des objets dans des fichiers, utilisez `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-237">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="d9a8f-238">L' `Set-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d9a8f-238">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d9a8f-239">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="d9a8f-239">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="d9a8f-240">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d9a8f-240">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d9a8f-241">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d9a8f-241">RELATED LINKS</span></span>

[<span data-ttu-id="d9a8f-242">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="d9a8f-242">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="d9a8f-243">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="d9a8f-243">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="d9a8f-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d9a8f-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="d9a8f-245">Add-Content</span><span class="sxs-lookup"><span data-stu-id="d9a8f-245">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="d9a8f-246">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="d9a8f-246">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="d9a8f-247">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d9a8f-247">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="d9a8f-248">Get-Content</span><span class="sxs-lookup"><span data-stu-id="d9a8f-248">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="d9a8f-249">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d9a8f-249">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="d9a8f-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="d9a8f-250">New-Item</span></span>](New-Item.md)

---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: 462b90535e33f1822d346dde2b2b1ecb9a790d84
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202881"
---
# <span data-ttu-id="2a174-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-103">Move-Item</span></span>

## <span data-ttu-id="2a174-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2a174-104">SYNOPSIS</span></span>
<span data-ttu-id="2a174-105">Déplace un élément d'un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="2a174-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="2a174-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a174-106">SYNTAX</span></span>

### <span data-ttu-id="2a174-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2a174-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2a174-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2a174-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a174-109">Description</span><span class="sxs-lookup"><span data-stu-id="2a174-109">DESCRIPTION</span></span>

<span data-ttu-id="2a174-110">L' `Move-Item` applet de commande déplace un élément, y compris ses propriétés, son contenu et ses éléments enfants, d’un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="2a174-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="2a174-111">Les emplacements doivent être pris en charge par le même fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2a174-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="2a174-112">Par exemple, elle peut déplacer un fichier ou un sous-répertoire d'un répertoire à un autre ou une sous-clé de Registre d'une clé à une autre.</span><span class="sxs-lookup"><span data-stu-id="2a174-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="2a174-113">Lors du déplacement d'un élément, celui-ci est ajouté au nouvel emplacement et supprimé de l'emplacement d'origine.</span><span class="sxs-lookup"><span data-stu-id="2a174-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="2a174-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2a174-114">EXAMPLES</span></span>

### <span data-ttu-id="2a174-115">Exemple 1 : déplacer un fichier vers un autre répertoire et le renommer</span><span class="sxs-lookup"><span data-stu-id="2a174-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="2a174-116">Cette commande déplace le `Test.txt` fichier du `C:` lecteur vers le `E:\Temp` répertoire et le renomme `test.txt` en `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="2a174-116">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="2a174-117">Exemple 2 : déplacer un répertoire et son contenu vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="2a174-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="2a174-118">Cette commande déplace le `C:\Temp` répertoire et son contenu vers le `C:\Logs` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2a174-118">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="2a174-119">Le répertoire « Temp », ainsi que tous ses sous-répertoires et fichiers, apparaissent dans le répertoire « logs ».</span><span class="sxs-lookup"><span data-stu-id="2a174-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="2a174-120">Exemple 3 : déplacer tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="2a174-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="2a174-121">Cette commande déplace tous les fichiers texte ( `*.txt` ) dans le répertoire actif (représenté par un point ( `.` )) vers le `C:\Logs` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2a174-121">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="2a174-122">Exemple 4 : déplacer de manière récursive tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="2a174-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="2a174-123">Cette commande déplace tous les fichiers texte du répertoire actif et de tous ses sous-répertoires, de manière récursive, vers le répertoire « C:\Textfiles. ».</span><span class="sxs-lookup"><span data-stu-id="2a174-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="2a174-124">La commande utilise l' `Get-ChildItem` applet de commande pour obtenir tous les éléments enfants dans le répertoire actif (représenté par le \[ point \] ) et ses sous-répertoires qui ont une *extension de nom de fichier « . txt ». Elle utilise le paramètre **recurse** pour rendre la récupération récursive et le paramètre Include pour limiter la récupération aux fichiers «* . txt ».</span><span class="sxs-lookup"><span data-stu-id="2a174-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "* .txt" files.</span></span>

<span data-ttu-id="2a174-125">L’opérateur de pipeline ( `|` ) envoie les résultats de cette commande à `Move-Item` , qui déplace les fichiers texte vers le répertoire « textfiles ».</span><span class="sxs-lookup"><span data-stu-id="2a174-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="2a174-126">Si les fichiers à déplacer vers « C:\Textfiles. » portent le même nom, `Move-Item` affiche une erreur et se poursuit, mais il déplace un seul fichier avec chaque nom à « c:\Textfiles. ».</span><span class="sxs-lookup"><span data-stu-id="2a174-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="2a174-127">Les autres fichiers restent dans les répertoires d'origine.</span><span class="sxs-lookup"><span data-stu-id="2a174-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="2a174-128">Si le répertoire « Textfiles » (ou tout autre élément du chemin d’accès de destination) n’existe pas, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2a174-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="2a174-129">Le répertoire manquant n’est pas créé pour vous, même si vous utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="2a174-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="2a174-130">`Move-Item` déplace le premier élément vers un fichier appelé « Textfiles », puis affiche une erreur expliquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="2a174-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="2a174-131">De même, par défaut, `Get-ChildItem` ne déplace pas les fichiers masqués.</span><span class="sxs-lookup"><span data-stu-id="2a174-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="2a174-132">Pour déplacer des fichiers masqués, utilisez le paramètre **force** avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2a174-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="2a174-133">Dans Windows PowerShell 2,0, quand vous utilisez le paramètre **recurse** de l’applet de commande `Get-ChildItem` , la valeur du paramètre **path** doit être un conteneur.</span><span class="sxs-lookup"><span data-stu-id="2a174-133">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="2a174-134">Utilisez le paramètre **Include** pour spécifier le filtre d'extension de nom de fichier .txt (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span><span class="sxs-lookup"><span data-stu-id="2a174-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="2a174-135">Exemple 5 : déplacer des clés et des valeurs de Registre vers une autre clé</span><span class="sxs-lookup"><span data-stu-id="2a174-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="2a174-136">Cette commande déplace les clés et les valeurs de registre de la clé de Registre « MyCompany » dans `HKLM\Software` vers la clé « MyNewCompany ».</span><span class="sxs-lookup"><span data-stu-id="2a174-136">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="2a174-137">Le caractère générique ( `*` ) indique que le contenu de la clé « MyCompany » doit être déplacé, et non la clé elle-même.</span><span class="sxs-lookup"><span data-stu-id="2a174-137">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="2a174-138">Dans cette commande, les noms de paramètres facultatifs **path** et **destination** sont omis.</span><span class="sxs-lookup"><span data-stu-id="2a174-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="2a174-139">Exemple 6 : déplacer un répertoire et son contenu vers un sous-répertoire du répertoire spécifié</span><span class="sxs-lookup"><span data-stu-id="2a174-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="2a174-140">Cette commande déplace le répertoire « logs \[ septembre \` 06 \] » (et son contenu) dans le répertoire « logs \[ 2006 \] ».</span><span class="sxs-lookup"><span data-stu-id="2a174-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="2a174-141">Le paramètre **LiteralPath** est utilisé à la place de **path** , car le nom du répertoire d’origine comprend les parenthèses ouvrante et fermante (« \[ » et «» \] ).</span><span class="sxs-lookup"><span data-stu-id="2a174-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="2a174-142">Le chemin d’accès est également placé entre guillemets simples (' '), afin que le symbole de la contre-impulsion ( \` ) ne soit pas interprété à tort.</span><span class="sxs-lookup"><span data-stu-id="2a174-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="2a174-143">Le paramètre **destination** ne requiert pas de chemin d’accès littéral, car la variable de destination doit également être placée entre guillemets simples, car elle comprend des crochets qui peuvent être mal interprétés.</span><span class="sxs-lookup"><span data-stu-id="2a174-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="2a174-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a174-144">PARAMETERS</span></span>

### <span data-ttu-id="2a174-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="2a174-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2a174-146">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a174-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2a174-147">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2a174-148">-Destination</span><span class="sxs-lookup"><span data-stu-id="2a174-148">-Destination</span></span>

<span data-ttu-id="2a174-149">Spécifie le chemin d'accès à l'emplacement vers lequel les éléments sont déplacés.</span><span class="sxs-lookup"><span data-stu-id="2a174-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="2a174-150">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2a174-150">The default is the current directory.</span></span>
<span data-ttu-id="2a174-151">Les caractères génériques sont autorisés, mais le résultat doit spécifier un seul emplacement.</span><span class="sxs-lookup"><span data-stu-id="2a174-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="2a174-152">Pour renommer l’élément déplacé, spécifiez un nouveau nom dans la valeur du paramètre **destination** .</span><span class="sxs-lookup"><span data-stu-id="2a174-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2a174-153">-Exclude</span><span class="sxs-lookup"><span data-stu-id="2a174-153">-Exclude</span></span>

<span data-ttu-id="2a174-154">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="2a174-154">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2a174-155">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="2a174-155">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2a174-156">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2a174-156">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2a174-157">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2a174-157">Wildcard characters are permitted.</span></span> <span data-ttu-id="2a174-158">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2a174-158">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2a174-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="2a174-159">-Filter</span></span>

<span data-ttu-id="2a174-160">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="2a174-160">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2a174-161">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="2a174-161">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2a174-162">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-162">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2a174-163">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="2a174-163">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="2a174-164">-Force</span><span class="sxs-lookup"><span data-stu-id="2a174-164">-Force</span></span>

<span data-ttu-id="2a174-165">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2a174-165">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="2a174-166">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="2a174-166">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="2a174-167">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="2a174-168">-Include</span><span class="sxs-lookup"><span data-stu-id="2a174-168">-Include</span></span>

<span data-ttu-id="2a174-169">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="2a174-169">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2a174-170">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="2a174-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2a174-171">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="2a174-171">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2a174-172">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2a174-172">Wildcard characters are permitted.</span></span> <span data-ttu-id="2a174-173">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2a174-173">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2a174-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2a174-174">-LiteralPath</span></span>

<span data-ttu-id="2a174-175">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="2a174-175">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2a174-176">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="2a174-176">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2a174-177">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="2a174-177">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2a174-178">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="2a174-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2a174-179">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="2a174-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2a174-180">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="2a174-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2a174-181">-PassThru</span></span>

<span data-ttu-id="2a174-182">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="2a174-182">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="2a174-183">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="2a174-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2a174-184">-Path</span><span class="sxs-lookup"><span data-stu-id="2a174-184">-Path</span></span>

<span data-ttu-id="2a174-185">Spécifie le chemin d'accès à l'emplacement actuel des éléments.</span><span class="sxs-lookup"><span data-stu-id="2a174-185">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="2a174-186">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="2a174-186">The default is the current directory.</span></span>
<span data-ttu-id="2a174-187">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2a174-187">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2a174-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a174-188">-Confirm</span></span>

<span data-ttu-id="2a174-189">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2a174-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2a174-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a174-190">-WhatIf</span></span>

<span data-ttu-id="2a174-191">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2a174-191">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2a174-192">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2a174-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2a174-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a174-193">CommonParameters</span></span>

<span data-ttu-id="2a174-194">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2a174-194">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2a174-195">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2a174-196">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2a174-196">INPUTS</span></span>

### <span data-ttu-id="2a174-197">System.String</span><span class="sxs-lookup"><span data-stu-id="2a174-197">System.String</span></span>

<span data-ttu-id="2a174-198">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2a174-198">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="2a174-199">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2a174-199">OUTPUTS</span></span>

### <span data-ttu-id="2a174-200">Aucun ou un objet représentant l’élément déplacé</span><span class="sxs-lookup"><span data-stu-id="2a174-200">None or an object representing the moved item</span></span>

<span data-ttu-id="2a174-201">Quand vous utilisez le paramètre *PassThru* , cette applet de commande génère un objet représentant l’élément déplacé.</span><span class="sxs-lookup"><span data-stu-id="2a174-201">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="2a174-202">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="2a174-202">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2a174-203">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2a174-203">NOTES</span></span>

- <span data-ttu-id="2a174-204">Cette applet de commande déplace les fichiers entre les lecteurs pris en charge par le même fournisseur, mais elle déplace les répertoires uniquement dans le même lecteur.</span><span class="sxs-lookup"><span data-stu-id="2a174-204">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="2a174-205">Étant donné qu’une `Move-Item` commande déplace les propriétés, le contenu et les éléments enfants d’un élément, tous les déplacements sont récursifs par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a174-205">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="2a174-206">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2a174-206">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="2a174-207">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2a174-207">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="2a174-208">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2a174-208">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2a174-209">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2a174-209">RELATED LINKS</span></span>

[<span data-ttu-id="2a174-210">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-210">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="2a174-211">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-211">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="2a174-212">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-212">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="2a174-213">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-213">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="2a174-214">New-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-214">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="2a174-215">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-215">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="2a174-216">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-216">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="2a174-217">Set-Item</span><span class="sxs-lookup"><span data-stu-id="2a174-217">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="2a174-218">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2a174-218">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

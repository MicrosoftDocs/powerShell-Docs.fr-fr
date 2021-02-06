---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599010"
---
# <span data-ttu-id="09b56-102">Move-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-102">Move-Item</span></span>

## <span data-ttu-id="09b56-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="09b56-103">SYNOPSIS</span></span>
<span data-ttu-id="09b56-104">Déplace un élément d'un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="09b56-104">Moves an item from one location to another.</span></span>

## <span data-ttu-id="09b56-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="09b56-105">SYNTAX</span></span>

### <span data-ttu-id="09b56-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="09b56-106">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="09b56-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="09b56-107">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="09b56-108">Description</span><span class="sxs-lookup"><span data-stu-id="09b56-108">DESCRIPTION</span></span>

<span data-ttu-id="09b56-109">L' `Move-Item` applet de commande déplace un élément, y compris ses propriétés, son contenu et ses éléments enfants, d’un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="09b56-109">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="09b56-110">Les emplacements doivent être pris en charge par le même fournisseur.</span><span class="sxs-lookup"><span data-stu-id="09b56-110">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="09b56-111">Par exemple, elle peut déplacer un fichier ou un sous-répertoire d'un répertoire à un autre ou une sous-clé de Registre d'une clé à une autre.</span><span class="sxs-lookup"><span data-stu-id="09b56-111">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="09b56-112">Lors du déplacement d'un élément, celui-ci est ajouté au nouvel emplacement et supprimé de l'emplacement d'origine.</span><span class="sxs-lookup"><span data-stu-id="09b56-112">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="09b56-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="09b56-113">EXAMPLES</span></span>

### <span data-ttu-id="09b56-114">Exemple 1 : déplacer un fichier vers un autre répertoire et le renommer</span><span class="sxs-lookup"><span data-stu-id="09b56-114">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="09b56-115">Cette commande déplace le `Test.txt` fichier du `C:` lecteur vers le `E:\Temp` répertoire et le renomme `test.txt` en `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="09b56-115">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="09b56-116">Exemple 2 : déplacer un répertoire et son contenu vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="09b56-116">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="09b56-117">Cette commande déplace le `C:\Temp` répertoire et son contenu vers le `C:\Logs` répertoire.</span><span class="sxs-lookup"><span data-stu-id="09b56-117">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="09b56-118">Le répertoire « Temp », ainsi que tous ses sous-répertoires et fichiers, apparaissent dans le répertoire « logs ».</span><span class="sxs-lookup"><span data-stu-id="09b56-118">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="09b56-119">Exemple 3 : déplacer tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="09b56-119">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="09b56-120">Cette commande déplace tous les fichiers texte ( `*.txt` ) dans le répertoire actif (représenté par un point ( `.` )) vers le `C:\Logs` répertoire.</span><span class="sxs-lookup"><span data-stu-id="09b56-120">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="09b56-121">Exemple 4 : déplacer de manière récursive tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="09b56-121">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="09b56-122">Cette commande déplace tous les fichiers texte du répertoire actif et de tous ses sous-répertoires, de manière récursive, vers le répertoire « C:\Textfiles. ».</span><span class="sxs-lookup"><span data-stu-id="09b56-122">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="09b56-123">La commande utilise l' `Get-ChildItem` applet de commande pour obtenir tous les éléments enfants dans le répertoire actif (représenté par le \[ point \] ) et ses sous-répertoires qui ont une *extension de nom de fichier « . txt ». Elle utilise le paramètre **recurse** pour rendre la récupération récursive et le paramètre Include pour limiter la récupération aux fichiers «*. txt ».</span><span class="sxs-lookup"><span data-stu-id="09b56-123">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a "*.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="09b56-124">L’opérateur de pipeline ( `|` ) envoie les résultats de cette commande à `Move-Item` , qui déplace les fichiers texte vers le répertoire « textfiles ».</span><span class="sxs-lookup"><span data-stu-id="09b56-124">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="09b56-125">Si les fichiers à déplacer vers « C:\Textfiles. » portent le même nom, `Move-Item` affiche une erreur et se poursuit, mais il déplace un seul fichier avec chaque nom à « c:\Textfiles. ».</span><span class="sxs-lookup"><span data-stu-id="09b56-125">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="09b56-126">Les autres fichiers restent dans les répertoires d'origine.</span><span class="sxs-lookup"><span data-stu-id="09b56-126">The other files remain in their original directories.</span></span>

<span data-ttu-id="09b56-127">Si le répertoire « Textfiles » (ou tout autre élément du chemin d’accès de destination) n’existe pas, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="09b56-127">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="09b56-128">Le répertoire manquant n’est pas créé pour vous, même si vous utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="09b56-128">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="09b56-129">`Move-Item` déplace le premier élément vers un fichier appelé « Textfiles », puis affiche une erreur expliquant que le fichier existe déjà.</span><span class="sxs-lookup"><span data-stu-id="09b56-129">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="09b56-130">De même, par défaut, `Get-ChildItem` ne déplace pas les fichiers masqués.</span><span class="sxs-lookup"><span data-stu-id="09b56-130">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="09b56-131">Pour déplacer des fichiers masqués, utilisez le paramètre **force** avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="09b56-131">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="09b56-132">Dans Windows PowerShell 2,0, quand vous utilisez le paramètre **recurse** de l’applet de commande `Get-ChildItem` , la valeur du paramètre **path** doit être un conteneur.</span><span class="sxs-lookup"><span data-stu-id="09b56-132">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="09b56-133">Utilisez le paramètre **Include** pour spécifier le filtre d'extension de nom de fichier .txt (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span><span class="sxs-lookup"><span data-stu-id="09b56-133">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="09b56-134">Exemple 5 : déplacer des clés et des valeurs de Registre vers une autre clé</span><span class="sxs-lookup"><span data-stu-id="09b56-134">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="09b56-135">Cette commande déplace les clés et les valeurs de registre de la clé de Registre « MyCompany » dans `HKLM\Software` vers la clé « MyNewCompany ».</span><span class="sxs-lookup"><span data-stu-id="09b56-135">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="09b56-136">Le caractère générique ( `*` ) indique que le contenu de la clé « MyCompany » doit être déplacé, et non la clé elle-même.</span><span class="sxs-lookup"><span data-stu-id="09b56-136">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="09b56-137">Dans cette commande, les noms de paramètres facultatifs **path** et **destination** sont omis.</span><span class="sxs-lookup"><span data-stu-id="09b56-137">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="09b56-138">Exemple 6 : déplacer un répertoire et son contenu vers un sous-répertoire du répertoire spécifié</span><span class="sxs-lookup"><span data-stu-id="09b56-138">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="09b56-139">Cette commande déplace le répertoire « logs \[ septembre \` 06 \] » (et son contenu) dans le répertoire « logs \[ 2006 \] ».</span><span class="sxs-lookup"><span data-stu-id="09b56-139">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="09b56-140">Le paramètre **LiteralPath** est utilisé à la place de **path**, car le nom du répertoire d’origine comprend les parenthèses ouvrante et fermante (« \[ » et «» \] ).</span><span class="sxs-lookup"><span data-stu-id="09b56-140">The **LiteralPath** parameter is used instead of **Path**, because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="09b56-141">Le chemin d’accès est également placé entre guillemets simples (' '), afin que le symbole de la contre-impulsion ( \` ) ne soit pas interprété à tort.</span><span class="sxs-lookup"><span data-stu-id="09b56-141">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="09b56-142">Le paramètre **destination** ne requiert pas de chemin d’accès littéral, car la variable de destination doit également être placée entre guillemets simples, car elle comprend des crochets qui peuvent être mal interprétés.</span><span class="sxs-lookup"><span data-stu-id="09b56-142">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="09b56-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09b56-143">PARAMETERS</span></span>

### <span data-ttu-id="09b56-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="09b56-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="09b56-145">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09b56-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="09b56-146">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="09b56-147">-Destination</span><span class="sxs-lookup"><span data-stu-id="09b56-147">-Destination</span></span>

<span data-ttu-id="09b56-148">Spécifie le chemin d'accès à l'emplacement vers lequel les éléments sont déplacés.</span><span class="sxs-lookup"><span data-stu-id="09b56-148">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="09b56-149">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="09b56-149">The default is the current directory.</span></span>
<span data-ttu-id="09b56-150">Les caractères génériques sont autorisés, mais le résultat doit spécifier un seul emplacement.</span><span class="sxs-lookup"><span data-stu-id="09b56-150">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="09b56-151">Pour renommer l’élément déplacé, spécifiez un nouveau nom dans la valeur du paramètre **destination** .</span><span class="sxs-lookup"><span data-stu-id="09b56-151">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

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

### <span data-ttu-id="09b56-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="09b56-152">-Exclude</span></span>

<span data-ttu-id="09b56-153">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="09b56-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="09b56-154">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="09b56-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="09b56-155">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="09b56-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="09b56-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09b56-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="09b56-157">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="09b56-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="09b56-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="09b56-158">-Filter</span></span>

<span data-ttu-id="09b56-159">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="09b56-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="09b56-160">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="09b56-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="09b56-161">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-161">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="09b56-162">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="09b56-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="09b56-163">-Force</span><span class="sxs-lookup"><span data-stu-id="09b56-163">-Force</span></span>

<span data-ttu-id="09b56-164">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="09b56-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="09b56-165">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="09b56-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="09b56-166">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="09b56-167">-Include</span><span class="sxs-lookup"><span data-stu-id="09b56-167">-Include</span></span>

<span data-ttu-id="09b56-168">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="09b56-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="09b56-169">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="09b56-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="09b56-170">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="09b56-170">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="09b56-171">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09b56-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="09b56-172">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="09b56-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="09b56-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="09b56-173">-LiteralPath</span></span>

<span data-ttu-id="09b56-174">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="09b56-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="09b56-175">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="09b56-175">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="09b56-176">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="09b56-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="09b56-177">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="09b56-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="09b56-178">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="09b56-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="09b56-179">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="09b56-180">-PassThru</span><span class="sxs-lookup"><span data-stu-id="09b56-180">-PassThru</span></span>

<span data-ttu-id="09b56-181">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="09b56-181">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="09b56-182">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="09b56-182">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="09b56-183">-Path</span><span class="sxs-lookup"><span data-stu-id="09b56-183">-Path</span></span>

<span data-ttu-id="09b56-184">Spécifie le chemin d'accès à l'emplacement actuel des éléments.</span><span class="sxs-lookup"><span data-stu-id="09b56-184">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="09b56-185">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="09b56-185">The default is the current directory.</span></span>
<span data-ttu-id="09b56-186">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="09b56-186">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="09b56-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="09b56-187">-Confirm</span></span>

<span data-ttu-id="09b56-188">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09b56-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="09b56-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="09b56-189">-WhatIf</span></span>

<span data-ttu-id="09b56-190">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09b56-190">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="09b56-191">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="09b56-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="09b56-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09b56-192">CommonParameters</span></span>

<span data-ttu-id="09b56-193">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="09b56-193">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="09b56-194">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="09b56-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="09b56-195">INPUTS</span></span>

### <span data-ttu-id="09b56-196">System.String</span><span class="sxs-lookup"><span data-stu-id="09b56-196">System.String</span></span>

<span data-ttu-id="09b56-197">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="09b56-197">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="09b56-198">SORTIES</span><span class="sxs-lookup"><span data-stu-id="09b56-198">OUTPUTS</span></span>

### <span data-ttu-id="09b56-199">Aucun ou un objet représentant l’élément déplacé</span><span class="sxs-lookup"><span data-stu-id="09b56-199">None or an object representing the moved item</span></span>

<span data-ttu-id="09b56-200">Quand vous utilisez le paramètre *PassThru* , cette applet de commande génère un objet représentant l’élément déplacé.</span><span class="sxs-lookup"><span data-stu-id="09b56-200">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="09b56-201">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="09b56-201">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="09b56-202">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="09b56-202">NOTES</span></span>

- <span data-ttu-id="09b56-203">Cette applet de commande déplace les fichiers entre les lecteurs pris en charge par le même fournisseur, mais elle déplace les répertoires uniquement dans le même lecteur.</span><span class="sxs-lookup"><span data-stu-id="09b56-203">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="09b56-204">Étant donné qu’une `Move-Item` commande déplace les propriétés, le contenu et les éléments enfants d’un élément, tous les déplacements sont récursifs par défaut.</span><span class="sxs-lookup"><span data-stu-id="09b56-204">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="09b56-205">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="09b56-205">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="09b56-206">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="09b56-206">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="09b56-207">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="09b56-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="09b56-208">RELATED LINKS</span></span>

[<span data-ttu-id="09b56-209">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="09b56-210">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="09b56-211">Get-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-211">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="09b56-212">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="09b56-213">New-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="09b56-214">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="09b56-215">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="09b56-216">Set-Item</span><span class="sxs-lookup"><span data-stu-id="09b56-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="09b56-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="09b56-217">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)


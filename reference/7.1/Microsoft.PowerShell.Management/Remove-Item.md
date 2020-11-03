---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 3d33f0e3ab859d839b22a49a88860624ae06ddf2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202062"
---
# <span data-ttu-id="076c8-103">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-103">Remove-Item</span></span>

## <span data-ttu-id="076c8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="076c8-104">SYNOPSIS</span></span>
<span data-ttu-id="076c8-105">Supprime les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="076c8-105">Deletes the specified items.</span></span>

## <span data-ttu-id="076c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="076c8-106">SYNTAX</span></span>

### <span data-ttu-id="076c8-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="076c8-107">Path (Default)</span></span>

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="076c8-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="076c8-108">LiteralPath</span></span>

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="076c8-109">Description</span><span class="sxs-lookup"><span data-stu-id="076c8-109">DESCRIPTION</span></span>

<span data-ttu-id="076c8-110">L' `Remove-Item` applet de commande supprime un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="076c8-110">The `Remove-Item` cmdlet deletes one or more items.</span></span> <span data-ttu-id="076c8-111">Étant donné qu’il est pris en charge par de nombreux fournisseurs, il peut supprimer de nombreux types d’éléments différents, y compris des fichiers, des dossiers, des clés de Registre, des variables, des alias et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="076c8-111">Because it is supported by many providers, it can delete many different types of items, including files, folders, registry keys, variables, aliases, and functions.</span></span>

## <span data-ttu-id="076c8-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="076c8-112">EXAMPLES</span></span>

### <span data-ttu-id="076c8-113">Exemple 1 : supprimer les fichiers qui ont une extension de nom de fichier</span><span class="sxs-lookup"><span data-stu-id="076c8-113">Example 1: Delete files that have any file name extension</span></span>

<span data-ttu-id="076c8-114">Cet exemple supprime tous les fichiers dont le nom contient un point ( `.` ) du `C:\Test` dossier.</span><span class="sxs-lookup"><span data-stu-id="076c8-114">This example deletes all of the files that have names that include a dot (`.`) from the `C:\Test` folder.</span></span> <span data-ttu-id="076c8-115">Étant donné que la commande spécifie un point, la commande ne supprime pas les dossiers ou les fichiers qui n’ont pas d’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="076c8-115">Because the command specifies a dot, the command does not delete folders or files that have no file name extension.</span></span>

```powershell
Remove-Item C:\Test\*.*
```

### <span data-ttu-id="076c8-116">Exemple 2 : supprimer certains fichiers de document dans un dossier</span><span class="sxs-lookup"><span data-stu-id="076c8-116">Example 2: Delete some of the document files in a folder</span></span>

<span data-ttu-id="076c8-117">Cet exemple supprime du dossier actif tous les fichiers qui ont une `.doc` extension de nom de fichier et un nom qui n’inclut pas `*1*` .</span><span class="sxs-lookup"><span data-stu-id="076c8-117">This example deletes from the current folder all files that have a `.doc` file name extension and a name that does not include `*1*`.</span></span>

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

<span data-ttu-id="076c8-118">Elle utilise le caractère générique ( `*` ) pour spécifier le contenu du dossier actif.</span><span class="sxs-lookup"><span data-stu-id="076c8-118">It uses the wildcard character (`*`) to specify the contents of the current folder.</span></span> <span data-ttu-id="076c8-119">Elle utilise les paramètres **include** et **Exclude** pour spécifier les fichiers à supprimer.</span><span class="sxs-lookup"><span data-stu-id="076c8-119">It uses the **Include** and **Exclude** parameters to specify the files to delete.</span></span>

### <span data-ttu-id="076c8-120">Exemple 3 : supprimer les fichiers masqués et en lecture seule</span><span class="sxs-lookup"><span data-stu-id="076c8-120">Example 3: Delete hidden, read-only files</span></span>

<span data-ttu-id="076c8-121">Cette commande supprime un fichier qui est à la fois *masqué* et *en lecture seule* .</span><span class="sxs-lookup"><span data-stu-id="076c8-121">This command deletes a file that is both *hidden* and *read-only* .</span></span>

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

<span data-ttu-id="076c8-122">Elle utilise le paramètre **path** pour spécifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="076c8-122">It uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="076c8-123">Elle utilise le paramètre **force** pour la supprimer.</span><span class="sxs-lookup"><span data-stu-id="076c8-123">It uses the **Force** parameter to delete it.</span></span> <span data-ttu-id="076c8-124">Sans **force** , vous ne pouvez pas supprimer les fichiers _cachés_ ou _en lecture seule_ .</span><span class="sxs-lookup"><span data-stu-id="076c8-124">Without **Force** , you cannot delete _read-only_ or _hidden_ files.</span></span>

### <span data-ttu-id="076c8-125">Exemple 4 : supprimer des fichiers dans des sous-dossiers de manière récursive</span><span class="sxs-lookup"><span data-stu-id="076c8-125">Example 4: Delete files in subfolders recursively</span></span>

<span data-ttu-id="076c8-126">Cette commande supprime de manière récursive tous les fichiers CSV dans le dossier actif et tous les sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="076c8-126">This command deletes all of the CSV files in the current folder and all subfolders recursively.</span></span>

<span data-ttu-id="076c8-127">Étant donné que le paramètre **recurse** dans `Remove-Item` présente un problème connu, la commande de cet exemple utilise `Get-ChildItem` pour obtenir les fichiers souhaités, puis utilise l’opérateur de pipeline pour les passer à `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="076c8-127">Because the **Recurse** parameter in `Remove-Item` has a known issue, the command in this example uses `Get-ChildItem` to get the desired files, and then uses the pipeline operator to pass them to `Remove-Item`.</span></span>

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

<span data-ttu-id="076c8-128">Dans la `Get-ChildItem` commande, **path** a la valeur ( `*` ), qui représente le contenu du dossier actif.</span><span class="sxs-lookup"><span data-stu-id="076c8-128">In the `Get-ChildItem` command, **Path** has a value of (`*`), which represents the contents of the current folder.</span></span> <span data-ttu-id="076c8-129">Elle utilise **include** pour spécifier le type de fichier CSV et utilise **recurse** pour rendre la récupération récursive.</span><span class="sxs-lookup"><span data-stu-id="076c8-129">It uses **Include** to specify the CSV file type, and it uses **Recurse** to make the retrieval recursive.</span></span> <span data-ttu-id="076c8-130">Si vous essayez de spécifier le type de fichier, par exemple `-Path *.csv` , l’applet de commande interprète l’objet de la recherche comme étant un fichier qui n’a pas d’élément enfant, et **recurse** échoue.</span><span class="sxs-lookup"><span data-stu-id="076c8-130">If you try to specify the file type the path, such as `-Path *.csv`, the cmdlet interprets the subject of the search to be a file that has no child items, and **Recurse** fails.</span></span>

### <span data-ttu-id="076c8-131">Exemple 5 : supprimer les sous-clés de manière récursive</span><span class="sxs-lookup"><span data-stu-id="076c8-131">Example 5: Delete subkeys recursively</span></span>

<span data-ttu-id="076c8-132">Cette commande supprime la clé de Registre « OldApp » et toutes ses sous-clés et valeurs.</span><span class="sxs-lookup"><span data-stu-id="076c8-132">This command deletes the "OldApp" registry key and all its subkeys and values.</span></span> <span data-ttu-id="076c8-133">Elle utilise `Remove-Item` pour supprimer la clé.</span><span class="sxs-lookup"><span data-stu-id="076c8-133">It uses `Remove-Item` to remove the key.</span></span> <span data-ttu-id="076c8-134">Le chemin d’accès est spécifié, mais le nom de paramètre facultatif ( **path** ) est omis.</span><span class="sxs-lookup"><span data-stu-id="076c8-134">The path is specified, but the optional parameter name ( **Path** ) is omitted.</span></span>

<span data-ttu-id="076c8-135">Le paramètre **recurse** supprime tout le contenu de la clé « OldApp » de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="076c8-135">The **Recurse** parameter deletes all of the contents of the "OldApp" key recursively.</span></span> <span data-ttu-id="076c8-136">Si la clé contient des sous-clés et que vous omettez le paramètre **recurse** , vous êtes invité à confirmer que vous souhaitez supprimer le contenu de la clé.</span><span class="sxs-lookup"><span data-stu-id="076c8-136">If the key contains subkeys and you omit the **Recurse** parameter, you are prompted to confirm that you want to delete the contents of the key.</span></span>

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### <span data-ttu-id="076c8-137">Exemple 6 : suppression de fichiers avec des caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="076c8-137">Example 6: Deleting files with special characters</span></span>

<span data-ttu-id="076c8-138">L’exemple suivant montre comment supprimer des fichiers qui contiennent des caractères spéciaux, tels que des crochets ou des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="076c8-138">The following example shows how to delete files that contain special characters like brackets or parentheses.</span></span>

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### <span data-ttu-id="076c8-139">Exemple 7 : supprimer un flux de données de remplacement</span><span class="sxs-lookup"><span data-stu-id="076c8-139">Example 7: Remove an alternate data stream</span></span>

<span data-ttu-id="076c8-140">Cet exemple montre comment utiliser le paramètre dynamique **Stream** de l' `Remove-Item` applet de commande pour supprimer un autre flux de données.</span><span class="sxs-lookup"><span data-stu-id="076c8-140">This example shows how to use the **Stream** dynamic parameter of the `Remove-Item` cmdlet to delete an alternate data stream.</span></span> <span data-ttu-id="076c8-141">Le paramètre Stream est introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="076c8-141">The stream parameter is introduced in Windows PowerShell 3.0.</span></span>

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

<span data-ttu-id="076c8-142">Le **Stream** paramètre Stream `Get-Item` obtient le flux de **zone. identificateur** du `Copy-Script.ps1` fichier.</span><span class="sxs-lookup"><span data-stu-id="076c8-142">The **Stream** parameter `Get-Item` gets the **Zone.Identifier** stream of the `Copy-Script.ps1` file.</span></span> <span data-ttu-id="076c8-143">`Remove-Item` utilise le paramètre **Stream** pour supprimer le flux de **zone. identifier** du fichier.</span><span class="sxs-lookup"><span data-stu-id="076c8-143">`Remove-Item` uses the **Stream** parameter to remove the **Zone.Identifier** stream of the file.</span></span> <span data-ttu-id="076c8-144">Enfin, l' `Get-Item` applet de commande indique que le flux de **zone. identifier** a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="076c8-144">Finally, the `Get-Item` cmdlet shows that the **Zone.Identifier** stream was deleted.</span></span>

## <span data-ttu-id="076c8-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="076c8-145">PARAMETERS</span></span>

### <span data-ttu-id="076c8-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="076c8-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="076c8-147">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="076c8-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="076c8-148">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="076c8-149">-Exclude</span><span class="sxs-lookup"><span data-stu-id="076c8-149">-Exclude</span></span>

<span data-ttu-id="076c8-150">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="076c8-150">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="076c8-151">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="076c8-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="076c8-152">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="076c8-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="076c8-153">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="076c8-153">Wildcard characters are permitted.</span></span> <span data-ttu-id="076c8-154">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="076c8-154">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="076c8-155">-Filter</span><span class="sxs-lookup"><span data-stu-id="076c8-155">-Filter</span></span>

<span data-ttu-id="076c8-156">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="076c8-156">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="076c8-157">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="076c8-157">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="076c8-158">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-158">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="076c8-159">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="076c8-159">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="076c8-160">-Force</span><span class="sxs-lookup"><span data-stu-id="076c8-160">-Force</span></span>

<span data-ttu-id="076c8-161">Force l’applet de commande à supprimer des éléments qui ne peuvent pas être modifiés autrement, tels que des fichiers cachés ou en lecture seule ou des alias ou des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="076c8-161">Forces the cmdlet to remove items that cannot otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="076c8-162">L’applet de commande ne peut pas modifier des alias ou variables constants.</span><span class="sxs-lookup"><span data-stu-id="076c8-162">The cmdlet cannot remove constant aliases or variables.</span></span>
<span data-ttu-id="076c8-163">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="076c8-163">Implementation varies from provider to provider.</span></span> <span data-ttu-id="076c8-164">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-164">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="076c8-165">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="076c8-165">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="076c8-166">-Include</span><span class="sxs-lookup"><span data-stu-id="076c8-166">-Include</span></span>

<span data-ttu-id="076c8-167">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="076c8-167">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="076c8-168">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="076c8-168">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="076c8-169">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="076c8-169">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="076c8-170">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="076c8-170">Wildcard characters are permitted.</span></span> <span data-ttu-id="076c8-171">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="076c8-171">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="076c8-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="076c8-172">-LiteralPath</span></span>

<span data-ttu-id="076c8-173">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="076c8-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="076c8-174">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="076c8-174">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="076c8-175">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="076c8-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="076c8-176">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="076c8-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="076c8-177">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="076c8-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="076c8-178">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="076c8-179">-Path</span><span class="sxs-lookup"><span data-stu-id="076c8-179">-Path</span></span>

<span data-ttu-id="076c8-180">Spécifie un chemin d’accès aux éléments en cours de suppression.</span><span class="sxs-lookup"><span data-stu-id="076c8-180">Specifies a path of the items being removed.</span></span>
<span data-ttu-id="076c8-181">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="076c8-181">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="076c8-182">-Recurse</span><span class="sxs-lookup"><span data-stu-id="076c8-182">-Recurse</span></span>

<span data-ttu-id="076c8-183">Indique que cette applet de commande supprime les éléments aux emplacements spécifiés et dans tous les éléments enfants des emplacements.</span><span class="sxs-lookup"><span data-stu-id="076c8-183">Indicates that this cmdlet deletes the items in the specified locations and in all child items of the locations.</span></span>

<span data-ttu-id="076c8-184">Lorsqu’il est utilisé avec le paramètre **include** , le paramètre **recurse** peut ne pas supprimer tous les sous-dossiers ou tous les éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="076c8-184">When it is used with the **Include** parameter, the **Recurse** parameter might not delete all subfolders or all child items.</span></span> <span data-ttu-id="076c8-185">Il s'agit d'un problème connu.</span><span class="sxs-lookup"><span data-stu-id="076c8-185">This is a known issue.</span></span> <span data-ttu-id="076c8-186">Pour résoudre ce problème, essayez de suivre les résultats de la `Get-ChildItem -Recurse` commande `Remove-Item` , comme décrit dans l’exemple 4 de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="076c8-186">As a workaround, try piping results of the `Get-ChildItem -Recurse` command to `Remove-Item`, as described in "Example 4" in this topic.</span></span>

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

### <span data-ttu-id="076c8-187">-Stream</span><span class="sxs-lookup"><span data-stu-id="076c8-187">-Stream</span></span>

<span data-ttu-id="076c8-188">Le paramètre **Stream** est un paramètre dynamique que le fournisseur FileSystem ajoute à `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="076c8-188">The **Stream** parameter is a dynamic parameter that the FileSystem provider adds to `Remove-Item`.</span></span>
<span data-ttu-id="076c8-189">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="076c8-189">This parameter works only in file system drives.</span></span>

<span data-ttu-id="076c8-190">Vous pouvez utiliser `Remove-Item` pour supprimer un flux de données de remplacement.</span><span class="sxs-lookup"><span data-stu-id="076c8-190">You can use `Remove-Item` to delete an alternative data stream.</span></span> <span data-ttu-id="076c8-191">Elle ne constitue cependant pas un moyen recommandé pour éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d'Internet.</span><span class="sxs-lookup"><span data-stu-id="076c8-191">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="076c8-192">Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="076c8-192">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="076c8-193">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="076c8-193">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="076c8-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="076c8-194">-Confirm</span></span>

<span data-ttu-id="076c8-195">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="076c8-195">Prompts you for confirmation before running the cmdlet.</span></span> <span data-ttu-id="076c8-196">Pour plus d’informations, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="076c8-196">For more information, see the following articles:</span></span>

- [<span data-ttu-id="076c8-197">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="076c8-197">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [<span data-ttu-id="076c8-198">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="076c8-198">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### <span data-ttu-id="076c8-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="076c8-199">-WhatIf</span></span>

<span data-ttu-id="076c8-200">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="076c8-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="076c8-201">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="076c8-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="076c8-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="076c8-202">CommonParameters</span></span>

<span data-ttu-id="076c8-203">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="076c8-203">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="076c8-204">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="076c8-205">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="076c8-205">INPUTS</span></span>

### <span data-ttu-id="076c8-206">System.String</span><span class="sxs-lookup"><span data-stu-id="076c8-206">System.String</span></span>

<span data-ttu-id="076c8-207">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="076c8-207">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="076c8-208">SORTIES</span><span class="sxs-lookup"><span data-stu-id="076c8-208">OUTPUTS</span></span>

### <span data-ttu-id="076c8-209">Aucun</span><span class="sxs-lookup"><span data-stu-id="076c8-209">None</span></span>

<span data-ttu-id="076c8-210">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="076c8-210">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="076c8-211">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="076c8-211">NOTES</span></span>

<span data-ttu-id="076c8-212">L' `Remove-Item` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="076c8-212">The `Remove-Item` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="076c8-213">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="076c8-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="076c8-214">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="076c8-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="076c8-215">Lorsque vous essayez de supprimer un dossier qui contient des éléments sans utiliser le paramètre **recurse** , l’applet de commande vous invite à confirmer.</span><span class="sxs-lookup"><span data-stu-id="076c8-215">When you try to delete a folder that contains items without using the **Recurse** parameter, the cmdlet prompts for confirmation.</span></span> <span data-ttu-id="076c8-216">L’utilisation `-Confirm:$false` de ne supprime pas l’invite.</span><span class="sxs-lookup"><span data-stu-id="076c8-216">Using `-Confirm:$false` does not suppress the prompt.</span></span> <span data-ttu-id="076c8-217">C'est la procédure normale.</span><span class="sxs-lookup"><span data-stu-id="076c8-217">This is by design.</span></span>

## <span data-ttu-id="076c8-218">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="076c8-218">RELATED LINKS</span></span>

[<span data-ttu-id="076c8-219">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-219">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="076c8-220">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-220">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="076c8-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-221">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="076c8-222">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-222">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="076c8-223">Move-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-223">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="076c8-224">New-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-224">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="076c8-225">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="076c8-225">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="076c8-226">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-226">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="076c8-227">Set-Item</span><span class="sxs-lookup"><span data-stu-id="076c8-227">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="076c8-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="076c8-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="076c8-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="076c8-229">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[<span data-ttu-id="076c8-230">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="076c8-230">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)


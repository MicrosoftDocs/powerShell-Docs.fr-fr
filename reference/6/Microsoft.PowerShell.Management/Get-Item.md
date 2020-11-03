---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 8483fd374ee973256633e3711322561fc14b8ae2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204454"
---
# <span data-ttu-id="3fa45-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-103">Get-Item</span></span>

## <span data-ttu-id="3fa45-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3fa45-104">SYNOPSIS</span></span>
<span data-ttu-id="3fa45-105">Obtient l'élément à l'emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3fa45-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="3fa45-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3fa45-106">SYNTAX</span></span>

### <span data-ttu-id="3fa45-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3fa45-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3fa45-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3fa45-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3fa45-109">Description</span><span class="sxs-lookup"><span data-stu-id="3fa45-109">DESCRIPTION</span></span>

<span data-ttu-id="3fa45-110">L' `Get-Item` applet de commande obtient l’élément à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3fa45-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="3fa45-111">Elle n’obtient pas le contenu de l’élément à l’emplacement, sauf si vous utilisez un caractère générique ( `*` ) pour demander tout le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3fa45-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="3fa45-112">Cette applet de commande est utilisée par les fournisseurs PowerShell pour parcourir différents types de magasins de données.</span><span class="sxs-lookup"><span data-stu-id="3fa45-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="3fa45-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3fa45-113">EXAMPLES</span></span>

### <span data-ttu-id="3fa45-114">Exemple 1 : récupérer le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="3fa45-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="3fa45-115">Cet exemple obtient le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3fa45-115">This example gets the current directory.</span></span> <span data-ttu-id="3fa45-116">Le point ('. ') représente l’élément à l’emplacement actuel (et non son contenu).</span><span class="sxs-lookup"><span data-stu-id="3fa45-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="3fa45-117">Exemple 2 : récupération de tous les éléments dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="3fa45-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="3fa45-118">Cet exemple obtient tous les éléments du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3fa45-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="3fa45-119">Le caractère générique ( `*` ) représente tout le contenu de l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="3fa45-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="3fa45-120">Exemple 3 : obtenir le répertoire actif d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="3fa45-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="3fa45-121">Cet exemple obtient le répertoire actif du `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="3fa45-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="3fa45-122">L’objet récupéré représente uniquement le répertoire, pas son contenu.</span><span class="sxs-lookup"><span data-stu-id="3fa45-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="3fa45-123">Exemple 4 : récupérer des éléments dans le lecteur spécifié</span><span class="sxs-lookup"><span data-stu-id="3fa45-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="3fa45-124">Cet exemple obtient les éléments du `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="3fa45-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="3fa45-125">Le caractère générique ( `*` ) représente tous les éléments dans le conteneur, et pas seulement le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3fa45-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="3fa45-126">Dans PowerShell, utilisez un seul astérisque ( `*` ) pour obtenir le contenu, plutôt que le traditionnel `*.*` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="3fa45-127">Le format est interprété littéralement. par conséquent, n' `*.*` extrayez pas les répertoires ou les noms de fichiers sans point.</span><span class="sxs-lookup"><span data-stu-id="3fa45-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="3fa45-128">Exemple 5 : obtenir une propriété dans le répertoire spécifié</span><span class="sxs-lookup"><span data-stu-id="3fa45-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="3fa45-129">Cet exemple obtient la propriété **LastAccessTime** du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="3fa45-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="3fa45-130">**LastAccessTime** n’est qu’une des propriétés des répertoires du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3fa45-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="3fa45-131">Pour afficher toutes les propriétés d’un répertoire, tapez `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="3fa45-132">Exemple 6 : afficher le contenu d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="3fa45-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="3fa45-133">Cet exemple montre le contenu de la clé de Registre **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="3fa45-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="3fa45-134">Vous pouvez utiliser cette applet de commande avec le fournisseur de Registre PowerShell pour récupérer les clés et les sous-clés de Registre, mais vous devez utiliser l' `Get-ItemProperty` applet de commande pour récupérer les valeurs et les données du Registre.</span><span class="sxs-lookup"><span data-stu-id="3fa45-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="3fa45-135">Exemple 7 : obtenir des éléments dans un répertoire qui ont une exclusion</span><span class="sxs-lookup"><span data-stu-id="3fa45-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="3fa45-136">Cet exemple obtient les éléments du répertoire Windows dont les noms incluent un point ( `.` ), mais ne commencent pas par `w*` . Cet exemple fonctionne uniquement lorsque le chemin d’accès contient un caractère générique ( `*` ) pour spécifier le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3fa45-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="3fa45-137">Exemple 8 : obtention d’informations hardlink</span><span class="sxs-lookup"><span data-stu-id="3fa45-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="3fa45-138">Dans PowerShell 6,2, une autre vue a été ajoutée pour obtenir les informations de liaison permanente.</span><span class="sxs-lookup"><span data-stu-id="3fa45-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="3fa45-139">Pour récupérer les informations hardlink, dirigez la sortie vers `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="3fa45-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

## <span data-ttu-id="3fa45-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3fa45-140">PARAMETERS</span></span>

### <span data-ttu-id="3fa45-141">-Stream</span><span class="sxs-lookup"><span data-stu-id="3fa45-141">-Stream</span></span>

<span data-ttu-id="3fa45-142">Obtient le flux de fichiers NTFS alternatif spécifié du fichier.</span><span class="sxs-lookup"><span data-stu-id="3fa45-142">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="3fa45-143">Entrez le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="3fa45-143">Enter the stream name.</span></span> <span data-ttu-id="3fa45-144">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3fa45-144">Wildcards are supported.</span></span> <span data-ttu-id="3fa45-145">Pour récupérer tous les flux, utilisez un astérisque ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="3fa45-145">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="3fa45-146">Ce paramètre n’est pas valide sur les dossiers.</span><span class="sxs-lookup"><span data-stu-id="3fa45-146">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="3fa45-147">**Stream** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l' `Get-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3fa45-147">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="3fa45-148">Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3fa45-148">This parameter works only in file system drives.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3fa45-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="3fa45-149">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3fa45-150">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fa45-150">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="3fa45-151">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="3fa45-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="3fa45-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="3fa45-152">-Exclude</span></span>

<span data-ttu-id="3fa45-153">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="3fa45-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="3fa45-154">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="3fa45-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3fa45-155">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="3fa45-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3fa45-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="3fa45-157">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="3fa45-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="3fa45-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="3fa45-158">-Filter</span></span>

<span data-ttu-id="3fa45-159">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="3fa45-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="3fa45-160">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge les filtres.</span><span class="sxs-lookup"><span data-stu-id="3fa45-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="3fa45-161">Les filtres sont plus efficaces que les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="3fa45-161">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="3fa45-162">Le fournisseur applique le filtre lorsque l’applet de commande obtient les objets au lieu d’avoir PowerShell de filtrer les objets une fois qu’ils sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="3fa45-162">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="3fa45-163">La chaîne de filtrage est transmise à l’API .NET pour énumérer les fichiers.</span><span class="sxs-lookup"><span data-stu-id="3fa45-163">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="3fa45-164">L’API prend en charge uniquement les `*` `?` caractères génériques et.</span><span class="sxs-lookup"><span data-stu-id="3fa45-164">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="3fa45-165">-Force</span><span class="sxs-lookup"><span data-stu-id="3fa45-165">-Force</span></span>

<span data-ttu-id="3fa45-166">Indique que cette applet de commande obtient des éléments qui ne sont pas accessibles autrement, tels que des éléments masqués.</span><span class="sxs-lookup"><span data-stu-id="3fa45-166">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="3fa45-167">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="3fa45-167">Implementation varies from provider to provider.</span></span> <span data-ttu-id="3fa45-168">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3fa45-168">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="3fa45-169">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="3fa45-169">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="3fa45-170">-Include</span><span class="sxs-lookup"><span data-stu-id="3fa45-170">-Include</span></span>

<span data-ttu-id="3fa45-171">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="3fa45-171">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="3fa45-172">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="3fa45-172">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3fa45-173">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-173">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="3fa45-174">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3fa45-174">Wildcard characters are permitted.</span></span> <span data-ttu-id="3fa45-175">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="3fa45-175">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="3fa45-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3fa45-176">-LiteralPath</span></span>

<span data-ttu-id="3fa45-177">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="3fa45-177">Specifies a path to one or more locations.</span></span> <span data-ttu-id="3fa45-178">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="3fa45-178">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="3fa45-179">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="3fa45-179">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="3fa45-180">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="3fa45-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3fa45-181">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="3fa45-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="3fa45-182">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="3fa45-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="3fa45-183">-Path</span><span class="sxs-lookup"><span data-stu-id="3fa45-183">-Path</span></span>

<span data-ttu-id="3fa45-184">Spécifie le chemin d’accès à un élément.</span><span class="sxs-lookup"><span data-stu-id="3fa45-184">Specifies the path to an item.</span></span> <span data-ttu-id="3fa45-185">Cette applet de commande obtient l’élément à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3fa45-185">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="3fa45-186">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3fa45-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="3fa45-187">Ce paramètre est obligatoire, mais le **chemin d’accès** au nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="3fa45-187">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="3fa45-188">Utilisez un point ( `.` ) pour spécifier l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="3fa45-188">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="3fa45-189">Utilisez le caractère générique ( `*` ) pour spécifier tous les éléments à l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="3fa45-189">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="3fa45-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3fa45-190">CommonParameters</span></span>

<span data-ttu-id="3fa45-191">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-191">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="3fa45-192">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3fa45-192">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3fa45-193">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3fa45-193">INPUTS</span></span>

### <span data-ttu-id="3fa45-194">System.String</span><span class="sxs-lookup"><span data-stu-id="3fa45-194">System.String</span></span>

<span data-ttu-id="3fa45-195">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3fa45-195">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="3fa45-196">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3fa45-196">OUTPUTS</span></span>

### <span data-ttu-id="3fa45-197">System.Object</span><span class="sxs-lookup"><span data-stu-id="3fa45-197">System.Object</span></span>

<span data-ttu-id="3fa45-198">Cette applet de commande retourne les objets qu’elle obtient.</span><span class="sxs-lookup"><span data-stu-id="3fa45-198">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="3fa45-199">Le type est déterminé par le type d’objets dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3fa45-199">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="3fa45-200">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3fa45-200">NOTES</span></span>

<span data-ttu-id="3fa45-201">Cette applet de commande n’a pas de paramètre **recurse** , car elle obtient uniquement un élément, et non son contenu.</span><span class="sxs-lookup"><span data-stu-id="3fa45-201">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="3fa45-202">Pour récupérer le contenu d’un élément de manière récursive, utilisez `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-202">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="3fa45-203">Pour parcourir le registre, utilisez cette applet de commande pour récupérer les clés de Registre et le `Get-ItemProperty` pour accéder aux données et valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="3fa45-203">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="3fa45-204">Les valeurs de Registre sont considérées comme des propriétés des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="3fa45-204">The registry values are considered to be properties of the registry key.</span></span>
  
<span data-ttu-id="3fa45-205">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3fa45-205">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="3fa45-206">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="3fa45-206">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="3fa45-207">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3fa45-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="3fa45-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3fa45-208">RELATED LINKS</span></span>

[<span data-ttu-id="3fa45-209">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="3fa45-210">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="3fa45-211">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-211">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="3fa45-212">Move-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-212">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="3fa45-213">New-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="3fa45-214">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="3fa45-215">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="3fa45-216">Set-Item</span><span class="sxs-lookup"><span data-stu-id="3fa45-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="3fa45-217">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="3fa45-217">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="3fa45-218">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3fa45-218">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="3fa45-219">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="3fa45-219">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="3fa45-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="3fa45-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

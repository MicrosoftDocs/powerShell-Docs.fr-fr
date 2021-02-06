---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "99598993"
---
# <span data-ttu-id="4505f-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-102">Get-Item</span></span>

## <span data-ttu-id="4505f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4505f-103">SYNOPSIS</span></span>
<span data-ttu-id="4505f-104">Obtient l'élément à l'emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="4505f-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="4505f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4505f-105">SYNTAX</span></span>

### <span data-ttu-id="4505f-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4505f-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4505f-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4505f-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4505f-108">Description</span><span class="sxs-lookup"><span data-stu-id="4505f-108">DESCRIPTION</span></span>

<span data-ttu-id="4505f-109">L' `Get-Item` applet de commande obtient l’élément à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="4505f-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="4505f-110">Elle n’obtient pas le contenu de l’élément à l’emplacement, sauf si vous utilisez un caractère générique ( `*` ) pour demander tout le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="4505f-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="4505f-111">Cette applet de commande est utilisée par les fournisseurs PowerShell pour parcourir différents types de magasins de données.</span><span class="sxs-lookup"><span data-stu-id="4505f-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="4505f-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4505f-112">EXAMPLES</span></span>

### <span data-ttu-id="4505f-113">Exemple 1 : récupérer le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="4505f-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="4505f-114">Cet exemple obtient le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4505f-114">This example gets the current directory.</span></span> <span data-ttu-id="4505f-115">Le point ('. ') représente l’élément à l’emplacement actuel (et non son contenu).</span><span class="sxs-lookup"><span data-stu-id="4505f-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="4505f-116">Exemple 2 : récupération de tous les éléments dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="4505f-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="4505f-117">Cet exemple obtient tous les éléments du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4505f-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="4505f-118">Le caractère générique ( `*` ) représente tout le contenu de l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="4505f-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="4505f-119">Exemple 3 : obtenir le répertoire actif d’un lecteur</span><span class="sxs-lookup"><span data-stu-id="4505f-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="4505f-120">Cet exemple obtient le répertoire actif du `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="4505f-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="4505f-121">L’objet récupéré représente uniquement le répertoire, pas son contenu.</span><span class="sxs-lookup"><span data-stu-id="4505f-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="4505f-122">Exemple 4 : récupérer des éléments dans le lecteur spécifié</span><span class="sxs-lookup"><span data-stu-id="4505f-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="4505f-123">Cet exemple obtient les éléments du `C:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="4505f-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="4505f-124">Le caractère générique ( `*` ) représente tous les éléments dans le conteneur, et pas seulement le conteneur.</span><span class="sxs-lookup"><span data-stu-id="4505f-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="4505f-125">Dans PowerShell, utilisez un seul astérisque ( `*` ) pour obtenir le contenu, plutôt que le traditionnel `*.*` .</span><span class="sxs-lookup"><span data-stu-id="4505f-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="4505f-126">Le format est interprété littéralement. par conséquent, n' `*.*` extrayez pas les répertoires ou les noms de fichiers sans point.</span><span class="sxs-lookup"><span data-stu-id="4505f-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="4505f-127">Exemple 5 : obtenir une propriété dans le répertoire spécifié</span><span class="sxs-lookup"><span data-stu-id="4505f-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="4505f-128">Cet exemple obtient la propriété **LastAccessTime** du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4505f-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="4505f-129">**LastAccessTime** n’est qu’une des propriétés des répertoires du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4505f-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="4505f-130">Pour afficher toutes les propriétés d’un répertoire, tapez `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="4505f-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="4505f-131">Exemple 6 : afficher le contenu d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="4505f-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="4505f-132">Cet exemple montre le contenu de la clé de Registre **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="4505f-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="4505f-133">Vous pouvez utiliser cette applet de commande avec le fournisseur de Registre PowerShell pour récupérer les clés et les sous-clés de Registre, mais vous devez utiliser l' `Get-ItemProperty` applet de commande pour récupérer les valeurs et les données du Registre.</span><span class="sxs-lookup"><span data-stu-id="4505f-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="4505f-134">Exemple 7 : obtenir des éléments dans un répertoire qui ont une exclusion</span><span class="sxs-lookup"><span data-stu-id="4505f-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="4505f-135">Cet exemple obtient les éléments du répertoire Windows dont les noms incluent un point ( `.` ), mais ne commencent pas par `w*` . Cet exemple fonctionne uniquement lorsque le chemin d’accès contient un caractère générique ( `*` ) pour spécifier le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="4505f-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="4505f-136">Exemple 8 : obtention d’informations hardlink</span><span class="sxs-lookup"><span data-stu-id="4505f-136">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="4505f-137">Dans PowerShell 6,2, une autre vue a été ajoutée pour obtenir les informations de liaison permanente.</span><span class="sxs-lookup"><span data-stu-id="4505f-137">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="4505f-138">Pour récupérer les informations hardlink, dirigez la sortie vers `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="4505f-138">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="4505f-139">Exemple 9 : sortie pour les systèmes d’exploitation autres que Windows</span><span class="sxs-lookup"><span data-stu-id="4505f-139">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="4505f-140">Dans PowerShell 7,1 sur les systèmes UNIX, l’applet de commande `Get-Item` fournit une sortie de type UNIX :</span><span class="sxs-lookup"><span data-stu-id="4505f-140">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="4505f-141">Les nouvelles propriétés qui font désormais partie de la sortie sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4505f-141">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="4505f-142">**UnixMode** est l’autorisation de fichier représentée sur un système UNIX</span><span class="sxs-lookup"><span data-stu-id="4505f-142">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="4505f-143">L' **utilisateur** est le propriétaire du fichier</span><span class="sxs-lookup"><span data-stu-id="4505f-143">**User** is the file owner</span></span>
- <span data-ttu-id="4505f-144">Le **groupe** est le propriétaire du groupe</span><span class="sxs-lookup"><span data-stu-id="4505f-144">**Group** is the group owner</span></span>
- <span data-ttu-id="4505f-145">**Taille** correspond à la taille du fichier ou du répertoire tel qu’il est représenté sur un système UNIX.</span><span class="sxs-lookup"><span data-stu-id="4505f-145">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="4505f-146">Cette fonctionnalité a été déplacée de expérimental vers standard dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="4505f-146">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="4505f-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4505f-147">PARAMETERS</span></span>

### <span data-ttu-id="4505f-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="4505f-148">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="4505f-149">Ce paramètre est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="4505f-149">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="4505f-150">Obtient le flux de données alternatif spécifié à partir du fichier.</span><span class="sxs-lookup"><span data-stu-id="4505f-150">Gets the specified alternative data stream from the file.</span></span> <span data-ttu-id="4505f-151">Entrez le nom du flux.</span><span class="sxs-lookup"><span data-stu-id="4505f-151">Enter the stream name.</span></span> <span data-ttu-id="4505f-152">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4505f-152">Wildcards are supported.</span></span> <span data-ttu-id="4505f-153">Pour récupérer tous les flux, utilisez un astérisque ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="4505f-153">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="4505f-154">Ce paramètre est valide sur les répertoires, mais notez que les répertoires n’ont pas de flux de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="4505f-154">This parameter is valid on directories, but note that directories do not have data streams by default.</span></span>

<span data-ttu-id="4505f-155">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4505f-155">This parameter was introduced in PowerShell 3.0.</span></span>  <span data-ttu-id="4505f-156">À compter de PowerShell 7,2, `Get-Item` peut recevoir des flux de données alternatifs de répertoires et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="4505f-156">As of PowerShell 7.2, `Get-Item` can get alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="4505f-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="4505f-157">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="4505f-158">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4505f-158">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="4505f-159">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="4505f-159">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="4505f-160">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4505f-160">-Exclude</span></span>

<span data-ttu-id="4505f-161">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="4505f-161">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="4505f-162">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="4505f-162">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4505f-163">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4505f-163">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4505f-164">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4505f-164">Wildcard characters are permitted.</span></span> <span data-ttu-id="4505f-165">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4505f-165">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4505f-166">-Filter</span><span class="sxs-lookup"><span data-stu-id="4505f-166">-Filter</span></span>

<span data-ttu-id="4505f-167">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="4505f-167">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="4505f-168">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge les filtres.</span><span class="sxs-lookup"><span data-stu-id="4505f-168">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="4505f-169">Les filtres sont plus efficaces que les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="4505f-169">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="4505f-170">Le fournisseur applique le filtre lorsque l’applet de commande obtient les objets au lieu d’avoir PowerShell de filtrer les objets une fois qu’ils sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="4505f-170">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="4505f-171">La chaîne de filtrage est transmise à l’API .NET pour énumérer les fichiers.</span><span class="sxs-lookup"><span data-stu-id="4505f-171">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="4505f-172">L’API prend en charge uniquement les `*` `?` caractères génériques et.</span><span class="sxs-lookup"><span data-stu-id="4505f-172">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="4505f-173">-Force</span><span class="sxs-lookup"><span data-stu-id="4505f-173">-Force</span></span>

<span data-ttu-id="4505f-174">Indique que cette applet de commande obtient des éléments qui ne sont pas accessibles autrement, tels que des éléments masqués.</span><span class="sxs-lookup"><span data-stu-id="4505f-174">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="4505f-175">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="4505f-175">Implementation varies from provider to provider.</span></span> <span data-ttu-id="4505f-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4505f-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="4505f-177">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4505f-177">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="4505f-178">-Include</span><span class="sxs-lookup"><span data-stu-id="4505f-178">-Include</span></span>

<span data-ttu-id="4505f-179">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="4505f-179">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="4505f-180">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="4505f-180">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4505f-181">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4505f-181">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4505f-182">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4505f-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="4505f-183">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4505f-183">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4505f-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4505f-184">-LiteralPath</span></span>

<span data-ttu-id="4505f-185">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="4505f-185">Specifies a path to one or more locations.</span></span> <span data-ttu-id="4505f-186">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="4505f-186">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="4505f-187">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="4505f-187">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4505f-188">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4505f-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4505f-189">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4505f-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="4505f-190">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="4505f-190">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="4505f-191">-Path</span><span class="sxs-lookup"><span data-stu-id="4505f-191">-Path</span></span>

<span data-ttu-id="4505f-192">Spécifie le chemin d’accès à un élément.</span><span class="sxs-lookup"><span data-stu-id="4505f-192">Specifies the path to an item.</span></span> <span data-ttu-id="4505f-193">Cette applet de commande obtient l’élément à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="4505f-193">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="4505f-194">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4505f-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="4505f-195">Ce paramètre est obligatoire, mais le **chemin d’accès** au nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4505f-195">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="4505f-196">Utilisez un point ( `.` ) pour spécifier l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="4505f-196">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="4505f-197">Utilisez le caractère générique ( `*` ) pour spécifier tous les éléments à l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="4505f-197">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="4505f-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4505f-198">CommonParameters</span></span>

<span data-ttu-id="4505f-199">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4505f-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4505f-200">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4505f-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4505f-201">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4505f-201">INPUTS</span></span>

### <span data-ttu-id="4505f-202">System.String</span><span class="sxs-lookup"><span data-stu-id="4505f-202">System.String</span></span>

<span data-ttu-id="4505f-203">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4505f-203">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="4505f-204">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4505f-204">OUTPUTS</span></span>

### <span data-ttu-id="4505f-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="4505f-205">System.Object</span></span>

<span data-ttu-id="4505f-206">Cette applet de commande retourne les objets qu’elle obtient.</span><span class="sxs-lookup"><span data-stu-id="4505f-206">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="4505f-207">Le type est déterminé par le type d’objets dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4505f-207">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="4505f-208">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4505f-208">NOTES</span></span>

<span data-ttu-id="4505f-209">Cette applet de commande n’a pas de paramètre **recurse** , car elle obtient uniquement un élément, et non son contenu.</span><span class="sxs-lookup"><span data-stu-id="4505f-209">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="4505f-210">Pour récupérer le contenu d’un élément de manière récursive, utilisez `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4505f-210">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="4505f-211">Pour parcourir le registre, utilisez cette applet de commande pour récupérer les clés de Registre et le `Get-ItemProperty` pour accéder aux données et valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="4505f-211">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="4505f-212">Les valeurs de Registre sont considérées comme des propriétés des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="4505f-212">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="4505f-213">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4505f-213">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4505f-214">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="4505f-214">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="4505f-215">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4505f-215">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="4505f-216">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4505f-216">RELATED LINKS</span></span>

[<span data-ttu-id="4505f-217">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-217">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="4505f-218">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-218">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="4505f-219">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-219">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="4505f-220">Move-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-220">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="4505f-221">New-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-221">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="4505f-222">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-222">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="4505f-223">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-223">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="4505f-224">Set-Item</span><span class="sxs-lookup"><span data-stu-id="4505f-224">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="4505f-225">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4505f-225">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="4505f-226">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4505f-226">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="4505f-227">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="4505f-227">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="4505f-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4505f-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)


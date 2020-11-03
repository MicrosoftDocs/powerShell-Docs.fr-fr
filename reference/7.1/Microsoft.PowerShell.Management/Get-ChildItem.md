---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: c29a938fc73b8b69ea1bbf96f12f5d42d16f79bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205117"
---
# <span data-ttu-id="46762-103">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="46762-103">Get-ChildItem</span></span>

## <span data-ttu-id="46762-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="46762-104">SYNOPSIS</span></span>

<span data-ttu-id="46762-105">Obtient les éléments et les éléments enfants dans un ou plusieurs emplacements spécifiés</span><span class="sxs-lookup"><span data-stu-id="46762-105">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="46762-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46762-106">SYNTAX</span></span>

### <span data-ttu-id="46762-107">Items (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="46762-107">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="46762-108">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="46762-108">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="46762-109">Description</span><span class="sxs-lookup"><span data-stu-id="46762-109">DESCRIPTION</span></span>

<span data-ttu-id="46762-110">L' `Get-ChildItem` applet de commande obtient les éléments dans un ou plusieurs emplacements spécifiés.</span><span class="sxs-lookup"><span data-stu-id="46762-110">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="46762-111">Si l’élément est un conteneur, elle obtient les éléments qui se trouvent à l’intérieur du conteneur, appelés éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="46762-111">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="46762-112">Vous pouvez utiliser le paramètre **recurse** pour récupérer des éléments dans tous les conteneurs enfants et utiliser le paramètre **Depth** pour limiter le nombre de niveaux à recurse.</span><span class="sxs-lookup"><span data-stu-id="46762-112">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="46762-113">`Get-ChildItem` n’affiche pas les répertoires vides.</span><span class="sxs-lookup"><span data-stu-id="46762-113">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="46762-114">Lorsqu’une `Get-ChildItem` commande inclut les paramètres **Depth** ou **recurse** , les répertoires vides ne sont pas inclus dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="46762-114">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="46762-115">Les emplacements sont exposés aux `Get-ChildItem` fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46762-115">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="46762-116">Un emplacement peut être un répertoire du système de fichiers, une ruche du registre ou un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="46762-116">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="46762-117">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="46762-117">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="46762-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="46762-118">EXAMPLES</span></span>

### <span data-ttu-id="46762-119">Exemple 1 : obtenir des éléments enfants à partir d’un répertoire de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="46762-119">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="46762-120">Cet exemple obtient les éléments enfants d’un répertoire de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="46762-120">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="46762-121">Les noms de fichiers et de sous-répertoires sont affichés.</span><span class="sxs-lookup"><span data-stu-id="46762-121">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="46762-122">Pour les emplacements vides, la commande ne retourne aucune sortie et retourne à l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46762-122">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="46762-123">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="46762-123">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="46762-124">`Get-ChildItem` affiche les fichiers et les répertoires dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46762-124">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="46762-125">Par défaut `Get-ChildItem` répertorie le mode ( **attributs** ), **LastWriteTime** , la taille de fichier ( **longueur** ) et le **nom** de l’élément.</span><span class="sxs-lookup"><span data-stu-id="46762-125">By default `Get-ChildItem` lists the mode ( **Attributes** ), **LastWriteTime** , file size ( **Length** ), and the **Name** of the item.</span></span> <span data-ttu-id="46762-126">Les lettres de la propriété **mode** peuvent être interprétées comme suit :</span><span class="sxs-lookup"><span data-stu-id="46762-126">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="46762-127">`l` lien</span><span class="sxs-lookup"><span data-stu-id="46762-127">`l` (link)</span></span>
- <span data-ttu-id="46762-128">`d` Directory</span><span class="sxs-lookup"><span data-stu-id="46762-128">`d` (directory)</span></span>
- <span data-ttu-id="46762-129">`a` archiver</span><span class="sxs-lookup"><span data-stu-id="46762-129">`a` (archive)</span></span>
- <span data-ttu-id="46762-130">`r` (lecture seule)</span><span class="sxs-lookup"><span data-stu-id="46762-130">`r` (read-only)</span></span>
- <span data-ttu-id="46762-131">`h` masquer</span><span class="sxs-lookup"><span data-stu-id="46762-131">`h` (hidden)</span></span>
- <span data-ttu-id="46762-132">`s` (système).</span><span class="sxs-lookup"><span data-stu-id="46762-132">`s` (system).</span></span>

<span data-ttu-id="46762-133">Pour plus d’informations sur les indicateurs de mode, consultez [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span><span class="sxs-lookup"><span data-stu-id="46762-133">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="46762-134">Exemple 2 : obtenir les noms des éléments enfants dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="46762-134">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="46762-135">Cet exemple répertorie uniquement les noms des éléments d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="46762-135">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="46762-136">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="46762-136">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="46762-137">Le paramètre **Name** retourne uniquement les noms de fichiers ou de répertoires à partir du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="46762-137">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="46762-138">Exemple 3 : récupérer des éléments enfants dans le répertoire et les sous-répertoires actifs</span><span class="sxs-lookup"><span data-stu-id="46762-138">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="46762-139">Cet exemple affiche les fichiers **. txt** qui se trouvent dans le répertoire actif et ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-139">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="46762-140">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier `C:\Test\*.txt` .</span><span class="sxs-lookup"><span data-stu-id="46762-140">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="46762-141">**Path** utilise le `*` caractère générique astérisque () pour spécifier tous les fichiers avec l’extension de nom de fichier `.txt` .</span><span class="sxs-lookup"><span data-stu-id="46762-141">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="46762-142">Le paramètre **recurse** recherche dans le répertoire du **chemin d’accès** ses sous-répertoires, comme indiqué dans les en-têtes **Directory :** .</span><span class="sxs-lookup"><span data-stu-id="46762-142">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="46762-143">Le paramètre **force** affiche les fichiers masqués, tels que, `hiddenfile.txt` qui ont le mode **h** .</span><span class="sxs-lookup"><span data-stu-id="46762-143">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h** .</span></span>

### <span data-ttu-id="46762-144">Exemple 4 : récupérer des éléments enfants à l’aide du paramètre include</span><span class="sxs-lookup"><span data-stu-id="46762-144">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="46762-145">Dans cet exemple, `Get-ChildItem` le paramètre **include** est utilisé pour rechercher des éléments spécifiques dans le répertoire spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="46762-145">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="46762-146">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire **C:\test** .</span><span class="sxs-lookup"><span data-stu-id="46762-146">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** .</span></span> <span data-ttu-id="46762-147">Le paramètre **path** contient un caractère générique d’astérisque ( `*` ) de fin pour spécifier le contenu du répertoire.</span><span class="sxs-lookup"><span data-stu-id="46762-147">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="46762-148">Le paramètre **include** utilise un `*` caractère générique astérisque () pour spécifier tous les fichiers portant l’extension de nom de fichier **. txt** .</span><span class="sxs-lookup"><span data-stu-id="46762-148">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt** .</span></span>

<span data-ttu-id="46762-149">Lorsque le paramètre **include** est utilisé, le paramètre **path** a besoin d’un caractère générique astérisque ( `*` ) de fin pour spécifier le contenu du répertoire.</span><span class="sxs-lookup"><span data-stu-id="46762-149">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="46762-150">Par exemple : `-Path C:\Test\*`.</span><span class="sxs-lookup"><span data-stu-id="46762-150">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="46762-151">Si le paramètre **recurse** est ajouté à la commande, l’astérisque ( `*` ) de fin dans le paramètre **path** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="46762-151">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="46762-152">Le paramètre **recurse** obtient les éléments du répertoire du **chemin d’accès** et de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-152">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="46762-153">Par exemple : `-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="46762-153">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="46762-154">Si un astérisque () de fin `*` n’est pas inclus dans le paramètre **path** , la commande ne retourne aucune sortie et retourne à l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46762-154">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="46762-155">Par exemple : `-Path C:\Test\`.</span><span class="sxs-lookup"><span data-stu-id="46762-155">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="46762-156">Exemple 5 : récupérer des éléments enfants à l’aide du paramètre Exclude</span><span class="sxs-lookup"><span data-stu-id="46762-156">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="46762-157">La sortie de l’exemple affiche le contenu du répertoire **C:\Test\Logs** .</span><span class="sxs-lookup"><span data-stu-id="46762-157">The example's output shows the contents of the directory **C:\Test\Logs** .</span></span> <span data-ttu-id="46762-158">La sortie est une référence pour les autres commandes qui utilisent les paramètres **Exclude** et **recurse** .</span><span class="sxs-lookup"><span data-stu-id="46762-158">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="46762-159">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="46762-159">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="46762-160">Le paramètre **Exclude** utilise le `*` caractère générique astérisque () pour spécifier tous les fichiers ou répertoires qui commencent par **un** ou **un** sont exclus de la sortie.</span><span class="sxs-lookup"><span data-stu-id="46762-160">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="46762-161">Lorsque le paramètre **Exclude** est utilisé, un astérisque ( `*` ) de fin dans le paramètre **path** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="46762-161">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="46762-162">Par exemple, `-Path C:\Test\Logs` ou `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="46762-162">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="46762-163">Si un astérisque () de fin `*` n’est pas inclus dans le paramètre **path** , le contenu du paramètre **path** est affiché.</span><span class="sxs-lookup"><span data-stu-id="46762-163">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="46762-164">Les noms de fichiers ou de sous-répertoires qui correspondent à la valeur du paramètre **Exclude** sont des exceptions.</span><span class="sxs-lookup"><span data-stu-id="46762-164">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="46762-165">Si un astérisque () de fin `*` est inclus dans le paramètre **path** , la commande parcourt les sous-répertoires du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="46762-165">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="46762-166">Les noms de fichiers ou de sous-répertoires qui correspondent à la valeur du paramètre **Exclude** sont des exceptions.</span><span class="sxs-lookup"><span data-stu-id="46762-166">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="46762-167">Si le paramètre **recurse** est ajouté à la commande, la sortie de récursivité est la même que le paramètre **path** inclue ou non un astérisque de fin ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="46762-167">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="46762-168">Exemple 6 : obtenir les clés de Registre à partir d’une ruche du Registre</span><span class="sxs-lookup"><span data-stu-id="46762-168">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="46762-169">Cet exemple obtient toutes les clés de Registre à partir de `HKEY_LOCAL_MACHINE\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="46762-169">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="46762-170">`Get-ChildItem` utilise le paramètre **path** pour spécifier la clé de Registre `HKLM:\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="46762-170">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="46762-171">Le chemin d’accès et le niveau supérieur des clés de registre de la ruche s’affichent dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46762-171">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="46762-172">Pour plus d’informations, consultez [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="46762-172">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="46762-173">La première commande affiche le contenu de la `HKLM:\HARDWARE` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="46762-173">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="46762-174">Le paramètre **Exclude** indique `Get-ChildItem` à de ne pas retourner les sous-clés qui commencent par `D*` .</span><span class="sxs-lookup"><span data-stu-id="46762-174">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="46762-175">Actuellement, le paramètre **Exclude** ne fonctionne que sur les sous-clés, et non sur les propriétés Item.</span><span class="sxs-lookup"><span data-stu-id="46762-175">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="46762-176">Exemple 7 : récupération de tous les certificats avec l’autorité de signature de code</span><span class="sxs-lookup"><span data-stu-id="46762-176">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="46762-177">Cet exemple obtient chaque certificat dans le lecteur du certificat PowerShell **:** qui dispose de l’autorité de signature de code.</span><span class="sxs-lookup"><span data-stu-id="46762-177">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="46762-178">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le fournisseur **CERT :** .</span><span class="sxs-lookup"><span data-stu-id="46762-178">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="46762-179">Le paramètre **recurse** recherche le répertoire spécifié par le **chemin d’accès** et ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-179">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="46762-180">Le paramètre **CodeSigningCert** obtient uniquement les certificats qui ont une autorité de signature de code.</span><span class="sxs-lookup"><span data-stu-id="46762-180">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="46762-181">Pour plus d’informations sur le fournisseur de certificats et le lecteur Cert :, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="46762-181">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="46762-182">Exemple 8 : récupérer des éléments à l’aide du paramètre DEPTH</span><span class="sxs-lookup"><span data-stu-id="46762-182">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="46762-183">Cet exemple affiche les éléments d’un répertoire et de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-183">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="46762-184">Le paramètre **Depth** détermine le nombre de niveaux de sous-répertoires à inclure dans la récursivité.</span><span class="sxs-lookup"><span data-stu-id="46762-184">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="46762-185">Les répertoires vides sont exclus de la sortie.</span><span class="sxs-lookup"><span data-stu-id="46762-185">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="46762-186">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier **C:\Parent** .</span><span class="sxs-lookup"><span data-stu-id="46762-186">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent** .</span></span> <span data-ttu-id="46762-187">Le paramètre **Depth** spécifie deux niveaux de récursivité.</span><span class="sxs-lookup"><span data-stu-id="46762-187">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="46762-188">`Get-ChildItem` affiche le contenu du répertoire spécifié par le paramètre **path** et les deux niveaux des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-188">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="46762-189">Exemple 9 : obtention d’informations sur les liens physiques</span><span class="sxs-lookup"><span data-stu-id="46762-189">Example 9: Getting hard link information</span></span>

<span data-ttu-id="46762-190">Dans PowerShell 6,2, une autre vue a été ajoutée pour obtenir des informations sur les liens physiques.</span><span class="sxs-lookup"><span data-stu-id="46762-190">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### <span data-ttu-id="46762-191">Exemple 9 : sortie pour la fonctionnalité expérimentale PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="46762-191">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="46762-192">Dans PowerShell 7 sur les systèmes UNIX, la fonctionnalité expérimentale **PSUnixFileStat** fournit une sortie de type UNIX :</span><span class="sxs-lookup"><span data-stu-id="46762-192">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

<span data-ttu-id="46762-193">Les nouvelles propriétés qui font désormais partie de la sortie sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="46762-193">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="46762-194">**UnixMode** est l’autorisation de fichier représentée sur un système UNIX</span><span class="sxs-lookup"><span data-stu-id="46762-194">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="46762-195">L' **utilisateur** est le propriétaire du fichier</span><span class="sxs-lookup"><span data-stu-id="46762-195">**User** is the file owner</span></span>
- <span data-ttu-id="46762-196">Le **groupe** est le propriétaire du groupe</span><span class="sxs-lookup"><span data-stu-id="46762-196">**Group** is the group owner</span></span>
- <span data-ttu-id="46762-197">**Taille** correspond à la taille du fichier ou du répertoire tel qu’il est représenté sur un système UNIX.</span><span class="sxs-lookup"><span data-stu-id="46762-197">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="46762-198">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46762-198">Parameters</span></span>

### <span data-ttu-id="46762-199">-Attributs</span><span class="sxs-lookup"><span data-stu-id="46762-199">-Attributes</span></span>

<span data-ttu-id="46762-200">Obtient les fichiers et les dossiers avec les attributs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="46762-200">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="46762-201">Ce paramètre prend en charge tous les attributs et vous permet de spécifier des combinaisons complexes d'attributs.</span><span class="sxs-lookup"><span data-stu-id="46762-201">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="46762-202">Par exemple, pour obtenir les fichiers non-système (pas les répertoires) qui sont chiffrés ou compressés, tapez :</span><span class="sxs-lookup"><span data-stu-id="46762-202">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="46762-203">Pour rechercher des fichiers et des dossiers avec des attributs couramment utilisés, utilisez le paramètre **attributes** .</span><span class="sxs-lookup"><span data-stu-id="46762-203">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="46762-204">Ou, le **répertoire** de paramètres, **file** , **Hidden** , **ReadOnly** et **System** .</span><span class="sxs-lookup"><span data-stu-id="46762-204">Or, the parameters **Directory** , **File** , **Hidden** , **ReadOnly** , and **System** .</span></span>

<span data-ttu-id="46762-205">Le paramètre **attributes** prend en charge les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="46762-205">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="46762-206">**Archive**</span><span class="sxs-lookup"><span data-stu-id="46762-206">**Archive**</span></span>
- <span data-ttu-id="46762-207">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="46762-207">**Compressed**</span></span>
- <span data-ttu-id="46762-208">**Appareil**</span><span class="sxs-lookup"><span data-stu-id="46762-208">**Device**</span></span>
- <span data-ttu-id="46762-209">**Directory**</span><span class="sxs-lookup"><span data-stu-id="46762-209">**Directory**</span></span>
- <span data-ttu-id="46762-210">**Chiffré**</span><span class="sxs-lookup"><span data-stu-id="46762-210">**Encrypted**</span></span>
- <span data-ttu-id="46762-211">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="46762-211">**Hidden**</span></span>
- <span data-ttu-id="46762-212">**IntegrityStream**</span><span class="sxs-lookup"><span data-stu-id="46762-212">**IntegrityStream**</span></span>
- <span data-ttu-id="46762-213">**Normal**</span><span class="sxs-lookup"><span data-stu-id="46762-213">**Normal**</span></span>
- <span data-ttu-id="46762-214">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="46762-214">**NoScrubData**</span></span>
- <span data-ttu-id="46762-215">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="46762-215">**NotContentIndexed**</span></span>
- <span data-ttu-id="46762-216">**Hors connexion**</span><span class="sxs-lookup"><span data-stu-id="46762-216">**Offline**</span></span>
- <span data-ttu-id="46762-217">**Lecture seule**</span><span class="sxs-lookup"><span data-stu-id="46762-217">**ReadOnly**</span></span>
- <span data-ttu-id="46762-218">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="46762-218">**ReparsePoint**</span></span>
- <span data-ttu-id="46762-219">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="46762-219">**SparseFile**</span></span>
- <span data-ttu-id="46762-220">**Système**</span><span class="sxs-lookup"><span data-stu-id="46762-220">**System**</span></span>
- <span data-ttu-id="46762-221">**Temporaire**</span><span class="sxs-lookup"><span data-stu-id="46762-221">**Temporary**</span></span>

<span data-ttu-id="46762-222">Pour obtenir une description de ces attributs, consultez l' [énumération FileAttributes](/dotnet/api/system.io.fileattributes).</span><span class="sxs-lookup"><span data-stu-id="46762-222">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="46762-223">Pour combiner des attributs, utilisez les opérateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="46762-223">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="46762-224">`!` PAS</span><span class="sxs-lookup"><span data-stu-id="46762-224">`!` (NOT)</span></span>
- <span data-ttu-id="46762-225">`+` LES</span><span class="sxs-lookup"><span data-stu-id="46762-225">`+` (AND)</span></span>
- <span data-ttu-id="46762-226">`,` NI</span><span class="sxs-lookup"><span data-stu-id="46762-226">`,` (OR)</span></span>

<span data-ttu-id="46762-227">N’utilisez pas d’espaces entre un opérateur et son attribut.</span><span class="sxs-lookup"><span data-stu-id="46762-227">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="46762-228">Les espaces sont acceptés après les virgules.</span><span class="sxs-lookup"><span data-stu-id="46762-228">Spaces are accepted after commas.</span></span>

<span data-ttu-id="46762-229">Pour les attributs courants, utilisez les abréviations suivantes :</span><span class="sxs-lookup"><span data-stu-id="46762-229">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="46762-230">`D` Directory</span><span class="sxs-lookup"><span data-stu-id="46762-230">`D` (Directory)</span></span>
- <span data-ttu-id="46762-231">`H` Masquer</span><span class="sxs-lookup"><span data-stu-id="46762-231">`H` (Hidden)</span></span>
- <span data-ttu-id="46762-232">`R` (Lecture seule)</span><span class="sxs-lookup"><span data-stu-id="46762-232">`R` (Read-only)</span></span>
- <span data-ttu-id="46762-233">`S` Requise</span><span class="sxs-lookup"><span data-stu-id="46762-233">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-234">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="46762-234">-Depth</span></span>

<span data-ttu-id="46762-235">Ce paramètre a été ajouté dans PowerShell 5,0 et vous permet de contrôler la profondeur de récurrence.</span><span class="sxs-lookup"><span data-stu-id="46762-235">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="46762-236">Par défaut, `Get-ChildItem` affiche le contenu du répertoire parent.</span><span class="sxs-lookup"><span data-stu-id="46762-236">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="46762-237">Le paramètre **Depth** détermine le nombre de niveaux de sous-répertoires qui sont inclus dans la récursivité et affiche le contenu.</span><span class="sxs-lookup"><span data-stu-id="46762-237">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="46762-238">Par exemple, `Depth 2` comprend le répertoire du paramètre **path** , le premier niveau de sous-répertoires et le second niveau de sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="46762-238">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="46762-239">Par défaut, les noms de répertoires et les noms de fichiers sont inclus dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="46762-239">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="46762-240">Sur un ordinateur Windows à partir de PowerShell ou **cmd.exe** , vous pouvez afficher une vue graphique d’une structure de répertoires à l’aide de la commande **Tree.com** .</span><span class="sxs-lookup"><span data-stu-id="46762-240">On a Windows computer from PowerShell or **cmd.exe** , you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-241">-Répertoire</span><span class="sxs-lookup"><span data-stu-id="46762-241">-Directory</span></span>

<span data-ttu-id="46762-242">Pour obtenir la liste des répertoires, utilisez le paramètre **Directory** ou le paramètre **attributes** avec la propriété **Directory** .</span><span class="sxs-lookup"><span data-stu-id="46762-242">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="46762-243">Vous pouvez utiliser le paramètre **recurse** avec le **répertoire** .</span><span class="sxs-lookup"><span data-stu-id="46762-243">You can use the **Recurse** parameter with **Directory** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-244">-Exclude</span><span class="sxs-lookup"><span data-stu-id="46762-244">-Exclude</span></span>

<span data-ttu-id="46762-245">Spécifie, sous la forme d’un tableau de chaînes, une propriété ou une propriété que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="46762-245">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="46762-246">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="46762-246">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="46762-247">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` ou `A*` .</span><span class="sxs-lookup"><span data-stu-id="46762-247">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="46762-248">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="46762-248">Wildcard characters are accepted.</span></span>

<span data-ttu-id="46762-249">Un astérisque ( `*` ) de fin dans le paramètre **path** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="46762-249">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="46762-250">Par exemple, `-Path C:\Test\Logs` ou `-Path C:\Test\Logs\*`.</span><span class="sxs-lookup"><span data-stu-id="46762-250">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="46762-251">Si un astérisque () de fin `*` est inclus, la commande parcourt les sous-répertoires du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="46762-251">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="46762-252">Sans l’astérisque ( `*` ), le contenu du paramètre **path** est affiché.</span><span class="sxs-lookup"><span data-stu-id="46762-252">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="46762-253">Plus de détails sont inclus dans l’exemple 5 et la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="46762-253">More details are included in Example 5 and the Notes section.</span></span>

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

### <span data-ttu-id="46762-254">-File</span><span class="sxs-lookup"><span data-stu-id="46762-254">-File</span></span>

<span data-ttu-id="46762-255">Pour obtenir la liste des fichiers, utilisez le paramètre **file** .</span><span class="sxs-lookup"><span data-stu-id="46762-255">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="46762-256">Vous pouvez utiliser le paramètre **recurse** avec le **fichier** .</span><span class="sxs-lookup"><span data-stu-id="46762-256">You can use the **Recurse** parameter with **File** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-257">-Filter</span><span class="sxs-lookup"><span data-stu-id="46762-257">-Filter</span></span>

<span data-ttu-id="46762-258">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="46762-258">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="46762-259">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge les filtres.</span><span class="sxs-lookup"><span data-stu-id="46762-259">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="46762-260">Les filtres sont plus efficaces que les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="46762-260">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="46762-261">Le fournisseur applique le filtre lorsque l’applet de commande obtient les objets au lieu d’avoir PowerShell de filtrer les objets une fois qu’ils sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="46762-261">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="46762-262">La chaîne de filtrage est transmise à l’API .NET pour énumérer les fichiers.</span><span class="sxs-lookup"><span data-stu-id="46762-262">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="46762-263">L’API prend en charge uniquement les `*` `?` caractères génériques et.</span><span class="sxs-lookup"><span data-stu-id="46762-263">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="46762-264">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="46762-264">-FollowSymlink</span></span>

<span data-ttu-id="46762-265">Par défaut, l' `Get-ChildItem` applet de commande affiche des liens symboliques vers les répertoires trouvés lors de la récursivité, mais ne les recurset pas.</span><span class="sxs-lookup"><span data-stu-id="46762-265">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="46762-266">Utilisez le paramètre **FollowSymlink** pour rechercher dans les répertoires qui ciblent ces liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="46762-266">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="46762-267">**FollowSymlink** est un paramètre dynamique qui est pris en charge uniquement dans le fournisseur **FileSystem** .</span><span class="sxs-lookup"><span data-stu-id="46762-267">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="46762-268">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="46762-268">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="46762-269">-Force</span><span class="sxs-lookup"><span data-stu-id="46762-269">-Force</span></span>

<span data-ttu-id="46762-270">Permet à l’applet de commande d’extraire des éléments qui ne sont pas accessibles par l’utilisateur, tels que des fichiers cachés ou système.</span><span class="sxs-lookup"><span data-stu-id="46762-270">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="46762-271">Le paramètre **force** ne remplace pas les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="46762-271">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="46762-272">L’implémentation est différente d’un fournisseur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="46762-272">Implementation varies among providers.</span></span> <span data-ttu-id="46762-273">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="46762-273">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="46762-274">-Hidden</span><span class="sxs-lookup"><span data-stu-id="46762-274">-Hidden</span></span>

<span data-ttu-id="46762-275">Pour récupérer uniquement les éléments masqués, utilisez le paramètre **Hidden** ou le paramètre **attributes** avec la propriété **Hidden** .</span><span class="sxs-lookup"><span data-stu-id="46762-275">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="46762-276">Par défaut, `Get-ChildItem` n’affiche pas les éléments masqués.</span><span class="sxs-lookup"><span data-stu-id="46762-276">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="46762-277">Utilisez le paramètre **force** pour récupérer les éléments masqués.</span><span class="sxs-lookup"><span data-stu-id="46762-277">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-278">-Include</span><span class="sxs-lookup"><span data-stu-id="46762-278">-Include</span></span>

<span data-ttu-id="46762-279">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="46762-279">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="46762-280">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="46762-280">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="46762-281">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="46762-281">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="46762-282">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="46762-282">Wildcard characters are permitted.</span></span> <span data-ttu-id="46762-283">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="46762-283">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="46762-284">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="46762-284">-LiteralPath</span></span>

<span data-ttu-id="46762-285">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="46762-285">Specifies a path to one or more locations.</span></span> <span data-ttu-id="46762-286">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="46762-286">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="46762-287">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="46762-287">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="46762-288">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="46762-288">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="46762-289">Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="46762-289">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="46762-290">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="46762-290">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="46762-291">-Name</span><span class="sxs-lookup"><span data-stu-id="46762-291">-Name</span></span>

<span data-ttu-id="46762-292">Obtient uniquement les noms des éléments de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="46762-292">Gets only the names of the items in the location.</span></span> <span data-ttu-id="46762-293">La sortie est un objet String qui peut être envoyé vers d’autres commandes via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="46762-293">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="46762-294">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="46762-294">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="46762-295">-Path</span><span class="sxs-lookup"><span data-stu-id="46762-295">-Path</span></span>

<span data-ttu-id="46762-296">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="46762-296">Specifies a path to one or more locations.</span></span> <span data-ttu-id="46762-297">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="46762-297">Wildcards are accepted.</span></span> <span data-ttu-id="46762-298">L’emplacement par défaut est le répertoire actif ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="46762-298">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="46762-299">-ReadOnly</span><span class="sxs-lookup"><span data-stu-id="46762-299">-ReadOnly</span></span>

<span data-ttu-id="46762-300">Pour obtenir uniquement les éléments en lecture seule, utilisez le paramètre **ReadOnly** ou la propriété **ReadOnly** du paramètre **attributes** .</span><span class="sxs-lookup"><span data-stu-id="46762-300">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-301">-Recurse</span><span class="sxs-lookup"><span data-stu-id="46762-301">-Recurse</span></span>

<span data-ttu-id="46762-302">Obtient les éléments aux emplacements spécifiés, de même que dans tous les éléments enfants de ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="46762-302">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-303">-System</span><span class="sxs-lookup"><span data-stu-id="46762-303">-System</span></span>

<span data-ttu-id="46762-304">Obtient uniquement les fichiers et répertoires système.</span><span class="sxs-lookup"><span data-stu-id="46762-304">Gets only system files and directories.</span></span> <span data-ttu-id="46762-305">Pour récupérer uniquement les fichiers et dossiers système, utilisez la propriété **système** du paramètre **System** ou du paramètre **attributes** .</span><span class="sxs-lookup"><span data-stu-id="46762-305">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46762-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46762-306">CommonParameters</span></span>

<span data-ttu-id="46762-307">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46762-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46762-308">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="46762-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46762-309">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="46762-309">INPUTS</span></span>

### <span data-ttu-id="46762-310">System.String</span><span class="sxs-lookup"><span data-stu-id="46762-310">System.String</span></span>

<span data-ttu-id="46762-311">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="46762-311">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="46762-312">SORTIES</span><span class="sxs-lookup"><span data-stu-id="46762-312">OUTPUTS</span></span>

### <span data-ttu-id="46762-313">System.Object</span><span class="sxs-lookup"><span data-stu-id="46762-313">System.Object</span></span>

<span data-ttu-id="46762-314">Le type d’objet `Get-ChildItem` retourné est déterminé par les objets figurant dans le chemin d’accès du lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="46762-314">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="46762-315">System.String</span><span class="sxs-lookup"><span data-stu-id="46762-315">System.String</span></span>

<span data-ttu-id="46762-316">Si vous utilisez le paramètre **Name** , `Get-ChildItem` retourne les noms d’objets sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="46762-316">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="46762-317">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="46762-317">NOTES</span></span>

- <span data-ttu-id="46762-318">`Get-ChildItem` peut être exécuté à l’aide de l’un des alias intégrés, `ls` , `dir` et `gci` .</span><span class="sxs-lookup"><span data-stu-id="46762-318">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="46762-319">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="46762-319">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="46762-320">`Get-ChildItem` n’obtient pas les éléments masqués par défaut.</span><span class="sxs-lookup"><span data-stu-id="46762-320">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="46762-321">Pour obtenir des éléments cachés, utilisez le paramètre **Force** .</span><span class="sxs-lookup"><span data-stu-id="46762-321">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="46762-322">L' `Get-ChildItem` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="46762-322">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="46762-323">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="46762-323">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="46762-324">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="46762-324">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="46762-325">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="46762-325">RELATED LINKS</span></span>

[<span data-ttu-id="46762-326">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="46762-326">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="46762-327">about_Providers</span><span class="sxs-lookup"><span data-stu-id="46762-327">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="46762-328">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="46762-328">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="46762-329">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="46762-329">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="46762-330">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="46762-330">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="46762-331">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="46762-331">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="46762-332">Get-Item</span><span class="sxs-lookup"><span data-stu-id="46762-332">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="46762-333">Get-Location</span><span class="sxs-lookup"><span data-stu-id="46762-333">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="46762-334">Get-Process</span><span class="sxs-lookup"><span data-stu-id="46762-334">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="46762-335">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="46762-335">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="46762-336">Split-Path</span><span class="sxs-lookup"><span data-stu-id="46762-336">Split-Path</span></span>](Split-Path.md)


---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des fichiers, dossiers et clés de Registre
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293093"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="033ee-103">Utilisation des fichiers, dossiers et clés de Registre</span><span class="sxs-lookup"><span data-stu-id="033ee-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="033ee-104">Windows PowerShell utilise le substantif **Item** pour faire référence aux éléments figurant sur un lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="033ee-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="033ee-105">En relation avec le fournisseur FileSystem de Windows PowerShell, le terme **Item** peut désigner un fichier, un dossier ou le lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="033ee-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="033ee-106">Nous allons examiner en détail comment répertorier et utiliser ces éléments, ces tâches étant essentielles dans la plupart des environnements d'administration.</span><span class="sxs-lookup"><span data-stu-id="033ee-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="033ee-107">Énumération des fichiers, des dossiers et des clés de Registre (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="033ee-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="033ee-108">L’obtention d’une collection d’éléments à partir d’un emplacement particulier étant une tâche très courante, l’applet de commande **Get-ChildItem** est conçue pour retourner tous les éléments figurant dans un conteneur tel qu’un dossier.</span><span class="sxs-lookup"><span data-stu-id="033ee-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="033ee-109">Pour retourner tous les fichiers et dossiers contenus directement dans le dossier C:\\Windows, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="033ee-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="033ee-110">La liste ressemble à celle qui s’affiche quand vous entrez la commande **dir** dans **Cmd.exe**, ou la commande **ls** dans un interpréteur de commandes UNIX.</span><span class="sxs-lookup"><span data-stu-id="033ee-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="033ee-111">Vous pouvez effectuer des recherches très complexes à l’aide des paramètres de l’applet de commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="033ee-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="033ee-112">Nous examinerons quelques scénarios dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="033ee-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="033ee-113">Pour afficher la syntaxe de l’applet de commande **Get-ChildItem**, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="033ee-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="033ee-114">Vous pouvez combiner ces paramètres pour personnaliser davantage les sorties.</span><span class="sxs-lookup"><span data-stu-id="033ee-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="033ee-115">Affichage de la liste de tous les éléments contenus (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="033ee-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="033ee-116">Pour afficher à la fois les éléments d’un dossier Windows et ceux contenus dans ses sous-dossiers, utilisez le paramètre **Recurse** de l’applet de commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="033ee-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="033ee-117">La liste affiche tous les éléments contenus dans le dossier Windows et ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="033ee-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="033ee-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="033ee-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="033ee-119">Filtrage des éléments par nom (-Name)</span><span class="sxs-lookup"><span data-stu-id="033ee-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="033ee-120">Pour afficher uniquement les noms des éléments, utilisez le paramètre **Name** de l’applet de commande **Get-Childitem** :</span><span class="sxs-lookup"><span data-stu-id="033ee-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="033ee-121">Affichage forcé de la liste des éléments cachés (-Force)</span><span class="sxs-lookup"><span data-stu-id="033ee-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="033ee-122">Les éléments normalement invisibles dans l’Explorateur de fichiers ou dans Cmd.exe n’apparaissent pas dans la sortie d’une commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="033ee-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="033ee-123">Pour afficher les éléments masqués, utilisez le paramètre **Force** de l’applet de commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="033ee-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="033ee-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="033ee-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="033ee-125">Ce paramètre est nommé Force, car il permet de remplacer de force le comportement normal de la commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="033ee-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="033ee-126">Force est un paramètre couramment employé qui force une action dont l'exécution n'est généralement pas assurée par une applet de commande. Notez toutefois qu'il n'exécute aucune action susceptible de compromettre la sécurité du système.</span><span class="sxs-lookup"><span data-stu-id="033ee-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="033ee-127">Recherche de noms d'éléments avec des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="033ee-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="033ee-128">La commande **Get-ChildItem** accepte les caractères génériques dans le chemin d’accès des éléments à répertorier.</span><span class="sxs-lookup"><span data-stu-id="033ee-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="033ee-129">La mise en correspondance des caractères génériques étant gérée par le moteur Windows PowerShell, toutes les applets de commande qui acceptent des caractères génériques utilisent la même notation et suivent le même comportement de mise en correspondance.</span><span class="sxs-lookup"><span data-stu-id="033ee-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="033ee-130">Parmi les caractères génériques disponibles dans la notation Windows PowerShell, citons les suivants :</span><span class="sxs-lookup"><span data-stu-id="033ee-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="033ee-131">L’astérisque (\*) correspond à zéro ou plusieurs occurrences d’un caractère quelconque.</span><span class="sxs-lookup"><span data-stu-id="033ee-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="033ee-132">Le point d'interrogation (?) correspond à exactement un caractère.</span><span class="sxs-lookup"><span data-stu-id="033ee-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="033ee-133">Le crochet gauche (\[) et le crochet droit (]) entourent un ensemble de caractères à mettre en correspondance.</span><span class="sxs-lookup"><span data-stu-id="033ee-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="033ee-134">Voici quelques exemples qui illustrent l'utilisation des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="033ee-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="033ee-135">Pour trouver tous les fichiers contenus dans le répertoire Windows avec le suffixe  **.log** et exactement cinq caractères dans le nom de base, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="033ee-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="033ee-136">Pour rechercher tous les fichiers qui commencent par la lettre **x** dans le répertoire Windows, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="033ee-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="033ee-137">Pour rechercher tous les fichiers dont le nom commence par **x** ou **z**, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="033ee-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="033ee-138">Exclusion d'éléments (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="033ee-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="033ee-139">Vous pouvez exclure des éléments spécifiques à l’aide du paramètre **Exclude** de l’applet de commande Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="033ee-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="033ee-140">Vous pouvez ainsi effectuer des opérations de filtrage complexes à l'aide d'une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="033ee-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="033ee-141">Par exemple, supposons que vous essayiez de trouver la DLL Windows Time Service dans le dossier System32. Tout ce dont vous souvenez, c'est que le nom de la DLL commence par la lettre « W » et qu'il contient le nombre « 32 ».</span><span class="sxs-lookup"><span data-stu-id="033ee-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="033ee-142">Une expression telle que **w\&#42;32\&#42;.dll** permet de trouver toutes les DLL qui répondent aux conditions, mais peut également retourner les DLL de compatibilité avec Windows 95 et Windows 16 bits qui comprennent « 95 » ou « 16 » dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="033ee-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="033ee-143">Pour omettre les fichiers contenant l’un de ces nombres dans leur nom, utilisez le paramètre **Exclude** selon le modèle **\&#42;\[9516]\&#42;**  :</span><span class="sxs-lookup"><span data-stu-id="033ee-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="033ee-144">Combinaison de paramètres Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="033ee-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="033ee-145">Vous pouvez utiliser plusieurs paramètres de l’applet de commande **Get-ChildItem** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="033ee-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="033ee-146">Avant de combiner des paramètres, assurez-vous de bien comprendre à quoi correspondent les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="033ee-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="033ee-147">Par exemple, la commande suivante ne retourne aucun résultat :</span><span class="sxs-lookup"><span data-stu-id="033ee-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="033ee-148">Aucun résultat n'est disponible, même s'il existe deux DLL qui commencent par la lettre « z » dans le dossier Windows.</span><span class="sxs-lookup"><span data-stu-id="033ee-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="033ee-149">Aucun résultat n'est retourné, car nous avons spécifié le caractère générique comme faisant partie du chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="033ee-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="033ee-150">Bien que la commande soit récursive, l’applet de commande **Get-ChildItem** limite le résultat aux éléments qui se trouvent dans le dossier Windows et dont le nom se termine par « .dll ».</span><span class="sxs-lookup"><span data-stu-id="033ee-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="033ee-151">Pour spécifier une recherche récursive des fichiers dont le nom correspond à un modèle particulier, utilisez le paramètre **-Include**.</span><span class="sxs-lookup"><span data-stu-id="033ee-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
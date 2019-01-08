---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion de l'emplacement actuel
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: d1ebc9507a45841e6d4d8219e45c002990e1328c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401768"
---
# <a name="managing-current-location"></a><span data-ttu-id="10e08-103">Gestion de l'emplacement actuel</span><span class="sxs-lookup"><span data-stu-id="10e08-103">Managing Current Location</span></span>

<span data-ttu-id="10e08-104">Quand vous parcourez des systèmes de dossiers dans l'Explorateur de fichiers, vous disposez généralement d'un emplacement de travail spécifique, à savoir le dossier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="10e08-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="10e08-105">Pour manipuler les éléments contenus dans le dossier actif, il vous suffit de cliquer dessus.</span><span class="sxs-lookup"><span data-stu-id="10e08-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="10e08-106">Dans les interfaces de ligne de commande telles que Cmd.exe, quand vous vous trouvez dans le même dossier qu'un fichier particulier, vous pouvez accéder à ce fichier en spécifiant un nom relativement court, ce qui vous évite de préciser le chemin d'accès complet au fichier.</span><span class="sxs-lookup"><span data-stu-id="10e08-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="10e08-107">Le répertoire actif est désigné sous le nom de « répertoire de travail ».</span><span class="sxs-lookup"><span data-stu-id="10e08-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="10e08-108">Windows PowerShell utilise le substantif **Location** pour faire référence au répertoire de travail, et implémente une famille d’applets de commande pour vous permettre d’examiner et de manipuler votre emplacement.</span><span class="sxs-lookup"><span data-stu-id="10e08-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="10e08-109">Obtention de votre emplacement actuel (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="10e08-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="10e08-110">Pour déterminer le chemin d’accès à l’emplacement de votre répertoire actif, entrez la commande **Get-Location** :</span><span class="sxs-lookup"><span data-stu-id="10e08-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="10e08-111">L’applet de commande Get-Location est similaire à la commande **pwd** dans l’interpréteur de commandes BASH.</span><span class="sxs-lookup"><span data-stu-id="10e08-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="10e08-112">L’applet de commande Set-Location est similaire à la commande **cd** dans Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="10e08-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="10e08-113">Définition de votre emplacement actuel (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="10e08-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="10e08-114">La commande **Get-Location** s’utilise avec la commande **Set-Location**.</span><span class="sxs-lookup"><span data-stu-id="10e08-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="10e08-115">La commande **Set-Location** permet de spécifier l’emplacement de votre répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="10e08-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="10e08-116">Une fois la commande entrée, notez qu'aucun commentaire concernant l'impact de la commande n'est affiché.</span><span class="sxs-lookup"><span data-stu-id="10e08-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="10e08-117">La plupart des commandes Windows PowerShell qui exécutent une action ne génèrent que peu de commentaires, voire aucun, car la sortie n'est pas toujours utile.</span><span class="sxs-lookup"><span data-stu-id="10e08-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="10e08-118">Pour vérifier qu’un changement de répertoire a bien eu lieu après l’exécution de la commande **Set-Location**, incluez le paramètre **-PassThru** dans la commande **Set-Location** :</span><span class="sxs-lookup"><span data-stu-id="10e08-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="10e08-119">Vous pouvez utiliser le paramètre **-PassThru** avec de nombreuses commandes Set dans Windows PowerShell pour retourner des informations sur le résultat quand aucune sortie n’est générée par défaut.</span><span class="sxs-lookup"><span data-stu-id="10e08-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="10e08-120">Pour spécifier des chemins d'accès par rapport à votre emplacement actuel, procédez de la même façon que dans la plupart des interpréteurs de commandes UNIX et Windows.</span><span class="sxs-lookup"><span data-stu-id="10e08-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="10e08-121">Dans la notation standard des chemins d’accès relatifs, un point (**.**) représente votre dossier actif, tandis qu’un point double (**..**) représente le répertoire parent de votre emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="10e08-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="10e08-122">Par exemple, si vous vous trouvez dans le dossier **C:\\Windows**, un point (**.**) représente **C:\\Windows** et un point double (**..**) représente **C:**.</span><span class="sxs-lookup"><span data-stu-id="10e08-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="10e08-123">Pour passer de votre emplacement actuel à la racine du lecteur C:, tapez :</span><span class="sxs-lookup"><span data-stu-id="10e08-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="10e08-124">Vous pouvez employer la même technique sur les lecteurs Windows PowerShell qui ne sont pas des lecteurs du système de fichiers, comme **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="10e08-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="10e08-125">Pour sélectionner l’emplacement de la clé HKLM\\Software dans le Registre, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10e08-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="10e08-126">Vous pouvez ensuite passer au répertoire parent, c'est-à-dire à la racine du lecteur Windows PowerShell HKLM:, à l'aide d'un chemin d'accès relatif :</span><span class="sxs-lookup"><span data-stu-id="10e08-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="10e08-127">Vous pouvez taper Set-Location ou utiliser l'un des alias Windows PowerShell intégrés pour Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="10e08-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="10e08-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="10e08-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="10e08-129">Enregistrement et rappel des emplacements récents (Push-Location et Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="10e08-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="10e08-130">Quand vous passez d'un emplacement à un autre, il est utile de faire le suivi des emplacements visités et d'être en mesure de retourner à l'emplacement précédent.</span><span class="sxs-lookup"><span data-stu-id="10e08-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="10e08-131">L’applet de commande **Push-Location** dans Windows PowerShell crée un historique chronologique (ou « pile ») des chemins d’accès aux répertoires visités. Pour revenir en arrière dans l’historique des chemins d’accès aux répertoires, utilisez l’applet de commande complémentaire, **Pop-Location**.</span><span class="sxs-lookup"><span data-stu-id="10e08-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="10e08-132">Par exemple, Windows PowerShell démarre généralement dans le répertoire de base de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10e08-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="10e08-133">Le terme de pile (*stack*) a une signification particulière dans de nombreux environnements de programmation, y compris dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10e08-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="10e08-134">Comme dans une pile d'objets, le dernier objet que vous placez en haut de la pile est le premier que vous pouvez ôter de la pile.</span><span class="sxs-lookup"><span data-stu-id="10e08-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="10e08-135">Quand vous ajoutez un élément à une pile, vous le « poussez » sur la pile (« push » en anglais).</span><span class="sxs-lookup"><span data-stu-id="10e08-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="10e08-136">Quand vous ôtez un élément de la pile, celui-ci est « extrait » de la pile (« pop » en anglais).</span><span class="sxs-lookup"><span data-stu-id="10e08-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="10e08-137">Pour ajouter l'emplacement actuel à la pile, puis passer au dossier Local Settings, tapez :</span><span class="sxs-lookup"><span data-stu-id="10e08-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="10e08-138">Ensuite, pour ajouter l'emplacement Local Settings à la pile et passer au dossier Temp, tapez :</span><span class="sxs-lookup"><span data-stu-id="10e08-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="10e08-139">Pour vérifier que le changement de répertoire a bien eu lieu, entrez la commande **Get-Location** :</span><span class="sxs-lookup"><span data-stu-id="10e08-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="10e08-140">Pour revenir au dernier répertoire visité, entrez la commande **Pop-Location**. Ensuite, pour vérifier que le changement a bien eu lieu, entrez la commande **Get-Location** :</span><span class="sxs-lookup"><span data-stu-id="10e08-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="10e08-141">Comme avec l’applet de commande **Set-Location**, lorsque vous entrez l’applet de commande **Pop-Location**, vous pouvez inclure le paramètre **-PassThru** pour afficher le répertoire entré :</span><span class="sxs-lookup"><span data-stu-id="10e08-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="10e08-142">Vous pouvez également utiliser les applets de commande Location avec des chemins d'accès réseau.</span><span class="sxs-lookup"><span data-stu-id="10e08-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="10e08-143">Si vous disposez d'un serveur nommé FS01 avec un partage nommé Public, vous pouvez changer votre emplacement en tapant</span><span class="sxs-lookup"><span data-stu-id="10e08-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="10e08-144">ou</span><span class="sxs-lookup"><span data-stu-id="10e08-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="10e08-145">Vous pouvez utiliser les commandes **Push-Location** et **Set-Location** pour modifier l’emplacement en le définissant sur tout lecteur disponible.</span><span class="sxs-lookup"><span data-stu-id="10e08-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="10e08-146">Par exemple, si vous possédez un lecteur de CD-ROM local associé à la lettre de lecteur D qui contient un CD de données, vous pouvez passer à l’emplacement du lecteur de CD en entrant la commande **Set-Location D:**.</span><span class="sxs-lookup"><span data-stu-id="10e08-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="10e08-147">Si le lecteur est vide, le message d'erreur suivant s'affiche :</span><span class="sxs-lookup"><span data-stu-id="10e08-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="10e08-148">Quand vous utilisez une interface de ligne de commande, il n'est pas pratique de recourir à l'Explorateur de fichiers pour examiner les lecteurs physiques disponibles.</span><span class="sxs-lookup"><span data-stu-id="10e08-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="10e08-149">En outre, l'Explorateur de fichiers n'affiche pas tous les lecteurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10e08-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="10e08-150">Windows PowerShell fournit un ensemble de commandes permettant de manipuler les lecteurs Windows PowerShell. Celles-ci seront traitées dans une autre section.</span><span class="sxs-lookup"><span data-stu-id="10e08-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>

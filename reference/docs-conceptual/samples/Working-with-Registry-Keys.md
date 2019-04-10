---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de clés de Registre
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: e7b497ec2fccf9ba3934439a9c1e9be3cf70a705
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293188"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="ef557-103">Utilisation de clés de Registre</span><span class="sxs-lookup"><span data-stu-id="ef557-103">Working with Registry Keys</span></span>

<span data-ttu-id="ef557-104">Étant donné que les clés de Registre sont des éléments sur des lecteurs Windows PowerShell, leur utilisation est très similaire à l’utilisation de fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="ef557-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="ef557-105">Une différence importante est que chaque élément sur un lecteur Windows PowerShell basé sur un Registre est un conteneur, tout comme un dossier sur un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ef557-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="ef557-106">En revanche, les entrées de Registre et les valeurs qui leur sont associées sont des propriétés des éléments, pas des éléments distincts.</span><span class="sxs-lookup"><span data-stu-id="ef557-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="ef557-107">Affichage de la liste de toutes les sous-clés d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="ef557-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="ef557-108">Vous pouvez afficher tous les éléments figurant directement à l’intérieur d’une clé de Registre à l’aide de l’applet de commande **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="ef557-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="ef557-109">Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**.</span><span class="sxs-lookup"><span data-stu-id="ef557-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="ef557-110">Par exemple, cette commande affiche les éléments figurant directement dans le lecteur Windows PowerShell HKCU:, qui correspond à la ruche du Registre HKEY_CURRENT_USER :</span><span class="sxs-lookup"><span data-stu-id="ef557-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="ef557-111">Il s’agit des clés de niveau supérieur visibles sous HKEY_CURRENT_USER dans l’Éditeur du Registre (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="ef557-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="ef557-112">Vous pouvez également définir ce chemin du Registre en spécifiant le nom du fournisseur de Registre, suivi de «  **::**  ».</span><span class="sxs-lookup"><span data-stu-id="ef557-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="ef557-113">Le nom complet du fournisseur de Registre est **Microsoft.PowerShell.Core\\Registry**, mais il peut être abrégé en **Registry**.</span><span class="sxs-lookup"><span data-stu-id="ef557-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="ef557-114">Toutes les commandes suivantes répertorient le contenu directement sous HKCU :</span><span class="sxs-lookup"><span data-stu-id="ef557-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="ef557-115">Ces commandes répertorient uniquement les éléments contenus directement, de manière très similaire à la commande **DIR** de Cmd.exe ou à la commande **ls** dans un interpréteur de commande UNIX.</span><span class="sxs-lookup"><span data-stu-id="ef557-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="ef557-116">Pour afficher les éléments contenus, vous devez spécifier le paramètre **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="ef557-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="ef557-117">Pour répertorier toutes les clés de Registre dans HKCU, utilisez la commande suivante (cette opération peut prendre beaucoup de temps) :</span><span class="sxs-lookup"><span data-stu-id="ef557-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="ef557-118">L’applet de commande **Get-ChildItem** peut exécuter des fonctionnalités de filtrage complexes via ses paramètres **Path**, **Filter**, **Include** et **Exclude**, mais ces paramètres sont généralement basés uniquement sur le nom.</span><span class="sxs-lookup"><span data-stu-id="ef557-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="ef557-119">Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de l’applet de commande **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="ef557-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="ef557-120">La commande suivante recherche dans HKCU:\\Software toutes les clés qui n’ont pas plus d’une sous-clé et ont aussi exactement quatre valeurs :</span><span class="sxs-lookup"><span data-stu-id="ef557-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="ef557-121">Copie de clés</span><span class="sxs-lookup"><span data-stu-id="ef557-121">Copying Keys</span></span>

<span data-ttu-id="ef557-122">La copie s’effectue à l’aide de l’applet de commande **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="ef557-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="ef557-123">La commande suivante copie HKLM:\\SOFTWARE\\Microsoft\\Window\\\CurrentVersion et toutes ses propriétés dans HKCU:\\, en créant une nouvelle clé nommée « CurrentVersion » :</span><span class="sxs-lookup"><span data-stu-id="ef557-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="ef557-124">Si vous examinez cette nouvelle clé dans l’Éditeur du Registre ou en utilisant l’applet de commande **Get-ChildItem**, vous pouvez remarquer que n’avez pas de copies des sous-clés contenues dans le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="ef557-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="ef557-125">Pour copier tout le contenu d’un conteneur, vous devez spécifier le paramètre **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="ef557-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="ef557-126">Pour rendre la commande de copie précédente récursive, vous devez utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ef557-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="ef557-127">Vous pouvez toujours utiliser d’autres outils déjà disponibles pour effectuer des copies du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ef557-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="ef557-128">Les outils d’édition du Registre (dont reg.exe, regini.exe et regedit.exe) et les objets COM qui prennent en charge l’édition du Registre (par exemple, WScript.Shell et la classe StdRegProv de WM) peuvent être utilisés à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef557-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="ef557-129">Création de clés</span><span class="sxs-lookup"><span data-stu-id="ef557-129">Creating Keys</span></span>

<span data-ttu-id="ef557-130">Créer des clés dans le Registre est plus simple que créer un élément dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ef557-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="ef557-131">Étant donné que toutes les clés de Registre sont des conteneurs, il est inutile spécifier le type d’élément. Vous devez simplement fournir un chemin d’accès explicite, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ef557-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="ef557-132">Pour spécifier une clé, vous pouvez également utiliser un chemin d’accès basé sur un fournisseur :</span><span class="sxs-lookup"><span data-stu-id="ef557-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="ef557-133">Suppression de clés</span><span class="sxs-lookup"><span data-stu-id="ef557-133">Deleting Keys</span></span>

<span data-ttu-id="ef557-134">La suppression d’éléments est essentiellement identique pour tous les fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="ef557-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="ef557-135">Les commandes suivantes suppriment des éléments en mode silencieux :</span><span class="sxs-lookup"><span data-stu-id="ef557-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="ef557-136">Suppression de toutes les clés sous une clé spécifique</span><span class="sxs-lookup"><span data-stu-id="ef557-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="ef557-137">Vous pouvez supprimer des élément contenus à l’aide de l’applet de commande **Remove-Item**, mais vous devez confirmer la suppression si les éléments contiennent autre chose.</span><span class="sxs-lookup"><span data-stu-id="ef557-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ef557-138">Par exemple, si nous tentons de supprimer la sous-clé HKCU:\\CurrentVersion que nous avons créée, nous voyons ceci :</span><span class="sxs-lookup"><span data-stu-id="ef557-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ef557-139">Pour supprimer des éléments contenus sans invite de confirmation, spécifiez le paramètre **-Recurse** :</span><span class="sxs-lookup"><span data-stu-id="ef557-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="ef557-140">Si vous souhaitez supprimer tous les éléments figurant dans HKCU:\\CurrentVersion mais pas HKCU:\\CurrentVersion proprement dit, vous pouvez utiliser à la place :</span><span class="sxs-lookup"><span data-stu-id="ef557-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
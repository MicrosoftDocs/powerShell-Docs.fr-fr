---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Utilisation de clés de Registre
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736843"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="71907-103">Utilisation de clés de Registre</span><span class="sxs-lookup"><span data-stu-id="71907-103">Working with Registry Keys</span></span>

<span data-ttu-id="71907-104">Étant donné que les clés de registre sont des éléments sur des lecteurs PowerShell, leur utilisation est très similaire à l’utilisation de fichiers et dossiers.</span><span class="sxs-lookup"><span data-stu-id="71907-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="71907-105">Une différence importante est que chaque élément sur un lecteur PowerShell basé sur un registre est un conteneur, tout comme un dossier sur un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="71907-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="71907-106">En revanche, les entrées de Registre et les valeurs qui leur sont associées sont des propriétés des éléments, pas des éléments distincts.</span><span class="sxs-lookup"><span data-stu-id="71907-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="71907-107">Affichage de la liste de toutes les sous-clés d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="71907-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="71907-108">Vous pouvez afficher tous les éléments figurant directement à l’intérieur d’une clé de registre à l’aide de `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="71907-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="71907-109">Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**.</span><span class="sxs-lookup"><span data-stu-id="71907-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="71907-110">Par exemple, cette commande affiche les éléments figurant directement dans le lecteur PowerShell `HKCU:`, qui correspond au hive du registre `HKEY_CURRENT_USER` :</span><span class="sxs-lookup"><span data-stu-id="71907-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="71907-111">Il s’agit des clés de niveau supérieur visibles sous `HKEY_CURRENT_USER` dans l’Éditeur du registre (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="71907-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="71907-112">Vous pouvez également définir ce chemin du registre en spécifiant le nom du fournisseur de registre, suivi de `::`.</span><span class="sxs-lookup"><span data-stu-id="71907-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="71907-113">Le nom complet du fournisseur de registre est `Microsoft.PowerShell.Core\Registry`, mais il peut être abrégé en `Registry` uniquement.</span><span class="sxs-lookup"><span data-stu-id="71907-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="71907-114">Toutes les commandes suivantes répertorient le contenu directement sous `HKCU:`.</span><span class="sxs-lookup"><span data-stu-id="71907-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="71907-115">Ces commandes répertorient uniquement les éléments contenus directement, de manière très similaire à l’utilisation de `DIR` dans **cmd.exe** ou `ls` dans un interpréteur de commandes UNIX.</span><span class="sxs-lookup"><span data-stu-id="71907-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="71907-116">Pour afficher les éléments contenus, vous devez spécifier le paramètre **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="71907-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="71907-117">Pour répertorier toutes les clés de registre dans `HKCU:`, utilisez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="71907-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="71907-118">`Get-ChildItem` peut exécuter des fonctionnalités de filtrage complexes via ses paramètres **Chemin d'accès**, **Filtre**, **Inclure** et **Exclure**, mais ces paramètres sont généralement basés uniquement sur le nom.</span><span class="sxs-lookup"><span data-stu-id="71907-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="71907-119">Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de la cmdlet `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="71907-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="71907-120">La commande suivante recherche dans `HKCU:\Software` toutes les clés qui n’ont pas plus d’une sous-clé et ont aussi exactement quatre valeurs :</span><span class="sxs-lookup"><span data-stu-id="71907-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="71907-121">Copie de clés</span><span class="sxs-lookup"><span data-stu-id="71907-121">Copying Keys</span></span>

<span data-ttu-id="71907-122">La copie s’effectue avec `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="71907-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="71907-123">L’exemple suivant copie la sous-clé `CurrentVersion` de `HKLM:\SOFTWARE\Microsoft\Windows\` et toutes ses propriétés dans `HKCU:\`.</span><span class="sxs-lookup"><span data-stu-id="71907-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="71907-124">Si vous examinez cette nouvelle clé dans l’Éditeur du registre ou en utilisant `Get-ChildItem`, vous remarquerez que vous n’avez pas de copies des sous-clés contenues dans le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="71907-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="71907-125">Pour copier tout le contenu d’un conteneur, vous devez spécifier le paramètre **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="71907-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="71907-126">Pour rendre la commande de copie précédente récursive, vous devez utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="71907-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="71907-127">Vous pouvez toujours utiliser d’autres outils déjà disponibles pour effectuer des copies du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="71907-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="71907-128">Les outils d’édition du registre (dont **reg.exe**, **regini.exe** et **regedit.exe**) et les objets COM qui prennent en charge l’édition du registre (par exemple, **WScript.Shell** et la classe **StdRegProv** de WM) peuvent être utilisés à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71907-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="71907-129">Création de clés</span><span class="sxs-lookup"><span data-stu-id="71907-129">Creating Keys</span></span>

<span data-ttu-id="71907-130">Créer des clés dans le Registre est plus simple que créer un élément dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="71907-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="71907-131">Étant donné que toutes les clés de Registre sont des conteneurs, il est inutile spécifier le type d’élément. Vous devez simplement fournir un chemin d’accès explicite, par exemple :</span><span class="sxs-lookup"><span data-stu-id="71907-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="71907-132">Pour spécifier une clé, vous pouvez également utiliser un chemin d’accès basé sur un fournisseur :</span><span class="sxs-lookup"><span data-stu-id="71907-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="71907-133">Suppression de clés</span><span class="sxs-lookup"><span data-stu-id="71907-133">Deleting Keys</span></span>

<span data-ttu-id="71907-134">La suppression d’éléments est essentiellement identique pour tous les fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="71907-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="71907-135">Les commandes suivantes suppriment des éléments en mode silencieux :</span><span class="sxs-lookup"><span data-stu-id="71907-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="71907-136">Suppression de toutes les clés sous une clé spécifique</span><span class="sxs-lookup"><span data-stu-id="71907-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="71907-137">Vous pouvez supprimer des éléments contenus à l’aide de `Remove-Item`, mais vous devez confirmer la suppression si les éléments contiennent autre chose.</span><span class="sxs-lookup"><span data-stu-id="71907-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="71907-138">Par exemple, si nous tentons de supprimer la sous-clé `HKCU:\CurrentVersion` que nous avons créée, nous voyons ceci :</span><span class="sxs-lookup"><span data-stu-id="71907-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="71907-139">Pour supprimer des éléments contenus sans invite de confirmation, spécifiez le paramètre **Recurse** :</span><span class="sxs-lookup"><span data-stu-id="71907-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="71907-140">Si vous vouliez supprimer tous les éléments dans `HKCU:\CurrentVersion` mais pas `HKCU:\CurrentVersion` lui-même, vous devrez plutôt utiliser :</span><span class="sxs-lookup"><span data-stu-id="71907-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

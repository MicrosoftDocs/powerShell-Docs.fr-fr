---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEFileCollection
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736213"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="23611-103">Objet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="23611-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="23611-104">L’objet **ISEFileCollection** est une collection d’objets **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="23611-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="23611-105">La collection `$psISE.CurrentPowerShellTab.Files` en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="23611-105">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="23611-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="23611-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="23611-107">Ajouter\( \[FullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="23611-107">Add\( \[FullPath\] \)</span></span>

<span data-ttu-id="23611-108">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="23611-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="23611-109">Crée et retourne un nouveau fichier sans titre, et l’ajoute à la collection.</span><span class="sxs-lookup"><span data-stu-id="23611-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="23611-110">La propriété **IsUntitled** du fichier nouvellement créé est `$true`.</span><span class="sxs-lookup"><span data-stu-id="23611-110">The **IsUntitled** property of the newly created file is `$true`.</span></span>

<span data-ttu-id="23611-111">**\[fullPath\]**  : chaîne facultative. Chemin entièrement spécifié du fichier.</span><span class="sxs-lookup"><span data-stu-id="23611-111">**\[FullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="23611-112">Une exception est générée si vous incluez le paramètre **FullPath** et un chemin d’accès relatif ou si vous utilisez un nom de fichier au lieu du chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="23611-112">An exception is generated if you include the **FullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="23611-113">Supprimer le fichier \(, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="23611-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="23611-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="23611-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="23611-115">Supprime un fichier spécifié dans l’onglet PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="23611-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="23611-116">**File** : chaîne. Fichier ISEFile que vous souhaitez supprimer de la collection.</span><span class="sxs-lookup"><span data-stu-id="23611-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="23611-117">Si le fichier n’a pas été enregistré, cette méthode lève une exception.</span><span class="sxs-lookup"><span data-stu-id="23611-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="23611-118">Utilisez le paramètre booléen **Force** pour forcer la suppression d’un fichier non enregistré.</span><span class="sxs-lookup"><span data-stu-id="23611-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="23611-119">**\[Force\]**  : valeur booléenne facultative. Si la valeur est `$true`, le fichier peut être supprimé même s’il n’a pas été enregistré depuis sa dernière utilisation.</span><span class="sxs-lookup"><span data-stu-id="23611-119">**\[Force\]** - optional Boolean If set to `$true`, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="23611-120">Par défaut, il s’agit de `$false`.</span><span class="sxs-lookup"><span data-stu-id="23611-120">The default is `$false`.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="23611-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="23611-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="23611-122">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="23611-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="23611-123">Sélectionne le fichier spécifié par le paramètre **SelectedFile**.</span><span class="sxs-lookup"><span data-stu-id="23611-123">Selects the file that is specified by the **SelectedFile** parameter.</span></span>

<span data-ttu-id="23611-124">**SelectedFile** : Microsoft.PowerShell.Host.ISE.ISEFile. Fichier ISEFile que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="23611-124">**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="23611-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23611-125">See Also</span></span>

- [<span data-ttu-id="23611-126">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="23611-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="23611-127">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="23611-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="23611-128">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="23611-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

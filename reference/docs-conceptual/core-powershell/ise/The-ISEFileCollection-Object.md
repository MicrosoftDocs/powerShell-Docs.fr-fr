---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="70df7-103">Objet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="70df7-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="70df7-104">L’objet **ISEFileCollection** est une collection d’objets **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="70df7-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="70df7-105">La collection $psISE.CurrentPowerShellTab.Files en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="70df7-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="70df7-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="70df7-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="70df7-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="70df7-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="70df7-108">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="70df7-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="70df7-109">Crée et retourne un nouveau fichier sans titre, et l’ajoute à la collection.</span><span class="sxs-lookup"><span data-stu-id="70df7-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="70df7-110">La propriété **IsUntitled** du nouveau fichier est **$true**.</span><span class="sxs-lookup"><span data-stu-id="70df7-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="70df7-111">**\[fullPath\]** : chaîne facultative. Chemin entièrement spécifié du fichier.</span><span class="sxs-lookup"><span data-stu-id="70df7-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="70df7-112">Une exception est générée si vous incluez le paramètre **fullPath** et un chemin d’accès relatif, ou si vous utilisez un nom de fichier au lieu du chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="70df7-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="70df7-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="70df7-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="70df7-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="70df7-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="70df7-115">Supprime un fichier spécifié dans l’onglet PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="70df7-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="70df7-116">**File** : chaîne. Fichier ISEFile que vous souhaitez supprimer de la collection.</span><span class="sxs-lookup"><span data-stu-id="70df7-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="70df7-117">Si le fichier n’a pas été enregistré, cette méthode lève une exception.</span><span class="sxs-lookup"><span data-stu-id="70df7-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="70df7-118">Utilisez le paramètre booléen **Force** pour forcer la suppression d’un fichier non enregistré.</span><span class="sxs-lookup"><span data-stu-id="70df7-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="70df7-119">**\[Force\]** : valeur booléenne facultative. Si la valeur est **$true**, le fichier peut être supprimé même s’il n’a pas été enregistré depuis sa dernière utilisation.</span><span class="sxs-lookup"><span data-stu-id="70df7-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="70df7-120">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="70df7-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="70df7-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="70df7-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="70df7-122">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="70df7-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="70df7-123">Sélectionne le fichier spécifié par le paramètre **selectedFile**.</span><span class="sxs-lookup"><span data-stu-id="70df7-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="70df7-124">**selectedFile** : Microsoft.PowerShell.Host.ISE.ISEFile. Fichier ISEFile que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="70df7-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="70df7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70df7-125">See Also</span></span>
- [<span data-ttu-id="70df7-126">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="70df7-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="70df7-127">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="70df7-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="70df7-128">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="70df7-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="70df7-129">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="70df7-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

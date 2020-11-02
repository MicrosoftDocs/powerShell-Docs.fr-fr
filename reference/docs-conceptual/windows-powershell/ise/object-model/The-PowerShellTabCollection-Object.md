---
ms.date: 06/05/2017
title: Objet PowerShellTabCollection
description: L’objet collection PowerShellTab est une collection d’objets PowerShellTab. Chaque objet PowerShellTab fonctionne comme un environnement d’exécution distinct.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658268"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="9c5ce-104">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="9c5ce-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="9c5ce-105">L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab** .</span><span class="sxs-lookup"><span data-stu-id="9c5ce-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="9c5ce-106">Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="9c5ce-107">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="9c5ce-108">L’objet `$psISE.PowerShellTabs` en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="9c5ce-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9c5ce-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="9c5ce-110">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="9c5ce-110">Add\(\)</span></span>

<span data-ttu-id="9c5ce-111">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9c5ce-112">Ajoute un nouvel onglet PowerShell à la collection.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="9c5ce-113">Elle retourne l’onglet qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="9c5ce-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="9c5ce-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="9c5ce-115">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9c5ce-116">Supprime l’onglet spécifié par le paramètre **psTab** .</span><span class="sxs-lookup"><span data-stu-id="9c5ce-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="9c5ce-117">**psTab** Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="9c5ce-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="9c5ce-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="9c5ce-119">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9c5ce-120">Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="9c5ce-121">**psTab** Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="9c5ce-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c5ce-122">See Also</span></span>

- [<span data-ttu-id="9c5ce-123">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="9c5ce-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="9c5ce-124">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9c5ce-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9c5ce-125">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="9c5ce-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet PowerShellTabCollection
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030492"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="d955c-103">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="d955c-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="d955c-104">L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="d955c-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="d955c-105">Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="d955c-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="d955c-106">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="d955c-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="d955c-107">L’objet **$psISE.PowerShellTabs** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="d955c-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d955c-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d955c-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="d955c-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="d955c-109">Add\(\)</span></span>

<span data-ttu-id="d955c-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d955c-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d955c-111">Ajoute un nouvel onglet PowerShell à la collection.</span><span class="sxs-lookup"><span data-stu-id="d955c-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="d955c-112">Elle retourne l’onglet qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="d955c-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d955c-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d955c-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d955c-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d955c-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d955c-115">Supprime l’onglet spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="d955c-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="d955c-116">**psTab** Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d955c-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d955c-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d955c-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d955c-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d955c-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d955c-119">Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="d955c-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="d955c-120">**psTab** Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="d955c-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d955c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d955c-121">See Also</span></span>

- [<span data-ttu-id="d955c-122">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d955c-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d955c-123">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d955c-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d955c-124">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="d955c-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

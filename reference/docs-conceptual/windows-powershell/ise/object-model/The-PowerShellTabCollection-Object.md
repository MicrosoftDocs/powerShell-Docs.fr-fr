---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet PowerShellTabCollection
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808565"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="2a320-103">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="2a320-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="2a320-104">L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="2a320-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="2a320-105">Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="2a320-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="2a320-106">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="2a320-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="2a320-107">L’objet `$psISE.PowerShellTabs` en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="2a320-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="2a320-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2a320-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="2a320-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="2a320-109">Add\(\)</span></span>

<span data-ttu-id="2a320-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2a320-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a320-111">Ajoute un nouvel onglet PowerShell à la collection.</span><span class="sxs-lookup"><span data-stu-id="2a320-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="2a320-112">Elle retourne l’onglet qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="2a320-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="2a320-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="2a320-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="2a320-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2a320-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a320-115">Supprime l’onglet spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="2a320-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="2a320-116">**psTab** Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2a320-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="2a320-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="2a320-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="2a320-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2a320-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a320-119">Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="2a320-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="2a320-120">**psTab** Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="2a320-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2a320-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a320-121">See Also</span></span>

- [<span data-ttu-id="2a320-122">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="2a320-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="2a320-123">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2a320-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2a320-124">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="2a320-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

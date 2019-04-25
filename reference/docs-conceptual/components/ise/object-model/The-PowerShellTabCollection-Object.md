---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086610"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="0b792-103">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="0b792-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="0b792-104">L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="0b792-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="0b792-105">Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="0b792-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="0b792-106">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="0b792-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="0b792-107">L’objet **$psISE.PowerShellTabs** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="0b792-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="0b792-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0b792-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="0b792-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="0b792-109">Add\(\)</span></span>

<span data-ttu-id="0b792-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0b792-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0b792-111">Ajoute un nouvel onglet PowerShell à la collection.</span><span class="sxs-lookup"><span data-stu-id="0b792-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="0b792-112">Elle retourne l’onglet qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="0b792-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0b792-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0b792-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="0b792-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0b792-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0b792-115">Supprime l’onglet spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="0b792-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="0b792-116">**psTab** Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0b792-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0b792-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0b792-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="0b792-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0b792-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0b792-119">Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="0b792-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="0b792-120">**psTab** Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="0b792-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b792-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b792-121">See Also</span></span>

- [<span data-ttu-id="0b792-122">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0b792-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="0b792-123">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0b792-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0b792-124">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="0b792-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
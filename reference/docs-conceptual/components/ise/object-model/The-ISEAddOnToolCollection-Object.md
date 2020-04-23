---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEAddOnToolCollection
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737013"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="36126-103">Objet ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="36126-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="36126-104">L’objet **ISEAddOnToolCollection** est une collection d’objets **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="36126-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="36126-105">L’objet `$psISE.CurrentPowerShellTab.VerticalAddOnTools` en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="36126-105">An example is the `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.</span></span>

## <a name="methods"></a><span data-ttu-id="36126-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="36126-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="36126-107">Ajouter\( Nom, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="36126-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="36126-108">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="36126-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="36126-109">Ajoute un nouvel outil complémentaire à la collection.</span><span class="sxs-lookup"><span data-stu-id="36126-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="36126-110">Elle retourne l’outil complémentaire qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="36126-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="36126-111">Avant d’exécuter cette commande, vous devez installer l’outil complémentaire sur l’ordinateur local et charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36126-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="36126-112">**Name** : chaîne. Spécifie le nom complet de l’outil complémentaire qui est ajouté à Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="36126-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="36126-113">**ControlType** : type. Spécifie le contrôle qui est ajouté.</span><span class="sxs-lookup"><span data-stu-id="36126-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="36126-114">**\[IsVisible\]**  : valeur booléenne facultative. Si la valeur définie est `$true`, l’outil de module complémentaire est immédiatement visible dans le volet d’outils associé.</span><span class="sxs-lookup"><span data-stu-id="36126-114">**\[IsVisible\]** - optional Boolean If set to `$true`, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="36126-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="36126-115">Remove\( Item \)</span></span>

<span data-ttu-id="36126-116">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="36126-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="36126-117">Supprime l’outil complémentaire spécifié de la collection.</span><span class="sxs-lookup"><span data-stu-id="36126-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="36126-118">**Item** : Microsoft.PowerShell.Host.ISE.ISEAddOnTool. Spécifie l’objet à supprimer de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="36126-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="36126-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="36126-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="36126-120">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="36126-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="36126-121">Sélectionne l’onglet PowerShell spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="36126-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="36126-122">**psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="36126-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="36126-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="36126-123">Remove\( psTab \)</span></span>

<span data-ttu-id="36126-124">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="36126-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="36126-125">Supprime l’onglet PowerShell spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="36126-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="36126-126">**psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="36126-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="36126-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36126-127">See Also</span></span>

- [<span data-ttu-id="36126-128">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="36126-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="36126-129">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="36126-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="36126-130">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="36126-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

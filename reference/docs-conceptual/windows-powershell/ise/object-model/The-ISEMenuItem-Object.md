---
ms.date: 12/31/2019
title: Objet ISEMenuItem
description: Un objet ISEMenuItem est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItem. Tous les objets du menu **Modules complémentaires** sont des instances de la classe ISEMenuItem.
ms.openlocfilehash: 15036e3551687a21dfbe50834a89247c80949656
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663434"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="1d28d-104">Objet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="1d28d-104">The ISEMenuItem Object</span></span>

<span data-ttu-id="1d28d-105">Un objet **ISEMenuItem** est une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="1d28d-105">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="1d28d-106">Tous les objets du menu **Modules complémentaires** sont des instances de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="1d28d-106">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="1d28d-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1d28d-107">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="1d28d-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1d28d-108">DisplayName</span></span>

<span data-ttu-id="1d28d-109">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d28d-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1d28d-110">Propriété en lecture seule qui obtient le nom complet de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="1d28d-110">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="1d28d-111">Action</span><span class="sxs-lookup"><span data-stu-id="1d28d-111">Action</span></span>

<span data-ttu-id="1d28d-112">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d28d-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1d28d-113">Propriété en lecture seule qui obtient le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="1d28d-113">The read-only property that gets the block of script.</span></span> <span data-ttu-id="1d28d-114">Elle appelle l’action qui est associée à l’élément de menu sur lequel vous cliquez.</span><span class="sxs-lookup"><span data-stu-id="1d28d-114">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="1d28d-115">Raccourci</span><span class="sxs-lookup"><span data-stu-id="1d28d-115">Shortcut</span></span>

<span data-ttu-id="1d28d-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d28d-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1d28d-117">Propriété en lecture seule qui obtient le raccourci clavier d’entrée Windows associé à l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="1d28d-117">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="1d28d-118">Submenus</span><span class="sxs-lookup"><span data-stu-id="1d28d-118">Submenus</span></span>

<span data-ttu-id="1d28d-119">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d28d-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1d28d-120">Propriété en lecture seule qui obtient la [liste des sous-menus](The-ISEMenuItemCollection-Object.md) de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="1d28d-120">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="1d28d-121">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="1d28d-121">Scripting example</span></span>

<span data-ttu-id="1d28d-122">Pour mieux comprendre l’utilisation du menu Modules complémentaires et ses propriétés de script, consultez l’exemple de script suivant.</span><span class="sxs-lookup"><span data-stu-id="1d28d-122">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="1d28d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d28d-123">See Also</span></span>

- [<span data-ttu-id="1d28d-124">Objet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="1d28d-124">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="1d28d-125">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1d28d-125">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1d28d-126">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="1d28d-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

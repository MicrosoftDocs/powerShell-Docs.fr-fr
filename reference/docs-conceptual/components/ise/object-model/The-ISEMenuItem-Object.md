---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402011"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="20077-103">Objet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="20077-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="20077-104">Un objet **ISEMenuItem** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="20077-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="20077-105">Tous les objets du menu **Modules complémentaires** sont des instances de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="20077-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="20077-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="20077-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="20077-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="20077-107">DisplayName</span></span>

<span data-ttu-id="20077-108">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="20077-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="20077-109">Propriété en lecture seule qui obtient le nom complet de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="20077-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="20077-110">Action</span><span class="sxs-lookup"><span data-stu-id="20077-110">Action</span></span>

<span data-ttu-id="20077-111">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="20077-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="20077-112">Propriété en lecture seule qui obtient le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="20077-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="20077-113">Elle appelle l’action qui est associée à l’élément de menu sur lequel vous cliquez.</span><span class="sxs-lookup"><span data-stu-id="20077-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="20077-114">Shortcut</span><span class="sxs-lookup"><span data-stu-id="20077-114">Shortcut</span></span>

<span data-ttu-id="20077-115">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="20077-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="20077-116">Propriété en lecture seule qui obtient le raccourci clavier d’entrée Windows associé à l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="20077-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="20077-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="20077-117">Submenus</span></span>

<span data-ttu-id="20077-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="20077-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="20077-119">Propriété en lecture seule qui obtient la [liste des sous-menus](The-ISEMenuItemCollection-Object.md) de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="20077-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="20077-120">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="20077-120">Scripting example</span></span>

<span data-ttu-id="20077-121">Pour mieux comprendre l’utilisation du menu Modules complémentaires et ses propriétés de script, consultez l’exemple de script suivant.</span><span class="sxs-lookup"><span data-stu-id="20077-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="20077-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20077-122">See Also</span></span>

- [<span data-ttu-id="20077-123">Objet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="20077-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="20077-124">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="20077-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="20077-125">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="20077-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
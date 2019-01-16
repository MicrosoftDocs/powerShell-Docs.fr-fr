---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401887"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="c6a4c-103">Objet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="c6a4c-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="c6a4c-104">Un objet **ISEMenuItemCollection** est une collection d’objets **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="c6a4c-105">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="c6a4c-106">Par exemple, l’objet **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** est utilisé pour personnaliser le menu **Module complémentaire** dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="c6a4c-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="c6a4c-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="c6a4c-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="c6a4c-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="c6a4c-109">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c6a4c-110">Ajoute un élément de menu à la collection.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="c6a4c-111">**DisplayName** Nom complet du menu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="c6a4c-112">**Action** Objet **System.Management.Automation.ScriptBlock** qui spécifie l’action associée à cet élément de menu.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="c6a4c-113">**Shortcut** Raccourci clavier associé à l’action.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="c6a4c-114">**Returns** Objet ISEMenuItem qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="c6a4c-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="c6a4c-115">Clear\(\)</span></span>

<span data-ttu-id="c6a4c-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c6a4c-117">Supprime tous les sous-menus de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="c6a4c-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="c6a4c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6a4c-118">See Also</span></span>

- [<span data-ttu-id="c6a4c-119">Objet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="c6a4c-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="c6a4c-120">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c6a4c-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c6a4c-121">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="c6a4c-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
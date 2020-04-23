---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEMenuItemCollection
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736170"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="6044a-103">Objet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="6044a-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="6044a-104">Un objet **ISEMenuItemCollection** est une collection d’objets **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="6044a-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="6044a-105">Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection**.</span><span class="sxs-lookup"><span data-stu-id="6044a-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** class.</span></span> <span data-ttu-id="6044a-106">Par exemple, l’objet `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` est utilisé pour personnaliser le menu **Composant additionnel** dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="6044a-106">An example is the `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="6044a-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="6044a-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="6044a-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="6044a-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="6044a-109">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6044a-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6044a-110">Ajoute un élément de menu à la collection.</span><span class="sxs-lookup"><span data-stu-id="6044a-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="6044a-111">**DisplayName** Nom complet du menu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="6044a-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="6044a-112">**Action** Objet **System.Management.Automation.ScriptBlock** qui spécifie l’action associée à cet élément de menu.</span><span class="sxs-lookup"><span data-stu-id="6044a-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="6044a-113">**Shortcut** Raccourci clavier associé à l’action.</span><span class="sxs-lookup"><span data-stu-id="6044a-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="6044a-114">**Renvoie** l’objet **ISEMenuItem** qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="6044a-114">**Returns** The **ISEMenuItem** object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="6044a-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="6044a-115">Clear\(\)</span></span>

<span data-ttu-id="6044a-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6044a-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6044a-117">Supprime tous les sous-menus de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="6044a-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="6044a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6044a-118">See Also</span></span>

- [<span data-ttu-id="6044a-119">Objet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="6044a-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="6044a-120">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6044a-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6044a-121">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="6044a-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

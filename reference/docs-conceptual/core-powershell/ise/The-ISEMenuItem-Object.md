---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950707"
---
# <a name="the-isemenuitem-object"></a>Objet ISEMenuItem

Un objet **ISEMenuItem** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItem. Tous les objets du menu **Modules complémentaires** sont des instances de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## <a name="properties"></a>Propriétés

### <a name="displayname"></a>DisplayName

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le nom complet de l’élément de menu.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Action

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le bloc de script. Elle appelle l’action qui est associée à l’élément de menu sur lequel vous cliquez.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Shortcut

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le raccourci clavier d’entrée Windows associé à l’élément de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenus

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la [liste des sous-menus](The-ISEMenuItemCollection-Object.md) de l’élément de menu.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Exemple de script

Pour mieux comprendre l’utilisation du menu Modules complémentaires et ses propriétés de script, consultez l’exemple de script suivant.

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

## <a name="see-also"></a>Voir aussi

- [Objet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
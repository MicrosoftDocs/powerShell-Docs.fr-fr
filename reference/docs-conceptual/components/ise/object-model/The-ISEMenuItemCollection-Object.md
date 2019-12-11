---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEMenuItemCollection
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030546"
---
# <a name="the-isemenuitemcollection-object"></a>Objet ISEMenuItemCollection

Un objet **ISEMenuItemCollection** est une collection d’objets **ISEMenuItem**. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Par exemple, l’objet **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** est utilisé pour personnaliser le menu **Module complémentaire** dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.

## <a name="method"></a>Méthode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Ajoute un élément de menu à la collection.

**DisplayName** Nom complet du menu à ajouter.

**Action** Objet **System.Management.Automation.ScriptBlock** qui spécifie l’action associée à cet élément de menu.

**Shortcut** Raccourci clavier associé à l’action.

**Returns** Objet ISEMenuItem qui vient d’être ajouté.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Supprime tous les sous-menus de l’élément de menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Voir aussi

- [Objet ISEMenuItem](The-ISEMenuItem-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

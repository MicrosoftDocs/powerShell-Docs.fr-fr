---
ms.date: 06/05/2017
title: Objet ISESnippet
description: Un objet ISESnippet est une instance de la classe Microsoft.PowerShell.Host.ISE.ISESnippet.
ms.openlocfilehash: 602b344686cbcfb1e994914d4e26438ff7e4b1de
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663412"
---
# <a name="the-isesnippetobject"></a>Objet ISESnippet

Un objet **ISESnippet** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISESnippet. Les membres de la collection `$psISE.CurrentPowerShellTab.Snippets` sont tous des exemples d’objets **ISESnippet** . La façon la plus simple de créer un extrait de code est d’utiliser la cmdlet [New-IseSnippet](/powershell/module/ISE/New-IseSnippet).

## <a name="properties"></a>Propriétés

### <a name="author"></a>Auteur

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le nom de l’auteur de l’extrait de code.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le fragment de code à insérer dans l’éditeur.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Raccourci

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui obtient le raccourci clavier Windows associé à l’élément de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Voir aussi

- [Objet ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippet
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028887"
---
# <a name="the-isesnippetobject"></a>Objet ISESnippet

Un objet **ISESnippet** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISESnippet. Les membres de la collection **$psISE.CurrentPowerShellTab.Snippets** sont tous des exemples d’objets **ISESnippet**. La façon la plus simple de créer un extrait de code est d’utiliser l’applet de commande [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

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

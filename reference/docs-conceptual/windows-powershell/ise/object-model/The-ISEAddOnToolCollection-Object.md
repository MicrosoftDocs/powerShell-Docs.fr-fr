---
ms.date: 12/31/2019
title: Objet ISEAddOnToolCollection
description: L’objet ISEAddOnToolCollection est une collection d’objets **ISEAddOnTool** .
ms.openlocfilehash: ba08ffd82a7ff2fa469540a5ea542abee8d4dc82
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658310"
---
# <a name="the-iseaddontoolcollection-object"></a>Objet ISEAddOnToolCollection

L’objet **ISEAddOnToolCollection** est une collection d’objets **ISEAddOnTool** . L’objet `$psISE.CurrentPowerShellTab.VerticalAddOnTools` en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add-name-controltype-isvisible-"></a>Ajouter\( Nom, ControlType, \[IsVisible\] \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Ajoute un nouvel outil complémentaire à la collection. Elle retourne l’outil complémentaire qui vient d’être ajouté. Avant d’exécuter cette commande, vous devez installer l’outil complémentaire sur l’ordinateur local et charger l’assembly.

**Name**  : chaîne. Spécifie le nom complet de l’outil complémentaire qui est ajouté à Windows PowerShell ISE.

**ControlType**  : type. Spécifie le contrôle qui est ajouté.

**\[IsVisible\]**  : valeur booléenne facultative. Si la valeur définie est `$true`, l’outil de module complémentaire est immédiatement visible dans le volet d’outils associé.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Supprime l’outil complémentaire spécifié de la collection.

**Item**  : Microsoft.PowerShell.Host.ISE.ISEAddOnTool. Spécifie l’objet à supprimer de Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Sélectionne l’onglet PowerShell spécifié par le paramètre **psTab** .

**psTab**  : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à sélectionner.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Supprime l’onglet PowerShell spécifié par le paramètre **psTab** .

**psTab**  : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à supprimer.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Voir aussi

- [Objet PowerShellTab](The-PowerShellTab-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

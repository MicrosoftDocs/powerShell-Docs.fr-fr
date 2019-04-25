---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057374"
---
# <a name="the-iseaddontoolcollection-object"></a>Objet ISEAddOnToolCollection

L’objet **ISEAddOnToolCollection** est une collection d’objets **ISEAddOnTool**. L’objet **$psISE.CurrentPowerShellTab.VerticalAddOnTools** en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add-name-controltype-isvisible-"></a>Add\( Name, ControlType, \[IsVisible\] \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Ajoute un nouvel outil complémentaire à la collection. Elle retourne l’outil complémentaire qui vient d’être ajouté. Avant d’exécuter cette commande, vous devez installer l’outil complémentaire sur l’ordinateur local et charger l’assembly.

**Name** : chaîne. Spécifie le nom complet de l’outil complémentaire qui est ajouté à Windows PowerShell ISE.

**ControlType** : type. Spécifie le contrôle qui est ajouté.

**\[IsVisible\]**  : valeur booléenne facultative. Si la valeur définie est **$true**, l’outil complémentaire est immédiatement visible dans le volet d’outils associé.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Supprime l’outil complémentaire spécifié de la collection.

**Item** : Microsoft.PowerShell.Host.ISE.ISEAddOnTool. Spécifie l’objet à supprimer de Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Sélectionne l’onglet PowerShell spécifié par le paramètre **psTab**.

**psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à sélectionner.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Supprime l’onglet PowerShell spécifié par le paramètre **psTab**.

**psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab. Onglet PowerShell à supprimer.

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
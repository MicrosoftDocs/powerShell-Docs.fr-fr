---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEFileCollection
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809335"
---
# <a name="the-isefilecollection-object"></a>Objet ISEFileCollection

L’objet **ISEFileCollection** est une collection d’objets **ISEFile**. La collection `$psISE.CurrentPowerShellTab.Files` en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add-fullpath-"></a>Ajouter\( \[FullPath\] \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Crée et retourne un nouveau fichier sans titre, et l’ajoute à la collection. La propriété **IsUntitled** du fichier nouvellement créé est `$true`.

**\[fullPath\]**  : chaîne facultative. Chemin entièrement spécifié du fichier. Une exception est générée si vous incluez le paramètre **FullPath** et un chemin d’accès relatif ou si vous utilisez un nom de fichier au lieu du chemin d’accès complet.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Supprimer le fichier \(, \[Force\] \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Supprime un fichier spécifié dans l’onglet PowerShell actuel.

**File** : chaîne. Fichier ISEFile que vous souhaitez supprimer de la collection. Si le fichier n’a pas été enregistré, cette méthode lève une exception. Utilisez le paramètre booléen **Force** pour forcer la suppression d’un fichier non enregistré.

**\[Force\]**  : valeur booléenne facultative. Si la valeur est `$true`, le fichier peut être supprimé même s’il n’a pas été enregistré depuis sa dernière utilisation. Par défaut, il s’agit de `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Sélectionne le fichier spécifié par le paramètre **SelectedFile**.

**SelectedFile** : Microsoft.PowerShell.Host.ISE.ISEFile. Fichier ISEFile que vous souhaitez sélectionner.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Voir aussi

- [Objet ISEFile](The-ISEFile-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

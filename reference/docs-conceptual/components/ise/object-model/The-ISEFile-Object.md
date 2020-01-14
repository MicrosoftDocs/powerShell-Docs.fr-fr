---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEFile
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736996"
---
# <a name="the-isefile-object"></a>Objet ISEFile

Un objet **ISEFile** représente un fichier dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®. Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEFile**. Cette rubrique répertorie les méthodes et propriétés membres de cet objet. Le `$psISE.CurrentFile` et les fichiers de le regroupement de fichiers dans un onglet PowerShell sont tous des instances de la classe ****Microsoft.PowerShell.Host.ISE.ISEFile**.

## <a name="methods"></a>Méthodes

### <a name="save-saveencoding-"></a>Enregistrer \( \[saveEncoding\] \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Enregistre le fichier sur le disque.

**\[saveEncoding\]** (facultatif) [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré. La valeur par défaut est **UTF8**.

### <a name="exceptions"></a>Exceptions

- **System.IO.IOException** : impossible d’enregistrer le fichier.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(nom_fichier, \[saveEncoding\]\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Enregistre le fichier avec le nom de fichier et l’encodage spécifiés.

**filename** : chaîne Nom à utiliser pour enregistrer le fichier.

**\[saveEncoding\]** (facultatif) [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré. La valeur par défaut est **UTF8**.

### <a name="exceptions"></a>Exceptions

- **System.ArgumentNullException** : le paramètre **filename** est nul.
- **System.ArgumentException** : le paramètre **filename** est vide.
- **System.IO.IOException** : impossible d’enregistrer le fichier.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Propriétés

### <a name="displayname"></a>DisplayName

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la chaîne contenant le nom complet de ce fichier. Le nom est affiché dans l’onglet **Fichier** en haut de l’éditeur. La présence d’un astérisque `(*)` à la fin du nom indique que le fichier comporte des modifications qui n’ont pas encore été enregistrées.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Éditeur

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient l’[objet editor](The-ISEEditor-Object.md) utilisé pour le fichier spécifié.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encodage

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient l’encodage du fichier initial. Il s’agit d’un objet **System.Text.Encoding**.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la chaîne spécifiant le chemin complet du fichier ouvert.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété booléenne en lecture seule qui renvoie la valeur `$true` si le fichier a été enregistré depuis sa dernière modification.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui renvoie la valeur `$true` si le fichier n’a pas encore de titre.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Voir aussi

- [Objet ISEFileCollection](The-ISEFileCollection-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401773"
---
# <a name="the-isefile-object"></a><span data-ttu-id="10e25-103">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="10e25-103">The ISEFile Object</span></span>

<span data-ttu-id="10e25-104">Un objet **ISEFile** représente un fichier dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="10e25-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="10e25-105">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="10e25-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="10e25-106">Cette rubrique répertorie les méthodes et propriétés membres de cet objet.</span><span class="sxs-lookup"><span data-stu-id="10e25-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="10e25-107">**$psISE.CurrentFile** et les fichiers de la collection Files dans un onglet PowerShell sont tous des instances de la classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="10e25-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="10e25-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="10e25-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="10e25-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="10e25-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="10e25-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-111">Enregistre le fichier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="10e25-111">Saves the file to disk.</span></span>

<span data-ttu-id="10e25-112">**\[saveEncoding\]** (facultatif) [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="10e25-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="10e25-113">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="10e25-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="10e25-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="10e25-114">Exceptions</span></span>

- <span data-ttu-id="10e25-115">**System.IO.IOException**: Impossible d'enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="10e25-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="10e25-116">SaveAs\(nom_fichier, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="10e25-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="10e25-117">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-118">Enregistre le fichier avec le nom de fichier et l’encodage spécifiés.</span><span class="sxs-lookup"><span data-stu-id="10e25-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="10e25-119">**filename** : chaîne Nom à utiliser pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="10e25-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="10e25-120">**\[saveEncoding\]** (facultatif) [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="10e25-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="10e25-121">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="10e25-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="10e25-122">Exceptions</span><span class="sxs-lookup"><span data-stu-id="10e25-122">Exceptions</span></span>

- <span data-ttu-id="10e25-123">**System.ArgumentNullException**: Le **filename** paramètre a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="10e25-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="10e25-124">**System.ArgumentException**: Le **filename** paramètre est vide.</span><span class="sxs-lookup"><span data-stu-id="10e25-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="10e25-125">**System.IO.IOException**: Impossible d'enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="10e25-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="10e25-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="10e25-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="10e25-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10e25-127">DisplayName</span></span>

<span data-ttu-id="10e25-128">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-129">Propriété en lecture seule qui obtient la chaîne contenant le nom complet de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="10e25-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="10e25-130">Le nom est affiché dans l’onglet **Fichier** en haut de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="10e25-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="10e25-131">La présence d’un astérisque \(\*\) à la fin du nom indique que le fichier comporte des modifications qui n’ont pas encore été enregistrées.</span><span class="sxs-lookup"><span data-stu-id="10e25-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="10e25-132">Editor</span><span class="sxs-lookup"><span data-stu-id="10e25-132">Editor</span></span>

<span data-ttu-id="10e25-133">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-134">Propriété en lecture seule qui obtient l’[objet editor](The-ISEEditor-Object.md) utilisé pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="10e25-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="10e25-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="10e25-135">Encoding</span></span>

<span data-ttu-id="10e25-136">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-137">Propriété en lecture seule qui obtient l’encodage du fichier initial.</span><span class="sxs-lookup"><span data-stu-id="10e25-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="10e25-138">Il s’agit d’un objet **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="10e25-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="10e25-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="10e25-139">FullPath</span></span>

<span data-ttu-id="10e25-140">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-141">Propriété en lecture seule qui obtient la chaîne spécifiant le chemin complet du fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="10e25-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="10e25-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="10e25-142">IsSaved</span></span>

<span data-ttu-id="10e25-143">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-144">Propriété booléenne en lecture seule qui renvoie la valeur **$true** si le fichier a été enregistré depuis sa dernière modification.</span><span class="sxs-lookup"><span data-stu-id="10e25-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="10e25-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="10e25-145">IsUntitled</span></span>

<span data-ttu-id="10e25-146">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="10e25-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="10e25-147">Propriété en lecture seule qui renvoie la valeur **$true** si le fichier n’a pas encore de titre.</span><span class="sxs-lookup"><span data-stu-id="10e25-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="10e25-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10e25-148">See Also</span></span>

- [<span data-ttu-id="10e25-149">Objet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="10e25-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="10e25-150">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="10e25-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="10e25-151">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="10e25-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
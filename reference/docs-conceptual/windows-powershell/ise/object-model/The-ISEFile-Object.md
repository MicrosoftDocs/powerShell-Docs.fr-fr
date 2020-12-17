---
ms.date: 12/31/2019
title: Objet ISEFile
description: Un objet ISEFile représente un fichier dans Windows PowerShell ISE.
ms.openlocfilehash: b5ea70219787f254fe85d728518cbc4746c00250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391491"
---
# <a name="the-isefile-object"></a><span data-ttu-id="75969-103">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="75969-103">The ISEFile Object</span></span>

<span data-ttu-id="75969-104">Un objet **ISEFile** représente un fichier dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75969-104">An **ISEFile** object represents a file in Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="75969-105">Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="75969-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEFile** class.</span></span> <span data-ttu-id="75969-106">Cette rubrique répertorie les méthodes et propriétés membres de cet objet.</span><span class="sxs-lookup"><span data-stu-id="75969-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="75969-107">Le `$psISE.CurrentFile` et les fichiers de le regroupement de fichiers dans un onglet PowerShell sont tous des instances de la classe \*\***Microsoft.PowerShell.Host.ISE.ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="75969-107">The `$psISE.CurrentFile` and the files in the Files collection in a PowerShell tab are all instances of the \*\*\*\*Microsoft.PowerShell.Host.ISE.ISEFile\*\* class.</span></span>

## <a name="methods"></a><span data-ttu-id="75969-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="75969-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="75969-109">Enregistrer \( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="75969-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="75969-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-111">Enregistre le fichier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="75969-111">Saves the file to disk.</span></span>

<span data-ttu-id="75969-112">`[saveEncoding]` - (facultatif) [System.Text.Encoding](/dotnet/api/system.text.encoding) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="75969-112">`[saveEncoding]` - optional [System.Text.Encoding](/dotnet/api/system.text.encoding) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="75969-113">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="75969-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="75969-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="75969-114">Exceptions</span></span>

- <span data-ttu-id="75969-115">**System.IO.IOException** : le fichier n’a pas pu être enregistré.</span><span class="sxs-lookup"><span data-stu-id="75969-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="75969-116">SaveAs\(nom_fichier, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="75969-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="75969-117">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-118">Enregistre le fichier avec le nom de fichier et l’encodage spécifiés.</span><span class="sxs-lookup"><span data-stu-id="75969-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="75969-119">**filename** : chaîne Nom à utiliser pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="75969-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="75969-120">`[saveEncoding]` - (facultatif) [System.Text.Encoding](/dotnet/api/system.text.encoding) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="75969-120">`[saveEncoding]` - optional [System.Text.Encoding](/dotnet/api/system.text.encoding) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="75969-121">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="75969-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="75969-122">Exceptions</span><span class="sxs-lookup"><span data-stu-id="75969-122">Exceptions</span></span>

- <span data-ttu-id="75969-123">**System.ArgumentNullException** : le paramètre **filename** est Null.</span><span class="sxs-lookup"><span data-stu-id="75969-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="75969-124">**System.ArgumentException** : le paramètre **filename** est vide.</span><span class="sxs-lookup"><span data-stu-id="75969-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="75969-125">**System.IO.IOException** : le fichier n’a pas pu être enregistré.</span><span class="sxs-lookup"><span data-stu-id="75969-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="75969-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="75969-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="75969-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="75969-127">DisplayName</span></span>

<span data-ttu-id="75969-128">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-129">Propriété en lecture seule qui obtient la chaîne contenant le nom complet de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="75969-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="75969-130">Le nom est affiché dans l’onglet **Fichier** en haut de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="75969-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="75969-131">La présence d’un astérisque `(*)` à la fin du nom indique que le fichier comporte des modifications qui n’ont pas encore été enregistrées.</span><span class="sxs-lookup"><span data-stu-id="75969-131">The presence of an asterisk `(*)` at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="75969-132">Éditeur</span><span class="sxs-lookup"><span data-stu-id="75969-132">Editor</span></span>

<span data-ttu-id="75969-133">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-134">Propriété en lecture seule qui obtient l’[objet editor](The-ISEEditor-Object.md) utilisé pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="75969-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="75969-135">Encodage</span><span class="sxs-lookup"><span data-stu-id="75969-135">Encoding</span></span>

<span data-ttu-id="75969-136">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-137">Propriété en lecture seule qui obtient l’encodage du fichier initial.</span><span class="sxs-lookup"><span data-stu-id="75969-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="75969-138">Il s’agit d’un objet **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="75969-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="75969-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="75969-139">FullPath</span></span>

<span data-ttu-id="75969-140">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-141">Propriété en lecture seule qui obtient la chaîne spécifiant le chemin complet du fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="75969-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="75969-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="75969-142">IsSaved</span></span>

<span data-ttu-id="75969-143">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-144">Propriété booléenne en lecture seule qui renvoie la valeur `$true` si le fichier a été enregistré depuis sa dernière modification.</span><span class="sxs-lookup"><span data-stu-id="75969-144">The read-only Boolean property that returns `$true` if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="75969-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="75969-145">IsUntitled</span></span>

<span data-ttu-id="75969-146">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="75969-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="75969-147">Propriété en lecture seule qui renvoie la valeur `$true` si le fichier n’a pas encore de titre.</span><span class="sxs-lookup"><span data-stu-id="75969-147">The read-only property that returns `$true` if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="75969-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75969-148">See Also</span></span>

- [<span data-ttu-id="75969-149">Objet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="75969-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="75969-150">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="75969-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="75969-151">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="75969-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

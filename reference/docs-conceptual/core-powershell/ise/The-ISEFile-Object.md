---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="7e777-103">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="7e777-103">The ISEFile Object</span></span>
  <span data-ttu-id="7e777-104">Un objet **ISEFile** représente un fichier dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="7e777-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="7e777-105">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="7e777-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="7e777-106">Cette rubrique répertorie les méthodes et propriétés membres de cet objet.</span><span class="sxs-lookup"><span data-stu-id="7e777-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="7e777-107">**$psISE.CurrentFile** et les fichiers de la collection Files dans un onglet PowerShell sont tous des instances de la classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="7e777-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="7e777-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7e777-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="7e777-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="7e777-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="7e777-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-111">Enregistre le fichier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="7e777-111">Saves the file to disk.</span></span>

 <span data-ttu-id="7e777-112">**\[saveEncoding\]** (facultatif) [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="7e777-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="7e777-113">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="7e777-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="7e777-114">**Exceptions**</span><span class="sxs-lookup"><span data-stu-id="7e777-114">**Exceptions**</span></span>
 -   <span data-ttu-id="7e777-115">**System.IO.IOException** : le fichier n’a pas pu être enregistré.</span><span class="sxs-lookup"><span data-stu-id="7e777-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="7e777-116">SaveAs\(nom_fichier, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="7e777-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="7e777-117">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-118">Enregistre le fichier avec le nom de fichier et l’encodage spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7e777-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="7e777-119">**filename** : chaîne Nom à utiliser pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="7e777-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="7e777-120">**\[saveEncoding\]** (facultatif) [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré.</span><span class="sxs-lookup"><span data-stu-id="7e777-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="7e777-121">La valeur par défaut est **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="7e777-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="7e777-122">**Exceptions**</span><span class="sxs-lookup"><span data-stu-id="7e777-122">**Exceptions**</span></span>
 -   <span data-ttu-id="7e777-123">**System.ArgumentNullException** : le paramètre **filename** est Null.</span><span class="sxs-lookup"><span data-stu-id="7e777-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="7e777-124">**System.ArgumentException** : le paramètre **filename** est vide.</span><span class="sxs-lookup"><span data-stu-id="7e777-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="7e777-125">**System.IO.IOException** : le fichier n’a pas pu être enregistré.</span><span class="sxs-lookup"><span data-stu-id="7e777-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="7e777-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7e777-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="7e777-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7e777-127">DisplayName</span></span>
  <span data-ttu-id="7e777-128">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7e777-129">Propriété en lecture seule qui obtient la chaîne contenant le nom complet de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="7e777-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="7e777-130">Le nom est affiché dans l’onglet **Fichier** en haut de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="7e777-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="7e777-131">La présence d’un astérisque \(\*\) à la fin du nom indique que le fichier comporte des modifications qui n’ont pas encore été enregistrées.</span><span class="sxs-lookup"><span data-stu-id="7e777-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="7e777-132">Editor</span><span class="sxs-lookup"><span data-stu-id="7e777-132">Editor</span></span>
  <span data-ttu-id="7e777-133">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-134">Propriété en lecture seule qui obtient l’[objet editor](The-ISEEditor-Object.md) utilisé pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e777-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="7e777-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="7e777-135">Encoding</span></span>
  <span data-ttu-id="7e777-136">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-137">Propriété en lecture seule qui obtient l’encodage du fichier initial.</span><span class="sxs-lookup"><span data-stu-id="7e777-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="7e777-138">Il s’agit d’un objet **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="7e777-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="7e777-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="7e777-139">FullPath</span></span>
  <span data-ttu-id="7e777-140">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-141">Propriété en lecture seule qui obtient la chaîne spécifiant le chemin complet du fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="7e777-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="7e777-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="7e777-142">IsSaved</span></span>
  <span data-ttu-id="7e777-143">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-144">Propriété booléenne en lecture seule qui renvoie la valeur **$true** si le fichier a été enregistré depuis sa dernière modification.</span><span class="sxs-lookup"><span data-stu-id="7e777-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="7e777-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="7e777-145">IsUntitled</span></span>
  <span data-ttu-id="7e777-146">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7e777-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7e777-147">Propriété en lecture seule qui renvoie la valeur **$true** si le fichier n’a pas encore de titre.</span><span class="sxs-lookup"><span data-stu-id="7e777-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="7e777-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e777-148">See Also</span></span>
- [<span data-ttu-id="7e777-149">Objet ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="7e777-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="7e777-150">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7e777-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="7e777-151">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7e777-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="7e777-152">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="7e777-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

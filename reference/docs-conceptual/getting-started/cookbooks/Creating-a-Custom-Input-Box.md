---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Création d'une zone d'entrée personnalisée"
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 94172102fb81a9b31b7e84188f3e60a372e9cba2
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="30c1a-103">Création d'une zone d'entrée personnalisée</span><span class="sxs-lookup"><span data-stu-id="30c1a-103">Creating a Custom Input Box</span></span>
<span data-ttu-id="30c1a-104">Dans Windows PowerShell 3.0 et versions ultérieures, utilisez les fonctionnalités de création de formulaires de Microsoft .NET Framework pour créer une zone d'entrée graphique personnalisée à l'aide d'un script.</span><span class="sxs-lookup"><span data-stu-id="30c1a-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="30c1a-105">Créer une zone d'entrée graphique personnalisée</span><span class="sxs-lookup"><span data-stu-id="30c1a-105">Create a custom, graphical input box</span></span>
<span data-ttu-id="30c1a-106">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="30c1a-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="30c1a-107">Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="30c1a-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="30c1a-108">Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form**. Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="30c1a-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="30c1a-109">Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.</span><span class="sxs-lookup"><span data-stu-id="30c1a-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="30c1a-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="30c1a-110">**Text.**</span></span> <span data-ttu-id="30c1a-111">Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="30c1a-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="30c1a-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="30c1a-112">**Size.**</span></span> <span data-ttu-id="30c1a-113">Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="30c1a-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="30c1a-114">Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="30c1a-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="30c1a-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="30c1a-115">**StartingPosition.**</span></span> <span data-ttu-id="30c1a-116">Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.</span><span class="sxs-lookup"><span data-stu-id="30c1a-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="30c1a-117">Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert.</span><span class="sxs-lookup"><span data-stu-id="30c1a-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="30c1a-118">Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="30c1a-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="30c1a-119">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="30c1a-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="30c1a-120">Spécifiez la taille et le comportement du bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="30c1a-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="30c1a-121">Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="30c1a-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="30c1a-122">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="30c1a-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="30c1a-123">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="30c1a-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="30c1a-124">De la même façon, créez un bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="30c1a-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="30c1a-125">Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="30c1a-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="30c1a-126">Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="30c1a-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

<span data-ttu-id="30c1a-127">Ajoutez le contrôle (dans ce cas, une zone de texte) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans votre texte d'étiquette.</span><span class="sxs-lookup"><span data-stu-id="30c1a-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="30c1a-128">Hormis les zones de texte, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="30c1a-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

<span data-ttu-id="30c1a-129">Affectez à la propriété **Topmost** la valeur **$True** pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="30c1a-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="30c1a-130">Ensuite, ajoutez cette ligne de code pour activer le formulaire et définissez le focus sur la zone de texte que vous avez créée.</span><span class="sxs-lookup"><span data-stu-id="30c1a-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="30c1a-131">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="30c1a-131">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="30c1a-132">Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur entre du texte dans la zone de texte, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="30c1a-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="30c1a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30c1a-133">See Also</span></span>
- [<span data-ttu-id="30c1a-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="30c1a-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="30c1a-135">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="30c1a-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="30c1a-136">Astuce Windows PowerShell de la semaine : création d’une zone d’entrée personnalisée</span><span class="sxs-lookup"><span data-stu-id="30c1a-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)


---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Zones de liste à sélection multiple
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 81708fd5d7204fb7d136e9d8e808303f4d3f4c30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954889"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="591ba-103">Zones de liste à sélection multiple</span><span class="sxs-lookup"><span data-stu-id="591ba-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="591ba-104">Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un contrôle de zone de liste à sélection multiple dans un formulaire Windows Form personnalisé.</span><span class="sxs-lookup"><span data-stu-id="591ba-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="591ba-105">Créer des contrôles de zone de liste autorisant plusieurs sélections</span><span class="sxs-lookup"><span data-stu-id="591ba-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="591ba-106">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="591ba-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="591ba-107">Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="591ba-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="591ba-108">Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form**. Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="591ba-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="591ba-109">Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.</span><span class="sxs-lookup"><span data-stu-id="591ba-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="591ba-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="591ba-110">**Text.**</span></span> <span data-ttu-id="591ba-111">Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="591ba-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="591ba-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="591ba-112">**Size.**</span></span> <span data-ttu-id="591ba-113">Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="591ba-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="591ba-114">Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="591ba-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="591ba-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="591ba-115">**StartingPosition.**</span></span> <span data-ttu-id="591ba-116">Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.</span><span class="sxs-lookup"><span data-stu-id="591ba-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="591ba-117">Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert.</span><span class="sxs-lookup"><span data-stu-id="591ba-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="591ba-118">Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="591ba-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="591ba-119">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="591ba-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="591ba-120">Spécifiez la taille et le comportement du bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="591ba-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="591ba-121">Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="591ba-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="591ba-122">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="591ba-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="591ba-123">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="591ba-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="591ba-124">De la même façon, créez un bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="591ba-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="591ba-125">Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="591ba-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="591ba-126">Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="591ba-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="591ba-127">Ajoutez le contrôle (dans ce cas, une zone de liste) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans votre texte d'étiquette.</span><span class="sxs-lookup"><span data-stu-id="591ba-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="591ba-128">Hormis les zones de texte, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="591ba-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="591ba-129">Voici comment faire pour spécifier que vous autorisez les utilisateurs à sélectionner plusieurs valeurs dans la liste.</span><span class="sxs-lookup"><span data-stu-id="591ba-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="591ba-130">Dans la section suivante, spécifiez les valeurs présentées aux utilisateurs dans la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="591ba-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="591ba-131">Spécifiez la hauteur maximale du contrôle de zone de liste.</span><span class="sxs-lookup"><span data-stu-id="591ba-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="591ba-132">Ajoutez le contrôle de zone de liste à votre formulaire, puis indiquez à Windows d'ouvrir le formulaire au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="591ba-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="591ba-133">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="591ba-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="591ba-134">Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne une ou plusieurs options dans la zone de liste, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="591ba-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="591ba-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="591ba-135">See Also</span></span>

- [<span data-ttu-id="591ba-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="591ba-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="591ba-137">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="591ba-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="591ba-138">Astuce Windows PowerShell de la semaine : Zones de liste à sélection multiple et bien plus encore</span><span class="sxs-lookup"><span data-stu-id="591ba-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](http://technet.microsoft.com/library/ff730950.aspx)
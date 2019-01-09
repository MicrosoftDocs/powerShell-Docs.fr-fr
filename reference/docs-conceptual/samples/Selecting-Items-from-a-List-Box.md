---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Sélection d'éléments dans une zone de liste
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401690"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="6814b-103">Sélection d'éléments dans une zone de liste</span><span class="sxs-lookup"><span data-stu-id="6814b-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="6814b-104">Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer une boîte de dialogue qui permet aux utilisateurs de sélectionner des éléments dans un contrôle de zone de liste.</span><span class="sxs-lookup"><span data-stu-id="6814b-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="6814b-105">Créer un contrôle de zone de liste et sélectionner des éléments dans celui-ci</span><span class="sxs-lookup"><span data-stu-id="6814b-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="6814b-106">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="6814b-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="6814b-107">Le script commence par charger deux classes du .NET Framework : **System.Drawing** et **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="6814b-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="6814b-108">Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form**. Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="6814b-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="6814b-109">Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.</span><span class="sxs-lookup"><span data-stu-id="6814b-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="6814b-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="6814b-110">**Text.**</span></span> <span data-ttu-id="6814b-111">Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6814b-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="6814b-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="6814b-112">**Size.**</span></span> <span data-ttu-id="6814b-113">Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="6814b-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="6814b-114">Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="6814b-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="6814b-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="6814b-115">**StartingPosition.**</span></span> <span data-ttu-id="6814b-116">Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.</span><span class="sxs-lookup"><span data-stu-id="6814b-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="6814b-117">Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert.</span><span class="sxs-lookup"><span data-stu-id="6814b-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="6814b-118">Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="6814b-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="6814b-119">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="6814b-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="6814b-120">Spécifiez la taille et le comportement du bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="6814b-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="6814b-121">Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="6814b-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="6814b-122">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="6814b-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="6814b-123">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="6814b-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="6814b-124">De la même façon, créez un bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="6814b-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="6814b-125">Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="6814b-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="6814b-126">Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6814b-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="6814b-127">Dans ce cas, vous souhaitez que les utilisateurs sélectionnent un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6814b-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="6814b-128">Ajoutez le contrôle (dans ce cas, une zone de liste) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans votre texte d'étiquette.</span><span class="sxs-lookup"><span data-stu-id="6814b-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="6814b-129">Hormis les zones de liste, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="6814b-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="6814b-130">Dans la section suivante, spécifiez les valeurs présentées aux utilisateurs dans la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="6814b-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="6814b-131">La zone de liste créée par ce script n'autorise qu'une seule sélection.</span><span class="sxs-lookup"><span data-stu-id="6814b-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="6814b-132">Pour créer un contrôle de zone de liste autorisant plusieurs sélections, spécifiez une valeur pour la propriété **SelectionMode**, comme suit : `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="6814b-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="6814b-133">Pour plus d’informations, voir [Zones de liste à sélection multiple](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="6814b-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="6814b-134">Ajoutez le contrôle de zone de liste à votre formulaire, puis indiquez à Windows d'ouvrir le formulaire au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6814b-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="6814b-135">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="6814b-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="6814b-136">Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne une option dans la zone de liste, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="6814b-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="6814b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6814b-137">See Also</span></span>

- [<span data-ttu-id="6814b-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="6814b-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="6814b-139">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="6814b-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="6814b-140">Astuce Windows PowerShell de la semaine : sélection d’éléments dans une zone de liste</span><span class="sxs-lookup"><span data-stu-id="6814b-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](https://technet.microsoft.com/library/ff730949.aspx)
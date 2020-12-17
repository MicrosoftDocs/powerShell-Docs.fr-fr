---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Sélection d'éléments dans une zone de liste
description: Cet article explique comment créer un contrôle de zone de liste à l’aide des fonctionnalités de création de formulaires .NET Framework dans Windows PowerShell.
ms.openlocfilehash: d6f881f0b92f294da105ae7df5e25e8c20ce5094
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391236"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="74dc2-104">Sélection d'éléments dans une zone de liste</span><span class="sxs-lookup"><span data-stu-id="74dc2-104">Selecting Items from a List Box</span></span>

<span data-ttu-id="74dc2-105">Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer une boîte de dialogue qui permet aux utilisateurs de sélectionner des éléments dans un contrôle de zone de liste.</span><span class="sxs-lookup"><span data-stu-id="74dc2-105">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="74dc2-106">Créer un contrôle de zone de liste et sélectionner des éléments dans celui-ci</span><span class="sxs-lookup"><span data-stu-id="74dc2-106">Create a list box control, and select items from it</span></span>

<span data-ttu-id="74dc2-107">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="74dc2-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

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

<span data-ttu-id="74dc2-108">Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="74dc2-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="74dc2-109">Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form**. Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="74dc2-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="74dc2-110">Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.</span><span class="sxs-lookup"><span data-stu-id="74dc2-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="74dc2-111">**Text.**</span><span class="sxs-lookup"><span data-stu-id="74dc2-111">**Text.**</span></span> <span data-ttu-id="74dc2-112">Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="74dc2-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="74dc2-113">**Size.**</span><span class="sxs-lookup"><span data-stu-id="74dc2-113">**Size.**</span></span> <span data-ttu-id="74dc2-114">Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="74dc2-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="74dc2-115">Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="74dc2-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="74dc2-116">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="74dc2-116">**StartingPosition.**</span></span> <span data-ttu-id="74dc2-117">Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.</span><span class="sxs-lookup"><span data-stu-id="74dc2-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="74dc2-118">Si vous n’ajoutez pas cette propriété, Windows sélectionne un emplacement lors de l’ouverture du formulaire.</span><span class="sxs-lookup"><span data-stu-id="74dc2-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="74dc2-119">Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affichera automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="74dc2-119">By setting the **StartingPosition** to **CenterScreen**, you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="74dc2-120">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="74dc2-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="74dc2-121">Spécifiez la taille et le comportement du bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="74dc2-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="74dc2-122">Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="74dc2-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="74dc2-123">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="74dc2-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="74dc2-124">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="74dc2-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="74dc2-125">De la même façon, créez un bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="74dc2-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="74dc2-126">Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="74dc2-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="74dc2-127">Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="74dc2-127">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="74dc2-128">Dans ce cas, vous souhaitez que les utilisateurs sélectionnent un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74dc2-128">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="74dc2-129">Ajoutez le contrôle (dans ce cas, une zone de liste) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans le texte de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="74dc2-129">Add the control (in this case, a list box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="74dc2-130">Hormis les zones de liste, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](/dotnet/api/system.windows.forms).</span><span class="sxs-lookup"><span data-stu-id="74dc2-130">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="74dc2-131">Dans la section suivante, spécifiez les valeurs présentées aux utilisateurs dans la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="74dc2-131">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="74dc2-132">La zone de liste créée par ce script n'autorise qu'une seule sélection.</span><span class="sxs-lookup"><span data-stu-id="74dc2-132">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="74dc2-133">Pour créer un contrôle de zone de liste autorisant plusieurs sélections, spécifiez une valeur pour la propriété **SelectionMode**, comme suit : `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="74dc2-133">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following: `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="74dc2-134">Pour plus d’informations, voir [Zones de liste à sélection multiple](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="74dc2-134">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="74dc2-135">Ajoutez le contrôle de zone de liste à votre formulaire, puis indiquez à Windows d’ouvrir le formulaire au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="74dc2-135">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it's opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="74dc2-136">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="74dc2-136">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="74dc2-137">Enfin, le code à l'intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne une option dans la zone de liste, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="74dc2-137">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="74dc2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74dc2-138">See Also</span></span>

- [<span data-ttu-id="74dc2-139">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="74dc2-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="74dc2-140">[Astuce Windows PowerShell de la semaine : Sélection d’éléments dans une zone de liste](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="74dc2-140">[Windows PowerShell Tip of the Week: Selecting Items from a List Box](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span></span>

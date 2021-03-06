---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Zones de liste à sélection multiple
description: Cet article explique comment créer un contrôle de zone de liste multisélection à l’aide des fonctionnalités de création de formulaires .NET Framework dans Windows PowerShell.
ms.openlocfilehash: 2724188695f054d1115b385987cda8a578c102de
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391525"
---
# <a name="multiple-selection-list-boxes"></a>Zones de liste à sélection multiple

Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un contrôle de zone de liste à sélection multiple dans un formulaire Windows Form personnalisé.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Créer des contrôles de zone de liste autorisant plusieurs sélections

Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).

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

Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**. Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form**. Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.

- **Text.** Il s'agit du titre de la fenêtre.

- **Size.** Il s'agit de la taille du formulaire en pixels. Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.

- **StartingPosition.** Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.
  Si vous n’ajoutez pas cette propriété, Windows sélectionne un emplacement lors de l’ouverture du formulaire. Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affichera automatiquement au milieu de l’écran à chaque chargement.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Ensuite, créez un bouton **OK** dans votre formulaire. Spécifiez la taille et le comportement du bouton **OK**. Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche. Le bouton mesure 23 pixels de haut et 75 pixels de long. Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

De la même façon, créez un bouton **Annuler**. Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Ajoutez le contrôle (dans ce cas, une zone de liste) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans votre texte d’étiquette. Hormis les zones de texte, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](/dotnet/api/system.windows.forms).

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Voici comment faire pour spécifier que vous autorisez les utilisateurs à sélectionner plusieurs valeurs dans la liste.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

Dans la section suivante, spécifiez les valeurs présentées aux utilisateurs dans la zone de liste.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

Spécifiez la hauteur maximale du contrôle de zone de liste.

```powershell
$listBox.Height = 70
```

Ajoutez le contrôle de zone de liste à votre formulaire, puis indiquez à Windows d’ouvrir le formulaire au-dessus des autres fenêtres et boîtes de dialogue.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.

```powershell
$result = $form.ShowDialog()
```

Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne une ou plusieurs options dans la zone de liste, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Voir aussi

- [Weekend Scripter: Fixing PowerShell GUI Examples](https://devblogs.microsoft.com/scripting/weekend-scripter-fixing-powershell-gui-examples/)
- [GitHub: Dave Wyatt’s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Astuce Windows PowerShell de la semaine : Zones de liste à sélection multiple et bien plus encore](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10))

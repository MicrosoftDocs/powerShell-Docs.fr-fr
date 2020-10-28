---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Sélection d'éléments dans une zone de liste
description: Cet article explique comment créer un contrôle de zone de liste à l’aide des fonctionnalités de création de formulaires .NET Framework dans Windows PowerShell.
ms.openlocfilehash: cfd6110a9cfcc3cea891d68d8ce7be5b332a949a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501046"
---
# <a name="selecting-items-from-a-list-box"></a>Sélection d'éléments dans une zone de liste

Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer une boîte de dialogue qui permet aux utilisateurs de sélectionner des éléments dans un contrôle de zone de liste.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Créer un contrôle de zone de liste et sélectionner des éléments dans celui-ci

Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).

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

Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms** . Démarrez ensuite une nouvelle instance de la classe .NET Framework **System.Windows.Forms.Form** . Celle-ci affiche une fenêtre ou un formulaire vide où vous pouvez commencer à ajouter des contrôles.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.

- **Text.** Il s'agit du titre de la fenêtre.

- **Size.** Il s'agit de la taille du formulaire en pixels. Le script précédent crée un formulaire de 300 pixels de largeur par 200 pixels de hauteur.

- **StartingPosition.** Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.
  Si vous n’ajoutez pas cette propriété, Windows sélectionne un emplacement lors de l’ouverture du formulaire. Si vous affectez à **StartingPosition** la valeur **CenterScreen** , le formulaire s’affichera automatiquement au milieu de l’écran à chaque chargement.

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Ensuite, créez un bouton **OK** dans votre formulaire. Spécifiez la taille et le comportement du bouton **OK** . Dans cet exemple, le bouton se trouve à 120 pixels du bord supérieur du formulaire et à 75 pixels du bord gauche. Le bouton mesure 23 pixels de haut et 75 pixels de long. Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

De la même façon, créez un bouton **Annuler** . Le bouton **Annuler** se trouve à 120 pixels du bord supérieur de la fenêtre, mais à 150 pixels du bord gauche.

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Ensuite, entrez le texte d'étiquette décrivant les informations que doivent fournir les utilisateurs dans la fenêtre. Dans ce cas, vous souhaitez que les utilisateurs sélectionnent un ordinateur.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Ajoutez le contrôle (dans ce cas, une zone de liste) qui permet aux utilisateurs de fournir les informations que vous avez décrites dans le texte de l’étiquette. Hormis les zones de liste, vous pouvez appliquer de nombreux autres contrôles. Pour plus de contrôles, voir [Espace de noms System.Windows.Forms](/dotnet/api/system.windows.forms) sur MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

Dans la section suivante, spécifiez les valeurs présentées aux utilisateurs dans la zone de liste.

> [!NOTE]
> La zone de liste créée par ce script n'autorise qu'une seule sélection. Pour créer un contrôle de zone de liste autorisant plusieurs sélections, spécifiez une valeur pour la propriété **SelectionMode** , comme suit : `$listBox.SelectionMode = 'MultiExtended'`. Pour plus d’informations, voir [Zones de liste à sélection multiple](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
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

Enfin, le code à l'intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne une option dans la zone de liste, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée** .

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Voir aussi

- [GitHub: Dave Wyatt’s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Astuce Windows PowerShell de la semaine : sélection d’éléments dans une zone de liste](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))

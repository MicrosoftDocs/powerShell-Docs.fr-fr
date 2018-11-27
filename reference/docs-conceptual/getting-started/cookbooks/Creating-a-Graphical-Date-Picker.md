---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d'un sélecteur de dates graphique
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320327"
---
# <a name="creating-a-graphical-date-picker"></a>Création d'un sélecteur de dates graphique

Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un formulaire avec un contrôle graphique de type calendrier qui permet aux utilisateurs de sélectionner un jour du mois.

## <a name="create-a-graphical-date-picker-control"></a>Créer un contrôle sélecteur de dates graphique

Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**. Démarrez ensuite une nouvelle instance de la classe .NET Framework **Windows.Forms.Form**. Celle-ci fournit une fenêtre ou un formulaire vide où vous pouvez ajouter des contrôles.

```powershell
$form = New-Object Windows.Forms.Form
```

Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.

- **Text.** Il s'agit du titre de la fenêtre.

- **Size.** Il s'agit de la taille du formulaire en pixels. Le script précédent crée un formulaire de 243 pixels de largeur par 230 pixels de hauteur.

- **StartingPosition.** Cette propriété facultative a la valeur **CenterScreen** dans le script précédent. Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert. Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Ensuite, créez et ajoutez un contrôle calendrier dans votre formulaire. Dans cet exemple, le jour actuel n'est ni mis en surbrillance ni encerclé. Les utilisateurs peuvent sélectionner un seul jour à la fois dans le calendrier.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Ensuite, créez un bouton **OK** dans votre formulaire. Spécifiez la taille et le comportement du bouton **OK**. Dans cet exemple, le bouton se trouve à 165 pixels du bord supérieur du formulaire et à 38 pixels du bord gauche. Le bouton mesure 23 pixels de haut et 75 pixels de long. Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

De la même façon, créez un bouton **Annuler**. Le bouton **Annuler** se trouve à 165 pixels du bord supérieur de la fenêtre, mais à 113 pixels du bord gauche.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Affectez à la propriété **Topmost** la valeur **$true** pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.

```powershell
$form.Topmost = $true
```

Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.

```powershell
$result = $form.ShowDialog()
```

Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne un jour dans le calendrier, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**. Windows PowerShell affiche la date sélectionnée aux utilisateurs.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Voir aussi

- [Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt’s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Astuce Windows PowerShell de la semaine : création d’un sélecteur de dates graphique](https://technet.microsoft.com/library/ff730942.aspx)
---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d'un sélecteur de dates graphique
ms.openlocfilehash: d05445963b41af61a61aa29a425e638d43fb5d9d
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030250"
---
# <a name="creating-a-graphical-date-picker"></a>Création d'un sélecteur de dates graphique

Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un formulaire avec un contrôle graphique de type calendrier qui permet aux utilisateurs de sélectionner un jour du mois.

## <a name="create-a-graphical-date-picker-control"></a>Créer un contrôle sélecteur de dates graphique

Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**.
Démarrez ensuite une nouvelle instance de la classe .NET Framework **Windows.Forms.Form**. Celle-ci fournit une fenêtre ou un formulaire vide où vous pouvez ajouter des contrôles.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

Cet exemple assigne des valeurs à quatre propriétés de cette classe à l’aide de la propriété **Property** et de la table de hachage.

1. **StartPosition** : Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert.
   Si vous affectez à cette propriété la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.

2. **Size** : Il s'agit de la taille du formulaire en pixels.
   Le script précédent crée un formulaire de 243 pixels de largeur par 230 pixels de hauteur.

3. **Text** : Il s'agit du titre de la fenêtre.

4. **Topmost** : Affectez à cette propriété la valeur `$true` pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.

Ensuite, créez et ajoutez un contrôle calendrier dans votre formulaire.
Dans cet exemple, le jour actuel n'est ni mis en surbrillance ni encerclé.
Les utilisateurs peuvent sélectionner un seul jour à la fois dans le calendrier.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Ensuite, créez un bouton **OK** dans votre formulaire.
Spécifiez la taille et le comportement du bouton **OK**.
Dans cet exemple, le bouton se trouve à 165 pixels du bord supérieur du formulaire et à 38 pixels du bord gauche.
Le bouton mesure 23 pixels de haut et 75 pixels de long.
Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

De la même façon, créez un bouton **Annuler**.
Le bouton **Annuler** se trouve à 165 pixels du bord supérieur de la fenêtre, mais à 113 pixels du bord gauche.

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.

```powershell
$result = $form.ShowDialog()
```

Enfin, le code à l’intérieur du bloc `if` indique à Windows comment traiter le formulaire quand un utilisateur sélectionne un jour dans le calendrier, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.
Windows PowerShell affiche la date sélectionnée aux utilisateurs.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Voir aussi

- [Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub : WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Astuce Windows PowerShell de la semaine :  Créer un sélecteur de dates graphique](https://technet.microsoft.com/library/ff730942.aspx)

---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d'un sélecteur de dates graphique
description: Cet article explique comment créer un contrôle personnalisé de style calendrier à l’aide des fonctionnalités de création de formulaires .NET Framework dans Windows PowerShell.
ms.openlocfilehash: b73c9ba78817af7c38c20642402752765a7a3674
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500502"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="dd05a-104">Création d'un sélecteur de dates graphique</span><span class="sxs-lookup"><span data-stu-id="dd05a-104">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="dd05a-105">Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un formulaire avec un contrôle graphique de type calendrier qui permet aux utilisateurs de sélectionner un jour du mois.</span><span class="sxs-lookup"><span data-stu-id="dd05a-105">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="dd05a-106">Créer un contrôle sélecteur de dates graphique</span><span class="sxs-lookup"><span data-stu-id="dd05a-106">Create a graphical date-picker control</span></span>

<span data-ttu-id="dd05a-107">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="dd05a-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="dd05a-108">Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms** .</span><span class="sxs-lookup"><span data-stu-id="dd05a-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms** .</span></span> <span data-ttu-id="dd05a-109">Démarrez ensuite une nouvelle instance de la classe .NET Framework **Windows.Forms.Form** . Celle-ci fournit une fenêtre ou un formulaire vide dans lequel vous pouvez ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="dd05a-109">You then start a new instance of the .NET Framework class **Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="dd05a-110">Cet exemple assigne des valeurs à quatre propriétés de cette classe à l’aide de la propriété **Property** et de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="dd05a-110">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="dd05a-111">**StartPosition** : Si vous n’ajoutez pas cette propriété, Windows sélectionne un emplacement lors de l’ouverture du formulaire.</span><span class="sxs-lookup"><span data-stu-id="dd05a-111">**StartPosition** : If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="dd05a-112">Si vous affectez à cette propriété la valeur **CenterScreen** , le formulaire s’affichera automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="dd05a-112">By setting this property to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="dd05a-113">**Size** : Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="dd05a-113">**Size** : This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="dd05a-114">Le script précédent crée un formulaire de 243 pixels de largeur par 230 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="dd05a-114">The preceding script creates a form that's 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="dd05a-115">**Text** : Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="dd05a-115">**Text** : This becomes the title of the window.</span></span>

4. <span data-ttu-id="dd05a-116">**Topmost** : Affectez à cette propriété la valeur `$true` pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="dd05a-116">**Topmost** : By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="dd05a-117">Ensuite, créez et ajoutez un contrôle calendrier dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="dd05a-117">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="dd05a-118">Dans cet exemple, le jour actuel n'est ni mis en surbrillance ni encerclé.</span><span class="sxs-lookup"><span data-stu-id="dd05a-118">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="dd05a-119">Les utilisateurs peuvent sélectionner un seul jour à la fois dans le calendrier.</span><span class="sxs-lookup"><span data-stu-id="dd05a-119">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="dd05a-120">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="dd05a-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="dd05a-121">Spécifiez la taille et le comportement du bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="dd05a-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="dd05a-122">Dans cet exemple, le bouton se trouve à 165 pixels du bord supérieur du formulaire et à 38 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="dd05a-122">In this example, the button position is 165 pixels from the form's top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="dd05a-123">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="dd05a-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="dd05a-124">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="dd05a-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="dd05a-125">De la même façon, créez un bouton **Annuler** .</span><span class="sxs-lookup"><span data-stu-id="dd05a-125">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="dd05a-126">Le bouton **Cancel** se trouve à 165 pixels du bord supérieur de la fenêtre, mais à 113 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="dd05a-126">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="dd05a-127">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="dd05a-127">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="dd05a-128">Enfin, le code à l’intérieur du bloc `if` indique à Windows comment traiter le formulaire quand un utilisateur sélectionne un jour dans le calendrier, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée** .</span><span class="sxs-lookup"><span data-stu-id="dd05a-128">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="dd05a-129">Windows PowerShell affiche la date sélectionnée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dd05a-129">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="dd05a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd05a-130">See Also</span></span>

- [<span data-ttu-id="dd05a-131">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="dd05a-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="dd05a-132">[Astuce Windows PowerShell de la semaine : création d’un sélecteur de dates graphique](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="dd05a-132">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span></span>

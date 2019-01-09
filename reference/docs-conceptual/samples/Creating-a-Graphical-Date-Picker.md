---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d'un sélecteur de dates graphique
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401149"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="6cda6-103">Création d'un sélecteur de dates graphique</span><span class="sxs-lookup"><span data-stu-id="6cda6-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="6cda6-104">Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un formulaire avec un contrôle graphique de type calendrier qui permet aux utilisateurs de sélectionner un jour du mois.</span><span class="sxs-lookup"><span data-stu-id="6cda6-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="6cda6-105">Créer un contrôle sélecteur de dates graphique</span><span class="sxs-lookup"><span data-stu-id="6cda6-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="6cda6-106">Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="6cda6-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="6cda6-107">Le script commence par charger deux classes du .NET Framework : **System.Drawing** et **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="6cda6-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="6cda6-108">Démarrez ensuite une nouvelle instance de la classe .NET Framework **Windows.Forms.Form**. Celle-ci fournit une fenêtre ou un formulaire vide où vous pouvez ajouter des contrôles.</span><span class="sxs-lookup"><span data-stu-id="6cda6-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="6cda6-109">Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.</span><span class="sxs-lookup"><span data-stu-id="6cda6-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="6cda6-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="6cda6-110">**Text.**</span></span> <span data-ttu-id="6cda6-111">Il s'agit du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6cda6-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="6cda6-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="6cda6-112">**Size.**</span></span> <span data-ttu-id="6cda6-113">Il s'agit de la taille du formulaire en pixels.</span><span class="sxs-lookup"><span data-stu-id="6cda6-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="6cda6-114">Le script précédent crée un formulaire de 243 pixels de largeur par 230 pixels de hauteur.</span><span class="sxs-lookup"><span data-stu-id="6cda6-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="6cda6-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="6cda6-115">**StartingPosition.**</span></span> <span data-ttu-id="6cda6-116">Cette propriété facultative a la valeur **CenterScreen** dans le script précédent.</span><span class="sxs-lookup"><span data-stu-id="6cda6-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="6cda6-117">Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert.</span><span class="sxs-lookup"><span data-stu-id="6cda6-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="6cda6-118">Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.</span><span class="sxs-lookup"><span data-stu-id="6cda6-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="6cda6-119">Ensuite, créez et ajoutez un contrôle calendrier dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="6cda6-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="6cda6-120">Dans cet exemple, le jour actuel n'est ni mis en surbrillance ni encerclé.</span><span class="sxs-lookup"><span data-stu-id="6cda6-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="6cda6-121">Les utilisateurs peuvent sélectionner un seul jour à la fois dans le calendrier.</span><span class="sxs-lookup"><span data-stu-id="6cda6-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="6cda6-122">Ensuite, créez un bouton **OK** dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="6cda6-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="6cda6-123">Spécifiez la taille et le comportement du bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="6cda6-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="6cda6-124">Dans cet exemple, le bouton se trouve à 165 pixels du bord supérieur du formulaire et à 38 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="6cda6-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="6cda6-125">Le bouton mesure 23 pixels de haut et 75 pixels de long.</span><span class="sxs-lookup"><span data-stu-id="6cda6-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="6cda6-126">Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.</span><span class="sxs-lookup"><span data-stu-id="6cda6-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="6cda6-127">De la même façon, créez un bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="6cda6-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="6cda6-128">Le bouton **Annuler** se trouve à 165 pixels du bord supérieur de la fenêtre, mais à 113 pixels du bord gauche.</span><span class="sxs-lookup"><span data-stu-id="6cda6-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="6cda6-129">Affectez à la propriété **Topmost** la valeur **$true** pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6cda6-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="6cda6-130">Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.</span><span class="sxs-lookup"><span data-stu-id="6cda6-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="6cda6-131">Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne un jour dans le calendrier, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="6cda6-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="6cda6-132">Windows PowerShell affiche la date sélectionnée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6cda6-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="6cda6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cda6-133">See Also</span></span>

- [<span data-ttu-id="6cda6-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="6cda6-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="6cda6-135">GitHub: Dave Wyatt’s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="6cda6-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="6cda6-136">Astuce Windows PowerShell de la semaine : création d’un sélecteur de dates graphique</span><span class="sxs-lookup"><span data-stu-id="6cda6-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)
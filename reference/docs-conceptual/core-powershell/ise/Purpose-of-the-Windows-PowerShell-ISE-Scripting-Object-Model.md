---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Objectif du modèle objet de script Windows PowerShell ISE"
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="63a60-103">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="63a60-104">Les objets sont associés aux forme et fonction de Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="63a60-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="63a60-105">La référence du modèle objet fournit des détails sur les propriétés et méthodes membres exposées par ces objets.</span><span class="sxs-lookup"><span data-stu-id="63a60-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="63a60-106">Des exemples sont fournis pour montrer comment vous pouvez utiliser des scripts pour accéder directement à ces méthodes et propriétés.</span><span class="sxs-lookup"><span data-stu-id="63a60-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="63a60-107">Le modèle objet de script facilite l’éventail des tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="63a60-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="63a60-108">Personnalisation de l’apparence de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="63a60-109">Vous pouvez utiliser le modèle objet pour modifier les options et paramètres de l’application.</span><span class="sxs-lookup"><span data-stu-id="63a60-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="63a60-110">Vous pouvez, par exemple, les modifier comme suit :</span><span class="sxs-lookup"><span data-stu-id="63a60-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="63a60-111">Vous pouvez modifier la couleur des erreurs, des avertissements, des sorties détaillées et des sorties de débogage.</span><span class="sxs-lookup"><span data-stu-id="63a60-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="63a60-112">Vous pouvez obtenir ou définir les couleurs d’arrière-plan pour les volets Commande, Sortie et Script.</span><span class="sxs-lookup"><span data-stu-id="63a60-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="63a60-113">Vous pouvez définir la couleur de premier plan du volet Sortie.</span><span class="sxs-lookup"><span data-stu-id="63a60-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="63a60-114">Vous pouvez définir le nom et la taille de la police pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63a60-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="63a60-115">Vous pouvez configurer des avertissements,</span><span class="sxs-lookup"><span data-stu-id="63a60-115">You can configure warnings.</span></span> <span data-ttu-id="63a60-116">notamment les avertissements émis quand un fichier est ouvert dans plusieurs onglets PowerShell ou qu’un script dans le fichier s’exécute avant que celui-ci n’ait été enregistré.</span><span class="sxs-lookup"><span data-stu-id="63a60-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="63a60-117">Vous pouvez basculer entre une vue où le volet Script et le volet Sortie sont côte à côte et une vue où le volet Script est au-dessus du volet Sortie.</span><span class="sxs-lookup"><span data-stu-id="63a60-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="63a60-118">Vous pouvez ancrer le volet Commande en bas ou en haut du volet Sortie.</span><span class="sxs-lookup"><span data-stu-id="63a60-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="63a60-119">Amélioration des fonctionnalités de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="63a60-120">Vous pouvez utiliser le modèle objet pour améliorer les fonctionnalités de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63a60-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="63a60-121">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="63a60-121">For example, you can:</span></span>

- <span data-ttu-id="63a60-122">Ajouter et modifier l’instance de Windows PowerShell ISE lui-même.</span><span class="sxs-lookup"><span data-stu-id="63a60-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="63a60-123">Par exemple, pour modifier les menus, vous pouvez ajouter de nouveaux éléments de menu et mapper les nouveaux éléments de menu à des scripts.</span><span class="sxs-lookup"><span data-stu-id="63a60-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="63a60-124">Créer des scripts qui effectuent certaines des tâches que vous pouvez effectuer à l’aide des commandes de menu et des boutons disponibles dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63a60-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="63a60-125">Par exemple, vous pouvez ajouter, supprimer ou sélectionner un onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63a60-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="63a60-126">Effectuer des tâches réalisables à l’aide des boutons et des commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="63a60-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="63a60-127">Par exemple, vous pouvez renommer un onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63a60-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="63a60-128">Manipuler des tampons de texte pour les volets Commande, Sortie et Script associés à un fichier.</span><span class="sxs-lookup"><span data-stu-id="63a60-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="63a60-129">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="63a60-129">For example, you can:</span></span>

    -   <span data-ttu-id="63a60-130">Obtenir ou définir tout le texte.</span><span class="sxs-lookup"><span data-stu-id="63a60-130">Get or set all text.</span></span>

    -   <span data-ttu-id="63a60-131">Obtenir ou définir une sélection de texte.</span><span class="sxs-lookup"><span data-stu-id="63a60-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="63a60-132">Exécuter un script ou une partie sélectionnée d’un script.</span><span class="sxs-lookup"><span data-stu-id="63a60-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="63a60-133">Faire défiler l’affichage jusqu’à une ligne spécifique.</span><span class="sxs-lookup"><span data-stu-id="63a60-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="63a60-134">Insérer du texte à l’emplacement du signe d’insertion.</span><span class="sxs-lookup"><span data-stu-id="63a60-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="63a60-135">Sélectionner un bloc de texte.</span><span class="sxs-lookup"><span data-stu-id="63a60-135">Select a block of text.</span></span>

    -   <span data-ttu-id="63a60-136">Obtenir le numéro de la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="63a60-136">Get the last line number.</span></span>

- <span data-ttu-id="63a60-137">Effectuer des opérations de fichier.</span><span class="sxs-lookup"><span data-stu-id="63a60-137">Perform file operations.</span></span> <span data-ttu-id="63a60-138">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="63a60-138">For example, you can:</span></span>

    -   <span data-ttu-id="63a60-139">Ouvrir un fichier, enregistrer un fichier ou enregistrer un fichier sous un nom différent.</span><span class="sxs-lookup"><span data-stu-id="63a60-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="63a60-140">Déterminer si un fichier a été modifié depuis son dernier enregistrement.</span><span class="sxs-lookup"><span data-stu-id="63a60-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="63a60-141">Obtenir le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="63a60-141">Get the file name.</span></span>

    -   <span data-ttu-id="63a60-142">Sélectionner un fichier.</span><span class="sxs-lookup"><span data-stu-id="63a60-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="63a60-143">Automatisation des tâches</span><span class="sxs-lookup"><span data-stu-id="63a60-143">Automating tasks</span></span>
 <span data-ttu-id="63a60-144">Vous pouvez utiliser le modèle objet de script pour créer des raccourcis clavier pour les opérations fréquentes.</span><span class="sxs-lookup"><span data-stu-id="63a60-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="63a60-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63a60-145">See Also</span></span>
- [<span data-ttu-id="63a60-146">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="63a60-147">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="63a60-148">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63a60-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  

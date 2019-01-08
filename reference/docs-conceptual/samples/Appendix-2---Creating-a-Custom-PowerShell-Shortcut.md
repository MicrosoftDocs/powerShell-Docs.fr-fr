---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 2 : création d’un raccourci PowerShell personnalisé'
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402016"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="7c7d6-103">Annexe 2 : création d’un raccourci PowerShell personnalisé</span><span class="sxs-lookup"><span data-stu-id="7c7d6-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="7c7d6-104">La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="7c7d6-105">Créez un raccourci qui pointe vers Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="7c7d6-106">Cliquez avec le bouton droit sur le raccourci, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="7c7d6-107">Cliquez sur l’onglet **Options**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="7c7d6-108">Dans la section **Modifier les options**, activez la case à cocher **QuickEdit**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="7c7d6-109">Ce paramètre permet de sélectionner du texte dans la fenêtre de console Windows PowerShell en faisant glisser tout en appuyant sur le bouton gauche de la souris, et permet de copier du texte dans le Presse-papiers en appuyant sur Entrée ou en cliquant avec le bouton droit.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="7c7d6-110">Dans la section **Modifier les options**, activez la case à cocher **Mode insertion**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="7c7d6-111">Ce paramètre permet de cliquer avec le bouton droit dans la fenêtre de console pour coller automatiquement du texte à partir du Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="7c7d6-112">Dans la section **Historique des commandes**, dans le champ **Taille de la mémoire tampon**, tapez ou sélectionnez un nombre compris entre 1 et 999.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="7c7d6-113">Cela a pour effet de définir le nombre de commandes saisies qui sont conservées dans la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="7c7d6-114">Dans la section **Historique des commandes**, activez la case à cocher **Supprimer les doublons** pour éliminer les commandes répétées de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="7c7d6-115">Cliquez sur l’onglet **Disposition**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="7c7d6-116">Dans la section **Mémoire tampon d’écran**, dans le champ **Hauteur**, tapez un nombre compris entre 1 et 9999.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="7c7d6-117">La hauteur représente le nombre de lignes de sortie qui sont mises en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="7c7d6-118">Il s’agit du nombre maximal de lignes conservées pour affichage lorsque vous faites défiler la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="7c7d6-119">Si ce nombre est inférieur à la hauteur affichée dans la section **Taille de la fenêtre**, la hauteur de la fenêtre est automatiquement réduite la même valeur.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="7c7d6-120">Dans la section **Taille de la fenêtre**, tapez un nombre compris entre 1 et 9999 pour la largeur.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="7c7d6-121">Ce nombre représente le nombre de caractères qui s’affichent dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="7c7d6-122">La largeur par défaut est 80, et la mise en forme de la sortie de Windows PowerShell est conçue pour cette largeur.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="7c7d6-123">Si vous souhaitez placer la console à un endroit particulier sur le Bureau quand elle est ouverte, désactivez la case à cocher **Positionnée par le système** dans la section **Position de la fenêtre**, puis modifiez les valeurs des champs **Gauche** et **Haut** dans la section **Position de la fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="7c7d6-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-124">Click **OK**.</span></span>
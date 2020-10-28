---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 2 : création d’un raccourci PowerShell personnalisé'
description: La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.
ms.openlocfilehash: abdab517dec1357050bf431b6f2e35311ad49976
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500723"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="40197-104">Annexe 2 : création d’un raccourci PowerShell personnalisé</span><span class="sxs-lookup"><span data-stu-id="40197-104">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="40197-105">La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.</span><span class="sxs-lookup"><span data-stu-id="40197-105">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="40197-106">Créez un raccourci qui pointe vers Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="40197-106">Create a shortcut that points to Powershell.exe.</span></span>

1. <span data-ttu-id="40197-107">Cliquez avec le bouton droit sur le raccourci, puis cliquez sur **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="40197-107">Right-click the shortcut, and then click **Properties** .</span></span>

1. <span data-ttu-id="40197-108">Cliquez sur l’onglet **Options** .</span><span class="sxs-lookup"><span data-stu-id="40197-108">Click the **Options** tab.</span></span>

1. <span data-ttu-id="40197-109">Dans la section **Modifier les options** , activez la case à cocher **QuickEdit** .</span><span class="sxs-lookup"><span data-stu-id="40197-109">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="40197-110">Ce paramètre permet de sélectionner du texte dans la fenêtre de console Windows PowerShell en appuyant sur le bouton gauche de la souris tout en la faisant glisser, et permet de copier du texte dans le Presse-papiers en appuyant sur Entrée ou en cliquant avec le bouton droit.</span><span class="sxs-lookup"><span data-stu-id="40197-110">This setting lets you select text in the Windows PowerShell console window by dragging the left  mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking  the mouse.</span></span>

1. <span data-ttu-id="40197-111">Dans la section **Modifier les options** , activez la case à cocher **Mode insertion** .</span><span class="sxs-lookup"><span data-stu-id="40197-111">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="40197-112">Ce paramètre permet de cliquer avec le bouton droit dans la fenêtre de console pour coller automatiquement du texte à partir du Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="40197-112">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

1. <span data-ttu-id="40197-113">Dans la section **Historique des commandes** , dans le champ **Taille de la mémoire tampon** , tapez ou sélectionnez un nombre compris entre 1 et 999.</span><span class="sxs-lookup"><span data-stu-id="40197-113">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="40197-114">Cela a pour effet de définir le nombre de commandes saisies qui sont conservées dans la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="40197-114">This sets the number of typed commands that will be kept in the console buffer.</span></span>

1. <span data-ttu-id="40197-115">Dans la section **Historique des commandes** , activez la case à cocher **Supprimer les doublons** pour éliminer les commandes répétées de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="40197-115">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

1. <span data-ttu-id="40197-116">Cliquez sur l’onglet **Disposition** .</span><span class="sxs-lookup"><span data-stu-id="40197-116">Click the **Layout** tab.</span></span>

1. <span data-ttu-id="40197-117">Dans la section **Mémoire tampon d’écran** , dans le champ **Hauteur** , tapez un nombre compris entre 1 et 9999.</span><span class="sxs-lookup"><span data-stu-id="40197-117">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="40197-118">La hauteur représente le nombre de lignes de sortie qui sont mises en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="40197-118">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="40197-119">Il s’agit du nombre maximal de lignes conservées pour affichage lorsque vous faites défiler la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="40197-119">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="40197-120">Si ce nombre est inférieur à la hauteur affichée dans la section **Taille de la fenêtre** , la hauteur de la fenêtre est automatiquement réduite la même valeur.</span><span class="sxs-lookup"><span data-stu-id="40197-120">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

1. <span data-ttu-id="40197-121">Dans la section **Taille de la fenêtre** , tapez un nombre compris entre 1 et 9999 pour la largeur.</span><span class="sxs-lookup"><span data-stu-id="40197-121">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="40197-122">Ce nombre représente le nombre de caractères qui s’affichent dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="40197-122">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="40197-123">La largeur par défaut est 80, et la mise en forme de la sortie de Windows PowerShell est conçue pour cette largeur.</span><span class="sxs-lookup"><span data-stu-id="40197-123">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

1. <span data-ttu-id="40197-124">Si vous souhaitez placer la console à un endroit particulier sur le Bureau quand elle est ouverte, décochez la case **Positionnée par le système** dans la section **Position de la fenêtre** , puis modifiez les valeurs des champs **Gauche** et **Haut** dans la section **Position de la fenêtre** .</span><span class="sxs-lookup"><span data-stu-id="40197-124">If you want to place the console at a particular point on the desktop when it is opened, clear  the **Let system position window** check box in the **Window position** section, and then change  the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

1. <span data-ttu-id="40197-125">Cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="40197-125">Click **OK** .</span></span>

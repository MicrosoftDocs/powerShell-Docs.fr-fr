---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment créer un onglet PowerShell dans Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030587"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="c0585-103">Comment créer un onglet PowerShell dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c0585-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="c0585-104">Les onglets de l’environnement d’écriture de scripts intégré de Windows PowerShell permettent de créer et d’utiliser simultanément plusieurs environnements d’exécution au sein de la même application.</span><span class="sxs-lookup"><span data-stu-id="c0585-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="c0585-105">Chaque onglet PowerShell correspond à un environnement d’exécution ou à une session distincts.</span><span class="sxs-lookup"><span data-stu-id="c0585-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="c0585-106">Les variables, fonctions et alias que vous créez sous un onglet ne s’appliquent pas à un autre.</span><span class="sxs-lookup"><span data-stu-id="c0585-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="c0585-107">Il s’agit de sessions Windows PowerShell différentes.</span><span class="sxs-lookup"><span data-stu-id="c0585-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="c0585-108">Pour ouvrir ou fermer un onglet dans Windows PowerShell, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="c0585-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="c0585-109">Pour renommer un onglet, définissez la propriété [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) sur l’objet de script Onglet Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0585-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="c0585-110">Pour créer et utiliser un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0585-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="c0585-111">Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell**. Le nouvel onglet PowerShell s’ouvre toujours comme la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="c0585-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="c0585-112">Les onglets PowerShell sont numérotés de façon incrémentielle dans l’ordre de leur ouverture.</span><span class="sxs-lookup"><span data-stu-id="c0585-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="c0585-113">Chaque onglet est associé à sa propre fenêtre de console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0585-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="c0585-114">Vous pouvez avoir jusqu’à 32 onglets PowerShell avec leur propre session ouverte simultanément (ce nombre est limité à 8 sur Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="c0585-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="c0585-115">Notez qu’un clic sur l’icône **Nouveau** ou **Ouvrir** dans la barre d’outils ne crée pas d’onglet avec une session distincte.</span><span class="sxs-lookup"><span data-stu-id="c0585-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="c0585-116">Au lieu de cela, ces boutons ouvrent un fichier de script nouveau ou existant sur l’onglet actif avec une session.</span><span class="sxs-lookup"><span data-stu-id="c0585-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="c0585-117">Vous pouvez avoir plusieurs fichiers script ouverts avec chaque onglet et session.</span><span class="sxs-lookup"><span data-stu-id="c0585-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="c0585-118">Les onglets de script pour une session s’affichent sous les onglets de la session uniquement lorsque la session associée est active.</span><span class="sxs-lookup"><span data-stu-id="c0585-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="c0585-119">Pour activer un onglet PowerShell, cliquez dessus. Pour opérer une sélection parmi tous les onglets PowerShell ouverts, dans le menu **Affichage**, cliquez sur l’onglet PowerShell que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="c0585-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="c0585-120">Pour créer et utiliser un onglet PowerShell à distance</span><span class="sxs-lookup"><span data-stu-id="c0585-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="c0585-121">Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell à distance** pour établir une session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c0585-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="c0585-122">Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="c0585-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="c0585-123">L’onglet à distance fonctionne exactement comme un onglet PowerShell local, mais les commandes et les scripts sont exécutés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c0585-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="c0585-124">Pour fermer un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0585-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="c0585-125">Pour fermer un onglet, vous pouvez utiliser l’une des techniques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0585-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="c0585-126">Cliquez sur l’onglet que vous souhaitez fermer.</span><span class="sxs-lookup"><span data-stu-id="c0585-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="c0585-127">Dans le menu **Fichier**, cliquez sur **Fermer l’onglet PowerShell** ou sur le bouton Fermer (**X**) d’un onglet actif pour fermer celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c0585-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="c0585-128">Si des fichiers non enregistrés sont ouverts dans l’onglet PowerShell que vous fermez, vous êtes invité à les enregistrer ou les ignorer.</span><span class="sxs-lookup"><span data-stu-id="c0585-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="c0585-129">Pour plus d’informations sur l’enregistrement d’un script, voir [Comment enregistrer un script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="c0585-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0585-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0585-130">See Also</span></span>

- [<span data-ttu-id="c0585-131">Présentation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c0585-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="c0585-132">Comment utiliser le volet Console dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c0585-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

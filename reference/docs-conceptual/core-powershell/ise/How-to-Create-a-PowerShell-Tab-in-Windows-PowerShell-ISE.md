---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Comment créer un onglet PowerShell dans Windows PowerShell ISE"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="7df3a-103">Comment créer un onglet PowerShell dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7df3a-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="7df3a-104">Les onglets de l’environnement d’écriture de scripts intégré de Windows PowerShell permettent de créer et d’utiliser simultanément plusieurs environnements d’exécution au sein de la même application.</span><span class="sxs-lookup"><span data-stu-id="7df3a-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="7df3a-105">Chaque onglet PowerShell correspond à un environnement d’exécution ou à une session distincts.</span><span class="sxs-lookup"><span data-stu-id="7df3a-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="7df3a-106">**REMARQUE** :</span><span class="sxs-lookup"><span data-stu-id="7df3a-106">**NOTE**:</span></span>
>
> <span data-ttu-id="7df3a-107">Les variables, fonctions et alias que vous créez sous un onglet ne s’appliquent pas à un autre.</span><span class="sxs-lookup"><span data-stu-id="7df3a-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="7df3a-108">Il s’agit de sessions Windows PowerShell différentes.</span><span class="sxs-lookup"><span data-stu-id="7df3a-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="7df3a-109">Pour ouvrir ou fermer un onglet dans Windows PowerShell, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="7df3a-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="7df3a-110">Pour renommer un onglet, définissez la propriété [DisplayName](The-PowerShellTab-Object.md#displayname) sur l’objet de script Onglet Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7df3a-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="7df3a-111">Pour créer et utiliser un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="7df3a-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="7df3a-112">Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell**. Le nouvel onglet PowerShell s’ouvre toujours comme la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="7df3a-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="7df3a-113">Les onglets PowerShell sont numérotés de façon incrémentielle dans l’ordre de leur ouverture.</span><span class="sxs-lookup"><span data-stu-id="7df3a-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="7df3a-114">Chaque onglet est associé à sa propre fenêtre de console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7df3a-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="7df3a-115">Vous pouvez avoir jusqu’à 32 onglets PowerShell avec leur propre session ouverte simultanément (ce nombre est limité à 8 sur Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="7df3a-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="7df3a-116">Notez qu’un clic sur l’icône **Nouveau** ou **Ouvrir** dans la barre d’outils ne crée pas d’onglet avec une session distincte.</span><span class="sxs-lookup"><span data-stu-id="7df3a-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="7df3a-117">Au lieu de cela, ces boutons ouvrent un fichier de script nouveau ou existant sur l’onglet actif avec une session.</span><span class="sxs-lookup"><span data-stu-id="7df3a-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="7df3a-118">Vous pouvez avoir plusieurs fichiers script ouverts avec chaque onglet et session.</span><span class="sxs-lookup"><span data-stu-id="7df3a-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="7df3a-119">Les onglets de script pour une session s’affichent sous les onglets de la session uniquement lorsque la session associée est active.</span><span class="sxs-lookup"><span data-stu-id="7df3a-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="7df3a-120">Pour activer un onglet PowerShell, cliquez dessus. Pour opérer une sélection parmi tous les onglets PowerShell ouverts, dans le menu **Affichage**, cliquez sur l’onglet PowerShell que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="7df3a-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="7df3a-121">Pour créer et utiliser un onglet PowerShell à distance</span><span class="sxs-lookup"><span data-stu-id="7df3a-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="7df3a-122">Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell à distance** pour établir une session sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7df3a-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="7df3a-123">Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="7df3a-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="7df3a-124">L’onglet à distance fonctionne exactement comme un onglet PowerShell local, mais les commandes et les scripts sont exécutés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7df3a-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="7df3a-125">Pour fermer un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="7df3a-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="7df3a-126">Pour fermer un onglet, vous pouvez utiliser l’une des techniques suivantes :</span><span class="sxs-lookup"><span data-stu-id="7df3a-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="7df3a-127">Cliquez sur l’onglet que vous souhaitez fermer.</span><span class="sxs-lookup"><span data-stu-id="7df3a-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="7df3a-128">Dans le menu **Fichier**, cliquez sur **Fermer l’onglet PowerShell** ou sur le bouton Fermer (**X**) d’un onglet actif pour fermer celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7df3a-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="7df3a-129">Si des fichiers non enregistrés sont ouverts dans l’onglet PowerShell que vous fermez, vous êtes invité à les enregistrer ou les ignorer.</span><span class="sxs-lookup"><span data-stu-id="7df3a-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="7df3a-130">Pour plus d’informations sur l’enregistrement d’un script, voir [Comment enregistrer un script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="7df3a-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="7df3a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7df3a-131">See Also</span></span>

- [<span data-ttu-id="7df3a-132">Utilisation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7df3a-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="7df3a-133">Comment utiliser le volet Console dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7df3a-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)


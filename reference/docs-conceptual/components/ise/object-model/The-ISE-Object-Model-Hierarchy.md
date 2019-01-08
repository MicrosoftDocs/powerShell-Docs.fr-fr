---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Hiérarchie du modèle objet ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401863"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="b6b4d-103">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="b6b4d-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="b6b4d-104">Cette rubrique présente la hiérarchie des objets qui font partie de l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="b6b4d-105">Windows PowerShell ISE est inclus dans Windows PowerShell 3.0 et Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="b6b4d-106">Cliquez sur un objet pour accéder à la documentation de référence de la classe qui définit l’objet.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="b6b4d-107">Objet $psISE</span><span class="sxs-lookup"><span data-stu-id="b6b4d-107">$psISE Object</span></span>

<span data-ttu-id="b6b4d-108">L’objet **$psISE** est l’[objet racine](The-ObjectModelRoot-Object.md) de la hiérarchie d’objets Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="b6b4d-109">Cet objet de premier niveau fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="b6b4d-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="b6b4d-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="b6b4d-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="b6b4d-111">L’objet **$psISE.CurrentFile** est une instance de la classe [ISEFile](The-ISEFile-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="b6b4d-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="b6b4d-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="b6b4d-113">L’objet **$psISE.CurrentPowerShellTab** est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="b6b4d-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="b6b4d-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="b6b4d-115">L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="b6b4d-116">Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord supérieur de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="b6b4d-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="b6b4d-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="b6b4d-118">L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="b6b4d-119">Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord droit de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="b6b4d-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="b6b4d-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="b6b4d-121">L’objet **$psISE.Options** est une instance de la classe [ISEOptions](The-ISEOptions-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="b6b4d-122">L’objet ISEOptions représente différents paramètres pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="b6b4d-123">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="b6b4d-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="b6b4d-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="b6b4d-125">L’objet **$psISE.PowerShellTabs** est une instance de la classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="b6b4d-126">Cet objet est une collection de tous les onglets PowerShell ouverts qui représentent les environnements d’exécution Windows PowerShell disponibles sur l’ordinateur local ou sur les ordinateurs distants connectés.</span><span class="sxs-lookup"><span data-stu-id="b6b4d-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="b6b4d-127">Chaque membre de la collection est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4d-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6b4d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6b4d-128">See Also</span></span>

- [<span data-ttu-id="b6b4d-129">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b6b4d-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b6b4d-130">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="b6b4d-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
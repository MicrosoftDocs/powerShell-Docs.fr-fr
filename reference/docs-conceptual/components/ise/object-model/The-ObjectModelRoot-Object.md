---
ms.date: 08/25/2017
keywords: powershell,applet de commande
title: Objet ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402066"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="36254-103">Objet ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="36254-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="36254-104">L’objet **$psISE**, qui est l’objet racine principal dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell® est une instance de la classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="36254-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="36254-105">Cette rubrique décrit les propriétés de l’objet **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="36254-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="36254-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="36254-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="36254-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="36254-107">CurrentFile</span></span>

> <span data-ttu-id="36254-108">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-109">Propriété en lecture seule qui obtient le fichier associé à cet objet hôte ayant actuellement le focus.</span><span class="sxs-lookup"><span data-stu-id="36254-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="36254-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="36254-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="36254-111">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-112">Propriété en lecture seule qui obtient l’onglet PowerShell ayant le focus.</span><span class="sxs-lookup"><span data-stu-id="36254-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="36254-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="36254-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="36254-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-115">Propriété en lecture seule qui obtient l’outil complémentaire Windows PowerShell ISE qui est actuellement visible dans le volet d’outils horizontal en bas de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="36254-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="36254-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="36254-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="36254-117">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-118">Propriété en lecture seule qui obtient l’outil complémentaire Windows PowerShell ISE qui est actuellement visible dans le volet d’outils vertical à droite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="36254-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="36254-119">Options</span><span class="sxs-lookup"><span data-stu-id="36254-119">Options</span></span>

> <span data-ttu-id="36254-120">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-121">Propriété en lecture seule qui obtient les diverses options permettant de modifier des paramètres dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="36254-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="36254-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="36254-122">PowerShellTabs</span></span>

> <span data-ttu-id="36254-123">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="36254-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="36254-124">Propriété en lecture seule qui obtient la collection des onglets PowerShell ouverts dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="36254-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="36254-125">Par défaut, cet objet contient un seul onglet PowerShell. Toutefois, vous pouvez ajouter plusieurs onglets PowerShell à cet objet à l’aide de scripts ou en utilisant les menus dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="36254-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="36254-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36254-126">See Also</span></span>

- [<span data-ttu-id="36254-127">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="36254-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="36254-128">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="36254-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
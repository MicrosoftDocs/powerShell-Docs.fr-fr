---
title: Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f1ffca045b7efcecb4dce4e788a8c508fa6ef08
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783753"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="46c1f-102">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="46c1f-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="46c1f-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="46c1f-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="46c1f-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="46c1f-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour l’élément View (format) CustomItem pour CustomEntry pour l’élément View (format) ExpressionBinding pour CustomItem (format) CustomControlName élément pour la liaison d’expression pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46c1f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c1f-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46c1f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46c1f-107">Attributes and Elements</span></span>

<span data-ttu-id="46c1f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="46c1f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46c1f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="46c1f-109">Attributes</span></span>

<span data-ttu-id="46c1f-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46c1f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46c1f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46c1f-111">Child Elements</span></span>

<span data-ttu-id="46c1f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46c1f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46c1f-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46c1f-113">Parent Elements</span></span>

|<span data-ttu-id="46c1f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="46c1f-114">Element</span></span>|<span data-ttu-id="46c1f-115">Description</span><span class="sxs-lookup"><span data-stu-id="46c1f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46c1f-116">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="46c1f-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="46c1f-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="46c1f-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="46c1f-118">Text Value</span></span>

<span data-ttu-id="46c1f-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="46c1f-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="46c1f-120">Notes</span><span class="sxs-lookup"><span data-stu-id="46c1f-120">Remarks</span></span>

<span data-ttu-id="46c1f-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="46c1f-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="46c1f-122">Les noms de ces contrôles sont spécifiés par les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="46c1f-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="46c1f-123">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="46c1f-124">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="46c1f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46c1f-125">See Also</span></span>

[<span data-ttu-id="46c1f-126">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="46c1f-127">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="46c1f-128">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="46c1f-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="46c1f-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="46c1f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

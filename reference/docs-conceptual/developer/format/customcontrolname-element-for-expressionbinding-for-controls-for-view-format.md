---
title: Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786014"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="85b30-102">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="85b30-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="85b30-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="85b30-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="85b30-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="85b30-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles de l’élément View (format) CustomItem pour CustomControlName pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="85b30-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85b30-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85b30-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85b30-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="85b30-107">Attributes and Elements</span></span>

<span data-ttu-id="85b30-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="85b30-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85b30-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="85b30-109">Attributes</span></span>

<span data-ttu-id="85b30-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="85b30-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85b30-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="85b30-111">Child Elements</span></span>

<span data-ttu-id="85b30-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="85b30-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85b30-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="85b30-113">Parent Elements</span></span>

|<span data-ttu-id="85b30-114">Élément</span><span class="sxs-lookup"><span data-stu-id="85b30-114">Element</span></span>|<span data-ttu-id="85b30-115">Description</span><span class="sxs-lookup"><span data-stu-id="85b30-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85b30-116">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="85b30-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="85b30-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85b30-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="85b30-118">Text Value</span></span>

<span data-ttu-id="85b30-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="85b30-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="85b30-120">Notes</span><span class="sxs-lookup"><span data-stu-id="85b30-120">Remarks</span></span>

<span data-ttu-id="85b30-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="85b30-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="85b30-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="85b30-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="85b30-123">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="85b30-124">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="85b30-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85b30-125">See Also</span></span>

[<span data-ttu-id="85b30-126">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="85b30-127">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="85b30-128">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="85b30-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="85b30-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="85b30-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: Élément CustomControlName pour ExpressionBinding pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 690b6ae01b8116b72fbd00aef574feda1fd737b0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786031"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="5080e-102">CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5080e-103">Spécifie le nom d’un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="5080e-103">Specifies the name of a common control.</span></span> <span data-ttu-id="5080e-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5080e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5080e-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément CustomItem pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) CustomControlName élément pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5080e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5080e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5080e-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5080e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5080e-107">Attributes and Elements</span></span>

<span data-ttu-id="5080e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="5080e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5080e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5080e-109">Attributes</span></span>

<span data-ttu-id="5080e-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5080e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5080e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5080e-111">Child Elements</span></span>

<span data-ttu-id="5080e-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5080e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5080e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5080e-113">Parent Elements</span></span>

|<span data-ttu-id="5080e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5080e-114">Element</span></span>|<span data-ttu-id="5080e-115">Description</span><span class="sxs-lookup"><span data-stu-id="5080e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5080e-116">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5080e-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5080e-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5080e-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="5080e-118">Text Value</span></span>

<span data-ttu-id="5080e-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5080e-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="5080e-120">Notes</span><span class="sxs-lookup"><span data-stu-id="5080e-120">Remarks</span></span>

<span data-ttu-id="5080e-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="5080e-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="5080e-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="5080e-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="5080e-123">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="5080e-124">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="5080e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5080e-125">See Also</span></span>

[<span data-ttu-id="5080e-126">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="5080e-127">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="5080e-128">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5080e-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5080e-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5080e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: Controls, élément de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783787"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="a39cc-102">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="a39cc-103">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a39cc-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="a39cc-104">Élément de configuration (format) contrôle l’élément de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a39cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a39cc-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a39cc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a39cc-106">Attributes and Elements</span></span>

<span data-ttu-id="a39cc-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Controls` élément.</span><span class="sxs-lookup"><span data-stu-id="a39cc-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a39cc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="a39cc-108">Attributes</span></span>

<span data-ttu-id="a39cc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a39cc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a39cc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a39cc-110">Child Elements</span></span>

|<span data-ttu-id="a39cc-111">Élément</span><span class="sxs-lookup"><span data-stu-id="a39cc-111">Element</span></span>|<span data-ttu-id="a39cc-112">Description</span><span class="sxs-lookup"><span data-stu-id="a39cc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a39cc-113">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="a39cc-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a39cc-114">Required element.</span></span><br /><br /> <span data-ttu-id="a39cc-115">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a39cc-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a39cc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a39cc-116">Parent Elements</span></span>

|<span data-ttu-id="a39cc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="a39cc-117">Element</span></span>|<span data-ttu-id="a39cc-118">Description</span><span class="sxs-lookup"><span data-stu-id="a39cc-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a39cc-119">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="a39cc-120">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a39cc-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a39cc-121">Notes</span><span class="sxs-lookup"><span data-stu-id="a39cc-121">Remarks</span></span>

<span data-ttu-id="a39cc-122">Vous pouvez créer n’importe quel nombre de contrôles communs.</span><span class="sxs-lookup"><span data-stu-id="a39cc-122">You can create any number of common controls.</span></span> <span data-ttu-id="a39cc-123">Pour chaque contrôle, vous devez spécifier le nom utilisé pour référencer le contrôle et les composants du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a39cc-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="a39cc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a39cc-124">See Also</span></span>

[<span data-ttu-id="a39cc-125">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a39cc-126">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a39cc-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="a39cc-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a39cc-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

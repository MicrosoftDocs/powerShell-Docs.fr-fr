---
title: Élément CustomEntries pour CustomControl pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b1f494cf1a254d71362830ba9eb0f4905a2a484d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785980"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="54119-102">CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54119-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54119-103">Fournit les définitions d’un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54119-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="54119-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="54119-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54119-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54119-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54119-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54119-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="54119-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="54119-107">Attributes and Elements</span></span>

<span data-ttu-id="54119-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="54119-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="54119-109">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="54119-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="54119-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="54119-110">Attributes</span></span>

<span data-ttu-id="54119-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="54119-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54119-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="54119-112">Child Elements</span></span>

|<span data-ttu-id="54119-113">Élément</span><span class="sxs-lookup"><span data-stu-id="54119-113">Element</span></span>|<span data-ttu-id="54119-114">Description</span><span class="sxs-lookup"><span data-stu-id="54119-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54119-115">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54119-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="54119-116">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54119-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54119-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="54119-117">Parent Elements</span></span>

|<span data-ttu-id="54119-118">Élément</span><span class="sxs-lookup"><span data-stu-id="54119-118">Element</span></span>|<span data-ttu-id="54119-119">Description</span><span class="sxs-lookup"><span data-stu-id="54119-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54119-120">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54119-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="54119-121">Définit un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54119-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54119-122">Notes</span><span class="sxs-lookup"><span data-stu-id="54119-122">Remarks</span></span>

<span data-ttu-id="54119-123">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="54119-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="54119-124">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="54119-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="54119-125">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="54119-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="54119-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54119-126">See Also</span></span>

[<span data-ttu-id="54119-127">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54119-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="54119-128">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54119-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="54119-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="54119-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour GroupBy (Format)
description: TypeName, élément pour EntrySelectedBy pour GroupBy (Format)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645717"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="a0207-103">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0207-103">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="a0207-104">Spécifie un type .NET qui utilise cette définition du contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a0207-104">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="a0207-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="a0207-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a0207-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour l’élément GroupBy (format) CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour l’élément GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0207-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0207-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0207-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0207-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a0207-108">Attributes and Elements</span></span>

<span data-ttu-id="a0207-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="a0207-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0207-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a0207-110">Attributes</span></span>

<span data-ttu-id="a0207-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a0207-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0207-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a0207-112">Child Elements</span></span>

<span data-ttu-id="a0207-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a0207-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0207-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a0207-114">Parent Elements</span></span>

|<span data-ttu-id="a0207-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a0207-115">Element</span></span>|<span data-ttu-id="a0207-116">Description</span><span class="sxs-lookup"><span data-stu-id="a0207-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0207-117">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0207-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a0207-118">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a0207-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a0207-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a0207-119">Text Value</span></span>

<span data-ttu-id="a0207-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="a0207-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0207-121">Notes</span><span class="sxs-lookup"><span data-stu-id="a0207-121">Remarks</span></span>

<span data-ttu-id="a0207-122">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="a0207-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a0207-123">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0207-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0207-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0207-124">See Also</span></span>

[<span data-ttu-id="a0207-125">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="a0207-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a0207-126">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0207-126">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a0207-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0207-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

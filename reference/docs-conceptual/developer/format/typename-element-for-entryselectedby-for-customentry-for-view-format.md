---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)
description: TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645744"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="e5b1a-103">TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5b1a-103">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="e5b1a-104">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-104">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="e5b1a-105">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-105">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="e5b1a-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément (format) TypeName pour EntrySelectedBy pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="e5b1a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5b1a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5b1a-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5b1a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5b1a-108">Attributes and Elements</span></span>

<span data-ttu-id="e5b1a-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5b1a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5b1a-110">Attributes</span></span>

<span data-ttu-id="e5b1a-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5b1a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5b1a-112">Child Elements</span></span>

<span data-ttu-id="e5b1a-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5b1a-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5b1a-114">Parent Elements</span></span>

|<span data-ttu-id="e5b1a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e5b1a-115">Element</span></span>|<span data-ttu-id="e5b1a-116">Description</span><span class="sxs-lookup"><span data-stu-id="e5b1a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5b1a-117">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e5b1a-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5b1a-118">Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisée ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-118">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5b1a-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e5b1a-119">Text Value</span></span>

<span data-ttu-id="e5b1a-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="e5b1a-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5b1a-121">Notes</span><span class="sxs-lookup"><span data-stu-id="e5b1a-121">Remarks</span></span>

<span data-ttu-id="e5b1a-122">Chaque définition d’affichage de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="e5b1a-122">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e5b1a-123">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e5b1a-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5b1a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5b1a-124">See Also</span></span>

[<span data-ttu-id="e5b1a-125">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="e5b1a-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e5b1a-126">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e5b1a-126">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5b1a-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b1a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: Élément TypeName pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780265"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="c9355-102">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c9355-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="c9355-103">Spécifie un type .NET qui utilise cette définition du contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c9355-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="c9355-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="c9355-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c9355-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour l’élément GroupBy (format) CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour l’élément GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c9355-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9355-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9355-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9355-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c9355-107">Attributes and Elements</span></span>

<span data-ttu-id="c9355-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="c9355-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9355-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c9355-109">Attributes</span></span>

<span data-ttu-id="c9355-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c9355-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9355-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c9355-111">Child Elements</span></span>

<span data-ttu-id="c9355-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c9355-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9355-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c9355-113">Parent Elements</span></span>

|<span data-ttu-id="c9355-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c9355-114">Element</span></span>|<span data-ttu-id="c9355-115">Description</span><span class="sxs-lookup"><span data-stu-id="c9355-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9355-116">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c9355-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c9355-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="c9355-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9355-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c9355-118">Text Value</span></span>

<span data-ttu-id="c9355-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="c9355-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9355-120">Notes</span><span class="sxs-lookup"><span data-stu-id="c9355-120">Remarks</span></span>

<span data-ttu-id="c9355-121">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="c9355-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c9355-122">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c9355-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9355-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9355-123">See Also</span></span>

[<span data-ttu-id="c9355-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="c9355-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c9355-125">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c9355-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c9355-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9355-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

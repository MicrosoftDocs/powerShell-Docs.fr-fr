---
title: Élément TypeName pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361668"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="722f3-102">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="722f3-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="722f3-103">Spécifie un type .NET qui utilise cette définition du contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="722f3-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="722f3-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="722f3-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="722f3-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour l’élément (format) TypeName de GroupBy pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="722f3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="722f3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="722f3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="722f3-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="722f3-107">Attributes and Elements</span></span>

<span data-ttu-id="722f3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="722f3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="722f3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="722f3-109">Attributes</span></span>

<span data-ttu-id="722f3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="722f3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="722f3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="722f3-111">Child Elements</span></span>

<span data-ttu-id="722f3-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="722f3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="722f3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="722f3-113">Parent Elements</span></span>

|<span data-ttu-id="722f3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="722f3-114">Element</span></span>|<span data-ttu-id="722f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="722f3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="722f3-116">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="722f3-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="722f3-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="722f3-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="722f3-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="722f3-118">Text Value</span></span>

<span data-ttu-id="722f3-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="722f3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="722f3-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="722f3-120">Remarks</span></span>

<span data-ttu-id="722f3-121">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="722f3-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="722f3-122">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="722f3-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="722f3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="722f3-123">See Also</span></span>

[<span data-ttu-id="722f3-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="722f3-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="722f3-125">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="722f3-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="722f3-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="722f3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: Élément TypeName pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361628"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9755f-102">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9755f-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9755f-103">Spécifie un type .NET qui utilise cette entrée de la vue table.</span><span class="sxs-lookup"><span data-stu-id="9755f-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="9755f-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de table.</span><span class="sxs-lookup"><span data-stu-id="9755f-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="9755f-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy élément (format) élément TypeName pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9755f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9755f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9755f-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9755f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9755f-107">Attributes and Elements</span></span>

<span data-ttu-id="9755f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="9755f-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9755f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9755f-109">Attributes</span></span>

<span data-ttu-id="9755f-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9755f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9755f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9755f-111">Child Elements</span></span>

<span data-ttu-id="9755f-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9755f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9755f-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9755f-113">Parent Elements</span></span>

|<span data-ttu-id="9755f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="9755f-114">Element</span></span>|<span data-ttu-id="9755f-115">Description</span><span class="sxs-lookup"><span data-stu-id="9755f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9755f-116">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="9755f-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9755f-117">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9755f-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9755f-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9755f-118">Text Value</span></span>

<span data-ttu-id="9755f-119">Spécifiez le nom du type .NET.</span><span class="sxs-lookup"><span data-stu-id="9755f-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="9755f-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="9755f-120">Remarks</span></span>

<span data-ttu-id="9755f-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="9755f-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9755f-122">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9755f-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9755f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9755f-123">See Also</span></span>

[<span data-ttu-id="9755f-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="9755f-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9755f-125">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="9755f-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9755f-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9755f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

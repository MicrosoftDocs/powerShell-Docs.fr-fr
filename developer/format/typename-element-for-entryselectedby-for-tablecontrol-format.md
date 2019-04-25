---
title: Élément TypeName pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083958"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ec8a8-102">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ec8a8-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ec8a8-103">Spécifie un type .NET qui utilise cette entrée de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="ec8a8-104">Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de table.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="ec8a8-105">Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy, élément (Format) TypeName élément de configuration pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ec8a8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec8a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec8a8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec8a8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ec8a8-107">Attributes and Elements</span></span>

<span data-ttu-id="ec8a8-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec8a8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ec8a8-109">Attributes</span></span>

<span data-ttu-id="ec8a8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec8a8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ec8a8-111">Child Elements</span></span>

<span data-ttu-id="ec8a8-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec8a8-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ec8a8-113">Parent Elements</span></span>

|<span data-ttu-id="ec8a8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ec8a8-114">Element</span></span>|<span data-ttu-id="ec8a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="ec8a8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec8a8-116">Élément EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ec8a8-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ec8a8-117">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec8a8-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="ec8a8-118">Text Value</span></span>

<span data-ttu-id="ec8a8-119">Spécifiez le nom du type .NET.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec8a8-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec8a8-120">Remarks</span></span>

<span data-ttu-id="ec8a8-121">Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="ec8a8-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ec8a8-122">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ec8a8-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec8a8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec8a8-123">See Also</span></span>

[<span data-ttu-id="ec8a8-124">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="ec8a8-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ec8a8-125">Élément EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ec8a8-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ec8a8-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8a8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: Élément TypeName pour EntrySelectedBy pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861665"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="21975-102">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21975-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="21975-103">Spécifie un type .NET qui utilise cette définition du contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="21975-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="21975-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="21975-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="21975-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de TypeName GroupBy (Format) pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21975-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21975-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21975-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21975-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="21975-107">Attributes and Elements</span></span>

<span data-ttu-id="21975-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="21975-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21975-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="21975-109">Attributes</span></span>

<span data-ttu-id="21975-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="21975-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21975-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21975-111">Child Elements</span></span>

<span data-ttu-id="21975-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="21975-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="21975-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21975-113">Parent Elements</span></span>

|<span data-ttu-id="21975-114">Élément</span><span class="sxs-lookup"><span data-stu-id="21975-114">Element</span></span>|<span data-ttu-id="21975-115">Description</span><span class="sxs-lookup"><span data-stu-id="21975-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21975-116">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21975-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="21975-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="21975-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="21975-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="21975-118">Text Value</span></span>

<span data-ttu-id="21975-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="21975-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="21975-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="21975-120">Remarks</span></span>

<span data-ttu-id="21975-121">Chaque définition de contrôle doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="21975-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="21975-122">Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="21975-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21975-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21975-123">See Also</span></span>

[<span data-ttu-id="21975-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="21975-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="21975-125">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21975-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="21975-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="21975-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

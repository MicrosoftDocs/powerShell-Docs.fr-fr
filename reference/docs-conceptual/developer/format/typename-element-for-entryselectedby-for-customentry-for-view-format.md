---
title: Élément TypeName pour EntrySelectedBy pour CustomEntry pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368068"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="4a6c4-102">TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4a6c4-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="4a6c4-103">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="4a6c4-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="4a6c4-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) EntrySelectedBy , Élément de CustomEntry pour l’élément de vue (format) TypeName pour EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4a6c4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a6c4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a6c4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a6c4-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4a6c4-107">Attributes and Elements</span></span>

<span data-ttu-id="4a6c4-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a6c4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4a6c4-109">Attributes</span></span>

<span data-ttu-id="4a6c4-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a6c4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4a6c4-111">Child Elements</span></span>

<span data-ttu-id="4a6c4-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a6c4-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4a6c4-113">Parent Elements</span></span>

|<span data-ttu-id="4a6c4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="4a6c4-114">Element</span></span>|<span data-ttu-id="4a6c4-115">Description</span><span class="sxs-lookup"><span data-stu-id="4a6c4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a6c4-116">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4a6c4-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4a6c4-117">Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisée ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a6c4-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4a6c4-118">Text Value</span></span>

<span data-ttu-id="4a6c4-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a6c4-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a6c4-120">Remarks</span></span>

<span data-ttu-id="4a6c4-121">Chaque définition d’affichage de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="4a6c4-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4a6c4-122">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4a6c4-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a6c4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a6c4-123">See Also</span></span>

[<span data-ttu-id="4a6c4-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="4a6c4-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4a6c4-125">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4a6c4-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4a6c4-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a6c4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368068"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="31827-102">TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="31827-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="31827-103">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="31827-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="31827-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.</span><span class="sxs-lookup"><span data-stu-id="31827-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="31827-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) EntrySelectedBy , Élément de CustomEntry pour l’élément de vue (format) TypeName pour EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="31827-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31827-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31827-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31827-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="31827-107">Attributes and Elements</span></span>

<span data-ttu-id="31827-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="31827-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31827-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="31827-109">Attributes</span></span>

<span data-ttu-id="31827-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="31827-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31827-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="31827-111">Child Elements</span></span>

<span data-ttu-id="31827-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="31827-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31827-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="31827-113">Parent Elements</span></span>

|<span data-ttu-id="31827-114">Élément</span><span class="sxs-lookup"><span data-stu-id="31827-114">Element</span></span>|<span data-ttu-id="31827-115">Description</span><span class="sxs-lookup"><span data-stu-id="31827-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31827-116">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="31827-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="31827-117">Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisée ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="31827-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31827-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="31827-118">Text Value</span></span>

<span data-ttu-id="31827-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="31827-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="31827-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="31827-120">Remarks</span></span>

<span data-ttu-id="31827-121">Chaque définition d’affichage de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="31827-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="31827-122">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="31827-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31827-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31827-123">See Also</span></span>

[<span data-ttu-id="31827-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="31827-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="31827-125">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="31827-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="31827-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="31827-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

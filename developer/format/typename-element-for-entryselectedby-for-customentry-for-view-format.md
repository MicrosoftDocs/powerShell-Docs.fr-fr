---
title: Élément TypeName pour EntrySelectedBy pour CustomEntry pour la vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083975"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="d7641-102">TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d7641-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="d7641-103">Spécifie un type .NET qui utilise cette définition de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d7641-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="d7641-104">Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une définition.</span><span class="sxs-lookup"><span data-stu-id="d7641-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="d7641-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry pour l’élément d’affichage (Format) de TypeName pour EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d7641-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7641-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7641-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7641-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d7641-107">Attributes and Elements</span></span>

<span data-ttu-id="d7641-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="d7641-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7641-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d7641-109">Attributes</span></span>

<span data-ttu-id="d7641-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d7641-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7641-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d7641-111">Child Elements</span></span>

<span data-ttu-id="d7641-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d7641-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7641-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d7641-113">Parent Elements</span></span>

|<span data-ttu-id="d7641-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d7641-114">Element</span></span>|<span data-ttu-id="d7641-115">Description</span><span class="sxs-lookup"><span data-stu-id="d7641-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7641-116">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d7641-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d7641-117">Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisé ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d7641-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7641-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="d7641-118">Text Value</span></span>

<span data-ttu-id="d7641-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="d7641-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7641-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="d7641-120">Remarks</span></span>

<span data-ttu-id="d7641-121">Chaque définition de vue du contrôle personnalisé doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="d7641-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d7641-122">Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d7641-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7641-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7641-123">See Also</span></span>

[<span data-ttu-id="d7641-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="d7641-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d7641-125">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d7641-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d7641-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7641-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

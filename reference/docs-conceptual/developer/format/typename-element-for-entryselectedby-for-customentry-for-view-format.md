---
title: Élément TypeName pour EntrySelectedBy pour CustomEntry pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f8dc2c808e6eb3d6a7873cdbddc936b95d94c541
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785096"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="64c74-102">TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="64c74-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="64c74-103">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64c74-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="64c74-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.</span><span class="sxs-lookup"><span data-stu-id="64c74-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="64c74-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément (format) TypeName pour EntrySelectedBy pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="64c74-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64c74-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64c74-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64c74-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64c74-107">Attributes and Elements</span></span>

<span data-ttu-id="64c74-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="64c74-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64c74-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="64c74-109">Attributes</span></span>

<span data-ttu-id="64c74-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64c74-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64c74-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64c74-111">Child Elements</span></span>

<span data-ttu-id="64c74-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64c74-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="64c74-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64c74-113">Parent Elements</span></span>

|<span data-ttu-id="64c74-114">Élément</span><span class="sxs-lookup"><span data-stu-id="64c74-114">Element</span></span>|<span data-ttu-id="64c74-115">Description</span><span class="sxs-lookup"><span data-stu-id="64c74-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64c74-116">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="64c74-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="64c74-117">Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisée ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="64c74-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="64c74-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="64c74-118">Text Value</span></span>

<span data-ttu-id="64c74-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="64c74-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="64c74-120">Notes</span><span class="sxs-lookup"><span data-stu-id="64c74-120">Remarks</span></span>

<span data-ttu-id="64c74-121">Chaque définition d’affichage de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="64c74-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="64c74-122">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="64c74-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64c74-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64c74-123">See Also</span></span>

[<span data-ttu-id="64c74-124">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="64c74-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="64c74-125">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="64c74-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="64c74-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="64c74-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
